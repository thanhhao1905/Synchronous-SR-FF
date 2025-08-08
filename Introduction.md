# Introduction to the `sr_ff_sync_rst_n` Module

## Overview
This repository contains a **Synchronous SR-FF** with an asynchronous active-low reset.

The flip-flop (FF) is a fundamental building block in digital logic, used for storing a single bit of data. The SR-FF (Set-Reset Flip-Flop) is one of the most basic types, featuring two primary inputs: **Set (S)** and **Reset (R)**.

* When **S** is activated (S=1, R=0), the output **Q** is set to 1.
* When **R** is activated (S=0, R=1), the output **Q** is reset to 0.

This design extends a standard synchronous SR-FF by including a **synchronous reset** and an **asynchronous active-low reset**, named **rst_n**. The synchronous reset ensures that the reset action only occurs on the rising edge of the clock signal, preventing timing issues. The asynchronous reset, however, allows for an immediate reset of the flip-flop regardless of the clock signal, which is crucial for quick system initialization or error recovery.

## Key Features

| Port Name | Function | Notes |
| :--- | :--- | :--- |
| **S** | Set | Sets Q to 1 |
| **R** | Reset | Resets Q to 0 |
| **clk** | Clock | Synchronous clock signal |
| **rst_n** | Asynchronous Reset | Asynchronous reset, active low |
| **Q** | Main Output | The primary output of the flip-flop |
| **Q_n** | Inverted Output | The inverted output of the flip-flop |

## Design Goal
The primary goal of this project is to provide a clear, simple, and reusable SR-FF module. The inclusion of both synchronous and asynchronous reset capabilities makes this module versatile for a wide range of digital logic designs, ensuring system stability and fast initialization. This design is ideal for educational purposes and for integration into larger, more complex digital circuits.
