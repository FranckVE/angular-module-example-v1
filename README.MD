# Create an Angular (v4) NPM module

> *Reference :*
> - https://github.com/jvandemo/generator-angular2-library

## 1. Install yeoman and generator-angular2-library

First, install [Yeoman](http://yeoman.io/) and generator-angular2-library using [npm](https://www.npmjs.com/) (assuming you already have [node.js](https://nodejs.org/) pre-installed).

```bash
npm install -g yo
npm install -g generator-angular2-library
```


## 2. Build the remote project repository on GuitHub

NB: the command below in creating `angular-module-example-v1234` as a PUBLIC repo !

```bash
curl -u 'FranckVE' https://api.github.com/user/repos -d '{"name":"angular-module-example-v1234", "private": false, "has_issues": true, "has_projects": true, "has_wiki": true}'
```

## 3. Clone the new (and empty) repository into the projects folder

```
cd ~/Documents/WebStormProjects2017
git clone https://github.com/FranckVE/angular-module-example-v1234.git
cd angular-module-example-v1234/
```

then open the project (folder) from Webstorm

## 4. Generate your new library

From the `angular-module-example-v1234` folder :

```bash
yo angular2-library
```

The generator will prompt you for:

```bash
     _-----_
    |       |    ╭──────────────────────────╮
    |--(o)--|    │  Welcome to the Angular  │
   `---------´   │    Library generator!    │
    ( _´U`_ )    ╰──────────────────────────╯
    /___A___\   /
     |  ~  |
   __'.___.'__
 ´   `  |° ´ Y `

? Your full name: FranckVE (your GitHub pseudo)
? Your email address: npm.franck.ve@gmail.com (your GitHub email)
? Your library name (kebab-case) angular-module-example-v1
? Git repository url https://github.com/FranckVE/angular-module-example-v1
? Test framework karma + jasmine
```


and create the following files for you:

```
.
├── README.MD
├── gulpfile.js
├── package.json
├── src
│   ├── index.ts
│   ├── package.json
│   ├── sample.component.ts
│   ├── sample.directive.ts
│   ├── sample.pipe.ts
│   ├── sample.service.ts
│   └── tsconfig.es5.json
├── tsconfig.json
└── tslint.json
```

## 5. Verify the remote git repository of the project

```
git remote show origin
```

## 6. Push the root


```
git add -A
git commit -m "Yeoman Angular Packaged Module generated"
git push -u origin master
```

## 7. Add the specific of your module

In `sample.component.ts` :

```javascript
@Component({
  selector: 'sample-component',
  templateUrl: './sample.component.html',
  styleUrls: ['./sample.component.css']
})
```

E.g. in `sample.component.html` :

```html
<div>
    <h1>This module H1</h1>
    <h2>This module H2</h2>
    <h2>This module other H2</h2>
</div>
```

## 8. use the module in another Angular app

### import the module

From the project :

```bash
yarn add https://github.com/FranckVE/angular-module-example-v1
```

### use the module

In the project module where you want to use the external module `xxx.module.ts` :

```javascript
...
import { SampleModule } from 'angular-module-example-v1/src';
...
@NgModule({
  imports: [
    ...
    SampleModule
    ...
  ],
  ...
})
...
```

and e.g. in `xxx.component.html` :

```html
<sample-component></sample-component>
```

# original README.md for angular-module-example-v1

## Installation

To install this library, run:

```bash
$ npm install angular-module-example-v1 --save
```

## Consuming your library

Once you have published your library to npm, you can import your library in any Angular application by running:

```bash
$ npm install angular-module-example-v1
```

and then from your Angular `AppModule`:

```typescript
import { BrowserModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';

import { AppComponent } from './app.component';

// Import your library
import { SampleModule } from 'angular-module-example-v1';

@NgModule({
  declarations: [
    AppComponent
  ],
  imports: [
    BrowserModule,

    // Specify your library as an import
    LibraryModule
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }
```

Once your library is imported, you can use its components, directives and pipes in your Angular application:

```xml
<!-- You can now use your library component in app.component.html -->
<h1>
  {{title}}
</h1>
<sampleComponent></sampleComponent>
```

## Development

To generate all `*.js`, `*.d.ts` and `*.metadata.json` files:

```bash
$ npm run build
```

To lint all `*.ts` files:

```bash
$ npm run lint
```

## License

MIT © [Franck VERMEULEN](mailto:npm.franck.ve@gmail.com)
