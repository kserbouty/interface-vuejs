# Frontend Vue.js 2

## Table of Contents

- [Frontend Vue.js 2](#frontend-vuejs-2)
  - [Table of Contents](#table-of-contents)
  - [Introduction](#introduction)
    - [Features](#features)
  - [Installation](#installation)
    - [Requirements](#requirements)
    - [Docker Installation](#docker-installation)
    - [Local Installation](#local-installation)
  - [Authors](#authors)
  - [License](#license)

## Introduction

Graphical interface connecting to the [Symfony API](https://github.com/kserbouty/backend-symfony) to manage its resources.

### Features

- Manage resources from API endpoints.
- Asynchronous requests with Axios.

## Installation

### Requirements

- [Symfony API](https://github.com/kserbouty/backend-symfony) running on port 8000
- Node >=16 with npm
- Docker (optional)

### Docker Installation

Build the image

```bash
docker build -t vue-demo .
```

Run your container on <http://localhost:8080>

```bash
docker run -it -p 8080:8080 --rm --name vue-demo vue-demo
```

### Local Installation

Install the dependencies

```bash
npm install
```

Run your server on <http://localhost:8080>

```bash
npm run serve
```

## Authors

Karim Serbouty

## License

[MIT License](./LICENSE.md)
