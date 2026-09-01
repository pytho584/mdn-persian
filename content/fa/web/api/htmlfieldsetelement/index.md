---
title: HTMLFieldSetElement
slug: Web/API/HTMLFieldSetElement
page-type: web-api-interface
browser-compat: api.HTMLFieldSetElement
---

{{APIRef("HTML DOM")}}

رابطِ **`HTMLFieldSetElement`** ویژگی‌ها و روش‌های خاصی (علاوه بر رابطِ معمول {{domxref("HTMLElement")}} که به‌صورت ارث‌بری نیز در دسترس دارد) برای دستکاری چیدمان و نمایش عناصرِ {{ HTMLElement("fieldset") }} فراهم می‌کند.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_ویژگی‌ها را از والدِ خود، {{domxref("HTMLElement")}}، به ارث می‌برد._

- {{domxref("HTMLFieldSetElement.disabled")}}
  - : یک مقدار بولین که ویژگیِ HTML [`disabled`](/en-US/docs/Web/HTML/Reference/Elements/fieldset#disabled) را بازتاب می‌دهد و نشان می‌دهد که آیا کاربر می‌تواند با کنترل تعامل داشته باشد یا نه.
- {{domxref("HTMLFieldSetElement.elements")}} {{ReadOnlyInline}}
  - : عناصر متعلق به این مجموعه‌فیلد. نوع این ویژگی بستگی به نسخه‌ای از مشخصات (spec) دارد که توسط مرورگر پیاده‌سازی شده است.
- {{domxref("HTMLFieldSetElement.form")}} {{ReadOnlyInline}}
  - : یک {{domxref("HTMLFormControlsCollection")}} یا {{domxref("HTMLCollection")}} که به عنصرِ فرمِ شامل اشاره می‌کند، اگر این عنصر در یک فرم باشد.
    اگر مجموعه‌فیلد از نوادگانِ یک عنصرِ فرم نباشد، آنگاه این ویژگی می‌تواند شناسه (ID) هر عنصرِ فرمی در همان سند باشد که با آن مرتبط است، یا اگر هیچ‌کدام مطابقت نداشت، مقدار `null` باشد.
- {{domxref("HTMLFieldSetElement.name")}}
  - : یک رشته که ویژگیِ HTML [`name`](/en-US/docs/Web/HTML/Reference/Elements/fieldset#name) را بازتاب می‌دهد و شامل نام مجموعه‌فیلد است. این مقدار می‌تواند هنگام دسترسی به مجموعه‌فیلد در جاوااسکریپت استفاده شود. این ویژگی _بخشی_ از داده‌هایی که به سرور ارسال می‌شوند نیست.
- {{domxref("HTMLFieldSetElement.type")}} {{ReadOnlyInline}}
  - : رشته‌ی `"fieldset"`.
- {{domxref("HTMLFieldSetElement.validationMessage")}} {{ReadOnlyInline}}
  - : یک رشته که یک پیام بومی‌سازی‌شده را نشان می‌دهد و محدودیت‌های اعتبارسنجی که عنصر آن‌ها را برآورده نمی‌کند (در صورت وجود) توصیف می‌کند. اگر عنصر کاندیدی برای اعتبارسنجی محدودیت‌ها نباشد (`willValidate` برابر `false` باشد) یا محدودیت‌های خود را برآورده کند، این رشته خالی است.
- {{domxref("HTMLFieldSetElement.validity")}} {{ReadOnlyInline}}
  - : یک {{domxref("ValidityState")}} که حالت‌های اعتبارسنجی‌ای که این عنصر در آن قرار دارد را نشان می‌دهد.
- {{domxref("HTMLFieldSetElement.willValidate")}} {{ReadOnlyInline}}
  - : یک مقدار بولین `false`، زیرا اشیاء {{HTMLElement("fieldset")}} هرگز کاندیدای اعتبارسنجی محدودیت‌ها نیستند.

## روش‌های نمونه

_روش‌ها را از والدِ خود، {{domxref("HTMLElement")}}، به ارث می‌برد._

- {{domxref("HTMLFieldSetElement.checkValidity()")}}
  - : همیشه `true` برمی‌گرداند، زیرا اشیاء {{HTMLElement("fieldset")}} هرگز کاندیدای اعتبارسنجی محدودیت‌ها نیستند.
- {{domxref("HTMLFieldSetElement.reportValidity()")}}
  - : همیشه `true` برمی‌گرداند، زیرا اشیاء {{HTMLElement("fieldset")}} هرگز کاندیدای اعتبارسنجی محدودیت‌ها نیستند.
- {{domxref("HTMLFieldSetElement.setCustomValidity()")}}
  - : یک پیام اعتبارسنجی سفارشی برای مجموعه‌فیلد تنظیم می‌کند. اگر این پیام رشته‌ی خالی نباشد، مجموعه‌فیلد دچار خطای اعتبارسنجی سفارشی است و اعتبارسنجی را رد می‌کند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- عنصرِ HTML که این رابط را پیاده‌سازی می‌کند: {{ HTMLElement("fieldset") }}.