---
title: "HTMLInputElement: selectionDirection property"
short-title: selectionDirection
slug: Web/API/HTMLInputElement/selectionDirection
page-type: web-api-instance-property
browser-compat: api.HTMLInputElement.selectionDirection
---

{{ApiRef("HTML DOM")}}

**ویژگی `selectionDirection`** در رابط {{domxref("HTMLInputElement")}} یک رشته است که جهتی را نشان می‌دهد که کاربر در حال انتخاب متن است.

## مقدار

یک رشته. می‌تواند یکی از مقادیر زیر را داشته باشد:

- `forward`
  - کاربر در حال گسترش انتخاب به سمت انتهای متن ورودی است.
- `backward`
  - کاربر در حال گسترش انتخاب به سمت ابتدای متن ورودی است.
- `none`
  - کاربر در حال گسترش انتخاب نیست.

> [!NOTE]
> در ویندوز، جهت نشان‌دهندهٔ موقعیت مکان‌نما نسبت به انتخاب است: انتخاب «forward» مکان‌نما را در انتهای انتخاب دارد و انتخاب «backward» مکان‌نما را در ابتدای انتخاب دارد. ویندوز جهت «none» ندارد.

> [!NOTE]
> در مک، جهت نشان می‌دهد که هنگام تنظیم اندازهٔ انتخاب با استفاده از کلیدهای جهتنما و کلید Shift، کدام انتهای انتخاب تحت تأثیر قرار می‌گیرد: جهت «forward» به معنای تغییر انتهای انتخاب، و جهت «backward» به معنای تغییر ابتدای انتخاب است. جهت «none» پیش‌فرض در مک است و نشان می‌دهد که هنوز جهت خاصی انتخاب نشده است. کاربر هنگام اولین تنظیم انتخاب، بر اساس کلید جهتنمای فشرده‌شده، جهت را به‌طور ضمنی تعیین می‌کند.

## مثال‌ها

### HTML

```html
<label for="selectionDirection">selectionDirection property</label>
<input type="text" id="selectionDirection" value="MDN" />
<p id="direction"></p>
```

### JavaScript

```js
const textSelectionDirection = document.querySelector("#selectionDirection");
const pConsole = document.querySelector("#direction");
pConsole.textContent = `Selection direction : ${textSelectionDirection.selectionDirection}`;
```

### نتیجه

{{EmbedLiveSample("Examples")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLTextAreaElement.selectionDirection")}} ویژگی
- {{domxref("HTMLInputElement.selectionStart")}} ویژگی
- {{domxref("HTMLInputElement.selectionEnd")}} ویژگی
- {{domxref("HTMLInputElement.setSelectionRange")}} روش