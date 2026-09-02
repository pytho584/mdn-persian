---
title: "MutationEvent: initMutationEvent() method"
short-title: initMutationEvent()
slug: Web/API/MutationEvent/initMutationEvent
page-type: web-api-instance-method
status:
  - deprecated
  - non-standard
browser-compat: api.MutationEvent.initMutationEvent
---

{{APIRef("UI Events")}}{{deprecated_header}}{{non-standard_header}}

متد **`initMutationEvent()`** از رابط {{domxref("MutationEvent")}} مقدار یک رویداد جهش (mutation) را پس از ایجاد آن (معمولاً با استفاده از متد {{domxref("Document.createEvent()")}}) مقداردهی اولیه می‌کند.

این متد باید قبل از ارسال رویداد (با استفاده از {{ domxref("EventTarget.dispatchEvent()") }}) فراخوانی شود تا رویداد تنظیم گردد.

> [!NOTE]
> به طور کلی، شما خودتان این رویدادها را ایجاد نمی‌کنید؛ آن‌ها توسط مرورگر ساخته می‌شوند.

## نحو (Syntax)

```js-nolint
initMutationEvent(type, canBubble, cancelable, relatedNode,
                  prevValue, newValue, attrName, attrChange)
```

### پارامترها

- `type`
  - : یک رشته (string) که {{domxref("Event.type", "type")}} رویداد را تنظیم می‌کند. مرورگرها مقادیر زیر را برای {{domxref("MutationEvent")}} تنظیم می‌کنند:
    `DOMAttrModified`، `DOMAttributeNameChanged`، `DOMCharacterDataModified`، `DOMElementNameChanged`، `DOMNodeInserted`، `DOMNodeInsertedIntoDocument`، `DOMNodeRemoved`، `DOMNodeRemovedFromDocument`، `DOMSubtreeModified`.
- `canBubble`
  - : یک مقدار بولی (boolean) که مشخص می‌کند آیا رویداد می‌تواند bubble کند یا خیر. مقدار {{domxref("Event.bubbles")}} را تنظیم می‌کند.
- `cancelable`
  - : یک مقدار بولی که مشخص می‌کند آیا می‌توان از اقدام پیش‌فرض رویداد جلوگیری کرد یا خیر. مقدار {{domxref("Event.cancelable")}} را تنظیم می‌کند.
- `relatedNode`
  - : یک رشته که مقدار جدید گره اصلاح‌شده را (در صورت وجود) نشان می‌دهد. مقدار {{domxref("MutationEvent.relatedNode")}} را تنظیم می‌کند.
- `prevValue`
  - : یک رشته که مقدار قبلی گره اصلاح‌شده را (در صورت وجود) نشان می‌دهد. مقدار {{domxref("MutationEvent.prevValue")}} را تنظیم می‌کند.
- `newValue`
  - : یک رشته که مقدار جدید گره اصلاح‌شده را (در صورت وجود) نشان می‌دهد. مقدار {{domxref("MutationEvent.newValue")}} را تنظیم می‌کند.
- `attrName`
  - : یک رشته که نام گره {{domxref("Attr")}} تغییر یافته را (در صورت وجود) نشان می‌دهد. مقدار {{domxref("MutationEvent.attrName")}} را تنظیم می‌کند.
- `attrChange`
  - : یک عدد صحیح (integer) که دلیل تغییر گره صفت را نشان می‌دهد. مقدار {{domxref("MutationEvent.attrChange")}} را تنظیم می‌کند.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}