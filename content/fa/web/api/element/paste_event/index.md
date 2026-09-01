---
title: "Element: paste event"
short-title: paste
slug: Web/API/Element/paste_event
page-type: web-api-event
browser-compat: api.Element.paste_event
---

{{APIRef("Clipboard API")}}

رویداد **`paste`** از [Clipboard API](/en-US/docs/Web/API/Clipboard_API) زمانی فعال می‌شود که کاربر از طریق رابط کاربری مرورگر یک عمل «چسباندن» (paste) را آغاز کرده باشد.

اگر مکان‌نما (cursor) در یک بافت قابل ویرایش قرار داشته باشد (مثلاً در یک {{HTMLElement("textarea")}} یا عنصری که ویژگی [`contenteditable`](/en-US/docs/Web/HTML/Reference/Global_attributes/contenteditable) آن روی `true` تنظیم شده است)، آنگاه عمل پیش‌فرض این است که محتویات کلیپ‌بورد در محل مکان‌نما درون سند درج شود.

یک کنترل‌کننده (handler) برای این رویداد می‌تواند با فراخوانی {{domxref("DataTransfer/getData", "getData()")}} روی ویژگی `clipboardData` رویداد، به محتویات کلیپ‌بورد دسترسی پیدا کند.

برای لغو رفتار پیش‌فرض (مثلاً برای درج داده‌ای متفاوت یا یک تبدیل از محتویات کلیپ‌بورد)، یک کنترل‌کننده رویداد باید با استفاده از {{domxref("Event/preventDefault", "event.preventDefault()")}} عمل پیش‌فرض را لغو کرده و سپس داده‌های مورد نظر خود را به‌صورت دستی درج کند.

می‌توان یک رویداد `paste` [مصنوعی (synthetic)](/en-US/docs/Web/API/Document_Object_Model/Events#creating_and_dispatching_events) ساخت و ارسال کرد، اما این کار بر محتویات سند تأثیری نخواهد گذاشت.

این رویداد در درخت DOM به سمت بالا [حباب می‌زند (bubbles)](/en-US/docs/Learn_web_development/Core/Scripting/Event_bubbling) و در نهایت به {{domxref("Document")}} و {{domxref("Window")}} می‌رسد، [قابل لغو (cancelable)](/en-US/docs/Web/API/Event/cancelable) است و [مرکب (composed)](/en-US/docs/Web/API/Event/composed) می‌باشد.

## Syntax

از نام رویداد در متدهایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد (event handler property) تنظیم نمایید.

```js-nolint
addEventListener("paste", (event) => { })

onpaste = (event) => { }
```

## Event type

یک {{domxref("ClipboardEvent")}}. از {{domxref("Event")}} ارث‌بری می‌کند.

{{InheritanceDiagram("ClipboardEvent")}}

## Examples

### نمونه زنده

#### HTML

```html
<div class="source" contenteditable="true">Copy text from this box.</div>
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
const target = document.querySelector("div.target");

target.addEventListener("paste", (event) => {
  event.preventDefault();

  let paste = (event.clipboardData || window.clipboardData).getData("text");
  paste = paste.toUpperCase();
  const selection = window.getSelection();
  if (!selection.rangeCount) return;
  selection.deleteFromDocument();
  selection.getRangeAt(0).insertNode(document.createTextNode(paste));
  selection.collapseToEnd();
});
```

#### Result

{{ EmbedLiveSample('Live_example', '100%', '120px') }}

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("Element/cut_event", "cut")}} event
- {{domxref("Element/copy_event", "copy")}} event