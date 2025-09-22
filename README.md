# Task Management System Template

> **📋 GitHub Template Repository**  
> This repository is configured as a [GitHub template](https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-template-repository). Click **"Use this template"** to create a new repository with all the task management structure pre-configured for your project.

A portable, reusable task tracking system for any software project.

## 🚀 Quick Start

```bash
# Copy template to your project
cp -r ./tasks-template/ your-project/task-system/

# Use it immediately
cd your-project/task-system/
cat tasks/INDEX.md | rg "Ready"  # Check available tasks
```

## 📁 Structure

- **`tasks/`** - Template files (INDEX.md, template.md, README.md)
- **`examples/`** - Real-world implementations (demo, sombrero-edge-control)
- **`docs/`** - Core principles (PRP methodology, dev philosophy)
- **`.claude/`** - AI assistant commands

## 📖 Usage

**For detailed setup and usage:**
→ See [`tasks/README.md`](tasks/README.md)

**For real examples:**
→ See [`examples/`](examples/)

**For core principles:**
→ See [`docs/`](docs/)

## 🎯 Key Features

- **Portable** - Works anywhere in your repo
- **Tech-agnostic** - Adapts to any tech stack
- **Dependency-aware** - Tracks task relationships
- **Validation-focused** - Clear success criteria
- **AI-powered** - Claude Code integration

## 🛠️ Commands

```bash
# Create new task
/create-task [CATEGORY] [description]

# Execute existing task
/execute-task [task-file-path]
```

## 📚 Core Principles

- **KISS** - Keep tasks simple and focused
- **YAGNI** - Don't over-engineer
- **PRP Methodology** - Structured task execution
- **Progressive Validation** - Test as you go

---

**Ready to track tasks?** → Copy `tasks-template/` to your project and start with [`tasks/README.md`](tasks/README.md)

## 🙏 Acknowledgments

This task management system draws inspiration from the excellent work in [PRPs-agentic-eng](https://github.com/Wirasm/PRPs-agentic-eng) by @Wirasm, particularly the structured approach to task creation, execution, and the PRP (Product Requirement Prompt) methodology for AI-assisted development.
