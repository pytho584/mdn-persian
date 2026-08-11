---
title: "translate HTML global attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Global_attributes/translate"
translated_by: "n8n + AI"
---

ویژگی سراسری `translate` یک ویژگی شمارشی (enumerated) است که مشخص می‌کند آیا مقادیر ویژگی‌های قابل ترجمهٔ یک عنصر (translatable attributes) و گره‌های متنی فرزند آن (`Text` node children) هنگام بومی‌سازی صفحه باید ترجمه شوند یا خیر.

مقادیر ممکن:

- **رشتهٔ خالی** یا **`yes`**: نشان می‌دهد که عنصر هنگام بومی‌سازی صفحه باید ترجمه شود.
- **`no`**: نشان می‌دهد که عنصر نباید ترجمه شود.

اگرچه همهٔ مرورگرها این ویژگی را تشخیص نمی‌دهند، اما سیستم‌های ترجمهٔ خودکار مانند Google Translate و ابزارهای مترجمان انسانی معمولاً به آن احترام می‌گذارند. بنابراین برای توسعه‌دهندگان وب مهم است که با استفاده از این ویژگی، محتوایی را که نباید ترجمه شود مشخص کنند.

## مثال

در این مثال، از ویژگی `translate` خواسته شده است که نام برند شرکت در فوتر ترجمه نشود.

```html
<footer>
  <small>© 2020 <span translate="no">BrandName</span></small>
</footer>
```

## همچنین ببینید

- همهٔ [ویژگی‌های سراسری](/en-US/docs/Web/HTML/Reference/Global_attributes)
- ویژگی `HTMLElement.translate` که این ویژگی را منعکس می‌کند
- [استفاده از ویژگی translate در HTML](https://www.w3.org/International/questions/qa-translate-flag)
- ویژگی [`lang`](/en-US/docs/Web/HTML/Reference/Global_attributes/lang)