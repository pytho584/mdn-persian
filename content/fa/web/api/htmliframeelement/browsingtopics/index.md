---
title: "HTMLIFrameElement: browsingTopics property"
---

---
title: "HTMLIFrameElement: browsingTopics property"
short-title: browsingTopics
slug: Web/API/HTMLIFrameElement/browsingTopics
page-type: web-api-instance-property
status:
  - deprecated
  - non-standard
browser-compat: api.HTMLIFrameElement.browsingTopics
---

{{APIRef("HTML DOM")}}{{non-standard_header}}{{deprecated_header}}

> [!WARNING]
> این ویژگی در حال حاضر با مخالفت دو فروشندهٔ مرورگر مواجه است. برای جزئیات مخالفت، بخش [مواضع استانداردها](/en-US/docs/Web/API/Topics_API#standards_positions) را ببینید.

ویژگی **`browsingTopics`** از رابط {{domxref("HTMLIFrameElement")}} یک مقدار بولی است که مشخص می‌کند موضوعات انتخاب‌شده برای کاربر فعلی باید همراه با درخواست منبع {{htmlelement("iframe")}} مرتبط، در یک هدر {{httpheader("Sec-Browsing-Topics")}} ارسال شوند. این ویژگی منعکس‌کنندهٔ ویژگی HTML «browsingtopics» است.

## مقدار

یک مقدار بولی. مقدار پیش‌فرض `false` است؛ برای ارسال درخواست منبع `<iframe>` مرتبط با هدر {{httpheader("Sec-Browsing-Topics")}} حاوی موضوعات انتخاب‌شده برای کاربر فعلی، آن را روی `true` قرار دهید.

## مثال‌ها

### دریافت

مقدار `browsingtopics` را روی `true` قرار دهید و سپس محتوای `<iframe>` را به‌صورت اعلامی بارگذاری کنید:

```html
<iframe browsingtopics title="Advertising container" src="ad-tech1.example">
  ...
</iframe>
```

مقدار `browsingTopics` را از طریق اسکریپت ثبت (لاگ) کنید:

```js
const iframeElem = document.querySelector("iframe");
console.log(iframeElem.browsingTopics); // will return true in supporting browsers
```

### تنظیم

یک `<iframe>` حداقلی مشخص کنید:

```html
<iframe> ... </iframe>
```

مقدار `browsingtopics` را روی `true` قرار دهید و سپس محتوای `<iframe>` را از طریق اسکریپت بارگذاری کنید:

```js
const iframeElem = document.querySelector("iframe");

iframeElem.browsingTopics = true;
iframeElem.title = "Advertising container";
iframeElem.src = "ad-tech1.example";
```

## مشخصات

این ویژگی بخشی از هیچ استاندارد رسمی نیست، اگرچه در [پیش‌نویس پیشنهادی غیررسمی Topics API](https://patcg-individual-drafts.github.io/topics/) مشخص شده است.

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Topics API](/en-US/docs/Web/API/Topics_API)