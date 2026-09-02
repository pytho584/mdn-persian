---
title: "NavigateEvent: navigationType property"
short-title: navigationType
slug: Web/API/NavigateEvent/navigationType
page-type: web-api-instance-property
browser-compat: api.NavigateEvent.navigationType
---

{{APIRef("Navigation API")}}

**`navigationType`** 只读属性，属于 {{domxref("NavigateEvent")}} 接口，返回导航的类型 — `push`、`reload`、`replace` 或 `traverse`。

## 值

一个枚举值，表示导航的类型。

可能的值如下：

- `push`
  - : 导航到一个新位置，导致一个新条目被推入历史列表。
- `reload`
  - : 重新加载 {{domxref("Navigation.currentEntry")}}。
- `replace`
  - : {{domxref("Navigation.currentEntry")}} 被替换为新历史条目。这个新条目将复用相同的 {{domxref("NavigationHistoryEntry.key", "key")}}，但会被分配一个不同的 {{domxref("NavigationHistoryEntry.id", "id")}}。
- `traverse`
  - : 浏览器从一个现有历史条目导航到另一个现有历史条目。

## 示例

### 带特殊后退/前进处理的异步过渡

有时需要特殊处理后退/前进导航，例如通过将缓存的视图过渡到屏幕上来复用它们。可以通过如下分支逻辑实现：

```js
navigation.addEventListener("navigate", (event) => {
  // Some navigations, e.g. cross-origin navigations, we
  // cannot intercept. Let the browser handle those normally.
  if (!event.canIntercept) {
    return;
  }

  // Don't intercept fragment navigations or downloads.
  if (event.hashChange || event.downloadRequest !== null) {
    return;
  }

  event.intercept({
    async handler() {
      if (myFramework.currentPage) {
        await myFramework.currentPage.transitionOut();
      }

      let { key } = event.destination;

      if (
        event.navigationType === "traverse" &&
        myFramework.previousPages.has(key)
      ) {
        await myFramework.previousPages.get(key).transitionIn();
      } else {
        // This will probably result in myFramework storing
        // the rendered page in myFramework.previousPages.
        await myFramework.renderPage(event.destination);
      }
    },
  });
});
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- [Modern client-side routing: the Navigation API](https://developer.chrome.com/docs/web-platform/navigation-api/)
- [Navigation API explainer](https://github.com/WICG/navigation-api/blob/main/README.md)