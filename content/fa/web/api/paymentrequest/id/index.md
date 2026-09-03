---
title: "PaymentRequest: id property"
short-title: id
slug: Web/API/PaymentRequest/id
page-type: web-api-instance-property
browser-compat: api.PaymentRequest.id
---

{{securecontext_header}}{{APIRef("Payment Request API")}}

{{domxref("PaymentRequest")}} 接口的 **`id`** 只读属性返回一个唯一标识符，用于标识特定的 {{domxref("PaymentRequest")}} 实例。

在构造 {{domxref("PaymentRequest")}} 实例时，你可以提供自定义的 `id`。如果没有提供，浏览器会自动将 `id` 设置为一个 UUID。

## 示例

此示例演示如何为 {{domxref("PaymentRequest")}} 实例设置自定义 id。

```js
const details = {
  id: "super-store-order-123-12312",
  total: {
    label: "Total due",
    amount: { currency: "USD", value: "65.00" },
  },
};
const request = new PaymentRequest(methodData, details);
console.log(request.id); // super-store-order-123-12312
```

`id` 同样可在从 `show()` 方法返回的 {{domxref("PaymentResponse")}} 中获得，但属性名是 `requestId`。

```js
const response = await request.show();
console.log(response.requestId === request.id);

// And in serialized form too
const json = response.toJSON();
console.log(json.requestId, response.requestId, request.id);
```

## 值

一个字符串。

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}