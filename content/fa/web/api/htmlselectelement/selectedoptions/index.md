---
title: "HTMLSelectElement: selectedOptions property"
short-title: selectedOptions
slug: Web/API/HTMLSelectElement/selectedOptions
page-type: web-api-instance-property
browser-compat: api.HTMLSelectElement.selectedOptions
---

{{APIRef("HTML DOM")}}

ویژگی **`selectedOptions`** از {{domxref("HTMLSelectElement")}} (که **فقط خواندنی** است) شامل لیستی از عناصر {{HTMLElement("option")}} موجود در عنصر {{HTMLElement("select")}} است که در حال حاضر انتخاب شده‌اند. لیست گزینه‌های انتخاب شده یک شیء {{domxref("HTMLCollection")}} است که برای هر گزینه انتخاب شده یک ورودی دارد.

یک گزینه در صورتی انتخاب شده در نظر گرفته می‌شود که دارای ویژگی {{domxref("HTMLOptionElement.selected")}} باشد.

## مقدار

یک {{domxref("HTMLCollection")}} که هر {{domxref("HTMLOptionElement")}} انتخاب شده را فهرست می‌کند که یا فرزند مستقیم {{domxref("HTMLSelectElement")}} باشد یا فرزند یک {{domxref("HTMLOptGroupElement")}} درون عنصر `<select>`.

به عبارت دیگر، هر گزینه‌ای که درون عنصر `<select>` قرار دارد ممکن است بخشی از نتایج باشد، اما گروه‌های گزینه (option groups) در لیست گنجانده نمی‌شوند.

اگر هیچ گزینه‌ای در حال حاضر انتخاب نشده باشد، مجموعه خالی است و یک {{domxref("HTMLCollection.length", "length")}} برابر ۰ برمی‌گرداند.

## مثال‌ها

در این مثال، از یک عنصر {{HTMLElement("select")}} با تعدادی گزینه استفاده شده است تا کاربر بتواند اقلام غذایی مختلفی را سفارش دهد.

### HTML

HTML که جعبه انتخاب و عناصر {{HTMLElement("option")}} نماینده هر یک از انتخاب‌های غذایی را ایجاد می‌کند به صورت زیر است:

```html
<label for="foods">What do you want to eat?</label><br />
<select id="foods" name="foods" size="7" multiple>
  <option value="1">Burrito</option>
  <option value="2">Cheeseburger</option>
  <option value="3">Double Bacon Burger Supreme</option>
  <option value="4">Pepperoni Pizza</option>
  <option value="5">Taco</option>
</select>
<br />
<button name="order" id="order">Order Now</button>
<p id="output"></p>
```

عنصر `<select>` به گونه‌ای تنظیم شده است که امکان انتخاب چندین آیتم را فراهم کند و ۷ ردیف ارتفاع دارد. همچنین به {{HTMLElement("button")}} توجه کنید که نقش آن فعال‌سازی دریافت {{domxref("HTMLCollection")}} از عناصر انتخاب شده با استفاده از ویژگی `selectedOptions` است.

### JavaScript

کد JavaScript که رویدادگردان (event handler) دکمه را تنظیم می‌کند و همچنین خود رویدادگردان به صورت زیر است:

```js
let orderButton = document.getElementById("order");
let itemList = document.getElementById("foods");
let outputBox = document.getElementById("output");

orderButton.addEventListener("click", () => {
  let collection = itemList.selectedOptions;
  let output = "";

  for (let i = 0; i < collection.length; i++) {
    if (output === "") {
      output = "Your order for the following items has been placed: ";
    }
    output += collection[i].label;

    if (i === collection.length - 2 && collection.length < 3) {
      output += " and ";
    } else if (i < collection.length - 2) {
      output += ", ";
    } else if (i === collection.length - 2) {
      output += ", and ";
    }
  }

  if (output === "") {
    output = "You didn't order anything!";
  }

  outputBox.textContent = output;
});
```

این اسکریپت یک شنونده رویداد {{domxref("Element/click_event", "click")}} روی دکمه «Order Now» تنظیم می‌کند. هنگام کلیک، رویدادگردان لیست گزینه‌های انتخاب شده را با استفاده از `selectedOptions` دریافت می‌کند، سپس روی گزینه‌های موجود در لیست پیمایش می‌کند. یک رشته برای فهرست کردن اقلام سفارش داده شده ساخته می‌شود، با منطقی برای ساخت لیست با استفاده از قواعد گرامر صحیح انگلیسی (شامل [کاما سریال](https://en.wikipedia.org/wiki/Serial_comma)).

### نتیجه

محتوای حاصل در عمل به این صورت است:

{{EmbedLiveSample("Examples", 600, 250)}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [کنترل‌های کشویی (Drop-down controls)](/en-US/docs/Learn_web_development/Extensions/Forms/Other_form_controls#drop-down_controls)