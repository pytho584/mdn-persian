---
title: "ContactsManager: getProperties() method"
short-title: getProperties()
slug: Web/API/ContactsManager/getProperties
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.ContactsManager.getProperties
---

{{securecontext_header}}{{APIRef("Contact Picker API")}}{{SeeCompatTable}}

**`getProperties()`** 方法属于 {{domxref("ContactsManager")}} 接口，返回一个 {{jsxref('Promise')}}，该 Promise 解析为一个包含 {{jsxref('String','字符串')}} 的 {{jsxref('Array')}}，用于表示当前系统可用的联系人属性。

## 语法

```js-nolint
getProperties()
```

### 参数

无。

### 返回值

返回一个 {{jsxref('Promise')}}，解析为一个包含 {{jsxref('String','字符串')}} 的 {{jsxref('Array')}}，这些字符串表示当前系统可以返回的联系人属性。

属性可能包括以下值：

- `'name'`：联系人的姓名。
- `'tel'`：联系人的电话号码。
- `'email'`：联系人的电子邮件地址。
- `'address'`：联系人的邮寄地址。
- `'icon'`：联系人的头像。

### 异常

不会抛出异常。

## 示例

### 验证属性支持情况

以下异步函数使用 `getProperties()` 方法来检查当前系统是否支持 `icon` 属性。

```js
async function checkProperties() {
  const supportedProperties = await navigator.contacts.getProperties();
  if (!supportedProperties.includes("icon")) {
    console.log("Your system does not support getting icons.");
  }
}
```

### 仅使用受支持的属性进行选择

以下示例与 {{domxref("ContactsManager.select", "select()")}} 方法的示例类似。它没有硬编码传递给 `select()` 的属性，而是使用 `getProperties()` 来确保只传递受支持的属性。否则，`select()` 可能会抛出 {{jsxref("TypeError")}}。`handleResults()` 是一个由开发者定义的函数。

```js
const supportedProperties = await navigator.contacts.getProperties();

async function getContacts() {
  try {
    const contacts = await navigator.contacts.select(supportedProperties);
    handleResults(contacts);
  } catch (ex) {
    // Handle any errors here.
  }
}
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}