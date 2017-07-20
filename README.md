# ngx-scroll-to

Scroll to any element to enhance scroll-based features in you app.<br>
Works for **Angular 4+**, both **AoT** and **SSR**. No dependencies.

Current Angular Version

[![npm version](https://badge.fury.io/js/%40angular%2Fcore.svg)](https://www.npmjs.com/~angular)

## Installation
```sh
$ npm install @nicky-lenaers/ngx-scroll-to
```

## Setup
```ts
...
import { ScrollToModule } from '@nicky-lenaers/ngx-scroll-to';
...

@NgModule({
  imports: [
    ...
    ScrollToModule.forRoot()
  ],
  ...
  bootstrap: [AppComponent]
})
export class AppModule { }
```

## Basic Usage
**my-component.html**

```html
<button [ngx-scroll-to]="'destination">Go to destination</button>

<div id="destination">
  You've reached your destination.
</div>
```

## Advanced Usage
**my-component.ts**
```ts
import { ScrollToAnimationEasing, ScrollToEvent, ScrollToOffsetMap } from '@nicky-lenaers/ngx-scroll-to';

@Component({
  selector: 'my-component'
  templateUrl: './component.html'
})
export class MyComponent {

  public ngxScrollToDestination: string;
  public ngxScrollToEvent: ScrollToEvent;
  public ngxScrollToDuration: number;
  public ngxScrollToEasing: ScrollToAnimationEasing;
  public ngxScrollToOffset: number;
  public ngxScrollToOffsetMap: ScrollToOffsetMap;

  constructor() {

    this.ngxScrollToDestination = 'destination-1';
    this.ngxScrollToEvent = 'mouseenter';
    this.ngxScrollToDuration = 1500;
    this.ngxScrollToEasing = 'easeOutElastic';
    this.ngxScrollToOffset = 300;
    this.ngxScrollToOffsetMap = new Map();
    this.ngxScrollToOffsetMap
      .set(480, 100)
      .set(768, 200)
      .set(1240, 300)
      .set(1920, 400)

  }

  public toggleDestination() {
    this.ngxScrollToDestination = this.ngxScrollToDestination === 'destination-1' ? 'destination-2' : 'destination-1';
  }
}
```


**my-component.html**
```html
<button (click)="toggleDestination()">Toggle Destination</button>

<button 
  [ngx-scroll-to]="ngxScrollToDestination"
  [ngx-scroll-to-event]="ngxScrollToEvent"
  [ngx-scroll-to-duration]="ngxScrollToDuration"
  [ngx-scroll-to-easing]="ngxScrollToEasing"
  [ngx-scroll-to-offset]="ngxScrollToOffset"
  [ngx-scroll-to-offset-map]="ngxScrollToOffsetMap">
  Go to destination
</button>

<div id="destination-1">
  You've reached your first destination
</div>

<div id="destination-2">
  You've reached your second destination
</div>
```

## Attributes Map
| Options                                                       | Type                  | Default         | Accepts                                            |
|---------------------------------------------------------------|-----------------------|-----------------|----------------------------------------------------|
| [ngx-scroll-to](#ngx-scroll-to-details)                       | `string`              | `''`            | Any `string` value                                 |
| [ngx-scroll-to-event](#ngx-scroll-to-event-details)           | `string`              | `click`         | `ScrollToEvent`                                    |
| [ngx-scroll-to-duration](#ngx-scroll-to-duration-details)     | `number`              | `650`           | Any `number` value                                 |
| [ngx-scroll-to-easing](#ngx-scroll-to-easing-details)         | `string`              | `easeInOutQuad` | `ScrollToAnimationEasing`                          |
| [ngx-scroll-to-offset](#ngx-scroll-to-offset-details)         | `number`              | `0`             | Any `number` value                                 |
| [ngx-scroll-to-offset-map](#ngx-scroll-to-offset-map-details) | `Map<number, number>` | `new Map()`     | Any `Map` with a key `number` and a value `number` |

## Attribue Map Details
#### <a name="ngx-scroll-to-details"></a>`[ngx-scroll-to]`
This value specifies the ID of the HTML Element to scroll to. Note the outer double quotes `""` and the inner single quotes `''` in the above examples. This enables you to dynamically set the string value based on a class property of your Component.

#### <a name="ngx-scroll-to-event-details"></a>`[ngx-scroll-to-event]`
This value controls to event on which to trigger the scroll animation. Allowed values are:
- `click`
- `mouseenter`
- `mouseover`
- `mousedown`
- `mouseup`
- `dblclick`
- `contextmenu`
- `wheel`
- `mouseleave`
- `mouseout`

#### <a name="ngx-scroll-to-duration-details"></a>`[ngx-scroll-to-duration]`
This value controls to duration of your scroll animation. Note that this value is in milliseconds.

#### <a name="ngx-scroll-to-easing-details"></a>`[ngx-scroll-to-easing]`
This value controls a named easing logic function to control your animation easing. Allowed values are:
- `easeInQuad`
- `easeOutQuad`
- `easeInOutQuad`
- `easeInCubic`
- `easeOutCubic`
- `easeInOutCubic`
- `easeInQuart`
- `easeOutQuart`
- `easeInOutQuart`
- `easeInQuint`
- `easeOutQuint`
- `easeInOutQuint`
- `easeOutElastic`

#### <a name="ngx-scroll-to-offset-details"></a>`[ngx-scroll-to-offset]`
This value controls the offset with respect to the top of the destination HTML element. Note that this value is in pixels.

#### <a name="ngx-scroll-to-offset-map-details"></a>`[ngx-scroll-to-offset-map]`
This value allows you to control dynamic offsets based on the width of the device screen. The Map get's iterated over internally in a sequential fashion, meaning you need to supply key values in the order from low to high. The `key` of the `Map` defines the width treshold. The `value` of the `Map` defines the offset. Note that the this value is in pixels.

# License
 [MIT](/LICENSE)