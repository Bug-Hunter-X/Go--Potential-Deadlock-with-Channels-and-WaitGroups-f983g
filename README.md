# Go: Potential Deadlock with Channels and WaitGroups

This repository demonstrates a potential deadlock scenario in Go when using channels and wait groups.  The program showcases a race condition where the sending goroutine might close the channel before the receiving goroutine processes all the data, resulting in a deadlock.

## Description

The `bug.go` file contains a program that uses two goroutines: one to send integer values to a channel and another to receive and process these values.  The `sync.WaitGroup` is used to wait for both goroutines to complete.  However, if the sender finishes significantly earlier than the receiver (or the receiver doesn't start consuming values early enough) then the program can deadlock.

## Solution

The `bugSolution.go` file provides a corrected version that avoids the deadlock issue using proper synchronization and error handling.

## How to Run

1. Clone this repository.
2. Navigate to the repository's directory.
3. Run the `bug.go` file to reproduce the deadlock (it may or may not deadlock; the timing is critical).
4. Run the `bugSolution.go` file to observe the correct behavior.