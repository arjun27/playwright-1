# Working with elements

## Interacting with elements

Playwright APIs that interact with elements accept selectors as the first
argument, used to search for the element. Playwright can search for elements
with CSS selectors (`css`), XPath (`xpath`), HTML attributes (like `id`,
`data-test-id`) and text content (`text`).

```js
// Fill <input id=search>
await page.fill('css=#search');
// which is equivalent to
await page.click('#search');

// Click <button>Login</button>
await page.click('text=Login');
// which is equivalent to
await page.click('"Login"');

// Click <div data-test-id=next>
await page.click('data-test-id=next');
```

#### Reference

* [Selector engines](selectors.md)
* [Custom selector engines](selectors.md#custom-selector-engines)

## Assertions on elements

The [`ElementHandle`](api.md#class-elementhandle) object represents an element
on a page. This can be used to get

```js
const element = await page.$('');
```

getAttribute
innerHTML
innerText
textContent

Assertions on elements: Use [`page.$`](api.md#pageselector) to get the element
from the page and [`page.$eval`](api.md#pageevalselector-pagefunction-arg-1) to 
run a JS function in the execution context of the page.

  * These can be used to assert element properties, like visibility or text contents.
  * These methods behave similar to the `$` operator in DevTools console or jQuery. They fetch the element from the page without waiting. If required, use `page.waitForSelector` and `evaluate` instead, as described above.

  ```js
  // Get value of the #search field
  const query = await page.$eval('#search', element => element.value);
  ```

## Element handles

* Actions on elements: Use methods like [`page.click`](../api.md#pageclickselector-options) or [`page.fill`](../api.md#pagefillselector-value-options) to execute actions on elements.
  * **Auto-wait** for elements: These actions auto-wait for the element to be ready. If these actions result in page navigations, they are also awaited automatically.

  ```js
  // Wait for element to be ready, click it and wait for navigations (if any)
  await page.click('text="Login"');
  ```
