---
title: "Node: textContent property"
short-title: textContent
slug: Web/API/Node/textContent
page-type: web-api-instance-property
browser-compat: api.Node.textContent
---

{{APIRef("DOM")}}

ویژگی **`textContent`** در رابط {{domxref("Node")}} محتوای متنی گره و تمام فرزندان آن را نشان می‌دهد.

> [!NOTE]
> `textContent` و {{domxref("HTMLElement.innerText")}} به راحتی با یکدیگر اشتباه گرفته می‌شوند، اما این دو ویژگی [تفاوت‌های مهمی](#differences_from_innertext) با هم دارند.

## مقدار

یک رشته (string)، یا [`null`](/en-US/docs/Web/JavaScript/Reference/Operators/null). مقدار آن به موقعیت بستگی دارد:

- اگر گره یک {{domxref("document")}} یا {{glossary("doctype")}} باشد، `textContent` مقدار [`null`](/en-US/docs/Web/JavaScript/Reference/Operators/null) برمی‌گرداند.

  > [!NOTE]
  > برای دریافت _همه_ متن و [داده‌های CDATA](/en-US/docs/Web/API/CDATASection) کل سند، از `document.documentElement.textContent` استفاده کنید.

- اگر گره یک [بخش CDATA](/en-US/docs/Web/API/CDATASection)، یک نظر (comment)، یک [دستورالعمل پردازش](/en-US/docs/Web/API/ProcessingInstruction) یا یک [گره متنی](/en-US/docs/Web/API/Text) باشد، `textContent` متن داخل گره را برمی‌گرداند یا تنظیم می‌کند، یعنی همان {{domxref("Node.nodeValue")}}.
- برای سایر انواع گره، `textContent` الحاق (concatenation) `textContent` تمام گره‌های فرزند را برمی‌گرداند، به جز نظرات و دستورالعمل‌های پردازش. (اگر گره فرزندی نداشته باشد، این یک رشته خالی است.)

> [!WARNING]
> تنظیم `textContent` روی یک گره، _تمام_ فرزندان آن گره را حذف کرده و آن‌ها را با یک گره متنی واحد حاوی رشته داده شده جایگزین می‌کند.

### تفاوت‌ها با innerText

تفاوت‌های بین `Node.textContent` و {{domxref("HTMLElement.innerText")}} را با هم اشتباه نگیرید. اگرچه نام‌ها مشابه به نظر می‌رسند، تفاوت‌های مهمی وجود دارد:

- `textContent` محتوای _همه_ عناصر، از جمله عناصر {{HTMLElement("script")}} و {{HTMLElement("style")}} را دریافت می‌کند. در مقابل، `innerText` فقط عناصر «قابل خواندن برای انسان» را نشان می‌دهد.
- `textContent` هر عنصری را که در گره وجود دارد برمی‌گرداند. در مقابل، `innerText` از سبک‌دهی (styling) آگاه است و متن عناصر «پنهان» را برنمی‌گرداند.
  - علاوه بر این، از آنجایی که `innerText` سبک‌های CSS را در نظر می‌گیرد، خواندن مقدار `innerText` باعث ایجاد {{glossary("reflow")}} می‌شود تا سبک‌های محاسبه‌شده به‌روز تضمین شوند. (بازچینی (reflow) می‌تواند از نظر محاسباتی پرهزینه باشد، بنابراین باید در صورت امکان از آن اجتناب کرد.)

### تفاوت‌ها با innerHTML

{{domxref("Element.innerHTML")}} همانطور که از نامش پیداست، HTML را دریافت یا تنظیم می‌کند. توصیه می‌کنیم از `innerHTML` برای دریافت یا تنظیم متن داخل یک عنصر استفاده نکنید، زیرا با HTML خام سروکار دارد نه متن ساده، و ممکن است در معرض {{glossary("Cross-site_scripting", "حملات XSS")}} قرار گیرد. حتی اگر مطمئن باشید که متن هرگز شامل نحو HTML نیست، باز هم معنایی (semantic) کمتری دارد و کندتر است، زیرا نیاز به فراخوانی تجزیه‌کننده HTML دارد.

## مثال‌ها

با این قطعه HTML شروع کنید.

```html
<div id="divA">This is <span>some</span> text!</div>
```

می‌توانید از `textContent` برای دریافت محتوای متنی عنصر استفاده کنید:

```js
let text = document.getElementById("divA").textContent;
// The text variable is now: 'This is some text!'
```

اگر ترجیح می‌دهید محتوای متنی عنصر را تنظیم کنید، می‌توانید این کار را انجام دهید:

```js
document.getElementById("divA").textContent = "This text is different!";
// The HTML for divA is now:
// <div id="divA">This text is different!</div>
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLScriptElement.textContent")}} و {{domxref("HTMLScriptElement.text")}}
- {{domxref("HTMLElement.innerText")}}
- {{domxref("Element.innerHTML")}}