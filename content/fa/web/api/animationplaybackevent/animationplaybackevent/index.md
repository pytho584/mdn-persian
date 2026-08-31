---
title: "AnimationPlaybackEvent: AnimationPlaybackEvent() constructor"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AnimationPlaybackEvent/AnimationPlaybackEvent"
translated_by: "n8n + AI"
---

---
title: "AnimationPlaybackEvent: AnimationPlaybackEvent() constructor"
short-title: AnimationPlaybackEvent()
slug: Web/API/AnimationPlaybackEvent/AnimationPlaybackEvent
page-type: web-api-constructor
browser-compat: api.AnimationPlaybackEvent.AnimationPlaybackEvent
---

{{ APIRef("Web Animations") }}

**`AnimationPlaybackEvent()`** 构造函数，属于 [Web Animations API](/en-US/docs/Web/API/Web_Animations_API)，返回一个新的 {{domxref("AnimationPlaybackEvent")}} 对象实例。

## 语法

```js-nolint
new AnimationPlaybackEvent(type)
new AnimationPlaybackEvent(type, options)
```

### 参数

- `type`
  - : 一个字符串，表示事件的名称。它是区分大小写的，浏览器将其设置为 `cancel`、`finish` 或 `remove`。
- `options` {{optional_inline}}
  - : 一个对象，_除了 {{domxref("Event/Event", "Event()")}} 定义的属性之外_，还具有以下属性：
    - `detail` {{optional_inline}}
      - : 一个与事件关联的、依赖于事件的值。默认为 `null`。

### 返回值

一个新的 {{domxref("AnimationPlaybackEvent")}} 对象。

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- [Web Animations API](/en-US/docs/Web/API/Web_Animations_API)
- {{domxref("AnimationPlayBackEvent")}}
- {{domxref("Animation.playState")}}
- {{domxref("CustomEvent.CustomEvent", "CustomEvent()")}}
- {{domxref("Event.Event", "Event()")}}