---
title: "ARIA: checkbox role"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/checkbox_role"
translated_by: "n8n + AI"
short-title: checkbox
slug: Web/Accessibility/ARIA/Reference/Roles/checkbox_role
page-type: aria-role
sidebar: accessibilitysidebar
---

نقش `checkbox` برای کنترل‌های تعاملی قابل علامت‌گذاری است. عناصری که حاوی `role="checkbox"` هستند باید شامل ویژگی [`aria-checked`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-checked) باشند تا وضعیت چک‌باکس را به فناوری کمکی نشان دهند.

```html
<span
  role="checkbox"
  aria-checked="false"
  tabindex="0"
  aria-labelledby="chk1-label"></span>
<label id="chk1-label">Remember my preferences</label>
```

> [!NOTE]
> اولین قانون ARIA این است که اگر یک عنصر یا ویژگی بومی HTML دارای معناشناسی و رفتار مورد نیاز شما است، از آن استفاده کنید به جای اینکه یک عنصر را تغییر کاربری داده و ARIA اضافه کنید. به جای آن از [چک‌باکس HTML `<input type="checkbox">`](/en-US/docs/Web/HTML/Reference/Elements/input/checkbox) (با یک {{HTMLElement('label')}} مرتبط) استفاده کنید که به صورت بومی تمام عملکرد مورد نیاز را فراهم می‌کند:

```html
<input type="checkbox" id="chk1-label" name="RememberPreferences" />
<label for="chk1-label">Remember my preferences</label>
```

## توضیحات

کنترل فرم چک‌باکس بومی HTML ([`<input type="checkbox">`](/en-US/docs/Web/HTML/Reference/Elements/input/checkbox)) دو حالت داشت ("علامت‌خورده" یا "علامت‌نخورده")، با یک حالت [`indeterminate`](/en-US/docs/Web/HTML/Reference/Elements/input/checkbox#indeterminate_state_checkboxes) که از طریق جاوااسکریپت قابل تنظیم است. به طور مشابه، یک عنصر با `role="checkbox"` می‌تواند سه حالت را از طریق ویژگی `aria-checked` نشان دهد: `true`، `false` یا `mixed`.

از آنجایی که چک‌باکس یک کنترل تعاملی است، باید قابل فوکوس و قابل دسترس از طریق صفحه‌کلید باشد. اگر نقش به یک عنصر غیرقابل فوکوس اعمال می‌شود، از ویژگی [`tabindex`](/en-US/docs/Web/HTML/Reference/Global_attributes/tabindex) برای تغییر این وضعیت استفاده کنید. میانبر مورد انتظار صفحه‌کلید برای فعال کردن یک چک‌باکس کلید <kbd>Space</kbd> است.

توسعه‌دهنده موظف است مقدار ویژگی `aria-checked` را به صورت پویا در هنگام فعال شدن چک‌باکس تغییر دهد.

### همه فرزندان نمایشی هستند

برخی از انواع اجزای رابط کاربری وجود دارند که وقتی در API دسترس‌پذیری پلتفرم نمایش داده می‌شوند، فقط می‌توانند حاوی متن باشند. APIهای دسترس‌پذیری راهی برای نمایش عناصر معنایی موجود در یک `checkbox` ندارند. برای مقابله با این محدودیت، مرورگرها به طور خودکار نقش [`presentation`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/presentation_role) را به تمام عناصر فرزند هر عنصر `checkbox` اعمال می‌کنند، زیرا این نقشی است که از فرزندان معنایی پشتیبانی نمی‌کند.

به عنوان مثال، عنصر `checkbox` زیر را در نظر بگیرید که شامل یک عنوان است.

```html
<div role="checkbox"><h6>Name of my checkbox</h6></div>
```

از آنجایی که فرزندان `checkbox` نمایشی هستند، کد زیر معادل است:

```html
<div role="checkbox"><h6 role="presentation">Name of my checkbox</h6></div>
```

از دیدگاه کاربر فناوری کمکی، عنوان وجود ندارد زیرا قطعه کدهای قبلی با موارد زیر در [درخت دسترس‌پذیری](/en-US/docs/Glossary/Accessibility_tree) معادل هستند:

```html
<div role="checkbox">Name of my checkbox</div>
```

### نقش‌ها، حالت‌ها و ویژگی‌های WAI-ARIA مرتبط

- [`aria-checked`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-checked)
  - : مقدار `aria-checked` وضعیت یک چک‌باکس را تعریف می‌کند. این ویژگی یکی از سه مقدار ممکن را دارد:
    - `true`
      - : چک‌باکس علامت‌خورده است.
    - `false`
      - : چک‌باکس علامت‌نخورده است.
    - `mixed`
      - : چک‌باکس تا حدی علامت‌خورده یا نامشخص است.

- `tabindex="0"`
  - : برای قابل فوکوس کردن آن استفاده می‌شود تا کاربر فناوری کمکی بتواند با کلید Tab به آن برسد و بلافاصله خواندن را شروع کند.

### تعاملات صفحه‌کلید

| کلید              | عملکرد               |
| ---------------- | ---------------------- |
| <kbd>Space</kbd> | چک‌باکس را فعال می‌کند |

### جاوااسکریپت مورد نیاز

#### کنترل‌کننده‌های رویداد مورد نیاز

- `onclick`
  - : کلیک‌های ماوس روی چک‌باکس و برچسب مرتبط را مدیریت می‌کند که وضعیت چک‌باکس را با تغییر مقدار ویژگی `aria-checked` و ظاهر چک‌باکس تغییر می‌دهد تا برای کاربر بینا علامت‌خورده یا علامت‌نخورده به نظر برسد.
- `onKeyDown`
  - : موردی را مدیریت می‌کند که کاربر کلید <kbd>Space</kbd> را فشار می‌دهد تا وضعیت چک‌باکس را با تغییر مقدار ویژگی `aria-checked` و ظاهر چک‌باکس تغییر دهد تا برای کاربر بینا علامت‌خورده یا علامت‌نخورده به نظر برسد.

## مثال‌ها

مثال زیر یک عنصر چک‌باکس غیر معنایی را با استفاده از CSS و جاوااسکریپت ایجاد می‌کند تا وضعیت علامت‌خورده یا علامت‌نخورده عنصر را مدیریت کند.

### HTML

```html
<span
  role="checkbox"
  id="chkPref"
  aria-checked="false"
  tabindex="0"
  aria-labelledby="chk1-label"></span>
<label id="chk1-label">Remember my preferences</label>
```

### CSS

```css
[role="checkbox"] {
  padding: 5px;
}

[role="checkbox"]:focus {
  border: 2px solid #0198e1;
}

[aria-checked="true"]::before {
  content: "[x]";
}

[aria-checked="false"]::before {
  content: "[ ]";
}
```

### JavaScript

```js
const item = document.getElementById("chkPref");
const label = document.getElementById("chk1-label");

function changeCheckbox(code) {
  const checked = item.getAttribute("aria-checked");

  if (code && code !== "Space") {
    return;
  }
  if (checked === "true") {
    item.setAttribute("aria-checked", "false");
  } else {
    item.setAttribute("aria-checked", "true");
  }
}

item.addEventListener("keydown", (event) => {
  changeCheckbox(event.code);
});

label.addEventListener("keydown", (event) => {
  changeCheckbox(event.code);
});

item.addEventListener("click", changeCheckbox);
label.addEventListener("click", changeCheckbox);
```

{{EmbedLiveSample("Examples", 230, 250)}}

## ملاحظات دسترس‌پذیری

هنگامی که نقش `checkbox` به یک عنصر اضافه می‌شود، عامل کاربر باید موارد زیر را انجام دهد:

- عنصر را به عنوان دارای نقش `checkbox` در API دسترس‌پذیری سیستم عامل نشان دهد.
- هنگامی که مقدار `aria-checked` تغییر می‌کند، یک رویداد تغییر حالت قابل دسترس ارسال کند.

محصولات فناوری کمکی باید موارد زیر را انجام دهند:

- صفحه‌خوان‌ها باید عنصر را به عنوان یک چک‌باکس اعلام کنند و در صورت تمایل دستورالعمل‌هایی برای فعال کردن آن ارائه دهند.

افرادی که چک‌باکس‌ها را پیاده‌سازی می‌کنند باید موارد زیر را انجام دهند:

- اطمینان حاصل کنند که چک‌باکس با کنترل‌های صفحه‌کلید و کلیک‌ها قابل دسترسی و تعامل است.
- ویژگی `aria-checked` را پس از تعاملات کاربر به‌روز نگه دارند.
- سبک‌هایی ارائه دهند که نشان دهد چک‌باکس فوکوس دارد.

> [!NOTE]
> نظرات ممکن است در مورد نحوه برخورد فناوری کمکی با این تکنیک متفاوت باشد. اطلاعات ارائه شده در بالا یکی از این نظرات است و ممکن است تغییر کند.

## بهترین روش‌ها

اولین قانون ARIA این است: اگر یک عنصر یا ویژگی بومی HTML دارای معناشناسی و رفتار مورد نیاز شما است، از آن استفاده کنید به جای اینکه یک عنصر را تغییر کاربری داده و یک نقش، حالت یا ویژگی ARIA اضافه کنید تا آن را قابل دسترس کنید. از این رو، توصیه می‌شود از [چک‌باکس HTML](/en-US/docs/Web/HTML/Reference/Elements/input/checkbox) با استفاده از کنترل فرم استفاده کنید به جای بازآفرینی عملکرد یک چک‌باکس با جاوااسکریپت و ARIA.

## همچنین ببینید

- [`<input type="checkbox">`](/en-US/docs/Web/HTML/Reference/Elements/input/checkbox)
- [ARIA: `radio` role](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/radio_role)
- [ARIA: `menuitem` role](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitem_role)
- [ARIA: `menuitemcheckbox` role](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitemcheckbox_role)
- [ARIA: `menuitemradio` role](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitemradio_role)
- [ARIA: `switch` role](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/switch_role)
- [ARIA: `option` role](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/option_role)