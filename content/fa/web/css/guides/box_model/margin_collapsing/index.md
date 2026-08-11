---
title: "Mastering margin collapsing"
source: "https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Box_model/Margin_collapsing"
translated_by: "n8n + AI"
---

# آشنایی با collapsing حاشیه (Margin)

حاشیه‌های بالا و پایین (top و bottom) بلوک‌ها گاهی با هم ترکیب می‌شوند (collapsed) و یک حاشیه واحد تشکیل می‌دهند که اندازه‌اش برابر بزرگ‌ترین حاشیه‌ی مجزاست (یا اگر مساوی باشند، همان یکی). به این رفتار **margin collapsing** می‌گویند. توجه داشته باشید که حاشیه‌های عناصر شناور (floating) و عناصر با موقعیت‌دهی مطلق (absolutely positioned) هرگز collapsed نمی‌شوند.

Margin collapsing در سه حالت اصلی رخ می‌دهد:

- **همسایه‌های مجاور (Adjacent siblings)**
  - حاشیه‌های دو خواهر و برادر مجاور collapsed می‌شوند (مگر اینکه خواهر و برادر بعدی نیاز به [clear](https://developer.mozilla.org/en-US/docs/Web/CSS/clear) کردن شناورها داشته باشد).
- **بدون محتوای جداکننده بین والد و فرزندان**
  - حاشیه‌های عمودی بین یک بلوک والد و فرزندان‌اش می‌توانند collapsed شوند. این اتفاق زمانی می‌افتد که محتوای جداکننده‌ای بین آن‌ها نباشد. به طور خاص، دو حالت اصلی وجود دارد:
    - `margin-top` والد با `margin-top` اولین فرزند درون‌جریان (in-flow) collapsed می‌شود، مگر اینکه والد دارای `border-top`، `padding-top`، محتوای inline (مثل متن) یا _clearance_ باشد.
    - `margin-bottom` والد با `margin-bottom` آخرین فرزند درون‌جریان collapsed می‌شود، مگر اینکه والد دارای `height` یا `min-height` تعریف‌شده، `border-bottom` یا `padding-bottom` باشد.
    در هر دو حالت، ایجاد یک [بافتار قالب‌بندی بلوکی جدید (new block formatting context)](https://developer.mozilla.org/en-US/docs/Web/Guide/CSS/Block_formatting_context) روی والد نیز از collapsed شدن حاشیه‌هایش با فرزندان جلوگیری می‌کند.
- **بلوک‌های خالی (Empty blocks)**
  - اگر هیچ border، padding، محتوای inline، `height` یا `min-height` برای جدا کردن `margin-top` یک بلوک از `margin-bottom` آن وجود نداشته باشد، حاشیه‌های بالا و پایین آن collapsed می‌شوند.

نکات مهم:

- وقتی حالت‌های بالا با هم ترکیب شوند، margin collapsing پیچیده‌تری (بیش از دو حاشیه) رخ می‌دهد.
- این قوانین حتی برای حاشیه‌های صفر هم اعمال می‌شوند؛ بنابراین حاشیه‌ی یک فرزند ممکن است بیرون از والدش قرار گیرد (طبق قوانین بالا) چه حاشیه‌ی والد صفر باشد چه نباشد.
- وقتی حاشیه‌های منفی وجود دارند، اندازه‌ی حاشیه‌ی collapsed شده برابر مجموع بزرگ‌ترین حاشیه‌ی مثبت و کوچک‌ترین (منفی‌ترین) حاشیه‌ی منفی است.
- وقتی همه‌ی حاشیه‌ها منفی هستند، اندازه‌ی حاشیه‌ی collapsed شده برابر کوچک‌ترین (منفی‌ترین) حاشیه است. این قانون هم برای عناصر مجاور و هم برای عناصر تو در تو اعمال می‌شود.
- collapsing حاشیه فقط در جهت عمودی معنا دارد.
- در ظرفی که `display` آن `flex` یا `grid` است، حاشیه‌ها collapsed نمی‌شوند.

## مثال‌ها

### HTML

```html
<p>حاشیه‌ی پایین این پاراگراف collapsed می‌شود…</p>
<p>
  … با حاشیه‌ی بالای این پاراگراف، که در نتیجه یک حاشیه‌ی
  <code>1.2rem</code> بین آن‌ها ایجاد می‌شود.
</p>

<div>
  این عنصر والد شامل دو پاراگراف است!
  <p>
    این پاراگراف یک حاشیه‌ی <code>.4rem</code> بین خود و متن بالا دارد.
  </p>
  <p>
    حاشیه‌ی پایین من با والد خود collapsed می‌شود و یک حاشیه‌ی پایین
    <code>2rem</code> ایجاد می‌کند.
  </p>
</div>

<p>من <code>2rem</code> پایین‌تر از عنصر بالا هستم.</p>
```

### CSS

```css
div {
  margin: 2rem 0;
  background: lavender;
}

p {
  margin: 0.4rem 0 1.2rem 0;
  background: yellow;
}
```

### نتیجه

{{EmbedLiveSample('Examples', 'auto', 350)}}

## همچنین ببینید

- [مدل جعبه‌ای CSS](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Box_Model)

- [CSS box model](/en-US/docs/Web/CSS/Guides/Box_model) ماژول
- [مقدمه‌ای بر CSS box model](/en-US/docs/Web/CSS/Guides/Box_model/Introduction)
- مفاهیم کلیدی CSS:
  - [CSS syntax](/en-US/docs/Web/CSS/Guides/Syntax/Introduction)
  - [At-rules](/en-US/docs/Web/CSS/Guides/Syntax/At-rules)
  - [Comments](/en-US/docs/Web/CSS/Guides/Syntax/Comments)
  - [Specificity](/en-US/docs/Web/CSS/Guides/Cascade/Specificity)
  - [Inheritance](/en-US/docs/Web/CSS/Guides/Cascade/Inheritance)
  - [Layout modes](/en-US/docs/Glossary/Layout_mode)
  - [Visual formatting model](/en-US/docs/Web/CSS/Guides/Display/Visual_formatting_model)
  - مقادیر:
    - [مقدار اولیه (Initial value)](/en-US/docs/Web/CSS/Guides/Cascade/Property_value_processing#initial_value)
    - [مقدار محاسبه‌شده (Computed value)](/en-US/docs/Web/CSS/Guides/Cascade/Property_value_processing#computed_value)
    - [مقدار استفاده‌شده (Used value)](/en-US/docs/Web/CSS/Guides/Cascade/Property_value_processing#used_value)
    - [مقدار واقعی (Actual value)](/en-US/docs/Web/CSS/Guides/Cascade/Property_value_processing#actual_value)
  - [Value definition syntax](/en-US/docs/Web/CSS/Guides/Values_and_units/Value_definition_syntax)
  - [Shorthand properties](/en-US/docs/Web/CSS/Guides/Cascade/Shorthand_properties)