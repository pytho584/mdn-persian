---
title: "LanguageModel: clone() method"
short-title: clone()
slug: Web/API/LanguageModel/clone
page-type: web-api-instance-method
browser-compat: api.LanguageModel.clone
---

{{APIRef("Prompt API")}}{{SecureContext_Header}}

{{domxref("LanguageModel")}} 接口的 **`clone()`** 方法会创建调用它的 `LanguageModel` 的一个副本，包括其完整的上下文窗口状态。克隆出的会话可以独立使用，而不会影响原会话。

原会话与克隆副本在克隆之前共享相同的上下文历史，使您无需从头开始就能探索多条响应路径或测试不同变体。

例如，您可以使用 {{domxref("LanguageModel.append()", "append()")}} 或早期的 {{domxref("LanguageModel.prompt()", "prompt()")}} `prompt()` 调用来构建共享上下文，克隆会话，然后并行地向每个克隆发送不同的后续提示。

## 语法

```js-nolint
clone()
clone(options)
```

### 参数

- `options` {{optional_inline}}
  - : 一个表示可传入选项的对象。如果省略此参数，则使用原会话的 `options`，例如其中止信号。
    属性包括：
    - `signal`
      - : 一个用于取消克隆操作的 {{domxref("AbortSignal")}}。

### 返回值

一个 {{jsxref("Promise")}}，解析为克隆的 {{domxref("LanguageModel")}} 实例。

### 异常

- `AbortError` {{domxref("DOMException")}}
  - : 如果操作通过 `signal` 选项被取消，则抛出。
- `NotAllowedError` {{domxref("DOMException")}}
  - : 如果方法的使用被 {{httpheader("Permissions-Policy/language-model", "language-model")}} {{httpheader("Permissions-Policy")}} 阻止，则抛出。
- `OperationError` {{domxref("DOMException")}}
  - : 如果由于未列在其他异常类型中的任何其他原因导致克隆失败，则抛出。

## 示例

另请参阅 [使用 Prompt API > 克隆会话](/en-US/docs/Web/API/Prompt_API/Using#cloning_a_session)。

### 探索多条响应路径

以下示例展示了如何探索不同的响应路径。首先，它创建一个含有故事开头的单个会话。然后，在提示不同的结局之前，将原始会话克隆两次。这种方法保留了原始会话，以防需要进一步探索。

```js
const session = await LanguageModel.create({
  initialPrompts: [
    { role: "system", content: "You are a creative writing assistant." },
  ],
});

await session.append(
  "The story begins in a small coastal town during a storm.",
);

const [clone1, clone2] = await Promise.all([session.clone(), session.clone()]);

const [ending1, ending2] = await Promise.all([
  clone1.prompt("Write a happy ending."),
  clone2.prompt("Write a mysterious ending."),
]);

console.log("Happy ending:", ending1);
console.log("Mysterious ending:", ending2);
```

### 在上下文溢出后克隆以重试

此示例使用检查点与回滚模式，在尝试追加大量数据之前保存会话状态。在调用 `append()` 之前克隆会话，使应用能够在超出上下文窗口时恢复状态。

```js
const veryLargeDocument = "This is my very long story...";
let session = await LanguageModel.create();
const checkpoint = await session.clone();

try {
  await session.append(veryLargeDocument);
} catch (err) {
  if (err.name === "QuotaExceededError") {
    console.warn("Document too large.");
    session = checkpoint;
  }
}
```

### 使用中止信号克隆会话

以下示例创建了一个超时，如果克隆操作耗时超过三秒，则中止该操作。

```js
const controller = new AbortController();
setTimeout(() => controller.abort(), 3000);

try {
  const clonedSession = await session.clone({
    signal: controller.signal,
  });
  console.log("Session cloned successfully.");
} catch (err) {
  if (err.name === "AbortError") {
    console.log("Clone operation was aborted.");
  }
}
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 另请参阅

- {{domxref("LanguageModel.append()")}}
- [Prompt API](/en-US/docs/Web/API/Prompt_API)
- [Using the Prompt API](/en-US/docs/Web/API/Prompt_API/Using)
- [Adding context with initial and ongoing prompt inputs](/en-US/docs/Web/API/Prompt_API/Adding_context)