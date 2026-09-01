---
title: "HTMLElement: dataset property"
short-title: dataset
slug: Web/API/HTMLElement/dataset
page-type: web-api-instance-property
browser-compat: api.HTMLElement.dataset
---

{{APIRef("HTML DOM")}}

ویژگی فقط‌خواندنی **`dataset`** در رابط {{DOMxRef("HTMLElement")}} دسترسی خواندن/نوشتن به [ویژگی‌های داده سفارشی](/en-US/docs/Web/HTML/Reference/Global_attributes/data-*) (`data-*`) روی عناصر را فراهم می‌کند. این ویژگی یک نقشه از رشته‌ها ({{domxref("DOMStringMap")}}) را با یک ورودی برای هر ویژگی `data-*` ارائه می‌دهد.

> [!NOTE]
> ویژگی `dataset` خودش قابل خواندن است، اما نمی‌توان مستقیماً به آن نوشت. در عوض، تمام نوشته‌ها باید روی ویژگی‌های منفرد درون `dataset` انجام شوند که به نوبه خود نشان‌دهنده ویژگی‌های داده هستند.

## مقدار

یک {{domxref("DOMStringMap")}}.

یک ویژگی HTML `data-*` و ویژگی `dataset.property` متناظر در DOM نام مشترک خود را با توجه به جایی که خوانده یا نوشته می‌شوند تغییر می‌دهند:

- در HTML
  - : نام ویژگی با `data-` شروع می‌شود. فقط می‌تواند شامل حروف، اعداد، خط تیره (`-`)، نقطه (`.`)، دونقطه (`:`) و زیرخط (`_`) باشد. هر حرف بزرگ {{Glossary("ASCII")}} (از `A` تا `Z`) به حروف کوچک تبدیل می‌شود.
- در JavaScript
  - : نام ویژگی یک ویژگی داده سفارشی همان نام ویژگی HTML بدون پیشوند `data-` است. خط تیره‌های تکی (`-`) حذف می‌شوند و کاراکتر ASCII بعد از یک خط تیره حذف شده بزرگ می‌شود تا نام CamelCase شکل بگیرد.

جزئیات و مثال‌های تبدیل بین فرم HTML و JavaScript در بخش بعدی با جزئیات بیشتر توضیح داده شده است.

علاوه بر اطلاعات زیر، یک راهنمای عملی برای استفاده از ویژگی‌های داده HTML در مقاله [_Using data attributes_](/en-US/docs/Web/HTML/How_to/Use_data_attributes) خواهید یافت.

### تبدیل نام

- تبدیل `dash-style` به `camelCase`
  - : یک نام ویژگی داده سفارشی به یک کلید برای ورودی {{domxref("DOMStringMap")}} با مراحل زیر تبدیل می‌شود:
    1. تمام حروف بزرگ ASCII (`A` تا `Z`) را به حروف کوچک تبدیل کنید.
    2. پیشوند `data-` (شامل خط تیره) را حذف کنید.
    3. برای هر خط تیره (`U+002D`) که با یک حرف کوچک ASCII `a` تا `z` دنبال می‌شود، خط تیره را حذف کرده و حرف را بزرگ کنید.
    4. سایر کاراکترها (از جمله خط تیره‌های دیگر) بدون تغییر باقی می‌مانند.

- تبدیل `camelCase` به `dash-style`
  - : تبدیل معکوس که یک کلید را به یک نام ویژگی نگاشت می‌کند، از مراحل زیر استفاده می‌کند:
    1. **محدودیت:** قبل از تبدیل، یک خط تیره _نباید_ بلافاصله با یک حرف کوچک ASCII `a` تا `z` دنبال شود.
    2. پیشوند `data-` را اضافه کنید.
    3. قبل از هر حرف بزرگ ASCII `A` تا `Z` یک خط تیره اضافه کنید، سپس حرف را کوچک کنید.
    4. سایر کاراکترها بدون تغییر باقی می‌مانند.

به عنوان مثال، یک ویژگی `data-abc-def` به `dataset.abcDef` مربوط می‌شود.

### دسترسی به مقادیر

- ویژگی‌ها را می‌توان با نام/کلید CamelCase به عنوان یک ویژگی شیء از dataset تنظیم و خواند: `element.dataset.keyname`.
- ویژگی‌ها را می‌توان با استفاده از نحو براکت نیز تنظیم و خواند: `element.dataset['keyname']`.
- عملگر [`in`](/en-US/docs/Web/JavaScript/Reference/Operators/in) می‌تواند بررسی کند که آیا یک ویژگی خاص وجود دارد: `'keyname' in element.dataset`. توجه داشته باشید که این کار زنجیره [پروتوتایپ](/en-US/docs/Web/JavaScript/Guide/Inheritance_and_the_prototype_chain) `dataset` را طی می‌کند و ممکن است در صورت وجود کد خارجی که زنجیره پروتوتایپ را آلوده کند، ناامن باشد. چندین جایگزین وجود دارد، مانند {{jsxref("Object/hasOwn", "Object.hasOwn(element.dataset, 'keyname')")}}، یا فقط بررسی اینکه `element.dataset.keyname !== undefined`.

### تنظیم مقادیر

- هنگامی که ویژگی تنظیم می‌شود، مقدار آن همیشه به یک رشته تبدیل می‌شود. به عنوان مثال: `element.dataset.example = null` به `data-example="null"` تبدیل می‌شود.
- برای حذف یک ویژگی، می‌توانید از [عملگر `delete`](/en-US/docs/Web/JavaScript/Reference/Operators/delete) استفاده کنید: `delete element.dataset.keyname`.

## مثال‌ها

```html
<div id="user" data-id="1234567890" data-user="carinaanand" data-date-of-birth>
  Carina Anand
</div>
```

```js
const el = document.querySelector("#user");

// el.id === 'user'
// el.dataset.id === '1234567890'
// el.dataset.user === 'carinaanand'
// el.dataset.dateOfBirth === ''

// set a data attribute
el.dataset.dateOfBirth = "1960-10-03";
// Result on JS: el.dataset.dateOfBirth === '1960-10-03'
// Result on HTML: <div id="user" data-id="1234567890" data-user="carinaanand" data-date-of-birth="1960-10-03">Carina Anand</div>

delete el.dataset.dateOfBirth;
// Result on JS: el.dataset.dateOfBirth === undefined
// Result on HTML: <div id="user" data-id="1234567890" data-user="carinaanand">Carina Anand</div>

if (el.dataset.someDataAttr === undefined) {
  el.dataset.someDataAttr = "mydata";
  // Result on JS: 'someDataAttr' in el.dataset === true
  // Result on HTML: <div id="user" data-id="1234567890" data-user="carinaanand" data-some-data-attr="mydata">Carina Anand</div>
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- کلاس ویژگی‌های سراسری HTML [`data-*`](/en-US/docs/Web/HTML/Reference/Global_attributes/data-*)
- [استفاده از ویژگی‌های داده](/en-US/docs/Web/HTML/How_to/Use_data_attributes)
- {{DOMxRef("Element.getAttribute()")}} و {{DOMxRef("Element.setAttribute()")}}