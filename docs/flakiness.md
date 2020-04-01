# Flakiness

As a tool for end-to-end testing, Playwright provides the means to eliminate flakiness from your test scripts. This is possibly through Playwright's architecture.

## Causes of flakiness

Web apps have lots of asynchronous behavior, which makes them harder to automate. The state of the application under test can be different than what the tests expect. For example:

* The app might be loading

In my experience what makes tests flaky is not having enough knowledge about the state of your app under test and what reliably signifies a "ready" state.

## Why is Playwright different

Playwright is a bi-directional automation driver.

## How can you use it

### Auto waits

### Explicitly waiting

### Listen for events

## Other scenarios

## Intercept network requests

## Console logs

## Eval
