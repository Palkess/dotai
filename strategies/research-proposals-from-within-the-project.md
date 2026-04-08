# Research proposals from within the project
When considering a new feature or change, it's very valuable to research the proposed changes with an agent to create a bulletproof plan before starting the planning session before implementing.

## 1. Write the proposal in a markdown-file
Structure the file with definitions of technical terms readable terms if needed. Give clear reasonings and planned actions so that the agent can better understand the why, how and what.

Ex. 

```md
## Definitions of Services and files

- **SomeNamedService**
    - ./route/to/service
    - ...
- **SomeBusinessCriticalTerm** - Explaining the business specific term so we don't have to adjust our language later

## Problem

Thing isn't working and are causing these issues. Give clear explanations and give more context about the solution if needed.

## Proposed solution
Give a clear suggestion of a solution with one or multiple steps/actions. Each action should be focused and not cover multiple sections of the issue if applicable.

Give code examples if applicable:

someObj = {
    ...someObj,
    overrideProp: 'newValue'
}

### Describe an action in a specific section
Separate actions in multiple sections by their own heading so that the agent can give focused suggestion to one section.

## Cascading effects from the solution
Give your own insights and findings about what effects the proposed solution has after being completed. Maybe some old states needs to be updated.
```

## 2. Research the proposal with an agent in the project
Open your preferred agent cli or client and ask the agent to go through the proposal and check it against the codebase. Use an interrogation skill like /grill-me to push it to challenge you on every decision and reach a conclusion.

After the interrogation about the proposal, more often than not you'll have discovered edge-cases or maybe a new approach that you hadn't considered before. Or even simplifying your approach to the problem.

## Key things to think about
- As with everything regarding agentic development, context is key. What the agent doesn't know, it tries to find out through the code but to save tokens and likely hallucinations, always provide as much focused context as possible. Don't add context unrelated to the issue.
- Consider the target audience who is going to read the proposal. If it's aimed at developers/agents, it should stay highly technical and direct. If a non-technical actors have to agree to the proposal, make it easier to understand with deep insight in the code or technical solution.