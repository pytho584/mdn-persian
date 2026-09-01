---
title: "Event: isTrusted property"
short-title: isTrusted
slug: Web/API/Event/isTrusted
page-type: web-api-instance-property
browser-compat: api.Event.isTrusted

---
{{APIRef("DOM")}}{{AvailableInWorkers}}

ویژگی‌ی فقط‌خواندنی **`isTrusted`** در رابط {{domxref("Event")}} یک مقدار بولی است که وقتی رویداد توسط عامل کاربر (شامل اقدامات کاربر و روش‌های برنامه‌نویسی مانند {{domxref("HTMLElement.focus()")}}) تولید شده باشد، `true` است و وقتی رویداد از طریق {{domxref("EventTarget.dispatchEvent()")}} ارسال شده باشد، `false` است. رویداد `click` که از طریق {{domxref("HTMLElement.click()")}} فعال می‌شود، ویژگی `isTrusted` را برابر `false` قرار می‌دهد.

## مقدار

یک مقدار بولی.

## مثال

```js
if (e.isTrusted) {
  /* The event is trusted */
} else {
  /* The event is not trusted */
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}