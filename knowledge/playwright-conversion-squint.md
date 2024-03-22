The following is an example of converting a javascript snippet to Squint-cljs

```js
import { Browser, BrowserContext, chromium, expect, Page } from "@playwright/test";
import { afterAll, beforeAll, describe, test } from "vitest";

describe("playwright meets vitest", () => {
  let page: Page;
  let browser: Browser;
  let context: BrowserContext;
  beforeAll(async () => {
    browser = await chromium.launch();
    let context = await browser.newContext();
    page = await context.newPage();
  });

  afterAll(async () => {
    await browser.close();
  });

  test("has title", async () => {
    await page.goto("<https://playwright.dev/>");

    // Expect a title "to contain" a substring.
    await expect(page).toHaveTitle(/Playwright/);
  });

  test("get started link", async () => {
    await page.goto("<https://playwright.dev/>");

    // Click the get started link.
    await page.getByRole("link", { name: "Get started" }).click();

    // Expects the URL to contain intro.
    await expect(page).toHaveURL(/.*intro/);
  });
});
```

```cljs
(require '["@playwright/test" :refer [chromium expect]]
         '["vitest" :refer [describe beforeAll afterAll test]])

(describe "playwright meets vitest"
  (fn []
    (let [page (atom nil)
          browser (atom nil)
          context (atom nil)]
      (beforeAll
       (fn ^:async before-all []
         (reset! browser (js/await (.launch chromium)))
         (reset! context (js/await (.newContext @browser)))
         (reset! page (js/await (.newPage @context))))

      (afterAll
       (fn []
         (.then (.close @browser)
                (fn [] (println "Browser closed")))))

      (test "has title"
            (fn []
              (-> (.goto @page "https://playwright.dev/")
                  (.then (fn [] (.toHaveTitle (expect @page) #"Playwright"))))))

      (test "get started link"
            (fn []
              (-> (.goto  @page "https://playwright.dev/")
                  (.then (fn []
                           (.click (.getByRole @page "link" #js {:name "Get started"}))
                           (.toHaveURL (expect @page) #".*intro"))))))))))
```
