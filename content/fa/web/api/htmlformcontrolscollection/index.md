```
---
title: HTMLFormControlsCollection
slug: Web/API/HTMLFormControlsCollection
page-type: web-api-interface
browser-compat: api.HTMLFormControlsCollection
---

{{APIRef("HTML DOM")}}

رابط **`HTMLFormControlsCollection`** یک _مجموعه_ از _عناصر کنترلی فرم_ HTML را نشان می‌دهد که توسط خاصیت {{domxref("HTMLFormElement.elements", "elements")}} از رابط {{domxref("HTMLFormElement")}} بازگردانده می‌شود.

مجموعه بازگردانده‌شده توسط {{domxref("HTMLFormElement.elements")}} شامل کنترل‌های فرم فهرست‌شده (listed form controls) مرتبط با آن فرم است. برای فهرست [کنترل‌های فرم فهرست‌شده](/en-US/docs/Web/API/HTMLFormElement/elements#value) و توضیح [ارتباط با فرم](/en-US/docs/Web/API/HTMLFormElement/elements#associated_form_controls) به {{domxref("HTMLFormElement.elements")}} مراجعه کنید.

این رابط یک متد از {{domxref("HTMLCollection")}} را که بر پایه آن ساخته شده است، جایگزین می‌کند.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_این رابط ویژگی‌های والد خود، {{domxref("HTMLCollection")}}، را به ارث می‌برد._

## روش‌های نمونه

_این رابط روش‌های والد خود، {{domxref("HTMLCollection")}}، را به ارث می‌برد._

- {{domxref("HTMLFormControlsCollection.namedItem()")}}
  - : عنصر {{domxref("RadioNodeList")}} یا {{domxref("Element")}} در مجموعه را برمی‌گرداند که `name` یا `id` آن با نام مشخص‌شده مطابقت داشته باشد، یا اگر هیچ گرهی مطابقت نداشت `null` را برمی‌گرداند. توجه کنید که این نسخه از `namedItem()`، نسخه به ارث رسیده از {{domxref("HTMLCollection")}} را پنهان می‌کند. مانند آن روش، استفاده از نحو براکت آرایه جاوااسکریپت با {{jsxref("String")}}، مانند `collection["value"]`، معادل `collection.namedItem("value")` است.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLCollection")}}, {{domxref("RadioNodeList")}}, {{domxref("HTMLOptionsCollection")}}
```