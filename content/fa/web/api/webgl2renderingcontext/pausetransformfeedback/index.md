---
title: "WebGL2RenderingContext: pauseTransformFeedback() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/WebGL2RenderingContext/pauseTransformFeedback"
status: "needs-translation"
---

---
title: "WebGL2RenderingContext: pauseTransformFeedback() method"
short-title: pauseTransformFeedback()
slug: Web/API/WebGL2RenderingContext/pauseTransformFeedback
page-type: web-api-instance-method
browser-compat: api.WebGL2RenderingContext.pauseTransformFeedback
---

{{APIRef("WebGL")}}{{AvailableInWorkers}}

The **`WebGL2RenderingContext.pauseTransformFeedback()`**
method of the [WebGL 2 API](/en-US/docs/Web/API/WebGL_API) pauses a transform
feedback operation.

## Syntax

```js-nolint
pauseTransformFeedback()
```

### Parameters

None.

### Return value

None ({{jsxref("undefined")}}).

## Examples

```js
const transformFeedback = gl.createTransformFeedback();
gl.bindTransformFeedback(gl.TRANSFORM_FEEDBACK, transformFeedback);
gl.beginTransformFeedback(gl.TRIANGLES);
gl.pauseTransformFeedback();
// …
gl.resumeTransformFeedback();
gl.drawArrays(gl.TRIANGLES, 0, 3);
gl.endTransformFeedback();
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("WebGLTransformFeedback")}}
