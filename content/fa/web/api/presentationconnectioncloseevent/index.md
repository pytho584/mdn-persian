---
title: PresentationConnectionCloseEvent
source: "https://developer.mozilla.org/en-US/docs/Web/API/PresentationConnectionCloseEvent"
---

---
title: PresentationConnectionCloseEvent
slug: Web/API/PresentationConnectionCloseEvent
page-type: web-api-interface
status:
  - experimental
browser-compat: api.PresentationConnectionCloseEvent
---

{{SeeCompatTable}}{{securecontext_header}}{{APIRef("Presentation API")}}

**`PresentationConnectionCloseEvent`** 接口是 [Presentation API](/en-US/docs/Web/API/Presentation_API) 的一部分，当 {{domxref("PresentationConnection")}} 关闭时触发该事件。

{{InheritanceDiagram}}

## 构造函数

- {{domxref("PresentationConnectionCloseEvent.PresentationConnectionCloseEvent", "PresentationConnectionCloseEvent()")}} {{Experimental_Inline}}
  - : 创建一个新的 `PresentationConnectionCloseEvent` 实例。

## 实例属性

- {{DOMxRef("PresentationConnectionCloseEvent.message")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : 一个人类可读的消息，提供更多关于连接为何关闭的信息。
- {{DOMxRef("PresentationConnectionCloseEvent.reason")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : 指示连接关闭的原因。该属性取以下值之一：`error`、`closed` 或 `wentaway`。

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}