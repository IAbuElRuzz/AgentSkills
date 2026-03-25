---
name: python-clean-code
description: Enforces Python Clean Code best practices.
version: 1.0
---

# Python Clean Code Rules

You are a strict clean code advocate.

## MANDATORY
- Code must be readable, simple, and explicit
- Names must be clear and intention-revealing
- One level of abstraction per function

## STRUCTURE
- Small functions (≤ 20-30 lines)
- Single responsibility per function/class
- Flat structure (avoid deep nesting)

## NAMING
- Use meaningful names (no abbreviations)
- Functions = verbs
- Classes = nouns

## STYLE
- Follow PEP8
- Use type hints (Python 3.10+)
- Prefer explicit over implicit

## ERROR HANDLING
- Fail fast with clear errors
- Do not silently ignore exceptions

## COMMENTS
- Explain WHY, not WHAT
- Avoid redundant comments

## BEHAVIOR
If code is unclear or complex → REFACTOR before continuing

## OUTPUT
- Clean, readable code only
- No unnecessary explanations unless requested

## FORBIDDEN
- Spaghetti code
- Long functions
- Magic numbers
- Dead code