[[01_Aigentic_Programming]]
# Cyclomatic Complexity
Cyclomatic Complexity is a metric that measures how many independent execution paths exist through a piece of code.

**In practice**, it tells you:
- **How complicated** a function is.
- How many **test cases are needed** for full branch coverage.
- How **difficult** the code is **to understand**, maintain, and modify.

|Complexity|Interpretation|
|---|---|
|1-5|Simple, easy to understand|
|6-10|Moderate, review if it can be simplified|
|11-20|Complex, likely needs refactoring|
|>20|High risk, difficult to maintain|
# The 3 Laws of TDD
1. You may not write production code until you have written a failing unit test. (**First write a failing test**)
    - Every new behavior starts with a test.
    - The test must fail initially because the functionality does not yet exist.
2. You may not write more of a unit test than is sufficient to fail, and not compiling is failing.
    - Write only the **smallest test necessary to express the next requirement**.
    - A compilation error counts as a failure.
3. You may **not write more production code than is sufficient to pass** the currently failing test.
    - Implement only the **minimal code required** to make the test pass.
    - Do not add extra functionality "for later."

This creates the classic **Red → Green → Refactor** cycle:
1. Red: write a small failing test.  
2. Green: write the minimum code needed to pass the test.    
3. Refactor: improve the design while keeping all tests green.
# Sources
- https://learning.oreilly.com/videos/clean-ai-agentic/9780135968819/9780135968819-caiad1_01_01/
