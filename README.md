# paping

TCP port ping utility. Tests connectivity to a host on a specific TCP port and reports latency, similar to how ICMP ping works - but over TCP.

## Usage

```
paping <host> -p <port> [options]
```

### Options

| Flag | Description |
|---|---|
| `-p`, `--port N` | TCP port to probe *(required)* |
| `-c`, `--count N` | Stop after N probes (default: run forever) |
| `-t`, `--timeout N` | Connection timeout in ms (default: 1000) |
| `--nocolor` | Disable colored output |
| `-h`, `--help` | Show help |

### Examples

```
paping google.com -p 80
paping 192.168.1.1 -p 443 -c 10
paping myserver.local -p 3306 -t 500 --nocolor
```

### Output

```
paping v1.0 - Copyright (c) 2026 Oliver (arch3r.eu)

Connecting to google.com [142.250.130.138] on TCP port 80:

Connected to 142.250.130.138: time=2.48ms protocol=TCP port=80
Connected to 142.250.130.138: time=2.91ms protocol=TCP port=80
Connected to 142.250.130.138: time=2.87ms protocol=TCP port=80

Connection statistics:
  Probed = 3, Connected = 3, Failed = 0 (0.00%)
Approximate connection times:
  Minimum = 2.48ms, Maximum = 2.91ms, Average = 2.75ms
```

## Building

Requires CMake 3.20+ and a C++20 compiler (MSVC 2022, GCC 12+, or Clang 15+).

```
cmake -B build
cmake --build build --config Release
```

The binary is placed at `build/Release/paping.exe` on Windows or `build/paping` on Linux.

## Platform support

- Windows 10 / 11 (x64)
- Linux

## License

Copyright (c) 2026 Oliver — [arch3r.eu](https://arch3r.eu)
