---
title: "Element: namespaceURI property"
---

---
title: "Element: namespaceURI property"
short-title: namespaceURI
slug: Web/API/Element/namespaceURI
page-type: web-api-instance-property
browser-compat: api.Element.namespaceURI
---

{{APIRef("DOM")}}

ویژگی فقط‌خواندنی **`Element.namespaceURI`**، URI فضای نام عنصر را برمی‌گرداند؛ یا اگر عنصر در هیچ فضای نامی نباشد، `null` را برمی‌گرداند.

## مقدار

یک رشته، یا `null`.

## مثال‌ها

در این قطعه‌کد، یک عنصر از نظر {{domxref("Element.localName", "localName")}} و `namespaceURI` بررسی می‌شود. اگر `namespaceURI` فضای نام XUL را برگرداند و `localName` مقدار «browser» را برگرداند، آن گره به عنوان یک `<browser/>` XUL شناخته می‌شود.

```js
if (
  element.localName === "browser" &&
  element.namespaceURI ===
    "http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul"
) {
  // this is a XUL browser
}
```

## یادداشت‌ها

این یک مقدار محاسبه‌شده نیست که از جست‌وجوی فضای نام بر اساس بررسی اعلان‌های فضای نام در حوزه (scope) به دست آمده باشد. URI فضای نام یک گره در زمان ایجاد آن گره ثابت می‌شود.

URI فضای نام برای عناصر HTML در اسناد HTML، مانند XHTML، [`http://www.w3.org/1999/xhtml`](https://www.w3.org/1999/xhtml/) است.

می‌توانید با استفاده از متد [`document.createElementNS()`](/en-US/docs/Web/API/Document/createElementNS) عنصری با `namespaceURI` مشخص ایجاد کنید.

DOM به خودی خود اعتبارسنجی فضای نام را مدیریت یا اعمال نمی‌کند. انجام هرگونه اعتبارسنجی لازم بر عهده برنامه‌ای است که از DOM استفاده می‌کند. همچنین توجه داشته باشید که پیشوند فضای نام، پس از اینکه به یک عنصر خاص مرتبط شد، قابل تغییر نیست.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Element.localName")}}
- {{domxref("Element.prefix")}}
- {{domxref("Attr.namespaceURI")}}