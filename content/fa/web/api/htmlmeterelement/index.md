---
title: "HTMLMeterElement"
---

---
title: HTMLMeterElement
slug: Web/API/HTMLMeterElement
page-type: web-api-interface
browser-compat: api.HTMLMeterElement
---

{{APIRef("HTML DOM")}}

المان‌های HTML {{HTMLElement("meter")}} رابط **`HTMLMeterElement`** را نمایان می‌کنند که ویژگی‌ها و متدهای خاصی را (علاوه بر رابط شیء {{domxref("HTMLElement")}} که به صورت ارث‌بری در اختیار دارند) برای دستکاری طرح‌بندی و نمایش المان‌های {{HTMLElement("meter")}} فراهم می‌کند.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_علاوه بر این، ویژگی‌هایی را از والد خود، {{domxref("HTMLElement")}}، به ارث می‌برد._

- {{domxref("HTMLMeterElement.high")}}
  - : یک `double` که مقدار مرز بالایی را نشان می‌دهد و بازتاب‌دهندهٔ صفت [`high`](/en-US/docs/Web/HTML/Reference/Elements/meter#high) است.
- {{domxref("HTMLMeterElement.low")}}
  - : یک `double` که مقدار مرز پایینی را نشان می‌دهد و بازتاب‌دهندهٔ صفت [`low`](/en-US/docs/Web/HTML/Reference/Elements/meter#low) است.
- {{domxref("HTMLMeterElement.max")}}
  - : یک `double` که حداکثر مقدار را نشان می‌دهد و بازتاب‌دهندهٔ صفت [`max`](/en-US/docs/Web/HTML/Reference/Elements/meter#max) است.
- {{domxref("HTMLMeterElement.min")}}
  - : یک `double` که حداقل مقدار را نشان می‌دهد و بازتاب‌دهندهٔ صفت [`min`](/en-US/docs/Web/HTML/Reference/Elements/meter#min) است.
- {{domxref("HTMLMeterElement.optimum")}}
  - : یک `double` که مقدار بهینه را نشان می‌دهد و بازتاب‌دهندهٔ صفت [`optimum`](/en-US/docs/Web/HTML/Reference/Elements/meter#optimum) است.
- {{domxref("HTMLMeterElement.value")}}
  - : یک `double` که مقدار فعلی را نشان می‌دهد و بازتاب‌دهندهٔ صفت [`value`](/en-US/docs/Web/HTML/Reference/Elements/meter#value) است.
- {{domxref("HTMLMeterElement.labels")}} {{ReadOnlyInline}}
  - : یک {{domxref("NodeList")}} از المان‌های {{HTMLElement("label")}} که با المان مرتبط هستند.

## متدهای نمونه

_این رابط هیچ متد خاصی را پیاده‌سازی نمی‌کند، اما متدهایی را از والد خود، {{domxref("HTMLElement")}}، به ارث می‌برد._

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- المان HTML که این رابط را پیاده‌سازی می‌کند: {{HTMLElement("meter")}}