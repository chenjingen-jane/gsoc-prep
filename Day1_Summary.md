GSoC 2026 Preparation: Day 1 Summary

📅 Overview
Focus: Linux Environment, Git Advanced Workflow, and Python Debugging.

Goal: Establish a solid foundation for system programming and professional open-source contribution.

💻 Technical Mastery
1. Linux System Administration
Mastered essential CLI tools for file management and process control.

File Operations: mkdir, touch, cp, mv, rm -r.

Permissions: Understanding chmod +x to make scripts executable.

Process Management: Using ps and top to monitor system resources and kill <PID> to terminate stalled processes.

Data Flow: Using Pipes (|) and Redirection (>, >>) to chain programs together.

2. Professional Git Workflow
Moved beyond basic commit/push to maintain a clean project history.

Context Switching: Used git stash and git stash pop to handle interrupted work.

History Cleanup: Applied git rebase -i (Interactive Rebase) to squash multiple commits into one clean entry.

Visualization: Used git log --graph --oneline --all to understand complex branching structures.

3. Debugging (The "No-Print" Philosophy)
Switched from "print-statement debugging" to "controlled execution" using PDB.

Breakpoints: Triggering the debugger with import pdb; pdb.set_trace().

Control Flow:

n (next): Step over.

s (step): Step into functions.

p <var> (print): Inspect variable state.

c (continue): Resume execution.

🧠 Key Takeaways
Muscle Memory: Commands are not just theory; they must be practiced until they are instinctive.

Safety First: Commands like rm -r and rebase are powerful but require caution.

Transparency: Documenting the process on GitHub builds trust with future GSoC mentors.
