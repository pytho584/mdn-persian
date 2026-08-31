---
title: Contact Picker API
slug: Web/API/Contact_Picker_API
page-type: web-api-overview
status:
  - experimental
browser-compat: api.ContactsManager
---

{{securecontext_header}}{{DefaultAPISidebar("Contact Picker API")}}{{SeeCompatTable}}

Contact Picker API به کاربران اجازه می‌دهد ورودی‌هایی را از فهرست مخاطبان خود انتخاب کنند و جزئیات محدودی از ورودی‌های انتخاب‌شده را با یک وب‌سایت یا برنامه به اشتراک بگذارند.

> [!NOTE]
> این API در [Web Workers](/en-US/docs/Web/API/Web_Workers_API) در دسترس _نیست_ (از طریق {{domxref("WorkerNavigator")}} در معرض دید قرار نمی‌گیرد).

## مفاهیم و کاربرد Contact Picker API

دسترسی به مخاطبان مدت طولانی است که یکی از امکانات موجود در برنامه‌های بومی (native) به شمار می‌رود. Contact Picker API این قابلیت را به برنامه‌های وب می‌آورد.

موارد استفاده شامل انتخاب مخاطب برای ارسال پیام از طریق یک برنامه ایمیل یا چت، انتخاب شماره تلفن مخاطب برای استفاده در تماس صوتی از طریق پروتکل اینترنت (VOIP)، یا یافتن مخاطبانی است که قبلاً به یک پلتفرم اجتماعی پیوسته‌اند. عامل‌های کاربر (user agents) همچنین می‌توانند تجربه‌ای سازگار با سایر برنامه‌های موجود روی دستگاه کاربر ارائه دهند.

هنگام فراخوانی متد {{domxref('ContactsManager.select', 'select')}} از رابط {{domxref('ContactsManager')}}، یک انتخاب‌گر مخاطب (contact picker) به کاربر نمایش داده می‌شود که از طریق آن می‌تواند اطلاعات تماس مورد نظر برای به اشتراک‌گذاری با برنامه وب را انتخاب کند. پیش از اعطای اجازه نمایش انتخاب‌گر مخاطب، تعامل کاربر ضروری است و دسترسی به مخاطبان دائمی نیست؛ کاربر باید هر بار که برنامه درخواستی ارسال می‌کند، اجازه دسترسی را صادر کند.

این API فقط از یک زمینه مرور سطح بالا و امن (secure top-level browsing context) در دسترس است و با دقت زیادی حساسیت و حریم خصوصی داده‌های مخاطبان را در نظر می‌گیرد. مسئولیت انتخاب داده‌های قابل اشتراک‌گذاری بر عهده کاربر است؛ این API فقط به داده‌های مشخصی از مخاطبان انتخاب‌شده اجازه می‌دهد و هیچ دسترسی به داده‌های سایر مخاطبان وجود ندارد.

## رابط‌ها

- {{domxref("ContactAddress")}}
  - : یک آدرس فیزیکی را نمایش می‌دهد.
- {{domxref("ContactsManager")}}
  - : راهی برای انتخاب و به اشتراک‌گذاری جزئیات محدود مخاطبان با یک برنامه وب در اختیار کاربران قرار می‌دهد.
- {{domxref("Navigator.contacts")}}
  - : یک نمونه از شیء {{domxref("ContactsManager")}} برمی‌گرداند که از طریق آن می‌توان به تمام عملکردهای دیگر دسترسی داشت.

## نمونه‌ها

### تشخیص ویژگی

کد زیر بررسی می‌کند که آیا Contact Picker API پشتیبانی می‌شود یا خیر.

```js
const supported = "contacts" in navigator;
```

### بررسی ویژگی‌های پشتیبانی‌شده

تابع ناهمگام زیر از متد `getProperties()` برای بررسی ویژگی‌های پشتیبانی‌شده استفاده می‌کند.

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

### انتخاب مخاطبان

مثال زیر آرایه‌ای از ویژگی‌های مورد نیاز برای بازیابی هر مخاطب و همچنین یک شیء options تنظیم می‌کند تا امکان انتخاب چند مخاطب فراهم شود.

سپس یک تابع ناهمگام تعریف می‌شود که از متد `select()` برای نمایش رابط انتخاب‌گر مخاطب به کاربر و مدیریت نتایج انتخاب‌شده استفاده می‌کند.

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

- [A Contact Picker for the Web](https://developer.chrome.com/docs/capabilities/web-apis/contact-picker)
- [Contact Picker API live demo](https://mdn.github.io/dom-examples/contact-picker/)