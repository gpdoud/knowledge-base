# Changes in Angular 17

## `Signals`?

## `@if`

@if is a new template statement meaning it can be coded in a template. An @else clause is optional

```
@if(aNumber % 2 === 0) {
    <p>The number is even!</p>
} @else {
    <p>The number is odd!</p>
}
```

## `@for`

@for is similar to the @if.

```
@for(item of items; track item.id) {
    <p>Item nbr {{ item.id }} is {{ item.name }}
}
```

## `@defer`

`@defer` allows controlled lazy loading of views. The default is that the view will be loaded when the browser is idle. With `(on viewport)`, the view is not loaded until it is presented.

`@placeholder` displays some template data until the view is actually loaded. With the `(minimum Ns)`, the template will continue to display till the timer expires.

`@loading` displays some template data while the loading is beging done. It too can use the `(minimum Ns)` to make it display a minimum amount of time. The `(after Ns)`, the loading template will remain even after the loading is complete.

```ng
@defer (on viewport) {
    // defers loading until on viewport
    <component />
} @placeholder (minimum 2s) {
    <p>Displays for minimum of 2s BEFORE the component is loaded</p>
} @loading (minimum 2s, after 3s) {
    <p>Displays WHILE the component is loading</p>
}
```

## `inject()`

`inject()` is an alternate way of injecting objects into a component or service rather than having to use the `constructor` parameter list. Both have the same effect.

```ng
// the inject() is used
userSvc = inject(UserService);
// versus
constructor(private userSvc: UserService) {}
```

## `pipes`

All pipes used must be imported individually. They can be imported automatically
by clicking the `Quick Fix` in the template.

## `HttpClient`

Because there is no 'imports' in services, to import the `HttpClient` service for use
by other services requires the following changes to `app.config.ts`:

Add `import { provideHttpClient} from '@angular/common/http';`

Add `provideHttpClient()` to providers

## `Using external config file`

The process of reading in an external configuration file is similar
to what was needed in v16 and older.

Start by creating a JSON file in the src/assets folder. It can be named anything.

Generate a service (i.e. app-config) in the app folder.

Place the following code in the service class

```ng
http = inject(HttpClient);
    appConfig: any;

get AppConfig() {
    return this.appConfig;
}

loadAppConfig() {
    this.http.get('/assets/app.config').subscribe(
        config => {
            this.appConfig = config
        }
    );
}
```

Add the following code to app.config.ts:

```
import { APP_INITIALIZER } from '@angular/core';
import { AppConfigService } from './app-config.service';

const startupServiceFactory = (appConfig: AppConfigService) => {
    return () => appConfig.loadAppConfig();
}

export const appConfig: ApplicationConfig = {
    providers: [ 
        AppConfigService, {
            provide: APP_INITIALIZER,
            useFactory: startupServiceFactory,
            deps: [AppConfigService],
            multi: true
        }
    ]
};
```
