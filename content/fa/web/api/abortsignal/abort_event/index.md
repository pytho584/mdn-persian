---
title: "AbortSignal: abort event"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AbortSignal/abort_event"
translated_by: "n8n + AI"
---

# AbortSignal: رویداد abort

رویداد **`abort`** در {{domxref("AbortSignal")}} زمانی فعال می‌شود که درخواست مرتبط با آن لغو شود — یعنی با استفاده از {{domxref("AbortController.abort()")}}.

## سینتکس

می‌توانید نام رویداد را در متدهایی مثل {{domxref("EventTarget.addEventListener", "addEventListener()")}} به کار ببرید یا یک ویژگی event handler تعیین کنید.

```js-nolint
addEventListener("abort", (event) => { })

onabort = (event) => { }
```

## نوع رویداد

یک {{DOMxRef("Event")}} عمومی بدون ویژگی اضافی.

## مثال‌ها

در مثال‌های زیر، یک شیء `AbortController` جدید می‌سازیم و {{domxref("AbortSignal")}} مربوط به آن (که از طریق ویژگی `signal` در دسترس است) را دریافت می‌کنیم. سپس با استفاده از یک event handler بررسی می‌کنیم که سیگنال لغو شده است یا خیر.

می‌توانید رویداد `abort` را با متد [`addEventListener`](/en-US/docs/Web/API/EventTarget/addEventListener) تشخیص دهید:

```js
const controller = new AbortController();
const signal = controller.signal;

signal.addEventListener("abort", () => {
  console.log("درخواست لغو شد");
});
```

یا از ویژگی event handler `onabort` استفاده کنید:

```js
const controller = new AbortController();
const signal = controller.signal;

signal.onabort = () => {
  console.log("درخواست لغو شد");
};
```