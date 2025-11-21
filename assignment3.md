# Assignment3 
## 一. 单选题（共6题，35分）

1. **(单选题, 5分)** In Many-to-One thread model, What would happen if a thread in a multithreaded process makes a blocking system call?

A. the other threads of the process would continue to run
B. the entire process would get blocked
C. the blocking thread will get killed
D. the blocking thread will never get to run again

2. **(单选题, 10分)**
   Suppose we have four resources, RA, RB, RC and RD. Given below current matrix, available vector and maximal requirement matrix, please answer question 1 to 2. What is the current state of existing system?
A. deadlock
B. unsafe
C. safe
D. not sure

3. **(单选题, 5分)**
   Can a request of one instance of RA by Process P0 be granted safely according to Banker’s algorithm?
A. can, but unsafe
B. cannot, deadlock
C. can, safe
D. not, sure

4. **(单选题, 5分)** There are N processes which share M mutual exclusive resources, each process can hold W resources at most. Which of the following condition may cause a deadlock?

A. M=2, N=1, W=2
B. M=2, N=2, W=1
C. M=4, N=3, W=2
D. M=4, N=2, W=3

5. **(单选题, 5分)**
   Consider the following resource trajectory graph for a system with two processes (P1 and P2) and two resources (R1 and R2). The x-axis and y-axis represent the time when P1 and P2 will request their resource respectively. Which of the following statements is correct?

A. The system is deadlocked at point B.
B. The system is safe at point B.
C. The system is safe at point D.
D. Point C represents a transition between safe state and deadlock.

6. **(单选题, 5分)** A computer system has a device with n mutually exclusive instances. Three concurrent processes require 3,4 and 5 instances. To ensure deadlock not to occur, what is the minimum number n?

A. 9
B. 10
C. 11
D. 12

---

## 二. 简答题（共2题，40分）

7. **(简答题, 20分)**




1. 变量定义缺失
代码中使用了 turn 变量，但未显式定义其类型和初始值。这会导致编译错误或运行时的未定义行为。
2. 潜在的死锁与进展问题
在当前逻辑中，当两个进程同时尝试进入临界区时，可能出现进展受阻的情况：
例如，P0 先设置 flag[0] = true，然后检查 flag[1]；同时 P1 设置 flag[1] = true，检查 flag[0]。此时两者会同时进入各自的内层循环，若 turn 的值恰好让双方都执行 “等待 + 重置 flag” 的逻辑，可能陷入无限循环，导致饥饿或死锁。

boolean flag[2];
int turn = 0;  // 显式定义turn并初始化

void P0() {
    while (true) {
        flag[0] = true;
        turn = 1;  // 表明自己想进入，同时把“轮次”让给对方
        while (flag[1] && turn == 1) { /* 等待：对方想进入且轮次是对方的 */ }
        /* critical section */;
        flag[0] = false;
        /* remainder */;
    }
}

void P1() {
    while (true) {
        flag[1] = true;
        turn = 0;  // 表明自己想进入，同时把“轮次”让给对方
        while (flag[0] && turn == 0) { /* 等待：对方想进入且轮次是对方的 */ }
        /* critical section */;
        flag[1] = false;
        /* remainder */;
    }
}

void main() {
    flag[0] = false;
    flag[1] = false;
    parbegin(P0, P1);
}

8. **(简答题, 20分)**
   Here is the code for implementing mutual exclusion. Please identify any existing issues
死锁问题：如果进程 0 和进程 1 同时执行 flag[0] = true 和 flag[1] = true，然后各自进入 while(flag[1]) 和 while(flag[0]) 循环，就会无限等待，导致死锁，无法进入临界区。
无进展保障：当两个进程同时竞争时，没有机制保证其中一个进程能最终进入临界区，存在饥饿的可能。
