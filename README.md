# Queueing System Simulator 🚦📊

A fully functional **Queueing System Simulator** built in **Dart**, modeling deterministic and probabilistic processes to evaluate system performance based on **event wait times**.

---

## 🔍 Project Overview

This simulator emulates a real-world queueing system — such as a grocery checkout line or CPU event handler — by tracking incoming events and computing how long each event waits before it is serviced. It supports:

- 🟩 **Singleton processes** (one-time fixed events)  
- 🔁 **Periodic processes** (fixed-interval events)  
- 🎲 **Stochastic processes** (randomly timed events based on exponential distribution)

It computes detailed **per-process** and **aggregate statistics** like:
- Total wait time
- Average wait time
- Number of events serviced

---

## 🧠 Motivation

This project was built to strengthen my understanding of:

- Event-driven architecture  
- Simulation modeling  
- Probability distributions  
- Performance metrics and queueing theory  
- Dart programming, YAML configs, and CLI tools

---

## 📁 Features

- ⌛ **Event Queueing**: FIFO-based event processing with real-time wait calculations  
- 📋 **YAML-Based Configurations**: Easily define process types and parameters  
- 🎲 **Support for Exponential Distributions**: Realistic modeling of stochastic behavior  
- 🖨️ **Simulation Trace Output**: Optional verbose Gantt-style log of event execution  
- 📊 **Statistical Summary Reports**: Total and per-process wait time breakdown  

---

## ⚙️ Technologies Used

- Dart 💙  
- YAML for configuration input  
- CLI argument handling (`args` package)  
- Custom random sampling from Exponential Distribution

---

## ▶️ How to Run the Simulator

### ✅ Prerequisite

- Dart SDK installed

### 🟢 Run Basic Simulation
```bash
dart run bin/main.dart -c conf/sim1.yaml
```

### 🟡 Run With Verbose Simulation Trace
```bash
dart run bin/main.dart -c conf/sim1.yaml -v
```

> 📝 Use `-c` to specify your YAML config file  
> 🔍 Use `-v` for a detailed simulation trace of the queue

---

## 🛠️ Sample Configuration (YAML)

```yaml
Computation:
  type: singleton
  duration: 50
  arrival: 10

Timer interrupt:
  type: periodic
  duration: 10
  interarrival-time: 25
  first-arrival: 0
  num-repetitions: 3

I/O request:
  type: stochastic
  mean-duration: 10
  mean-interarrival-time: 25
  first-arrival: 5
  end: 150
```

---

## 🧾 Sample Output

```markdown
# Simulation trace

t=0: Timer interrupt, duration 10 started (arrived @ 0, no wait)
t=10: I/O request, duration 18 started (arrived @ 5, waited 5)
t=28: Computation, duration 50 started (arrived @ 10, waited 18)
t=78: Timer interrupt, duration 10 started (arrived @ 25, waited 53)
t=88: I/O request, duration 22 started (arrived @ 49, waited 39)
t=110: Timer interrupt, duration 10 started (arrived @ 50, waited 60)
t=120: I/O request, duration 6 started (arrived @ 104, waited 16)
t=126: I/O request, duration 13 started (arrived @ 118, waited 8)

--------------------------------------------------------------

# Per-process statistics

Computation:
  Events generated:  1
  Total wait time:   18
  Average wait time: 18.0

Timer interrupt:
  Events generated:  3
  Total wait time:   113
  Average wait time: 37.67

I/O request:
  Events generated:  4
  Total wait time:   68
  Average wait time: 17.0

--------------------------------------------------------------

# Summary statistics

Total num events:  8
Total wait time:   199.0
Average wait time: 24.875
```

---

## 🧠 What I Learned

- Modeling real-world systems using **event-based simulations**  
- Implementing **event scheduling, sorting, and execution queues**  
- Working with **modular OOP design** (using abstract classes and polymorphism)  
- YAML parsing, command-line tools, and exponential distribution generation  
- Designing a **clean, testable codebase** in Dart

---


## ⭐️ If you found this project helpful or interesting, feel free to leave a ⭐ on GitHub!
