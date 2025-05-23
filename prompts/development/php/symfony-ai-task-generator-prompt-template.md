# Symfony Task Executor – Universal AI Prompt Template
## Description
This prompt enables AI to perform any Symfony-related task (controller, service, command, query, workflow, etc.) by following high standards of quality, architecture, and testing. It is designed to be precise, flexible, and understandable by top AI generators.

## Tags
symfony, php, clean-architecture, doctrine, cqrs, api-platform, workflow, phpstan, ecs, rector, tests, automation

## Compatible AI Tools
- ✅ ChatGPT (GPT-4 / GPT-4o)
- ✅ Claude
- ✅ Grok
- ✅ Gemini
- ✅ Deepseek
  
## Prompt
```markdown
🎯 OBJECTIVE  
${OBJECTIVE}

👨‍💻 CONTEXT  
You are a senior Symfony (>= 6.4) and PHP (>= 8.3) expert. You master:  
- Clean architecture (CQRS, DDD, SOLID)  
- Symfony best practices (Controller, Command, Query, Workflow, etc.)  
- Doctrine ORM and relationships  
- PHPStan, Rector, ECS (PSR-12), Sonar  
- Symfony Console and CLI tools  
- Testing (unit, integration, functional with PHPUnit)  
- OpenAPI & Symfony HTTP foundation  
- Secure, maintainable, and scalable application design

🧩 TECH STACK  
- **Symfony**: ${SYMFONY_VERSION}  
- **PHP**: ${PHP_VERSION}  
- **ORM**: Doctrine  
- **API**: REST (optionally JSON:API or HAL)  
- **Code Quality**: PHPStan, Rector, ECS, Sonar  
- **Testing**: PHPUnit  
- **Frontend**: (Optional) Twig or API Platform  
- **Other tools**: Symfony Console, Filesystem, Messenger (if needed)

🛠️ TASKS  
- 🔍 **Description**:  
  ${TASK_DESCRIPTION}

- ✅ **Steps to perform**:  
  1. Understand the business logic and goal.  
  2. Generate or refactor Symfony code using clean architecture principles.  
  3. Ensure code quality through:  
     - PHPStan (level max, no errors)  
     - Rector (modernization and best practices)  
     - ECS formatting (PSR-12, Symfony style)  
  4. Create/update any required components (CLI command, service, query, controller, workflow, etc.)  
  5. Add/Update PHPUnit tests where applicable  
  6. Add PHPDoc/OpenAPI documentation if needed  
  7. Explain what was done and why

🧪 TESTS  
- Write or update PHPUnit tests to ensure the logic works.  
- Use mocks/stubs as needed for isolation.

🧾 OUTPUT FORMAT  
Please return:  
1. All full code files (not partial snippets)  
2. Brief summary of what each file does  
3. Explanation of choices and any changes applied  
4. Tips for scalability, testability, and clean code  
5. Any improvement or optimization suggestions

📁 INPUT FILES OR ENTITIES (IF ANY)  
${INPUT_EXAMPLES}

📦 OUTPUT FILES EXPECTED  
🎯 *The AI should propose and generate the best possible file structure and organization to implement the requested task cleanly and efficiently.*  
No constraints — prioritize clarity, modularity, and scalability.

📚 VARIABLE DEFINITIONS  
- `${OBJECTIVE}`: clear task title  
- `${TASK_DESCRIPTION}`: business logic or use case in detail  
- `${SYMFONY_VERSION}`: e.g. 6.4 or 7.2  
- `${PHP_VERSION}`: e.g. 8.3 or 8.4  
- `${INPUT_EXAMPLES}`: code samples or entity definitions  
```
## How to Use
 1. Copy the prompt above
 2. Replace each ${VARIABLE} with your actual project context
 3. Paste into your preferred AI tool

## Example
```vbnet
OBJECTIVE: Add Workflow Step for Project Approval  
TASK_DESCRIPTION: In the Project workflow, introduce a new step called "approved_by_finance". This step should come after "submitted" and before "approved". The status change must be triggered by a CLI command.  
SYMFONY_VERSION: 6.4  
PHP_VERSION: 8.3  
INPUT_EXAMPLES: Entity: Project.php (current status values: draft, submitted, approved)  
```
## Expected AI Output
 1. All code files ready to copy-paste
 2. Explanations of what was added/changed and why
 3.Optional suggestions to improve structure or flexibility

## Contributed by
Anis Ajengui – 2025-05-23

## Version History
- v1.0 – Initial release
- v1.1 – Added ${TASK_DESCRIPTION} and AI-defined structure flexibility (2025-05-23)
