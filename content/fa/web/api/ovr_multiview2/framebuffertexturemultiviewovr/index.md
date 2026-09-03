---
title: "OVR_multiview2: framebufferTextureMultiviewOVR() method"
short-title: framebufferTextureMultiviewOVR()
slug: Web/API/OVR_multiview2/framebufferTextureMultiviewOVR
page-type: webgl-extension-method
browser-compat: api.OVR_multiview2.framebufferTextureMultiviewOVR
---

{{APIRef("WebGL")}}

**`OVR_multiview2.framebufferTextureMultiviewOVR()`** 方法属于
[WebGL API](/en-US/docs/Web/API/WebGL_API)،用于将一个多视图（multiview）纹理附加到
{{domxref("WebGLFramebuffer")}} 上。

## 语法

```js-nolint
framebufferTextureMultiviewOVR(target, attachment, texture, level, baseViewIndex, numViews)
```

### 参数

- `target`
  - : 一个 {{domxref("WebGL_API.Types", "GLenum")}}，指定绑定点（目标）。可选值：
    - `gl.FRAMEBUFFER`
      - : 收集用于渲染图像的颜色、Alpha、深度和模板缓冲区的缓冲数据存储。
    - `gl.DRAW_FRAMEBUFFER`
      - : 等同于 `gl.FRAMEBUFFER`，用作绘制、渲染、清除和写入操作的目标。
    - `gl.READ_FRAMEBUFFER`
      - : 用作读取操作的源。

- `attachment`
  - : 一个 {{domxref("WebGL_API.Types", "GLenum")}}，指定 `texture` 的附加点。可选值：
    - `gl.COLOR_ATTACHMENT0`：将纹理附加到帧缓冲区的颜色缓冲区。
    - `gl.DEPTH_ATTACHMENT`：将纹理附加到帧缓冲区的深度缓冲区。
    - `gl.STENCIL_ATTACHMENT`：将纹理附加到帧缓冲区的模板缓冲区。
    - `gl.DEPTH_STENCIL_ATTACHMENT`：深度和模板缓冲区。
    - `gl.COLOR_ATTACHMENT1 gl.COLOR_ATTACHMENT2 gl.COLOR_ATTACHMENT3 gl.COLOR_ATTACHMENT4 gl.COLOR_ATTACHMENT5 gl.COLOR_ATTACHMENT6 gl.COLOR_ATTACHMENT7 gl.COLOR_ATTACHMENT8 gl.COLOR_ATTACHMENT9 gl.COLOR_ATTACHMENT10 gl.COLOR_ATTACHMENT11 gl.COLOR_ATTACHMENT12 gl.COLOR_ATTACHMENT13 gl.COLOR_ATTACHMENT14 gl.COLOR_ATTACHMENT15`
      使用 {{domxref("WEBGL_draw_buffers")}} 扩展时：
      - `ext.COLOR_ATTACHMENT0_WEBGL`（等同于 `gl.COLOR_ATTACHMENT0`）
        `ext.COLOR_ATTACHMENT1_WEBGL ext.COLOR_ATTACHMENT2_WEBGL ext.COLOR_ATTACHMENT3_WEBGL ext.COLOR_ATTACHMENT4_WEBGL ext.COLOR_ATTACHMENT5_WEBGL ext.COLOR_ATTACHMENT6_WEBGL ext.COLOR_ATTACHMENT7_WEBGL ext.COLOR_ATTACHMENT8_WEBGL ext.COLOR_ATTACHMENT9_WEBGL ext.COLOR_ATTACHMENT10_WEBGL ext.COLOR_ATTACHMENT11_WEBGL ext.COLOR_ATTACHMENT12_WEBGL ext.COLOR_ATTACHMENT13_WEBGL ext.COLOR_ATTACHMENT14_WEBGL ext.COLOR_ATTACHMENT15_WEBGL`

    使用 {{domxref("WEBGL_depth_texture")}} 扩展时：
    - `ext.DEPTH_STENCIL_ATTACHMENT`：深度和模板缓冲区数据存储。

- `texture`
  - : 一个 {{domxref("WebGLTexture")}} 对象，其图像将被附加。
- `level`
  - : 一个 {{domxref("WebGL_API.Types", "GLint")}}，指定要附加的纹理图像的 mipmap 级别。必须为 0。
- `baseViewIndex`
  - : 一个 {{domxref("WebGL_API.Types", "GLint")}}，指定帧缓冲区对象附加的基础视图索引。
- `numViews`
  - : 一个 {{domxref("WebGL_API.Types", "GLsizei")}}，指定帧缓冲区对象附加的视图数量。

### 返回值

无（{{jsxref("undefined")}}）。

### 异常

- 如果出现以下情况，会抛出 `gl.INVALID_ENUM` 错误：
  - `target` 不是 `gl.FRAMEBUFFER`。
  - `attachment` 不是可接受的附加点之一。

- 如果出现以下情况，会抛出 `gl.INVALID_VALUE` 错误：
  - `level` 不是 0。
  - `numViews` 小于 1 或大于 `MAX_VIEWS_OVR`。

- 如果 `texture` 不是 0 或现有纹理对象的名称，会抛出 `gl.INVALID_OPERATION` 错误。

## 示例

```js
ext.framebufferTextureMultiviewOVR(
  gl.DRAW_FRAMEBUFFER,
  gl.COLOR_ATTACHMENT0,
  colorTex,
  0,
  0,
  2,
);
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- {{domxref("OVR_multiview2")}}
- {{domxref("WEBGL_depth_texture")}}
- {{domxref("WEBGL_draw_buffers")}}