---
title: "NavigationDestination: getState() method"
---

---
title: "NavigationDestination: getState() method"
short-title: getState()
slug: Web/API/NavigationDestination/getState
page-type: web-api-instance-method
browser-compat: api.NavigationDestination.getState
---

{{APIRef("Navigation API")}}

**`getState()`** 方法属于 {{domxref("NavigationDestination")}} 接口，它返回与目标 {{domxref("NavigationHistoryEntry")}} 或导航操作（例如 {{domxref("Navigation.navigate()", "navigate()")}}）相关联的开发人员提供状态的克隆。

## 语法

```js-nolint
getState()
```

### 参数

无。

### 返回值

表示状态的值。可以是任何类型。如果没有定义状态，则返回 `undefined`。

### 异常

无。

## 示例

```js
navigation.addEventListener("navigate", (event) => {
  console.log(event.destination.getState());
});
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 另请参阅

- [Modern client-side routing: the Navigation API](https://developer.chrome.com/docs/web-platform/navigation-api/)
- [Navigation API explainer](https://github.com/WICG/navigation-api/blob/main/README.md)
- 允许更新状态的方法 — {{domxref("Navigation.navigate()")}}、{{domxref("Navigation.reload()")}} 和 {{domxref("Navigation.updateCurrentEntry()")}}