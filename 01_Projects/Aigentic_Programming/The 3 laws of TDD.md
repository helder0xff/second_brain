[[01_Aigentic_Programming]]
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