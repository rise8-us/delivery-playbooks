# Automated Testing

## What is it?

Automated testing in software development is writing code or scripts (separate from the production code) that are able to test if the software is working as expected by controlling inputs and looking for expected results.  These tests can be triggered during key points of the development lifecycle such as making a change to a codebase or in a Continuous Integration / Continuous Delivery (CI/CD) pipeline before releasing software into production.

Most organizations have some quality assurance (QA) function to ensure that the products they produce are defect-free. Automated tests serve as the first line defense of software quality by running a set of repeatable steps and looking for expected results \- on the order of milliseconds. This frees up QA to move away from repeatable tests to focus on exploratory testing.

### Test Driven Development (TDD)

TDD is a software development approach where automated tests are written before implementation.  This means the behavior of the desired implementation is defined from the outset, ensuring that new code written meets specific requirements and functions correctly.  The cycle of TDD is broken down into three distinct phases:

1. Write a failing test case  
2. Write just enough code for the test case to pass  
3. Refactor code and repeat

This process is often referred to as a red-green refactor.

* [How to TDD a List Implementation in Java](https://www.baeldung.com/java-test-driven-list) \- Baeldung

### Tests as Documentation

Automated tests can serve as documentation for a codebase.  By examining tests, developers can understand the expected behavior of the application.  This practice not only helps new team members learn the specifications of the system, it also empowers developers to modify the codebase.  Extensive testing provides assurance that new changes are not introducing unexpected behavior elsewhere in the application.

Robert C. Martin, author of *Clean Code*, emphasizes in his book, “Tests are as important to the health of a project as the production code.  Perhaps they are even more important, because tests preserve and enhance the flexibility, maintainability, and reusability of production code.”

### Testing Pyramid

The Testing Pyramid is a concept that guides the distribution of automated tests in a software project, ensuring a balanced approach that optimizes for both speed and coverage of different workflows.  At the base of the pyramid is unit tests, which should make up the majority of tests written.  These test individual components of an application in isolation and are very fast to run.  At the top of the pyramid are end-to-end (E2E) tests, which should contain the fewest number of tests.  E2E tests cover entire workflows in the application from start to finish, and since they require spinning up the application and mocking user behavior they are the most time intensive.  Integration tests are in the middle of the pyramid.  These test the interaction between multiple components in an application and should run slower than unit tests and faster than E2E tests.  Due to this cost it is advised there should be less integration tests than unit tests, but more integration tests than E2E tests.

This guideline serves as a good rule of thumb, but testing practices may change from project to project.  In general, to write maintainable automated tests that aid with delivery it is important to write tests of different granularity, and as the scope of the workflow grows the number of tests should decrease.

![Balanced team](../assets/testpyramid.png)

### Why do it?

Automated testing allows for immediate feedback for changes in the codebase, immediately informing the developer whether implementations work as expected.  By supporting continuous integration and continuous delivery (CI/CD), automated testing accelerates development and reduces the risk of manual testing errors.  Additionally, this testing framework provides a secure foundation for code refactoring, improving the maintainability of the codebase.

### Relevant Links

* [Automated software testing](https://www.atlassian.com/continuous-delivery/software-testing/automated-testing) \- Atlassian  
* [Test Driven Development](https://martinfowler.com/bliki/TestDrivenDevelopment.html) \- Martin Fowler  
* [Docs as Tests](https://www.docsastests.com/)  
* [The Practical Test Pyramid](https://martinfowler.com/articles/practical-test-pyramid.html) \- Martin Fowler
