---
title: ContactAddress
slug: Web/API/ContactAddress
page-type: web-api-interface
status:
  - experimental
browser-compat: api.ContactAddress
---

{{securecontext_header}}{{APIRef("Contact Picker API")}}{{SeeCompatTable}}

رابطهٔ **`ContactAddress`** در [API انتخاب مخاطب](/en-US/docs/Web/API/Contact_Picker_API) یک آدرس فیزیکی را نشان می‌دهد. نمونه‌های این رابط از ویژگی `address` اشیایی که توسط {{domxref("ContactsManager.getProperties()")}} بازگردانده می‌شوند، بازیابی می‌شوند.

ممکن است مراجعه به مطالب [استاندارد S42 آدرس‌دهی](https://www.upu.int/en/Postal-Solutions/Programmes-Services/Addressing-Solutions#addressing-s42-standard) وب‌سایت اتحادیهٔ جهانی پست مفید باشد؛ این مطالب اطلاعاتی دربارهٔ استانداردهای بین‌المللی آدرس‌های پستی ارائه می‌دهند.

## ویژگی‌های نمونه

- {{domxref('ContactAddress.addressLine')}} {{ReadOnlyInline}} {{experimental_inline}}
  - : یک آرایه از رشته‌ها که هر خط از آدرس را که در سایر ویژگی‌ها ذکر نشده است، ارائه می‌دهد. اندازه و محتوای دقیق آن بسته به کشور یا مکان متفاوت است و می‌تواند شامل مواردی مانند نام خیابان، شمارهٔ خانه، شمارهٔ واحد، مسیر تحویل روستایی، دستورالعمل‌های توصیفی یا شمارهٔ صندوق پستی باشد.
- {{domxref('ContactAddress.country')}} {{ReadOnlyInline}} {{experimental_inline}}
  - : رشته‌ای که کشور محل آدرس را با استفاده از استاندارد [ISO-3166-1 alpha-2](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) مشخص می‌کند. این رشته همیشه به شکل حروف بزرگ استاندارد ارائه می‌شود. چند مثال از مقادیر معتبر `country`: `"US"`، `"GB"`، `"CN"` یا `"JP"`.
- {{domxref('ContactAddress.city')}} {{ReadOnlyInline}} {{experimental_inline}}
  - : رشته‌ای که بخش شهر یا شهرک آدرس را شامل می‌شود.
- {{domxref('ContactAddress.dependentLocality')}} {{ReadOnlyInline}} {{experimental_inline}}
  - : رشته‌ای که محل وابسته یا زیرمحل را در داخل یک شهر مشخص می‌کند؛ برای مثال، یک محله، ناحیه، منطقه یا محل وابسته در بریتانیا.
- {{domxref('ContactAddress.organization')}} {{ReadOnlyInline}} {{experimental_inline}}
  - : رشته‌ای که نام سازمان، شرکت، مؤسسه یا نهاد را در آن آدرس مشخص می‌کند.
- {{domxref('ContactAddress.phone')}} {{ReadOnlyInline}} {{experimental_inline}}
  - : رشته‌ای که شماره تلفن گیرنده یا شخص تماس را مشخص می‌کند.
- {{domxref('ContactAddress.postalCode')}} {{ReadOnlyInline}} {{experimental_inline}}
  - : رشته‌ای که کد پستی مورد استفاده یک حوزهٔ قضایی برای مسیریابی نامه را مشخص می‌کند؛ برای مثال، کد ZIP در ایالات متحده یا کد PIN در هند.
- {{domxref('ContactAddress.recipient')}} {{ReadOnlyInline}} {{experimental_inline}}
  - : رشته‌ای که نام گیرنده، خریدار یا شخص تماس در آن آدرس را ارائه می‌دهد.
- {{domxref('ContactAddress.region')}} {{ReadOnlyInline}} {{experimental_inline}}
  - : رشته‌ای که بالاترین سطح تقسیمات اداری کشور را شامل می‌شود؛ برای مثال، یک ایالت، استان، اوبلاست یا استان (در برخی کشورها).
- {{domxref('ContactAddress.sortingCode')}} {{ReadOnlyInline}} {{experimental_inline}}
  - : رشته‌ای که یک کد مرتب‌سازی پستی مانند کد مورد استفاده در فرانسه را ارائه می‌دهد.

## روش‌های نمونه

- {{domxref('ContactAddress.toJSON()')}} {{experimental_inline}}
  - : یک سریال‌ساز استاندارد که نمایش JSON از ویژگی‌های شیء `ContactAddress` را بازمی‌گرداند.

## مثال‌ها

مثال زیر از کاربر می‌خواهد مخاطبانی را انتخاب کند و سپس اولین آدرس بازگردانده‌شده را در کنسول چاپ می‌کند.

```js
const props = ["address"];
const opts = { multiple: true };

async function getContacts() {
  try {
    const contacts = await navigator.contacts.select(props, opts);
    const contactAddress = contacts[0].address[0];
    console.log(contactAddress);
  } catch (ex) {
    // Handle any errors here.
  }
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}