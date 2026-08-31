---
title: "BackgroundFetchEvent: BackgroundFetchEvent() constructor"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BackgroundFetchEvent/BackgroundFetchEvent"
translated_by: "n8n + AI"
---

---
title: "BackgroundFetchEvent: BackgroundFetchEvent() constructor"
short-title: BackgroundFetchEvent()
slug: Web/API/BackgroundFetchEvent/BackgroundFetchEvent
page-type: web-api-constructor
status:
  - experimental
browser-compat: api.BackgroundFetchEvent.BackgroundFetchEvent
---

{{APIRef("Background Fetch API")}}{{SeeCompatTable}}{{AvailableInWorkers("service")}}

**`BackgroundFetchEvent()`** 构造函数创建一个新的 {{domxref("BackgroundFetchEvent")}} 对象。此构造函数通常不被使用，因为浏览器会自行创建这些对象，并将其提供给后台获取事件回调。

## 语法

```js-nolint
new BackgroundFetchEvent(type, options)
```

### 参数

- `type`
  - : 一个字符串，表示事件的名称。它区分大小写，浏览器会将其设置为 `backgroundfetchabort` 或 `backgroundfetchclick`。
- `options`
  - : 一个对象，_除了 {{domxref("ExtendableEvent/ExtendableEvent", "ExtendableEvent()")}} 中定义的属性之外_，还具有以下属性：
    - `registration`
      - : 一个 {{domxref("BackgroundFetchRegistration")}} 对象。

### 返回值

一个新的 {{domxref("BackgroundFetchEvent")}} 对象。

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}