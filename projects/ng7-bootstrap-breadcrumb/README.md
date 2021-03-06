# ng7-bootstrap-breadcrumb


ng7-bootstrap-breadcrumb is a Angular7 bootstrap module for [Angular](https://angular.io/) that generates a Angular7 bootstrap breadcrumb for any page of your application. It is based on the built-in [Angular router](https://angular.io/docs/ts/latest/guide/router.html).

## [Demo  Example ](https://ng7-bootstrap-breadcrumb.stackblitz.io)
## [Demo  Source Example ](https://stackblitz.com/edit/ng7-bootstrap-breadcrumb)

# Usage

## Getting started

1.Install `ng7-bootstrap-breadcrumb` via npm:

```bash
npm install --save ng7-bootstrap-breadcrumb
```
Choose the version corresponding to your Angular version:

 Angular     | ng7-bootstrap-breadcrumb
 ----------- | ------------------- 
 8           | 2.x+               
 7           | 1.x   

2.Import the `Ng7BootstrapBreadcrumbModule` within your app:

```js
import {Ng7BootstrapBreadcrumbModule} from "ng7-bootstrap-breadcrumb";

@NgModule({
  imports: [
    Ng7BootstrapBreadcrumbModule,
  ],
})
```

3.Add a name to your route by adding a `breadcrumb` property in the route's `data`:
```js
const routes: Routes = [
  {
    path: 'page1/:pageOneID',
    component: PageComponent,
    data: {
      title: 'page1',
      breadcrumb: [
        {
          label: 'Page1',
          url: ''
        }
      ]
    },
  },
  {
    path: 'page1/:pageOneID/page2/:pageTwoID',
    component: Page2Component,
    data: {
      title: 'page2', 
      breadcrumb: [
        {
          label: 'page {{pageOneID}}',// pageOneID Parameter value will be add 
          url: '/page1/:pageOneID'
        },
        {
          label: 'page {{pageTwoID}}',// pageTwoID Parameter value will be add 
          url: ''
        }
      ]
    },
  },
  {
    path: 'page1/:pageOneID/page2/:pageTwoID/page3/:pageThreeID',
    component: Page3Component,
    data: {
      title: 'page3',
      breadcrumb: [
        {
          label: 'page1',
          url: '/page1/:pageOneID'
        },
        {
          label: '{{dynamicText}} page', // If "dynamicText" is not parameter , should be set value  using Ng7MatBreadcrumbService, More info please check the 5th point.
          url: 'page1/:pageOneID/page2/:pageTwoID'
        },
        {
          label: '{{customText}}', // If "customText" is not parameter , should be set value  using Ng7MatBreadcrumbService, More info please check the 5th point.
          url: ''
        }
      ]
    },
  },
];
```

4.Put the `Ng7DynamicBreadcrumbComponent`'s selector within your template:

```html
<app-ng7-bootstrap-breadcrumb></app-ng7-bootstrap-breadcrumb>
<router-outlet></router-outlet>
```

5.Set the value using `Ng7BootstrapBreadcrumbService`

```js
import { Ng7BootstrapBreadcrumbService } from 'ng7-bootstrap-breadcrumb';
constructor(private ng7BootstrapBreadcrumbService: Ng7BootstrapBreadcrumbService) { }
ngOnInit() {
  const breadcrumb =  {customText: 'This is Custom Text', dynamicText: 'Level 2 '};
  this.ng7BootstrapBreadcrumbService.updateBreadcrumbLabels(breadcrumb);
  }
```

## Help/Assistance

Developer: Raja Rama Mohan Thavalam <rajaram.tavalam@gmail.com>  


## License


(The MIT License)

Copyright (c) 2019 Raja Rama Mohan T <rajaram.tavalam@gmail.com>

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
'Software'), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY
CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE
SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
