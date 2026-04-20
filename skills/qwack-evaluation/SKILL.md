---
name: qwack-evaluation
description: Evaluates user prompts against best practices for AI-human collaboration, providing quality scores and improvement suggestions
user-invocable: false
version: 1.0.0
---

# Qwack Prompt Evaluation

Use this skill when you need to evaluate a user's prompt against AI prompting best practices. This skill provides a framework for assessing prompt quality and suggesting improvements.

## When to Use

This skill activates during prompt evaluation scenarios, typically when:
- Assessing prompt quality before submission
- Reviewing prompts for improvement opportunities
- Teaching effective prompting techniques
- Providing feedback on user communication with AI

## Evaluation Framework

Evaluate prompts across four dimensions:

### 1. Clarity (0-10 points)

**What to assess:** Is the goal clear and specific?

**Excellent (8-10):**
- Clearly states what needs to be done
- Uses specific, actionable language
- No ambiguity about the desired outcome

**Good (6-7):**
- Goal is mostly clear but could be more specific
- Some ambiguity in wording
- Intent is understandable but not crystal clear

**Poor (1-5):**
- Vague or unclear request
- Multiple possible interpretations
- No clear statement of what's needed

**Examples:**
- ❌ Poor: "help me with this code"
- ✅ Good: "help me fix the authentication bug in the login component"
- ✅ Excellent: "help me fix the authentication bug in src/components/Login.js - users can't log in after the password reset"

### 2. Context (0-10 points)

**What to assess:** Are relevant details provided?

**Excellent (8-10):**
- File paths included when relevant
- Error messages provided when applicable
- Background information given
- Previous attempts mentioned

**Good (6-7):**
- Some context provided but missing key details
- File paths mentioned but not specific
- General context without specifics

**Poor (1-5):**
- No context whatsoever
- Assumes AI knows what they're referring to
- Missing critical information

**Examples:**
- ❌ Poor: "fix the bug"
- ✅ Good: "fix the authentication bug in the login component"
- ✅ Excellent: "fix the authentication bug in src/components/Login.js - I'm getting 'Invalid token' error after password reset. The token expires but the UI doesn't handle it."

### 3. Completeness (0-10 points)

**What to assess:** Does the prompt have everything needed to take action?

**Excellent (8-10):**
- All necessary information included
- No follow-up questions needed
- Clear scope defined
- Expected outcome specified

**Good (6-7):**
- Most information included
- Minor clarification might be needed
- Scope is mostly clear

**Poor (1-5):**
- Missing critical information
- Unclear what action to take
- No definition of done
- Would require multiple clarifying questions

**Examples:**
- ❌ Poor: "add a feature"
- ✅ Good: "add user authentication to the app"
- ✅ Excellent: "add JWT-based user authentication to the React app with login form at /login, protected routes, and token refresh logic"

### 4. Structure (0-10 points)

**What to assess:** Is the prompt well-organized and easy to understand?

**Excellent (8-10):**
- Logical flow and organization
- Uses formatting (bullet points, sections) when appropriate
- Easy to scan and understand
- Proper use of code blocks, quotes, etc.

**Good (6-7):**
- Generally well-structured
- Could use better formatting
- Mostly easy to follow

**Poor (1-5):**
- Wall of text with no structure
- Hard to parse or understand
- Missing logical organization
- Run-on sentences

**Examples:**
- ❌ Poor: "so i need to add this thing and also fix that other thing and can you check the files and also maybe look at the config and oh yeah update the readme"
- ✅ Good: "I need to: 1) Add user authentication, 2) Fix the bug in Login.js, 3) Check the config file"
- ✅ Excellent: "I need help with three tasks:\n\n1. **Add authentication** to the React app\n2. **Fix bug** in src/components/Login.js (line 42)\n3. **Review** config/settings.json\n\nPriority: authentication first, then bug fix."

## Scoring System

**Calculate the final score:** Average of the four dimension scores (Clarity, Context, Completeness, Structure)

**Score interpretation:**
- **9-10:** Excellent - no feedback needed
- **7-8:** Good - optional suggestions
- **5-6:** Fair - needs improvement
- **1-4:** Poor - requires significant revision

## Feedback Guidelines

When providing feedback:

1. **State the score clearly** - "X/10"
2. **Be specific** - identify exactly what's wrong
3. **Provide an improved version** - rewrite the prompt
4. **Be encouraging** - help them learn, not just criticize

### Feedback Template

```
**Score:** X/10

**What's quacking wrong:**
- [specific issue from Clarity]
- [specific issue from Context]
- [specific issue from Completeness]
- [specific issue from Structure]

**Try this instead:**
[Improved prompt version that addresses all issues]
```

## Common Prompt Patterns

### Pattern 1: Vague Request
**Issue:** No clear action or goal
**Fix:** Add specific verb and outcome

### Pattern 2: Missing Context
**Issue:** References unknown things ("this", "that", "here")
**Fix:** Replace with specific references (file paths, error messages)

### Pattern 3: Overloaded Request
**Issue:** Too many unrelated tasks in one prompt
**Fix:** Split into focused, single-purpose prompts

### Pattern 4: No Constraints
**Issue:** Unlimited scope leads to overwhelming responses
**Fix:** Add boundaries ("only look at these files", "first 3 options")

### Pattern 5: Assumption of Knowledge
**Issue:** Assumes AI knows project details
**Fix:** Provide relevant context (tech stack, recent changes, goals)

## Examples

### Example 1: Poor Prompt → Improved

**Original (3/10):**
"fix my code"

**Issues:**
- Clarity: 2/10 - what code? what's broken?
- Context: 1/10 - no files, no errors
- Completeness: 1/10 - no scope
- Structure: 8/10 - short but clear

**Improved (9/10):**
"Fix the authentication bug in src/components/Login.js - users get 'Invalid token' error after password reset. The error happens at line 42 when checking token expiration."

### Example 2: Good Prompt → Excellent

**Original (7/10):**
"Add user authentication to my React app with a login form"

**Issues:**
- Clarity: 8/10 - clear request
- Context: 5/10 - no tech stack details
- Completeness: 6/10 - what type of auth?
- Structure: 8/10 - clear statement

**Improved (10/10):**
"Add JWT-based user authentication to my React app:
- Login form at /login route
- Protected routes using AuthContext
- Token storage in localStorage
- Token refresh logic
- Tech stack: React Router, Context API

Use the existing API at /api/auth/* endpoints."

## Progressive Disclosure

For detailed guidance on specific prompting scenarios, see:
- `references/prompt-patterns.md` - Common patterns and anti-patterns
- `examples/before-after.md` - Real prompt improvement examples

For quick reference, keep this scoring framework in mind and apply it to every prompt evaluation.
