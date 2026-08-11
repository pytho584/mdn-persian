---
title: "required HTML attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Attributes/required"
translated_by: "n8n + AI"
---

ویژگی (attribute) بولی (Boolean) **`required`** اگر وجود داشته باشد، نشان می‌دهد که کاربر باید قبل از ارسال فرم، مقداری را برای این input مشخص کند.

ویژگی `required` توسط انواع ورودی `{{HTMLElement("input/text","text")}}`، `{{HTMLElement("input/search","search")}}`، `{{HTMLElement("input/url","url")}}`، `{{HTMLElement("input/tel","tel")}}`، `{{HTMLElement("input/email","email")}}`، `{{HTMLElement("input/password","password")}}`، `{{HTMLElement("input/date","date")}}`، `{{HTMLElement("input/month","month")}}`، `{{HTMLElement("input/week","week")}}`، `{{HTMLElement("input/time","time")}}`، `{{HTMLElement("input/datetime-local","datetime-local")}}`، `{{HTMLElement("input/number","number")}}`، `{{HTMLElement("input/checkbox","checkbox")}}`، `{{HTMLElement("input/radio","radio")}}`، `{{HTMLElement("input/file","file")}}` از `<input>` و همچنین عناصر `<select>` و `<textarea>` پشتیبانی می‌شود. اگر روی هر یک از این انواع input و عناصر وجود داشته باشد، pseudo-class `:required` اعمال می‌شود. اگر ویژگی وجود نداشته باشد، pseudo-class `:optional` اعمال می‌شود.

این ویژگی برای انواع `{{HTMLElement("input/range","range")}}` و `{{HTMLElement("input/color","color")}}` پشتیبانی نمی‌شود (و کاربردی هم ندارد)؛ زیرا هر دو مقدار پیش‌فرض دارند. نوع `color` به طور پیش‌فرض `#000000` است. نوع `range` به طور پیش‌فرض نقطه میانی بین `min` و `max` است — در بیشتر مرورگرها اگر `min` و `max` اعلام نشوند، مقدار پیش‌فرض آن‌ها به ترتیب 0 و 100 است. `required` همچنین برای نوع `hidden` پشتیبانی نمی‌شود — نمی‌توان از کاربر انتظار داشت که یک فیلد مخفی فرم را پر کند. در نهایت، `required` روی هیچ نوع دکمه‌ای (از جمله `<input type="image">`) پشتیبانی نمی‌شود.

در مورد گروهی از دکمه‌های رادیویی (`radio`) با نام یکسان، اگر یک دکمه رادیویی در گروه دارای ویژگی `required` باشد، باید یکی از دکمه‌های رادیویی آن گروه انتخاب شده باشد، هرچند لازم نیست همان دکمه‌ای باشد که ویژگی روی آن اعمال شده است. برای بهبود نگهداری کد، توصیه می‌شود ویژگی `required` یا روی همه دکمه‌های رادیویی هم‌نام در گروه قرار گیرد یا روی هیچ‌کدام.

در مورد گروهی از checkboxهای هم‌نام، فقط آن checkboxهایی که ویژگی `required` دارند، اجباری هستند.

> **توجه:** تنظیم `aria-required="true"` به صفحه‌خوان (screen reader) می‌گوید که یک عنصر (هر عنصری) اجباری است، اما تأثیری بر اجباری یا اختیاری بودن خود عنصر ندارد.

## توضیحات

### تعامل ویژگی‌ها

از آنجا که یک فیلد فقط‌خواندنی (read-only) قابل تغییر نیست، `required` روی inputهایی که ویژگی [`readonly`](/en-US/docs/Web/HTML/Reference/Attributes/readonly) نیز دارند تأثیری ندارد.

### قابلیت استفاده

هنگام استفاده از ویژگی `required`، یک نشانه بصری در نزدیکی کنترل قرار دهید که به کاربر اطلاع دهد `<input>`، `<select>` یا `<textarea>` مورد نظر اجباری است. همچنین، کنترل‌های فرم اجباری را با pseudo-class `:required` هدف قرار دهید و آن‌ها را به شکلی استایل دهید که نشان‌دهنده اجباری بودنشان باشد. این کار قابلیت استفاده را برای کاربران بینا بهبود می‌بخشد. فناوری کمکی (assistive technology) باید بر اساس ویژگی `required` به کاربر اطلاع دهد که کنترل فرم اجباری است. اما اضافه کردن `aria-required="true"` ضرری ندارد، در صورتی که ترکیب مرورگر/صفحه‌خوان هنوز از `required` پشتیبانی نکند.

### اعتبارسنجی محدودیت (Constraint validation)

اگر المنت ویژگی `required` داشته باشد و مقدارش رشتهٔ خالی باشد، المنت دچار `valueMissing` می‌شود و با شبه‌کلاس `:invalid` مطابقت خواهد کرد.

## نگرانی‌های دسترس‌پذیری

به کاربران نشان دهید که این کنترلِ فرم الزامی است. مطمئن شوید پیام‌رسانی چندوجهی است؛ مثلاً از طریق متن، رنگ، نشانه‌گذاری و attribute، تا همهٔ کاربران — چه کسانی که کوررنگی دارند، چه افرادی با تفاوت‌های شناختی، و چه کسانی که از صفحه‌خوان استفاده می‌کنند — این الزام را درک کنند.

## مثال

### HTML

```html
<form>
  <div class="group">
    <input type="text" />
    <label>Normal</label>
  </div>
  <div class="group">
    <input type="text" required />
    <label>Required</label>
  </div>
  <input type="submit" />
</form>
```

## همچنین ببینید

- `ValidityState.valueMissing`
- `:required` و `:optional`
- `<input>`
- `<select>`