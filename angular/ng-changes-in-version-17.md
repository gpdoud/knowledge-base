# Changes in Angular 17

Signals?

@if

    trafficLight = "green";
    @if(trafficLight === "green") {
        <span>Drive on!</span>
    } @else {
        <span>Hit the brakes!!!</span>
    }

@for

    @for(item of items; track item.id) {
        <p>Item nbr {{ item.id }} is {{ item.name }}
    }

@defer

    @defer (on viewport) {
        <!-- defers loading once on viewport -->
        <component />
    } @placeholder (minimum 2s) {
        <p>Displays for minimum of 2s BEFORE the component is loaded</p>
    } @loading (minimum 2s, after 3s) {
        <p>Displays WHILE the component is loading</p>
    }

inject()

    // in addition to injecting a service into the constructor
    // the inject() is used
    userSvc = inject(UserService);

pipes

    all pipes used must be imported

HttpClient

    Because there is no 'import' in services, to import HttpClient for user
    by services requires the following changes to `app.config.ts`:

    1) Add `import { provideHttpClient} from '@angular/common/http';``
    2) Add `provideHttpClient()` to providers