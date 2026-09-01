---
title: HighlightRegistry
slug: Web/API/HighlightRegistry
page-type: web-api-interface
browser-compat: api.HighlightRegistry
---

{{APIRef("CSS Custom Highlight API")}}

**`HighlightRegistry`** 接口属于 [CSS 自定义高亮 API](/en-US/docs/Web/API/CSS_Custom_Highlight_API)，用于注册要通过该 API 设置样式的 {{domxref("Highlight")}} 对象。可通过 {{domxref("CSS.highlights_static", "CSS.highlights")}} 访问它。

`HighlightRegistry` 实例是一个 [类 `Map` 对象](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map#map-like_browser_apis)，其中每个键是自定义高亮的名称字符串，对应的值是与该名称关联的 {{domxref("Highlight")}} 对象。

{{InheritanceDiagram}}

## 实例属性

_`HighlightRegistry` 接口不继承任何属性。_

- {{domxref("HighlightRegistry.size")}} {{ReadOnlyInline}}
  - : 返回当前注册的 `Highlight` 对象数量。

## 实例方法

_`HighlightRegistry` 接口不继承任何方法。_

- {{domxref("HighlightRegistry.clear()")}}
  - : 从注册表中移除所有 `Highlight` 对象。
- {{domxref("HighlightRegistry.delete()")}}
  - : 从注册表中移除指定名称的 `Highlight` 对象。
- {{domxref("HighlightRegistry.entries()")}}
  - : 返回一个新的迭代器对象，该对象按插入顺序包含注册表中的每个 `Highlight` 对象。
- {{domxref("HighlightRegistry.forEach()")}}
  - : 按插入顺序为注册表中的每个 `Highlight` 对象调用给定的回调函数。
- {{domxref("HighlightRegistry.get()")}}
  - : 从注册表中获取指定名称的 `Highlight` 对象。
- {{domxref("HighlightRegistry.has()")}}
  - : 返回一个布尔值，表示注册表中是否存在指定的 `Highlight` 对象。
- {{domxref("HighlightRegistry.highlightsFromPoint()")}}
  - : 返回一个对象数组，表示在视口内特定点应用的自定义高亮。
- {{domxref("HighlightRegistry.keys()")}}
  - : {{domxref("HighlightRegistry.values()")}} 的别名。
- {{domxref("HighlightRegistry.set()")}}
  - : 将给定的 `Highlight` 对象以指定名称添加到注册表中；如果该名称已存在，则更新对应的 `Highlight` 对象。
- {{domxref("HighlightRegistry.values()")}}
  - : 返回一个新的迭代器对象，该对象按插入顺序产生注册表中的 `Highlight` 对象。

## 示例

### 注册一个高亮

以下示例演示如何创建范围（range），为这些范围实例化一个新的 `Highlight` 对象，并使用 `HighlightRegistry` 注册该高亮，以便在页面上为其设置样式：

#### HTML

```html
<p id="foo">CSS Custom Highlight API</p>
```

#### CSS

```css
::highlight(my-custom-highlight) {
  background-color: peachpuff;
}
```

#### JavaScript

```js
const text = document.getElementById("foo").firstChild;

if (!CSS.highlights) {
  text.textContent =
    "The CSS Custom Highlight API is not supported in this browser!";
}

// 创建几个范围。
const range1 = new Range();
range1.setStart(text, 0);
range1.setEnd(text, 3);

const range2 = new Range();
range2.setStart(text, 21);
range2.setEnd(text, 24);

// 为这些范围创建一个自定义高亮。
const highlight = new Highlight(range1, range2);

// 在 HighlightRegistry 中注册这些范围。
CSS.highlights.set("my-custom-highlight", highlight);
```

#### 结果

{{ EmbedLiveSample("Registering a highlight") }}

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- {{domxref("css_custom_highlight_api", "CSS 自定义高亮 API", "", "nocode")}}
- [CSS 自定义高亮 API](/en-US/docs/Web/CSS/Guides/Custom_highlight_API) 模块
- [CSS 自定义高亮 API：网页文本范围高亮的未来](https://css-tricks.com/css-custom-highlight-api-early-look/)