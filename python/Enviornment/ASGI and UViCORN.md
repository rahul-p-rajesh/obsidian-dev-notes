
### What is ASGI?
1. ASGI = **Asynchronous Server Gateway Interface**.
2. It is an **interface/specification**, i.e., a contract that defines how an async Python web app and server should communicate.
3. It is designed for asynchronous Python applications to efficiently handle many simultaneous connections with low latency.
4. It is especially useful for **high-concurrency**, I/O-bound workloads.

### What is a  **ASGI app**
1. An **ASGI app** is the actual code object that follows the ASGI interface.
2. It is provided by frameworks like FastAPI, Django (ASGI mode), and Starlette.
3. It exposes an async callable (scope, receive, send) that the server invokes for each connection/event.

### What is uvicorn
1. [uvicorn](https://www.uvicorn.org/) is an **ASGI server runtime** that implements the ASGI specification.
2. uvicorn is one ASGI server option, along with hypercorn and daphne.
3. It is  required because **ASGI is only a specification**, not a network server.
4. FastAPI gives you an ASGI app object (app) plus framework-level request/response handling, while an ASGI server (like uvicorn, hypercorn or daphne) handles sockets, HTTP/WebSocket protocol details, the event loop, connection management, timeouts, keep-alive, and worker orchestration. ^cabab0
5. uvicorn ≈ Node’s HTTP server/runtime layer when you use node: http or a server process.
	- Node.js/Bun ≈ the entire JavaScript runtime (language + standard library + event loop + package system + many APIs).
	- FastAPI (or Starlette/Django ASGI) ≈ web framework like Express/Nest on top.

