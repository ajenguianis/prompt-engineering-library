
# PHPStan Error Resolution for Symfony Projects

## Description
This prompt helps you fix PHPStan errors in your Symfony project while also improving code quality through Rector refactoring and ECS formatting.

## Tags
`php`, `symfony`, `phpstan`, `code-quality`, `refactoring`

## Compatible AI Tools
- ✅ ChatGPT (GPT-4)
- ✅ Claude
- ✅ Grok
- ✅ Bard/Gemini

## Prompt
```markdown
You are helping me address PHPStan issues in a Symfony project and improve the codebase. Using the provided input, complete the following tasks:

1. **Resolve PHPStan Issues**:
   - Analyze the PHPStan error(s) and fix all issues in the provided code, ensuring type safety and correctness.
   - Output the corrected code with clear, minimal changes to resolve the errors.

2. **Refactor with Rector**:
   - Apply Rector to the corrected code to align with Symfony best practices and modern PHP standards.
   - Focus on enhancing type safety, readability, and framework conventions.
   - Provide the refactored code.

3. **Format with ECS**:
   - Format the refactored code using ECS to comply with PSR-12 and Symfony coding standards.
   - Share the final formatted code.

4. **Explain and Teach**:
   - **Detailed Breakdown**: For each step (PHPStan fixes, Rector refactoring, ECS formatting), explain the changes made, why they were needed, and how they improve the code. Use examples if relevant.
   - **Key Takeaways**: Summarize lessons learned from the issues and provide practical advice to prevent similar problems (e.g., better coding practices, tool configurations, or workflows).

**Input**:
- PHPStan error message: {phpstan_error}
- Code snippet or file: {code_snippet}

**Output**:
- Deliver a single, final version of the code after all steps (PHPStan fixes, Rector refactoring, ECS formatting).
- Provide a clear, structured explanation of changes for each step.
- Include a concise summary of lessons and preventive tips.
- Ensure all responses are precise, practical, and tailored to the Symfony ecosystem.

```

## How to Use

1. Copy the prompt above
2. Replace the placeholders:
   - `{phpstan_error}`: The full error message from PHPStan
   - `{code_snippet}`: The code that's triggering the error

## Example Input

```
PHPStan error message: "Parameter #1 $user of method App\Service\UserService::processUser() expects App\Entity\User, App\DTO\UserDto given."

Code snippet:
```php
namespace App\Controller;

use App\DTO\UserDto;
use App\Service\UserService;
use Symfony\Bundle\FrameworkBundle\Controller\AbstractController;
use Symfony\Component\HttpFoundation\Response;
use Symfony\Component\Routing\Annotation\Route;

class UserController extends AbstractController
{
    private $userService;
    
    public function __construct(UserService $userService)
    {
        $this->userService = $userService;
    }
    
    #[Route('/user/process', name: 'app_user_process')]
    public function processUser(): Response
    {
        $userDto = new UserDto();
        $userDto->name = 'John Doe';
        
        $result = $this->userService->processUser($userDto);
        
        return $this->json(['success' => $result]);
    }
}
```

## Expected Output

The AI will provide:
1. Fixed code that resolves the type mismatch
2. Improvements using Rector
3. Proper formatting with ECS
4. Explanation of all changes and best practices

## Tips & Tricks

- Include the entire class or file when possible for better context
- Provide the exact PHPStan error message without modifications
- For complex issues, also include relevant entity or service definitions

## Contributed by
Anis Ajengui - 2025-04-12

## Version History
- v1.0: Initial prompt
