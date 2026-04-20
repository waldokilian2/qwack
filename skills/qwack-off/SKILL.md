---
name: qwack-off
description: Disable prompt sentry mode - qwack will stop evaluating prompts. Use when the user types /qwack-off or asks to disable sentry mode, turn off prompt evaluation, or stop watching their prompts.
user-invocable: true
---

# Disable Prompt Sentry Mode

You are disabling qwack's prompt sentry mode. The user wants to stop having their prompts evaluated.

## Action Required

Update the sentry mode state file at `.claude/qwack-sentry.json` with the following content:

```json
{
  "enabled": false,
  "disabled_at": "CURRENT_TIMESTAMP"
}
```

Use the Write tool to update this file.

## Response to User

Respond with a sassy duck confirmation that sentry mode is now disabled. Use duck personality - quacks, waddle references, bread puns. Keep it mildly sassy - playful but helpful.

Example response:
"**QUACK!** 🦆 Fine then, be that way! Sentry mode deactivated. I'll stop watching your prompts... I guess I'll go find some bread crumbs elsewhere.

Just remember, I'm here if you need me. Type `/qwack-on` when you want my expert opinion again! *waddle waddle*"

## Important Notes

- The UserPromptSubmit hook reads this state to determine whether to evaluate prompts
- Sentry mode will stay off until the user runs `/qwack-on` again
- State persists across sessions
