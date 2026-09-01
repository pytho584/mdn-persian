---
title: "HTMLImageElement: attributionSrc property"
---

---
title: "HTMLImageElement: attributionSrc property"
short-title: attributionSrc
slug: Web/API/HTMLImageElement/attributionSrc
page-type: web-api-instance-property
status:
  - deprecated
  - non-standard
browser-compat: api.HTMLImageElement.attributionSrc
---

{{APIRef("Attribution Reporting API")}}{{securecontext_header}}{{deprecated_header}}{{non-standard_header}}

ویژگی **`attributionSrc`** از رابط {{domxref("HTMLImageElement")}}، رشته‌ای را مشخص می‌کند که باعث می‌شود مرورگر یک هدر {{httpheader("Attribution-Reporting-Eligible")}} را همراه با درخواست تصویر ارسال کند. این ویژگی، ویژگی محتوایی [`attributionsrc`](/en-US/docs/Web/HTML/Reference/Elements/img#attributionsrc) عنصر `<img>` را بازتاب می‌دهد.

برای جزئیات بیشتر، به [Attribution Reporting API](/en-US/docs/Web/API/Attribution_Reporting_API) مراجعه کنید.

## مقدار

رشته‌ای که یا خالی است یا فهرستی از URLها که با فاصله از هم جدا شده‌اند. برای تفسیر این ویژگی، به مرجع [`<img>`](/en-US/docs/Web/HTML/Reference/Elements/img#attributionsrc) در HTML مراجعه کنید.

## مثال‌ها

### تنظیم یک attributionSrc خالی

```html
<img src="advertising-image.png" />
```

```js
const imgElem = document.querySelector("img");
imgElem.attributionSrc = "";
```

### تنظیم یک attributionSrc شامل URLها

```html
<img src="advertising-image.png" />
```

```js
// encode the URLs in case they contain special characters
// such as '=' that would be improperly parsed.
const encodedUrlA = encodeURIComponent("https://a.example/register-source");
const encodedUrlB = encodeURIComponent("https://b.example/register-source");

const imgElem = document.querySelector("img");
imgElem.attributionSrc = `${encodedUrlA} ${encodedUrlB}`;
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [Attribution Reporting API](/en-US/docs/Web/API/Attribution_Reporting_API).