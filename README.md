# 🤖 Bop: The Raspberry Pi Robot Pet

**Bop** is a distributed, event-driven robot pet powered by Raspberry Pi. Built with modularity and fun in mind, Bop is capable of **hearing**, **thinking**, **reacting**, and **interacting** with the world around him — all driven by Python microservices and hardware components.

He is very much a WIP right now. Parts are untested, probably don't work and will change or break often. Stability will
come with a Beta release when the MVP feels ready and as I get time to work on it.

That said, feel free to clone the repo's and have a play.

This project is my first journey into Python, AI, electronics and robotics, so feedback is very much welcomed!



---

## 🧠 Project Overview

Bop is designed as a multi-device system where each Pi (or machine) is responsible for a specific role:

| Component    | Responsibility                                   |
|--------------|--------------------------------------------------|
| `bop_sense`  | Handles input: microphone, camera, etc.          |
| `bop_brain`  | Processes input and routes commands intelligently |
| `bop_body`   | Handles output: screen display, motor control, etc. |
| `bop_common` | Shared DTOs, constants, and communication layers  |

Communication between these components happens via MQTT or AMQP, with support for both real and mocked message brokers for testing.

It is designed to run on 3 x Raspberry Pi computers. It is not fully tested now, is very much a WIP
and is a fun side project of mine.

The Pi running the bop_brain codebase should be a min of 8GB, as there is some planned ONNX inference planned. This is also
where the bulk of the work is carried out.

---

## 🧩 Codebase Structure

### `bop_sense`
- Voice recognition via `speech_recognition` and Google API
- Camera capture using PiCamera or USB
- Publishes input data as events

### `bop_brain`
- Consumes input events
- Runs command resolution, face recognition, etc.
- Dispatches meaningful events for Bop to act on

### `bop_body`
- Displays messages on a screen (using `pygame`)
- Moves components like wheels or arms (future)
- Plays sound or performs visual feedback

### `bop_common`
- DTOs for structured messaging
- Interfaces for swappable implementations
- Shared utility code and config management

---

## 🛠️ Hardware Support (current - more planned)

| Feature        | Hardware Required              |
|----------------|--------------------------------|
| Voice Input    | USB Microphone |
| Image Capture  | PiCamera or USB Webcam         |
| Display        | HDMI Screen                    |


Bop was originally developed using the **Raspberry Pi Edukit 3: Robotics** kit, which includes motors, sensors, and a breadboard — perfect for learning and experimenting.

---

## 📡 Communication

Bop uses **message queues** to connect the components:

- ✅ **MQTT** support (default for lightweight messaging)
- 🐇 **AMQP** support for advanced routing
- 🧪 **Mock** publisher for test environments

---

## 🚀 Goals

- Create a friendly, extendable robot pet for fun, learning, or companionship
- Support multiple hardware configurations
- Learn lots about robots, AI and Python
---

## 📖 Future Documentation

This repository (`bop_docs`) will serve as the central knowledge base for:

- Setup guides and installation
- Developer documentation
- Command reference
- Contribution guide
- Hardware schematics

---

Made with ❤️ and Python.
