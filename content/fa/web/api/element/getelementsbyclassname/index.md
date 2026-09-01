---
title: "Element: getElementsByClassName() method"
short-title: getElementsByClassName()
slug: Web/API/Element/getElementsByClassName
page-type: web-api-instance-method
browser-compat: api.Element.getElementsByClassName
---

{{APIRef("DOM")}}

متد {{domxref("Element")}} با نام **`getElementsByClassName()`** یک {{domxref("HTMLCollection")}} زنده (live) برمی‌گرداند که شامل تمام عناصر فرزند (descendant) است که نام کلاس یا کلاس‌های مشخص‌شده را دارند.

متد {{domxref("Document.getElementsByClassName", "getElementsByClassName()")}} در رابط {{domxref("Document")}} تقریباً به همین صورت کار می‌کند، با این تفاوت که روی کل سند و از ریشه سند (document root) اعمال می‌شود.

## Syntax

```js-nolint
getElementsByClassName(names)
```

### Parameters

- `names`
  - : یک رشته شامل یک یا چند نام کلاس که با فاصله از هم جدا شده‌اند.

### Return value

یک {{domxref("HTMLCollection")}} که فهرستی به‌روز شونده (live-updating) از تمام عناصر عضو هر کلاس در `names` ارائه می‌دهد.

## Usage notes

همانند همیشه، مجموعه بازگشتی _زنده (live)_ است، به این معنی که همیشه وضعیت فعلی درخت DOM ریشه‌شده در عنصری که تابع روی آن فراخوانی شده را منعکس می‌کند. به محض اینکه عناصر جدیدی که با `names` مطابقت دارند به زیردرخت اضافه شوند، بلافاصله در مجموعه ظاهر می‌شوند. به همین ترتیب، اگر یک عنصر موجود که با `names` مطابقت ندارد، مجموعه کلاس‌هایش طوری تنظیم شود که مطابقت پیدا کند، بلافاصله در مجموعه ظاهر می‌شود.

عکس این نیز صادق است: به محض اینکه عناصر دیگر با مجموعه نام‌ها مطابقت نداشته باشند، بلافاصله از مجموعه حذف می‌شوند.

> [!NOTE]
> در [حالت quirks](/en-US/docs/Web/HTML/Guides/Quirks_mode_and_standards_mode)، نام کلاس‌ها به صورت غیرحساس به بزرگی/کوچکی حروف (case-insensitive) مقایسه می‌شوند. در غیر این صورت، به حروف حساس هستند.

## Examples

### Matching a single class

برای جستجوی عناصری که در میان کلاس‌های خود یک کلاس مشخص را دارند، کافی است هنگام فراخوانی `getElementsByClassName()` آن نام کلاس را ارائه دهیم:

```js
element.getElementsByClassName("test");
```

این مثال تمام عناصری را پیدا می‌کند که کلاس `test` دارند و همچنین فرزند عنصری هستند که `id` برابر `main` دارد:

```js
document.getElementById("main").getElementsByClassName("test");
```

### Matching multiple classes

برای یافتن عناصری که فهرست کلاس‌هایشان شامل هر دو کلاس `red` و `test` است:

```js
element.getElementsByClassName("red test");
```

### Examining the results

می‌توانید از متد {{domxref("HTMLCollection.item", "item()")}} روی `HTMLCollection` بازگشتی یا از نحو آرایه استاندارد برای بررسی عناصر منفرد در مجموعه استفاده کنید. با این حال، کد زیر آنطور که انتظار می‌رود کار نخواهد کرد زیرا `"matches"` به محض حذف هر کلاس `"color-box"` تغییر می‌کند.

```js
const matches = element.getElementsByClassName("color-box");

for (let i = 0; i < matches.length; i++) {
  matches[i].classList.remove("color-box");
  matches.item(i).classList.add("hue-frame");
}
```

در عوض، از روش دیگری مانند زیر استفاده کنید:

```js
const matches = element.getElementsByClassName("color-box");

while (matches.length > 0) {
  matches.item(0).classList.add("hue-frame");
  matches[0].classList.remove("color-box");
}
```

این کد عناصر فرزند دارای کلاس `"color-box"` را پیدا می‌کند، با فراخوانی `item(0)` کلاس `"hue-frame"` را اضافه می‌کند و سپس `"color-box"` را (با استفاده از نماد آرایه) حذف می‌کند. عنصر دیگری (اگر باقی مانده باشد) سپس به `item(0)` تبدیل می‌شود.

### Filtering the results using array methods

همچنین می‌توانیم از متدهای {{jsxref("Array")}} روی هر {{domxref("HTMLCollection")}} با ارسال {{domxref("HTMLCollection")}} به عنوان مقدار `this` متد استفاده کنیم. در اینجا تمام عناصر {{HTMLElement("div")}} را که دارای کلاس `test` هستند پیدا می‌کنیم:

```js
const testElements = document.getElementsByClassName("test");
const testDivs = Array.prototype.filter.call(
  testElements,
  (testElement) => testElement.nodeName === "DIV",
);
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}