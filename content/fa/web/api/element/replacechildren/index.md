---
title: "Element: replaceChildren() method"
short-title: replaceChildren()
slug: Web/API/Element/replaceChildren
page-type: web-api-instance-method
browser-compat: api.Element.replaceChildren
---

{{APIRef("DOM")}}

روش **`Element.replaceChildren()`** فرزندان موجود یک {{domxref("Node")}} را با مجموعه‌ای جدید از فرزندان مشخص شده جایگزین می‌کند. این فرزندان می‌توانند رشته‌ها یا اشیاء {{domxref("Node")}} باشند.

## نحو

```js-nolint
replaceChildren(param1)
replaceChildren(param1, param2)
replaceChildren(param1, param2, /* …, */ paramN)
```

### پارامترها

- `param1`, …, `paramN`
  - : مجموعه‌ای از اشیاء {{domxref("Node")}} یا رشته‌ها برای جایگزینی فرزندان موجود `Element`. اگر هیچ شیء جایگزینی مشخص نشود، `Element` از تمام گره‌های فرزند خالی می‌شود.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### استثناها

- `HierarchyRequestError` {{DOMxRef("DOMException")}}
  - : زمانی پرتاب می‌شود که [محدودیت‌های درخت گره](https://dom.spec.whatwg.org/#concept-node-tree) نقض شده باشند.

## مثال‌ها

### خالی کردن یک گره

`replaceChildren()` یک مکانیسم بسیار راحت برای خالی کردن یک گره از تمام فرزندانش فراهم می‌کند. شما آن را روی گره والد بدون هیچ آرگومانی فراخوانی می‌کنید:

```js
myNode.replaceChildren();
```

### انتقال گره‌ها بین عناصر

`replaceChildren()` به شما امکان می‌دهد تا به راحتی گره‌ها را بین عناصر انتقال دهید، بدون نیاز به استفاده از کدهای حلقه‌ای طولانی. به عنوان مثال، فرض کنید یک برنامه ساده داریم که به شما امکان می‌دهد غذای مورد نظر خود را برای مهمانی انتخاب کنید. این HTML ممکن است چیزی شبیه به این باشد:

```html
<h2>لیست گزینه‌های غذای مهمانی</h2>

<main>
  <div>
    <label for="no">نه، ممنون!</label>

    <select id="no" multiple size="10">
      <option>سیب</option>
      <option>پرتقال</option>
      <option>انگور</option>
      <option>موز</option>
      <option>کیوی</option>
      <option>کوکی شکلاتی</option>
      <option>کوکی بادام‌زمینی</option>
      <option>شکلات تخته‌ای</option>
      <option>ساندویچ ژامبون</option>
      <option>ساندویچ پنیر</option>
      <option>ساندویچ فلافل</option>
      <option>بستنی</option>
      <option>ژله</option>
      <option>چوب هویج و حمص</option>
      <option>پیتزا مارگاریتا</option>
      <option>پیتزا پپرونی</option>
      <option>پیتزای گیاهی وگان</option>
    </select>
  </div>

  <div class="buttons">
    <button id="to-yes">انتقال به "بله" --&gt;</button>
    <button id="to-no">&lt;-- انتقال به "نه"</button>
  </div>

  <div>
    <label for="yes">بله، لطفا!</label>

    <select id="yes" multiple size="10"></select>
  </div>
</main>
```

منطقی است که از CSS ساده برای چیدمان دو لیست انتخابی در کنار هم با دکمه‌های کنترل بین آنها استفاده کنیم:

```css
main {
  display: flex;
}

div {
  margin-right: 20px;
}

label,
button {
  display: block;
}

.buttons {
  display: flex;
  flex-flow: column;
  justify-content: center;
}

select {
  width: 200px;
}
```

کاری که می‌خواهیم انجام دهیم این است که گزینه‌های انتخاب شده در لیست "نه" را با فشار دادن دکمه "بله" به لیست "بله" منتقل کنیم و گزینه‌های انتخاب شده در لیست "بله" را با فشار دادن دکمه "نه" به لیست "نه" منتقل کنیم.

برای این کار، به هر یک از دکمه‌ها یک رویدادگردان کلیک می‌دهیم که گزینه‌های انتخاب شده را برای انتقال در یک ثابت و گزینه‌های موجود در لیست مقصد را در ثابت دیگر جمع‌آوری می‌کند. سپس `replaceChildren()` را روی لیست مقصد فراخوانی می‌کند و با استفاده از عملگر spread تمام گزینه‌های موجود در هر دو ثابت را به آن منتقل می‌کند.

```js
const noSelect = document.getElementById("no");
const yesSelect = document.getElementById("yes");
const noBtn = document.getElementById("to-no");
const yesBtn = document.getElementById("to-yes");

yesBtn.addEventListener("click", () => {
  const selectedTransferOptions =
    document.querySelectorAll("#no option:checked");
  const existingYesOptions = document.querySelectorAll("#yes option");
  yesSelect.replaceChildren(...selectedTransferOptions, ...existingYesOptions);
});

noBtn.addEventListener("click", () => {
  const selectedTransferOptions = document.querySelectorAll(
    "#yes option:checked",
  );
  const existingNoOptions = document.querySelectorAll("#no option");
  noSelect.replaceChildren(...selectedTransferOptions, ...existingNoOptions);
});
```

نتیجه نهایی به این شکل است:

{{EmbedLiveSample('Transferring_nodes_between_elements', '100%', '350')}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Element.prepend()")}}
- {{domxref("Element.append()")}}
- {{domxref("NodeList")}}