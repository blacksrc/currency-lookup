# Currency lookup

Look for Currencies.

## Installation Guide

Clone the project.

```sh
git clone git@github.com:blacksrc/currency-lookup.git
```

1. Open `currency-lookup/backend` directory.

2. Install dependencies.

```sh
$ yarn install
```

3. Copy `.env.example` file to `.env`. The latest env variables will be added to `.env.example`. So do not delete or rename this file. Then open the copied file and add your environment variables:

```env
# application secret key
APP_SECRET=SomeComplexStupidStringWhichIsHardToGuess
# application running port
APP_PORT=3001

# countries api url and version
COUNTRIES_URL=https://restcountries.eu/rest
COUNTRIES_VERSION=v2

# currency exchange rate api url and endpoint and api key
EXCHANGE_RATE_URL=http://data.fixer.io/api
EXCHANGE_RATE_ENDPOINT=latest
EXCHANGE_RATE_API_KEY=

# rate limiting configuration
# MAX_REQUEST_COUNT => maximum possible requests per MAX_REQUEST_TIME
# MAX_REQUEST_TIME => in minute
MAX_REQUEST_COUNT=30
MAX_REQUEST_TIME=1
```

It will be look like something like this:

```env
APP_SECRET=torasaristkebamaforoonemiayad
APP_PORT=3001

COUNTRIES_URL=https://restcountries.eu/rest
COUNTRIES_VERSION=v2

EXCHANGE_RATE_URL=http://data.fixer.io/api
EXCHANGE_RATE_ENDPOINT=latest
EXCHANGE_RATE_API_KEY=someapikey

MAX_REQUEST_COUNT=30
MAX_REQUEST_TIME=1
```

> Consider adding `EXCHANGE_RATE_API_KEY` getting from `https://fixer.io/`

4. Run project in development mode.

```sh
$ yarn start
```

5. Open `currency-lookup/frontend` directory.

6. Install dependencies.

```sh
$ yarn install
```

7. Copy `.env.development.local.example` file to `.env.development.local`. The latest env variables will be added to `.env.development.local.example`. So do not delete or rename this file. Then open the copied file and add your environment variables:

```env
# Application running port like: 3002
PORT=

# HOST => API endpoint host without "/" in the end like: http://localhost
REACT_APP_API_HOST=
# PORT => API endpoint port like: 3001
REACT_APP_API_PORT=
```

It will be look like something like this:

```env
# Application running port like: 3002
PORT=3002

# HOST => API endpoint host without "/" in the end like: http://localhost
REACT_APP_API_HOST=http://localhost
# PORT => API endpoint port like: 3001
REACT_APP_API_PORT=3001
# TOKEN => API endpoint token generated by backend endpoint: http://localhost:3001/auth/login
REACT_APP_API_TOKEN=sometoken
```

8. To get a valid `REACT_APP_API_TOKEN` you should make a request to this url while backend server is running:

```code
http://localhost:3001/auth/login
```

9. Copy and paste the token in the `.env.development.local` file.

10. Run project in development mode.

```sh
$ yarn start
```

## Project's structure

`src` directory contains some important sub directories which is explained below the tree view:

```code
.
├── app
│   ├── api
│   ├── assets
│   ├── components
│   ├── config
│   ├── index.js
│   ├── layouts
│   ├── locales
│   ├── pages
│   ├── redux
│   ├── theme
│   └── utils
```

`api`:

> Contains the api request functionality. There is a `_API.js` files which hold `API` class to implement a layer of abstraction for making request. So, any token or header variable or maybe refresh token functionality will be implemented there. For each model endpoint, There is a need to create a new file like `Country.js` which will be used in different parts of the code to make request.

`assets`

> Contains the static assets like images or styles.

`components`

> Contains all components that is being used in the application.

`config`

> Contains all application configuration. Basically this folder exits to read all environment variables from env file.

`layouts`

> Contains all layouts of application like header, footer, main, etc. The layout components are not meant to be for implementing functionality. They are just here to load component into pages and construct the page structure.

`locales`

> Contains all translations. To add new translations you need to just add another file and import it in `index.js`. Consider changing the key (`se-SE`) in the translation file.

`pages`

> Contains all pages in the application. If there is any router implemented. It should load this components.

`redux`

> Contains all redux functionalities.

`theme`

> Contains theme variables, colors, break pints, fonts, etc. Adding new themes need to be implemented in `index.js` file.

`utils`

> Contains all utility functions. If number of functions increased during the development, it can be decoupled in small files or maybe classes.

## Todo

Things need to be done.

- [x] Backend functionality.
- [x] Frontend functionality.
- [x] Localization.
- [x] Review inline code comments.
- [ ] Create component visual documentation (Storybook).
- [ ] Unit tests (Jest / Mocha / Chai).
- [ ] e2e tests (Cypress).
- [ ] Dockerizing.
