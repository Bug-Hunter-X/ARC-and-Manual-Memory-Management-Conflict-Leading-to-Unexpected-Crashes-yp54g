# Objective-C ARC and Manual Memory Management Conflict

This repository demonstrates a common yet subtle error in Objective-C related to memory management.  The bug arises from a conflict between Automatic Reference Counting (ARC) and manual memory management using `retain`, `release`, and `autorelease`.  Incorrect usage can lead to unexpected crashes due to accessing deallocated memory.

## Bug Description

The core issue lies in manually managing the retain count of an object without proper synchronization with ARC's automatic handling.  This situation can occur when an object is retained and later passed to a method that doesn't explicitly retain it.  If the initial owner releases the object prematurely, the other method may attempt to access deallocated memory, causing a crash.

## Solution

The most effective solution is to ensure consistent and predictable memory management.  Either rely entirely on ARC (preferred), or carefully use manual memory management while adhering to the principles of ownership and retain/release cycles.

## Files

* `bug.m`: Demonstrates the buggy code.
* `bugSolution.m`: Presents the corrected code.
