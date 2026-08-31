---
title: "ContactAddress: dependentLocality property"
---

---
title: "ContactAddress: dependentLocality property"
short-title: dependentLocality
slug: Web/API/ContactAddress/dependentLocality
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.ContactAddress.dependentLocality
---

{{securecontext_header}}{{APIRef("Contact Picker API")}}{{SeeCompatTable}}

{{domxref("ContactAddress")}} 接口的只读属性 **`dependentLocality`** 是一个字符串，包含城市内的地区或子地区标识，例如街区、自治市、区，或英国所称的依赖地区（dependent locality）。也被称为 _邮镇_（post town）。

## 值

一个字符串，表示地址的子地区部分。如果没有或不要求子地区，则此值可能为空字符串。当城市中可能出现街道重名的区域时，该属性用于提供消歧。

子地区是城市内的一个区域，例如街区、自治市或区。在英国，该属性用于表示英国的 **邮镇**（post town）（皇家邮政官方称之为 **依赖地区**）。在城市可能存在街道重名区域的情况下，这是地址的一个消歧特性。

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}