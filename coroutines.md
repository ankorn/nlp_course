# Python Concurrency Cheat Sheet

## Core Concepts
- **Concurrency vs Parallelism**: Concurrency = managing multiple tasks (can be single-core); Parallelism = executing tasks simultaneously (needs multiple cores).
- **GIL (Global Interpreter Lock)**: Only one thread executes Python bytecode at a time → threads are **never truly parallel for CPU-bound work**, only good for **I/O-bound** tasks.
- **Rule of thumb**: I/O-bound → threads or asyncio; CPU-bound → multiprocessing.

---

## Threads (`threading`)
- Threads share the same memory space (shared state, but race conditions possible).
- Use `threading.Thread(target=func, args=...)` or `ThreadPoolExecutor` from `concurrent.futures`.
- Best for: blocking I/O (network requests, file reads) in a few concurrent tasks.
- GIL released during I/O → threads still help for I/O-bound work.
- **Synchronization primitives**: `Lock`, `RLock`, `Semaphore`, `Condition`, `Event`, `Barrier`.
- `threading.local()` for thread-local storage.
- `queue.Queue` is thread-safe — prefer it over locks for producer/consumer.
- Beware deadlocks; always acquire locks in consistent order, use `with lock:` context manager.

---

## Processes (`multiprocessing`)
- Separate memory space → true parallelism, bypasses the GIL.
- Best for: CPU-bound work (number crunching, image processing).
- `Process` class or `ProcessPoolExecutor`.
- Data passed between processes must be **pickled** → costly for large data.
- Slower to create than threads; heavier memory footprint.
- `Pool.map` / `Pool.apply_async` for distributing work.
- Inter-process communication: `Queue`, `Pipe`, `Value`, `Array` (shared memory), `Manager` (shared data structures).
- On Windows/macOS, must guard entry point with `if __name__ == '__main__':` (spawn method).
- Watch out for zombie processes → use `.join()`.

---

## Asyncio (`async`/`await`)
- **Single-threaded, single-process** cooperative multitasking using an event loop.
- Best for: **massive** concurrency of I/O-bound tasks (thousands of connections).
- `async def` defines a coroutine; it doesn't run until awaited or scheduled.
- `await` yields control back to the event loop (cooperative — won't yield during CPU work).
- `asyncio.run(main())` entry point; `asyncio.create_task()` to run coroutines concurrently.
- `asyncio.gather()` for running many coroutines concurrently and collecting results.
- `asyncio.sleep()` is the async equivalent of `time.sleep()` — use it, never block calls!
- Never call **blocking** code (requests, time.sleep, file I/O) inside async code → it freezes the whole loop. Use `asyncio.to_thread()` to offload blocking calls.
- `aiohttp`, `asyncpg`, `aiosqlite` — async libraries for networking/DB.
- Concurrency primitives: `asyncio.Lock`, `Semaphore`, `Event`, `Queue`.

---

## Trap Questions / Gotchas
- Q: *Why do threads exist if the GIL blocks parallel execution?* → A: GIL is released during I/O ops, so threads still help for I/O-bound work.
- Q: *When would you mix asyncio and threads?* → A: Offload blocking calls with `asyncio.to_thread()`; combine with `ProcessPoolExecutor` via `loop.run_in_executor()` for CPU-bound chunks in async apps.
- `asyncio.gather(return_exceptions=True)` to prevent one failure from cancelling everything.
- `asyncio.create_task()` without keeping a reference → task may be garbage collected mid-execution.
- In threads, even `x += 1` is not atomic → always guard shared state with locks.
- `daemon=True` threads die when main thread exits.

## One-Liner Answers
- **Threads**: "Shared memory, GIL-limited, great for a handful of I/O tasks."
- **Processes**: "True parallelism, isolated memory, pickle overhead, great for CPU-bound work."
- **Asyncio**: "Cooperative single-threaded concurrency, event loop, scale to thousands of I/O tasks."