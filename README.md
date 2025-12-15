

---

## Features Implemented

- Message Authentication Code (MAC)
- Freshness counter for replay protection
- Classic CAN (8-byte payload)
- CAN-FD (64-byte payload)
- Interrupt-based transmission and reception
- LED indication for TX / RX / verification status
- Lightweight SecOC-style security (non-AUTOSAR)

---

## Security Concept

### MAC (Message Authentication Code)
- Generated using a **shared secret key**
- Ensures message **authenticity** and **integrity**
- Receiver recomputes MAC and verifies it

### Freshness Counter
- Incremented for every transmitted message
- Prevents **replay attacks**
- Receiver rejects old or repeated counters

---

## Classic CAN Frame Format (8 Bytes)

| Word | Description |
|-----|-------------|
| TX[0] | Upper 16 bits → Payload<br>Lower 16 bits → Freshness |
| TX[1] | 32-bit MAC |

---

## CAN-FD Frame Format (64 Bytes)

| Word Index | Description |
|-----------|-------------|
| TX[0] | Freshness Counter |
| TX[1–14] | Application Payload (56 bytes) |
| TX[15] | 32-bit MAC |

---

## Hardware & Tools

- Infineon **AURIX™ TC397**
- AURIX Development Studio
- iLLD (Infineon Low Level Drivers)
- CAN / CAN-FD transceivers
- Optional: BusMaster for traffic analysis

---

## How to Use

1. Import the required ZIP project into **AURIX Development Studio**
2. Flash **TX code** on one TC397 board
3. Flash **RX code** on another TC397 board
4. Connect CAN / CAN-FD lines
5. Observe LEDs:
   - TX LED → Message transmitted
   - RX LED → Message received
   - Verification success → MAC & freshness validated

---

## Attacks Addressed

- Spoofing attacks
- Replay attacks
- Message tampering

*(DoS and fuzzing can be demonstrated by modifying TX behavior)*

---

## Target Use Case

- Academic projects
- Automotive cybersecurity demonstrations
- SecOC concept validation
- CAN vs CAN-FD security comparison

---


---
