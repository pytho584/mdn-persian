---
title: "ImageBitmap: close() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/ImageBitmap/close"
status: "needs-translation"
---

---
title: "ImageBitmap: close() method"
short-title: close()
slug: Web/API/ImageBitmap/close
page-type: web-api-instance-method
browser-compat: api.ImageBitmap.close
---

{{APIRef("Canvas API")}}{{AvailableInWorkers}}

The **`ImageBitmap.close()`**
method disposes of all graphical resources associated with an `ImageBitmap`.

## Syntax

```js-nolint
close()
```

### Parameters

None.

### Return value

None ({{jsxref("undefined")}}).

## Examples

```js
const offscreen = new OffscreenCanvas(256, 256);
const gl = offscreen.getContext("webgl");

// Perform some drawing using the gl context

const bitmap = offscreen.transferToImageBitmap();
// ImageBitmap { width: 256, height: 256 }

bitmap.close();
// ImageBitmap { width: 0, height: 0 } — disposed
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- The interface defining this method, {{domxref("ImageBitmap")}}.
