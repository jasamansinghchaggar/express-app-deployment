# Docker

A small Node.js + Express application that uses the built-in `cluster` module to start one worker per CPU core.

## What it does

- Starts a master process that forks a worker for each available CPU core.
- Runs an Express server in each worker.
- Exposes a few simple routes for testing and experimentation.

## Requirements

- Node.js 18 or newer
- npm

## Install

```bash
npm install
```

## Run

Start the app in normal mode:

```bash
npm start
```

Start the app in watch mode during development:

```bash
npm run dev
```

The server listens on port `3000` by default.

## Routes

- `GET /` returns `Hello World`
- `GET /host` returns the hostname of the machine running the worker
- `GET /cpu` runs a CPU-heavy loop before responding with `Hello World`

## Project Structure

```text
package.json
src/
	bin.js   # cluster entry point
	index.js # Express app definition
```

## Notes

- The `/cpu` route is intentionally expensive and is useful for observing how clustering distributes load across workers.
