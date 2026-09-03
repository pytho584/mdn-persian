---
title: "Navigator: language property"
short-title: language
slug: Web/API/Navigator/language
page-type: web-api-instance-property
browser-compat: api.Navigator.language
---

{{APIRef("HTML DOM")}}

ویژگی فقط‌خواندنی **`language`** از رابط {{domxref("Navigator")}} یک رشته را برمی‌گرداند که زبان ترجیحی کاربر را نشان می‌دهد، معمولاً زبان رابط کاربری مرورگر.

## مقدار

یک رشته که نسخه زبان را در قالب {{glossary("BCP 47 language tag")}} نشان می‌دهد. نمونه‌هایی از برچسب‌های زبان معتبر عبارتند از `en`، `en-US`، `fr`، `fr-FR`، `es-ES` و غیره.

توجه داشته باشید که در Safari روی iOS پیش از نسخه ۱۰.۲، کد کشور برگردانده شده به حروف کوچک است: `"en-us"`، `"fr-fr"` و غیره.

## مثال‌ها

### استفاده از سازنده‌های Intl برای قالب‌بندی خاص زبان

سازنده‌های {{jsxref("Intl")}} امکان قالب‌بندی محتوا را مطابق با قوانین یک locale خاص فراهم می‌کنند. می‌توانید `navigator.language` را به آن‌ها ارسال کنید تا محتوا را در locale متناظر با زبان ترجیحی کاربر قالب‌بندی کنید:

```js
const date = new Date("2012-05-24");

const formattedDate = new Intl.DateTimeFormat(navigator.language).format(date);
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("navigator.languages")}}
- {{domxref("navigator")}}
- {{jsxref("Intl")}}