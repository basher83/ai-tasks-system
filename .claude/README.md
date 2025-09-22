# Claude Code Custom Slah Commands for Task Management

## Commands

- `/create-task [Task category] [Task description]`
- `/execute-task [Task file path]`

## Create Task

Create a new task in the task management system by copying the template and filling out the details based on the arguments.

## Arguments

- @1 **Task Category**: Choose from DEV, FEAT, BUG, DOCS, TEST, PERF, SEC, REFACTOR
- @2 **Task Description**: Brief description of what needs to be done

Example usage:

- `/create-task FEAT implement-user-authentication`
- `/create-task DEV setup-database-migrations`
- `/create-task BUG fix-mobile-responsive-layout`

## Execute Task

- `/execute-task [Task file path]`

## Example

- `/create-task FEAT implement-user-authentication`
- `/execute-task path/to/tasks/features/FEAT-001-implement-user-auth.md`
