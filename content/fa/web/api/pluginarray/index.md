---
title: PluginArray
slug: Web/API/PluginArray
page-type: web-api-interface
status:
  - deprecated
browser-compat: api.PluginArray
---

{{APIRef("HTML DOM")}}{{deprecated_header}}

رابط `PluginArray` برای نگهداری فهرستی از اشیاء {{DOMxRef("Plugin")}} به‌کار می‌رود و توسط ویژگی {{DOMxRef("Navigator.plugins", "navigator.plugins")}} بازگردانده می‌شود. `PluginArray` یک آرایهٔ جاوااسکریپت نیست، اما دارای ویژگی `length` است و امکان دسترسی به تک‌تک آیتم‌ها را هم از طریق نشانه‌گذاری براکت (`plugins[2]`) و هم از طریق متدهای `item(index)` و `namedItem("name")` فراهم می‌کند.

> [!NOTE]
> در جدیدترین نسخه‌های مرورگرها، ویژگی‌های اختصاصی اشیای `PluginArray` دیگر شمارش‌پذیر نیستند.

## ویژگی‌های نمونه

- {{DOMxRef("PluginArray.length")}} {{ReadOnlyInline}} {{Deprecated_Inline}}
  - : تعداد پلاگین‌های موجود در آرایه.

## متدهای نمونه

- {{DOMxRef("PluginArray.item")}} {{Deprecated_Inline}}
  - : شیء {{DOMxRef("Plugin")}} را در ایندکسِ مشخص‌شده در آرایه بازمی‌گرداند.
- {{DOMxRef("PluginArray.namedItem")}} {{Deprecated_Inline}}
  - : شیء {{DOMxRef("Plugin")}} را با نام مشخص‌شده بازمی‌گرداند.
- {{DOMxRef("PluginArray.refresh")}} {{Deprecated_Inline}}
  - : همهٔ پلاگین‌های صفحهٔ جاری را تازه‌سازی می‌کند و به‌صورت اختیاری اسناد را نیز از نو بارگذاری می‌کند.

## مثال‌ها

مثال زیر، نسخهٔ پلاگین شاک‌ویو فلش را به دست می‌دهد.

```js
const pluginsLength = navigator.plugins.length;

document.body.innerHTML =
  `${pluginsLength} Plugin(s)<br>` +
  `<table id="pluginTable"><thead>` +
  `<tr><th>Name</th><th>Filename</th><th>description</th><th>version</th></tr>` +
  `</thead><tbody></tbody></table>`;

const table = document.getElementById("pluginTable");

for (let i = 0; i < pluginsLength; i++) {
  let newRow = table.insertRow();
  newRow.insertCell().textContent = navigator.plugins[i].name;
  newRow.insertCell().textContent = navigator.plugins[i].filename;
  newRow.insertCell().textContent = navigator.plugins[i].description;
  newRow.insertCell().textContent = navigator.plugins[i].version ?? "";
}
```

مثال زیر اطلاعاتی دربارهٔ پلاگین(های) نصب‌شده نمایش می‌دهد.

```js
const pluginsLength = navigator.plugins.length;

document.write(
  `${pluginsLength.toString()} Plugin(s)<br>` +
    `Name | Filename | description<br>`,
);

for (let i = 0; i < pluginsLength; i++) {
  document.write(
    `${navigator.plugins[i].name} | ${navigator.plugins[i].filename} | ${navigator.plugins[i].description} | ${navigator.plugins[i].version}<br>`,
  );
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

علاوه بر اینکه هر پلاگین از طریق ویژگی‌های عددی با ایندکسِ صفر به‌صورت یک شبه‌آرایه فهرست می‌شود، فایرفاکس ویژگی‌هایی را نیز مستقیماً روی شیء `PluginArray` ارائه می‌کند که نامِ همان پلاگین هستند.