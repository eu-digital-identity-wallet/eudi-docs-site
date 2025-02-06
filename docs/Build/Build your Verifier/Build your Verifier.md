# Build your Verifier

## Overview

This is a WEB UI that provides functionality to interact with the Verifier/RP trusted end-point implemented [here](https://github.com/eu-digital-identity-wallet/eudi-srv-web-verifier-endpoint-23220-4-kt){:target="_blank"}.
Another way to think of this application is that it represents an arbitrary application that wants to delegate to the trusted end-point the burden of
interacting with a wallet using OpenId4VP.
The project was generated with [Angular CLI](https://github.com/angular/angular-cli){:target="_blank"} version 19.1.4.

## Development server

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The application will automatically reload if you change any of the source files.

## Code scaffolding

Run `ng generate component component-name` to generate a new component. You can also use `ng generate directive|pipe|service|class|guard|interface|enum|module`.

## Build

Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory.

## How to run for development

You need npm (node version 18.15.0) and [Angular CLI](https://github.com/angular/angular-cli){:target="_blank"} installed on your machine.

In order to run Verifier UI run the following commands:

```bash
npm install
ng serve --proxy-config src/proxy.conf.json
```
The above command utilizes [proxy.conf.json](src/proxy.conf.json){:target="_blank"} that proxies the calls to the expected verifier backend service.
Update this file if you want your Verifier UI to point to a locally running verifier backend service.

You can access the application at [http://localhost:4200](http://localhost:4200){:target="_blank"} 
