[![npm version](https://img.shields.io/npm/v/ngx-gallery.svg)](https://www.npmjs.com/package/ngx-gallery)
[![Downloads](https://img.shields.io/npm/dm/ngx-gallery.svg)](https://www.npmjs.com/package/ngx-gallery)

# NgxGallery
Angular 2/4 image gallery plugin

# Demo
[Link](https://lukasz-galka.github.io/ngx-gallery-demo/)

# Prerequisites
- [Font Awesome](http://fontawesome.io/) (required for icons)

```npm install font-awesome --save```

For angular-cli based projects insert styles into .angular-cli.json

````
"styles": [
    ...
    "../node_modules/font-awesome/css/font-awesome.css"
]
````

- [Hammerjs](http://hammerjs.github.io/) (required for swipe)

```npm install hammerjs --save```

````
import 'hammerjs';
````

# Angular Material

**If you are not using Angular Material you can skip this section.**

Angular Material is using `transform: translate3d(0,0,0);` in components styles. Unfortunately  `transform` changes positioning context and preview won't work properly. To avoid this situation you have to override material styles, for example:

````
@import "~@angular/material/prebuilt-themes/indigo-pink.css"; // your theme

.mat-sidenav-container, .mat-sidenav-content, .mat-tab-body-content {
    transform: none !important;
}
````

You can read more about this issue [here](https://github.com/angular/material2/issues/998)

# Installation
```npm install ngx-gallery --save```

# NgxGalleryOptions

- `width` | Type: `string` | Default value: `'500px'` - gallery width
- `height` | Type: `string` | Default value: `'400px'` - gallery height
- `breakpoint` | Type: `number` | Default value: `undefined` - responsive breakpoint, works like media query max-width
- `fullWidth` | Type: `boolean` | Default value: `false` - sets the same width as browser
- `layout` | Type: `string` | Default value: `NgxGalleryLayout.Bottom` - sets thumbnails position
- `startIndex` | Type: `number` | Default value: `0` - sets index of selected image on start

- `image` | Type: `boolean` | Default value: `true` - enables or disables image
- `imagePercent` | Type: `number` | Default value: `75` - percentage height
- `imageArrows` | Type: `boolean` | Default value: `true` - enables or disables arrows
- `imageArrowsAutoHide` | Type: `boolean` | Default value: `false` - enables or disables arrows auto hide
- `imageSwipe` | Type: `boolean` | Default value: `false` - enables or disables swipe
- `imageAnimation` | Type: `string` | Default value: `NgxGalleryAnimation.Fade` - animation type
- `imageSize` | Type: `string` | Default value: `NgxGalleryImageSize.Cover` - image size
- `imageAutoPlay` | Type: `boolean` | Default value `false` - enables or disables auto play
- `imageAutoPlayInterval` | Type: `number` | Default value: `2000` - interval for auto play (ms)
- `imageInfinityMove` | Type: `boolean` | Default value: `false` - enables or disables infinity move by arrows
- `thumbnails` | Type: `boolean` | Default value: `true` - enables or disables thumbnails
- `thumbnailsColumns` | Type: `number` | Default value: `4` - columns count
- `thumbnailsRows` | Type: `number` | Default value: `1` - rows count
- `thumbnailsPercent` | Type: `number` | Default value: `25` - percentage height
- `thumbnailsMargin` | Type: `number` | Default value: `10` - margin between thumbnails and image
- `thumbnailsArrows` | Type: `boolean` | Default value: `true` - enables or disables arrows
- `thumbnailsArrowsAutoHide` | boolean: `string` | Default value: `false` - enables or disables arrows auto hide
- `thumbnailsSwipe` | Type: `boolean` | Default value: `false` - enables or disables swipe
- `thumbnailMargin` | Type: `number` | Default value: `10` - margin between images in thumbnails
- `thumbnailSize` | Type: `string` | Default value: `NgxGalleryImageSize.Cover` - thumbnail size

- `preview` | Type: `boolean` | Default value: `true` - enables or disables preview
- `previewDescription` | Type: `boolean` | Default value: `true` - enables or disables description for images
- `previewSwipe` | Type: `boolean` | Default value: `false` - enables or disables swipe
- `previewFullscreen` | Type: `boolean` | Default value: `false` - enables or disables fullscreen icon
- `previewForceFullscreen` | Type: `boolean` | Default value: `false` - enables or disables opening preview in fullscreen mode
- `previewCloseOnClick` | Type: `boolean` | Default value: `false` - enables or disables closing preview by click
- `previewCloseOnEsc` | Type: `boolean` | Default value: `false` - enables or disables closing preview by esc keyboard
- `previewKeyboardNavigation` | Type: `boolean` | Default value: `false` - enables or disables navigation by keyboard
- `previewAutoPlay` | Type: `boolean` | Default value `false` - enables or disables auto play
- `previewAutoPlayInterval` | Type: `number` | Default value: `2000` - interval for auto play (ms)
- `previewInfinityMove` | Type: `boolean` | Default value: `false` - enables or disables infinity move by arrows

- `arrowPrevIcon` | Type: `string` | Default value: `'fa fa-arrow-circle-left'` - icon for prev arrow
- `arrowNextIcon` | Type: `string` | Default value: `'fa fa-arrow-circle-right'` - icon for next arrow
- `closeIcon` | Type: `string` | Default value: `'fa fa-times-circle'` - icon for close button
- `fullscreenIcon` | Type: `string` | Default value: `'fa fa-arrows-alt'` - icon for fullscreen button
- `spinnerIcon` | Type: `string` | Default value: `'fa fa-spinner fa-pulse fa-3x fa-fw'` - icon for spinner

# NgxGalleryImage
- `small` | Type: `string | SafeResourceUrl` - url used in thumbnails
- `medium` | Type: `string | SafeResourceUrl` - url used in image
- `big` | Type: `string | SafeResourceUrl` - url used in preview
- `description` | Type: `string` - description used in preview

# NgxGalleryAnimation
- `Fade` (default)
- `Slide`
- `Rotate`
- `Zoom`

# NgxGalleryImageSize
- `Cover` (default)
- `Contain`

# NgxGalleryLayout
- `Top`
- `Bottom` (default)

# Events
- `change` - triggered on image change
- `previewOpen` - triggered on preview open
- `previewClose` - triggered on preview close

# Usage
````ts
// app.module.ts
import { NgxGalleryModule } from 'ngx-gallery';
...
@NgModule({
    imports: [
        ...
        NgxGalleryModule
        ...
    ],
    ...
})
export class AppModule { }
````

````ts
// app.component.ts
import { Component, OnInit } from '@angular/core';
import { NgxGalleryOptions, NgxGalleryImage, NgxGalleryAnimation } from 'ngx-gallery';
...

@Component({
    templateUrl: './app.component.html',
    styleUrls: ['./app.component.scss'],
})
export class AppComponent implements OnInit {    
    galleryOptions: NgxGalleryOptions[];
    galleryImages: NgxGalleryImage[];

    ngOnInit(): void {     

        this.galleryOptions = [
            {
                width: '600px',
                height: '400px',
                thumbnailsColumns: 4,
                imageAnimation: NgxGalleryAnimation.Slide
            },
            // max-width 800
            {
                breakpoint: 800,
                width: '100%',
                height: '600px',
                imagePercent: 80,
                thumbnailsPercent: 20,
                thumbnailsMargin: 20,
                thumbnailMargin: 20
            },
            // max-width 400
            {
                breakpoint: 400,
                preview: false
            }
        ];

        this.galleryImages = [
            {
                small: 'assets/1-small.jpg',
                medium: 'assets/1-medium.jpg',
                big: 'assets/1-big.jpg'
            },
            {
                small: 'assets/2-small.jpg',
                medium: 'assets/2-medium.jpg',
                big: 'assets/2-big.jpg'
            },
            {
                small: 'assets/3-small.jpg',
                medium: 'assets/3-medium.jpg',
                big: 'assets/3-big.jpg'
            }
        ];
    }
}

````

````html
// app.component.html
<ngx-gallery [options]="galleryOptions" [images]="galleryImages"></ngx-gallery>
````
