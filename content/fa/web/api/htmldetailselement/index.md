---
title: "HTMLDetailsElement"
---

---
title: HTMLDetailsElement
slug: Web/API/HTMLDetailsElement
page-type: web-api-interface
browser-compat:
  - api.HTMLDetailsElement
  - api.HTMLElement.toggle_event.details_elements
---

{{APIRef("HTML DOM")}}

**`HTMLDetailsElement`** 接口提供了用于操作 {{HTMLElement("details")}} 元素的专用属性（除了通过继承自常规 {{domxref("HTMLElement")}} 接口可用的属性之外）。

{{InheritanceDiagram}}

## 实例属性

_继承其父接口 {{domxref("HTMLElement")}} 的属性。_

- {{domxref("HTMLDetailsElement.name")}}
  - : 一个字符串，对应 [`name`](/en-US/docs/Web/HTML/Reference/Elements/details#name) HTML 属性，该属性允许你创建一组互斥的 {{htmlelement("details")}} 元素。打开该组中某个具名的 `<details>` 元素会导致组内其他元素关闭。
- {{domxref("HTMLDetailsElement.open")}}
  - : 一个布尔值，对应 [`open`](/en-US/docs/Web/HTML/Reference/Elements/details#open) HTML 属性，表示元素的内容（不包括 {{HTMLElement("summary")}}）是否应向用户显示。

## 实例方法

_没有特定方法；继承其父接口 {{domxref("HTMLElement")}} 的方法。_

## 事件

_继承其父接口 {{DOMxRef("HTMLElement")}} 的事件。_

## 示例

### 记录章节的打开与关闭

本示例使用 `HTMLElement` 的 {{domxref("HTMLElement/toggle_event", "toggle")}} 事件，在章节打开和关闭时，将章节信息添加到一个日志侧栏中或从中移除。

#### HTML

```html
<section id="summaries">
  <p>章节摘要：</p>
  <details id="ch1">
    <summary>第一章</summary>
    哲学斥责波爱修斯对自己抱怨命运之神的愚蠢行为。命运的本质就是反复无常。
  </details>
  <details id="ch2">
    <summary>第二章</summary>
    哲学以命运之神的名义回应波爱修斯的指责，并证明命运之神的礼物由她决定给予和收回。
  </details>
  <details id="ch3">
    <summary>第三章</summary>
    波爱修斯重新陷入当前的痛苦之中。哲学提醒他昔日命运的辉煌。
  </details>
</section>
<aside id="log">
  <p>已打开的章节：</p>
  <div data-id="ch1" hidden>I</div>
  <div data-id="ch2" hidden>II</div>
  <div data-id="ch3" hidden>III</div>
</aside>
```

#### CSS

```css
body {
  display: flex;
}

#log {
  flex-shrink: 0;
  padding-left: 3em;
}

#summaries {
  flex-grow: 1;
}
```

#### JavaScript

```js
function logItem(e) {
  console.log(e);
  const item = document.querySelector(`[data-id=${e.target.id}]`);
  item.toggleAttribute("hidden");
}

const chapters = document.querySelectorAll("details");
chapters.forEach((chapter) => {
  chapter.addEventListener("toggle", logItem);
});
```

#### 结果

{{EmbedLiveSample("Log chapters as they are opened and closed", 700, 200)}}

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- 实现此接口的 HTML 元素：{{HTMLElement("details")}}