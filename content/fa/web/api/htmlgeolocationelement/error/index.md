---
title: "HTMLGeolocationElement: error property"
short-title: error
slug: Web/API/HTMLGeolocationElement/error
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.HTMLGeolocationElement.error
---

{{APIRef("Navigation API")}}{{SeeCompatTable}}

{{domxref("HTMLGeolocationElement")}} 接口的只读属性 **`error`** 返回一个 {{domxref("GeolocationPositionError")}} 对象，用于在位置数据获取失败时表示错误信息。

如果位置数据获取成功，数据可通过 {{domxref("HTMLGeolocationElement.position")}} 属性获取。

## 值

一个 {{domxref("GeolocationPositionError")}} 对象；如果位置数据成功获取，则为 `null`。

## 示例

### 基本用法

```html
<geolocation autolocate></geolocation>
```

```js
const geo = document.querySelector("geolocation");
geo.addEventListener("location", () => {
  if (geo.position) {
    console.log(
      `(${geo.position.coords.latitude},${geo.position.coords.longitude})`,
    );
  } else if (geo.error) {
    console.log(geo.error.message);
  }
});
```

有关包含 `error` 的真实示例，请参阅我们的 [嵌入式地图示例演练](/en-US/docs/Web/API/HTMLGeolocationElement#embedded_map_example)。

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- {{htmlelement("geolocation")}} 元素