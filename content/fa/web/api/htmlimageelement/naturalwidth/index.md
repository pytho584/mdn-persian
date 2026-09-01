---
title: "HTMLImageElement: naturalWidth property"
short-title: naturalWidth
slug: Web/API/HTMLImageElement/naturalWidth
page-type: web-api-instance-property
browser-compat: api.HTMLImageElement.naturalWidth
---

{{APIRef("HTML DOM")}}

خاصیت فقط-خواندنی **`naturalWidth`** از رابط {{domxref("HTMLImageElement")}} عرض ذاتی (طبیعی) و تصحیح‌شده بر اساس تراکم تصویر را بر حسب {{Glossary("CSS pixel", "پیکسل‌های CSS")}} برمی‌گرداند.

این عرضی است که تصویر در صورت رسم بدون هیچ محدودیت عرضی خواهد داشت؛ اگر نه عرضی برای تصویر تعیین کنید و نه تصویر را درون ظرفی قرار دهید که عرض آن را محدود یا به‌صراحت مشخص کند، تصویر با این عرض نمایش داده می‌شود.

> [!NOTE]
> در بیشتر مواقع، عرض طبیعی همان عرض واقعی تصویری است که توسط سرور ارسال شده است. با این حال، مرورگرها می‌توانند تصویر را قبل از ارسال به رندرکننده تغییر دهند. برای مثال، کروم [وضوح تصاویر را در دستگاه‌های کم‌قدرت کاهش می‌دهد](https://crbug.com/1187043#c7). در چنین مواردی، `naturalWidth` عرض تصویر تغییر یافته توسط این مداخلات مرورگر را به‌عنوان عرض طبیعی در نظر گرفته و این مقدار را برمی‌گرداند.

## مقدار

یک مقدار عدد صحیح که عرض ذاتی تصویر را بر حسب پیکسل‌های CSS نشان می‌دهد. این عرضی است که تصویر به‌طور طبیعی در زمانی که هیچ محدودیت یا مقدار مشخصی برای آن تعیین نشده است، رسم می‌شود. این عرض طبیعی برای تراکم پیکسلی دستگاهی که تصویر روی آن نمایش داده می‌شود تصحیح شده است، بر خلاف {{domxref("HTMLImageElement.width", "width")}}.

اگر عرض ذاتی در دسترس نباشد - یا به دلیل اینکه تصویر عرض ذاتی مشخص نکرده است یا به دلیل اینکه داده‌های تصویر برای به‌دست آوردن این اطلاعات در دسترس نیستند - `naturalWidth` مقدار 0 را برمی‌گرداند.

## مثال‌ها

برای مشاهده کد نمونه‌ای که یک تصویر را هم در اندازه طبیعی «تنظیم‌شده بر اساس تراکم» و هم در اندازه رندر شده‌اش که توسط CSS صفحه و سایر عوامل تغییر یافته است نمایش می‌دهد، به [`HTMLImageElement.naturalHeight`](/en-US/docs/Web/API/HTMLImageElement/naturalHeight#examples) مراجعه کنید.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("HTMLImageElement.width")}}
- {{domxref("HTMLImageElement.naturalHeight")}}