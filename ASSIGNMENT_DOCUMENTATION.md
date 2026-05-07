# Assignment 3 - Complete Documentation

**Student Name**: [Norah alkubra ]  
**Student ID**: [445052179]  
**Date Submitted**: [May 7, 2026]

---

## 🎥 VIDEO DEMONSTRATION LINK (REQUIRED)

> **⚠️ IMPORTANT: This section is REQUIRED for grading!**
> 
> Upload your 3-5 minute video to your **PERSONAL Gmail Google Drive** (NOT university email).
> Set sharing to "Anyone with the link can view".
> Test the link in incognito/private mode before submitting.

**Video Link**: [Paste your personal Gmail Google Drive link here]

**Video filename**: `[YourStudentID]_Assignment3_Synchronization.mp4`

**Verification**:
- [ ] Link is accessible (tested in incognito mode)
- [ ] Video is 3-5 minutes long
- [ ] Video shows code walkthrough and commits
- [ ] Video has clear audio
- [ ] Uploaded to PERSONAL Gmail (not @std.psau.edu.sa)

---

## Part 1: Development Log (1 mark)

Document your development process with **minimum 3 entries** showing progression:







### Entry 1 - [     May 7, 2026 - 4:00 AM  ]
**What I implemented**: 
Updated my student ID and analyzed the scheduler code to identify shared resources and race conditions.
**Challenges encountered**: 

**How I solved it**: 
I reviewed the code carefully and checked all variables modified by multiple processes.
**Testing approach**: 
Ran the program before synchronization to observe execution behavior.
**Time spent**: 
30 minutes
---


Entry 2 - May 7, 2026 - 4:45 AM
What I implemented:

Added ReentrantLock to protect shared counters and execution log.
Challenges encountered:

Making sure locks were released correctly.
How I solved it:
Used try-finally blocks for every critical section.
Testing approach:
Ran the program multiple times and checked consistency of final statistics.
Time spent:
45 minutes



Entry 3 - May 7, 2026 - 5:30 AM
What I implemented:
Added binary semaphore for CPU synchronization in run() and runToCompletion() methods.
Challenges encountered:
Handling InterruptedException from semaphore acquire operation.
How I solved it:
Used nested try-catch blocks around acquire().
Testing approach:
Verified that only one process executes CPU section at a time.
Time spent:
40 minutes


Entry 4 - May 7, 2026 - 6:15 AM
What I implemented:
Tested the final program and completed assignment documentation.
Challenges encountered:
Verifying all synchronization mechanisms worked correctly.
How I solved it:
Compared outputs from multiple runs and reviewed execution log results.
Testing approach:
Executed the program several times and checked statistics correctness.
Time spent:
35 minute

### Entry 5 - May 7, 2026 - 6:50 AM

**What I implemented**:
Reviewed the complete project, checked all TODO sections, and verified Git commits and final output.

**Challenges encountered**:
Ensuring that all synchronization code matched the assignment requirements without modifying the original scheduler logic.

**How I solved it**:
Carefully reviewed each synchronized section and tested the final version after all modifications.

**Testing approach**:
Ran the program again and verified final statistics, execution log count, and process completion.

**Time spent**:
20 minutes

---

## Part 2: Technical Questions (1 mark)

### Question 1: Race Conditions
**Q**: Identify and explain TWO race conditions in the original code. For each:
- What shared resource is affected?
- Why is concurrent access a problem?
- What incorrect behavior could occur?

**Your Answer**:
The first race condition exists in the shared counters such as contextSwitchCount and completedProcessCount. Multiple threads may update these variables at the same time, which can cause incorrect final values due to lost updates. The second race condition exists in the executionLog ArrayList because ArrayList is not thread-safe. Concurrent access may corrupt the internal structure of the list or cause inconsistent log entries. Without synchronization, the scheduler statistics may become inaccurate and program behavior may become unpredictable.


ReentrantLock is used to provide mutual exclusion for critical sections. I used it to protect shared counters and executionLog because only one thread should modify them at a time. Semaphore is used to control access to limited resources. I used a binary semaphore with one permit to simulate one CPU core and ensure that only one process can execute CPU operations simultaneously.


Deadlock occurs when multiple threads wait forever for resources held by each other. One prevention technique is using try-finally blocks to guarantee releasing locks and semaphores. Another technique is keeping synchronization simple and avoiding nested locks. In my code, I used finally blocks to always release locks and semaphores even if exceptions occur. This prevents resources from remaining locked permanently.


.I used one ReentrantLock for all shared counters and execution log operations. I selected this approach because it keeps the synchronization logic simple and easier to manage. Using separate locks could improve concurrency because the counters are independent resources, but it would increase code complexity. Coarse-grained locking is easier to understand and reduces the possibility of synchronization mistakes. Fine-grained locking provides better performance in highly concurrent systems because different threads can access different resources simultaneously. For this assignment, one lock was sufficient and matched the assignment requirements.








---

### Question 2: Locks vs Semaphores
**Q**: Explain the difference between ReentrantLock and Semaphore. Where did you use each in your code and why?

**Your Answer**:

[Your answer here - explain your implementation choices]

---

### Question 3: Deadlock Prevention
**Q**: What is deadlock? Explain TWO prevention techniques and what you did to prevent deadlocks in your code.

**Your Answer**:

[Your answer here - reference try-finally blocks, lock ordering, etc.]

---

### Question 4: Lock Granularity Design Decision 
**Q**: For Task 1 (protecting the three counters), explain your lock design choice:
- Did you use ONE lock for all three counters (coarse-grained) OR separate locks for each counter (fine-grained)?
- Explain WHY you made this choice
- What are the trade-offs between the two approaches?
- Given that the three counters are independent, which approach provides better concurrency and why?

**Your Answer**:

[Your answer here - explain coarse-grained vs fine-grained locking, independence of counters, concurrency implications. Show understanding of when to use each approach. 5-8 sentences expected.]

---

## Part 3: Synchronization Analysis (1 mark)

### Critical Section #1: Counter Variables

**Which variables**: 

**Why they need protection**: 

**Synchronization mechanism used**: 

**Code snippet**:
```java
// Paste your implementation here
```

**Justification**: 

---

### Critical Section #2: Execution Log

**What resource**: 

**Why it needs protection**: 

**Synchronization mechanism used**: 

**Code snippet**:
```java
// Paste your implementation here
```

**Justification**: 

---

### Critical Section #3: CPU Semaphore

**Purpose of semaphore**: 

**Number of permits and why**: 

**Where implemented**: 

**Code snippet**:
```java
// Paste your implementation here
```

**Effect on program behavior**: 

---

## Part 4: Testing and Verification (2 marks)

### Test 1: Consistency Check
**What I tested**: Running program multiple times to verify consistent results

**Testing procedure**: 
```bash
# Commands used (run the program at least 5 times)
```

**Results**: 
(Show that running multiple times produces consistent, correct results)

**Why synchronization is necessary**: 
(Explain what race conditions COULD occur without synchronization, even if you didn't observe them. Explain which shared resources need protection and why.)

**Conclusion**: 

---

### Test 2: Exception Testing
**What I tested**: Checking for ConcurrentModificationException

**Testing procedure**: 

**Results**: 

**What this proves**: 

---

### Test 3: Correctness Verification
**What I tested**: Verifying correct final values (total burst time, context switches, etc.)

**Expected values**: 

**Actual values**: 

**Analysis**: 

---

### Test 4: Different Scenarios
**Scenario tested**: [e.g., different time quantum, more processes, etc.]

**Purpose**: 

**Results**: 

**What I learned**: 

---

## Part 5: Reflection and Learning

### What I learned about synchronization:

[6-8 sentences about key concepts, challenges, insights]

---

### Real-world applications:

Give TWO examples where synchronization is critical:

**Example 1**: 

**Example 2**: 

---

### How I would explain synchronization to others:

[Explain to someone who just finished Assignment 1 - use simple terms and analogies]

---

## Part 6: GitHub Repository Information

**Repository URL**: 

**Number of commits**: 

**Commit messages**: 
1. 
2. 
3. 
4. 

---

## Summary

**Total time spent on assignment**: 

**Key takeaways**: 
1. 
2. 
3. 

**Most challenging aspect**: 

**What I'm most proud of**: 

---

**End of Documentation**
