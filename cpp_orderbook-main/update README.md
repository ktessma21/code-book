📈 High-Performance C++ Order Book
Summary
This project implements an ultra-high-performance C++ order book capable of processing over 5 million orders per second per CPU core. It supports both limit and market orders, and uses fixed-point arithmetic via cpp_fixed to maintain high precision and speed.

The design is inspired by go-trader and integrates seamlessly with broader trading systems such as cpp-trader.

🛠 Build Instructions
To build the project:

Clone cpp_fixed at the same directory level.

Install the Boost Unit Testing Framework.

Run make (uses Clang by default). For GCC, use Makefile.gcc.

🧪 Running Tests
Run all unit tests using:

bash
Copy
Edit
make run_tests
📂 Usage
exchange.h — Public API

orderbook.h — Core single-threaded order book logic

⚙️ Performance Tuning
The PriceLevels implementation can be customized by editing the typedef in pricelevels.h.

Performance varies by container implementation (deque, vector, map, etc.) and price level depth (e.g., 10 vs. 1000 levels). Sample throughput ranges from 5M–10.5M orders/sec per core depending on configuration.

For multithreaded benchmarks and profiling, refer to:

benchmark_test.cpp

benchmark_multithread_test.cpp

📊 Performance Snapshot
Insert performance: 5.5M – 10.5M ops/sec

Insert + match (30%): 4M – 8M ops/sec

Cancel performance: 4M – 8.5M ops/sec

With multiple instruments per core:

<50ns per insert → 22M+ orders/sec

<70ns per cancel → 13M+ cancels/sec

Performance is CPU-bound and scales well with additional cores, aided by lock-free data structures.

📌 Notes
This project is designed as a low-latency, memory-efficient order book engine for use in exchange and trading simulations. While tuned for speed, it prioritizes clean design and modularity, making it a flexible foundation for further experimentation or integration into more complete trading systems.
