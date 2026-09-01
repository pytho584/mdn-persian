---
title: "HMDVRDevice: getEyeParameters() method"
short-title: getEyeParameters()
slug: Web/API/HMDVRDevice/getEyeParameters
page-type: web-api-instance-method
status:
  - deprecated
  - non-standard
browser-compat: api.HMDVRDevice.getEyeParameters
---

{{deprecated_header}}{{APIRef("WebVR API")}}{{Non-standard_header}}

**`getEyeParameters()`** 方法属于 {{domxref("HMDVRDevice")}} 接口，用于返回以参数形式指定的眼睛（`"left"` 或 `"right"`）的当前参数——这些参数存储在一个 {{domxref("VREyeParameters")}} 对象中。

其中包含视场角信息等。

## 语法

```js-nolint
getEyeParameters(whichEye)
```

### 参数

- `whichEye`
  - : 一个字符串，表示您想要获取其信息的眼睛。该值可以是 `left` 或 `right`。

### 返回值

一个 {{domxref("VREyeParameters")}} 对象。

## 示例

以下示例取自 Mozilla VR 团队的 [threejs-vr-boilerplate](https://github.com/MozillaReality/vr-web-examples/tree/master/threejs-vr-boilerplate) 代码——更准确地说是其中的 [VREffect.js 文件](https://github.com/MozillaReality/vr-web-examples/blob/master/threejs-vr-boilerplate/js/VREffect.js)。在代码早期，使用 `getEyeParameters()` 方法来获取每只眼睛的信息，这些信息随后会用于渲染计算。

```js
if (vrHMD.getEyeParameters !== undefined) {
  const eyeParamsL = vrHMD.getEyeParameters("left");
  const eyeParamsR = vrHMD.getEyeParameters("right");

  eyeTranslationL = eyeParamsL.eyeTranslation;
  eyeTranslationR = eyeParamsR.eyeTranslation;
  eyeFOVL = eyeParamsL.recommendedFieldOfView;
  eyeFOVR = eyeParamsR.recommendedFieldOfView;
} else {
  // …
}
```

## 浏览器兼容性

{{Compat}}

## 参见

- [WebVR API](/en-US/docs/Web/API/WebVR_API)