---
title: "Navigator: xr property"
short-title: xr
slug: Web/API/Navigator/xr
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.Navigator.xr
---

{{APIRef("WebXR Device API")}}{{SecureContext_Header}}{{SeeCompatTable}}

ویژگی فقط‌خواندنی **`xr`** که توسط رابط {{domxref("Navigator")}} ارائه می‌شود، یک شیء {{domxref("XRSystem")}} برمی‌گرداند که برای دسترسی به [WebXR Device API](/en-US/docs/Web/API/WebXR_Device_API) قابل استفاده است.

## مقدار

شیء {{domxref("XRSystem")}} که برای تعامل با [WebXR Device API](/en-US/docs/Web/API/WebXR_Device_API) در زمینهٔ فعلی استفاده می‌شود. از این شیء می‌توان برای نمایش تصاویر واقعیت افزوده و/یا واقعیت مجازی به کاربر استفاده کرد.

## مثال‌ها

هر {{domxref("Window")}} نمونهٔ مخصوص به خود از {{domxref("Navigator")}} را دارد که می‌توان از طریق {{domxref("Window.navigator","window.navigator")}} یا {{domxref("Window.navigator", "navigator")}} به آن دسترسی داشت. همزمان، یک نمونهٔ جدید از {{domxref("XRSystem")}} نیز ساخته شده و به‌عنوان `navigator.xr` به نمونهٔ `navigator` متصل می‌شود. اگر ویژگی `xr` وجود داشته باشد، می‌توانید از آن برای دسترسی به [WebXR Device API](/en-US/docs/Web/API/WebXR_Device_API) استفاده کنید.

برای تعیین اینکه آیا WebXR در دسترس است یا نه، می‌توانید کاری شبیه به این انجام دهید:

```js
if ("xr" in window.navigator) {
  /* WebXR قابل استفاده است! */
} else {
  /* WebXR در دسترس نیست */
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebGL API](/en-US/docs/Web/API/WebGL_API): گرافیک شتاب‌گرفتهٔ دوبعدی و سه‌بعدی برای وب
- [Canvas API](/en-US/docs/Web/API/Canvas_API): رابط برنامه‌نویسی گرافیک دوبعدی