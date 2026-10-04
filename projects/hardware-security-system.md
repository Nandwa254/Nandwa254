# Hardware-Based Security System — Discrete Logic Design Study

## Overview

I designed this as a hands-on engineering study to understand how an authentication and physical access-control system could be broken down into hardware functions without starting from a conventional software controller.

The main question I wanted to explore was simple:

> **What happens when I treat each security function as a physical logic problem?**

Instead of beginning with firmware, I started with individual components and built the logic around them. That forced me to think carefully about timing, state, validation, failure handling and physical outputs.

The result was a large transistor-level design that I could study and refine as a collection of smaller functional blocks.

## What I was trying to learn

This was less about producing a finished commercial lock and more about understanding the engineering underneath one.

I wanted to understand:

- how a physical input can be conditioned before it is evaluated;
- how timing can be created without software;
- how a sequence or state can be represented using discrete logic;
- how valid and invalid conditions can be separated;
- how repeated failure can trigger a hardware lockout state;
- how an alarm or indicator can be driven from that state;
- how the final decision can control a physical actuator;
- and how the whole design behaves when the blocks are connected together.

## Architecture

The public architecture is intentionally simplified. The original design contains considerably more component-level detail.

![Conceptual architecture](assets/security-architecture.svg)

**Physical input → timing and conditioning → discrete logic → validation → controlled response**

The response side is separated into three important functions:

**Lockout and reset** for failure handling and recovery.

**Alert / indication** for communicating an abnormal or locked state.

**Actuation** for the final physical output.

This block-level view is the most useful way to understand the project without exposing the exact implementation.

## How I approached the design

I deliberately started with discrete components rather than hiding the logic behind a microcontroller.

That made every function visible.

A timing problem became a timing circuit.

A state problem became a state circuit.

A validation problem became a logic path.

A lockout problem became a separate physical state.

This approach was useful because it forced me to understand what each part of the system was actually doing rather than relying on software to abstract it away.

I also explored how different input behaviours, including longer presses, could be handled before the main validation path.

## The design challenge

The biggest challenge was complexity.

As more states and conditions were added, the number of components and interconnections grew quickly. That created a useful engineering lesson: removing software does not remove complexity. It moves the complexity into the physical architecture.

I therefore started thinking about how the same logic could be represented more efficiently while keeping the security control philosophy intact.

That led me to explore a later architectural direction where dedicated logic and memory devices could take over repetitive data-handling work, while discrete circuitry remained responsible for the physical control and response functions.

## What this project taught me

### 1. Decomposition matters

A complicated security system becomes much easier to reason about when every function has a clearly defined role.

### 2. Hardware has state too

It is easy to think of “state” as something that belongs to software. Building it physically made me think much more carefully about what creates, holds, clears and changes state.

### 3. Security is also an operating problem

Authentication is only one part of the system. You also need to think about invalid input, lockout, recovery, alerting, power behaviour and the physical output.

### 4. Simplicity at one layer can create complexity at another

A software-free design can remove one class of dependency while making the physical design considerably larger and harder to maintain. That trade-off became an important part of the study.

## My role

I designed the architecture and developed the logic as a personal engineering study.

I worked through the design at component level, breaking the overall system into smaller functions and studying how those functions interacted.

The project reflects the way I approach problems in my other work as well: understand the system from the ground up, separate the problem into manageable parts, and then find a practical way to connect those parts into something that works.

## Public disclosure boundary

The original schematic is **not included in this public repository**.

I have intentionally withheld:

- exact component-level authentication logic;
- the complete wiring topology;
- exact values and timing parameters;
- recovery and reset implementation details;
- implementation-specific security paths;
- and other details that could make the design easier to reproduce, probe or bypass.

The public version is meant to demonstrate my engineering thinking and the architecture of the study, not to publish the complete security design.

## Status

**Design study / prototype architecture**

This project should be read as an engineering exploration rather than a claim that the resulting system is production-certified, tamper-proof or suitable for security-critical deployment without further validation.

## Why it belongs in my portfolio

Most of my professional work has involved people, processes, financial services, data and software-enabled systems.

This project shows another side of the same mindset.

I wanted to understand a system at the lowest practical level, assign clear responsibilities to each part, and see how far I could take the design using physical logic.

That is the kind of problem-solving I enjoy.
