---
title: "<acronym> HTML acronym or abbreviation element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/acronym"
translated_by: "n8n + AI"
---

عنوان HTML `<acronym>` — عنصر (element) مخفف یا سرواژه در HTML

عنصر **`<acronym>`** در [HTML](/en-US/docs/Web/HTML) به نویسنده اجازه می‌دهد دنباله‌ای از نویسه‌ها را که یک سرواژه (acronym) یا مخفف یک کلمه هستند، به‌وضوح مشخص کند.

> [!WARNING]
> از این عنصر استفاده نکنید. به جای آن از عنصر {{HTMLElement("abbr")}} استفاده کنید.

## ویژگی‌ها (Attributes)

این عنصر فقط [ویژگی‌های سراسری (global attributes)](/en-US/docs/Web/HTML/Reference/Global_attributes) را دارد که در همه عناصر مشترک هستند.

## رابط DOM (DOM Interface)

این عنصر رابط {{domxref('HTMLElement')}} را پیاده‌سازی می‌کند.

## مثال‌ها

```html
<p>
  The <acronym title="World Wide Web">WWW</acronym> is only a component of the
  Internet.
</p>
```

### نتیجه

(نمونه تعاملی در اینجا نمایش داده می‌شود)

## استایل پیش‌فرض (Default styling)

اگرچه هدف این تگ (tag) صرفاً برای راحتی نویسنده است، استایل پیش‌فرض آن در مرورگرهای مختلف متفاوت است:

- Opera، Firefox، Chrome و برخی دیگر یک خط‌چین زیر محتوای عنصر اضافه می‌کنند.
- تعدادی از مرورگرها نه‌تنها خط‌چین زیر اضافه می‌کنند، بلکه محتوا را با حروف کوچک (small caps) نمایش می‌دهند. برای جلوگیری از این استایل‌دهی، می‌توانید چیزی مثل {{cssxref("font-variant", "font-variant: none")}} در CSS اضافه کنید.

بنابراین توصیه می‌شود که نویسندگان وب یا صریحاً این عنصر را استایل دهند، یا با تغییرات بین مرورگرها کنار بیایند.

## مشخصات (Specifications)

(مشخصات در نسخه اصلی ذکر شده است)

## سازگاری با مرورگرها (Browser compatibility)

(جدول سازگاری در نسخه اصلی موجود است)

## همچنین ببینید

- عنصر HTML {{HTMLElement("abbr")}}