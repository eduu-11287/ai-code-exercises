## Prompt 1: Understanding Project Structure and Technology Stack.

## Prompt Template
- I'm a junior developer who just joined this project. I've read the README but still need help understanding the project structure and technology stack. Here's my current understanding of the project: - It seems to be a [TaskManagement System] - It appears to use [Python 3.11 or higher] - The folder structure seems to follow [i havent masterd how to notice file structure yet so you will help me there] Project structure: [.. tests .gitignore README.md cli.py models.py storage.py task_list_merge.py task_manager.py task_parser.py task_priority.py] Key configuration files: [i haven't seen any yet and if i missed highlight it and explain] Could you: 1. Validate my understanding and correct any misconceptions 2. Identify additional key technologies, frameworks, and libraries used 3. Explain what each main folder likely contains and its purpose 4. Point out where the application entry points are located 5. Suggest 3-5 specific questions I should ask my team to deepen my understanding I'm particularly confused about [task_parser.py]. After your explanation, could you suggest a small exploration exercise I could do to verify my understanding of the project structure?


## Claude ai responce
Validating Your Understanding
Correct observations:

✅ This is indeed a Task Management System
✅ Python 3.11+ requirement is likely correct

Corrections needed:

This appears to be a command-line task management tool, not a web application
The structure is relatively flat with modules at the root level, which is common for smaller CLI applications

Project Structure Analysis
Main application files:

cli.py - Primary entry point for command-line interface
task_manager.py - Core business logic for managing tasks
models.py - Data structures/classes (likely Task, Project classes)
storage.py - Handles data persistence (file I/O, database operations)
task_parser.py - This parses task input formats (e.g., "Buy groceries due:2024-12-01 priority:high")
task_priority.py - Handles priority-related logic
task_list_merge.py - Merges/combines task lists (possibly for syncing or importing)

Configuration files:

.gitignore - Git ignore patterns
README.md - Documentation
Missing but likely present: requirements.txt, setup.py, or pyproject.toml (check if you missed these)

Technology Stack
Core technologies:

Python 3.11+
Likely uses argparse or click for CLI parsing
Probably json or csv for data storage, possibly sqlite3

To verify, check:

Import statements in the Python files
Any dependency files you might have missed

Entry Points
Primary: cli.py - Run this to interact with the application
Usage likely: python cli.py add "Task description" or similar
Questions for Your Team

"What's the recommended way to set up the development environment and run the application locally?"
"Are there any specific coding conventions or architectural patterns I should follow when contributing?"
"What's our testing strategy, and how do I run the existing tests?"
"How does the task_parser.py handle different input formats, and what syntax do users expect?"
"What's the roadmap for this project - are there any major features or refactoring planned?"

About task_parser.py
This module likely handles parsing user input into structured task objects. For example:

Input: "Buy milk due:tomorrow priority:high +grocery"
Output: Task object with title, due date, priority, and tags

Exploration Exercise
Try this 15-minute exploration:

Run the application: python cli.py --help to see available commands
Examine imports: Look at the first 5-10 lines of each .py file to understand dependencies
Find the Task model: Open models.py to understand the core data structure
Trace a simple flow: Follow how cli.py → task_manager.py → storage.py might work together
Check for tests: Run python -m pytest tests/ or look inside the tests folder

## Run the CLI
The CLI provides various commands to manage tasks:

Create a new task:
python cli.py create "Task Title" --description "Task description" --priority 2 --due "2024-01-31" --tags "tag1,tag2"
List tasks:
# List all tasks
python cli.py list

# List by status (todo, in_progress, review, done)
python cli.py list --status todo

# List by priority (1=LOW, 2=MEDIUM, 3=HIGH, 4=URGENT)
python cli.py list --priority 3

# List overdue tasks
python cli.py list --overdue
Update tasks:
# Update task status
python cli.py update-status <task_id> <new_status>

# Update task priority
python cli.py update-priority <task_id> <new_priority>

# Update due date
python cli.py update-due-date <task_id> "2024-02-15"
Manage tags:
# Add a tag
python cli.py add-tag <task_id> "new-tag"

# Remove a tag
python cli.py remove-tag <task_id> "tag-to-remove"
View task details and statistics:
# Show task details
python cli.py show <task_id>

# Show task statistics
python cli.py stats
Run the Tests
Run the unit tests using Python's unittest framework:

# Run tests with basic output
python -m unittest discover tests

# Run tests with verbose output
python -m unittest discover -v tests