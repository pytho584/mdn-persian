---
title: "console: assert() static method"
short-title: assert()
slug: Web/API/console/assert_static
page-type: web-api-static-method
browser-compat: api.console.assert_static
---

{{APIRef("Console API")}} {{AvailableInWorkers}}

متد استاتیک **`console.assert()`** اگر گزاره (assertion) نادرست باشد، یک پیام خطا به کنسول می‌نویسد. اگر گزاره درست باشد، هیچ اتفاقی رخ نمی‌دهد.

## نحو

```js-nolint
console.assert(assertion)

console.assert(assertion, val1)
console.assert(assertion, val1, val2)
console.assert(assertion, val1, val2, /* …, */ valN)

console.assert(assertion, msg)
console.assert(assertion, msg, subst1)
console.assert(assertion, msg, subst1, /* …, */ substN)
```

### پارامترها

- `assertion`
  - : هر عبارت بولی. اگر این گزاره نادرست باشد، یک پیام عمومی مبنی بر شکست گزاره به کنسول نوشته می‌شود.
- `val1` … `valN`
  - : فهرستی از مقادیر جاوااسکریپت برای خروجی. نمایشی از هر یک از این مقادیر پس از یک پیام عمومی شکست گزاره (که ممکن است با پیامی که در نبود این مقادیر خروجی داده می‌شود متفاوت باشد) به ترتیب داده‌شده، با نوعی جداسازی بین پیام و بین هر یک از آن‌ها، به کنسول خروجی داده می‌شود. حالت خاصی وجود دارد اگر `val1` یک رشته باشد که در ادامه شرح داده می‌شود.
- `msg`
  - : یک رشته جاوااسکریپت شامل صفر یا چند رشته جایگزین که به ترتیب متوالی تا تعداد رشته‌های جایگزین با `subst1` تا `substN` جایگزین می‌شوند. یک دونقطه، یک فاصله و سپس رشته جایگزین‌شده به پیام عمومی گزاره اضافه می‌شود تا یک پیام گزارهٔ دقیق‌تر ساخته شود و نتیجه به کنسول خروجی داده می‌شود. برای شرح نحوه عملکرد جایگزینی‌ها، به [استفاده از جایگزینی‌های رشته](/en-US/docs/Web/API/console#using_string_substitutions) مراجعه کنید.
- `subst1` … `substN`
  - : مقادیر جاوااسکریپتی که رشته‌های جایگزین درون `msg` با آن‌ها جایگزین می‌شوند. اگر تعداد مقادیر جایگزین بیشتر از تعداد رشته‌های جایگزین باشد، مقادیر اضافی خودشان پس از پیام گزارهٔ دقیق‌تر، به همان شکلی که در نبود رشتهٔ قالب‌بندی انجام می‌شود، به کنسول نوشته می‌شوند.

برای جزئیات بیشتر، [خروجی دادن متن به کنسول](/en-US/docs/Web/API/console#outputting_text_to_the_console) را در مستندات {{domxref("console")}} ببینید.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

کد مثال زیر استفاده از یک شیء جاوااسکریپت را پس از گزاره نشان می‌دهد:

```js
const errorMsg = "the # is not even";
for (let number = 2; number <= 5; number++) {
  console.log(`the # is ${number}`);
  console.assert(number % 2 === 0, "%o", { number, errorMsg });
}
// output:
// the # is 2
// the # is 3
// Assertion failed: {number: 3, errorMsg: "the # is not even"}
// the # is 4
// the # is 5
// Assertion failed: {number: 5, errorMsg: "the # is not even"}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [مستندات Microsoft Edge برای `console.assert()`](https://learn.microsoft.com/en-us/microsoft-edge/devtools/console/api#assert)
- [مستندات Node.js برای `console.assert()`](https://nodejs.org/docs/latest/api/console.html#consoleassertvalue-message)
- [مستندات Google Chrome برای `console.dir()`](https://developer.chrome.com/docs/devtools/console/api/#dir)