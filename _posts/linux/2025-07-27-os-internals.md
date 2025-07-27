---
title: "OS Internals"
date: 2025-07-27 00:00:00 +0530
categories: [linux]
tags: [linux]
---

---

# OS Internals
---

#### Resources:
- [Top 100+ Linux Interview Questions and Answers (2025) - Naukri Code 360](https://www.naukri.com/code360/library/linux-interview-questions)

---

### What is the role of the `Linux Kernel`?

The `Linux Kernel` is the core component of the Linux OS that manages hardware resources like CPU, memory, and I/O devices. It provides essential services to applications through system calls and manages processes, memory, file systems, and hardware devices.

---

### What is a `system call` in Linux?

A `system call` is a mechanism that allows user-space applications to request services from the kernel. Examples include file manipulation (open, read, write), process control (fork, exec), and inter-process communication (pipe, shmget).

---

### What is the difference between `user mode` and `kernel mode` in Linux?

- `User mode`: The CPU runs user applications with restricted access to system resources.
- `Kernel mode`: The CPU runs in privileged mode, allowing full access to system hardware and resources. Transitions between these modes happen via system calls.

---

### What are `kernel modules`, and how do you manage them?

Kernel modules are pieces of code that can be dynamically loaded and unloaded into the Linux kernel at runtime. They extend kernel functionality (e.g., device drivers).

- `Load module`: insmod module_name.ko
- `Unload module`: rmmod module_name
- `List modules`: lsmod

---

### Explain process scheduling in the Linux kernel.

The Linux kernel uses the `Completely Fair Scheduler (CFS)`, which distributes CPU time fairly among processes based on priority and workload. It supports real-time and normal processes, ensuring each process gets a fair share of CPU time.

---

### What is the difference between a process and a thread in Linux?

- `Process`: An independent program that runs in its own memory space with its own resources.
- `Thread`: A lightweight execution unit within a process, sharing the process's memory and resources, making it easier to share data between threads.

---

### How does the Linux kernel handle memory management?

The Linux kernel handles memory through

- `paging` (splitting memory into pages),
- `segmentation` (splitting memory into logical divisions like code, data, and stack), and
- `virtual memory` (allowing processes to use more memory than physically available by swapping pages between RAM and disk).

---

### What is an `inode` in Linux?

An `inode` is a data structure that stores information about a file, such as file size, ownership, permissions, and data block pointers. It does not store the file name, which is managed separately in the directory structure.

---

### What is the purpose of the `fork()` system call?

The `fork()` system call creates a new process by duplicating the calling process. The child process gets its own PID but shares the same code and memory structure initially as the parent. It returns 0 to the child process and the child’s PID to the parent.

---

### How does the Linux kernel handle interrupts?

The kernel uses an `Interrupt Request (IRQ)` system. When a device needs CPU attention, it sends an interrupt. The kernel's interrupt handler responds to the request, processes the interrupt, and communicates with the device. After handling, the CPU resumes the previous task.

