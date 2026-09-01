---
title: "HTMLButtonElement: validationMessage property"
short-title: validationMessage
slug: Web/API/HTMLButtonElement/validationMessage
page-type: web-api-instance-property
browser-compat: api.HTMLButtonElement.validationMessage
---

{{APIRef("HTML DOM")}}

ویژگی فقط‌خواندنی **`validationMessage`** متعلق به رابط {{domxref("HTMLButtonElement")}} یک رشته را برمی‌گرداند که یک پیام محلی‌سازی‌شده را توصیف می‌کند که نشان‌دهندهٔ محدودیت‌های اعتبارسنجی (constraint validation) است که کنترل {{htmlelement("button")}} آن‌ها را برآورده نمی‌کند (در صورت وجود). اگر کنترل نامزد اعتبارسنجی محدودیت نباشد (نوع `type` عنصر `<button>` برابر با `button` یا `reset` باشد) یا محدودیت‌های خود را برآورده کند، این رشته خالی خواهد بود.

اگر `<button>` نامزد اعتبارسنجی محدودیت باشد (نوع `type` روی `submit` تنظیم شده باشد یا به‌طور پیش‌فرض `submit` باشد و {{domxref("HTMLButtonElement.willValidate")}} برابر `true` باشد) و محدودیت‌ها برآورده نشوند (یک {{domxref("ValidityState.customError")}} غیر null وجود داشته باشد)، مقدار این ویژگی همان پیام خطایی است که در طول اعتبارسنجی عنصر به کاربر نشان داده می‌شود.

## مقدار

یک رشته.

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{HTMLElement("button")}}
- {{domxref("HTMLButtonElement")}}
- {{domxref("HTMLButtonElement.willValidate")}}
- {{domxref("HTMLButtonElement.validity")}}
- {{domxref("HTMLButtonElement.checkValidity()")}}
- {{domxref("HTMLButtonElement.reportValidity()")}}
- {{domxref("HTMLButtonElement.setCustomValidity()")}}
- [یادگیری: اعتبارسنجی فرم سمت کلاینت](/en-US/docs/Learn_web_development/Extensions/Forms/Form_validation)
- [راهنما: اعتبارسنجی محدودیت](/en-US/docs/Web/HTML/Guides/Constraint_validation)
- شبه‌کلاس‌های CSS {{cssxref(":valid")}} و {{cssxref(":invalid")}}