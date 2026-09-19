## Andreas Sjögren

Backend and platform engineer — .NET, distributed simulation, containers.

📫 **[sjogrenandreas@live.se](mailto:sjogrenandreas@live.se)**

**[polyglot-tick-engine](https://github.com/Edes0/polyglot-tick-engine)** — engineering write-up of
Screeps2, a game server I have been building solo for the past year.

It is an authoritative tick engine: a .NET 10 backend that advances a shared world once per second
and, on every tick, executes arbitrary untrusted player code in Docker containers across **24
languages** (75 images), under a CPU budget, a hard kill and a memory ceiling — where one player's
crash or infinite loop can never delay another player's results, or the tick itself.

What the write-up covers:

- **Sandboxed polyglot execution** — 24 language runtimes behind one interface, per-language
  resource limits, fault classification and container recovery
- **A persistent-worker protocol** — versioned JSON-line messaging over two transports, with the
  enqueue-time snapshot that closes a race against tick advancement
- **Determinism as a tested invariant** — replay tests asserting byte-equal output, and a four-level
  total order over every contested decision
- **Instrument-first performance work** — including the time I wrote down the wrong root cause and
  the allocation profiler corrected it by a factor of thirty-four

Roughly 80k lines of backend C#, 1,350 tests, and a Unity 6 client that renders the deltas.

*The engine source is private; the write-up is not.*
