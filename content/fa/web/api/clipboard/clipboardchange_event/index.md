---
title: "Clipboard: clipboardchange event"
slug: Web/API/Clipboard/clipboardchange_event
page-type: web-api-event
status:
  - experimental
browser-compat: api.Clipboard.clipboardchange_event
---

{{APIRef("HTML DOM")}}{{SeeCompatTable}}

رویداد **`clipboardchange`** از رابط {{domxref("Clipboard")}} زمانی رخ می‌دهد که محتویات کلیپ‌بورد سیستم به هر شکلی تغییر کند؛ برای مثال از طریق دستور کپی سیستمی یا از طریق یک متد API مانند {{domxref("Clipboard.writeText()")}}.

رویداد `clipboardchange` تنها با [فعال‌سازی چسبنده](/en-US/docs/Glossary/Sticky_activation) یا پس از اعطای مجوز `clipboard-read` رخ می‌دهد.

## نحو

نام رویداد را در متدهایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} به کار ببرید، یا یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("clipboardchange", (event) => { })

onclipboardchange = (event) => { }
```

## نوع رویداد

یک {{domxref("ClipboardChangeEvent")}} که از {{domxref("Event")}} به ارث می‌رسد.

{{InheritanceDiagram("ClipboardChangeEvent")}}

## مثال‌ها

### گوش دادن به دستورهای کپی سیستمی

این مثال نشان می‌دهد که چگونه به دستورهای کپی سیستمی گوش دهید و محتوای کپی‌شده به کلیپ‌بورد را نمایش دهید.

#### HTML

بخش HTML شامل سه عنصر {{htmlelement("p")}} است — یکی برای نمایش محتویات کلیپ‌بورد و دو مورد حاوی متن نمونه برای کپی.

```html live-sample___basic-usage
<p id="output">Copied text:</p>

<p>
  Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed a mattis purus.
  Donec at ipsum libero. Maecenas at dictum turpis. Vivamus eget aliquet augue.
  Aenean tempor dictum posuere. Vestibulum vehicula, nulla ac convallis feugiat,
  tortor velit lobortis est, vitae convallis velit libero vel urna. Suspendisse
  potenti. In bibendum ex et pellentesque gravida. Phasellus magna risus,
  euismod vitae sem in, viverra venenatis lacus. Sed dignissim risus eu congue
  consequat. Vestibulum nec feugiat libero. Maecenas quis sodales lorem, eu
  luctus nisl. Cras vel diam sed lacus finibus elementum sed sed nunc.
</p>

<p>
  Nam ac metus eget est bibendum pulvinar. Nunc a venenatis lorem. Lorem ipsum
  dolor sit amet, consectetur adipiscing elit. In dignissim, arcu ornare luctus
  pharetra, dui velit faucibus leo, ac posuere ipsum risus vel ligula. Morbi
  varius, felis et ornare efficitur, tortor erat imperdiet lacus, non rhoncus
  lectus sapien sit amet augue. Suspendisse potenti. Sed fringilla mi augue, at
  laoreet felis varius in. Donec venenatis gravida lacus ut rutrum. Donec
  suscipit egestas justo. Proin semper nibh tortor, sit amet elementum metus
  placerat quis. Sed consectetur leo sed lorem varius, sit amet ultrices sem
  tincidunt. Vivamus facilisis at velit eget commodo.
</p>
```

```css hidden live-sample___basic-usage
body {
  margin: 0 5px;
}
#output {
  font-family: "Helvetica", "Arial";
  padding: 10px;
  border: 2px solid #cccccc;
  border-radius: 5px;
}
```

#### JavaScript

در اسکریپت خود، ابتدا ارجاعی به عنصر `<p>` خروجی می‌گیریم. سپس یک کنترل‌کننده رویداد `clipboardchange` روی شیء `Clipboard` مرورگر تعریف می‌کنیم. وقتی رویداد رخ داد، متد {{domxref("Clipboard.readText()")}} را برای خواندن متنی که به تازگی در کلیپ‌بورد کپی شده است فراخوانی می‌کنیم. وقتی نتیجه برگردانده شد، آن را به عنوان مقدار `textContent` پاراگراف خروجی تنظیم می‌کنیم.

```js live-sample___basic-usage
const outputPara = document.querySelector("#output");

navigator.clipboard.addEventListener("clipboardchange", (event) => {
  navigator.clipboard
    .readText()
    .then((text) => (outputPara.textContent = `Copied text: ${text}`));
});
```

#### نتیجه

نمونه رندر شده به صورت زیر است:

{{EmbedLiveSample("basic-usage", '100%', "350px", "", "", "", "clipboard-read")}}

مقداری از متن مثال را انتخاب کنید و سپس با استفاده از <kbd>Ctrl</kbd> + <kbd>C</kbd> (یا <kbd>Cmd</kbd> + <kbd>C</kbd> اگر از مک استفاده می‌کنید) آن را در کلیپ‌بورد کپی کنید. در اولین تلاش، یک اعلان مجوز مشاهده خواهید کرد که از شما اجازه خواندن محتویات کلیپ‌بورد را می‌خواهد. پس از آن (یا بلافاصله در تلاش‌های بعدی)، باید متنی که کپی کرده‌اید را در پاراگراف خروجی بالای رابط کاربری ببینید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("ClipboardChangeEvent")}}
- [Clipboard API](/en-US/docs/Web/API/Clipboard_API)