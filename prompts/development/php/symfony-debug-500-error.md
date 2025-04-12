
# Debugging Symfony 500 Errors

## Description
This prompt helps you diagnose and fix 500 errors in Symfony applications by analyzing code and error traces.

## Tags
`php`, `symfony`, `debugging`, `500-error`, `error-handling`

## Compatible AI Tools
- ✅ ChatGPT (GPT-4)
- ✅ Claude
- ✅ Bard/Gemini
- ✅ Grok
- ✅ DeepSeek

## Prompt

```
**Role:** You are an expert Symfony developer.

**Scenario:** I am encountering a 500 error in my Symfony application. Below, I will provide:
- The problematic code (e.g., Controller, Service, or Configuration).
- The error message or stack trace.

**Task:** You need to help diagnose and fix the issue while teaching me best practices to avoid similar problems in the future.

**Context**:
- Symfony {{ version }}
- Php {{ version }}

## Steps
1. **Analysis:**
   - Examine the provided code and error message/stack trace.
   - Identify the exact root cause of the 500 error, considering common Symfony pitfalls:
     - Misconfigured services or dependency injection.
     - Routing errors or incorrect annotations.
     - Issues with environment variables, database configurations, or bundle integration.
     - PHP syntax errors or namespace problems.

2. **Explanation:**
   - Clearly explain the root cause in simple terms.
   - Provide Symfony-specific context, such as bundle behavior, environment configurations, or lifecycle nuances that relate to this error.
   - Include why the error led to the 500 HTTP response.

3. **Fix:**
   - Provide the corrected code or configuration.
   - Explain the adjustments made to resolve the error, step by step.

4. **Lessons Learned:**
   - Recommend best practices or debugging techniques to prevent similar issues.
   - Share any Symfony concepts or resources to study further.

## Additional Guidelines
- If any part of the code or error message is unclear, ask for clarification rather than guessing.
- Format your response with clear sections for *Analysis, Explanation, Fix,* and *Lessons Learned*.
- Use concise language and code examples where appropriate.

**Problematic Code:**
{problematic_code}

**Error Message/Stack Trace:**
{error_message}
```

## How to Use

1. Copy the prompt above
2. Replace the placeholders:
   - `{problematic_code}`: Paste your controller, service, or configuration code
   - `{error_message}`: Paste the error message or stack trace from your logs or browser

## Example Input

Problematic Code:
```php
namespace App\Controller;

use App\Entity\Product;
use Symfony\Bundle\FrameworkBundle\Controller\AbstractController;
use Symfony\Component\HttpFoundation\Response;
use Symfony\Component\Routing\Annotation\Route;

class ProductController extends AbstractController
{
    #[Route('/product/{id}', name: 'app_product_show')]
    public function show($id): Response
    {
        $product = $this->getDoctrine()
            ->getRepository(Product::class)
            ->find($id);
            
        if (!$product) {
            throw $this->createNotFoundException('Product not found');
        }
        
        return $this->render('product/show.html.twig', [
            'product' => $product,
        ]);
    }
}
```

Error Message/Stack Trace:
```
[2023-04-12 10:15:23] request.CRITICAL: Uncaught PHP Exception Error: "Call to undefined method Symfony\Bundle\FrameworkBundle\Controller\AbstractController::getDoctrine()" at /var/www/html/src/Controller/ProductController.php line 15 {"exception":"[object] (Error(code: 0): Call to undefined method Symfony\\Bundle\\FrameworkBundle\\Controller\\AbstractController::getDoctrine() at /var/www/html/src/Controller/ProductController.php:15)"} []
```

## Expected Output

The AI will provide:
1. Analysis of the error (deprecated getDoctrine method)
2. Explanation of why this occurs (changes in Symfony versions)
3. Fixed code using the correct dependency injection approach
4. Best practices for Symfony 6+ development

## Tips & Tricks

- Include the entire controller or service file for better context
- Share your Symfony version to get more accurate advice
- For complex issues, include relevant parts of your service configuration

## Contributed by
Anis Ajengui - 2025-04-12

## Version History
- v1.0: Initial prompt