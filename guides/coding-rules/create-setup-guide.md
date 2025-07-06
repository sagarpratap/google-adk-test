# Creating setup guides

## Goal

To guide an AI assistant in creating a detailed Setup Guide in Markdown format, based on an initial user prompt. The Setup Guide should be clear, actionable, and suitable for a junior developer to understand and implement the setup-feature.

## Process
1.  **Receive Initial Prompt:** The user provides a brief description or request for a how-to guide.
2. **Ask Setup-Feature name:** Ask the user to provide a name for the setup-feature. This name will be used for naming the setup guide file.
2.  **Ask Clarifying Questions:** Before writing the Setup Guide, the AI *must* ask clarifying questions to gather sufficient detail. The goal is to understand the "what", "why" of the setup-feature first, before we tackle the "how". Ask clarifying questions one at a time, get the response from user and proceed to the next clarifying question.
3. **Identify Prerequisites** Check for dependencies, both that the user requires to take manual actions to complete, external registrations or subscriptions as well as project/machine dependencies that the AI needs to download/install and configure
5.  **Generate Parent Tasks:** Based on the analysis, create the file and generate the main, high-level tasks required to implement the setup-feature. Parent tasks should be sequenced in a logical manner such that all preconditions and information required for the subsequent tasks are completed before the next task.  
6. **Prioritization of Tasks** Setup Guide for a technical feature should prioritize the setup on local environment first, completely executable within a containerized environment.
7. Inform the user: "I have generated the high-level tasks. Ready to generate the sub-tasks? Respond with 'Go' to proceed."
8.  **Wait for Confirmation:** Pause and wait for the user to respond with "Go".
9.  **Phase 2: Generate Sub-Tasks:** Once the user confirms, break down each parent task into smaller, actionable sub-tasks necessary to complete the parent task. Ensure sub-tasks logically follow from the parent task and cover the implementation details implied to achieve the parent task.
Sub-Tasks should be sequenced in a logical manner such that all preconditions and information required for the subsequent tasks are completed before the next task.
For each Sub-Task, include the exact implementation instructions or steps either in text format, or if these are code snippets or commands, add them in the markdown. Tasks should be represented in a sequential manner, with all the manual instructions as well as code blocks residing together. Do not represent in tabular format.
10. **Validate Task Strategy** Check official documents, best practices, popular dev guides, github links, trusted bloggers and evangelists in the relevant industry (defined by following of more than 10k users on the internet) to validate the task implementation strategy and steps vs the goal to achieve. Adjust tasks as necessary.
10.  **Identify Relevant Files:** Based on the tasks, identify potential files that will need to be created or modified. List these under the `Relevant Files` section, including a comment for each file listing its purpose.
11.  **Generate Setup Guide:** Based on the initial prompt and the user's answers to the clarifying questions, generate a Setup Guide using the structure outlined below.
12.  **Save Setup Guide:** Save the generated document as `setup-[feature-name].md` inside the `/setup` directory.


## Clarifying Questions (Examples)

The AI should adapt its questions based on the prompt, but here are some common areas to explore:

*   **Problem/Goal:** "What problem does this feature solve for the user?" or "What is the main goal we want to achieve with this feature?"
*   **Core Functionality:** "Can you describe the key objectives a user should be able to perform with this setup guide"
*   **Prerequisites/Dependencies** List down your understanding of any prerequisites and dependencies from the user, external sources that require additional installation/subscription. Ask the user to confirm and clarify.
*   **Acceptance Criteria:** "How will we know when this feature is successfully implemented? What are the key success criteria?"
*   **Scope/Boundaries:** "Are there any specific things this feature *should not* do (non-goals)?"

## Setup Guide Structure

The generated Setup Guide should include a topic starting with "How to [implement a setup-feature]". It should include the following sections:

1.  **Overview:** Briefly describe the feature and the problem it solves. State the goal.
2.  **Goals:** List the specific, measurable objectives for this feature.
3.  **Out of Scope:** Clearly state what this feature will *not* include to manage scope.
4.  **Prerequisites/Dependencies:** Detail the prerequisites and dependencies required before the setup tasks can be executed. Tabulate this information in a markdown table with the following columns- Serial No, Prerequisite/Dependency, Action Owner (Human/AI), Status   
5.  **Tasks:** List the Parent Tasks and its Sub-Tasks in a markdown manner, using the columns- Task No., Description, Implementation Details.
If the implementation details is code block/snippet, show as markdown code format.
If the implementation details is a guide for users, show as text, detailing step by step instructions.
6. **Relevant files** Add relevant files that were generated or updated to implement the setup-feature. Refer to the structure below in the Markdown for Relevant Files.
6. **Verification** List the steps that the AI will perform the validate the setup was successful vs the original specification
5.  **Acceptance Criteria:** List at least 1 specific scenario and expected results that should be met for a successful implementation of each functional requirement. Tabulate this data with the following columns- Seq # (Start with 1), Scenario, Expected Result 
6.  **Open Questions:** List any remaining questions or areas needing further clarification.


```markdown
## Relevant Files

- `path/to/potential/file1.ts` - Brief description of why this file is relevant (e.g., Contains the main component for this feature).
- `path/to/file1.test.ts` - Unit tests for `file1.ts`.
- `path/to/another/file.tsx` - Brief description (e.g., API route handler for data submission).
- `path/to/another/file.test.tsx` - Unit tests for `another/file.tsx`.
- `lib/utils/helpers.ts` - Brief description (e.g., Utility functions needed for calculations).
- `lib/utils/helpers.test.ts` - Unit tests for `helpers.ts`.
- `docs/test-coverage.md` - Test coverage report updated after each major task completion
```
## Target Audience

Assume the primary reader of the PRD is a **junior developer**. Therefore, requirements should be explicit, unambiguous, and avoid jargon where possible. Provide enough detail for them to understand the feature's purpose and core logic.

## Output

*   **Format:** Markdown (`.md`)
*   **Location:** `/setup/`
*   **Filename:** `setup-[setup-feature].md`

## Notes
1. Do not embed the code blocks within the table cells using HTML <br> tags, else it will not render properly
2. Mark each Parent/Sub-Task with a green tick once they are completed

## Final instructions

1. Do NOT start implementing the Setup-Feature
2. Make sure to ask the user clarifying questions
3. Take the user's answers to the clarifying questions and improve the PRD
