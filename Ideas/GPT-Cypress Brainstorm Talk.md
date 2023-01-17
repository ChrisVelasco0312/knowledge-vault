
## Suggested structure of the talk
Here is a suggested outline for a one-hour talk on the Cypress test framework:

1.  Introduction (5-10 minutes): Provide an overview of Cypress, including what it is and why it's useful for testing web applications.
2.  Getting started (10-15 minutes): Cover the basics of setting up Cypress, including installation and configuration.
3.  Writing tests (20-25 minutes): Dive into the specifics of writing Cypress tests, including how to use the Cypress API to interact with web pages, how to organize tests, and best practices for writing maintainable tests.
4.  Advanced topics (10-15 minutes): Cover more advanced topics such as running Cypress tests in parallel, integrating Cypress with other tools such as Jenkins, or testing web applications with non-traditional architectures (e.g. single-page applications, progressive web apps).
5.  Conclusion (5-10 minutes): Summarize the key points of the talk and provide resources for further learning.
    
Make sure to include some live demonstration of the cypress test framework and also keep some time for Q&A session, so that attendees can ask questions.

### WRITING TESTS

When we install and run cypress, it provide us with a browser and a dashboard that help us interact with the test. For this expo we are going to touch E2E tests only.

It also setups automatically for us the necessary configuration and folder structure.

In the folder `cypress` we are going to found
`fixtures` Where we mock data.
`plugins` Allow us to extend cypress with additional functionality write by the cypress team or the community.
`support` Global configuration
`integation` Where we add the tests.

We can create a test suite con `describe` and with `beforeEach` we can run setup code that runs before every test.

```js

describe('my awesome website', () => {
	beforeEach(() => {
		cy.visit('http://localhost:3000')
	})
	// use it to describe a test case
	it('allows a user to sign up', () => {
		// grab elements from the DOM with the GET method
		cy.get('h1').should('contain.text', 'Login')
		//bundles the chai associate library for bdd
		cy.get('input').type('hi-mom')
		cy.get('button').click()
		cy.get('h1').should('contain.text', 'Success!')
	})
})

describe("My awesome app", () => {
  beforeEach(() => {
    cy.visit("http://localhost:5173");
  });

  it("allows to write in the inputs", () => {
    cy.get('[data-cy="email"]').type("admin@mail.com");
    cy.get('[data-cy="password"]').type("admin");

    cy.get('[data-cy="submit"]').click();

    cy.contains("Success !!!");
  });
});

```

A cool thing about cypress is that handles wait automatically, so we don't have to use `sleep(500)` and similar methods.

Run test to match everything you write visually, the cypress tool use the browsers native API and creates a snapshot for every single test statement. It also provide useful descriptions. If some assert fails we can easilly inspect the dom to debug.

We can open a selector playground to easily grab every element on the page

```markdown
Writing tests for your application is an important part of the development process. It allows you to catch bugs and edge cases before they make it to production, and it gives you confidence in your code.

Cypress makes it easy to write tests for your application, it provides a simple and intuitive API that allows you to interact with your application just like a user would. Cypress also provides a set of built-in commands that make it easy to test common user interactions, such as clicking buttons, filling out forms, and navigating between pages.

When writing tests, it's important to keep in mind that your tests should be as simple and easy to understand as possible. Cypress tests are written in JavaScript and it's recommended to use the latest version of JavaScript, such as ES6, to make your tests more readable and maintainable.

Cypress also allows you to write tests in a synchronous way, which means that you don't need to worry about callback functions or promises, this makes your tests more predictable and easier to read.

It's also important to consider the test organization, Cypress allows you to organize your tests in a way that makes sense for your application, you can create a folder for each feature or page and put all the tests related to that feature or page in that folder.

Cypress also provides a feature called `describe()` and `it()` that allows you to group your tests and provide a clear and concise structure for your tests.

Another important aspect to consider is the test's assertion. Cypress uses Chai as the assertion library, this library provides a set
```


## Intro script
```
Welcome everyone, today I am going to be talking about the Cypress test framework. Cypress is a modern end-to-end testing framework for web applications that makes it easy to set up, write, run, and debug tests.

Cypress is a JavaScript-based framework, which means that it can be used with any web application that is built with JavaScript. It provides a high-level API that makes it easy to interact with web pages, as well as a powerful command line tool for running and debugging tests.

Cypress is also browser independent, Cypress runs your tests directly in the browser, so you can be sure that your tests are running in the same environment as your users. This means that you can catch more bugs and edge cases before they make it to production.

Cypress also includes a time-traveling debugger, that allows you to see exactly what happened during the test runs, which makes it easy to understand why a test is failing.

The goal of Cypress is to make it easy for developers to write and maintain end-to-end tests, so they can be confident that their web application is working as expected.

Today we're going to take a look at how to get started with Cypress, how to write tests, and some advanced topics such as running Cypress tests in parallel, integrating Cypress with other tools such as Jenkins, and testing web applications with non-traditional architectures.

So, let's dive in and learn how to use Cypress to write effective end-to-end tests for your web applications.
```

## Advanced topics

```
Advanced Topics:

Now that we've covered the basics of getting started with Cypress and writing tests, let's take a look at some advanced topics.

1.  Running Cypress tests in parallel: Cypress has built-in support for running tests in parallel, which allows you to speed up your test runs by running multiple tests at the same time. We will cover how to set up parallelization and how to monitor the progress of parallel test runs.
    
2.  Integrating Cypress with other tools: Cypress can be integrated with other tools such as Jenkins, Travis CI, and CircleCI. We'll take a look at how to set up Cypress with these tools and how to configure your pipeline to run Cypress tests automatically.
    
3.  Testing web applications with non-traditional architectures: Cypress can be used to test web applications with non-traditional architectures such as single-page applications, progressive web apps, and web components. We will cover strategies for testing these types of applications with Cypress.
    
4.  Advanced debugging: Cypress has a built-in debugger that allows you to see exactly what happened during a test run. We'll take a look at how to use the debugger to understand why a test is failing and how to fix the issues.
    
5.  Best practices: We'll go over some best practices for writing maintainable Cypress tests, including how to organize your tests, how to use Cypress' built-in test runner, and how to debug and troubleshoot test failures.
    
6.  Conclusion: Summarize the key points of the talk and provide resources for further learning.
    

Make sure to include some live demonstration of the advanced topics and also keep some time for Q&A session, so that attendees can ask questions related to advanced topics.
```

## Questions
why do i still need end to end test when i have unit testing already?
```
Great question! Unit tests are great for testing individual units of code and making sure that they work as expected. However, unit tests can only test the code that you write, they can't test the interactions between different parts of your application, or how your application behaves in the browser.

End-to-end tests, on the other hand, test the entire application as a whole, including the interactions between different parts of the code and the interactions between the code and the browser. This means that end-to-end tests can catch issues that unit tests can't, such as bugs that only appear when different parts of the code are used together or bugs that are caused by browser-specific behavior.

Additionally, end-to-end tests can provide a more realistic simulation of how your application is used in the real world. This makes it more likely that you'll catch issues that would be encountered by your users, such as usability problems or performance issues.

End-to-end testing is especially important for web applications, which have a lot of moving parts and are often used by many different types of users on different devices and browsers. Cypress makes it easy to write and run end-to-end tests for your web application, which allows you to catch more bugs and edge cases before they make it to production.

It's also important to note that end-to-end tests and unit tests are not mutually exclusive, rather they complement each other, both types of testing play different roles in ensuring the quality and integrity of an application.
```
What's the value that offers testing our apps with cypress that jest cannot offer?
```
Cypress and Jest are both JavaScript testing frameworks, but they serve different purposes. Jest is primarily a unit testing framework that is used for testing individual units of code. It's great for testing the functionality of individual functions or components, and it's designed to be easy to use and integrate with other JavaScript tools.

Cypress, on the other hand, is an end-to-end testing framework. It's designed to test the entire web application as a whole, including the interactions between different parts of the code and the interactions between the code and the browser. Cypress provides a high-level API for interacting with web pages and a powerful command line tool for running and debugging tests.

One of the key value that Cypress offers over Jest is the ability to run tests directly in the browser. Cypress tests run in the same environment as your users, which allows you to catch more bugs and edge cases before they make it to production. Cypress also includes a time-traveling debugger, which makes it easy to understand why a test is failing.

Additionally, Cypress provides a lot of built-in functionality for interacting with web pages, such as automatic waiting for elements to load, automatic retries on failures, and a built-in test runner. This makes it easy to write and maintain end-to-end tests, and it helps you to catch more bugs and edge cases before they make it to production.

In short, while Jest is great for unit testing and Cypress is a powerful end-to-end testing framework, and they both have their own strengths, Cypress is particularly well-suited for testing web applications and catching bugs that might be difficult or impossible to detect with unit tests alone.
```
Why run test in parallel is useful?
```
Running Cypress tests in parallel is useful in a few different scenarios:

1.  Large test suites: If you have a large test suite, running tests in parallel can significantly speed up your test runs. By running multiple tests at the same time, you can complete your test runs faster and get feedback on your application's functionality more quickly.
    
2.  Testing across multiple browsers or devices: Cypress allows you to test your application across multiple browsers and devices. By running tests in parallel, you can test your application across multiple browsers or devices at the same time, which can help you catch cross-browser or cross-device compatibility issues.
    
3.  Continuous integration and delivery: When you set up Cypress with a continuous integration and delivery (CI/CD) pipeline, running tests in parallel can help you reduce the total time it takes to run your tests and get feedback on your changes.
    
4.  Parallelizing test execution can also help you to identify test flakiness and test that are taking too much time to run, thus you can optimize your test suite and make it more efficient.
    
5.  Parallelization also allows you to test more scenarios and use cases in a shorter amount of time, this can help you increase the coverage of your tests and increase the confidence in your application.
    

It's important to note that parallelization is not always the best option, it depends on the size and complexity of your test suite, and also the resources you have available, so it's always recommended to test and measure the results before making any decision.
```
Is cypress worth for unit testing, and can be a good replacement for Jest or Vitest in the context of a React app?
```
Cypress can be used for both end-to-end testing and unit testing, although it is primarily designed as an end-to-end testing framework. Cypress uses a "real browser" to run the tests, which makes it possible to test the application as a whole, including the interactions between different parts of the code and the interactions between the code and the browser.

When it comes to unit testing, Cypress can be used to test individual units of code, such as React components. Cypress allows you to mount a React component and interact with it directly, just like a user would interact with the component in a browser. Cypress also provides a set of utility functions that make it easy to test the component's behavior and state.

It's important to keep in mind that Cypress is primarily designed as an end-to-end testing framework, and it might be more verbose than other unit testing frameworks like Jest, which is specifically designed for unit testing and it has a lot of built-in functionality for unit testing.

In a React app, Jest is a popular choice for unit testing, it works well with React and provides a lot of built-in functionality for testing React components, including a powerful assertion library and a set of utilities for testing component behavior and state. Jest also provides a set of features such as snapshots, that can help you to improve the maintainability of your tests.

Cypress can be used as a replacement for Jest for unit testing in a React app, but it's important to keep in mind that Cypress is primarily designed for end-to-end testing and it might be more verbose than Jest for unit testing and it might not have as many built-in features for unit testing.

It's also important to note that Cypress and Jest are not mutually exclusive, both can complement each other, Cypress can be used for end-to-end testing and Jest for unit testing, which can provide a comprehensive testing strategy for a React application
```
ABout, cypress difficulty when handling asynchronous tests.
```
Cypress does have some built-in functionality for handling promises, but it's true that it can be a bit more complex than other testing frameworks when it comes to dealing with asynchronous code. Cypress provides two main ways to handle promises:

1.  Cypress.Promise: Cypress provides a `Cypress.Promise` class that allows you to resolve or reject a promise and use it in your test. Cypress.Promise can be used to wrap a promise, and it will automatically retry the command until the promise is resolved.
    
2.  Cypress.clock(): Cypress provides a `Cypress.clock()` function that allows you to control the browser's clock, this function can be used to control the timing of your tests, and it can help you to make your tests more deterministic.
    

It's important to note that Cypress.Promise and Cypress.clock() are not always the best option and they might not be the most elegant way to handle promises, it depends on the complexity of your code and the nature of your tests. Some developers prefer to use a more traditional approach to handle promises, such as using a library like `bluebird` or `async/await` functions.

Additionally, Cypress has a feature called `cy.wait()` that allows you to wait for a specific condition to be true before continuing your test, this function can be useful when you need to wait for an asynchronous action to complete.

It's worth to note that Cypress is constantly improving and adding new features, so it's important to check the latest documentation and see if there are new ways to handle promises.

Overall, Cypress can handle promises, but it might require more work than other testing frameworks, it's always recommended to test and measure the results before making any decision.
```
Can Cypress intercept request and mock the data of the backend?
```
Yes, Cypress allows you to intercept requests and mock the data of the backend using the method `cy.intercept()`. This method allows you to intercept and mock HTTP requests, and it works similarly to the old `cy.route()` method. With `cy.intercept()` you can:

-   Stub a request and return a custom response: This can be useful when you want to test your application's behavior when a specific endpoint returns a specific response.
-   Intercept a request and respond with a delay: This can be useful when you want to test your application's behavior when a request takes a long time to complete.
-   Respond with a failure status code: This can be useful when you want to test your application's behavior when a request fails.

Additionally, `cy.intercept()` allows you to intercept and mock requests to `fetch`, `XMLHttpRequest`, and `WebSocket` which makes it more flexible and closer to the browser's API.

You can use `cy.intercept()` to intercept a request and then respond with a custom response, you can also use `cy.intercept()` with `cy.wait()` function to wait for a specific request and then check the request and response, this can be useful when you want to check the request headers, the request payload and the response status code.

Overall, Cypress allows you to intercept and mock requests, this feature can be very useful when you want to test your application's behavior when a specific endpoint returns a specific response, or when you want to test your application's behavior when a request takes a long time to complete.
```
Why someone needs to intercept requests?
```
Intercepting requests allows you to control the behavior of the application under test by returning custom responses or simulating delays or errors. This can be useful in a few different scenarios:

1.  Testing edge cases: When you intercept requests, you can return custom responses that simulate edge cases or unexpected conditions. This can help you test how your application handles these conditions and ensure that it behaves as expected.
    
2.  Isolating the test: By intercepting requests, you can isolate your test from the backend and test the application's behavior independently of the backend's behavior. This can make your tests more robust and less prone to breaking when the backend changes.
    
3.  Testing performance: By simulating delays or errors in requests, you can test how your application handles performance issues and ensure that it behaves as expected.
    
4.  Testing in offline or unstable environments: By intercepting requests, you can simulate an offline or unstable environment and test how your application behaves in these conditions.
    
5.  Speed up the test: By intercepting requests, you can avoid the need to wait for a response from the backend and this can speed up your test runs.
    

Testing the request with the real API or backend is not always recommended because it can make your tests less robust and more prone to breaking when the backend changes. Additionally, it can also make your tests slower, as they have to wait for a response from the backend.

Intercepting requests also allows you to test your application's behavior in conditions that might be difficult or impossible to reproduce with a real API or backend, such as simulating delays or errors, testing in offline or unstable environments, or simulating edge cases.

Overall, intercepting requests can be a powerful tool for testing your application, and it allows you to test your applicationIntercepting requests allows you to control the behavior of the application under test by returning custom responses or simulating delays or errors. This can be useful in a few different scenarios:

1.  Testing edge cases: When you intercept requests, you can return custom responses that simulate edge cases or unexpected conditions. This can help you test how your application handles these conditions and ensure that it behaves as expected.
    
2.  Isolating the test: By intercepting requests, you can isolate your test from the backend and test the application's behavior independently of the backend's behavior. This can make your tests more robust and less prone to breaking when the backend changes.
    
3.  Testing performance: By simulating delays or errors in requests, you can test how your application handles performance issues and ensure that it behaves as expected.
    
4.  Testing in offline or unstable environments: By intercepting requests, you can simulate an offline or unstable environment and test how your application behaves in these conditions.
    
5.  Speed up the test: By intercepting requests, you can avoid the need to wait for a response from the backend and this can speed up your test runs.
    

Testing the request with the real API or backend is not always recommended because it can make your tests less robust and more prone to breaking when the backend changes. Additionally, it can also make your tests slower, as they have to wait for a response from the backend.

Intercepting requests also allows you to test your application's behavior in conditions that might be difficult or impossible to reproduce with a real API or backend, such as simulating delays or errors, testing in offline or unstable environments, or simulating edge cases.

Overall, intercepting requests can be a powerful tool for testing your application, and it allows you to test your application
```