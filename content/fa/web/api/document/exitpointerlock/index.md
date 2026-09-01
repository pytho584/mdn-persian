---
title: "Document: exitPointerLock() method"
short-title: exitPointerLock()
slug: Web/API/Document/exitPointerLock
page-type: web-api-instance-method
browser-compat: api.Document.exitPointerLock
---

{{APIRef("Pointer Lock API")}}

روش **`exitPointerLock()`** در واسط {{domxref("Document")}} به صورت ناهمزمان (asynchronous) یک قفل اشاره‌گر (pointer lock) را که پیش‌تر از طریق {{domxref("Element.requestPointerLock")}} درخواست شده بود، آزاد می‌کند.

> [!NOTE]
> در حالی که روش **`exitPointerLock()`** روی سند (document) فراخوانی می‌شود، روش **`requestPointerLock()`** روی یک عنصر (element) فراخوانی می‌شود.

برای پیگیری موفقیت یا شکست درخواست، لازم است به رویدادهای {{domxref("Document/pointerlockchange_event", "pointerlockchange")}} و {{domxref("Document/pointerlockerror_event", "pointerlockerror")}} گوش دهید.

## Syntax

```js-nolint
exitPointerLock()
```

### Parameters

هیچ.

### Return value

هیچ ({{jsxref("undefined")}}).

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{ domxref("Document.pointerLockElement") }}
- {{ domxref("Element.requestPointerLock()") }}
- [Pointer Lock](/en-US/docs/Web/API/Pointer_Lock_API)