---
title: "translate HTML global attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Global_attributes/translate"
translated_by: "n8n + AI"
---

# ویژگی سراسری `translate` در HTML

ویژگی سراسری **`translate`** یک ویژگی از نوع `enumerated` است که مشخص می‌کند آیا مقادیر ویژگی‌های قابل ترجمهٔ یک عنصر و گره‌های متنی فرزند آن باید هنگام بومی‌سازی صفحه ترجمه شوند یا بدون تغییر بمانند.

این ویژگی می‌تواند مقادیر زیر را داشته باشد:

- رشتهٔ خالی یا `yes` که نشان می‌دهد عنصر هنگام بومی‌سازی صفحه باید ترجمه شود.
- `no` که نشان می‌دهد عنصر نباید ترجمه شود.

اگرچه همهٔ مرورگرها این ویژگی را تشخیص نمی‌دهند، اما سیستم‌های ترجمهٔ خودکار مانند Google Translate به آن احترام می‌گذارند و ممکن است ابزارهای مترجمان انسانی نیز از آن پیروی کنند. بنابراین برای توسعه‌دهندگان وب مهم است که از این ویژگی برای علامت‌گذاری محتوایی که نباید ترجمه شود استفاده کنند.

## مثال

در این مثال، ویژگی `translate` برای درخواست از ابزارهای ترجمه استفاده شده است که نام تجاری شرکت را در فوتر ترجمه نکنند.

```html
<footer>
  <small>© 2020 <span translate="no">BrandName</span></small>
</footer>
```

## همچنین ببینید

- تمام [ویژگی‌های سراسری](/en-US/docs/Web/HTML/Reference/Global_attributes)
- ویژگی `HTMLElement.translate` که این ویژگی را منعکس می‌کند
- [Using HTML's translate attribute](https://www.w3.org/International/questions/qa-translate-flag)
- ویژگی HTML [`lang`](/en-US/docs/Web/HTML/Reference/Global_attributes/lang)