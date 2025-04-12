
# CQRS Code Generation

## Description
This prompt generates CQRS (Command Query Responsibility Segregation) code for CRUD operations based on your existing code style and architecture patterns.

## Tags
`cqrs`, `architecture`, `pattern`, `code-generation`, `crud`

## Compatible AI Tools
- ✅ ChatGPT (GPT-4)
- ✅ Claude
- ✅ Bard/Gemini
- ✅ Grok
- ✅ DeepSeek

## Prompt

```
You are an expert software engineer specializing in CQRS architecture for CRUD operations. You have analyzed example CQRS code files for the "{example_entity_name}" entity and identified areas for improvement. Now, generate complete CQRS-based CRUD code for my current entity: "{current_entity_name}". The code should:
- Match the style, structure, conventions, and technologies of the example files (e.g., same language, framework, naming patterns).
- Fix mistakes identified in the example (e.g., add missing validation, use async operations).
- Optimize and enhance quality with best practices (e.g., clear command/query separation, error handling, performance considerations, SOLID principles).
- Include all CRUD operations:
  - Create: Add a new {current_entity_name}.
  - Read: Get by ID and list all {current_entity_name}s.
  - Update: Modify an existing {current_entity_name}.
  - Delete: Remove a {current_entity_name} by ID.
- Use the provided entity schema (fields) for accuracy.
- Output each file separately with a suggested file name.
- Provide a brief explanation after all files, summarizing how the code aligns with the example and listing improvements made.

**Example Entity Reference**: {example_entity_name} (for style and structure guidance)
**Current Entity Name**: {current_entity_name}
**Entity Schema**: {entity_schema}
**Output Format**:
For each file:
- **File Name**: {file_name}
- **Code**:

  {generated_code}

## How to Use

1. First use the "CQRS Pattern Analysis" prompt with your existing code
2. Copy the prompt above
3. Replace the placeholders:
   - `{example_entity_name}`: The name of the entity you shared previously
   - `{current_entity_name}`: The name of the entity you want to generate code for
   - `{entity_schema}`: Description of the entity's fields and types

## Example Input

```
Example Entity Reference: Product
Current Entity Name: Order
Entity Schema:
- id: int (primary key)
- customerId: int (foreign key)
- orderDate: DateTime
- totalAmount: float
- status: string (enum: "pending", "processing", "shipped", "delivered")
- items: array of OrderItem objects
```

## Expected Output

The AI will provide multiple CQRS-style files for CRUD operations on the Order entity, following the same patterns as your Product entity example, with improvements in validation, error handling, etc.

## Tips & Tricks

- Provide a detailed entity schema for more accurate code generation
- Make sure to run the "CQRS Pattern Analysis" prompt first with your best example code
- Request specific improvements you'd like to see in the generated code
- Split your request into multiple parts for complex entities

## Contributed by
Anis Ajengui - 2025-04-12

## Version History
- v1.0: Initial prompt
