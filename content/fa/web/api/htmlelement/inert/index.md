```
---
title: "HTMLElement: inert property"
---

---
title: "HTMLElement: inert property"
short-title: inert
slug: Web/API/HTMLElement/inert
page-type: web-api-instance-property
browser-compat: api.HTMLElement.inert
---

{{ APIRef("HTML DOM") }}

ویژگی **`inert`** در {{domxref("HTMLElement")}}، مقدار ویژگی [`inert`](/en-US/docs/Web/HTML/Reference/Global_attributes/inert) عنصر را بازتاب می‌دهد. این یک مقدار بولی است که وقتی وجود داشته باشد، باعث می‌شود مرورگر رویدادهای ورودی کاربر را برای آن عنصر «نادیده» بگیرد، از جمله رویدادهای فوکوس و رویدادهای فناوری‌های کمکی. مرورگر ممکن است جستجوی صفحه و انتخاب متن را در آن عنصر نیز نادیده بگیرد. این موضوع هنگام ساخت رابط‌های کاربری مانند مودال‌ها مفید است که در آن‌ها می‌خواهید وقتی مودال قابل مشاهده است، فوکوس را در همان مودال «به دام بیندازید».

توجه داشته باشید که اگر ویژگی `inert` مشخص نشده باشد، خود عنصر ممکن است همچنان بی‌اثری را از والد خود به ارث ببرد. با این حال، این بی‌اثری به ارث رسیده در مقدار این ویژگی بازتاب نمی‌یابد. تنظیم صریح این ویژگی به `false` نمی‌تواند بی‌اثری به ارث رسیده از والد را معکوس کند.

## مقدار

یک مقدار بولی که اگر عنصر بی‌اثر (inert) باشد، `true` است؛ در غیر این صورت مقدار آن `false` است.

## مثال‌ها

### HTML

```html
<div>
  <label for="button1">Button 1</label>
  <button id="button1">I am not inert</button>
</div>
<div inert>
  <label for="button2">Button 2</label>
  <button id="button2">I am inert</button>
</div>
```

### CSS

```css
[inert] > * {
  opacity: 0.5;
}
```

{{ EmbedLiveSample('Examples', 560, 200) }}

> [!NOTE]
> این ویژگی به‌تنهایی هیچ تغییر بصری در محتوای نمایش‌داده‌شده در مرورگر ایجاد نمی‌کند. در مثال بالا، CSS اعمال شده است تا هر فرزند مستقیم عنصری که ویژگی `inert` دارد، به‌صورت نیمه‌شفاف نمایش داده شود.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [ویژگی سراسری: `inert`](/en-US/docs/Web/HTML/Reference/Global_attributes/inert)
- {{domxref("HTMLInputElement.disabled", "disabled")}}
- {{HTMLElement("dialog")}}
- ویژگی CSS {{cssxref("interactivity")}}
```