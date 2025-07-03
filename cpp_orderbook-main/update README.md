# 🏦 High-Performance C++ Order Book Engine

## 📘 Overview

This project implements an ultra-high-performance **C++ financial exchange order book**, capable of handling over **5 million orders per second per CPU core**. It supports **limit** and **market** orders and is optimized for **low latency**, **memory efficiency**, and **multi-core scalability**.

Fixed-point arithmetic is handled via [cpp_fixed](https://github.com/robaho/cpp_fixed) to ensure precision without floating-point overhead.

> Inspired by concepts from [go-trader](https://github.com/robaho/go-trader) and designed for extensibility in high-frequency trading environments.

---

## ⚙️ Features

- 🔁 Supports limit and market orders
- 🚀 Ultra-low latency: ~5–10M ops/sec per core
- 🧮 Fixed-point math via `cpp_fixed`
- 🧵 Lock-free and CPU-bound performance scaling
- 🧩 Modular design for easy integration and extension 

---

## 🛠 Build Instructions

1. Clone [cpp_fixed](https://github.com/robaho/cpp_fixed) at the same directory level as this repo.
2. Ensure Boost Unit Test Framework is installed:  
   [Boost Test Docs](https://www.boost.org/doc/libs/1_87_0/libs/test/doc/html/index.html)
3. Build with:

```bash
make           # uses Clang by default
make -f Makefile.gcc   # for GCC
```

---

## ✅ Running Tests

```bash
make run_tests
```

All unit tests will be executed using the Boost test framework.

---

## 📂 Project Structure

| File | Description |
|------|-------------|
| `exchange.h` | Public API for interacting with the order book |
| `orderbook.h` | Core order book logic (single-threaded) |
| `benchmark_test.cpp` | Performance benchmarks |
| `benchmark_multithread_test.cpp` | Multi-core performance test suite |

---

## 📊 Performance

Tested on a 4.0 GHz Quad-Core Intel Core i7 (macOS):

| Operation | Throughput |
|----------|------------|
| Insert (no match, 10 levels) | 7.9M – 10.4M ops/sec |
| Insert + Match (30%) | 4M – 8M ops/sec |
| Cancel | 4.3M – 8.5M ops/sec |

Multicore scaling with one instrument per core achieves:

- ⚡ **22M+ orders/sec**
- ⏱ **<50ns per insert**
- 📉 **<70ns per cancel**

> Performance is highly dependent on price level depth and the chosen container (`vector`, `map`, `deque`, etc.). See `pricelevels.h` for configuration.

---

## 📌 Notes

This engine is built for experimentation and educational use in **quantitative finance**, **exchange simulations**, or **trading infrastructure prototypes**. It emphasizes **readable, clean design** while pushing system-level performance boundaries.

---

## 📎 Dependencies

- C++17+
- [Boost](https://www.boost.org/)
- [cpp_fixed](https://github.com/robaho/cpp_fixed)

---

## 📬 Contact

Feel free to fork, open issues, or contribute improvements.
