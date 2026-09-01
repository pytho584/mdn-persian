---
title: "Element: ariaOwnsElements property"
short-title: ariaOwnsElements
slug: Web/API/Element/ariaOwnsElements
page-type: web-api-instance-property
browser-compat: api.Element.ariaOwnsElements
---

{{APIRef("DOM")}}

خصوصیت **`ariaOwnsElements`** در رابط {{domxref("Element")}} آرایه‌ای شامل عنصر (یا عناصر) است که رابطهٔ بصری، عملکردی، یا زمینه‌ای بین یک عنصر والد که این خصوصیت روی آن اعمال شده و عناصر فرزندش را تعریف می‌کند.
زمانی از این خصوصیت استفاده می‌شود که نتوان از سلسله‌مراتب DOM برای نمایش این رابطه استفاده کرد و در غیر این صورت این رابطه برای فناوری‌های کمکی در دسترس نخواهد بود.

مقالهٔ [`aria-owns`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-owns) اطلاعات بیشتری دربارهٔ نحوهٔ استفاده از این ویژگی (attribute) و این خصوصیت (property) ارائه می‌دهد.

## مقدار

آرایه‌ای از زیرکلاس‌های {{domxref("HTMLElement")}}.

هنگام خواندن، آرایهٔ بازگشتی ایستا و فقط‌خواندنی است. هنگام نوشتن، آرایهٔ انتساب‌داده‌شده کپی می‌شود؛ تغییرات بعدی روی آرایه، بر مقدار این خصوصیت تأثیری ندارند.

## توضیحات

این خصوصیت جایگزینی انعطاف‌پذیر برای استفاده از ویژگی [`aria-owns`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-owns) به‌منظور نشان‌دادن مالکیت یک عنصر است. برخلاف `aria-owns`، عناصری که به این خصوصیت اختصاص می‌یابند لزومی ندارد ویژگی [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id) داشته باشند.

این خصوصیت ویژگی [`aria-owns`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-owns) عنصر را هنگام تعریف‌شدن بازتاب می‌دهد، اما فقط برای مقادیر ارجاعی `id` فهرست‌شده‌ای که با عناصر معتبر درون‌حوزه (in-scope) مطابقت دارند. اگر این خصوصیت تنظیم شده باشد، ویژگی متناظر پاک می‌شود. برای اطلاعات بیشتر دربارهٔ ارجاع عناصر بازتاب‌شده و حوزهٔ کاربرد، به [ارجاع عناصر بازتاب‌شده](/en-US/docs/Web/API/Document_Object_Model/Reflected_attributes#reflected_element_references) در راهنمای _ویژگی‌های بازتاب‌شده_ مراجعه کنید.

## مثال‌ها

### دریافت عنصر تحت مالکیت

این مثال نحوهٔ استفاده از ویژگی `aria-owns` و خصوصیت متناظر با آن را نشان می‌دهد.

کد، یک منو و زیرمنوی مرتبط با آن را در دو عنصر {{htmlelement("div")}} جدا و غیرتوئوتو تعریف می‌کند. از آنجا که این عناصر تودرتو نیستند، رابطهٔ مالکیت بین منو و زیرمنو توسط DOM ثبت نمی‌شود. در این‌جا این اطلاعات را با استفاده از ویژگی `aria-owns` در اختیار ابزارهای کمکی قرار می‌دهیم؛ اما می‌توانستیم این کار را با استفاده از خصوصیت بازتاب‌شده نیز انجام دهیم.

توجه کنید که می‌توانستیم منویی بسازیم که زیرمنو در آن تودرتو باشد؛ این مثال عامدانه چنین ساخته شده است تا حالتی را نشان دهد که رابطه باید به‌صراحت تعریف شود.

#### HTML

اچ‌تی‌ام‌ال عناصر {{htmlelement("div")}} را برای منو با `id=parentMenu` و برای زیرمنو با `id="subMenu1"` تعریف می‌کند. ما یک `<div>` در بین آن‌ها اضافه کرده‌ایم تا واضح‌تر شود که هیچ مدل مالکیت مستقیمی در DOM تعریف نشده است.

`<div>` منوی والد شامل ویژگی `aria-owns="subMenu1"` است تا این رابطهٔ مالکیت ایجاد شود.

```html
<div class="menu" id="parentMenu" role="menubar" aria-owns="subMenu1">
  Top level menu (hover over)
</div>

<div>Some other element</div>

<div class="submenu" id="subMenu1" role="menu">
  <a href="#" role="menuitem">Menu item 1</a>
  <a href="#" role="menuitem">Menu item 2</a>
  <a href="#" role="menuitem">Menu item 3</a>
</div>
```

#### CSS

سی‌اس‌اس استایل منو و زیرمنو را تنظیم می‌کند و زیرمنو را هنگام hover کردن روی منو نمایش می‌دهد.

```css
.menu {
  position: relative;
  display: inline-block;
  color: purple;
}

.submenu {
  display: none;
  position: absolute;
  background-color: #f9f9f9;
  min-width: 160px;
  box-shadow: 0px 6px 14px 0px rgb(0 0 0 / 0.2);
  z-index: 1;
  top: 20px;
  left: 0;
}

.menu:hover ~ .submenu {
  display: block;
}

.submenu a {
  color: black;
  padding: 12px 16px;
  text-decoration: none;
  display: block;
}

.submenu a:hover {
  background-color: #f1f1f1;
}
```

```html hidden
<pre id="log"></pre>
```

```css hidden
#log {
  height: 80px;
  overflow: scroll;
  padding: 0.5rem;
  margin: 5px;
  border: 1px solid black;
}
```

#### JavaScript

کد ابتدا بررسی می‌کند که آیا `ariaOwnsElements` پشتیبانی می‌شود یا خیر. اگر پشتیبانی شود، ویژگی، عناصر موجود در خصوصیت، و مقدار `id` هر عنصر را در لاگ می‌نویسیم.

```js hidden
const logElement = document.querySelector("#log");
function log(text) {
  logElement.innerText = `${logElement.innerText}${text}\n`;
  logElement.scrollTop = logElement.scrollHeight;
}
```

```js
// Feature test for ariaOwnsElements
if ("ariaOwnsElements" in Element.prototype) {
  const parentMenu = document.querySelector("#parentMenu");
  log(`parentMenu.getAttribute(): ${parentMenu.getAttribute("aria-owns")}`);
  log(`parentMenu.ariaOwnsElements: ${parentMenu.ariaOwnsElements}`);
  parentMenu.ariaOwnsElements?.forEach((elem) => {
    log(`  id: ${elem.id}`);
  });
} else {
  log("element.ariaOwnsElements: not supported by browser");
}
```

#### نتیجه

نتیجهٔ اجرای کد در زیر نمایش داده شده است. لاگ نشان می‌دهد که رابطهٔ تعریف‌شده با ویژگی `aria-owns` در خصوصیت `ariaOwnsElements` بازتاب یافته است (عناصر موجود در آرایه با ارجاع‌های عنصری ویژگی مطابقت دارند).

{{EmbedLiveSample("Get the flow-to element","100%","200px")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- ویژگی [`aria-owns`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-flowto)
- {{domxref("ElementInternals.ariaOwnsElements")}}
- [ارجاع عناصر بازتاب‌شده](/en-US/docs/Web/API/Document_Object_Model/Reflected_attributes#reflected_element_references) در راهنمای _بازتاب ویژگی‌ها_.