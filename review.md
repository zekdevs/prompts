OBJECTIVE:
Perform a code quality focused review to identify inefficient and badly written code. Focus only on technical debt and code quality only.

CRITICAL INSTRUCTIONS:
1. MINIMIZE INEFFICIENCIES: Flag and fix code that is not preformant, if a better solution can be used.
2. AVOID NOISE: Skip theoretical issues, style concerns, or low-impact findings
3. FOCUS ON IMPACT: Prioritize techinical debt that could lead to major bugs, issues refactoring later, and preformance issues.
4. EXCLUSIONS: Do NOT report the following issue types:
   - Security
   - Styling / Code formatting
   - Performance optimizations without evidence of bottlenecks
   - Documentation gaps or missing comments

CATEGORIES TO EXAMINE:

**Code Structure & Design Debt:**
- Duplicated code blocks or logic
- God classes or overly complex modules
- Lack of modularity or poor separation of concerns
- Tight coupling between components
- Violation of design principles (e.g., SOLID)

**Maintainability Debt:**
- Magic numbers or hardcoded values
- Overly complex control flows (e.g., deep nesting)
- Lack of abstraction in repetitive patterns
- Poor error handling or exception management
- Unnecessary complexity in algorithms

**Scalability & Performance Debt:**
- Inefficient data structures for large-scale use
- Potential bottlenecks in loops or queries
- Lack of caching in performance-critical paths
- Resource leaks or improper resource management

**Testing & Reliability Debt:**
- Untestable code (e.g., monolithic functions)
- Missing unit test coverage indicators
- Fragile dependencies on external systems
- State management issues in concurrent code

**Refactoring Opportunities:**
- Legacy code patterns needing modernization
- Deprecated API usage
- Inconsistent naming or architecture mismatches
Additional notes:
- Even if debt is only evident in future scaling, it can still be a HIGH severity issue if growth is anticipated.

ANALYSIS METHODOLOGY:

Phase 1 - Repository Context Research (Use file search tools):
- Identify existing design patterns and architectural standards in the codebase
- Look for established maintainability practices
- Examine common refactoring patterns
- Understand the project's evolution and known debt areas

Phase 2 - Comparative Analysis:
- Compare new code changes against existing design patterns
- Identify deviations from established maintainable practices
- Look for inconsistent implementations
- Flag code that introduces new debt surfaces

Phase 3 - Debt Assessment:
- Examine each modified file for debt implications
- Trace code flows for complexity and duplication
- Look for extensibility boundaries being compromised
- Identify areas ripe for refactoring

SEVERITY GUIDELINES:
- **HIGH**: Debt leading to significant rework, frequent bugs, or blocking future features
- **MEDIUM**: Debt requiring moderate effort to address but with notable impact
- **LOW**: Minor debt affecting local readability or minor extensibility

CONFIDENCE SCORING:

- 0.9-1.0: Clear debt pattern with demonstrable impact, verifiable if possible
- 0.8-0.9: Recognizable debt with known long-term consequences
- 0.7-0.8: Suspicious pattern likely to accrue debt under growth
- Below 0.7: Don't report (too speculative)

FINAL REMINDER:
Focus on HIGH and MEDIUM findings only. Better to miss some minor issues than flood the report with false positives. Each finding should be something a software engineer would confidently raise in a PR review for long-term code health.

IMPORTANT EXCLUSIONS - DO NOT REPORT:

- Stylistic or formatting issues (managed by automated tools)
- Performance concerns without data-backed evidence
- Documentation or comment-related problems
- Minor readability issues without broader impact
- Lack of features like logging in non-critical areas. If there isn't a proven maintenance problem, don't report it.

Begin your analysis and fixes now. Use the repository exploration tools to understand the codebase context, then analyze the PR changes for technical debt.
