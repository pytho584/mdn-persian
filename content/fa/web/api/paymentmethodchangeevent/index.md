---
title: PaymentMethodChangeEvent
slug: Web/API/PaymentMethodChangeEvent
page-type: web-api-interface
browser-compat: api.PaymentMethodChangeEvent
---

{{securecontext_header}}{{APIRef("Payment Request API")}}

**`PaymentMethodChangeEvent`** 接口属于 [Payment Request API](/en-US/docs/Web/API/Payment_Request_API)（支付请求 API），用于描述 {{domxref("PaymentRequest/paymentmethodchange_event", "paymentmethodchange")}} 事件。当用户在切换支付方式（例如，在使用 Apple Pay 时选择一张“商店”卡进行支付）时，某些支付处理程序会触发该事件。

{{InheritanceDiagram}}

## 构造函数

- {{domxref("PaymentMethodChangeEvent.PaymentMethodChangeEvent", "PaymentMethodChangeEvent()")}}
  - : 创建并返回一个新的 `PaymentMethodChangeEvent` 对象。

## 实例属性

_除了以下属性外，该接口还包含从 {{domxref("PaymentRequestUpdateEvent")}} 继承的属性。_

- {{domxref("PaymentMethodChangeEvent.methodDetails", "methodDetails")}} {{ReadOnlyInline}}
  - : 一个对象，包含与支付方式相关的数据，在处理支付方式变更时非常有用。如果没有此类信息，则此值为 `null`。
- {{domxref("PaymentMethodChangeEvent.methodName", "methodName")}} {{ReadOnlyInline}}
  - : 一个字符串，包含支付方式标识符，该字符串唯一标识特定的支付方式。此标识符通常是支付过程中使用的 URL，但也可能是标准化的非 URL 字符串，例如 `basic-card`。默认值为空字符串 `""`。

## 实例方法

_该接口包含从 {{domxref("PaymentRequestUpdateEvent")}} 继承的方法。_

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}