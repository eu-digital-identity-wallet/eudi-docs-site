# Steps to Build your Verifier

## Development Server

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The application will automatically reload if you change any of the source files.

## Code Scaffolding

Run `ng generate component component-name` to generate a new component. You can also use `ng generate directive|pipe|service|class|guard|interface|enum|module`.

## Build

Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory.

## Run your Verifier

You need npm (node version 18.15.0) and [Angular CLI](https://github.com/angular/angular-cli){:target="_blank"} installed on your machine.

To run Verifier UI run the following commands:

```bash
npm install
ng serve --proxy-config src/proxy.conf.json
```
The above command utilizes [proxy.conf.json](https://github.com/eu-digital-identity-wallet/eudi-web-verifier/blob/main/src/proxy.conf.json){:target="_blank"} that proxies the calls to the expected verifier backend service.
Update this file if you want your Verifier UI to point to a locally running verifier backend service.

You can access the application at `http://localhost:4200`. 


## Run Tests

Run `ng test` to execute the unit tests via [Karma](https://karma-runner.github.io){:target="_blank"}.

Run `ng e2e` to execute the end-to-end tests via a platform of your choice. To use this command, you need to first add a package that implements end-to-end testing capabilities.

To get more help on the Angular CLI use `ng help` or go check out the [Angular CLI Overview and Command Reference](https://angular.io/cli){:target="_blank"} page.

