---
title: "Cache: matchAll() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Cache/matchAll"
translated_by: "n8n + AI"
---

---
title: "Cache: matchAll() method"
short-title: matchAll()
slug: Web/API/Cache/matchAll
page-type: web-api-instance-method
browser-compat: api.Cache.matchAll
---

{{APIRef("Service Workers API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

{{domxref("Cache")}} 接口的 **`matchAll()`** 方法返回一个 {{jsxref("Promise")}}，该 Promise 解析为 {{domxref("Cache")}} 对象中所有匹配响应的数组。

## 语法

```js-nolint
matchAll()
matchAll(request)
matchAll(request, options)
```

### 参数

- `request` {{optional_inline}}
  - : 您尝试在 {{domxref("Cache")}} 中查找响应的 {{domxref("Request")}}。这可以是一个 `Request` 对象或一个 URL。如果省略此参数，您将获得此缓存中所有响应的副本。
- `options` {{optional_inline}}
  - : 一个选项对象，允许您为执行的匹配设置特定的控制选项。可用选项包括：
    - `ignoreSearch`
      - : 一个布尔值，指定匹配过程是否应忽略 URL 中的查询字符串。如果设置为 `true`，则执行匹配时将忽略 `https://example.com/?value=bar` 中的 `?value=bar` 部分。默认值为 `false`。
    - `ignoreMethod`
      - : 一个布尔值，当设置为 `true` 时，阻止匹配操作验证 {{domxref("Request")}} 的 `http` 方法（通常只允许 `GET` 和 `HEAD`）。默认值为 `false`。
    - `ignoreVary`
      - : 一个布尔值，当设置为 `true` 时，告诉匹配操作不执行 `VARY` 标头匹配 —— 即，如果 URL 匹配，无论 {{domxref("Response")}} 对象是否具有 `VARY` 标头，您都会获得匹配。默认值为 `false`。

### 返回值

一个 {{jsxref("Promise")}}，解析为 {{domxref("Cache")}} 对象中所有匹配响应的数组。

> [!NOTE]
> {{domxref("Cache.match()")}} 与 `Cache.matchAll()` 基本相同，区别在于它不是解析为所有匹配响应的数组，而是仅解析为第一个匹配响应（即 `response[0]`）。

## 示例

以下示例检索 `v1` 缓存中与 URL `/` 匹配的所有响应，甚至包括潜在的查询参数。通过使用 `{ ignoreSearch: true }`，使用 `matchAll` 将检索到 `/` 以及 `/?value=bar`。

然后记录匹配响应的数量。

```js
caches
  .open("v1")
  .then((cache) => cache.matchAll("/", { ignoreSearch: true }))
  .then((responses) => {
    console.log(`Found ${responses.length} matching responses`);
  });
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 另请参阅

- [使用 Service Workers](/en-US/docs/Web/API/Service_Worker_API/Using_Service_Workers)
- {{domxref("Cache")}}
- {{domxref("Window.caches")}} 和 {{domxref("WorkerGlobalScope.caches")}}