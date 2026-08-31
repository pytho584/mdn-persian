---
title: "BackgroundFetchManager"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BackgroundFetchManager"
translated_by: "n8n + AI"
---

---
title: BackgroundFetchManager
slug: Web/API/BackgroundFetchManager
page-type: web-api-interface
status:
  - experimental
browser-compat: api.BackgroundFetchManager
---

{{APIRef("Background Fetch API")}}{{SeeCompatTable}}{{AvailableInWorkers}}

**`BackgroundFetchManager`** 接口属于 {{domxref('Background Fetch API','','',' ')}}，它是一个映射表，键是后台获取的 ID，值是对应的 {{domxref("BackgroundFetchRegistration")}} 对象。

## 实例属性

无。

## 实例方法

- {{domxref('BackgroundFetchManager.fetch','fetch()' )}} {{Experimental_Inline}}
  - 返回一个 {{jsxref("Promise")}}，会解析为一个 {{domxref("BackgroundFetchRegistration")}} 对象，对应给定的 URL 数组和 {{domxref("Request")}} 对象。
- {{domxref('BackgroundFetchManager.get','get()')}} {{Experimental_Inline}}
  - 返回一个 {{jsxref("Promise")}}，会解析为与所提供的 `id` 关联的 {{domxref("BackgroundFetchRegistration")}}；如果未找到该 `id`，则解析为 {{jsxref("undefined")}}。
- {{domxref('BackgroundFetchManager.getIds','getIds()')}} {{Experimental_Inline}}
  - 返回所有已注册的后台获取的 ID。

## 示例

下面的示例展示了如何从 {{domxref("ServiceWorkerRegistration")}} 对象获取 `BackgroundFetchManager` 实例，并调用 `fetch()` 在后台下载一个音频文件。

```js
navigator.serviceWorker.ready.then(async (swReg) => {
  const bgFetch = await swReg.backgroundFetch.fetch(
    "my-fetch",
    ["/ep-5.mp3", "ep-5-artwork.jpg"],
    {
      title: "Episode 5: Interesting things.",
      icons: [
        {
          sizes: "300x300",
          src: "/ep-5-icon.png",
          type: "image/png",
        },
      ],
      downloadTotal: 60 * 1024 * 1024,
    },
  );
});
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}