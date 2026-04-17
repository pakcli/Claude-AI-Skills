---
name: markdown-writer
description: Create polished, well-structured markdown files (.md) for blogs, guides, documentation, notes, and technical writing. Use this skill whenever the user asks to write markdown content, create .md files, write documentation, draft blog posts, build knowledge bases, generate README files, or produce any markdown-formatted document. Trigger even if they don't explicitly say "markdown" but mention writing guides, technical documentation, tutorials, knowledge articles, or formatted text files. This skill handles everything from structure planning to final formatting to ensure professional output.
---
 
# Markdown Writer Skill
 
A comprehensive guide for creating high-quality, well-structured markdown documents. This skill covers everything from planning and organizing content to formatting, styling, and best practices for professional markdown output.
 
## When to Use This Skill
 
Use this skill when:
- Creating blog posts, articles, or long-form content in markdown
- Writing technical documentation, guides, or tutorials
- Building README files, API documentation, or knowledge bases
- Generating structured notes, study guides, or checklists
- Converting content to markdown format
- Organizing complex information with proper heading hierarchy
- Adding code blocks, tables, lists, and other markdown elements
- Creating professional documents that need clean formatting
 
## Core Workflow
 
1. **Plan the Structure** — Understand what the user needs and create a logical outline
2. **Write the Content** — Compose clear, well-organized markdown with proper formatting
3. **Format Professionally** — Apply markdown best practices for readability and style
4. **Save and Present** — Create the .md file and present it to the user
 
---
 
## Part 1: Planning & Structure
 
### Understanding the Request
 
Before writing, clarify:
- **Purpose**: Blog post? Documentation? Guide? Knowledge base?
- **Audience**: Technical experts? Beginners? General audience?
- **Length**: Brief (500-1000 words)? Standard (1500-3000)? Comprehensive (5000+)?
- **Tone**: Formal? Conversational? Technical? Creative?
- **Key Topics**: What are the main sections/ideas to cover?
 
### Creating an Outline
 
Start with a clear structure. Most markdown documents follow this pattern:
 
```
# Main Title
## Introduction/Overview
## Section 1
## Section 2
## Section 3
## Conclusion/Summary
## (Optional) Additional Resources
```
 
For more complex docs:
- Use H2 (##) for major sections
- Use H3 (###) for subsections
- Use H4 (####) only for detailed breakdowns
- Limit to 4 heading levels for clarity
 
---
 
## Part 2: Writing Best Practices
 
### Heading Hierarchy
 
✅ DO:
```markdown
# Main Title (use once at top)
## Major Section
### Subsection
#### Minor detail (rarely needed)
```
 
❌ DON'T:
- Skip heading levels (don't jump from H1 to H3)
- Use H5+ unless absolutely necessary
- Use multiple H1 headings in one document
 
### Content Organization
 
**Use clear transitions** between sections. Connect ideas logically.
 
**Break up walls of text** with:
- Bullet lists (for non-sequential items)
- Numbered lists (for steps, processes, ranked items)
- Subheadings (to organize long sections)
- Code blocks (to show examples)
- Tables (to compare options side-by-side)
 
### Code Blocks
 
Always use proper syntax highlighting:
 
```markdown
\`\`\`python
def hello_world():
    print("Hello, World!")
\`\`\`
```
 
Supported languages: python, javascript, bash, sql, json, html, css, java, c++, etc.
 
#### Tree Output Formatting
 
When the user inputs tree structures with triple backticks and `---` markers, preserve them exactly:
 
```tree
---
some-file/
├── file1.txt
├── file2.md
└── subfolder/
    ├── nested1.js
    └── nested2.py
---
```
 
**IMPORTANT**: When reproducing tree outputs in markdown:
 
- ✅ **Preserve the exact opening line**: ` ```tree ` followed by `---` (can be on same line or next line)
- ✅ **Preserve the exact closing line**: `---` followed by ` ``` `
- ✅ **Keep all tree characters**: Box-drawing characters (├──, └──, │), pipes, and spacing exactly as shown
- ✅ **Do NOT overwrite or modify** variable names, code references, or links within the tree (e.g., if a file is named `${VAR}` or `[link](url)`, keep it EXACTLY as provided - never rewrite these)
- ✅ **Maintain indentation** precisely as shown - no changes to spacing or structure
 
**Example of correct tree preservation with variables and links:**
 
```tree
---
project/
├── src/
│   ├── ${OUTPUT_DIR}/results.md
│   └── [config](./config.json)
├── docs/
│   └── README.md
└── ${BUILD_FOLDER}/output.txt
---
```
 
**Key rule**: Variable references like `${OUTPUT_DIR}` and `${BUILD_FOLDER}` are preserved EXACTLY as-is, and the link `[config](./config.json)` remains UNCHANGED. Never modify or rewrite any names or references inside tree structures - output them exactly as input, character-for-character.
 
### Lists
 
**Bullet lists** (unordered):
```markdown
- Item one
- Item two
  - Nested item
  - Another nested
- Item three
```
 
**Numbered lists** (ordered):
```markdown
1. First step
2. Second step
   3. Sub-step
   4. Another sub-step
5. Third step
```
 
#### Hierarchical Indentation (Outline/Tab Structure)
 
When the user provides content with **hierarchical tab/indentation levels** (like an outline or project structure), preserve the exact nesting structure in markdown using nested lists:
 
**Original hierarchical structure (with tabs):**
```
Project
	Title: My Project
	Description: ...
	Skripsi
		Bab 1
			latar belakang
				Why it's serious
					The narrative...
```
 
**Convert to markdown preserving hierarchy:**
```markdown
- Project
  - Title: My Project
  - Description: ...
  - Skripsi
    - Bab 1
      - latar belakang
        - Why it's serious
          - The narrative...
```
 
**IMPORTANT RULES for hierarchical content:**
 
- ✅ **Preserve indentation depth exactly** - Count the tabs/levels from the source and match them in markdown nesting
- ✅ **Use consistent spacing** - Each nesting level uses 2 spaces indentation in markdown
- ✅ **Maintain hierarchy order** - Don't flatten or reorder the structure
- ✅ **Keep all text content unchanged** - Preserve every word, link, and reference exactly as provided
- ✅ **Handle mixed content types** - If some items are headings, descriptions, or links, keep them in their correct nested positions
- ✅ **Don't restructure** - Never reorganize the hierarchy (don't move items between levels or change their parent-child relationships)
 
**Example with complex content:**
 
```markdown
- Project
  - Title: Knowledge Platform
  - Date: 04/2026
  - Skripsi
    - Bab 1: Latar Belakang
      - Why It's Serious
        - The narrative around global issues is controlled by outside pressure
        - Evidence
          - [JHL congratulates Rabbi Yehuda Kaploun](https://www.youtube.com/watch?v=tpQb9DWEe1c)
            - Quoted transcript:
              - 00:00:00: The president is sending a very strong message
              - 00:00:02: Think about it. Ironically, I get off a plane...
    - Bab 2: Glossary
      - What is Zionism?
    - Bab 3: Requirements and Flow Chart
```
 
**Key principle**: The user's outline structure IS the hierarchy you should represent. Each tab/indent level in their source becomes a nesting level in markdown lists. This preserves the original organizational intent while making it properly formatted markdown.
 
---
 
## CRITICAL: NO RESTRUCTURING POLICY
 
**When you receive content with any structure (hierarchical, outline, nested, etc.):**
 
### ✅ ALWAYS DO:
- **Preserve EXACT hierarchy** - Keep every indentation level exactly as provided
- **Keep ALL content unchanged** - No rewording, no reorganizing, no editing
- **Maintain original numbering** - If items are numbered (1, 2, 3 or a, b, c), keep those exact numbers
- **Preserve formatting intent** - If it's a list, keep it as a list; if it's text, keep it as text
- **Output ONLY in markdown** - Convert to proper markdown syntax, nothing else
 
### ❌ NEVER DO:
- **Restructure the content** - Don't reorganize, shuffle, or change hierarchy order
- **Change numbering** - Never renumber items or change their sequence
- **Convert to headings** - Don't turn list items into H1/H2/H3 headings unless explicitly asked
- **Reorganize sections** - Keep the exact order provided
- **Add commentary** - Don't add explanations or restructure rationale
- **Flatten structures** - Don't remove nesting levels
- **Reword content** - Keep every word exactly as provided
- **Interpret intent** - Don't assume better organization; respect the user's structure as absolute
 
### The Rule
**If you say nothing about restructuring, I do NOTHING but format to markdown.**
 
The user's structure = the correct structure. Period.
 
**Examples of what NOT to do:**
 
❌ User provides: "Project → Title → Description → Skripsi" 
❌ DON'T turn "Project" into a H1 heading unless told
❌ DON'T reorganize sections
❌ DON'T split into multiple documents
❌ DON'T add new sections
 
✅ DO convert exactly to nested list format preserving structure
✅ DO keep "Project" as a list item at the top level
✅ DO preserve every level exactly
 
**This applies to:**
- Outline structures with tabs
- Numbered/lettered hierarchies
- Mixed content (headings + descriptions + links)
- Any user-provided structure with intentional organization
 
**The content is sacred. The structure is sacred. Only the markdown syntax changes.**
 
### Emphasis
 
```markdown
*italic text* or _italic text_
**bold text** or __bold text__
***bold italic*** or ___bold italic___
~~strikethrough~~
`inline code`
```
 
### Links and Images
 
**Links:**
```markdown
[Link text](https://example.com)
[Link with title](https://example.com "Hover text")
```
 
**Images:**
```markdown
![Alt text](image-path.png)
![Alt text](image-path.png "Image title")
```
 
### Blockquotes
 
```markdown
> This is a blockquote
> It can span multiple lines
>> And be nested
```
 
### Horizontal Rules
 
```markdown
---
or
***
or
___
```
 
### Tables
 
```markdown
| Column 1 | Column 2 | Column 3 |
|----------|----------|----------|
| Data 1   | Data 2   | Data 3   |
| Data 4   | Data 5   | Data 6   |
```
 
**Alignment:**
```markdown
| Left | Center | Right |
|:-----|:------:|------:|
| L1   |  C1    |    R1 |
```
 
---
 
## Part 3: Formatting & Style Guidelines
 
### Front Matter (Optional)
 
For blogs and articles, consider adding YAML front matter:
 
```markdown
---
title: Article Title
date: 2024-04-08
author: Your Name
tags: [tag1, tag2, tag3]
---
```
 
### Introduction Section
 
Start with a compelling intro that:
- Clearly states what the document covers
- Explains why it matters
- Sets reader expectations
- Hooks the audience
 
### Section Structure Pattern
 
For each major section:
 
```markdown
## Section Title
 
Brief intro explaining what this section covers.
 
### Key Point 1
Explain this concept with examples.
 
### Key Point 2  
Build on the previous concept.
 
**Key takeaway:** Summarize the main idea.
```
 
### Conclusion
 
Wrap up with:
- Summary of main points
- Key takeaways
- Call to action (if relevant)
- Resources for further learning
 
### Additional Sections (as needed)
 
```markdown
## Resources
- [Link 1](url)
- [Link 2](url)
 
## See Also
- Related topic 1
- Related topic 2
 
## Changelog / Updates
- v1.0 - Initial release
- v1.1 - Added new section
```
 
---
 
## Part 4: Content Best Practices
 
### Writing Tips
 
✅ Keep paragraphs short (3-4 sentences max for readability)
✅ Use active voice ("Claude creates" not "Markdown files are created by Claude")
✅ Write conversationally but professionally
✅ Define technical terms before using them
✅ Use examples to illustrate concepts
✅ Add relevant code snippets when explaining technical content
 
❌ Avoid walls of text
❌ Don't overuse CAPS
❌ Avoid jargon without explanation
❌ Don't use too many exclamation marks!
 
### Technical Documentation Specific
 
For API docs, guides, and technical writing:
 
**Include examples:**
```markdown
### Example Usage
 
Here's how to use this feature:
 
\`\`\`python
# Initialize the client
client = MyClient()
 
# Make a request
response = client.request()
\`\`\`
```
 
**Document parameters:**
```markdown
#### Parameters
- `param1` (string): Description of param1
- `param2` (integer): Description of param2, default is 0
- `param3` (optional): Description of optional param
```
 
**Show expected output:**
```markdown
#### Expected Output
 
When successful, you'll receive:
 
\`\`\`json
{
  "status": "success",
  "data": {...}
}
\`\`\`
```
 
### Blog/Article Specific
 
For blogs and news-style content:
 
- **Hook readers** in the first paragraph
- **Use descriptive headings** that summarize content
- **Break up text** with plenty of visual elements
- **Add personality** while staying professional
- **Close with reflection** or call-to-action
- **Include metadata** (author, date, tags)
 
---
 
## Part 5: Common Mistakes to Avoid
 
| Mistake | Problem | Fix |
|---------|---------|-----|
| Inconsistent heading levels | Confusing structure | Use proper hierarchy (1→2→3) |
| No introduction | Reader confusion | Add 2-3 sentence intro |
| Wall of text | Hard to read | Add subheadings and lists |
| Bad code formatting | Unreadable examples | Use proper code blocks with language |
| Broken links | Frustrating for readers | Verify all links work |
| No conclusion | Abrupt ending | Summarize key points |
| Too many images | Slow to load | Use sparingly, optimize size |
| Unclear language | Reader frustration | Use simple, direct language |
 
---
 
## Part 6: File Naming & Organization
 
### File Naming Conventions
 
```
# Good names:
- my-blog-post.md
- api-documentation.md
- quick-start-guide.md
- README.md
 
# Avoid:
- My Blog Post.md (spaces)
- api_documentation_FINAL_v2.md (confusing)
- doc.md (too vague)
```
 
### Directory Organization (for multi-file projects)
 
```
project/
├── README.md (main overview)
├── CONTRIBUTING.md (contribution guidelines)
├── CHANGELOG.md (version history)
├── docs/
│   ├── getting-started.md
│   ├── api-reference.md
│   └── examples.md
└── guides/
    ├── tutorial-1.md
    └── troubleshooting.md
```
 
---
 
## Workflow for Creating Markdown Files
 
### Step 1: Understand the Need
Ask the user clarifying questions about purpose, audience, and scope.
 
### Step 2: Create Outline
Draft a table of contents or outline for the document.
 
### Step 3: Write Content
Compose the markdown with proper formatting.
 
### Step 4: Format & Polish
- Ensure heading hierarchy is correct
- Check that lists are consistent
- Verify code blocks have language markers
- Test that links work
- Fix any grammar or clarity issues
 
### Step 5: Create & Present File
Save the .md file to `/mnt/user-data/outputs/` and present it to the user using the `present_files` tool.
 
---
 
## Quick Reference
 
### Markdown Syntax Cheat Sheet
 
```markdown
# H1 Heading
## H2 Heading
### H3 Heading
 
**bold** *italic* ***bold italic***
 
- Bullet list
  - Nested bullet
1. Numbered list
   2. Nested numbered
 
[Link](url)
![Image](path.png)
 
\`\`\`language
code block
\`\`\`
 
> Blockquote
 
| Table | Header |
|-------|--------|
| Cell  | Cell   |
```
 
---
 
## Tips for Specific Document Types
 
### README Files
- Lead with what the project does
- Include installation instructions
- Provide usage examples
- Link to documentation
- Add badge/status info if relevant
 
### Blog Posts
- Write engaging headlines
- Use conversational tone
- Include personal touches
- Structure with clear sections
- End with takeaways or CTA
 
### Technical Guides
- Start with prerequisites
- Use step-by-step structure
- Include warnings/notes for important info
- Add screenshots/diagrams where helpful
- Provide example code
 
### API Documentation
- Document every endpoint
- Show request/response examples
- Include error codes and meanings
- Provide curl/SDK examples
- Add authentication details
 
---
 
## Final Checklist
 
Before presenting the file to the user:
 
- [ ] Heading hierarchy is correct and logical
- [ ] All sections have clear introductions
- [ ] Code blocks use proper language markers
- [ ] Lists are consistent (bullet vs. numbered)
- [ ] Links are working (if external, verify valid)
- [ ] No grammar or spelling errors
- [ ] Content flows logically
- [ ] File name is descriptive and lowercase
- [ ] File is saved to `/mnt/user-data/outputs/`
- [ ] Markdown renders properly without errors
 
---
 
Good luck creating amazing markdown! 🚀