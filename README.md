# 🔍 8085 Program: Search an Element in Memory

## 📌 Objective

This project implements a simple 8085 assembly program to search for a specific value in memory. Once the value is found, the program stores the address of that memory location.

---

## 🎥 Demo

<p align="center">
  <img src="./demo.gif" width="750">
</p>

---

## 🧠 Concepts Used

* Using HL register pair as a memory pointer
* Accumulator-based comparison
* Looping using jump instructions
* Conditional branching
* Register exchange using XCHG

---

## ⚙️ Program

```
LXI H 1000h
MVI A FFh

GO: CMP M
JZ FOUND
INX H
JMP GO

FOUND: XCHG
HLT
```

---

## 📝 How It Works

### 🔹 Initialization

The program starts by loading the memory address `1000h` into the HL register pair. This acts as the starting point of our search.
The accumulator is loaded with `FFh`, which is the value we want to find.

---

### 🔹 Searching Process

The program compares the value in the accumulator with the data stored at the memory location pointed to by HL.

* If the values match, the program jumps to the `FOUND` label
* If not, HL is incremented to point to the next memory location
* This process continues in a loop until a match is found

---

### 🔹 When Value is Found

Once the value is found:

* `XCHG` swaps HL and DE registers
* This effectively stores the address of the matched location in the DE register pair
* The program then halts

---

## 📊 Example

| Memory Address | Data |
| -------------- | ---- |
| 1000h          | 12h  |
| 1001h          | 34h  |
| 1002h          | FFh  |
| 1003h          | 56h  |

The program searches for **FFh**
✔ Found at address **1002h**
✔ Address stored in **DE register pair**

---

## 🎯 Output

After execution, the DE register pair holds the address where the value was found.

---

## ⚠️ Limitation

This program does not handle the case where the value is not present in memory. In such cases, it will continue running indefinitely.

---

## 🚀 Improvements (Future Scope)

* Add a counter to limit the search range
* Handle "value not found" condition
* Store the result in memory instead of registers

---

## 📁 Project Structure

```
8085-memory-search/
│── search.asm
│── README.md
├── demo.gif
```

---

## ⭐ Author

<p align="center">
  <img src="https://media.giphy.com/media/v1.Y2lkPWVjZjA1ZTQ3bm8wYnloN3E1N3FuczV5MTI2Mmp2MjNtN282eGJ0M2Zld3JpcnAyMiZlcD12MV9naWZzX3NlYXJjaCZjdD1n/MBchOyOFof4tfmxrD8/giphy.gif" height="160" width="160">
</p>
<p align="center"><b>DuduBoiii</b></p>

---

## 📌 Final Note

This is a basic implementation of a linear search using the 8085 microprocessor. It’s a great starting point for understanding how memory traversal and comparisons work at a low level.
