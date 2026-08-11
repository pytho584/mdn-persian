---
title: "capture HTML attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Attributes/capture"
translated_by: "n8n + AI"
---

# ویژگی HTML `capture`

ویژگی **`capture`** مشخص می‌کند که (به‌صورت اختیاری) یک فایل جدید باید ضبط شود، و کدام دستگاه برای ضبط آن رسانه با نوع تعریف‌شده توسط ویژگی [`accept`](/en-US/docs/Web/HTML/Reference/Attributes/accept) استفاده شود.

مقادیر شامل `user` و `environment` است. ویژگی `capture` روی نوع ورودی `<input type="file">` پشتیبانی می‌شود.

ویژگی `capture` یک رشته به‌عنوان مقدار می‌پذیرد که مشخص می‌کند برای ضبط تصویر یا ویدئو از کدام دوربین استفاده شود، اگر ویژگی [`accept`](/en-US/docs/Web/HTML/Reference/Attributes/accept) مشخص کند که ورودی باید از یکی از این انواع باشد.

| مقدار | توضیحات |
| ------------- | ---------------------------------------------------------- |
| `user` | دوربین و/یا میکروفونِ روبه‌روی کاربر باید استفاده شود. |
| `environment` | دوربین و/یا میکروفونِ رو به بیرون باید استفاده شود. |

> [!NOTE]
> ویژگی `capture` قبلاً یک ویژگی Boolean بود که اگر وجود داشت، به‌جای درخواست انتخاب فایل، دستگاه ضبط رسانه (مثل دوربین یا میکروفون) را درخواست می‌کرد.

## مثال تعاملی

```html interactive-example
<label for="selfie">Take a picture of your face:</label>

<input type="file" id="selfie" name="selfie" accept="image/*" capture="user" />

<label for="picture">Take a picture using back facing camera:</label>

<input
  type="file"
  id="picture"
  name="picture"
  accept="image/*"
  capture="environment" />
```

```css interactive-example
label {
  display: block;
  margin-top: 1rem;
}

input {
  margin-bottom: 1rem;
}
```

## مثال‌ها

وقتی روی نوع ورودی فایل تنظیم شود، سیستم‌عامل‌های دارای میکروفون و دوربین، رابط کاربری نمایش می‌دهند که امکان انتخاب از یک فایل موجود یا ایجاد فایل جدید را فراهم می‌کند.

```html
<p>
  <label for="soundFile">What does your voice sound like?:</label>
  <input type="file" id="soundFile" capture="user" accept="audio/*" />
</p>
<p>
  <label for="videoFile">Upload a video:</label>
  <input type="file" id="videoFile" capture="environment" accept="video/*" />
</p>
<p>
  <label for="imageFile">Upload a photo of yourself:</label>
  <input type="file" id="imageFile" capture="user" accept="image/*" />
</p>
```

این نمونه‌ها روی دستگاه‌های موبایل بهتر کار می‌کنند؛ اگر دستگاه شما رایانه رومیزی است، احتمالاً یک انتخاب‌گر فایل معمولی خواهید دید.

## جستارهای وابسته

- [استفاده از فایل‌ها در برنامه‌های وب](/en-US/docs/Web/API/File_API/Using_files_from_web_applications)
- [File API](/en-US/docs/Web/API/File)
- `HTMLInputElement.files`