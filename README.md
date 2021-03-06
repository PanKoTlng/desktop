<img src="http://slack.stoplight.io/badge.svg">

# StopLight API Designer App

This is a wrapper app around the StopLight API Designer, that makes certain native functionality available to it. It also starts and manages an instance of the StopLight API Proxy.

### Setup

##### Dependencies
- StopLight API Designer
- Node >= 4.1.0

##### OS X / Linux

Install the dev deps listed above.

```bash
npm install && cd app && npm install && cd ..
npm start
```

##### Building

Builds will be located in the /dist folder.

```bash
npm run build:production
```

##### Code Signing

This is useful: https://mkaz.tech/code-signing-a-windows-application.html.

CSC_LINK, WIN_CSC_LINK, and CSC_KEY_PASSWORD must be set in your environment. For example:

Our mac cert is provided by apple developer program. Install it into your keychain, export it to .p12 from the keychain/login screen.

Our windows cert is provided by Digicert. Install it into your keychain, export it to .p12 from the keychain/login screen.

```bash
export CSC_LINK="~/Documents/Credentials/evario-cert/cert-mac.p12"
export WIN_CSC_LINK="~/Documents/Credentials/evario-cert/cert.p12"
export CSC_KEY_PASSWORD="123"
```

##### Releasing

GH_TOKEN needs to be set in your environment.

Code signing needs to be setup.

1. Increment app/package.json version property.

```bash
npm run release:production
```

### Project Structure

Notable directories and files:

##### app/main.js

The entry point to the application. This is run when it starts. This file opens a new Electron window, loading either a local instance of the API Dashboard (in development), or a remote instance of the dashboard.

##### app/browser-setup.js

This is a pre-script, run before the remote dashboard is loaded. Here, we set a global Electron variable, making several native node modules available to the dashboard.
