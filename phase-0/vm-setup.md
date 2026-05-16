# VM Setup and Environment Understanding

## What a virtual machine is

A virtual machine is a simulated computer running inside my real computer. 

It behaves like a separate system with:
- its own operating system
- its own filesystem
- its own processes
- isolated memory space

---

## Why NAT networking is used

The VM uses NAT networking, which allows internet access through the host machine. 

This means:
- the VM is not directly exposed to the local network
- traffic is routed through the host system

This increases isolation and safety.

---

## Why snapshots matter

Snapshots allow saving the entire state of the VM. If something breaks, the system can be restored instantly. This is important for experimentation and learning.

---

## Why shared clipboard is disabled

Shared clipboard and drag-and-drop increase integration between host and VM. Disabling them increases isolation and reduces accidental host exposure. 

---

## Key understanding

The VM is not just software running inside Windows. It is a full simulated hardware environment with its own operating system layer.

---

## Core insight

This setup creates a safe environment to:
- experiment with system behavior
- test code
- observe crashes
- learn low-level concepts without risking the host system
