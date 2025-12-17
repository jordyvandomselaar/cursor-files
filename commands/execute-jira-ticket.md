# Execute Jira Ticket

Given a Jira ticket ID, fetch the ticket details and implement the requested changes through a thorough, research-driven process.

## Input
- `$ARGUMENTS` - The Jira ticket ID (e.g., `STORY-123`, `AGP-456`)

## Phase 1: Gather Requirements

1. **Fetch the Jira ticket** using the `internal-data` tool with the ticket URL (e.g., `https://zapierorg.atlassian.net/browse/$ARGUMENTS`)

2. **Analyze the ticket thoroughly** - Review:
   - Title and description
   - Acceptance criteria
   - Story points (to gauge complexity)
   - Any linked tickets or parent epics
   - Comments for additional context
   - Attachments or mockups

3. **Fetch related tickets** - If there are linked tickets, parent epics, or mentioned tickets, fetch those too for full context

## Phase 2: Research the Codebase

Before writing any code, conduct thorough research:

### 2.1 Find Existing Related Code
- Search for code related to the feature/area mentioned in the ticket
- Look for existing implementations that solve similar problems
- Identify files that will need to be modified
- Find any existing utilities, hooks, or components that can be reused

### 2.2 Study Patterns and Conventions
Research how similar things are done in this codebase:

- **Testing patterns**: How are tests structured? What testing utilities exist? How is test data seeded/mocked? What assertions are commonly used?
- **Component patterns**: What component libraries are used? How are components structured? What styling approach is used?
- **State management**: How is state handled? What patterns exist for data fetching?
- **File organization**: Where should new files go? What naming conventions are used?
- **Similar implementations**: Find 2-3 files that do something similar to what the ticket requires and study them

### 2.3 Research Data Access Patterns
When the feature requires accessing data:
- Search for existing code that accesses the same or similar data
- Identify the data layer patterns used (e.g., repositories, services, API clients, hooks)
- If exact data access code doesn't exist, study how other data is accessed and follow those patterns
- Look for existing API endpoints, GraphQL queries, or database access methods that can be extended
- Use the established patterns to add new data access methods rather than inventing new approaches

### 2.4 Identify Dependencies
- What existing utilities, hooks, or services should be used?
- Are there shared components that apply?
- What APIs or data sources are involved?

## Phase 3: Plan the Implementation

1. **Create a detailed todo list** based on your research using the `todo_write` tool
2. **Document your findings** - Note the patterns you'll follow and the existing code you'll leverage
3. **If anything is unclear**, ask for clarification before proceeding

## Phase 4: Implement

1. **Follow the patterns** you discovered during research - match the existing code style exactly
2. **Reuse existing code** - Use existing utilities, hooks, and components rather than creating new ones
3. **Keep changes focused** - Only implement what the ticket requests, nothing more

## Phase 5: Testing

1. **Study existing tests first** - Find tests for similar features and follow the same patterns
2. **Write comprehensive tests** including:
   - Positive assertions (expected behavior works)
   - Negative assertions BEFORE actions (state is correct before the action)
   - Edge cases mentioned in acceptance criteria
3. **Use existing test utilities** - Don't reinvent test helpers that already exist

## Phase 6: Verify and Submit

1. **Run linting and tests** to verify the implementation
2. **Review your changes** - Ensure they match codebase patterns
3. **Create a merge request** using `glab mr create` linking back to the Jira ticket

## Principles

- **Research before coding** - Understanding existing patterns prevents rework
- **Match existing style exactly** - New code should be indistinguishable from existing code
- **Reuse over reinvent** - Always check if something already exists before creating it
- **Stay focused** - Don't add features, refactor, or "improve" beyond what was asked
- **Ask when unclear** - It's better to clarify than to assume incorrectly
