# Hardware-Based Security System — Discrete Logic Design Study

## Overview

I designed this as a hands-on engineering study to understand how an authentication and physical access-control system could be broken down into hardware functions without starting from a conventional software controller.

I started with a simple question:

> **What happens when I treat each security function as a physical logic problem?**

Instead of beginning with firmware, I started with individual components and built the logic around them. That forced me to think carefully about timing, state, validation, failure handling and physical outputs.

I ended up with a large transistor-level design that I could study and refine as a collection of smaller functional blocks.

## What I was trying to learn

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

I have intentionally simplified the public architecture. My original design contains considerably more component-level detail.

![Conceptual architecture](assets/security-architecture.svg)

**Physical input → timing and conditioning → discrete logic → validation → controlled response**

I separated the response side into three important functions:

**Lockout and reset** for failure handling and recovery.

**Alert / indication** for communicating an abnormal or locked state.

**Actuation** for the final physical output.

I use this block-level view because it lets me explain the engineering without exposing the exact implementation.

## How I approached the design

I deliberately started with discrete components rather than hiding the logic behind a microcontroller.

That made every function visible.

I turned a timing problem into a timing circuit.

I turned a state problem into a state circuit.

I turned a validation problem into a logic path.

I treated a lockout problem as a separate physical state.

That forced me to understand what each part of the system was actually doing rather than relying on software to abstract it away.

I also explored how different input behaviours, including longer presses, could be handled before the main validation path.

## The design challenge

The biggest challenge was complexity.

As I added more states and conditions, the number of components and interconnections grew quickly. That gave me a useful engineering lesson: removing software does not remove complexity. I found that it moves the complexity into the physical architecture.

I therefore started thinking about how I could represent the same logic more efficiently while keeping the security control philosophy intact.

That led me to explore a later architectural direction where dedicated logic and memory devices could take over repetitive data-handling work, while discrete circuitry remained responsible for the physical control and response functions.

## What this project taught me

### 1. Decomposition matters

I found that a complicated security system becomes much easier to reason about when every function has a clearly defined role.

### 2. Hardware has state too

Building state physically made me think much more carefully about what creates, holds, clears and changes state.

### 3. Security is also an operating problem

Authentication is only one part of the system. I also had to think about invalid input, lockout, recovery, alerting, power behaviour and the physical output.

### 4. Simplicity at one layer can create complexity at another

A software-free design can remove one class of dependency while making the physical design considerably larger and harder to maintain. That trade-off became an important part of my study.

## My role

I designed the architecture and developed the logic as a personal engineering study.

I worked through the design at component level, breaking the overall system into smaller functions and studying how those functions interacted.

I approach this the same way I approach problems in my other work: I try to understand the system from the ground up, separate the problem into manageable parts, and then find a practical way to connect those parts into something that works.

## Public disclosure boundary

I have intentionally not included the original schematic in this public repository.

I have withheld:

- exact component-level authentication logic;
- the complete wiring topology;
- exact values and timing parameters;
- recovery and reset implementation details;
- implementation-specific security paths;
- and other details that could make the design easier to reproduce, probe or bypass.

I am using the public version to demonstrate my engineering thinking and the architecture of the study, not to publish the complete security design.

## Status

**Design study / prototype architecture**

I regard this as an engineering exploration rather than a claim that the resulting system is production-certified, tamper-proof or suitable for security-critical deployment without further validation.

## Why I include it in my portfolio

Most of my professional work has involved people, processes, financial services, data and software-enabled systems.

I include this project because it shows another side of the same mindset.

I wanted to understand a system at the lowest practical level, assign clear responsibilities to each part, and see how far I could take the design using physical logic.

That is the kind of problem-solving I enjoy.
