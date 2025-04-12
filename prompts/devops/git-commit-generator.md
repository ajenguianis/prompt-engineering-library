
# Git Commit Message Generator

## Description
This prompt generates concise, descriptive git commit messages based on diff content and contextual keywords.

## Tags
`git`, `commit`, `version-control`, `documentation`

## Compatible AI Tools
- ✅ ChatGPT (GPT-4)
- ✅ Claude
- ✅ GitHub Copilot

## Prompt

```markdown
You are an expert software engineer. Given the following git diff and keywords, generate a concise and descriptive commit message that summarizes the changes. Use the keywords to guide the context if they align with the diff. Start with an action verb (e.g., Add, Fix, Update, Remove), keep the summary under 50 characters, and include a detailed description if the changes are complex.

**Diff**:
{insert_diff_here}

**Keywords**:
{insert_keywords_here}

```

## How to Use

1. Copy the prompt above
2. Replace the placeholders:
   - `{insert_diff_here}`: Paste the git diff output (from `git diff` command)
   - `{insert_keywords_here}`: Add comma-separated words related to the context of the change

## Example Input

```
Diff:
diff --git a/src/components/Header.jsx b/src/components/Header.jsx
index 1234567..abcdefg 100644
--- a/src/components/Header.jsx
+++ b/src/components/Header.jsx
@@ -15,7 +15,7 @@ const Header = () => {
     <header className="app-header">
       <Logo />
       <nav>
-        <Link to="/">Home</Link>
+        <Link to="/">Dashboard</Link>
         <Link to="/profile">Profile</Link>
         <Link to="/settings">Settings</Link>
       </nav>

Keywords:
navigation, ui, rename, homepage
```

## Expected Output


Rename Home link to Dashboard in header navigation

Updates the main navigation label to better reflect that the 
homepage functions as a dashboard for logged-in users.


## Tips & Tricks

- Include only the relevant parts of the diff to get more focused commit messages
- Add specific keywords to guide the context when the changes might be ambiguous
- For larger commits with multiple changes, break down the diff into logical chunks

## Contributed by
Anis Ajengui - 2025-04-12

## Version History
- v1.0: Initial prompt
