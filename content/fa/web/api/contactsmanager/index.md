---
title: ContactsManager
slug: Web/API/ContactsManager
page-type: web-api-interface
status:
  - experimental
browser-compat: api.ContactsManager
---

{{securecontext_header}}{{APIRef("Contact Picker API")}}{{SeeCompatTable}}

**`ContactsManager`** رابطِ [Contact Picker API](/en-US/docs/Web/API/Contact_Picker_API) است که به کاربران اجازه می‌دهد از لیست مخاطبین خود انتخاب کرده و اطلاعات محدودی از مخاطبین انتخابی را با یک وب‌سایت یا برنامه به اشتراک بگذارند.

`ContactsManager` از طریق ویژگی سراسری {{domxref('navigator.contacts')}} در دسترس است.

## روش‌های نمونه

- {{domxref('ContactsManager.select','select()')}} {{Experimental_Inline}}
  - : یک {{jsxref('Promise')}} برمی‌گرداند که پس از حل شدن، یک انتخاب‌گر مخاطب به کاربر نمایش می‌دهد تا مخاطب(های) مورد نظر خود را برای به اشتراک‌گذاری انتخاب کند.
- {{domxref('ContactsManager.getProperties()','getProperties()')}} {{Experimental_Inline}}
  - : یک {{jsxref('Promise')}} برمی‌گرداند که با یک {{jsxref('Array')}} از {{jsxref('String','string ها')}} حل می‌شود و نشان می‌دهد کدام ویژگی‌های مخاطب در دسترس هستند.

## مثال‌ها

### تشخیص ویژگی

کد زیر بررسی می‌کند که آیا Contact Picker API پشتیبانی می‌شود یا خیر.

```js
const supported = "contacts" in navigator && "ContactsManager" in window;
```

### بررسی ویژگی‌های پشتیبانی‌شده

تابع ناهمگام زیر از روش `getProperties` برای بررسی ویژگی‌های پشتیبانی‌شده استفاده می‌کند.

```js
async function checkProperties() {
  const supportedProperties = await navigator.contacts.getProperties();
  if (supportedProperties.includes("name")) {
    // run code for name support
  }
  if (supportedProperties.includes("email")) {
    // run code for email support
  }
  if (supportedProperties.includes("tel")) {
    // run code for telephone number support
  }
  if (supportedProperties.includes("address")) {
    // run code for address support
  }
  if (supportedProperties.includes("icon")) {
    // run code for avatar support
  }
}
```

### انتخاب مخاطبین

مثال زیر یک آرایه از ویژگی‌هایی را که باید برای هر مخاطب بازیابی شوند تعیین می‌کند و همچنین یک شیء options برای اجازه انتخاب چند مخاطب تنظیم می‌کند.

سپس یک تابع ناهمگام تعریف می‌شود که از روش `select()` برای نمایش رابط انتخاب‌گر مخاطب به کاربر و پردازش نتایج انتخاب‌شده استفاده می‌کند.

```js
const props = ["name", "email", "tel", "address", "icon"];
const opts = { multiple: true };

async function getContacts() {
  try {
    const contacts = await navigator.contacts.select(props, opts);
    handleResults(contacts);
  } catch (ex) {
    // Handle any errors here.
  }
}
```

`handleResults()` یک تابع تعریف‌شده توسط توسعه‌دهنده است.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [یک انتخاب‌گر مخاطب برای وب](https://developer.chrome.com/docs/capabilities/web-apis/contact-picker)
- [دموی زنده Contact Picker API](https://mdn.github.io/dom-examples/contact-picker/)