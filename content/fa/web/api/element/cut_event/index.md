```markdown
---
title: "Element: cut event"
short-title: cut
slug: Web/API/Element/cut_event
page-type: web-api-event
browser-compat: api.Element.cut_event
---

{{APIRef("Clipboard API")}}

رویداد **`cut`** از [API کلیپبورد](/en-US/docs/Web/API/Clipboard_API) زمانی فعال میشود که کاربر یک عمل «برش» را از طریق رابط کاربری مرورگر آغاز کند.

اگر کاربر یک عمل برش را بر روی محتوای غیرقابل ویرایش انجام دهد، رویداد `cut` همچنان فعال میشود، اما شیء رویداد حاوی هیچ دادهای نخواهد بود.

عمل پیشفرض این رویداد، کپی کردن انتخاب کنونی (در صورت وجود) به کلیپبورد سیستم و حذف آن از سند است.

یک کنترلکننده برای این رویداد میتواند محتویات کلیپبورد را با فراخوانی {{domxref("DataTransfer.setData", "setData(format, data)")}} بر روی ویژگی {{domxref("ClipboardEvent.clipboardData")}} رویداد، _تغییر_ دهد و با استفاده از {{domxref("Event/preventDefault", "event.preventDefault()")}} عمل پیشفرض را لغو کند.

توجه داشته باشید که لغو عمل پیشفرض، از بهروزرسانی سند نیز جلوگیری میکند. بنابراین، یک کنترلکننده رویداد که میخواهد عمل پیشفرض «برش» را شبیهسازی کند و در عین حال کلیپبورد را تغییر دهد، باید بهصورت دستی نیز انتخاب را از سند حذف کند.

کنترلکننده نمیتواند دادههای کلیپبورد را _بخواند_.

ساخت و ارسال یک رویداد `cut` [مصنوعی](/en-US/docs/Web/API/Document_Object_Model/Events#creating_and_dispatching_events) امکانپذیر است، اما این کار بر کلیپبورد سیستم یا محتویات سند تأثیری نخواهد داشت.

این رویداد در درخت DOM به سمت بالا [حباب میکند](/en-US/docs/Learn_web_development/Core/Scripting/Event_bubbling) و در نهایت به {{domxref("Document")}} و {{domxref("Window")}} میرسد، [قابل لغو](/en-US/docs/Web/API/Event/cancelable) و [ترکیبپذیر](/en-US/docs/Web/API/Event/composed) است.

## نحو (Syntax)

از نام رویداد در روشهایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترلکننده رویداد تنظیم کنید.

```js-nolint
addEventListener("cut", (event) => { })

oncut = (event) => { }
```

## نوع رویداد

یک {{domxref("ClipboardEvent")}}. به ارث برده شده از {{domxref("Event")}}.

{{InheritanceDiagram("ClipboardEvent")}}

## مثالها

### مثال زنده

#### HTML

```html
<div class="source" contenteditable="true">Cut text from this box.</div>
<div class="target" contenteditable="true">And paste it into this one.</div>
```

```css hidden
div.source,
div.target {
  border: 1px solid gray;
  margin: 0.5rem;
  padding: 0.5rem;
  height: 1rem;
  background-color: #e9eef1;
}
```

#### JavaScript

```js
const source = document.querySelector("div.source");

source.addEventListener("cut", (event) => {
  const selection = document.getSelection();
  event.clipboardData.setData("text/plain", selection.toString().toUpperCase());
  selection.deleteFromDocument();
  event.preventDefault();
});
```

#### نتیجه

{{ EmbedLiveSample('Live_example', '100%', '120px') }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رویداد {{domxref("Element/copy_event", "copy")}}
- رویداد {{domxref("Element/paste_event", "paste")}}
```