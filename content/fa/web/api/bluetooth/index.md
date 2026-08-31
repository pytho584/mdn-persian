---
title: "Bluetooth"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Bluetooth"
translated_by: "n8n + AI"
---

---
title: Bluetooth
slug: Web/API/Bluetooth
page-type: web-api-interface
status:
  - experimental
browser-compat: api.Bluetooth
---

{{APIRef("Bluetooth API")}}{{securecontext_header}}{{SeeCompatTable}}

رابط **`Bluetooth`** در [Web Bluetooth API](/en-US/docs/Web/API/Web_Bluetooth_API) روش‌هایی برای بررسی در دسترس بودن بلوتوث و درخواست دسترسی به دستگاه‌ها فراهم می‌کند.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_ویژگی‌ها را از والد خود، {{domxref("EventTarget")}}، به ارث می‌برد._

## متدهای نمونه

- {{domxref("Bluetooth.getAvailability","Bluetooth.getAvailability()")}} {{Experimental_Inline}}
  - : یک {{jsxref("Promise")}} برمی‌گرداند که به یک مقدار بولی (Boolean) تبدیل می‌شود و نشان می‌دهد که آیا عامل کاربر (User Agent) می‌تواند از بلوتوث پشتیبانی کند یا خیر. برخی عامل‌های کاربر به کاربر اجازه می‌دهند گزینه‌ای را تنظیم کند که مشخص می‌کند این متد چه مقداری را برمی‌گرداند.
- {{domxref("Bluetooth.getDevices","Bluetooth.getDevices()")}} {{Experimental_Inline}}
  - : یک {{jsxref("Promise")}} برمی‌گرداند که به آرایه‌ای از {{domxref("BluetoothDevice")}}ها تبدیل می‌شود که این مبدأ (origin) اجازه دسترسی به آن‌ها را دارد. مجوز از طریق فراخوانی‌های قبلی {{domxref("Bluetooth.requestDevice","Bluetooth.requestDevice()")}} به دست می‌آید.
- {{domxref("Bluetooth.requestDevice","Bluetooth.requestDevice()")}} {{Experimental_Inline}}
  - : یک {{jsxref("Promise")}} برمی‌گرداند که به یک شیء {{domxref("BluetoothDevice")}} منطبق با گزینه‌های مشخص‌شده تبدیل می‌شود.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}