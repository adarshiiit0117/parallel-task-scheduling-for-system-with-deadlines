# 🚀 Parallel Dependency-Aware Task Scheduler (C++ / OpenMP)

A **high-performance task scheduling system** implemented in **C++**, supporting both **sequential** and **parallel** execution models.  
The scheduler assigns tasks to workers while respecting **task dependencies**, **deadlines**, and **resource constraints**, and evaluates **performance trade-offs** between different parallelization strategies.

This project explores **real-world scheduling concepts** inspired by **CPU/GPU workload scheduling**.

---

## 📌 Key Features

- 📅 Deadline-aware scheduling (Earliest Deadline First)
- 🔗 Dependency-aware execution (topological constraints)
- ⏱️ Resource-constrained assignment (per-worker hour limits)
- ⚙️ Sequential baseline implementation
- 🚀 Parallel scheduler using OpenMP
- 📊 Performance benchmarking and comparison
- 🧠 Exploration of synchronization strategies (`critical`, `atomic`, `reduction`)

---

## 🧠 Scheduling Model

1. Tasks are sorted by deadline
2. Scheduling proceeds day-by-day
3. Each worker:
   - Pulls eligible tasks
   - Respects dependency completion
   - Cannot exceed daily hour limits
4. Assigned tasks are immediately marked completed, unlocking dependent tasks
5. Scheduling terminates when no further progress is possible

---

## ⚡ Parallelization Strategy

The parallel implementation uses **OpenMP** to assign tasks concurrently across workers.

### Design Highlights
- Parallelized across workers (members)
- Uses local computation with controlled synchronization
- Avoids naïve shared-state mutation
- Uses `reduction` to safely aggregate scheduling progress
- Demonstrates correctness vs performance trade-offs

This design closely mirrors **GPU scheduling models**, where multiple execution units pull work from a shared queue.

---

## 🧪 Implementations

| Version | Description |
|------|------------|
| Sequential Scheduler | Baseline single-threaded implementation |
| Parallel OpenMP Scheduler | Optimized parallel version (main implementation) |


