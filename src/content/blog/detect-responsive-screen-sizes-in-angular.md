---
title: 'Detect Responsive Screen Sizes in Angular'
description: 'Learn how to detect responsive breakpoints in Angular using Bootstrap classes without maintaining breakpoint sizes in your TypeScript code.'
pubDate: '2015-06-05'
heroImage: '/images/angularjs-2.jpg'
---

Usually, we rely on CSS media queries for responsive design. But there are situations when CSS alone isn't sufficient, and we need to detect screen size changes programmatically. Here's how to detect responsive breakpoints in Angular efficiently, using Bootstrap CSS classes instead of hardcoding breakpoints in TypeScript.

## The Approach

We'll use Bootstrap's predefined responsive visibility classes to detect the current screen size:

- **Extra small (`xs`):** `.d-block .d-sm-none`
- **Small (`sm`):** `.d-none .d-sm-block .d-md-none`
- **Medium (`md`):** `.d-none .d-md-block .d-lg-none`
- **Large (`lg`):** `.d-none .d-lg-block .d-xl-none`
- **Extra large (`xl`):** `.d-none .d-xl-block`

Each class toggles the element's `display` property between `none` and `block`. When the screen size changes, we detect which element is displayed.

## Creating the Size Detector Component

Create an Angular component named `size-detector.component`.

**HTML Template:**

```html
<!-- size-detector.component.html -->
<div *ngFor="let s of sizes" class="{{s.css + ' ' + (prefix + s.id)}}">{{s.name}}</div>
```

**TypeScript Component:**

```typescript
// size-detector.component.ts
import { Component, AfterViewInit, HostListener, ElementRef } from '@angular/core';
import { ResizeService } from './resize.service';

export enum SCREEN_SIZE {
  XS,
  SM,
  MD,
  LG,
  XL
}

@Component({
  selector: 'app-size-detector',
  templateUrl: './size-detector.component.html'
})
export class SizeDetectorComponent implements AfterViewInit {
  prefix = 'is-';
  sizes = [
    { id: SCREEN_SIZE.XS, name: 'xs', css: 'd-block d-sm-none' },
    { id: SCREEN_SIZE.SM, name: 'sm', css: 'd-none d-sm-block d-md-none' },
    { id: SCREEN_SIZE.MD, name: 'md', css: 'd-none d-md-block d-lg-none' },
    { id: SCREEN_SIZE.LG, name: 'lg', css: 'd-none d-lg-block d-xl-none' },
    { id: SCREEN_SIZE.XL, name: 'xl', css: 'd-none d-xl-block' },
  ];

  constructor(private elementRef: ElementRef, private resizeSvc: ResizeService) {}

  @HostListener('window:resize', [])
  private onResize() {
    this.detectScreenSize();
  }

  ngAfterViewInit() {
    this.detectScreenSize();
  }

  private detectScreenSize() {
    const currentSize = this.sizes.find(x => {
      const el = this.elementRef.nativeElement.querySelector(`.${this.prefix}${x.id}`);
      return window.getComputedStyle(el).display !== 'none';
    });

    this.resizeSvc.onResize(currentSize.id);
  }
}
```

## Resize Service

Create a `ResizeService` to broadcast screen size changes:

```typescript
// resize.service.ts
import { Injectable } from '@angular/core';
import { Subject, Observable } from 'rxjs';
import { distinctUntilChanged } from 'rxjs/operators';
import { SCREEN_SIZE } from './size-detector.component';

@Injectable()
export class ResizeService {
  private resizeSubject: Subject<SCREEN_SIZE> = new Subject();

  get onResize$(): Observable<SCREEN_SIZE> {
    return this.resizeSubject.asObservable().pipe(distinctUntilChanged());
  }

  onResize(size: SCREEN_SIZE) {
    this.resizeSubject.next(size);
  }
}
```

## Using the Service in Other Components

Inject the `ResizeService` into any component to react to screen size changes:

```typescript
// hello.component.ts
import { Component } from '@angular/core';
import { ResizeService } from './resize.service';
import { SCREEN_SIZE } from './size-detector.component';

@Component({
  selector: 'hello',
  template: `<h1>Hello {{size}}!</h1>`,
})
export class HelloComponent {
  size: SCREEN_SIZE;

  constructor(private resizeSvc: ResizeService) {
    this.resizeSvc.onResize$.subscribe(x => this.size = x);
  }
}
```

## Include Bootstrap

Include Bootstrap in your project via CDN in `index.html`:

```html
<!-- index.html -->
<link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css">
```

## Summary

With this approach, Angular components become aware of responsive breakpoints without duplicating CSS media query logic in TypeScript.
