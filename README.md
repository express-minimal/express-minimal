# Eframix

![NPM Version](https://img.shields.io/npm/v/eframix)
![NPM Downloads](https://img.shields.io/npm/dy/eframix)
![NPM Type Definitions](https://img.shields.io/npm/types/eframix)
![NPM License](https://img.shields.io/npm/l/eframix)

A minimalistic [Node.js](https://nodejs.org/en) framework inspired by Express.js, offering core routing, middleware, and JSON body parsing features with zero dependencies. Ideal for lightweight HTTP server applications.

## Table of Contents

- [Installation](#installation)
- [Features](#features)
- [Quick Start](#quick-start)
- [Examples](#examples)
- [Contributing](#contributing)
- [Technical Committee (TC)](#technical-committee-tc)
- [License](#license)

---

## Installation

Install `eframix` from npm:

```bash
npm install eframix
```

## Features

- **Routing**: Support for `GET`, `POST`, `PUT`, and `DELETE` methods.
- **Middleware**: Add global and route-specific middleware.
- **Body Parser**: Built-in JSON body parser for handling incoming request data.
- **Lightweight**: Minimal footprint, built on Node's HTTP module for efficient handling.

## Quick Start

Get started with a basic setup:

```typescript
import Router from 'eframix';

const app = new Router();

app.use(app.bodyParser);

app.get("/", (req, res) => {
    res.writeHead(200, { "Content-Type": "text/plain" });
    res.end("Welcome to Eframix!");
});

app.post("/data", (req, res) => {
    res.writeHead(201, { "Content-Type": "application/json" });
    res.end(JSON.stringify({ received: req.body }));
});

app.startServer(3000, () => {
    console.log("Server is running on port 3000");
});
```

## Examples

### Basic Movie API

Below is a sample structure for a movie API using `eframix`.

```typescript
import { addMovie, getAllMovies, getMovieByID, updateMovie, deleteMovie } from './routes/movieRoutes';
import Router from 'eframix';

const app = new Router();

app.use(app.bodyParser);

app.get("/api/movies", getAllMovies);
app.get("/api/movies/:id", getMovieByID);
app.post("/api/movies", addMovie);
app.put("/api/movies/:id", updateMovie);
app.delete("/api/movies/:id", deleteMovie);

app.startServer(5001, () => {
    console.log("Server is running on port 5001");
});
```

## Contributing

We welcome contributions from the community! To get started:
1. Fork the repository on [GitHub](https://github.com/efraimnabil/eframix).
2. Create a branch with your feature or fix.
3. Open a pull request with a detailed description.

Please follow the coding standards and conventions in the repository.

## Technical Committee (TC)

The Technical Committee (TC) oversees the direction of `eframix`. Current members include:
- [Efraim Nabil](https://github.com/efraimnabil)
- [Mina Magdy](https://github.com/MiinaMagdy)

For more information on contributing, please visit our [GitHub](https://github.com/efraimnabil/eframix) repository.

## License

This project is licensed under the MIT License.
