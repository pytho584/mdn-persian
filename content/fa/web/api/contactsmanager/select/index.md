---
title: "ContactsManager: select() method"
short-title: select()
slug: Web/API/ContactsManager/select
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.ContactsManager.select
---

{{securecontext_header}}{{APIRef("Contact Picker API")}}{{SeeCompatTable}}

متد **`select()`** از رابط {{domxref("ContactsManager")}} یک {{jsxref('Promise')}} برمی‌گرداند که پس از حل شدن، یک انتخاب‌گر مخاطب (contact picker) به کاربر نمایش می‌دهد و به او امکان می‌دهد مخاطب(هایی) را که می‌خواهد به اشتراک بگذارد، انتخاب کند. این متد برای حل شدن {{jsxref('Promise')}} نیاز به یک کنش کاربری (user gesture) دارد.

## Syntax

```js-nolint
select(properties)
select(properties, options)
```

### پارامترها

- `properties`
  - : آرایه‌ای از {{jsxref('String', 'رشته‌ها')}} که مشخص می‌کند چه اطلاعاتی از یک مخاطب دریافت شود. مقادیر مجاز به شرح زیر است:
    - `'name'`: نام مخاطب.
    - `'tel'`: شماره(های) تلفن مخاطب.
    - `'email'`: آدرس ایمیل مخاطب.
    - `'address'`: آدرس پستی مخاطب.
    - `'icon'`: تصویر آواتار مخاطب.

- `options` {{optional_inline}}
  - : گزینه‌ها به شرح زیر است:
    - `multiple`
      - : یک مقدار بولین که امکان انتخاب چندین مخاطب را فراهم می‌کند. مقدار پیش‌فرض `false` است.

### مقدار بازگشتی

یک {{jsxref('Promise')}} برمی‌گرداند که با آرایه‌ای از اشیاء حاوی اطلاعات مخاطب حل می‌شود. هر شیء نمایانگر یک مخاطب است و ممکن است شامل ویژگی‌های زیر باشد:

- `address`
  - : یک {{jsxref("Array")}} از اشیاء {{domxref("ContactAddress")}} که هر کدام جزئیات یک آدرس فیزیکی منحصربه‌فرد را شامل می‌شود.
- `email`
  - : آرایه‌ای از رشته‌ها حاوی آدرس‌های ایمیل.
- `icon`
  - : آرایه‌ای از اشیاء {{domxref("Blob")}} حاوی تصاویر یک شخص.
- `name`
  - : آرایه‌ای از رشته‌ها، هر کدام حاوی یک نام منحصربه‌فرد از یک شخص.
- `tel`
  - : آرایه‌ای از رشته‌ها، هر کدام حاوی یک شماره تلفن منحصربه‌فرد از یک شخص.

### استثناها

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر زمینه مرورگر (browsing context) سطح بالا نباشد، اگر انتخاب‌گر مخاطب پرچمی را نشان دهد که نشان‌دهنده یک انتخاب‌گر مخاطب از قبل موجود است (زیرا فقط یک انتخاب‌گر می‌تواند در هر زمان وجود داشته باشد)، یا اگر راه‌اندازی انتخاب‌گر مخاطب با شکست مواجه شود، برگردانده می‌شود.
- `SecurityError` {{domxref("DOMException")}}
  - : اگر متد توسط [فعال‌سازی کاربر](/en-US/docs/Web/Security/Defenses/User_activation) راه‌اندازی نشود، برگردانده می‌شود.
- {{jsxref("TypeError")}}
  - : اگر `properties` خالی باشد، یا اگر هر یک از ویژگی‌های مشخص‌شده پشتیبانی نشوند، برگردانده می‌شود.

## امنیت

{{Glossary("Transient activation")}} (فعال‌سازی زودگذر) مورد نیاز است. کاربر باید با صفحه یا یک عنصرUI تعامل داشته باشد تا این ویژگی کار کند.

## مثال‌ها

### مثال پایه

مثال زیر یک آرایه از ویژگی‌هایی را که برای هر مخاطب باید بازیابی شود، تنظیم می‌کند و همچنین یک شیء گزینه را تنظیم می‌کند تا امکان انتخاب چندین مخاطب فراهم شود.

سپس یک تابع ناهمگام (asynchronous) تعریف می‌شود که از متد `select()` برای نمایش یک رابط انتخاب‌گر مخاطب به کاربر و مدیریت نتایج انتخاب‌شده استفاده می‌کند. `handleResults()` یک تابع تعریف‌شده توسط توسعه‌دهنده است.

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

### انتخاب فقط با استفاده از ویژگی‌های پشتیبانی‌شده

مثال زیر از {{domxref("ContactsManager.getProperties", "getProperties()")}} استفاده می‌کند تا اطمینان حاصل شود که فقط ویژگی‌های پشتیبانی‌شده ارسال می‌شوند. در غیر این صورت، `select()` ممکن است یک {{jsxref("TypeError")}} پرتاب کند. `handleResults()` یک تابع تعریف‌شده توسط توسعه‌دهنده است.

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

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}