---
title: "HTMLOptionElement: label property"
---

---
title: "HTMLOptionElement: label property"
short-title: label
slug: Web/API/HTMLOptionElement/label
page-type: web-api-instance-property
browser-compat: api.HTMLOptionElement.label
---

{{ApiRef("HTML DOM")}}

**`label`** 属性属于 {{domxref("HTMLOptionElement")}}，表示 {{htmlelement("select")}} 元素中某个选项所显示的文本，或 {{htmlelement("datalist")}} 元素建议列表中的某个选项所显示的文本。它对应 {{htmlelement("option")}} 元素的 [`label`](/en-US/docs/Web/HTML/Reference/Elements/option#label) 属性。

如果该属性被省略或为空字符串，`label` 属性会返回该元素的 {{domxref("HTMLOptionElement.text", "text")}} 内容。

## 值

一个字符串。

## 示例

```js
const optionElement = document.getElementById("exampleOption");
console.log(`Option's label: ${optionElement.label}`);
optionElement.label = "Updated label";
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- {{domxref("HTMLOptionElement.value")}}
- {{HTMLElement("select")}}
- {{HTMLElement("datalist")}}
- {{HTMLElement("optgroup")}}