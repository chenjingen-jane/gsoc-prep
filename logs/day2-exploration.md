GSoC Day 2 Learning Log: Codebase Exploration & Debugging Practice

Project: OWASP Python Honeypot
Focus: Understanding the codebase through debugging, not just running the project
Goal: Learn how a real-world Python project starts, initializes, and fails in practice

🟦 Phase 1: Environment Setup & Dependency Reality Check
Objective

Set up a local development environment and understand how dependencies affect real projects.

What I did

Cloned the OWASP Python Honeypot repository

Attempted to run the project locally on Windows using Git Bash

Installed dependencies using pip install -r requirements.txt

Ran the project using both normal execution and python -m pdb

What I learned

This project is not designed to run smoothly on a modern local Windows environment without Docker.
Multiple dependency issues appeared, including:

Missing modules (terminable_thread, netaddr, pyshark, elasticsearch)

Version conflicts between Flask and Werkzeug

Python ecosystem changes (e.g. distutils removal in newer Python versions)

Instead of treating these as “mistakes”, I learned to recognize them as expected friction when working with an older but real-world codebase.

📌 Key realization:
Getting a project to “run” is not the same as understanding it.

🟦 Phase 2: Tracing the Entry Point with PDB
Objective

Identify the true entry point of the program and understand what happens during startup.

Step 4: Finding the Entry Point

I initially searched for:

main.py

__main__.py

setup.py and possible entry_points

After inspection and verification with PDB, I confirmed that:

➡️ ohp.py is the actual entry point of the application

I inserted a breakpoint using:

import pdb; pdb.set_trace()


and launched the program with:

python -m pdb ohp.py


This allowed me to verify, not assume, where execution begins.

🟦 Phase 3: Code Walk Using the Debugger
Objective

Use PDB to “walk through” the startup sequence and observe real execution flow.

Step 5: Code Walk (Startup Phase)

Using PDB commands (n, s, l, c), I traced the execution path:

ohp.py
 └─ core/load.py
     ├─ api/server.py
     ├─ database/connector.py
         └─ elasticsearch (external dependency)


During startup, the program successfully:

Imported core modules

Loaded configuration logic

Initialized the main honeypot engine

The program then exited intentionally with:

[X] Cannot connect to elasticsearch
sys.exit(1)

Important understanding

This is not a crash.

It is a controlled and correct failure due to a missing external service (Elasticsearch).

📌 Key insight:
Program startup involves many stages before “doing work”, and a failure during initialization is still part of normal execution logic.

🟦 Phase 4: Understanding (Not Forcing) Tests
Objective

Understand the role of tests without forcing them to pass.

Step 6: Tests (Conceptual Completion)

Although the schedule includes running tests, I learned that:

Many tests depend on:

Elasticsearch

Network capture tools

System-level permissions

Running them in a non-Docker Windows environment is unrealistic

Instead of forcing execution, I focused on:

Understanding the structure of the tests/ directory

Recognizing tests as contracts for expected behavior

Learning how failures communicate what is broken and where

📌 Key realization:
Passing tests is not the goal at this stage — understanding what they validate is.

🟦 Problems Encountered & How I Interpreted Them
1. Repeated ModuleNotFoundError

Cause: Legacy dependencies + modern Python environment
Fix: Install where reasonable, analyze and stop where external services are required

2. Flask / Werkzeug incompatibility

Cause: API changes across versions
Fix: Do not patch blindly; recognize environment mismatch

3. Elasticsearch connection failure

Cause: External service not running
Conclusion: Expected behavior, not a bug

🟦 What I Actually Achieved Today

Identified and verified the real entry point of a large Python project

Used PDB to trace execution instead of guessing

Learned to distinguish:

Import-time errors

Runtime logic

External dependency failures

Stopped treating errors as personal mistakes and started reading them as system signals

🟦 Final Reflection

Before today, I thought “running the project” meant everything must work.

Now I understand that in real-world projects:

Understanding the startup flow is more important than a green terminal

Debugging is about asking why something happens, not just fixing it

Failing early due to missing dependencies is often intentional design

This day helped me move from reading code to reasoning about systems.
