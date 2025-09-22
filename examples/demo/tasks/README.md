# Task Management System - Example Implementation

## Overview

This is a working example of the task management system in action. It demonstrates how tasks are organized, tracked, and executed using the structured approach defined in the template.

## Directory Structure

```text
tasks/
├── README.md                    # This file - system usage guide
├── INDEX.md                     # Live task tracker and progress dashboard
├── development/                 # Development setup tasks (DEV)
│   ├── DEV-001-setup-project.md
│   └── DEV-002-install-dependencies.md
├── features/                    # New features and functionality (FEAT)
│   └── FEAT-001-user-authentication.md
├── testing/                     # Testing infrastructure (TEST)
│   └── TEST-001-unit-tests.md
└── [other-categories]/          # Additional categories as needed
```

## Current Status

- **Total Tasks**: 6 tasks across 3 categories
- **Estimated Time**: 12 hours total effort
- **Current Phase**: Development Setup (2 tasks ready to start)
- **Overall Progress**: 0% complete

### Ready to Start

- DEV-001: Initialize Project Structure (1h)
- DEV-002: Install Core Dependencies (1h)
- DEV-003: Configure Build System (2h)
- DEV-004: Setup Database Schema (2h)

### Blocked (Waiting on Dependencies)

- FEAT-001: User Authentication (3h) - waiting on DEV-003
- TEST-001: Unit Test Framework (3h) - waiting on DEV-003

## How to Use This Example

### 1. Explore the Task Structure

Review the tasks in each category to understand the format and approach:

```bash
# Check development setup tasks
cat tasks/development/DEV-001-*.md
cat tasks/development/DEV-002-*.md

# Review feature implementation
cat tasks/features/FEAT-001-*.md

# Examine testing setup
cat tasks/testing/TEST-001-*.md
```

### 2. Understand Dependencies

Notice how tasks have dependencies that create a logical flow:

```bash
# DEV-001 must complete first (no dependencies)
# DEV-002 depends on DEV-001
# DEV-003, DEV-004 can run in parallel after DEV-001
# FEAT-001 and TEST-001 depend on DEV-003
```

### 3. Try the Commands

Execute the validation commands in each task to see how they work:

```bash
# From the project root, try some validation commands
npm run build    # From DEV-003 task
npm test         # From TEST-001 task
npm run lint     # From various tasks
```

### 4. Adapt to Your Project

Use this structure as a starting point for your own tasks:

```bash
# Copy this structure to your project
cp -r tasks-template/tasks/ your-project/tasks/

# Adapt categories and task IDs for your needs
# DEV, FEAT, TEST → customize to your project (API, UI, DATA, etc.)
# Update task IDs to match your numbering scheme
```

## Task Categories in This Example

### Development (DEV)

Tasks for project setup and tooling:

- DEV-001: Project structure and configuration
- DEV-002: Dependencies and development tools
- DEV-003: Build system and development server
- DEV-004: Database schema and migrations

### Features (FEAT)

Tasks for implementing new functionality:

- FEAT-001: User authentication system
- FEAT-002: User dashboard (blocked until FEAT-001 complete)
- FEAT-003: Data export functionality (blocked until FEAT-001 complete)

### Testing (TEST)

Tasks for testing infrastructure:

- TEST-001: Unit test framework and configuration
- TEST-002: Integration tests (would be added later)
- TEST-003: E2E testing setup (would be added later)

## Key Principles Demonstrated

### 1. **Dependency Management**

- Tasks clearly state what they depend on
- INDEX.md shows dependency graph with Mermaid diagrams
- Blocked tasks are clearly marked and explained

### 2. **Progressive Implementation**

- Start with foundation (DEV tasks)
- Build features on solid foundation (FEAT tasks)
- Add testing to ensure quality (TEST tasks)

### 3. **Clear Validation**

- Each task has specific success criteria
- Validation commands are provided
- Expected outputs are documented

### 4. **Structured Documentation**

- Consistent task format across all categories
- Detailed implementation steps
- References to related documentation

## Getting Started with Your Own Tasks

### 1. Copy the Structure

```bash
# Copy the tasks directory to your project
cp -r tasks-template/tasks/ your-project/tasks/
```

### 2. Update INDEX.md

- Change project name and description
- Update task counts and estimates
- Modify categories to match your project
- Set realistic timelines

### 3. Adapt Task Categories

Replace DEV/FEAT/TEST with categories relevant to your project:

- **API**: Backend API development
- **UI**: Frontend interface components
- **DATA**: Database and data processing
- **INFRA**: Infrastructure and deployment
- **DOCS**: Documentation and guides

### 4. Update Task IDs

Use your own numbering scheme:

- API-001, API-002, API-003...
- UI-001, UI-002, UI-003...
- DATA-001, DATA-002, DATA-003...

### 5. Customize Validation Commands

Replace the example commands with commands specific to your tech stack:

- **Web Apps**: `npm run build`, `npm test`, `npm run lint`
- **APIs**: `go build`, `go test`, `golangci-lint run`
- **Data**: `dbt build`, `python -m pytest`, `black --check`

## Next Steps

1. **Copy this structure** to your actual project
2. **Adapt the categories** to match your project type
3. **Create your first task** following the template format
4. **Update the INDEX.md** with your project details
5. **Start with DEV-001** (or equivalent) to establish foundation

This example demonstrates a complete, working task management system that you can immediately adapt to your own projects.

---

_Use [INDEX.md](INDEX.md) for current task status and progress tracking_
