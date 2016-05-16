# angular-2-local-storage

LocalStorageService for Angular 2 with mostly the same API (and most of the code) from [angular-local-storage](https://github.com/grevory/angular-local-storage)

## Differences:

* No events broadcast on $rootScope - LocalStorageService exposes observables for `errors$`, `removeItems$`, `setItems$` and `warning$` if you really need something to happen when something happens.
* The `bind` function doesn't work anymore (there is a stub so this can still be a drop-in, but it'll do nothing).

## Usage:

### With SystemJS:

Add the following to the `map`:

```
'angular-2-local-storage': 'vendor/angular-2-local-storage/dist/'
```

### In your app:

First you need to configure the service:

```typescript
import { LocalStorageService, LOCAL_STORAGE_SERVICE_CONFIG } from './LocalStorageService';

// Create config options (see ILocalStorageServiceConfigOptions) for deets:
let localStorageServiceConfig = {
    prefix: 'my-app',
    storageType: 'sessionStorage'
};
// Provide the config to the service:
const LOCAL_STORAGE_CONFIG_PROVIDER: Provider = provide(LOCAL_STORAGE_SERVICE_CONFIG, {
    useValue: localStorageServiceConfig
});

// Use the provider:
bootstrap(AppComponent, [LocalStorageService, LOCAL_STORAGE_CONFIG_PROVIDER]);
```

Then you can use it in a component:

```typescript
import { LocalStorageService } from 'angular-2-local-storage/angular-2-local-storage';

@Component({
    // ...
})
export class SomeComponent {
    constructor (
        private localStorageService: LocalStorageService
    ) {
        // YAY!
    }
}

```
