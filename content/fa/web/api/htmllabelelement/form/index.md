---
title: "HTMLLabelElement: form property"
short-title: form
slug: Web/API/HTMLLabelElement/form
page-type: web-api-instance-property
browser-compat: api.HTMLLabelElement.form
---

{{APIRef("HTML DOM")}}

ویژگی فقط‌خواندنی **`form`** در رابط {{domxref("HTMLLabelElement")}}، یک شیء {{domxref("HTMLFormElement")}} برمی‌گرداند که مالک {{domxref("HTMLLabelElement.control", "کنترل")}} مرتبط با این {{HTMLElement("label")}} است، یا اگر این برچسب با هیچ عنصر [قابل برچسب‌گذاری](/en-US/docs/Web/HTML/Guides/Content_categories#labelable) [مرتبط با فرم](/en-US/docs/Web/HTML/Guides/Content_categories#form-associated_content) (شامل {{htmlelement("button")}}، {{htmlelement("input")}}، {{htmlelement("output")}}، {{htmlelement("select")}}، {{htmlelement("textarea")}} یا [عناصر سفارشی مرتبط با فرم](https://html.spec.whatwg.org/multipage/custom-elements.html#form-associated-custom-element)) که متعلق به یک فرم است، مرتبط نباشد، مقدار `null` را برمی‌گرداند.

برخلاف [عناصر مرتبط با فرم](/en-US/docs/Web/HTML/Guides/Content_categories#form-associated_content)، عنصر `<label>` ویژگی [`form`](/en-US/docs/Web/HTML/Reference/Attributes/form) ندارد. این ویژگی هیچ ویژگی HTML را بازتاب نمی‌دهد و صرفاً یک میان‌بر برای `label.control.form` است.

## مقدار

یک {{domxref("HTMLFormElement")}} یا `null`.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("HTMLLabelElement")}}
- {{domxref("HTMLInputElement.form")}}
- {{domxref("HTMLFormElement")}}
- {{HTMLElement("label")}}
- [راهنمای فرم‌های HTML](/en-US/docs/Learn_web_development/Extensions/Forms)