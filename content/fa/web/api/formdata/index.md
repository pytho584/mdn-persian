---
title: FormData
slug: Web/API/FormData
page-type: web-api-interface
browser-compat: api.FormData
---

{{APIRef("XMLHttpRequest API")}} {{AvailableInWorkers}}

رابط **`FormData`** روشی برای ساخت مجموعه‌ای از جفت‌های کلید/مقدار فراهم می‌کند که نشان‌دهنده فیلدهای فرم و مقادیر آن‌ها هستند و می‌توان آن‌ها را با استفاده از روش‌های {{domxref("Window/fetch", "fetch()")}}، {{domxref("XMLHttpRequest.send()")}} یا {{domxref("navigator.sendBeacon()")}} ارسال کرد. این رابط از همان قالبی استفاده می‌کند که یک فرم در صورت تنظیم نوع رمزگذاری بر روی `"multipart/form-data"` استفاده می‌کرد.

همچنین می‌توانید آن را مستقیماً به سازنده {{domxref("URLSearchParams")}} ارسال کنید، اگر بخواهید پارامترهای query را به همان شکلی تولید کنید که یک {{HTMLElement("form")}} در صورت استفاده از ارسال ساده `GET` تولید می‌کرد.

یک شیء پیاده‌ساز `FormData` می‌تواند مستقیماً در ساختار {{jsxref("Statements/for...of", "for...of")}} به جای {{domxref('FormData.entries()', 'entries()')}} استفاده شود: `for (const p of myFormData)` معادل `for (const p of myFormData.entries())` است.

## سازنده

- {{domxref("FormData.FormData","FormData()")}}
  - : یک شیء `FormData` جدید ایجاد می‌کند.

## روش‌های نمونه

- {{domxref("FormData.append()")}}
  - : یک مقدار جدید به یک کلید موجود در شیء `FormData` اضافه می‌کند، یا اگر کلید وجود نداشته باشد آن را اضافه می‌کند.
- {{domxref("FormData.delete()")}}
  - : یک جفت کلید/مقدار را از یک شیء `FormData` حذف می‌کند.
- {{domxref("FormData.entries()")}}
  - : یک [تکرارگر](/en-US/docs/Web/JavaScript/Reference/Iteration_protocols) برمی‌گرداند که از میان همه جفت‌های کلید/مقدار موجود در `FormData` عبور می‌کند.
- {{domxref("FormData.get()")}}
  - : اولین مقدار مرتبط با یک کلید معین را از درون یک شیء `FormData` برمی‌گرداند.
- {{domxref("FormData.getAll()")}}
  - : آرایه‌ای از همه مقادیر مرتبط با یک کلید معین را از درون یک `FormData` برمی‌گرداند.
- {{domxref("FormData.has()")}}
  - : بررسی می‌کند که آیا یک شیء `FormData` حاوی کلید خاصی است یا خیر.
- {{domxref("FormData.keys()")}}
  - : یک [تکرارگر](/en-US/docs/Web/JavaScript/Reference/Iteration_protocols) برمی‌گرداند که از میان همه کلیدهای جفت‌های کلید/مقدار موجود در `FormData` عبور می‌کند.
- {{domxref("FormData.set()")}}
  - : یک مقدار جدید برای یک کلید موجود در شیء `FormData` تنظیم می‌کند، یا اگر کلید/مقدار وجود نداشته باشد آن را اضافه می‌کند.
- {{domxref("FormData.values()")}}
  - : یک [تکرارگر](/en-US/docs/Web/JavaScript/Reference/Iteration_protocols) برمی‌گرداند که از میان همه مقادیر موجود در `FormData` عبور می‌کند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از اشیاء FormData](/en-US/docs/Web/API/XMLHttpRequest_API/Using_FormData_Objects)
- {{HTMLElement("Form")}}