---
title: "Navigator: webdriver property"
---

---
title: "Navigator: webdriver property"
short-title: webdriver
slug: Web/API/Navigator/webdriver
page-type: web-api-instance-property
browser-compat: api.Navigator.webdriver
---

{{APIRef("WebDriver")}}

ویژگی فقط خواندنی **`webdriver`** از رابط {{domxref("navigator")}} نشان می‌دهد که آیا عامل کاربر (user agent) توسط خودکارسازی (automation) کنترل می‌شود یا خیر.

این ویژگی یک روش استاندارد برای عامل‌های کاربر همکار تعریف می‌کند تا به سند اطلاع دهند که توسط [WebDriver](/en-US/docs/Web/WebDriver) کنترل می‌شود، به عنوان مثال، تا مسیرهای کد جایگزین در طول خودکارسازی فعال شوند.

ویژگی `navigator.webdriver` در شرایط زیر `true` است:

- Chrome
  - : پرچم `--enable-automation` یا `--headless` استفاده شود، یا پرچم `--remote-debugging-port` با پورت 0 مشخص شده باشد.
- Firefox
  - : تنظیمات (preference) `marionette.enabled` فعال باشد یا پرچم `--marionette` ارسال شود.

## مقدار

یک {{JSxRef("Boolean")}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}