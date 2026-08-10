---
title: "display CSS property"
source: "https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/display"
translated_by: "n8n + AI"
---

ویژگی `display` در [CSS](/en-US/docs/Web/CSS) تعیین می‌کند که یک المان به‌عنوان یک جعبهٔ بلوکی یا درون‌خطی رفتار کند، و همچنین چیدمانی که برای فرزندانش به‌کار می‌رود – مانند [flow layout](/en-US/docs/Web/CSS/Guides/Display/Flow_layout)، [grid](/en-US/docs/Web/CSS/Guides/Grid_layout) یا [flex](/en-US/docs/Web/CSS/Guides/Flexible_box_layout).

به‌طور رسمی، ویژگی `display` نوع نمایش بیرونی و درونی یک المان را مشخص می‌کند. نوع بیرونی، نحوهٔ شرکت المان در [flow layout](/en-US/docs/Web/CSS/Guides/Display/Flow_layout) را تعیین می‌کند؛ نوع درونی، چیدمان فرزندان را مشخص می‌کند. برخی از مقادیر `display` در مشخصات جداگانهٔ خودشان به‌طور کامل تعریف شده‌اند. برای مثال جزئیات اتفاقاتی که با اعلام `display: flex` رخ می‌دهد، در مشخصات CSS Flexible Box Model تعریف شده است.

```css interactive-example-choice
display: block;
```

```css interactive-example-choice
display: inline flow-root;
```

```css interactive-example-choice
display: none;
```

```css interactive-example-choice
display: flex;
```

```css interactive-example-choice
display: grid;
```

```html interactive-example
<p>
  Apply different <code>display</code> values on the dashed orange-bordered
  <code>div</code>, which contains three child elements.
</p>
<section class="default-example" id="default-example">
  <div class="example-container">
    Some text A.
    <div id="example-element">
      <div class="child">Child 1</div>
      <div class="child">Child 2</div>
      <div class="child">Child 3</div>
    </div>
    Some text B.
  </div>
</section>
```

```css interactive-example
.example-container {
  width: 100%;
  height: 100%;
}

code {
  background: #88888888;
}

#example-element {
  border: 3px dashed orange;
}

.child {
  display: inline-block;
  padding: 0.5em 1em;
  background-color: #ccccff;
  border: 1px solid #ababab;
  color: black;
}
```

## نحو

```css
/* مقدارهای کوتاه display */
display: none;
display: contents;
display: block;
display: flow-root;
display: inline;
display: inline-block;
display: list-item;
display: inline list-item;
display: flex;
display: inline-flex;
display: grid;
display: inline-grid;
display: grid-lanes;
display: inline-grid-lanes;
display: table;
display: inline-table;

/* مقدارهای کامل display */
display: block flow;
display: block flow-root;
display: inline flow;
display: inline flow-root;
display: block flow list-item;
display: inline flow list-item;
display: block flex;
display: inline flex;
display: block grid;
display: inline grid;
display: block table;
display: inline table;

/* مقادیر سراسری */
display: inherit;
display: initial;
display: revert;
display: revert-layer;
display: unset;
```

ویژگی `display` در CSS با استفاده از مقادیر کلیدی مشخص می‌شود.

## مقادیر گروه‌بندی‌شده

مقادیر کلیدی را می‌توان در شش دستهٔ کلی قرار داد.

### بیرونی

- `block`
  - : المان یک جعبهٔ بلوکی تولید می‌کند که در جریان عادی، قبل و بعد از خود شکست خط ایجاد می‌کند.
- `inline`
  - : المان یک یا چند جعبهٔ درون‌خطی تولید می‌کند که پیش و پس از خود شکست خط ایجاد نمی‌کنند. در جریان عادی، اگر فضا وجود داشته باشد، المان بعدی در همان خط قرار می‌گیرد.

> [!NOTE]
> وقتی ویژگی display فقط با یک مقدار **بیرونی** مشخص می‌شود (مثلاً `display: block` یا `display: inline`)، مقدار درونی به‌طور پیش‌فرض `flow` در نظر گرفته می‌شود (یعنی `display: block flow` و `display: inline flow`).

> [!NOTE]
> می‌توانید از سینتکس تک‌مقداری به‌عنوان جایگزینی برای سینتکس چندکلیدواژه‌ای استفاده کنید؛ برای مثال `display: inline flex` می‌تواند این fallback را داشته باشد:
>
> ```css
> .container {
>   display: inline-flex;
>   display: inline flex;
> }
> ```
>
> برای اطلاعات بیشتر، [استفاده از سینتکس چندکلیدواژه‌ای با display در CSS](/en-US/docs/Web/CSS/Guides/Display/Multi-keyword_syntax) را ببینید.

### Inside

- {{CSSxRef("&lt;display-inside&gt;")}}
  - : این کلیدواژه‌ها نوع نمایش داخلی عنصر را مشخص می‌کنند و تعیین می‌کنند که محتوای آن در چه نوع formatting contextای چیده می‌شود (به شرطی که عنصر یک عنصر جایگزین‌شده نباشد). اگر یکی از این کلیدواژه‌ها به‌تنهایی به‌عنوان یک مقدار واحد استفاده شود، نوع نمایش خارجی عنصر به‌طور پیش‌فرض `block` خواهد بود (به جز `ruby` که پیش‌فرض آن `inline` است).
    - `flow`
      - : عنصر، محتوای خود را با استفاده از flow layout (طرح‌بندی block و inline) می‌چیند.

        اگر نوع نمایش خارجی آن `inline` باشد و در یک formatting context از نوع block یا inline شرکت کند، یک جعبه inline تولید می‌کند. در غیر این‌صورت یک جعبه block.

        بسته به مقدار سایر propertyها (مانند {{CSSxRef("position")}}، {{CSSxRef("float")}} یا {{CSSxRef("overflow")}}) و اینکه آیا خودش در یک formatting context از نوع block یا inline شرکت می‌کند، یا یک [block formatting context](/en-US/docs/Web/CSS/Guides/Display/Block_formatting_context) (BFC) جدید برای محتوایش ایجاد می‌کند یا محتوایش را با formatting context والد ادغام می‌کند.

    - `flow-root`
      - : عنصر یک جعبه block تولید می‌کند که یک [block formatting context](/en-US/docs/Web/CSS/Guides/Display/Block_formatting_context) جدید ایجاد می‌کند و ریشه formatting را مشخص می‌کند.
    - `table`
      - : این عناصر مانند عناصر HTML {{HTMLElement("table")}} رفتار می‌کنند. یک جعبه در سطح block تعریف می‌کند.
    - `flex`
      - : عنصر مانند یک عنصر در سطح block رفتار می‌کند و محتوای خود را بر اساس [مدل flexbox](/en-US/docs/Web/CSS/Guides/Flexible_box_layout) می‌چیند.
    - `grid`
      - : عنصر مانند یک عنصر در سطح block رفتار می‌کند و محتوای خود را بر اساس [مدل grid](/en-US/docs/Web/CSS/Guides/Grid_layout/Basic_concepts) می‌چیند.
    - `grid-lanes`
      - : عنصر مانند یک عنصر در سطح block رفتار می‌کند و محتوای خود را با استفاده از masonry layout می‌چیند. ستون‌ها با {{cssxref("grid-template-columns")}} تعریف می‌شوند و مانند یک grid صلب عمل می‌کنند، در حالی که آیتم‌ها در جهت block طوری بسته‌بندی می‌شوند که فاصله بین آیتم‌های با اندازه‌های مختلف پر شود. برای جزئیات بیشتر [Masonry layout](/en-US/docs/Web/CSS/Guides/Grid_layout/Masonry_layout) را ببینید.

    - `inline-grid-lanes`
      - : عنصر مانند یک عنصر در سطح inline رفتار می‌کند و محتوای خود را با استفاده از masonry layout می‌چیند. ردیف‌ها با {{cssxref("grid-template-rows")}} تعریف می‌شوند و مانند یک grid صلب عمل می‌کنند، در حالی که آیتم‌ها در جهت inline بسته‌بندی می‌شوند. برای جزئیات بیشتر [Masonry layout](/en-US/docs/Web/CSS/Guides/Grid_layout/Masonry_layout) را ببینید.
    - `ruby`
      - : عنصر مانند یک عنصر در سطح inline رفتار می‌کند و محتوای خود را بر اساس مدل ruby formatting می‌چیند. مانند عناصر متناظر HTML {{HTMLElement("ruby")}} رفتار می‌کند.

> [!NOTE]
> وقتی یک ویژگی display فقط با یک مقدار **inner** (مانند `display: flex` یا `display: grid`) مشخص می‌شود، مقدار outer به‌طور پیش‌فرض `block` در نظر گرفته می‌شود (مثلاً `display: block flex` و `display: block grid`).

### List Item

- {{CSSxRef("&lt;display-listitem&gt;")}}
  - : عنصر یک جعبه block برای محتوا و یک جعبه inline جداگانه برای list-item تولید می‌کند.

مقدار تکی `list-item` باعث می‌شود عنصر مانند یک آیتم لیست رفتار کند.
این می‌تواند همراه با {{CSSxRef("list-style-type")}} و {{CSSxRef("list-style-position")}} استفاده شود.

`list-item` همچنین می‌تواند با هر کلیدواژه {{CSSxRef("&lt;display-outside&gt;")}} و کلیدواژه `flow` یا `flow-root` از {{CSSxRef("&lt;display-inside&gt;")}} ترکیب شود.

> [!NOTE]
> اگر مقدار داخلی (inner) مشخص نشود، به‌طور پیش‌فرض `flow` در نظر گرفته می‌شود.
> اگر مقدار خارجی (outer) مشخص نشود، جعبه اصلی (principal box) نوع نمایش خارجی `block` خواهد داشت.

### Internal

- `<display-internal>`
  - : برخی از مدل‌های چیدمان مانند `table` و `ruby` ساختار داخلی پیچیده‌ای دارند و فرزندان و نوادگان آن‌ها می‌توانند نقش‌های مختلفی ایفا کنند. این بخش مقادیر نمایش «داخلی» را تعریف می‌کند که فقط در همان حالت چیدمان خاص معنا دارند.
    - `table-row-group`
      - : این عناصر مانند عناصر HTML `<tbody>` رفتار می‌کنند.
    - `table-header-group`
      - : این عناصر مانند عناصر HTML `<thead>` رفتار می‌کنند.
    - `table-footer-group`
      - : این عناصر مانند عناصر HTML `<tfoot>` رفتار می‌کنند.
    - `table-row`
      - : این عناصر مانند عناصر HTML `<tr>` رفتار می‌کنند.
    - `table-cell`
      - : این عناصر مانند عناصر HTML `<td>` رفتار می‌کنند.
    - `table-column-group`
      - : این عناصر مانند عناصر HTML `<colgroup>` رفتار می‌کنند.
    - `table-column`
      - : این عناصر مانند عناصر HTML `<col>` رفتار می‌کنند.
    - `table-caption`
      - : این عناصر مانند عناصر HTML `<caption>` رفتار می‌کنند.
    - `ruby-base`
      - : این عناصر مانند عناصر HTML `<rb>` رفتار می‌کنند.
    - `ruby-text`
      - : این عناصر مانند عناصر HTML `<rt>` رفتار می‌کنند.
    - `ruby-base-container`
      - : این عناصر به‌عنوان جعبه‌های ناشناس (anonymous boxes) تولید می‌شوند.
    - `ruby-text-container`
      - : این عناصر مانند عناصر HTML `<rtc>` رفتار می‌کنند.

### Box

- `<display-box>`
  - : این مقادیر تعیین می‌کنند که آیا یک عنصر اصلاً جعبه‌های نمایشی تولید می‌کند یا خیر.
    - `contents`
      - : این عناصر به‌خودی‌خود جعبه مشخصی تولید نمی‌کنند. آن‌ها با جعبه مجازی (pseudo-box) و جعبه‌های فرزند جایگزین می‌شوند. توجه کنید که مشخصه CSS Display Level 3 نحوه تأثیر مقدار `contents` بر «عناصر غیرمعمول» را تعریف می‌کند — عناصری که صرفاً با مفاهیم جعبه CSS رندر نمی‌شوند، مانند عناصر جایگزین‌شده. برای جزئیات بیشتر به [Appendix B: Effects of display: contents on Unusual Elements](https://drafts.csswg.org/css-display/#unbox) مراجعه کنید.
    - `none`
      - : نمایش عنصر را غیرفعال می‌کند، به‌طوری که هیچ تأثیری بر چیدمان ندارد (سند طوری رندر می‌شود که انگار عنصر وجود ندارد). تمام عناصر نواده نیز نمایششان غیرفعال می‌شود. برای اینکه عنصری فضایی را که در حالت عادی اشغال می‌کند حفظ کند، اما چیزی رندر نکند، به‌جای آن از ویژگی `visibility` استفاده کنید.

### Precomposed

- `<display-legacy>`
  - : CSS 2 از یک نحو تک‌کلیدواژه و از پیش ترکیب‌شده برای ویژگی `display` استفاده می‌کرد که برای انواع block-level و inline-level یک مدل چیدمان یکسان، به کلیدواژه‌های جداگانه نیاز داشت.
    - `inline-block`
      - : عنصر یک جعبه block تولید می‌کند که همراه با محتوای اطراف جریان می‌یابد، انگار که یک جعبه inline واحد است (رفتاری شبیه به عنصر جایگزین‌شده). معادل `inline flow-root` است.
    - `inline-table`
      - : مقدار `inline-table` نگاشتی مستقیم در HTML ندارد. مانند عنصر HTML `<table>` رفتار می‌کند، اما به‌عنوان یک جعبه inline، نه block-level. درون جعبه table یک بافت block-level است. معادل `inline table` است.
    - `inline-flex`
      - : عنصر مانند یک عنصر inline-level رفتار می‌کند و محتوای خود را طبق مدل flexbox می‌چیند. معادل `inline flex` است.
    - `inline-grid`
      - : عنصر مانند یک عنصر inline-level رفتار می‌کند و محتوای خود را طبق مدل grid می‌چیند. معادل `inline grid` است.

### کدام نحو را باید استفاده کنید؟

ماژول [CSS display](/en-US/docs/Web/CSS/Guides/Display) یک سینتکس چندکلمه‌ای را برای مقادیر ویژگی `display` توصیف می‌کند که با آن می‌توانید نمایش **بیرونی** و **درونی** را به‌طور صریح تعریف کنید.
مقادیر تک‌کلمه‌ای (مقادیر پیش‌ساختهٔ `<display-legacy>`) برای حفظ سازگاری با نسخه‌های قبلی پشتیبانی می‌شوند.

برای نمونه، با استفاده از دو مقدار می‌توانید یک flex container درون‌خطی را این‌گونه مشخص کنید:

```css
.container {
  display: inline flex;
}
```

همین را با مقدار قدیمی تک‌کلمه‌ای نیز می‌توان مشخص کرد:

```css
.container {
  display: inline-flex;
}
```

برای اطلاعات بیشتر دربارهٔ این تغییرات، به راهنمای [استفاده از سینتکس چندکلمه‌ای با display در CSS](/en-US/docs/Web/CSS/Guides/Display/Multi-keyword_syntax) مراجعه کنید.

## توضیحات

صفحات مربوط به انواع مختلف مقادیری که می‌توان برای `display` تنظیم کرد، شامل مثال‌های متعددی از کاربرد آن مقادیر هستند — بخش [Syntax](#syntax) را ببینید. همچنین، منابع زیر را مشاهده کنید که مقادیر گوناگون display را به‌طور عمیق پوشش می‌دهند.

### مقادیر چندکلمه‌ای

- [استفاده از سینتکس چندکلمه‌ای با display در CSS](/en-US/docs/Web/CSS/Guides/Display/Multi-keyword_syntax)

### طرح‌بندی جریانی CSS (display: block, display: inline)

- [طرح‌بندی block و inline در جریان عادی](/en-US/docs/Web/CSS/Guides/Display/Block_and_inline_layout)
- [طرح‌بندی جریانی و overflow](/en-US/docs/Web/CSS/Guides/Display/Flow_layout_and_overflow)
- [طرح‌بندی جریانی و حالت‌های نوشتار](/en-US/docs/Web/CSS/Guides/Display/Flow_layout_and_writing_modes)
- [آشنایی با formatting contextها](/en-US/docs/Web/CSS/Guides/Display/Formatting_contexts)
- [درون جریان و بیرون از جریان](/en-US/docs/Web/CSS/Guides/Display/In_flow_and_out_of_flow)

### display: flex

- [مفاهیم پایه flexbox](/en-US/docs/Web/CSS/Guides/Flexible_box_layout/Basic_concepts)
- [ترازبندی آیتم‌ها در یک flex container](/en-US/docs/Web/CSS/Guides/Flexible_box_layout/Aligning_items)
- [کنترل نسبت آیتم‌های flex در راستای محور اصلی](/en-US/docs/Web/CSS/Guides/Flexible_box_layout/Controlling_flex_item_ratios)
- [تسلط بر شکستن خط آیتم‌های flex](/en-US/docs/Web/CSS/Guides/Flexible_box_layout/Wrapping_items)
- [مرتب‌سازی آیتم‌های flex](/en-US/docs/Web/CSS/Guides/Flexible_box_layout/Ordering_items)
- [ارتباط flexbox با سایر روش‌های طرح‌بندی](/en-US/docs/Web/CSS/Guides/Flexible_box_layout/Relationship_with_other_layout_methods)
- [کاربردهای معمول flexbox](/en-US/docs/Web/CSS/Guides/Flexible_box_layout/Use_cases)

### display: grid

- [مفاهیم پایه grid layout](/en-US/docs/Web/CSS/Guides/Grid_layout/Basic_concepts)
- [ارتباط با سایر روش‌های طرح‌بندی](/en-US/docs/Web/CSS/Guides/Grid_layout/Relationship_with_other_layout_methods)
- [جانمایی مبتنی بر خط](/en-US/docs/Web/CSS/Guides/Grid_layout/Line-based_placement)
- [نواحی قالب grid](/en-US/docs/Web/CSS/Guides/Grid_layout/Grid_template_areas)
- [طرح‌بندی با استفاده از خطوط grid نام‌گذاری‌شده](/en-US/docs/Web/CSS/Guides/Grid_layout/Named_grid_lines)
- [جانمایی خودکار در grid layout](/en-US/docs/Web/CSS/Guides/Grid_layout/Auto-placement)
- [ترازبندی آیتم‌ها در CSS grid layout](/en-US/docs/Web/CSS/Guides/Grid_layout/Box_alignment)
- [gridها، مقادیر منطقی و حالت‌های نوشتار](/en-US/docs/Web/CSS/Guides/Grid_layout/Logical_values_and_writing_modes)
- [CSS grid layout و دسترسی‌پذیری](/en-US/docs/Web/CSS/Guides/Grid_layout/Accessibility)
- [پیاده‌سازی طرح‌بندی‌های رایج با استفاده از grid](/en-US/docs/Web/CSS/Guides/Grid_layout/Common_grid_layouts)
- [Masonry layout](/en-US/docs/Web/CSS/Guides/Grid_layout/Masonry_layout)

### انیمیت کردن display

[مرورگرهای پشتیبانی‌کننده](#browser_compatibility) خصوصیت `display` را با [نوع انیمیشن گسسته](/en-US/docs/Web/CSS/Guides/Animations/Animatable_properties#discrete) متحرک‌سازی می‌کنند. این معمولاً به این معنی است که خصوصیت در نیمهٔ راه بین دو مقدار، از یکی به دیگری تغییر وضعیت می‌دهد.

یک استثنا وجود دارد و آن زمانی است که از/به `display: none` انیمیشن می‌سازید. در این حالت، مرورگر بین دو مقدار جابه‌جا می‌شود تا محتوای متحرک‌شده در تمام طول انیمیشن نمایش داده شود. برای نمونه:

- هنگام انیمیشن‌سازی `display` از `none` به `block` (یا یک مقدار `display` قابل مشاهده‌ی دیگر)، مقدار در `0%` زمان انیمیشن به `block` تغییر می‌کند تا در سراسر انیمیشن قابل مشاهده باشد.
- هنگام انیمیشن‌سازی `display` از `block` (یا یک مقدار `display` قابل مشاهده‌ی دیگر) به `none`، مقدار در `100%` زمان انیمیشن به `none` تغییر می‌کند تا در سراسر انیمیشن قابل مشاهده بماند.

این رفتار برای ساخت انیمیشن‌های ورود/خروج کاربردی است؛ مثلاً وقتی می‌خواهید یک ظرف (container) را با `display: none` از DOM حذف کنید، اما به‌جای ناپدید شدن ناگهانی، با {{cssxref("opacity")}} محو شود.

هنگام انیمیشن‌سازی `display` با [CSS animations](/en-US/docs/Web/CSS/Guides/Animations)، باید مقدار آغازین `display` را در یک keyframe صریح (مثلاً با `0%` یا `from`) مشخص کنید. برای نمونه به [استفاده از CSS animations](/en-US/docs/Web/CSS/Guides/Animations/Using) مراجعه کنید.

هنگام انیمیشن‌سازی `display` با [CSS transitions](/en-US/docs/Web/CSS/Guides/Transitions)، دو ویژگی اضافی نیاز است:

- {{cssxref("@starting-style")}} مقادیر آغازین ویژگی‌هایی که می‌خواهید transition از آن‌ها شروع شود را هنگام اولین نمایش عنصر فراهم می‌کند. این کار برای جلوگیری از رفتار غیرمنتظره ضروری است. به‌طور پیش‌فرض، CSS transitions در اولین به‌روزرسانی استایل یک عنصر یا زمانی که نوع `display` از `none` به نوع دیگری تغییر کند، فعال نمی‌شوند.
- [`transition-behavior: allow-discrete`](/en-US/docs/Web/CSS/Reference/Properties/transition-behavior) باید در اعلان {{cssxref("transition-property")}} (یا شکل خلاصه {{cssxref("transition")}}) تنظیم شود تا transitionهای `display` فعال شوند.

برای نمونه‌هایی از transition ویژگی `display`، به صفحه‌های [`@starting-style`](/en-US/docs/Web/CSS/Reference/At-rules/@starting-style#examples) و [`transition-behavior`](/en-US/docs/Web/CSS/Reference/Properties/transition-behavior#examples) مراجعه کنید.

## دسترسی‌پذیری

### display: none

استفاده از مقدار `display: none` روی یک عنصر، آن را از [درخت دسترسی‌پذیری](/en-US/docs/Learn_web_development/Core/Accessibility/What_is_accessibility#accessibility_apis) حذف می‌کند. در نتیجه، خود عنصر و تمام عناصر فرزند آن دیگر توسط فناوری‌های صفحه‌خوان اعلام نمی‌شوند.

اگر می‌خواهید عنصر را فقط از نظر بصری پنهان کنید، یک جایگزین دسترس‌پذیرتر استفاده از [ترکیبی از ویژگی‌ها](https://webaim.org/techniques/css/invisiblecontent/) است تا عنصر از صفحه پنهان شود اما همچنان برای فناوری‌های کمکی مانند صفحه‌خوان‌ها در دسترس بماند.

با اینکه `display: none` محتوا را از درخت دسترسی‌پذیری خارج می‌کند، عناصری که پنهان هستند اما از طریق ویژگی‌های `aria-describedby` یا `aria-labelledby` در عناصر قابل مشاهده به آن‌ها ارجاع داده شده باشد، برای فناوری‌های کمکی آشکار می‌مانند.

### display: contents

در پیاده‌سازی‌های فعلی برخی مرورگرها، هر عنصری که `display` آن `contents` باشد از [درخت دسترسی‌پذیری](/en-US/docs/Learn_web_development/Core/Accessibility/What_is_accessibility#accessibility_apis) حذف می‌شود (اما فرزندان باقی می‌مانند). این باعث می‌شود خود عنصر دیگر توسط صفحه‌خوان‌ها اعلام نشود. این رفتار طبق [مشخصات CSS](https://drafts.csswg.org/css-display/#valdef-display-contents) نادرست است.

- [نشانه‌گذاری دسترس‌پذیرتر با display: contents | Hidde de Vries](https://hidde.blog/more-accessible-markup-with-display-contents/)
- [display: contents یک ریست CSS نیست | Adrian Roselli](https://adrianroselli.com/2018/05/display-contents-is-not-a-css-reset.html)

در برخی مرورگرها، تغییر مقدار `display` عنصر `<table>` به `block`، `grid` یا `flex` نحوهٔ حضور آن در [درخت دسترس‌پذیری](/en-US/docs/Learn_web_development/Core/Accessibility/What_is_accessibility#accessibility_apis) را تغییر می‌دهد. این موضوع باعث می‌شود فناوری‌های صفحه‌خوان دیگر نتوانند جدول را به‌درستی اعلام کنند.

- [محتوای مخفی برای دسترس‌پذیری بهتر | Go Make Things](https://gomakethings.com/articles/hidden-content-for-better-a11y/)
- [توضیحات راهنمای WCAG (راهنما ۱.۳) در MDN](/en-US/docs/Web/Accessibility/Guides/Understanding_WCAG/Perceivable#guideline_1.3_%e2%80%94_create_content_that_can_be_presented_in_different_ways)
- [درک معیار موفقیت ۱.۳.۱ | درک WCAG 2.0 از W3C](https://www.w3.org/TR/UNDERSTANDING-WCAG20/content-structure-separation-programmatic.html)

## Formal definition

## Formal syntax

## Examples

### مقایسه مقدار display

در این مثال دو عنصر کانتینری block-level داریم که هر کدام سه فرزند inline دارند. در پایین صفحه یک منوی select قرار دارد که می‌توانید مقادیر مختلف `display` را روی کانتینرها اعمال کنید و تأثیر هر مقدار را روی چیدمان عنصر و فرزندانش مقایسه کنید.

برای دیدن بهتر تأثیر مقادیر display، از `padding` و `background-color` روی کانتینرها و فرزندان استفاده کرده‌ایم.

#### HTML

```html
<article class="container">
  <span>First</span>
  <span>Second</span>
  <span>Third</span>
</article>

<article class="container">
  <span>First</span>
  <span>Second</span>
  <span>Third</span>
</article>

<div>
  <label for="display">Choose a display value:</label>
  <select id="display">
    <option selected>block</option>
    <option>block flow</option>
    <option>inline</option>
    <option>inline flow</option>
    <option>flow</option>
    <option>flow-root</option>
    <option>block flow-root</option>
    <option>table</option>
    <option>block table</option>
    <option>flex</option>
    <option>block flex</option>
    <option>grid</option>
    <option>block grid</option>
    <option>list-item</option>
    <option>block flow list-item</option>
    <option>inline flow list-item</option>
    <option>block flow-root list-item</option>
    <option>inline flow-root list-item</option>
    <option>contents</option>
    <option>none</option>
    <option>inline-block</option>
    <option>inline flow-root</option>
    <option>inline-table</option>
    <option>inline table</option>
    <option>inline-flex</option>
    <option>inline flex</option>
    <option>inline-grid</option>
    <option>inline grid</option>
  </select>
</div>
```

#### CSS

```css
html {
  font-family: "Helvetica", "Arial", sans-serif;
  letter-spacing: 1px;
  padding-top: 10px;
}

article {
  background-color: red;
}

article span {
  background-color: black;
  color: white;
  margin: 1px;
}

article,
span {
  padding: 10px;
  border-radius: 7px;
}

article,
div {
  margin: 20px;
}
```

#### JavaScript

```js
const articles = document.querySelectorAll(".container");
const select = document.querySelector("select");

function updateDisplay() {
  articles.forEach((article) => {
    article.style.display = select.value;
  });
}

select.addEventListener("change", updateDisplay);

updateDisplay();
```

#### Result

توجه کنید که برخی مقادیر چندکلمه‌ای برای نمایش اضافه شده‌اند که معادل‌های زیر را دارند:

- `block` = `block flow`
- `inline` = `inline flow`
- `flow` = `block flow`
- `flow-root` = `block flow-root`
- `table` = `block table`
- `flex` = `block flex`
- `grid` = `block grid`
- `list-item` = `block flow list-item`
- `inline-block` = `inline flow-root`
- `inline-table` = `inline table`
- `inline-flex` = `inline flex`
- `inline-grid` = `inline grid`

مثال‌های بیشتری را می‌توانید در صفحه‌های مربوط به هر نوع نمایش مجزا، در بخش [مقادیر گروه‌بندی‌شده](#grouped_values) بیابید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{CSSxRef("visibility")}}, {{CSSxRef("float")}}, {{CSSxRef("position")}}
- {{CSSxRef("grid")}}, {{CSSxRef("flex")}}
- ماژول [چیدمان ruby در CSS](/en-US/docs/Web/CSS/Guides/Ruby_layout)
- خصوصیت SVG {{SVGAttr("display")}}
- [چیدمان بلاک و اینلاین در جریان عادی](/en-US/docs/Web/CSS/Guides/Display/Block_and_inline_layout)
- [معرفی contextهای قالب‌بندی](/en-US/docs/Web/CSS/Guides/Display/Formatting_contexts)
- [چیدمان Masonry](/en-US/docs/Web/CSS/Guides/Grid_layout/Masonry_layout)