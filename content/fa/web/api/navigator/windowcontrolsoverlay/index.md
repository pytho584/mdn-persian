---
title: "Navigator: windowControlsOverlay property"
short-title: windowControlsOverlay
slug: Web/API/Navigator/windowControlsOverlay
page-type: web-api-instance-property
browser-compat: api.Navigator.windowControlsOverlay
---

{{SecureContext_Header}}{{APIRef("Window Controls Overlay API")}}

خاصیت فقط-خواندنی **`windowControlsOverlay`** از رابط {{domxref("Navigator")}}، رابط {{domxref("WindowControlsOverlay")}} را بازمی‌گرداند. این رابط اطلاعاتی در مورد هندسهٔ نوار عنوان در برنامه‌های وب پیش‌روندهٔ دسکتاپ که از [Window Controls Overlay API](/en-US/docs/Web/API/Window_Controls_Overlay_API) استفاده می‌کنند، ارائه می‌دهد.

برنامه‌های وب پیش‌رونده نصب‌شده روی سیستم‌عامل‌های دسکتاپ می‌توانند با استفاده از مقدار `window-controls-overlay` در عضو `display_override` از [بیانیهٔ برنامهٔ وب](/en-US/docs/Web/Progressive_web_apps/Manifest/Reference/display_override) خود، قابلیت Window Controls Overlay را انتخاب کنند.

این کار نوار عنوان پیش‌فرض پنجره را مخفی کرده و به برنامه دسترسی به تمام ناحیهٔ پنجرهٔ برنامه را می‌دهد.

## مقدار

رابط {{domxref("WindowControlsOverlay")}}.

## مثال‌ها

```js
if ("windowControlsOverlay" in navigator) {
  const rect = navigator.windowControlsOverlay.getTitlebarAreaRect();
  // Do something with the title bar area rectangle.
} else {
  // The Window Controls Overlay feature is not available.
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}