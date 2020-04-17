# Working with elements

The Playwright API can select and interact with elements on a web page.

## Selecting elements

Playwright can query elements on a web page through [multiple selector engines](selectors.md) like CSS, HTML attributes, XPath and text contents.

```js
```

Once selected, 

## Assertions on elements

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

* Use the [`page.waitForSelector`](../api.md#pagewaitforselectorselector-options) method to explicitly wait for elements.

  ```js
  // Explicitly wait for the #search field to be present in the DOM
  const search = await page.waitForSelector('#search');
  // Retrieve the query value from the element
  const query = await search.evaluate(element => element.value);
  ```
