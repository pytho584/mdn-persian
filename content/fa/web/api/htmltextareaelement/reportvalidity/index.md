---
title: "HTMLTextAreaElement: reportValidity() method"
short-title: reportValidity()
slug: Web/API/HTMLTextAreaElement/reportValidity
page-type: web-api-instance-method
browser-compat: api.HTMLTextAreaElement.reportValidity
---

{{APIRef("HTML DOM")}}

**`reportValidity()`** 方法属于 {{domxref("HTMLTextAreaElement")}} 接口，执行与 {{domxref("HTMLTextAreaElement.checkValidity", "checkValidity()")}} 方法相同的有效性检查步骤。此外，如果 {{domxref("HTMLElement/invalid_event", "invalid")}} 事件未被取消，浏览器会向用户显示问题。

## 语法

```js-nolint
reportValidity()
```

### 参数

无。

### 返回值

如果元素的值没有任何有效性问题，则返回 `true`；否则返回 `false`。

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- {{domxref("HTMLTextAreaElement.checkValidity()")}}
- {{HTMLElement("textarea")}}
- {{HTMLElement("form")}}
- [学习：客户端表单验证](/en-US/docs/Learn_web_development/Extensions/Forms/Form_validation)
- [指南：约束验证](/en-US/docs/Web/HTML/Guides/Constraint_validation)
- CSS {{cssxref(":valid")}} 和 {{cssxref(":invalid")}} 伪类