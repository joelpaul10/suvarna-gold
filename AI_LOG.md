# AI_LOG

## Tools

AI assistance was used to draft the initial project structure, validation, API, UI, and documentation. All generated output should be reviewed before submission.

## Prompts used

1. “Implement validated Indian mobile and gold-weight request schemas. Reject net weight above gross weight with a field error and calculate pure gold and loan eligibility using paise and whole-rupee flooring.”
2. “Design a loan assistant that calls scheme, quote, and submit backend tools; the model must not calculate numbers and must ask for explicit confirmation before submitting.”

## Mistake caught

An initial review caught the risk of calculating loan values with floating-point rupees. The implementation now rounds gold value into integer paise and floors the final eligible loan to whole rupees. Required regression examples are in the automated tests.

## Limitation

This six-hour-sized implementation uses a deterministic guided assistant instead of an LLM function-calling agent. It is explicitly disclosed in the README.
