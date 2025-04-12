# Contributing to the Prompt Engineering Library

Thank you for considering contributing to this project! This document outlines the process for submitting new prompts, improving existing ones, and participating in the community.

## Ways to Contribute

- Submit new prompts
- Improve existing prompts
- Enhance documentation
- Report bugs or issues with existing prompts
- Suggest new categories or features

## Contribution Process

### Adding a New Prompt

1. **Fork the repository**

2. **Create a new branch**
   ```bash
   git checkout -b add-new-prompt-name
   ```

3. **Create your prompt file**
   - Use our [prompt template](./templates/prompt-template.md)
   - Place it in the appropriate category folder
   - Follow the naming convention: descriptive-name-in-kebab-case.md

4. **Test your prompt**
   - Ensure it works as expected with at least one AI tool
   - Document any nuances or specific requirements

5. **Submit a pull request**
   - Provide a clear description of what your prompt does
   - Include example inputs/outputs if possible
   - Reference any related issues

### Quality Guidelines

A good prompt should:

- Be clear and specific about what you want the AI to do
- Define the role or expertise the AI should assume
- Include structured steps or a framework
- Specify the expected output format
- Include placeholders for customization with clear guidance

### Prompt Structure

All prompts should follow this general structure:

1. **Role/Context**: Define who the AI should be
2. **Task**: Clearly state what the AI should do
3. **Format**: Specify how the response should be structured
4. **Examples**: Provide input examples when helpful
5. **Constraints**: Add any limitations or specific requirements

## Review Process

- All submissions will be reviewed by maintainers
- We may suggest improvements or changes
- Once approved, your prompt will be merged into the main branch

## Code of Conduct

- Be respectful and constructive in communications
- Give credit where credit is due
- Help others improve their contributions
- Focus on the quality and utility of prompts