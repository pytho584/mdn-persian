---
title: "Document: startViewTransition() method"
short-title: startViewTransition()
slug: Web/API/Document/startViewTransition
page-type: web-api-instance-method
browser-compat: api.Document.startViewTransition
---

{{APIRef("View Transition API")}}

**`startViewTransition()`** 方法属于 {{domxref("Document")}} 接口，用于启动一个新的同文档（{{glossary("SPA")}}）且作用域为文档的[视图转换](/en-US/docs/Web/API/View_Transition_API)，并返回一个表示该转换的 {{domxref("ViewTransition")}} 对象。

调用 `startViewTransition()` 后所执行的步骤序列，在[视图转换过程](/en-US/docs/Web/API/View_Transition_API/Using#the_view_transition_process)一节中有详细说明。

## 语法

```js-nolint
startViewTransition()
startViewTransition(updateCallback)
startViewTransition(options)
```

### 参数

- `updateCallback` {{optional_inline}}
  - 一个在 SPA 视图转换过程中用于更新 DOM 的回调函数。它返回一个 {{jsxref("Promise")}}。当 API 已对当前页面拍摄快照后，该回调会被调用。当此回调返回的 Promise 兑现时，视图转换将在下一帧开始。如果该 Promise 被拒绝，则转换被放弃。
- `options` {{optional_inline}}
  - 一个包含配置视图转换选项的对象。它可以包含以下属性：
    - `update` {{optional_inline}}
      - 即上面描述的 `updateCallback` 函数。默认为 `null`。
    - `types` {{optional_inline}}
      - 一个字符串数组，表示应用于视图转换的类型。[视图转换类型](/en-US/docs/Web/API/View_Transition_API/Using_types)使得可以根据正在发生的转换类型，有选择地应用 CSS 样式或 JavaScript 逻辑。默认为空数组。

### 返回值

一个 {{domxref("ViewTransition")}} 对象实例。

## 示例

请参阅[视图转换 API > 示例](/en-US/docs/Web/API/View_Transition_API#examples)以获取完整示例列表。

### 基本用法

在这个同文档视图转换中，我们首先检查浏览器是否支持视图转换。如果不支持，我们使用一种立即生效的回退方法来设置背景颜色。否则，我们可以安全地调用 `document.startViewTransition()`，并结合我们在 CSS 中定义的动画规则。

```html
<main>
  <section></section>
  <button id="change-color">Change color</button>
</main>
```

我们使用 {{CSSXRef("::view-transition-group")}} 伪元素将 `animation-duration` 设置为 2 秒。

```css
html {
  --bg: indigo;
}
main {
  display: flex;
  flex-direction: column;
  gap: 5px;
}
section {
  background-color: var(--bg);
  height: 60px;
  border-radius: 5px;
}
::view-transition-group(root) {
  animation-duration: 2s;
}
```

```js
const colors = ["darkred", "darkslateblue", "darkgreen"];
const colBlock = document.querySelector("section");
let count = 0;
const updateColor = () => {
  colBlock.style = `--bg: ${colors[count]}`;
  count = count !== colors.length - 1 ? ++count : 0;
};
const changeColor = () => {
  // Fallback for browsers that don't support View Transitions:
  if (!document.startViewTransition) {
    updateColor();
    return;
  }

  // With View Transitions:
  const transition = document.startViewTransition(() => {
    updateColor();
  });
};
const changeColorButton = document.querySelector("#change-color");
changeColorButton.addEventListener("click", changeColor);
changeColorButton.addEventListener("keypress", changeColor);
```

如果浏览器支持视图转换，点击按钮后，颜色将在 2 秒内从一种过渡到另一种。否则，背景颜色将使用回退方法立即设置，没有任何动画。

{{EmbedLiveSample('color_change', '100%', '120')}}

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- {{domxref("Document.activeViewTransition")}}
- {{domxref("Element.startViewTransition()")}}
- {{CSSXRef(":active-view-transition")}} 伪类
- {{cssxref(":active-view-transition-type", ":active-view-transition-type()")}} 伪类
- [视图转换 API](/en-US/docs/Web/API/View_Transition_API)
- [使用视图转换 API](/en-US/docs/Web/API/View_Transition_API/Using)
- [使用视图转换类型](/en-US/docs/Web/API/View_Transition_API/Using_types)
- [使用视图转换 API 实现平滑过渡](https://developer.chrome.com/docs/web-platform/view-transitions/)