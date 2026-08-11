---
title: "autocapitalize HTML global attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Global_attributes/autocapitalize"
translated_by: "n8n + AI"
---

## ویژگی سراسری `autocapitalize`

ویژگی سراسری `autocapitalize` از نوع enumerated است که مشخص می‌کند آیا متن ورودی به‌طور خودکار با حرف بزرگ شروع شود یا نه، و اگر بله، به چه صورت. این ویژگی برای موارد زیر کاربرد دارد:

- المان‌های {{htmlelement("input")}} و {{htmlelement("textarea")}}
- هر المانی که [`contenteditable`](/en-US/docs/Web/HTML/Reference/Global_attributes/contenteditable) روی آن تنظیم شده باشد.

`autocapitalize` روی تایپ با صفحه‌کلید فیزیکی تأثیری ندارد. این ویژگی روی سایر مکانیزم‌های ورودی مثل صفحه‌کلید مجازی در دستگاه‌های موبایل و ورودی صوتی تأثیر می‌گذارد. این کار می‌تواند با بزرگ‌کردن خودکار حرف اول هر جمله، ورود داده را سریع‌تر و آسان‌تر کند.

## مقدار

مقادیر ممکن عبارتند از:

- `none` یا `off`
  - : هیچ متنی به‌طور خودکار بزرگ نمی‌شود.
- `sentences` یا `on`
  - : اولین نویسه هر جمله به‌طور خودکار بزرگ می‌شود.
- `words`
  - : اولین نویسه هر کلمه به‌طور خودکار بزرگ می‌شود.
- `characters`
  - : همه نویسه‌ها به‌طور خودکار بزرگ می‌شوند.

## نکات استفاده

- `autocapitalize` را می‌توان روی المان‌های `<input>` و `<textarea>` _و_ روی المان {{htmlelement("form")}} والد آن‌ها تنظیم کرد. وقتی `autocapitalize` روی یک `<form>` تنظیم شود، رفتار بزرگ‌سازی خودکار را برای تمام `<input>` و `<textarea>`های داخل آن تعیین می‌کند و هر مقدار `autocapitalize` تنظیم‌شده روی المان‌های داخلی را نادیده می‌گیرد.
- `autocapitalize` روی انواع `<input>` با `url`، `email` یا `password` اثری ندارد، زیرا بزرگ‌سازی خودکار در این موارد هرگز فعال نیست.
- وقتی `autocapitalize` مشخص نشده باشد، رفتار پیش‌فرض در مرورگرهای مختلف متفاوت است. مثلاً:
  - Chrome و Safari پیش‌فرض را روی `on`/`sentences` قرار می‌دهند.
  - Firefox پیش‌فرض را روی `off`/`none` قرار می‌دهد.

## مثال‌ها

### HTML

```html
<p>فرمی برای تست تنظیمات مختلف autocapitalize:</p>

<form>
  <div>
    <label for="default">پیش‌فرض: autocapitalize تنظیم نشده</label>
    <input type="text" id="default" name="default" />
  </div>
  <div>
    <label for="off">autocapitalize="off"</label>
    <input type="text" id="off" name="off" autocapitalize="off" />
  </div>
  <div>
    <label for="none">autocapitalize="none"</label>
    <input type="text" id="none" name="none" autocapitalize="none" />
  </div>
  <div>
    <label for="on">autocapitalize="on"</label>
    <input type="text" id="on" name="on" autocapitalize="on" />
  </div>
  <div>
    <label for="sentences">autocapitalize="sentences"</label>
    <input
      type="text"
      id="sentences"
      name="sentences"
      autocapitalize="sentences" />
  </div>
  <div>
    <label for="words">autocapitalize="words"</label>
    <input type="text" id="words" name="words" autocapitalize="words" />
  </div>
  <div>
    <label for="characters">autocapitalize="characters"</label>
    <input type="text" id="characters" name="characters" autocapitalize="characters" />
  </div>
  <div>
    <label for="characters-ta">autocapitalize="characters" روی textarea</label>
    <textarea
      type="text"
      id="characters-ta"
      name="characters-ta"
      autocapitalize="characters">
    </textarea>
  </div>
</form>

<hr />

<p contenteditable autocapitalize="characters">
  این محتوا قابل ویرایش است و autocapitalize="characters" روی آن تنظیم شده است.
</p>
```

```css hidden
div {
  margin-bottom: 20px;
}
```

## نتیجه

با استفاده از صفحه‌کلید مجازی یا ورودی صوتی (نه صفحه‌کلید فیزیکی) تأثیر تنظیمات مختلف را روی هر فیلد تست کنید.