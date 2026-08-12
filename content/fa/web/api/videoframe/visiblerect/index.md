---
title: "VideoFrame: visibleRect property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/VideoFrame/visibleRect"
status: "needs-translation"
---

---
title: "VideoFrame: visibleRect property"
short-title: visibleRect
slug: Web/API/VideoFrame/visibleRect
page-type: web-api-instance-property
browser-compat: api.VideoFrame.visibleRect
---

{{APIRef("Web Codecs API")}}{{AvailableInWorkers("window_and_dedicated")}}

The **`visibleRect`** property of the {{domxref("VideoFrame")}} interface returns a {{domxref("DOMRectReadOnly")}} describing the visible rectangle of pixels for this `VideoFrame`.

## Value

A {{domxref("DOMRectReadOnly")}}.

## Examples

The following example prints the `visibleRect` to the console.

```js
console.log(VideoFrame.visibleRect);
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}
