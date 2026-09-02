---
title: "NavigateEvent: formData property"
short-title: formData
slug: Web/API/NavigateEvent/formData
page-type: web-api-instance-property
browser-compat: api.NavigateEvent.formData
---

{{APIRef("Navigation API")}}

**`formData`** 是 {{domxref("NavigateEvent")}} 接口的一个只读属性，在 [`POST`](/en-US/docs/Web/HTTP/Reference/Methods/POST) 表单提交的情况下，返回一个表示所提交数据的 {{domxref("FormData")}} 对象；否则返回 `null`。

## 值

一个 {{domxref("FormData")}} 对象，或 `null`。

## 示例

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
    handler() {
      if (event.formData) {
        processFormDataAndUpdateUI(event.formData, event.signal);
      } else {
        doSinglePageAppNav(event.destination, event.signal);
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