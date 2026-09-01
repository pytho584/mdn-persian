---
title: "Element: copy event"
short-title: copy
slug: Web/API/Element/copy_event
page-type: web-api-event
browser-compat: api.Element.copy_event
---

{{APIRef("Clipboard API")}}

رویداد **`copy`** از [Clipboard API](/en-US/docs/Web/API/Clipboard_API) زمانی رخ می‌دهد که کاربر از طریق رابط کاربری مرورگر، عمل کپی را آغاز کند.

عمل پیش‌فرض این رویداد، کپی‌کردن انتخاب فعلی (در صورت وجود) به کلیپ‌بورد است.

یک مدیریت‌کننده رویداد (handler) برای این رویداد می‌تواند با فراخوانی {{domxref("DataTransfer.setData", "setData(format, data)")}} روی ویژگی {{domxref("ClipboardEvent.clipboardData")}} رویداد، محتوای کلیپ‌بورد را _تغییر دهد_ و با استفاده از {{domxref("Event/preventDefault", "event.preventDefault()")}} عمل پیش‌فرض رویداد را لغو کند.

با این حال، مدیریت‌کننده رویداد نمی‌تواند داده‌های کلیپ‌بورد را _بخواند_.

امکان ساخت و ارسال یک رویداد `copy` [مصنوعی (synthetic)](/en-US/docs/Web/API/Document_Object_Model/Events#creating_and_dispatching_events) وجود دارد، اما این کار روی کلیپ‌بورد سیستمی تأثیری نخواهد گذاشت.

این رویداد در درخت DOM به سمت بالا [منتشر می‌شود](/en-US/docs/Learn_web_development/Core/Scripting/Event_bubbling) و در نهایت به {{domxref("Document")}} و {{domxref("Window")}} می‌رسد. این رویداد [لغوپذیر (cancelable)](/en-US/docs/Web/API/Event/cancelable) و [composed](/en-US/docs/Web/API/Event/composed) است.

## نحو (Syntax)

نام رویداد را در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} به کار ببرید، یا یک ویژگی مدیریت رویداد (event handler property) تنظیم کنید.

```js-nolint
addEventListener("copy", (event) => { })

oncopy = (event) => { }
```

## نوع رویداد

یک {{domxref("ClipboardEvent")}} که از {{domxref("Event")}} ارث می‌برد.

{{InheritanceDiagram("ClipboardEvent")}}

## مثال‌ها

### مثال زنده

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
const source = document.querySelector("div.source");

source.addEventListener("copy", (event) => {
  const selection = document.getSelection();
  event.clipboardData.setData("text/plain", selection.toString().toUpperCase());
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

- رویداد {{domxref("Element/cut_event", "cut")}}
- رویداد {{domxref("Element/paste_event", "paste")}}