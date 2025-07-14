# Frequency-Doubler-Counter-
Designed two logic-level architectures to double the effective count rate of a synchronous 4-bit counter using XOR-based edge detection and dual-path MUX-controlled counters.
# Frequency-Doubled 4-bit Counter (Digital Design Challenge)

This project implements a **4-bit synchronous up-counter** that operates at **2× the base clock frequency**. Designed using fundamental digital logic components (flip-flops, logic gates, MUX), this project explores **two creative architectures** to double the counting speed **without changing the original clock frequency**.

---

## Objective

- Design a 4-bit counter that counts **0 → 15 → 0** using JK flip-flops.
- Extend this to a **2× frequency counter** using:
  1. **Edge-detection clock doubler**
  2. **Dual counters with MUX selection**

---

## Solution 1: XOR-Based Clock Doubler

### Concept
- Use an XOR gate to generate a pulse on **every clock edge** (rising and falling).
- Use this toggled signal to clock a 4-bit synchronous JK counter.

### Components
- 1 D Flip-Flop (delays clock)
- 1 XOR Gate (detects clock edge)
- 4 JK Flip-Flops (for counter)

### How it Works
- XOR compares delayed and current clock → produces a HIGH pulse on transitions.
- Output clock = 2× base clock
- Standard counter toggles on this new clock

### Result
- Efficient and minimal design that doubles counter speed using **pure logic**

---

## Solution 2: Dual Edge Counter with MUX

### Concept
- Use **two counters**:
  - One triggered on **rising edges** (even numbers)
  - One on **falling edges** (odd numbers)
- Use **4-bit MUX** to switch between the two on each half cycle.

### Components
- 8 JK Flip-Flops (4 for each counter)
- 4 2:1 MUXes (1 per bit)
- 1 NOT gate (inverts clock for odd counter)

### How it Works
| Clock | Active Counter | MUX Output |
|-------|----------------|------------|
| HIGH  | Even counter   | Q from even counter |
| LOW   | Odd counter    | Q from odd counter  |

- Output switches every half cycle, giving the illusion of **double-speed counting**

### Result
- Modular and scalable design with clean separation of logic
- Flexible for future enhancements

---

## Comparison Table

| Feature               | Clock Doubler (XOR)       | Dual Counter + MUX           |
|-----------------------|----------------------------|-------------------------------|
| **Style**             | Signal-driven, minimal     | Structural, modular           |
| **Components**        | 1 DFF, 1 XOR, 4 JK FFs     | 2 counters, 4 MUXes, 1 NOT    |
| **Speed Control**     | Implicit via XOR edges     | MUX select with system clock  |
| **Output Behavior**   | Direct from counter        | Alternating via MUX           |
| **Strengths**         | Compact, fast              | Clear logic, scalable         |

---

## Tools Used

- **Deeds Digital Simulator** (DLS)
- Timing diagrams and waveforms simulated and verified

---

## Files

- `clock_doubler_solution.sch` — XOR-based design
- `dual_counter_mux_solution.sch` — Dual path design
- `README.md` — Project documentation
- Screenshots & waveform plots (to be added)

---

## Visuals

*(Include your circuit diagram images and Deeds waveforms here)*

---

## Applications

- Custom frequency dividers/doublers
- Digital counters with high responsiveness
- Low-power timing circuits in embedded systems
