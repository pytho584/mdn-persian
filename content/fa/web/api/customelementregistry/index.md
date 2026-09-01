---
title: CustomElementRegistry
slug: Web/API/CustomElementRegistry
page-type: web-api-interface
browser-compat: api.CustomElementRegistry

{{APIRef("Web Components")}}

رابط **`CustomElementRegistry`** روش‌هایی برای ثبت عناصر سفارشی و پرس‌وجو از عناصر ثبت‌شده فراهم می‌کند. برای دریافت یک نمونه از آن، از ویژگی {{domxref("window.customElements")}} استفاده کنید. برای ایجاد یک ثبت‌نام محدوده‌ای (scoped registry)، از سازنده {{domxref("CustomElementRegistry.CustomElementRegistry()", "CustomElementRegistry()")}} استفاده کنید.

## سازنده

- {{domxref("CustomElementRegistry.CustomElementRegistry()", "CustomElementRegistry()")}}
  - : یک شیء `CustomElementRegistry` جدید برای استفاده محدوده‌ای ایجاد می‌کند.

## روش‌های نمونه

- {{domxref("CustomElementRegistry.define()")}}
  - : یک [عنصر سفارشی](/en-US/docs/Web/API/Web_components/Using_custom_elements) جدید تعریف می‌کند.
- {{domxref("CustomElementRegistry.get()")}}
  - : سازنده عنصر سفارشی با نام داده‌شده را برمی‌گرداند، یا اگر عنصر سفارشی تعریف نشده باشد {{jsxref("undefined")}} را برمی‌گرداند.
- {{domxref("CustomElementRegistry.getName()")}}
  - : نام عنصر سفارشی از پیش تعریف‌شده را برمی‌گرداند، یا اگر عنصر سفارشی تعریف نشده باشد `null` را برمی‌گرداند.
- {{domxref("CustomElementRegistry.upgrade()")}}
  - : یک عنصر سفارشی را مستقیماً ارتقا می‌دهد، حتی پیش از آن که به ریشه سایه (shadow root) خود متصل شود.
- {{domxref("CustomElementRegistry.initialize()")}}
  - : یک ثبت‌نام محدوده‌ای را با یک زیردرخت DOM مرتبط می‌کند، ثبت‌نام عنصر سفارشی را روی هر فرزند شامل‌شونده تنظیم کرده و هر عنصر سفارشی را ارتقا می‌دهد.
- {{domxref("CustomElementRegistry.whenDefined()")}}
  - : یک {{jsxref("Promise")}} خالی برمی‌گرداند که وقتی یک عنصر سفارشی با نام داده‌شده تعریف شود، حل می‌شود. اگر چنین عنصر سفارشی از قبل تعریف شده باشد، پرامیس برگشتی بلافاصله برآورده می‌شود.

## مثال‌ها

بخش [مثال‌ها](/en-US/docs/Web/API/Web_components/Using_custom_elements#examples) را در [راهنمای استفاده از عناصر سفارشی](/en-US/docs/Web/API/Web_components/Using_custom_elements) ما ببینید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}