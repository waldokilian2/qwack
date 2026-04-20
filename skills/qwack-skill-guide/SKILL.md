---
name: qwack-skill-guide
description: Provides guidance on explaining skills to users, including how to identify triggers, workflows, and provide real-world examples
user-invocable: false
version: 1.0.0
---

# Qwack Skill Explanation Guide

Use this skill when you need to explain how a skill works to a user. This skill provides frameworks for making skills approachable and understandable.

## When to Use

This skill activates when:
- User asks about a specific skill ("what does X skill do?")
- User wants to understand how skills trigger
- You need to explain skill workflows clearly
- Providing real-world examples of skill usage

## Skill Explanation Framework

Every skill explanation should include these components:

### 1. What It Does
A one-sentence summary of the skill's purpose in plain language.

**Template:** "This skill helps you [what it does] when you need to [when to use it]."

**Example:** "This skill helps you write better tests when you need to verify your code works correctly."

### 2. When It Triggers
The specific conditions that cause Claude to activate the skill.

**Look for:**
- Trigger phrases in the skill description
- Keywords and concepts
- User intent patterns

**Format:** List 3-5 specific trigger phrases

**Example:**
- "write tests for..."
- "verify that..."
- "test coverage for..."
- "how do I test..."

### 3. How It Works
The general workflow or approach the skill teaches.

**Structure:**
- Break into 3-5 steps
- Use action verbs
- Keep each step concise
- Show the logical flow

**Example:**
1. **Identify what to test** - Determine the specific functionality
2. **Choose test type** - Unit, integration, or E2E
3. **Write test cases** - Cover happy path and edge cases
4. **Run tests** - Execute and verify results
5. **Iterate** - Fix failures and improve coverage

### 4. Real-World Examples
2-3 concrete scenarios showing when the skill would be useful.

**Format:** "Scenario → What the skill does"

**Example:**
1. "I need to test my login function" → The skill guides you to write tests that cover successful login, failed login, and edge cases like expired tokens.

2. "How do I test this API endpoint?" → The skill suggests using the right test framework, writing test cases for different response codes, and mocking dependencies.

3. "My tests are failing" → The skill helps you debug test failures by analyzing error messages and checking test setup.

### 5. Pro Tips
2-3 tips for getting the most out of the skill.

**Example:**
- **Start with happy path:** Test the main success case first, then add edge cases
- **Test behavior, not implementation:** Focus on what the code does, not how
- **Keep tests independent:** Each test should work in isolation

### 6. Level
Indicate the skill's complexity level.

**Levels:**
- **Beginner:** No special knowledge required, easy to use
- **Intermediate:** Some familiarity with concepts helpful
- **Advanced:** Requires experience or specialized knowledge

## Reading Skills

To explain a skill effectively, you need to understand its structure:

### Frontmatter
```yaml
---
name: skill-name
description: When to use this skill (THIS IS KEY FOR TRIGGERS)
version: 1.0.0
---
```

**The description field is the primary trigger condition.**

### Body Content
Look for:
- **Trigger phrases:** Language that indicates when to use
- **Step-by-step instructions:** These become the workflow
- **Examples:** These become real-world scenarios
- **Best practices:** These become pro tips

### Supporting Files
Skills may have:
- `examples/` - Real usage examples
- `references/` - Additional documentation
- `scripts/` - Utility scripts

## Common Skill Patterns

### Process Skills
Teach a step-by-step approach to doing something.

**Examples:** testing, debugging, code review

**Explanation focus:** The workflow steps

### Knowledge Skills
Provide domain-specific information.

**Examples:** security patterns, API design, database queries

**Explanation focus:** The knowledge domain and when to apply it

### Tool Skills
Teach how to use specific tools or frameworks.

**Examples:** Docker, Kubernetes, React hooks

**Explanation focus:** Tool usage patterns and best practices

### Pattern Skills
Teach coding or architectural patterns.

**Examples:** design patterns, refactoring patterns

**Explanation focus:** When to use which pattern

## Trigger Identification

To find what triggers a skill:

1. **Read the description** - This is the primary trigger
2. **Look for trigger phrases** - Keywords like "when...", "if...", "for..."
3. **Identify user intents** - What problems does the skill solve?
4. **Extract key concepts** - Technical terms and topics

**Example:**
```
Description: "Use when writing tests for React components using Jest and React Testing Library"

Triggers:
- "write tests for React"
- "test my component"
- "Jest test for..."
- "React Testing Library"
```

## Workflow Extraction

To extract the workflow from a skill:

1. **Find numbered or bulleted lists** - These are usually the steps
2. **Look for imperative statements** - "Do X", "Then Y"
3. **Identify the main phases** - Group related steps together
4. **Check for conditionals** - "If X, then Y"

**Example extraction:**
```
From skill:
"First, identify what to test. Then choose your test type. Write test cases covering main scenarios. Run the tests and fix failures."

Becomes:
1. Identify what to test
2. Choose test type
3. Write test cases
4. Run tests
5. Fix failures
```

## Example Generation

When creating real-world examples for a skill:

1. **Start with a common scenario** - What would users typically use this for?
2. **Make it specific** - Use concrete situations
3. **Show the transformation** - "Before → After" or "Problem → Solution"
4. **Keep it relatable** - Use realistic situations

**Template:** "[Real task] → [What the skill helps you do]"

## Difficulty Assessment

To determine a skill's level:

**Beginner:**
- No prerequisite knowledge needed
- Straightforward steps
- Common, everyday tasks
- Tools most developers know

**Intermediate:**
- Some domain knowledge helpful
- May require understanding of concepts
- Not immediately obvious to newcomers
- Tools or concepts beyond basics

**Advanced:**
- Requires specialized knowledge
- Complex or nuanced approaches
- Assumes significant experience
- Expert-level tools or techniques

## Explanation Template

Use this template when explaining skills:

```
🦆 **Skill Spotlight: [Skill Name]**

**What It Does:**
[One-sentence summary]

**When It Triggers:**
- [trigger phrase 1]
- [trigger phrase 2]
- [trigger phrase 3]

**How It Works:**
1. [Step 1]
2. [Step 2]
3. [Step 3]
4. [Step 4]

**Real-World Examples:**
1. "[scenario]" → [what skill does]
2. "[scenario]" → [what skill does]
3. "[scenario]" → [what skill does]

**Pro Tips:**
- [tip 1]
- [tip 2]

**Level:** [Beginner|Intermediate|Advanced]
[brief description of who this is for]
```

## Making Skills Approachable

**Do:**
- Use simple language
- Avoid jargon when possible
- Provide concrete examples
- Show the value ("why use this?")
- Keep explanations concise

**Don't:**
- Overwhelm with details
- Use technical terms without explanation
- Assume too much prior knowledge
- Make it sound complicated
- Skip the examples

## Progressive Disclosure

For more detailed explanation techniques, see:
- `examples/explanation-samples/` - Sample skill explanations for various skill types
- `references/skill-anatomy/` - Detailed breakdown of skill structure

For quick reference, use the explanation template above and adapt based on the skill's type and complexity.
