---
title: "CustomEvent"
---

---
title: CustomEvent
slug: Web/API/CustomEvent
page-type: web-api-interface
browser-compat: api.CustomEvent
---

{{APIRef("DOM")}}{{AvailableInWorkers}}

接口 **`CustomEvent`** 可用于将自定义数据附加到应用程序生成的事件上。

作为 `CustomEvent` 的替代方案，你可以[对 `Event` 接口进行子类化](/en-US/docs/Web/API/Document_Object_Model/Events#adding_custom_data_–_subclassing_event)来添加自定义数据和行为。

> [!NOTE]
> 如果尝试在 Web 扩展的内容脚本与网页脚本之间通信，在 Firefox 中，非字符串的 `detail` 属性会抛出“Permission denied to access property”（拒绝访问属性）错误。为避免此问题，请克隆该对象。有关更多信息，请参阅[与页面脚本共享对象](/en-US/docs/Mozilla/Add-ons/WebExtensions/Sharing_objects_with_page_scripts)。

{{InheritanceDiagram}}

## 构造函数

- {{domxref("CustomEvent.CustomEvent", "CustomEvent()")}}
  - : 创建一个新的 `CustomEvent`。

## 实例属性

_此接口继承其父接口 {{domxref("Event")}} 的属性。_

- {{domxref("CustomEvent.detail")}} {{ReadOnlyInline}}
  - : 返回初始化事件时传入的任何数据。

## 实例方法

_此接口继承其父接口 {{domxref("Event")}} 的方法。_

- {{domxref("CustomEvent.initCustomEvent()")}} {{deprecated_inline}}
  - : 初始化一个 `CustomEvent` 对象。如果事件已被派发，则此方法不执行任何操作。

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- {{domxref("Window.postMessage()")}}
- [创建和派发事件](/en-US/docs/Web/API/Document_Object_Model/Events#creating_and_dispatching_events)