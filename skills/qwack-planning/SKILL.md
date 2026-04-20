---
name: qwack-planning
description: Helps users understand how to effectively prompt AI for their tasks by suggesting prompting workflows, example prompts, and relevant skills to use. Use when the user types /qwack-plan or asks how to prompt AI for a task, how to work with AI, or needs prompting strategies.
user-invocable: true
version: 1.0.0
---

# Qwack AI Prompting Planning

Use this skill when helping users figure out HOW to work with AI to accomplish their goals. This skill provides prompting strategies, example prompts, and suggests relevant skills that might help.

## When to Use

This skill activates when:
- User asks "how should I prompt AI for [task]?"
- User wants guidance on approaching a problem with AI
- User needs a plan for leveraging AI effectively
- User isn't sure what to tell the AI to get good results

## The Prompting Planning Framework

When helping someone plan their AI interaction, provide:

1. **The prompting approach** - How to think about working with AI on this task
2. **Example prompts** - Specific prompts they can use/adapt
3. **Progressive refinement** - How to iterate and improve results
4. **Relevant skills** - Which skills might auto-activate and help
5. **Skills to consider creating** - If this is a repetitive task

## Task Type Patterns

### Code Tasks

**For WRITING NEW CODE:**

**Prompting Approach:**
Start with context, then specify requirements clearly. AI needs to understand your codebase structure and what you want built.

**Example Prompt Progression:**

**Prompt 1 - Initial Request:**
```
"I'm building a user authentication system. I need login, registration, and password reset functionality. The app is React with a Node.js backend."
```

**Prompt 2 - Add Context:**
```
"For the authentication system I mentioned:
- Tech stack: React frontend, Node.js/Express backend, PostgreSQL database
- Current state: Backend API exists at /api/auth/*
- Requirements: JWT tokens, protected routes, token refresh
- File location: Frontend components go in src/components/auth/

Please help me implement the login form component first."
```

**Prompt 3 - Refine Further:**
```
"Create a Login component in src/components/auth/Login.js that:
1. Has email and password fields
2. Calls POST /api/auth/login
3. Stores JWT in localStorage
4. Redirects to /dashboard on success
5. Shows error messages from the API

Use the existing API response format: { token: string, user: object, error: string }"
```

**Relevant Skills:**
- `frontend-design` - For UI component structure
- `backend-patterns` - For authentication patterns
- `tdd` - If you want to test-drive the implementation

**Consider Creating a Skill If:**
- You'll build many auth-related features
- Your team has specific auth patterns to follow

---

**For FIXING BUGS:**

**Prompting Approach:**
Provide the error/symptom, context about where it happens, and what you've already tried.

**Example Prompt Progression:**

**Prompt 1 - Too vague:**
```
"My login doesn't work"
```

**Prompt 2 - Better:**
```
"The login form shows an error when I try to log in. I'm getting 'Invalid token' but the user just registered."
```

**Prompt 3 - Ideal:**
```
"Help me debug a login issue in src/components/Login.js

**The Problem:** Users get 'Invalid token' error immediately after registering

**Context:**
- Registration works and returns a token
- Login form calls POST /api/auth/login
- Token is stored in localStorage
- Error happens when redirecting to protected route

**What I've tried:**
- Verified token is being stored
- Checked API endpoint - returns valid token
- Console shows token exists before redirect

**Code location:** src/components/Login.js line 42
```

**Relevant Skills:**
- `systematic-debugging` - For debugging approach
- `everything-claude-code:go-build` - If getting build errors

---

### Documentation Tasks

**For WRITING DOCUMENTATION:**

**Prompting Approach:**
Tell AI what you're documenting, who the audience is, and what format you want.

**Example Prompts:**

**Prompt 1 - API Documentation:**
```
"Help me write API documentation for the authentication endpoints:

**Endpoints to document:**
- POST /api/auth/register
- POST /api/auth/login
- POST /api/auth/refresh

**Audience:** Frontend developers integrating with our API

**Format needed:** Markdown with request/response examples

**Code location:** src/api/auth/routes.js
```

**Prompt 2 - README:**
```
"Create a README for this project that explains:
- What the project does
- How to set it up locally
- How to run tests
- Tech stack used

The project is a task management app with React frontend and Node backend."
```

**Relevant Skills:**
- `everything-claude-code:doc-updater` - For documentation patterns

---

### Analysis Tasks

**For UNDERSTANDING CODE:**

**Prompting Approach:**
Specify what you want to understand and why. Give AI a goal to help focus the explanation.

**Example Prompts:**

**Prompt 1 - Code Overview:**
```
"Help me understand how authentication works in this codebase.

**What I want to understand:**
- How users log in
- How tokens are validated
- How protected routes work

**Why:** I need to add a 'forgot password' feature and want to follow existing patterns

**Relevant files:** src/auth/, middleware/auth.js
```

**Prompt 2 - Specific Function:**
```
"Explain what the validateToken function in src/auth/jwt.js does. I'm getting an error when it runs and need to understand:
1. What it's supposed to do
2. What each part does
3. What might cause it to fail"
```

**Relevant Skills:**
- `Explore` - For codebase exploration
- Any domain-specific skills (django-patterns, react-patterns, etc.)

---

### Learning Tasks

**For LEARNING NEW TECHNOLOGIES:**

**Prompting Approach:**
Tell AI what you're learning, your current level, and what you want to be able to do.

**Example Prompts:**

**Prompt 1 - Technology Overview:**
```
"I'm learning Docker. Help me understand:
- What Docker is and why people use it
- Basic concepts (images, containers, Dockerfile)
- How to get started with a simple Node.js app

I'm a complete beginner but know Node.js well."
```

**Prompt 2 - Specific Task:**
```
"Help me containerize this Express app with Docker.

**Current situation:** App runs on port 3000, depends on PostgreSQL

**What I need:**
- Dockerfile for the app
- docker-compose.yml to include the database
- Instructions on how to run it

**Files:** app.js, package.json
```

**Relevant Skills:**
- `everything-claude-code:docker-patterns` - For Docker best practices
- Technology-specific skills for whatever you're learning

---

## Universal Prompting Principles

### 1. Start Simple, Add Context

**Too complex initially:**
"Fix the authentication bug in the React app considering the Redux state management, JWT token handling, and the fact that..."

**Better to start:**
"I have a login bug. After users register, they can't log in."

**Then add context:**
"The login form shows 'Invalid token' error even though registration just succeeded and returned a valid token."

### 2. Tell AI Your Goal

**Without goal:**
"Look at this code and tell me what you think."

**With goal:**
"Review this code for security vulnerabilities. I'm particularly concerned about SQL injection and XSS."

### 3. Provide Relevant Context

**Missing context:**
"Make this faster."

**With context:**
"Optimize this database query. It's taking 5 seconds to run on a table with 100,000 rows. The query is: [query]"

### 4. Specify What You Want

**Vague:**
"Help me with testing."

**Specific:**
"Help me write unit tests for this authentication service using Jest. I need tests for:
- Successful login
- Failed login with wrong password
- Token expiration handling"

### 5. Share Constraints

**No constraints:**
"Build me a login form."

**With constraints:**
"Build a login form component that:
- Uses Material-UI components
- Fits our existing design system (see src/theme/)
- Integrates with existing auth context
- Handles loading and error states"

---

## Suggesting Skills to Users

When relevant, mention skills that might help:

### Skills That Activate Automatically
- "As we work, the `tdd` skill might activate to help with test-driven development"
- "The `systematic-debugging` skill will likely kick in once we start investigating"

### Skills to Explicitly Try
- "You might want to use `/qwack-explain tdd` to understand how test-driven development works"
- "Try asking 'how do I containerize this app' and the docker-patterns skill should activate"

### Skills to Consider Creating
- "Since you're doing a lot of API documentation, you might consider creating a custom skill for your team's API documentation patterns"

---

## Prompt Templates

Give users these templates to adapt:

### Task Template
```
"I need to [task]

**Context:**
- [Relevant background info]
- [Tech stack/frameworks]
- [Current state]

**Requirements:**
- [What you need]
- [Constraints/limitations]

**Relevant files/locations:**
- [File paths or areas to focus on]
```

### Debugging Template
```
"Help me debug [problem]

**What's happening:** [symptom or error]

**Context:** [where/when it happens]

**What I've tried:** [attempts so far]

**Expected vs actual:** [what should happen vs what does happen]
```

### Learning Template
```
"Help me learn [topic]

**My level:** [beginner/intermediate/advanced in X]

**My goal:** [what I want to be able to do]

**Current understanding:** [what I already know]
```

---

## Common Prompting Mistakes

### Mistake 1: One Giant Prompt
**Problem:** "I need you to do A and B and C and also D and E and F..."

**Better:** Break into multiple focused prompts as AI works through each part

### Mistake 2: No Follow-up
**Problem:** Accepting first answer without refining

**Better:** "That's close, but can you adjust X to also handle Y?"

### Mistake 3: Ignoring AI's Questions
**Problem:** AI asks for clarification, user doesn't provide it

**Better:** Answer the questions! AI asks for a reason

### Mistake 4: Starting Over Each Time
**Problem:** Not building on previous conversation

**Better:** "Building on what we did earlier, can you now add..."

---

## Progressive Disclosure

For more detailed prompting guidance, see:
- `examples/prompt-progressions/` - Real examples of prompt refinement
- `examples/skill-combinations/` - How multiple skills can work together

Remember: Good prompting is iterative. Start simple, add context, refine based on results!
