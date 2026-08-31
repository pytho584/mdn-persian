---
title: "ARIA: aria-multiselectable attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-multiselectable"
translated_by: "n8n + AI"
---

---
title: "ARIA: aria-multiselectable attribute"
short-title: aria-multiselectable
slug: Web/Accessibility/ARIA/Reference/Attributes/aria-multiselectable
page-type: aria-attribute
spec-urls: https://w3c.github.io/aria/#aria-multiselectable
sidebar: accessibilitysidebar
---

ویژگی `aria-multiselectable` نشان می‌دهد که کاربر می‌تواند بیش از یک مورد را از بین فرزندان قابل انتخاب فعلی انتخاب کند.

## توضیحات

رفتار پیش‌فرض لیست‌های انتخابی، مانند {{HTMLElement('select')}}، این است که فقط یک مورد یا گزینه قابل انتخاب است. به‌طور پیش‌فرض یا بر اساس قرارداد، وقتی کاربر با لیستی مواجه می‌شود که باید از آن یک مورد را انتخاب کند، فرض می‌کند که فقط می‌تواند یک مورد را انتخاب کند، مگر اینکه اطلاع‌رسانی دیگری شود. ویژگی `aria-multiselectable` روشی است برای اطلاع‌رسانی به کاربران فناوری کمکی که می‌توانند بیش از یک مورد را از بین موارد قابل انتخاب فعلی انتخاب کنند، در صورت تمایل. لیست‌ها و درختان نمونه‌هایی از نقش‌هایی هستند که ممکن است به کاربران اجازه دهند بیش از یک مورد را همزمان انتخاب کنند.

> [!NOTE]
> هنگام اجازه دادن به انتخاب‌های چندگانه، کاربر را از امکان انتخاب چند مقدار مطلع کنید و دستورالعمل‌هایی برای نحوه انتخاب چند مقدار ارائه دهید، مانند "برای انتخاب بیش از یک مقدار، کلید کنترل را در حین انتخاب نگه دارید."

### استفاده با `aria-selected`

وقتی کاربر یک یا چند مورد را انتخاب می‌کند، به یاد داشته باشید که فرزندان انتخاب‌شده را با [`aria-selected="true"`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-selected) به عنوان انتخاب‌شده علامت‌گذاری کنید، و فرزندان قابل انتخاب که انتخاب نشده‌اند دارای `aria-selected="false"` باشند. اگر یک عنصر قابل انتخاب نیست، به‌کلی ویژگی `aria-selected` را حذف کنید، زیرا وجود آن به کاربر اطلاع می‌دهد که آیتم قابل انتخاب است.

اگر یک درخت، شبکه، لیست زبانه‌ها یا جعبه لیست از انتخاب بیش از یک گره پشتیبانی می‌کند، عنصری با نقش [`grid`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/grid_role)، [`listbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/listbox_role)، [`tablist`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tablist_role) یا [`tree`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tree_role) دارای `aria-multiselectable` با مقدار `true` است. در غیر این صورت، `aria-multiselectable` یا روی `false` تنظیم می‌شود یا مقدار پیش‌فرض false ضمنی است.

## مثال

```html
<p id="colorOptions">رنگ‌های پرچم خود را انتخاب کنید.</p>
<ul
  tabindex="0"
  role="listbox"
  aria-labelledby="colorOptions"
  aria-multiselectable="true">
  <li id="red" role="option" aria-selected="false">قرمز</li>
  <li id="orange" role="option" aria-selected="false">نارنجی</li>
  <li id="yellow" role="option" aria-selected="false">زرد</li>
  <li id="green" role="option" aria-selected="false">سبز</li>
  <li id="blue" role="option" aria-selected="false">آبی</li>
  <li id="purple" role="option" aria-selected="false">بنفش</li>
  <li id="magenta" role="option" aria-selected="false">صورتی تند</li>
  <li id="lightpink" role="option" aria-selected="true">صورتی روشن</li>
  <li id="white" role="option" aria-selected="true">سفید</li>
  <li id="lightblue" role="option" aria-selected="true">آبی روشن</li>
  <li id="black" role="option" aria-selected="false">سیاه</li>
  <li id="brown" role="option" aria-selected="false">قهوه‌ای</li>
</ul>
```

این جعبه لیست از انتخاب چندگانه پشتیبانی می‌کند، بنابراین عنصر با نقش `listbox` را با `aria-multiselectable="true"` تنظیم می‌کنیم. تمام گزینه‌های انتخاب‌شده دارای `aria-selected` با مقدار `true` هستند. تمام گزینه‌هایی که انتخاب نشده‌اند اما قابل انتخاب هستند، دارای `aria-selected` با مقدار `false` هستند. اگر گزینه‌هایی را شامل می‌کردیم که غیرفعال یا غیرقابل انتخاب بودند، ویژگی `aria-selected` را به‌کلی حذف می‌کردیم. گنجاندن ویژگی، حتی بدون مقدار یا با مقدار صریح `false`، به کاربران فناوری کمکی نشان می‌دهد که آیتم قابل انتخاب است.

اولین قانون استفاده از ARIA این است: "اگر می‌توانید از یک ویژگی بومی با معناشناسی و رفتاری که نیاز دارید استفاده کنید، به جای تغییر کاربری یک عنصر و **افزودن** نقش، حالت یا ویژگی ARIA برای دسترسی‌پذیر کردن آن، این کار را انجام دهید." به جای ایجاد یک لیست نامرتب که نیاز به [`tabindex`](/en-US/docs/Web/HTML/Reference/Global_attributes/tabindex)، ARIA و جاوااسکریپت برای تبدیل متن به گزینه‌های قابل انتخاب دارد، می‌توانستیم از یک انتخاب چندگانه بومی استفاده کنیم: عنصر {{htmlelement('select')}} دارای یک ویژگی بولی [`multiple`](/en-US/docs/Web/HTML/Reference/Elements/select#multiple) است. اگر شامل شود، کاربر می‌تواند چندین گزینه را انتخاب کند. اگر نه، فقط یک گزینه قابل انتخاب است.

```html
<label for="flagcolors"> رنگ‌های پرچم خود را انتخاب کنید. </label>
<select multiple id="flagcolors">
  <option value="red">قرمز</option>
  <option value="orange">نارنجی</option>
  <option value="yellow">زرد</option>
  <option value="green">سبز</option>
  <option value="blue">آبی</option>
  <option value="purple">بنفش</option>
  <option value="magenta">صورتی تند</option>
  <option value="lightpink" selected>صورتی روشن</option>
  <option value="white" selected>سفید</option>
  <option value="lightblue" selected>آبی روشن</option>
  <option value="black">سیاه</option>
  <option value="brown">قهوه‌ای</option>
</select>
```

این نسخه `<select>` HTML دسترسی‌پذیر و تعاملی است و نیازی به ARIA یا جاوااسکریپت برای عملکرد ندارد.

اگر موارد بالا مطابق سلیقه شما قابل استایل‌دهی نیستند، می‌توانید با چک‌باکس‌های HTML نیز لیستی از گزینه‌های قابل انتخاب ایجاد کنید، که همچنین معنایی، قابل تمرکز و با CSS بی‌نهایت قابل استایل‌دهی است:

```html
<fieldset>
  <legend>رنگ‌های پرچم خود را انتخاب کنید.</legend>
  <ul>
    <li>
      <label><input type="checkbox" name="fc" value="red" />قرمز</label>
    </li>
    <li>
      <label><input type="checkbox" name="fc" value="orange" />نارنجی</label>
    </li>
    <li>
      <label><input type="checkbox" name="fc" value="yellow" />زرد</label>
    </li>
    <li>
      <label><input type="checkbox" name="fc" value="green" />سبز</label>
    </li>
    <li>
      <label><input type="checkbox" name="fc" value="blue" />آبی</label>
    </li>
    <li>
      <label><input type="checkbox" name="fc" value="purple" />بنفش</label>
    </li>
    <li>
      <label><input type="checkbox" name="fc" value="magenta" />صورتی تند</label>
    </li>
    <li>
      <label
        ><input type="checkbox" name="fc" value="lightpink" checked />صورتی
        روشن</label
      >
    </li>
    <li>
      <label
        ><input type="checkbox" name="fc" value="white" checked />سفید</label
      >
    </li>
    <li>
      <label
        ><input type="checkbox" name="fc" value="lightblue" checked />آبی
        روشن</label
      >
    </li>
    <li>
      <label><input type="checkbox" name="fc" value="black" />سیاه</label>
    </li>
    <li>
      <label><input type="checkbox" name="fc" value="brown" />قهوه‌ای</label>
    </li>
  </ul>
</fieldset>
```

به جای `aria-selected="true"`، ویژگی [`checked`](/en-US/docs/Web/HTML/Reference/Elements/input/checkbox#checked) را شامل کنید. مرورگر بقیه کار را انجام می‌دهد.

## مقادیر

- `true`
  - : بیش از یک مورد در ویجت ممکن است همزمان انتخاب شوند.
- `false`
  - : فقط یک مورد می‌تواند انتخاب شود.

## رابط‌های مرتبط

- {{domxref("Element.ariaMultiSelectable")}}
  - : ویژگی [`ariaMultiSelectable`](/en-US/docs/Web/API/Element/ariaMultiSelectable)، بخشی از رابط {{domxref("Element")}}، مقدار ویژگی `aria-multiselectable` را منعکس می‌کند.
- {{domxref("ElementInternals.ariaMultiSelectable")}}
  - : ویژگی [`ariaMultiSelectable`](/en-US/docs/Web/API/ElementInternals/ariaMultiSelectable)، بخشی از رابط {{domxref("ElementInternals")}}، مقدار ویژگی `aria-multiselectable` را منعکس می‌کند.

## نقش‌های مرتبط

مورد استفاده در نقش‌ها:

- [`grid`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/grid_role)
- [`listbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/listbox_role)
- [`tablist`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tablist_role)
- [`tree`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tree_role)

به ارث برده شده در نقش‌ها:

- [`treegrid`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/treegrid_role)

## مشخصات

{{Specifications}}

## همچنین ببینید

- عنصر HTML {{HTMLElement('select')}}
- عنصر HTML {{HTMLElement('option')}}
- عنصر HTML {{HTMLElement('input')}}
- ویژگی [`multiple`](/en-US/docs/Web/HTML/Reference/Attributes/multiple)
- [`aria-selected`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-selected)