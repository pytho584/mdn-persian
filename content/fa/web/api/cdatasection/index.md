---
title: "CDATASection"
slug: Web/API/CDATASection
page-type: web-api-interface
browser-compat: api.CDATASection
---

{{APIRef("DOM")}}

رابط **`CDATASection`** یک بخش CDATA را نشان می‌دهد که می‌تواند درون XML برای گنجاندن بخش‌های گسترده‌ای از متن بدون escape استفاده شود. درون یک بخش CDATA، نمادهای `<` و `&` نیازی به escape کردن ندارند، برخلاف حالت عادی.

در XML، یک بخش CDATA به این شکل است:

```xml
<![CDATA[ … ]]>
```

برای مثال:

```xml
<foo>
  Here is a CDATA section: <![CDATA[ < > & ]]> with all kinds of unescaped text.
</foo>
```

تنها دنباله‌ای که درون یک بخش CDATA مجاز نیست، دنباله پایانی خود بخش CDATA یعنی `]]>` است.

> [!NOTE]
> بخش‌های CDATA نباید درون HTML استفاده شوند. آنها به عنوان توضیح (comment) در نظر گرفته شده و نمایش داده نمی‌شوند.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_این رابط ویژگی خاصی ندارد و ویژگی‌های والد خود {{DOMxRef("Text")}} را پیاده‌سازی می‌کند._

## روش‌های نمونه

_این رابط روش خاصی ندارد و روش‌های والد خود {{DOMxRef("Text")}} را پیاده‌سازی می‌کند._

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Document.createCDATASection()")}}