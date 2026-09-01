---
title: "Element: checkVisibility() method"
short-title: checkVisibility()
slug: Web/API/Element/checkVisibility
page-type: web-api-instance-method
browser-compat: api.Element.checkVisibility
---

{{APIRef("DOM")}}

متد **`checkVisibility()`** در رابط {{domxref("Element")}} بررسی می‌کند که آیا عنصر به‌طور بالقوه قابل مشاهده است یا خیر.

این متد در هر یک از شرایط زیر مقدار `false` برمی‌گرداند:

- عنصر جعبهٔ مرتبطی ندارد، مثلاً به این دلیل که ویژگی CSS {{cssxref("display")}} روی [`none`](/en-US/docs/Web/CSS/Reference/Properties/display#none) یا [`contents`](/en-US/docs/Web/CSS/Reference/Properties/display#contents) تنظیم شده باشد.
- عنصر به این دلیل رندر نمی‌شود که عنصر یا یکی از عناصر بالادست (ancestor) ویژگی {{cssxref("content-visibility")}} را روی [`hidden`](/en-US/docs/Web/CSS/Reference/Properties/content-visibility#hidden) تنظیم کرده باشد.

پارامتر اختیاری، امکان انجام بررسی‌های اضافی برای آزمایش دیگر تفسیرهای «قابل مشاهده» را فراهم می‌کند. برای مثال، می‌توانید بیشتر بررسی کنید که آیا عنصر مقدار `opacity` برابر با `0` دارد، آیا مقدار ویژگی `visibility` عنصر آن را نامرئی می‌کند، یا آیا ویژگی `content-visibility` عنصر مقدار `auto` دارد و رندر آن در حال نادیده گرفته شدن است.

توجه داشته باشید که مقدار بازگشتی `true` تضمین نمی‌کند که عنصر برای کاربر قابل مشاهده است، فقط ممکن است قابل مشاهده باشد. عناصری که خارج از viewport هستند یا توسط سایر محتوا پوشانده شده‌اند ممکن است همچنان `true` برگردانند.

## Syntax

```js-nolint
checkVisibility(options)
```

### Parameters

- `options` {{optional_inline}}
  - : یک شیء که بررسی‌های اضافی را مشخص می‌کند. گزینه‌های ممکن عبارتند از:
    - `contentVisibilityAuto`
      - `true` برای بررسی اینکه آیا ویژگی {{cssxref("content-visibility")}} عنصر مقدار [`auto`](/en-US/docs/Web/CSS/Reference/Properties/content-visibility#auto) را دارد (یا به ارث می‌برد) و آیا در حال حاضر رندر آن نادیده گرفته می‌شود. به‌طور پیش‌فرض `false` است.
    - `opacityProperty`
      - `true` برای بررسی اینکه آیا ویژگی {{cssxref("opacity")}} عنصر مقدار `0` را دارد (یا به ارث می‌برد). به‌طور پیش‌فرض `false` است.
    - `visibilityProperty`
      - `true` برای بررسی اینکه آیا عنصر به دلیل مقدار ویژگی {{cssxref("visibility")}} خود نامرئی است. به‌طور پیش‌فرض `false` است.

        > [!NOTE]
        > عناصر نامرئی شامل آن‌هایی هستند که [`visibility: hidden`](/en-US/docs/Web/CSS/Reference/Properties/visibility#hidden) دارند و برخی از انواع عناصر که [`visibility: collapse`](/en-US/docs/Web/CSS/Reference/Properties/visibility#collapse) دارند.

    - `checkOpacity`
      - : یک نام مستعار تاریخی برای [`opacityProperty`](#opacityproperty).
    - `checkVisibilityCSS`
      - : یک نام مستعار تاریخی برای [`visibilityProperty`](#visibilityproperty).

### Return value

اگر هر یک از شرایط زیر برقرار باشد، `false` و در غیر این صورت `true` برمی‌گرداند:

- عنصر جعبهٔ مرتبطی ندارد.
- ویژگی {{cssxref("content-visibility")}} عنصر مقدار [`hidden`](/en-US/docs/Web/CSS/Reference/Properties/visibility#hidden) را دارد (یا به ارث می‌برد).
- `opacityProperty` (یا `checkOpacity`) برابر با `true` است و ویژگی {{cssxref("opacity")}} عنصر مقدار `0` را دارد (یا به ارث می‌برد).
- `visibilityProperty` (یا `checkVisibilityCSS`) برابر با `true` است و عنصر به دلیل مقدار ویژگی {{cssxref("visibility")}} خود نامرئی است.
- `contentVisibilityAuto` برابر با `true` است، ویژگی {{cssxref("content-visibility")}} مقدار [`auto`](/en-US/docs/Web/CSS/Reference/Properties/content-visibility#auto) را دارد (یا به ارث می‌برد)، و رندر عنصر نادیده گرفته می‌شود.

## Examples

### Test checkVisibility() with varied CSS

مثال زیر به شما امکان می‌دهد بررسی کنید که نتیجهٔ `checkVisibility()` چگونه ممکن است با مقادیر مختلف ویژگی‌های CSS `display`، `content-visibility`، `visibility` و `opacity` تغییر کند.

#### HTML

HTML یک عنصر `<select>` برای ویژگی‌های CSS که بر نتایج `checkVisibility()` تأثیر می‌گذارند تعریف می‌کند. مقادیر اول (پیش‌فرض انتخاب‌شده) باید هنگام اعمال بر روی یک عنصر باعث شوند `checkVisibility()` مقدار `true` برگرداند، در حالی که سایر مقادیر بر روی قابلیت مشاهده تأثیر می‌گذارند.

```html
<select id="css_display" name="css_display">
  <option value="block" selected>display: block</option>
  <option value="none">display: none</option>
  <option value="contents">display: contents</option>
</select>

<select id="css_content_visibility" name="css_content_visibility">
  <option value="visible" selected>content-visibility: visible</option>
  <option value="hidden">content-visibility: hidden</option>
  <option value="auto">content-visibility: auto</option>
</select>

<select id="css_opacity" name="css_opacity">
  <option value="1" selected>opacity: 1</option>
  <option value="0">opacity: 0</option>
</select>

<select id="css_visibility" name="css_visibility">
  <option value="visible" selected>visibility: visible</option>
  <option value="hidden">visibility: hidden</option>
  <option value="collapse">visibility: collapse</option>
</select>
```

سپس یک عنصر `<pre>` داریم که برای نمایش نتیجهٔ بررسی `checkVisibility()` در زمانی که هیچ گزینه‌ای در پارامتر ارسال نمی‌شود و همچنین برای هر مقدار گزینهٔ جداگانه استفاده می‌شود. در پایان، عنصری داریم که قرار است آزمایش شود (مقادیر ویژگی CSS انتخاب‌شده را روی آن اعمال خواهیم کرد).

```html
<pre id="output_result"></pre>
<div id="test_element">The element to be checked for visibility.</div>
```

#### CSS

CSS فقط عنصر مورد آزمایش را برجسته می‌کند.

```css
#test_element {
  border: solid;
  border-color: blue;
}
```

#### JavaScript

کد زیر هر یک از عناصر `<select>` را دریافت می‌کند. متد `updateCSS()` در شروع و هر بار که عناصر انتخاب تغییر می‌کنند فراخوانی می‌شود تا CSS انتخاب‌شده را روی عنصر هدف اعمال کند.

```js
const displayCssSelect = document.getElementById("css_display");
const contentVisibilityCssSelect = document.getElementById(
  "css_content_visibility",
);
const displayCssOpacity = document.getElementById("css_opacity");
const displayCssVisibility = document.getElementById("css_visibility");

const outputResult = document.getElementById("output_result");
const elementToCheck = document.getElementById("test_element");

updateCSS();

const cssSelectors = document.querySelectorAll("select");
cssSelectors.forEach((select) => {
  select.addEventListener("change", (event) => {
    updateCSS();
  });
});

function updateCSS() {
  // Apply selected CSS properties to target element
  elementToCheck.style.display = displayCssSelect.value;
  elementToCheck.style.contentVisibility = contentVisibilityCssSelect.value;
  elementToCheck.style.opacity = displayCssOpacity.value;
  elementToCheck.style.visibility = displayCssVisibility.value;

  // Call checkVisibility() on element using default and each of options
  const defaultVisibilityCheck = elementToCheck.checkVisibility();
  const opacityVisibilityCheck = elementToCheck.checkVisibility({
    opacityProperty: true,
  });
  const cssVisibilityCheck = elementToCheck.checkVisibility({
    visibilityProperty: true,
  });
  const contentVisibilityAutoCheck = elementToCheck.checkVisibility({
    contentVisibilityAuto: true,
  });

  // Output the results of the tests
  outputResult.innerText = `Checks on element below (may be hidden):
- Result of checkVisibility(): ${defaultVisibilityCheck}
- Result of checkVisibility({opacityProperty: true}): ${opacityVisibilityCheck}
- Result of checkVisibility({visibilityProperty: true}): ${cssVisibilityCheck}
- Result of checkVisibility({contentVisibilityAuto: true}): ${contentVisibilityAutoCheck}`;
}
```

#### نتیجه

نتایج در زیر نمایش داده می‌شود. اگر انتخاب را تغییر دهید، نتایج روی عنصر آزمایش (با طرح آبی) اعمال می‌شود و نتایج `checkVisibility()` برای هر تنظیمات باید نمایش داده شود. به‌عنوان مثال، اگر `opacity: 0` را تنظیم کنید، آن آزمایش (فقط) باید `false` را نشان دهد. با این حال، اگر `display: none` را تنظیم کنید، همه آزمایش‌ها باید `false` برگردانند.

{{ EmbedLiveSample('Test checkVisibility() with varied CSS', "100%", "200" ) }}

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}