---
title: "Performance: mark() method"
short-title: mark()
slug: Web/API/Performance/mark
page-type: web-api-instance-method
browser-compat: api.Performance.mark
---

{{APIRef("Performance API")}}{{AvailableInWorkers}}

**`mark()`** 方法会创建一个具名的 {{domxref("PerformanceMark")}} 对象，用于在浏览器的性能时间线中表示一个高分辨率时间戳标记。

## 语法

```js-nolint
mark(name)
mark(name, markOptions)
```

### 参数

- `name`
  - : 一个表示标记名称的字符串。该名称不得与已废弃的 {{domxref("PerformanceTiming")}} 接口中的任何属性名相同。

- `markOptions` {{optional_inline}}
  - : 一个对象，用于指定标记的时间戳和附加元数据。
    - `detail` {{optional_inline}}
      - : 要包含在标记中的任意元数据。默认值为 `null`。该值必须是[结构化可克隆](/en-US/docs/Web/API/Web_Workers_API/Structured_clone_algorithm)的。
        - `devtools` {{optional_inline}} {{experimental_inline}}
          - : 某些浏览器会在 `detail` 对象中使用一个结构化的 `devtools` 对象，作为可扩展性 API 的一部分，在性能跟踪的自定义轨道中显示这些信息。有关更多信息，请参阅 [Chrome 的扩展性 API 文档](https://developer.chrome.com/docs/devtools/performance/extension#inject_your_data_with_the_user_timings_api)。
            - `dataType` {{experimental_inline}}
              - : 一个字符串，必须设置为 `marker`。用于标识为标记。
            - `color` {{optional_inline}} {{experimental_inline}}
              - : 默认值为 `"primary"`。必须是 `"primary"`、`"primary-light"`、`"primary-dark"`、`"secondary"`、`"secondary-light"`、`"secondary-dark"`、`"tertiary"`、`"tertiary-light"`、`"tertiary-dark"`、`"error"` 之一。
            - `properties` {{optional_inline}} {{experimental_inline}}
              - : 键值对数组。值可以是任何与 JSON 兼容的类型。
            - `tooltipText` {{optional_inline}} {{experimental_inline}}
              - : 用于工具提示的简短描述。

    - `startTime` {{optional_inline}}
      - : 用作标记时间的 {{domxref("DOMHighResTimeStamp")}}。默认值为 {{domxref("performance.now()")}}。

### 返回值

已创建的 {{domxref("PerformanceMark")}} 条目。

### 异常

- {{jsxref("SyntaxError")}}：如果 `name` 是已废弃的 {{domxref("PerformanceTiming")}} 接口的属性名之一，则抛出该异常。请参阅下面的[示例](#保留名称)。
- {{jsxref("TypeError")}}：如果 `startTime` 为负数，则抛出该异常。

## 示例

### 创建命名标记

以下示例使用 `mark()` 创建具名的 {{domxref("PerformanceMark")}} 条目。你可以使用相同的名称创建多个标记。你也可以将返回值赋给变量，以获得对已创建 {{domxref("PerformanceMark")}} 对象的引用。

```js
performance.mark("login-started");
performance.mark("login-started");
performance.mark("login-finished");
performance.mark("form-sent");

const videoMarker = performance.mark("video-loaded");
```

### 创建带详细信息的标记

性能标记可以通过 `markOptions` 对象进行配置，你可以在 `detail` 属性中放入附加信息，该属性的值可以是任意类型。

```js
performance.mark("login-started", {
  detail: "Login started using the login button in the top menu.",
});

performance.mark("login-started", {
  detail: { htmlElement: myElement.id },
});
```

### 使用不同的开始时间创建标记

`mark()` 方法的默认时间戳是 {{domxref("performance.now()")}}。你可以通过 `markOptions` 中的 `startTime` 选项将其设置为其他时间。

```js
performance.mark("start-checkout", {
  startTime: 20.0,
});

performance.mark("login-button-pressed", {
  startTime: myEvent.timeStamp,
});
```

### DevTools 扩展性 API

对于支持[扩展性 API](https://developer.chrome.com/docs/devtools/performance/extension) 的浏览器，你可以使用 `detail` 参数在 `devtools` 对象中提供更多详细信息，这些信息将用于在性能分析文件中显示：

```js
// Marker indicating when the processed image was uploaded
performance.mark("Image Upload", {
  detail: {
    devtools: {
      dataType: "marker",
      color: "secondary",
      properties: [
        ["Image Size", "2.5MB"],
        ["Upload Destination", "Cloud Storage"],
      ],
      tooltipText: "Processed image uploaded",
    },
  },
});
```

### 保留名称

请注意，为了保持向后兼容性，属于已废弃的 {{domxref("PerformanceTiming")}} 接口的名称不能使用。以下示例会抛出异常：

```js example-bad
performance.mark("navigationStart");
// SyntaxError: "navigationStart" is part of
// the PerformanceTiming interface,
// and cannot be used as a mark name
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}
```