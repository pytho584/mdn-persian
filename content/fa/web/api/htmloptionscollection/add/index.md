---
title: "HTMLOptionsCollection: add() method"
short-title: add()
slug: Web/API/HTMLOptionsCollection/add
page-type: web-api-instance-method
browser-compat: api.HTMLOptionsCollection.add
---

{{APIRef("HTML DOM")}}

متد **`add()`** از رابط {{DOMxRef("HTMLOptionsCollection")}} یک {{domxref("HTMLOptionElement")}} یا {{domxref("HTMLOptGroupElement")}} را به این `HTMLOptionsCollection` اضافه می‌کند.

## نحو

```js-nolint
add(item)
add(item, before)
```

### پارامترها

- `item`
  - : یک {{domxref("HTMLOptionElement")}} یا {{domxref("HTMLOptGroupElement")}}.
- `before` {{optional_inline}}
  - : یک عنصر از مجموعه، یا یک اندیس عددی مبتنی بر ۰ که نشان‌دهنده عنصری است که `item` باید قبل از آن درج شود. اگر حذف شود، `null` باشد، یا اندیس وجود نداشته باشد، عنصر جدید به انتهای مجموعه اضافه می‌شود.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

### استثناها

- `HierarchyRequestError` {{DOMxRef("DOMException")}}
  - : اگر `item` ارسال‌شده به متد، نیای عنصری باشد که قرار است در آن درج شود، این خطا پرتاب می‌شود.

## توضیحات

به‌طور پیش‌فرض، متد `add()` عنصر {{HTMLelement("option")}} یا {{HTMLelement("optgroup")}} که به عنوان پارامتر ارسال شده است را به انتهای مجموعه اضافه می‌کند. می‌توانید با تعیین پارامتر `before` مشخص کنید که `<option>` یا `<optgroup>` اضافه‌شده کجا قرار گیرد. `before` می‌تواند یک عنصر `<option>` یا یک اندیس عددی مبتنی بر ۰ از عنصر `<option>` باشد که عنصر اضافه‌شده باید قبل از آن قرار گیرد.

اگر پارامتر `before` null باشد یا خارج از محدوده باشد (یا حذف شود)، `<option>` یا `<optgroup>` به عنوان آخرین عنصر در مجموعه، خارج از هر {{HTMLelement("optgroup")}} اضافه می‌شود. اگر `<option>` که توسط پارامتر `before` ارجاع داده شده است درون یک {{HTMLelement("optgroup")}} باشد، `HTMLOptionElement` اضافه‌شده در همان گروه قرار می‌گیرد.

عنصر `<optgroup>` فقط می‌تواند حاوی عناصر `<option>` به عنوان گره‌های فرزند باشد. متد `add()` فقط می‌تواند یک `HTMLOptGroupElement` را با موفقیت به انتهای `HTMLOptionsCollection` یا بین عناصر `<optgroup>` اضافه کند. به عبارت دیگر، تلاش برای اضافه کردن یک `HTMLOptGroupElement` قبل از یک `<option>` درون یک `<optgroup>` ممکن است بی‌صدا شکست بخورد اگر `<option>` که توسط پارامتر `before` ارجاع داده شده است اولین `<option>` درون `<optgroup>` خود نباشد.

## مثال‌ها

```js
const optionList = document.querySelector("select").options;
const firstOption = document.createElement("option");
firstOption.text = "new item";
optionList.add(firstOption, 0); // added as the first item
optionList.add(optionList[0]); // moves the first item to the end
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{HTMLElement("select")}}
- {{DOMxRef("HTMLOptionsCollection.remove")}}
- {{DOMxRef("HTMLOptionsCollection.length")}}
- {{DOMxRef("HTMLOptionsCollection.selectedIndex")}}