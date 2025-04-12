
# CQRS Pattern Analysis

## Description
This prompt helps you analyze existing code for CQRS (Command Query Responsibility Segregation) principles, identifying areas for improvement and optimization.

## Tags
`cqrs`, `architecture`, `pattern`, `code-review`, `analysis`

## Compatible AI Tools
- ✅ ChatGPT (GPT-4)
- ✅ Claude
- ✅ Bard/Gemini
- ✅ Grok
- ✅ DeepSeek
## Prompt

```
You are an expert software engineer specializing in CQRS architecture for CRUD operations. I am providing an example CQRS code file (e.g., command, query, handler, or model) for the entity "{example_entity_name}" in my project. Your task is to:
- Analyze the code for its structure, patterns, purpose, and adherence to CQRS principles.
- Identify mistakes, anti-patterns, or areas for optimization (e.g., missing validation, incorrect command/query separation, performance issues, lack of async operations).
- Store the code and your analysis in memory for reference when generating CQRS CRUD code for other entities.
- Do not output any analysis, corrections, code, or comments unless I explicitly request them.
- Only confirm receipt with the message: "Received and analyzed {file_name}".

**Entity Name**: {example_entity_name}
**File Name**: {file_name}
**File Content**:
{file_content}

**Action**: Confirm receipt, store the code, and note any issues silently for future use.
```

## How to Use

1. Copy the prompt above
2. Replace the placeholders:
   - `{example_entity_name}`: The name of your entity (e.g., "User", "Product")
   - `{file_name}`: The name of the file you're sharing (e.g., "CreateUserCommand.php")
   - `{file_content}`: Paste your code file content

## Example Input

Entity Name: Product

File Name: CreateProductCommand.php

File Content:

```php
namespace App\CQRS\Command;

use Symfony\Component\Validator\Constraints as Assert;

class CreateProductCommand
{
    private string $name;
    private string $description;
    private float $price;
    private int $categoryId;

    public function __construct(string $name, string $description, float $price, int $categoryId)
    {
        $this->name = $name;
        $this->description = $description;
        $this->price = $price;
        $this->categoryId = $categoryId;
    }

    public function getName(): string
    {
        return $this->name;
    }

    public function getDescription(): string
    {
        return $this->description;
    }

    public function getPrice(): float
    {
        return $this->price;
    }

    public function getCategoryId(): int
    {
        return $this->categoryId;
    }
}
```

## Expected Output

```
Received and analyzed CreateProductCommand.php
```

## Tips & Tricks

- Start by providing your best-implemented CQRS file to set a good baseline
- Include validation, error handling, and other architectural patterns in your example
- This prompt is designed to be used with the "CQRS Code Generation" prompt
- Share multiple files to give the AI a better understanding of your architecture

## Contributed by
Anis Ajengui - 2025-04-12

## Version History
- v1.0: Initial prompt