---
title: CharacterBoundsUpdateEvent
slug: Web/API/CharacterBoundsUpdateEvent
page-type: web-api-interface
status:
  - experimental
browser-compat: api.CharacterBoundsUpdateEvent
---

{{APIRef("EditContext API")}}{{SeeCompatTable}}

**`CharacterBoundsUpdateEvent`** 是一个 [DOM 事件](/en-US/docs/Web/API/Event)，表示操作系统发出的请求，目的是获取已附加到 {{domxref("EditContext")}} 实例的可编辑区域中某些字符的边界。

此接口继承自 {{domxref("Event")}} 的属性。

{{InheritanceDiagram}}

## 构造函数

- {{domxref("CharacterBoundsUpdateEvent.CharacterBoundsUpdateEvent", "CharacterBoundsUpdateEvent()")}} {{experimental_inline}}
  - : 创建一个新的 `CharacterBoundsUpdateEvent` 对象。

## 实例属性

- {{domxref('CharacterBoundsUpdateEvent.rangeStart')}} {{readonlyinline}} {{experimental_inline}}
  - : 操作系统需要其边界的可编辑区域文本中第一个字符的偏移量。
- {{domxref('CharacterBoundsUpdateEvent.rangeEnd')}} {{readonlyinline}} {{experimental_inline}}
  - : 操作系统需要其边界的可编辑区域文本中最后一个字符的偏移量。

## 示例

### 在需要时更新字符边界

此示例展示了如何使用 `characterboundsupdate` 事件和 `updateCharacterBounds` 方法，将操作系统所需的字符边界告知操作系统。注意，事件监听器的回调仅在通过 IME 窗口或其他平台特定的编辑界面来组合文本时才会被调用。

```html
<canvas id="editor-canvas"></canvas>
```

```js
const FONT_SIZE = 40;
const FONT = `${FONT_SIZE}px Arial`;

const canvas = document.getElementById("editor-canvas");
const ctx = canvas.getContext("2d");
ctx.font = FONT;

const editContext = new EditContext();
canvas.editContext = editContext;

function computeCharacterBound(offset) {
  // Measure the width from the start of the text to the character.
  const widthBeforeChar = ctx.measureText(
    editContext.text.substring(0, offset),
  ).width;

  // Measure the character width.
  const charWidth = ctx.measureText(editContext.text[offset]).width;

  const charX = canvas.offsetLeft + widthBeforeChar;
  const charY = canvas.offsetTop;

  // Return a DOMRect representing the character bounds.
  return DOMRect.fromRect({
    x: charX,
    y: charY - FONT_SIZE,
    width: charWidth,
    height: FONT_SIZE,
  });
}

editContext.addEventListener("characterboundsupdate", (e) => {
  const charBounds = [];
  for (let offset = e.rangeStart; offset < e.rangeEnd; offset++) {
    charBounds.push(computeCharacterBound(offset));
  }

  // Update the character bounds in the EditContext instance.
  editContext.updateCharacterBounds(e.rangeStart, charBounds);

  console.log(
    "The required character bounds are",
    charBounds
      .map(
        (bound) =>
          `(x: ${bound.x}, y: ${bound.y}, width: ${bound.width}, height: ${bound.height})`,
      )
      .join(", "),
  );
});
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}