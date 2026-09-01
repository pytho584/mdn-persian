---
title: "HTMLIFrameElement: credentialless property"
short-title: credentialless
slug: Web/API/HTMLIFrameElement/credentialless
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.HTMLIFrameElement.credentialless
---

{{APIRef("HTML DOM")}}{{SeeCompatTable}}

ویژگی **`credentialless`** در رابط {{domxref("HTMLIFrameElement")}} مشخص می‌کند که آیا {{htmlelement("iframe")}} بدونِ اعتبار (credentialless) است یا خیر؛ یعنی اسناد داخل آن با استفاده از زمینه‌های جدید و موقتی بارگذاری می‌شوند.

این زمینه‌ها به شبکه، کوکی‌ها و داده‌های ذخیره‌سازی مرتبط با مبدأ خود دسترسی ندارند. در عوض، از داده‌های جدیدی استفاده می‌کنند که فقط در طول عمر سند سطح بالا معتبر هستند. این یعنی پس از اینکه کاربر از صفحه خارج شد یا آن را دوباره بارگذاری کرد، هیچ‌یک از داده‌های ذخیره‌شده دیگر قابل دسترسی نخواهند بود.

در مقابل، قوانین جاسازی {{httpheader("Cross-Origin-Embedder-Policy")}} (COEP) قابل برداشتن هستند؛ بنابراین اسنادی که COEP را تنظیم کرده‌اند می‌توانند اسناد شخص ثالثی را که این خط‌مشی را ندارند جاسازی کنند. برای توضیحات بیشتر به [IFrame credentialless](/en-US/docs/Web/HTTP/Guides/IFrame_credentialless) مراجعه کنید.

## مقدار

یک مقدار بولین (boolean). مقدار پیش‌فرض `false` است؛ آن را روی `true` قرار دهید تا `<iframe>` بدونِ اعتبار شود.

## مثال‌ها

### خواندن

یک `<iframe>` بدونِ اعتبار را به این صورت تعریف کنید:

```html
<iframe
  src="https://en.wikipedia.org/wiki/Spectre_(security_vulnerability)"
  title="Spectre vulnerability Wikipedia page"
  width="960"
  height="600"
  credentialless></iframe>
```

مقدار ویژگی `credentialless` را برگردانید:

```js
const iframeElem = document.querySelector("iframe");
console.log(iframeElem.credentialless); // will return true in supporting browsers
```

### تنظیم

یا اینکه در HTML فقط حداقل جزئیات را مشخص کنید:

```html
<iframe width="960" height="600"> </iframe>
```

سپس `credentialless` را روی `true` قرار دهید و محتوای `<iframe>` را از طریق اسکریپت بارگذاری کنید:

```js
const iframeElem = document.querySelector("iframe");

iframeElem.credentialless = true;
iframeElem.title = "Spectre vulnerability Wikipedia page";
iframeElem.src =
  "https://en.wikipedia.org/wiki/Spectre_(security_vulnerability)";
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [IFrame credentialless](/en-US/docs/Web/HTTP/Guides/IFrame_credentialless)
- {{htmlelement("iframe")}}