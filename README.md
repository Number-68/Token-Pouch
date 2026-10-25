# Token-Pouch

A personal password and TOTP vault written entirely in Rust.

This project started as a way for me to learn Rust while building something useful. The long-term goal is to create a small standalone hardware device that can securely store passwords and generate one-time authentication codes without relying on cloud services or third-party password manager applications.

## Project Goals

- Learn Rust through a real project.
- Build a secure offline password vault.
- Generate TOTP (Time-based One-Time Password) codes.
- Keep all sensitive information under local control.
- Design software that can eventually run on dedicated hardware.

---

## Planned Hardware

The intended target platform is an ESP32 microcontroller paired with a small OLED display.

Current ideas include:

- ESP32
- Monochrome OLED display
- Simple button-based navigation
- USB connectivity
- Offline-first design

The UI is intended to be extremely simple and pixel-focused. No touchscreen, animations, or unnecessary complexity. The goal is a functional and lightweight interface that feels more like a utility than an application.

---

## Current Development Plan

Development will begin as a desktop application written in Rust.

The desktop version will serve as:

- A simulator
- A testing environment
- A proof of concept

This allows the vault logic, encryption, storage, and TOTP functionality to be developed and tested before purchasing hardware.

Once the core functionality is stable, the project can be adapted to run on the ESP32 with minimal changes to the business logic.

---

## Planned Features

### Vault

- [ ] Create encrypted vault
- [ ] Unlock vault with master password
- [ ] Add password entries
- [ ] Edit password entries
- [ ] Delete password entries
- [ ] Search password entries

### TOTP

- [ ] Store TOTP secrets
- [ ] Generate 6-digit authentication codes
- [ ] Display remaining code lifetime

### Security

- [ ] Encrypted storage
- [ ] Password-based key derivation
- [ ] Secure handling of sensitive data
- [ ] Local-only storage

### Hardware

- [ ] OLED display support
- [ ] Button navigation
- [ ] ESP32 firmware
- [ ] Flash storage integration

---

## Architecture (Early Draft)

```text
+----------------+
|      UI        |
+--------+-------+
         |
         v
+----------------+
|  Vault Logic   |
+--------+-------+
         |
   +-----+-----+
   |           |
   v           v
Storage     TOTP
   |
   v
Crypto
```

The goal is to keep the vault logic independent from the hardware implementation.

This should allow the application to run:
- On a desktop computer (development)
- In a simulated environment (testing)
- On ESP32 hardware (deployment)

using the same core business logic.



### Device Management

The long-term goal is to support desktop management when the device is connected to a computer.

Rather than editing raw vault files directly, the device will expose a management interface that can:

- Import password collections
- Bulk edit entries
- Organize categories and tags
- Create backups
- Synchronize encrypted vault data

This approach allows the vault contents to remain encrypted at rest while still supporting efficient management of large password collections.

The intended workflow is:

Device → Connected to Computer → Companion Application → Authenticated Access → Encrypted Save