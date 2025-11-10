# Panther Scan (PP Scanner)

**Panther Scan** High-performance multithreaded port scanner written in C.

Fast, lightweight, and designed for bulk discovery and banner grabbing.

---

## Features

* Multithreaded (pthreads) for high concurrency
* Target formats: single IP, ranges (`192.168.1.1-255`), CIDR (`10.0.0.0/24`), or file input
* Flexible ports: single, lists and ranges (`22,80,8000-8100`)
* Banner grabbing (`-g`) (best-effort)
* Machine-friendly output: CSV or JSON
* Configurable threads, timeouts, and retries

---

## Quick Start

run:

```bash
./panther 192.168.1.1 -p 22,80 -t 100 -T 300 
```

---

## CLI

```
./panther <target|range|cidr> [OPTIONS]

Options:
  -h, --help           Show this help
  -p, --ports <str>    Ports to scan (e.g. 22,80,100-200)
  -f, --file <path>    File with targets (one per line)
  -t, --threads <n>    Number of worker threads (default: 100)
  -T, --timeout <ms>   Connection timeout in milliseconds (default: 500)
  -r, --retries <n>    Number of connection retries (default: 1)
  -g, --grab           Attempt banner grabbing on open ports
  -o, --output <file>  Write results to file
  -v, --verbose        Verbose progress
  --no-resolve         Skip DNS resolution
```

---

## Example Usage

* Single host:

```bash
./panther 192.168.1.10 -p 22,80,443 -t 50 -T 300
```

* CIDR, ports 1-1024, banner grab:

```bash
./panther 192.168.1.0/24 -p 1-1024 -g -t 200 -T 500 -o results.txt
```

* Targets from file:

```bash
./panther -f targe
```
