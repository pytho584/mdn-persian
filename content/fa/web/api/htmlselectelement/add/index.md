---
title: "HTMLSelectElement: add() method"
---

---
title: "HTMLSelectElement: add() method"
short-title: add()
slug: Web/API/HTMLSelectElement/add
page-type: web-api-instance-method
browser-compat: api.HTMLSelectElement.add
---

{{APIRef("HTML DOM")}}

متد **`HTMLSelectElement.add()`** یک عنصر را به مجموعه عناصر `option` برای این عنصر `select` اضافه می‌کند.

## سینتکس

```js-nolint
add(item)
add(item, before)
```

### پارامترها

- `item`
  - : یک {{domxref("HTMLOptionElement")}} یا {{domxref("HTMLOptGroupElement")}}.
- `before` {{optional_inline}}
  - : یک عنصر از مجموعه، یا یک اندیس از نوع _long_، که نشان می‌دهد _item_ باید قبل از آن درج شود. اگر این پارامتر `null` باشد (یا اندیس وجود نداشته باشد)، عنصر جدید به انتهای مجموعه اضافه می‌شود.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### استثناها

- `HierarchyRequestError` {{DOMxRef("DOMException")}}
  - : زمانی پرتاب می‌شود که _item_ ارسال‌شده به متد، یکی از اجداد (ancestor) {{domxref("HTMLSelectElement")}} باشد.

## مثال‌ها

### ایجاد عناصر از ابتدا

```js
const sel = document.createElement("select");
const opt1 = document.createElement("option");
const opt2 = document.createElement("option");

opt1.value = "1";
opt1.text = "Option: Value 1";

opt2.value = "2";
opt2.text = "Option: Value 2";

sel.add(opt1, null);
sel.add(opt2, null);

/*
  Produces the following, conceptually:

  <select>
    <option value="1">Option: Value 1</option>
    <option value="2">Option: Value 2</option>
  </select>
*/
```

پارامتر before اختیاری است. بنابراین کد زیر نیز پذیرفته می‌شود.

```js
sel.add(opt1);
sel.add(opt2);
```

### افزودن به یک مجموعه موجود

```js
const sel = document.getElementById("existingList");

const opt = document.createElement("option");
opt.value = "3";
opt.text = "Option: Value 3";

sel.add(opt, null);

/*
  Takes the existing following select object:

  <select id="existingList">
    <option value="1">Option: Value 1</option>
    <option value="2">Option: Value 2</option>
  </select>

  And changes it to:

  <select id="existingList">
    <option value="1">Option: Value 1</option>
    <option value="2">Option: Value 2</option>
    <option value="3">Option: Value 3</option>
  </select>
*/
```

پارامتر before اختیاری است. بنابراین کد زیر نیز پذیرفته می‌شود.

```js
sel.add(opt);
```

### درج در یک مجموعه موجود

```js
const sel = document.getElementById("existingList");

const opt = document.createElement("option");
opt.value = "3";
opt.text = "Option: Value 3";

sel.add(opt, sel.options[1]);

/*
  Takes the existing following select object:

  <select id="existingList">
    <option value="1">Option: Value 1</option>
    <option value="2">Option: Value 2</option>
  </select>

  And changes it to:

  <select id="existingList">
    <option value="1">Option: Value 1</option>
    <option value="3">Option: Value 3</option>
    <option value="2">Option: Value 2</option>
  </select>
*/
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}