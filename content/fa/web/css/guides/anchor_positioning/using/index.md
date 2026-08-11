---
title: "Using CSS anchor positioning"
source: "https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Anchor_positioning/Using"
translated_by: "n8n + AI"
---

```markdown
ماژول **CSS anchor positioning** قابلیت‌هایی را تعریف می‌کند که به شما امکان می‌دهند المان‌ها را به یکدیگر متصل کنید. المان‌ها می‌توانند به عنوان **anchor element** یا **anchor-positioned element** تعریف شوند. المان‌های anchor-positioned می‌توانند به anchor elementها متصل شوند. سپس می‌توان اندازه و موقعیت این المان‌ها را نسبت به اندازه و مکان anchor elementهایی که به آن‌ها متصل شده‌اند تنظیم کرد.

CSS anchor positioning همچنین مکانیزم‌هایی صرفاً با CSS برای تعیین چندین موقعیت جایگزین برای یک المان anchor-positioned فراهم می‌کند. برای مثال، اگر یک tooltip به یک فیلد فرم متصل باشد اما با تنظیمات پیش‌فرض موقعیت‌دهی خارج از صفحه رندر شود، مرورگر می‌تواند آن را در یک موقعیت پیشنهادی دیگر رندر کند تا روی صفحه قرار گیرد، یا در صورت تمایل، آن را به طور کلی مخفی کند.

این مقاله مفاهیم پایه‌ای anchor positioning و نحوه استفاده از قابلیت‌های اتصال، موقعیت‌دهی و اندازه‌دهی این ماژول را در سطح مقدماتی توضیح می‌دهد. برای هر مفهوم، لینک‌هایی به صفحات مرجع با مثال‌ها و جزئیات syntax آورده شده است. برای اطلاعات بیشتر درباره تعیین موقعیت‌های جایگزین و مخفی‌سازی المان‌های anchor-positioned، راهنمای [Fallback options and conditional hiding for overflow](/en-US/docs/Web/CSS/Guides/Anchor_positioning/Try_options_hiding) را مطالعه کنید.

## مفاهیم پایه

اتصال (یا bind کردن) یک المان به المان دیگر بسیار رایج است. برای مثال:

- پیام‌های خطا که در کنار کنترل‌های فرم نمایش داده می‌شوند.
- Tooltipها یا جعبه‌های اطلاعاتی که کنار یک المان رابط کاربری ظاهر می‌شوند تا اطلاعات بیشتری درباره آن بدهند.
- دیالوگ‌های تنظیمات یا گزینه‌ها که برای پیکربندی سریع المان‌های رابط کاربری در دسترس هستند.
- منوهای کشویی (drop-down) یا پاپ‌اور که کنار نوار ناوبری یا دکمه مرتبط ظاهر می‌شوند.

رابط‌های کاربری مدرن اغلب به این نیاز دارند که بخشی از محتوا — معمولاً قابل استفاده مجدد و تولیدشده به صورت پویا — نسبت به یک anchor element قرار بگیرد. اگر المانی که قرار است به آن متصل شویم (یا همان **anchor element**) همیشه در جای ثابتی از رابط کاربری باشد و المان متصل‌شونده (یا همان **anchor-positioned element**، یا به اختصار **positioned element**) همیشه بتواند بلافاصله قبل یا بعد از آن در ترتیب سورس قرار گیرد، پیاده‌سازی چنین مواردی بسیار ساده بود. اما در عمل شرایط به ندرت این‌قدر ساده است.

موقعیت المان‌های positioned نسبت به anchor element خود باید با جابه‌جایی یا تغییر پیکربندی anchor element حفظ و تنظیم شود (مثلاً با اسکرول، تغییر اندازه viewport، درگ‌اندروپ و غیره). برای مثال، اگر المانی مانند فیلد فرم به لبه viewport نزدیک شود، ممکن است tooltip آن خارج از صفحه قرار گیرد. معمولاً می‌خواهید tooltip به کنترل فرم خود متصل بماند و تا زمانی که فیلد فرم دیده می‌شود، tooltip نیز کاملاً روی صفحه و قابل مشاهده باشد؛ در صورت نیاز هم به صورت خودکار جابه‌جا شود. شاید این رفتار پیش‌فرض را در سیستم‌عامل خود دیده باشید؛ وقتی روی منوی زمینه (context menu) با دکمه راست ماوس (<kbd>Ctrl</kbd> + کلیک) کلیک می‌کنید.

در گذشته، اتصال یک المان به المان دیگر و تغییر پویای موقعیت و اندازه یک المان positioned بر اساس موقعیت anchor، به جاوااسکریپت نیاز داشت که پیچیدگی و مشکلات عملکردی به همراه داشت. همچنین در همه شرایط تضمین نمی‌شد که به درستی کار کند. قابلیت‌های تعریف‌شده در ماژول [CSS anchor positioning](/en-US/docs/Web/CSS/Guides/Anchor_positioning) امکان پیاده‌سازی این موارد را به صورت کارآمد و اعلانی (declarative) با CSS (و HTML) به جای جاوااسکریپت فراهم می‌کند.

## مرتبط کردن المان‌های anchor و positioned

برای مرتبط کردن یک المان با یک anchor، ابتدا باید مشخص کنید کدام المان anchor است و سپس تعیین کنید کدام المان(های) positioned باید با آن anchor مرتبط شوند. این کار یک مرجع anchor (anchor reference) بین آن دو ایجاد می‌کند. این ارتباط را می‌توان به صورت صریح (explicit) با CSS یا به صورت ضمنی (implicit) ایجاد کرد.
```

### ارتباط صریح anchor با CSS

برای اینکه یک عنصر را با CSS به عنوان anchor تعریف کنید، باید یک نام anchor روی آن از طریق ویژگی `anchor-name` تنظیم کنید. نام anchor باید یک `dashed-ident` باشد. در این مثال، `width` عنصر anchor را هم روی `fit-content` قرار می‌دهیم تا یک anchor مربعی کوچک داشته باشیم که اثر اتصال را بهتر نشان می‌دهد.

```css hidden
.anchor {
  font-size: 1.8rem;
  color: white;
  text-shadow: 1px 1px 1px black;
  background-color: hsl(240 100% 75%);
  border-radius: 10px;
  border: 1px solid black;
  padding: 3px;
}
```

```css
.anchor {
  anchor-name: --my-anchor;
  width: fit-content;
}
```

تبدیل یک عنصر به عنصر موقعیت‌دهی‌شده با anchor دو مرحله دارد: ابتدا باید با ویژگی `position` به صورت `absolute` یا `fixed` [موقعیت‌دهی شود](/en-US/docs/Learn_web_development/Core/CSS_layout/Positioning). سپس ویژگی `position-anchor` روی عنصر موقعیت‌دهی‌شده به مقدار ویژگی `anchor-name` عنصر anchor تنظیم می‌شود تا این دو به هم مرتبط شوند:

```css hidden
.infobox {
  color: darkblue;
  background-color: azure;
  border: 1px solid #dddddd;
  padding: 10px;
  border-radius: 10px;
  font-size: 1rem;
}
```

```css
.infobox {
  position: fixed;
  position-anchor: --my-anchor;
}
```

CSS بالا را روی HTML زیر اعمال می‌کنیم:

```html
<div class="anchor">⚓︎</div>

<div class="infobox">
  <p>This is an information box.</p>
</div>
```

نتیجه به این صورت رندر می‌شود:

حالا anchor و infobox به هم مرتبط شده‌اند، اما فعلاً باید به ما اعتماد کنید. هنوز به یکدیگر متصل نیستند — اگر anchor را جابه‌جا کنید، به تنهایی حرکت می‌کند و infobox در همان جای قبلی می‌ماند. اتصال واقعی را وقتی بررسی کنیم که به بخش [موقعیت‌دهی عناصر بر اساس موقعیت anchor](#positioning_elements_relative_to_their_anchor) برسیم.

### ارتباط ضمنی anchor

در برخی موارد، به دلیل ماهیت معنایی رابطه بین دو عنصر، یک ارجاع ضمنی anchor بین آن‌ها ایجاد می‌شود:

- وقتی از [Popover API](/en-US/docs/Web/API/Popover_API) برای مرتبط‌کردن یک popover با یک کنترل استفاده می‌کنید، یک ارجاع ضمنی anchor بین آن دو برقرار می‌شود. این اتفاق می‌تواند در این حالت‌ها رخ دهد:
  - وقتی به صورت اعلانی (declarative) یک popover را با استفاده از ویژگی‌های [`popovertarget`](/en-US/docs/Web/HTML/Reference/Elements/button#popovertarget) و [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id) یا ویژگی‌های [`commandfor`](/en-US/docs/Web/HTML/Reference/Elements/button#commandfor) و `id` به یک کنترل مرتبط می‌کنید.
  - وقتی به صورت برنامه‌نویسی (programmatic) یک اکشن popover مانند `showPopover()` را با گزینه `source` به یک کنترل مرتبط می‌کنید.
- عنصر `<select>` و فهرست بازشوی آن با استفاده از ویژگی `appearance` به مقدار `base-select` در قابلیت [عنصر select سفارشی‌پذیر](/en-US/docs/Learn_web_development/Extensions/Forms/Customizable_select) قرار می‌گیرند. در این حالت، یک رابطه ضمنی «فراخوان popover» (popover-invoker) بین آن دو ایجاد می‌شود که به معنای وجود ارجاع ضمنی anchor بین آن‌ها نیز هست.

> [!NOTE]
> روش‌های بالا یک anchor را به یک عنصر مرتبط می‌کنند، اما هنوز به هم متصل نیستند. برای متصل‌کردن آن‌ها، عنصر موقعیت‌دهی‌شده باید نسبت به anchor خود موقعیت‌دهی شود؛ این کار با CSS انجام می‌شود.

### حذف ارتباط anchor

اگر بخواهید یک ارتباط صریح anchor را که قبلاً بین یک عنصر anchor و یک عنصر موقعیت‌دهی‌شده ایجاد شده است حذف کنید، می‌توانید یکی از کارهای زیر را انجام دهید:

1. مقدار ویژگی `anchor-name` عنصر anchor را روی `none` یا یک `<dashed-ident>` دیگر تنظیم کنید (اگر می‌خواهید عنصر دیگری به آن متصل شود).
2. ویژگی `position-anchor` عنصر موقعیت‌دهی‌شده را روی `none` یا نام anchor تنظیم کنید که در سند فعلی وجود ندارد، مثل `--not-an-anchor-name`.

در مورد ارتباط‌های ضمنی لنگر (implicit anchor associations)، باید از روش دوم استفاده کنید — روش اول کار نمی‌کند. دلیلش این است که این ارتباط به صورت داخلی کنترل می‌شود و شما نمی‌توانید `anchor-name` را از طریق CSS حذف کنید.

مثلاً برای اینکه picker یک عنصر `<select>` سفارشی‌شده از لنگر شدن به خود `<select>` جلوگیری کنید، می‌توانید از rule زیر استفاده کنید:

```css
::picker(select) {
  position-anchor: none;
}
```

## محدوده لنگر (Anchor scoping)

وقتی چندین عنصر لنگر مقدار {{cssxref("anchor-name")}} یکسانی داشته باشند و یک عنصر موقعیت‌یافته (positioned element) نیز آن نام را به عنوان مقدار خاصیت {{cssxref("position-anchor")}} خود داشته باشد، عنصر موقعیت‌یافته با **آخرین** عنصر لنگر در ترتیب سورس که همان `anchor-name` را دارد، مرتبط می‌شود.

مثلاً اگر یک سند شامل چندین مؤلفه‌ی تکراری باشد که هر کدام یک عنصر موقعیت‌یافته متصل به یک لنگر دارند، همه‌ی عناصر موقعیت‌یافته به آخرین لنگر در صفحه متصل می‌شوند مگر اینکه هر مؤلفه از یک نام لنگر متفاوت استفاده کند. این معمولاً رفتار دلخواه نیست.

خاصیت {{cssxref("anchor-scope")}} می‌تواند این مشکل را با محدود کردن دید (visibility) یا «حوزه» (scope) یک مقدار `anchor-name` به یک زیردرخت خاص حل کند. نتیجه این است که هر عنصر موقعیت‌یافته فقط می‌تواند به یک عنصر در همان زیردرختی که scope روی آن تنظیم شده است، لنگر شود.

- `anchor-scope: all` scope را به گونه‌ای تنظیم می‌کند که **هر** مقدار `anchor-name` تعیین‌شده در زیردرخت، فقط توسط عناصر موقعیت‌یافته در همان زیردرخت قابل اتصال باشد.
- `anchor-scope: --my-anchor, --my-anchor2` scope را به گونه‌ای تنظیم می‌کند که مقادیر `anchor-name` مشخص‌شده، وقتی در زیردرخت تنظیم شوند، فقط توسط عناصر موقعیت‌یافته در همان زیردرخت قابل اتصال باشند.
- `anchor-scope: none` مقدار پیش‌فرض است؛ یعنی هیچ محدودیت scope لنگری تنظیم نشده است.

مثلاً فرض کنید چندین لنگر و عناصر {{htmlelement("div")}} با موقعیت‌یابی لنگر داخل کانتینرهای {{htmlelement("section")}} دارید:

```html live-sample___anchor-scope
<section class="scoped">
  <div class="anchor">⚓︎</div>
  <div class="positioned">Positioned 1</div>
</section>

<section class="scoped">
  <div class="anchor">⚓︎</div>
  <div class="positioned">Positioned 2</div>
</section>

<section class="scoped">
  <div class="anchor">⚓︎</div>
  <div class="positioned">Positioned 3</div>
</section>
```

هر `<div class="anchor">` را با دادن یک `anchor-name` به نام `--my-anchor` به یک عنصر لنگر تبدیل می‌کنیم. سپس هر `<div class="positioned">` را نسبت به یک عنصر با نام لنگر `--my-anchor` موقعیت‌یابی می‌کنیم، با دادن موقعیت مطلق (absolute positioning)، مقدار `position-anchor` برابر `--my-anchor` و مقدار {{cssxref("position-area")}} برابر `right`. در نهایت، scope لنگر هر کانتینر `<section>` را با استفاده از `anchor-scope: --my-anchor` تنظیم می‌کنیم:

```css hidden live-sample___anchor-scope
html {
  height: 100%;
}

body {
  height: inherit;
  display: flex;
  justify-content: space-evenly;
  align-items: center;
}

.scoped {
  padding: 20px;
  background: #eeeeee;
}

.anchor {
  font-size: 1.8rem;
  color: white;
  text-shadow: 1px 1px 1px black;
  background-color: blue;
  width: fit-content;
  padding: 3px;
}

.positioned {
  background: orange;
  width: fit-content;
  padding: 3px;
}
```

```css live-sample___anchor-scope
.anchor {
  anchor-name: --my-anchor;
}

.positioned {
  position: absolute;
  position-anchor: --my-anchor;
  position-area: right;
}

.scoped {
  anchor-scope: --my-anchor;
}
```

این کد رفتار موقعیت‌یابی زیر را به همراه دارد:

{{ EmbedLiveSample("anchor-scope", "100%", "150") }}

هر عنصر موقعیت‌یافته نسبت به لنگر داخل همان عنصر `<section>` قرار می‌گیرد. دلیلش این است که هر عنصر `<section>` دارای `anchor-scope: --my-anchor` است؛ بنابراین عناصر موقعیت‌یافته داخل هر کانتینر با scope فقط می‌توانند نسبت به لنگرهای `my-anchor` درون همان کانتینر موقعیت‌گیری شوند.

اگر `anchor-scope: --my-anchor` را روی کانتینرها تنظیم نکنیم، تمام عناصر position شده نسبت به آخرین anchor در صفحه قرار می‌گیرند.

## قرار دادن عناصر موقعیت‌یافته نسبت به anchor خودشان

همان‌طور که پیش‌تر دیدیم، صرفاً مرتبط کردن یک عنصر position شده با یک anchor کاربرد چندانی ندارد. هدف ما این است که عنصر position شده را نسبت به عنصر anchor مرتبط با خودش قرار دهیم. این کار از طریق یکی از روش‌های زیر انجام می‌شود: تنظیم یک مقدار تابع [`anchor()` CSS](#using_inset_properties_with_anchor_function_values) روی یک خاصیت inset (حاشیه‌گذاری)، [مشخص کردن یک `position-area`](#setting_a_position-area)، یا وسط‌چین کردن عنصر position شده با مقدار [`anchor-center` placement](#centering_on_the_anchor_using_anchor-center).

> **نکته:** anchor positioning در CSS همچنین مکانیزم‌هایی برای تعیین موقعیت‌های جایگزین (fallback) در صورتی که موقعیت پیش‌فرض عنصر position شده باعث سرریز شدن آن از viewport شود، فراهم می‌کند. برای جزئیات بیشتر به راهنمای [گزینه‌های Try و مخفی‌سازی شرطی](/en-US/docs/Web/CSS/Guides/Anchor_positioning/Try_options_hiding) مراجعه کنید.

> **نکته:** عنصر anchor باید یک گره DOM قابل مشاهده باشد تا ارتباط و موقعیت‌دهی کار کند. اگر مخفی باشد (مثلاً با `display: none`)، عنصر position شده نسبت به نزدیک‌ترین ancestor position شده خود قرار می‌گیرد. در [مخفی‌سازی شرطی با `position-visibility`](/en-US/docs/Web/CSS/Guides/Anchor_positioning/Try_options_hiding#conditionally_hiding_anchor-positioned_elements)讨论了 وقتی anchor ناپدید می‌شود، چگونه یک عنصر anchor-positioned را مخفی کنیم.

### استفاده از خاصیت‌های inset با مقادیر تابع `anchor()`

عناصر position شده به صورت مطلق و ثابت (absolute و fixed) به طور معمول با تنظیم مقادیر {{cssxref("length")}} یا {{cssxref("percentage")}} روی {{glossary("inset properties", "خاصیت‌های inset")}} موقعیت‌یابی می‌شوند. با `position: absolute`، مقدار inset یک فاصله مطلق نسبت به لبه‌های نزدیک‌ترین ancestor position شده است. با `position: fixed`، مقدار inset یک فاصله مطلق نسبت به viewport است.

CSS anchor positioning این الگو را تغییر می‌دهد و امکان قرار دادن عناصر anchor-positioned را نسبت به لبه‌های anchor(های) مرتبط فراهم می‌کند. این ماژول تابع [`anchor()`](/en-US/docs/Web/CSS/Reference/Values/anchor) را تعریف می‌کند که یک مقدار معتبر برای هر یک از خاصیت‌های inset است. وقتی استفاده شود، این تابع مقدار inset را به عنوان یک فاصله مطلق نسبت به عنصر anchor تنظیم می‌کند: با تعیین عنصر anchor، سمت (side) از عنصر anchor که عنصر position شده نسبت به آن قرار می‌گیرد، و فاصله از آن سمت.

اجزای تابع به این شکل هستند:

```plain
anchor(<anchor-name> <anchor-side>, <fallback>)
```

- `<anchor-name>`
  - : مقدار خاصیت {{cssxref("anchor-name")}} عنصر anchor که می‌خواهید سمت عنصر خود را نسبت به آن قرار دهید. این یک مقدار `<dashed-ident>` است. اگر حذف شود، از **anchor پیش‌فرض** عنصر استفاده می‌شود. این anchor همان است که در خاصیت {{cssxref("position-anchor")}} ارجاع داده شده، یا با استفاده از ویژگی HTML غیراستاندارد [`anchor`](/en-US/docs/Web/HTML/Reference/Global_attributes/anchor) به عنصر مرتبط شده است.
    > **نکته:** مشخص کردن یک `<anchor-name>` عنصر را نسبت به آن anchor قرار می‌دهد، اما ارتباط (association) بین عناصر را برقرار نمی‌کند. اگرچه می‌توانید با تعیین [مقادیر مختلف `<anchor-name>`](/en-US/docs/Web/CSS/Reference/Values/anchor#positioning_an_element_relative_to_multiple_anchors) درون توابع `anchor()` مختلف روی یک عنصر، سمت‌های آن را نسبت به چندین anchor قرار دهید، اما عنصر position شده تنها با یک anchor مرتبط است.

- [`<anchor-side>`](/en-US/docs/Web/CSS/Reference/Values/anchor#anchor-side)
  - : موقعیت را نسبت به یک یا چند ضلع عنصر مرجع (anchor) مشخص می‌کند. مقادیر معتبر شامل `center` عنصر مرجع، ضلع‌های فیزیکی (`top`، `left` و غیره) یا منطقی (`start`، `self-end` و غیره) و همچنین یک `<percentage>` بین شروع (`0%`) و پایان (`100%`) محور خاصیت inset که `anchor()` روی آن تنظیم شده است، می‌باشد. اگر از مقداری استفاده شود که با خاصیت inset حاوی تابع `anchor()` [سازگار](/en-US/docs/Web/CSS/Reference/Values/anchor#compatibility_of_inset_properties_and_anchor-side_values) نباشد، مقدار fallback به کار می‌رود.

- `<fallback>`
  - : یک {{cssxref("length-percentage")}} که فاصله‌ای را به عنوان مقدار جایگزین (fallback) تعریف می‌کند. این مقدار در صورتی استفاده می‌شود که عنصر به صورت `absolute` یا `fixed` positioned نباشد، یا مقدار `<anchor-side>` با خاصیت inset حاوی `anchor()` سازگار نباشد، یا عنصر مرجع وجود نداشته باشد.

مقدار بازگشتی تابع `anchor()` یک طول (length) است که بر اساس موقعیت عنصر مرجع محاسبه می‌شود. اگر مستقیماً یک طول یا درصد روی خاصیت inset یک عنصر anchor-positioned تنظیم کنید، آن عنصر طوری positioned می‌شود که گویی به عنصر مرجع متصل نیست. این رفتار مشابه حالتی است که مقدار `<anchor-side>` با خاصیت inset ناسازگار باشد و fallback استفاده شود. دو اعلان زیر معادل هستند:

```css example-bad
bottom: anchor(right, 50px);
bottom: 50px;
```

هر دو، عنصر positioned را به اندازه `50px` بالای لبه پایین نزدیک‌ترین ancestor positioned (در صورت وجود) یا بلوک containing اولیه قرار می‌دهند.

رایج‌ترین پارامترهای `anchor()` که استفاده می‌کنید به یک ضلع از عنصر مرجع پیش‌فرض اشاره دارند. همچنین اغلب یا یک {{cssxref("margin")}} اضافه می‌کنید تا فاصله بین لبه عنصر مرجع و عنصر positioned ایجاد شود، یا از `anchor()` درون یک تابع `calc()` برای افزودن آن فاصله استفاده می‌کنید.

مثلاً این قانون لبه چپ عنصر positioned را دقیقاً در مجاورت لبه راست عنصر مرجع قرار می‌دهد و سپس با `margin-left` فاصله‌ای بین لبه‌ها ایجاد می‌کند:

```css
.positionedElement {
  left: anchor(right);
  margin-left: 10px;
}
```

مقدار بازگشتی تابع `anchor()` یک طول است. یعنی می‌توانید از آن درون یک تابع {{cssxref("calc()")}} استفاده کنید. این قانون لبه منطقی block-end عنصر positioned را به اندازه `10px` از لبه منطقی block-start عنصر مرجع فاصله می‌دهد – فاصله‌گذاری با استفاده از تابع `calc()` انجام شده، بنابراین نیازی به margin اضافه نیست:

```css
.positionedElement {
  inset-block-end: calc(anchor(start) + 10px);
}
```

#### مثال از `anchor()`

بیایید یک مثال عملی از `anchor()` ببینیم. از همان HTML مثال‌های قبلی استفاده کرده‌ایم، اما با اضافه کردن متن‌های پرکننده در بالا و پایین تا محتوا از ظرف خود سرریز کند و اسکرول شود. همچنین به عنصر مرجع همان `anchor-name` مثال قبلی را داده‌ایم:

```html hidden
<p>
  Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor
  incididunt ut labore et dolore magna aliqua. Dui nunc mattis enim ut tellus
  elementum sagittis vitae et.
</p>

<div class="anchor">⚓︎</div>

<div class="infobox">
  <p>This is an information box.</p>
</div>

<p>
  Nisi quis eleifend quam adipiscing vitae proin sagittis nisl rhoncus. In arcu
  cursus euismod quis viverra nibh cras pulvinar. Vulputate ut pharetra sit amet
  aliquam.
</p>

<p>
  Malesuada nunc vel risus commodo viverra maecenas accumsan lacus. Vel elit
  scelerisque mauris pellentesque pulvinar pellentesque habitant morbi
  tristique. Porta lorem mollis aliquam ut porttitor. Turpis cursus in hac
  habitasse platea dictumst quisque. Dolor sit amet consectetur adipiscing elit.
  Ornare lectus sit amet est placerat. Nulla aliquet porttitor lacus luctus
  accumsan.
</p>
```

```css hidden
.anchor {
  font-size: 1.8rem;
  color: white;
  text-shadow: 1px 1px 1px black;
  background-color: hsl(240 100% 75%);
  width: fit-content;
  border-radius: 10px;
  border: 1px solid black;
  padding: 3px;
}

body {
  width: 50%;
  margin: 0 auto;
}
```

```css
.anchor {
  anchor-name: --my-anchor;
}
```

جعبهٔ اطلاعات (infobox) با استفاده از نام anchor به آن متصل می‌شود و موقعیت‌یابی fixed می‌گیرد. با اضافه کردن خاصیت‌های `inset-block-start` و `inset-inline-start` (که در حالت نوشتاری افقی چپ‌به‌راست معادل `top` و `left` هستند)، آن را به anchor گره می‌زنیم. همچنین یک `margin` به جعبهٔ اطلاعات اضافه می‌کنیم تا فاصله‌ای بین عنصر موقعیت‌یاب و anchor ایجاد شود:

```css hidden
.infobox {
  color: darkblue;
  background-color: azure;
  border: 1px solid #dddddd;
  padding: 10px;
  border-radius: 10px;
  font-size: 1rem;
}
```

```css
.infobox {
  position-anchor: --my-anchor;
  position: fixed;
  inset-block-start: anchor(end);
  inset-inline-start: anchor(self-end);
  margin: 5px 0 0 5px;
}
```

حالا بیایید اعلان‌های موقعیت‌یابی مبتنی بر inset را دقیق‌تر بررسی کنیم:

- `inset-block-start: anchor(end)`: این مقدار، لبهٔ شروع بلوک عنصر موقعیت‌یاب را به لبهٔ پایان بلوک anchor تنظیم می‌کند که با استفاده از تابع `anchor(end)` محاسبه می‌شود.
- `inset-inline-start: anchor(self-end)`: این مقدار، لبهٔ شروع درون‌خطی عنصر موقعیت‌یاب را به لبهٔ پایان درون‌خطی خود anchor تنظیم می‌کند که با استفاده از تابع `anchor(self-end)` محاسبه می‌شود.

نتیجهٔ نهایی به این صورت خواهد بود:

{{ EmbedLiveSample("`anchor()` example", "100%", "250") }}

عنصر موقعیت‌یاب، `5px` پایین‌تر و `5px` سمت راست عنصر anchor قرار گرفته است. اگر صفحه را بالا و پایین اسکرول کنید، عنصر موقعیت‌یاب موقعیت خود را نسبت به عنصر anchor حفظ می‌کند — یعنی به anchor متصل است، نه به viewport.

### تنظیم `position-area`

خاصیت `position-area` جایگزینی برای تابع `anchor()` برای موقعیت‌دهی عناصر نسبت به anchorها فراهم می‌کند. این خاصیت بر اساس یک شبکهٔ ۳×۳ از خانه‌ها کار می‌کند که عنصر anchor در خانهٔ مرکزی قرار دارد. با `position-area` می‌توان عنصر موقعیت‌یاب را در هر یک از نه خانه قرار داد، یا آن را در دو یا سه خانه گسترش داد.

![شبکهٔ position-area، همانطور که در زیر توضیح داده شده است](/shared-assets/images/diagrams/css/anchor-positioning/position-area.svg)

خانه‌های شبکه به ردیف‌ها و ستون‌ها تقسیم می‌شوند:

- سه ردیف با مقادیر فیزیکی `top`, `center`, `bottom` نمایش داده می‌شوند. همچنین معادل‌های منطقی مانند `start`, `center`, `end` و معادل‌های مختصاتی مانند `y-start`, `center`, `y-end` دارند.
- سه ستون با مقادیر فیزیکی `left`, `center`, `right` نمایش داده می‌شوند. همچنین معادل‌های منطقی مانند `start`, `center`, `end` و معادل‌های مختصاتی مانند `x-start`, `center`, `x-end` دارند.

ابعاد خانهٔ مرکزی توسط [containing block](/en-US/docs/Web/CSS/Guides/Display/Containing_block) عنصر anchor تعریف می‌شود، در حالی که فاصله بین خانهٔ مرکزی و لبهٔ بیرونی شبکه توسط containing block عنصر موقعیت‌یاب مشخص می‌شود.

مقادیر خاصیت `position-area` از یک یا دو مقدار بر اساس مقادیر ردیف و ستون بالا تشکیل می‌شوند، و گزینه‌های spanning برای تعریف ناحیه‌ای از شبکه که عنصر در آن قرار می‌گیرد در دسترس هستند.

به عنوان مثال:

می‌توانید دو مقدار مشخص کنید تا عنصر موقعیت‌یاب را در یک خانهٔ خاص از شبکه قرار دهید. برای مثال:

- `top left` (معادل منطقی `start start`) عنصر را در خانهٔ بالا-چپ قرار می‌دهد.
- `bottom center` (معادل منطقی `end center`) عنصر را در خانهٔ پایین-مرکز قرار می‌دهد.

می‌توانید یک مقدار ردیف یا ستون را به همراه یک مقدار `span-*` مشخص کنید. مقدار اول تعیین می‌کند که عنصر موقعیت‌یافته در کدام ردیف یا ستون قرار گیرد (در ابتدا در مرکز آن قرار می‌گیرد) و مقدار دوم مشخص می‌کند که در چند بخش از آن ستون/ردیف گسترش یابد. برای مثال:

- `top span-left` باعث می‌شود عنصر موقعیت‌یافته در ردیف بالا قرار گیرد و در بخش‌های مرکز و چپ آن ردیف گسترش یابد.
- `y-end span-x-end` باعث می‌شود عنصر موقعیت‌یافته در انتهای ستون y قرار گیرد و در بخش‌های مرکز و انتهای x آن ستون گسترش یابد.
- `block-end span-all` باعث می‌شود عنصر موقعیت‌یافته در ردیف انتهای بلاک قرار گیرد و در بخش‌های شروع درون‌خطی (inline-start)، مرکز و انتهای درون‌خطی (inline-end) آن ردیف گسترش یابد.

اگر فقط یک مقدار مشخص کنید، رفتار بسته به نوع آن مقدار متفاوت است:

- یک مقدار ضلع فیزیکی (`top`، `bottom`، `left` یا `right`) یا مقدار مختصات (`y-start`، `y-end`، `x-start`، `x-end`) طوری عمل می‌کند که گویی مقدار دیگر برابر `span-all` است. مثلاً `top` همان اثر `top span-all` را دارد.
- یک مقدار ضلع منطقی (`start` یا `end`) طوری عمل می‌کند که گویی مقدار دیگر همان مقدار تنظیم شده است؛ مثلاً `start` اثر `start start` را دارد.
- مقدار `center` طوری عمل می‌کند که گویی هر دو مقدار برابر `center` هستند (یعنی `center center`).

> [!NOTE]
> برای توضیح دقیق تمام مقادیر موجود به صفحه مرجع مقدار [`<position-area>`](/en-US/docs/Web/CSS/Reference/Values/position-area_value) مراجعه کنید. ترکیب یک مقدار منطقی با یک مقدار فیزیکی، اعلام (declaration) را باطل می‌کند.

بیایید چند نمونه از این مقادیر را نشان دهیم؛ این مثال از همان HTML و استایل‌های پایه CSS مثال قبلی استفاده می‌کند، با این تفاوت که یک عنصر {{htmlelement("select")}} اضافه کرده‌ایم تا بتوانید مقدار `position-area` عنصر موقعیت‌یافته را تغییر دهید.

```html hidden
<p>
  Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor
  incididunt ut labore et dolore magna aliqua. Dui nunc mattis enim ut tellus
  elementum sagittis vitae et.
</p>

<div class="anchor">⚓︎</div>

<div class="infobox">
  <p>This is an information box.</p>
</div>

<p>
  Nisi quis eleifend quam adipiscing vitae proin sagittis nisl rhoncus. In arcu
  cursus euismod quis viverra nibh cras pulvinar. Vulputate ut pharetra sit amet
  aliquam.
</p>

<p>
  Malesuada nunc vel risus commodo viverra maecenas accumsan lacus. Vel elit
  scelerisque mauris pellentesque pulvinar pellentesque habitant morbi
  tristique. Porta lorem mollis aliquam ut porttitor. Turpis cursus in hac
  habitasse platea dictumst quisque. Dolor sit amet consectetur adipiscing elit.
  Ornare lectus sit amet est placerat. Nulla aliquet porttitor lacus luctus
  accumsan.
</p>

<form>
  <label for="position-area-select">Choose a position-area:</label>
  <select id="position-area-select" name="position-area-select">
    <option>top</option>
    <option>bottom</option>
    <option>left</option>
    <option>right</option>
    <option>start</option>
    <option>end</option>
    <option>top left</option>
    <option>top right</option>
    <option>bottom left</option>
    <option>bottom right</option>
    <option>top span-left</option>
    <option>bottom span-right</option>
    <option>start span-start</option>
    <option>end span-end</option>
    <option>center</option>
    <option>center span-all</option>
    <option>bottom center</option>
    <option>end span-all</option>
  </select>
</form>
```

```css hidden
.anchor {
  font-size: 1.8rem;
  color: white;
  text-shadow: 1px 1px 1px black;
  background-color: hsl(240 100% 75%);
  width: fit-content;
  border-radius: 10px;
  border: 1px solid black;
  padding: 3px;
}

.anchor {
  anchor-name: --my-anchor;
}

body {
  width: 50%;
  margin: 0 auto;
}

form {
  background: white;
  border: 1px solid black;
  padding: 5px;
}

select {
  display: block;
  margin-top: 5px;
}

form {
  position: fixed;
  top: 0;
  right: 2px;
}
```

به این infobox موقعیت‌دهی ثابت (fixed positioning) داده می‌شود و با استفاده از CSS به anchor مرتبط می‌شود. هنگام بارگذاری، با `position-area: top;` به anchor متصل می‌شود؛ در نتیجه در بالای شبکه‌ی position-area قرار می‌گیرد. این مقدار به محض انتخاب مقادیر مختلف از منوی `<select>` بازنویسی می‌شود.

```css hidden
.infobox {
  color: darkblue;
  background-color: azure;
  border: 1px solid #dddddd;
  padding: 10px;
  border-radius: 10px;
  font-size: 1rem;
}
```

```css
.infobox {
  position: fixed;
  position-anchor: --my-anchor;
  position-area: top;
}
```

همچنین یک اسکریپت کوتاه اضافه کرده‌ایم تا مقادیر جدید `position-area` انتخاب‌شده از منوی `<select>` را روی infobox اعمال کند:

```js
const infobox = document.querySelector(".infobox");
const selectElem = document.querySelector("select");

selectElem.addEventListener("change", () => {
  const area = selectElem.value;

  // Set the position-area to the value chosen in the select box
  infobox.style.positionArea = area;
});
```

مقادیر مختلف `position-area` را از منوی `<select>` انتخاب کنید تا تأثیر آن‌ها را روی موقعیت infobox ببینید:

### عرض عنصر موقعیت‌یافته

در مثال بالا، اندازه‌ی عنصر موقعیت‌یافته را در هیچ‌یک از ابعاد به‌صورت صریح تعیین نکرده‌ایم. عمداً از تعیین اندازه صرف‌نظر کرده‌ایم تا بتوانید رفتاری که این وضعیت ایجاد می‌کند را مشاهده کنید.

وقتی یک عنصر موقعیت‌یافته بدون تعیین اندازه‌ی صریح در خانه‌های شبکه‌ی `position-area` قرار می‌گیرد، با ناحیه‌ی مشخص‌شده هم‌تراز می‌شود و رفتاری مشابه وقتی دارد که `width` برابر با `max-content` تنظیم شده باشد. اندازه‌ی آن بر اساس اندازه‌ی [containing block](/en-US/docs/Web/CSS/Guides/Display/Containing_block) تعیین می‌شود که همان عرض محتوای آن است. این اندازه توسط `position: fixed` اعمال شده است. عناصر دارای موقعیت مطلق (absolute) و ثابت (fixed) با اندازه‌ی خودکار، به اندازه‌ای که برای جا دادن متن لازم است گسترش می‌یابند و لبه‌ی viewport محدودشان می‌کند. در این حالت، وقتی در سمت چپ شبکه با هر مقدار `left` یا `inline-start` قرار بگیرند، متن به خط بعد می‌رود. اگر اندازه‌ی `max-content` عنصر متصل‌شده از anchor کوچک‌تر یا کوتاه‌تر باشد، به اندازه‌ی anchor بزرگ نخواهد شد.

اگر عنصر موقعیت‌یافته به‌صورت عمودی وسط‌چین شود، مثلاً با `position-area: bottom center`، با خانه‌ی شبکه‌ی مشخص‌شده هم‌تراز می‌شود و عرض آن با عنصر anchor برابر خواهد بود. در این حالت، حداقل ارتفاع آن برابر با اندازه‌ی containing block عنصر anchor است. این عنصر سرریز نمی‌کند، زیرا `min-width` برابر با `min-content` است؛ یعنی حداقل به اندازه‌ی بلندترین کلمه‌ی خود عرض خواهد داشت.

## وسط‌چین کردن روی anchor با استفاده از `anchor-center`

هرچند می‌توانید عنصر متصل به anchor را با مقادیر `center` در `position-area` وسط‌چین کنید، ویژگی‌های inset به همراه تابع `anchor()` کنترل بیشتری روی موقعیت دقیق می‌دهند. CSS anchor positioning روشی برای وسط‌چین کردن یک عنصر متصل به anchor نسبت به anchor فراهم می‌کند، در حالی که برای اتصال، به‌جای `position-area` از ویژگی‌های inset استفاده می‌شود.

ویژگی‌های `justify-self`، `align-self`، `justify-items` و `align-items` (و شکل‌های کوتاه‌شده‌ی `place-items` و `place-self`) به توسعه‌دهندگان امکان می‌دهند تا عناصر را به‌راحتی در جهت inline یا block در سیستم‌های چیدمان مختلف تراز کنند؛ مثلاً در امتداد محور اصلی یا عرضی در مورد فرزندان flex. CSS anchor positioning مقدار دیگری به این ویژگی‌ها اضافه می‌کند به نام `anchor-center` که یک عنصر موقعیت‌یافته را با مرکز anchor پیش‌فرض آن هم‌تراز می‌کند.

این مثال از همان HTML و CSS پایه‌ای مثال قبلی استفاده می‌کند. به infobox موقعیت‌دهی ثابت داده شده و به لبه‌ی پایینی anchor متصل شده است. سپس از `justify-self: anchor-center` استفاده می‌شود تا مطمئن شویم که به‌صورت افقی روی مرکز anchor وسط‌چین است:

## تعیین اندازه عناصر بر اساس اندازه لنگر

علاوه بر موقعیت‌دهی یک عنصر نسبت به موقعیت لنگرش، می‌توانید اندازه یک عنصر را نیز نسبت به اندازه لنگرش با استفاده از تابع [`anchor-size()`](/en-US/docs/Web/CSS/Reference/Values/anchor-size) درون یک مقدار ویژگی اندازه‌دهی تعیین کنید.

ویژگی‌های اندازه‌دهی که می‌توانند مقدار `anchor-size()` را بپذیرند عبارتند از:

- {{cssxref("width")}}
- {{cssxref("height")}}
- {{cssxref("min-width")}}
- {{cssxref("min-height")}}
- {{cssxref("max-width")}}
- {{cssxref("max-height")}}
- {{cssxref("block-size")}}
- {{cssxref("inline-size")}}
- {{cssxref("min-block-size")}}
- {{cssxref("min-inline-size")}}
- {{cssxref("max-block-size")}}
- {{cssxref("max-inline-size")}}

توابع `anchor-size()` به مقادیر {{cssxref("length")}} تبدیل می‌شوند. سینتکس آن‌ها به این شکل است:

```plain
anchor-size(<anchor-name> <anchor-size>, <length-percentage>)
```

- `<anchor-name>`
  - : نام `<dashed-ident>` که به عنوان مقدار ویژگی {{cssxref("anchor-name")}} عنصر لنگر (که می‌خواهید عنصر را نسبت به آن اندازه‌دهی کنید) تنظیم شده است. اگر حذف شود، از **لنگر پیش‌فرض** عنصر (همان لنگری که در {{cssxref("position-anchor")}} به آن ارجاع داده شده) استفاده می‌شود.
- [`<anchor-size>`](/en-US/docs/Web/CSS/Reference/Values/anchor-size#anchor-size)
  - : ابعاد عنصر لنگر را مشخص می‌کند که عنصر موقعیت‌یافته نسبت به آن اندازه‌دهی می‌شود. این می‌تواند با مقادیر فیزیکی (`width` یا `height`) یا منطقی (`inline`، `block`، `self-inline`، یا `self-block`) بیان شود.
- {{cssxref("length-percentage")}}
  - : اندازه‌ای را مشخص می‌کند که در صورت عدم موقعیت‌دهی مطلق یا ثابت (fixed) عنصر، یا عدم وجود عنصر لنگر، به عنوان مقدار جایگزین استفاده شود.

رایج‌ترین توابع `anchor-size()` که استفاده خواهید کرد فقط به یک بعد از لنگر پیش‌فرض اشاره دارند. همچنین می‌توانید آن‌ها را درون توابع {{cssxref("calc")}} به کار ببرید تا اندازه اعمال‌شده روی عنصر موقعیت‌یافته را تغییر دهید.

برای مثال، این قانون عرض عنصر موقعیت‌یافته را برابر با عرض عنصر لنگر پیش‌فرض قرار می‌دهد:

```css
.elem {
  width: anchor-size(width);
}
```

این قانون اندازه inline عنصر موقعیت‌یافته را ۴ برابر اندازه inline عنصر لنگر قرار می‌دهد که ضرب درون تابع `calc()` انجام شده است:

```css
.elem {
  inline-size: calc(anchor-size(self-inline) * 4);
}
```

بیایید یک مثال را بررسی کنیم. HTML و CSS پایه مانند مثال‌های قبلی است، با این تفاوت که به عنصر anchor یک ویژگی [`tabindex="0"`](/en-US/docs/Web/HTML/Reference/Global_attributes/tabindex) داده شده تا قابل focus باشد. infobox همان‌طور که قبلاً دیدیم، موقعیت‌دهی ثابت (`fixed`) گرفته و به anchor متصل شده است. اما این بار با استفاده از `position-area` آن را به سمت راست anchor می‌چسبانیم و عرضی پنج برابر عرض anchor به آن می‌دهیم:

```html hidden
<p>
  Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor
  incididunt ut labore et dolore magna aliqua. Dui nunc mattis enim ut tellus
  elementum sagittis vitae et.
</p>

<div class="anchor" tabindex="0">⚓︎</div>

<div class="infobox">
  <p>This is an information box.</p>
</div>

<p>
  Nisi quis eleifend quam adipiscing vitae proin sagittis nisl rhoncus. In arcu
  cursus euismod quis viverra nibh cras pulvinar. Vulputate ut pharetra sit amet
  aliquam.
</p>

<p>
  Malesuada nunc vel risus commodo viverra maecenas accumsan lacus. Vel elit
  scelerisque mauris pellentesque pulvinar pellentesque habitant morbi
  tristique. Porta lorem mollis aliquam ut porttitor. Turpis cursus in hac
  habitasse platea dictumst quisque. Dolor sit amet consectetur adipiscing elit.
  Ornare lectus sit amet est placerat. Nulla aliquet porttitor lacus luctus
  accumsan.
</p>
```

```css hidden
.anchor {
  font-size: 1.8rem;
  color: white;
  text-shadow: 1px 1px 1px black;
  background-color: hsl(240 100% 75%);
  width: fit-content;
  border-radius: 10px;
  border: 1px solid black;
  padding: 3px;
}

.anchor {
  anchor-name: --my-anchor;
}

body {
  width: 50%;
  margin: 0 auto;
}

.infobox {
  color: darkblue;
  background-color: azure;
  border: 1px solid #dddddd;
  padding: 10px;
  border-radius: 10px;
  font-size: 1rem;
}
```

```css
.infobox {
  position: fixed;
  position-anchor: --my-anchor;
  position-area: right;
  margin-left: 5px;
  width: calc(anchor-size(width) * 5);
}
```

علاوه بر این، عرض عنصر anchor را در حالت‌های `:hover` و `:focus` افزایش می‌دهیم و یک `transition` به آن اضافه می‌کنیم تا هنگام تغییر حالت، به‌صورت انیمیشن تغییر کند.

```css
.anchor {
  text-align: center;
  width: 30px;
  transition: 1s width;
}

.anchor:hover,
.anchor:focus {
  width: 50px;
}
```

اگر نشانگر ماوس را روی عنصر anchor ببرید یا با Tab روی آن تمرکز کنید، عنصر موقعیت‌یافته (positioned element) همراه با anchor بزرگ می‌شود؛ این موضوع نشان می‌دهد که اندازه عنصر anchor-positioned نسبت به anchor خود تعریف شده است.

## سایر کاربردهای `anchor-size()`

همچنین می‌توانید از `anchor-size()` در خصوصیت‌های `inset` و `margin` فیزیکی و منطقی استفاده کنید. بخش‌های زیر این کاربردها را با جزئیات بیشتری بررسی می‌کنند و سپس یک مثال کاربردی ارائه می‌دهند.

### تنظیم موقعیت عنصر بر اساس اندازه anchor

می‌توانید تابع [`anchor-size()`](/en-US/docs/Web/CSS/Reference/Values/anchor-size) را در مقدار یک [inset property](/en-US/docs/Glossary/Inset_properties) استفاده کنید تا عناصر را بر اساس اندازه عنصر anchor خود موقعیت‌دهی کنید؛ برای مثال:

```css
left: anchor-size(width);
inset-inline-end: anchor-size(--my-anchor height, 100px);
```

این کار عنصر را نسبت به موقعیت anchor قرار نمی‌دهد، برخلاف تابع [`anchor()`](/en-US/docs/Web/CSS/Reference/Values/anchor) یا خصوصیت `position-area` (به بخش [Positioning elements relative to their anchor](#positioning_elements_relative_to_their_anchor) در بالا مراجعه کنید). در این حالت، موقعیت عنصر با جابه‌جایی anchor تغییر نمی‌کند؛ در عوض، طبق قوانین عادی موقعیت‌دهی `absolute` یا `fixed` قرار می‌گیرد.

این قابلیت در برخی موقعیت‌ها مفید است. برای مثال، اگر المان anchor شما فقط بتواند به صورت عمودی حرکت کند و همیشه به صورت افقی در کنار لبهٔ نزدیک‌ترین ancestor دارای position باقی بماند، می‌توانید از `left: anchor-size(width)` استفاده کنید تا المان anchor-positioned همیشه در سمت راست anchor قرار بگیرد، حتی اگر عرض anchor تغییر کند.

### تنظیم margin المان بر اساس اندازهٔ anchor

می‌توانید تابع [`anchor-size()`](/en-US/docs/Web/CSS/Reference/Values/anchor-size) را در مقدار یک property از خانوادهٔ `margin-*` استفاده کنید تا marginهای المان را بر اساس اندازهٔ المان anchor تنظیم کنید. برای مثال:

```css
margin-left: calc(anchor-size(width) / 4);
margin-block-start: anchor-size(--my-anchor self-block, 20px);
```

این کار زمانی مفید است که بخواهید margin المان anchor-positioned همیشه برابر با درصد ثابتی از عرض المان anchor باشد، حتی اگر عرض تغییر کند.

### مثال position و margin با `anchor-size()`

بیایید مثالی را بررسی کنیم که در آن margin و position یک المان anchor-positioned را نسبت به عرض المان anchor تنظیم می‌کنیم.

در HTML، دو المان `<div>` تعریف می‌کنیم: یکی به عنوان عنصر `anchor` و دیگری به عنوان المان `infobox` که آن را نسبت به anchor قرار می‌دهیم. به المان anchor یک attribute به نام [`tabindex`](/en-US/docs/Web/HTML/Reference/Global_attributes/tabindex) می‌دهیم تا بتوان آن را با کیبورد فوکوس کرد. همچنین برای اینکه `<body>` به اندازه‌ای بلند شود که نیاز به اسکرول داشته باشد، متن پرکننده‌ای اضافه می‌کنیم؛ اما برای اختصار، این بخش مخفی شده است.

```html hidden
<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit.</p>

<p>
  Nisi quis eleifend quam adipiscing vitae proin sagittis nisl rhoncus. In arcu
  cursus euismod quis viverra nibh cras pulvinar.
</p>
```

```html
<div class="anchor" tabindex="0">⚓︎</div>

<div class="infobox">
  <p>Infobox.</p>
</div>
```

```html hidden
<p>Vulputate ut pharetra sit amet aliquam.</p>

<p>
  Malesuada nunc vel risus commodo viverra maecenas accumsan lacus. Vel elit
  scelerisque mauris pellentesque pulvinar pellentesque habitant morbi
  tristique. Porta lorem mollis aliquam ut porttitor. Turpis cursus in hac
  habitasse platea dictumst quisque. Dolor sit amet consectetur adipiscing elit.
  Ornare lectus sit amet est placerat. Nulla aliquet porttitor lacus luctus
  accumsan.
</p>
```

در CSS، ابتدا `<div>` با کلاس `anchor` را با دادن یک `anchor-name` به عنوان المان anchor اعلام می‌کنیم. المان موقعیت‌دهی‌شده، property `position` آن برابر `absolute` است و از طریق property `position-anchor` به المان anchor مرتبط می‌شود. همچنین برای anchor و infobox ابعاد absolute برای `height` و `width` تنظیم می‌کنیم و برای anchor یک `transition` قرار می‌دهیم تا تغییرات عرض هنگام تغییر وضعیت، به نرمی انیمیت شود.

```css hidden
.anchor {
  font-size: 2rem;
  color: white;
  text-shadow: 1px 1px 1px black;
  background-color: hsl(240 100% 75%);
  text-align: center;
  align-content: center;
  outline: 1px solid black;
}

body {
  width: 80%;
  margin: 0 auto;
  position: relative;
}

.infobox {
  align-content: center;
  color: darkblue;
  background-color: azure;
  outline: 1px solid #dddddd;
  font-size: 1rem;
  text-align: center;
}
```

```css
.anchor {
  anchor-name: --my-anchor;
  width: 100px;
  height: 100px;
  transition: 1s all;
}

.infobox {
  position-anchor: --my-anchor;
  position: absolute;
  height: 100px;
  width: 100px;
}
```

حالا به جالب‌ترین بخش می‌رسیم. در اینجا، وقتی anchor هاور یا فوکوس شود، `width` آن را به `300px` تنظیم می‌کنیم. سپس این مقادیر را برای infobox تنظیم می‌کنیم:

- مقدار `top` را به `anchor(top)` تنظیم کنید. این باعث می‌شود لبهٔ بالای infobox همیشه با لبهٔ بالای anchor هم‌تراز بماند.
- مقدار `left` را به `anchor-size(width)` تنظیم کنید. این کار باعث می‌شود لبهٔ چپ infobox با فاصلهٔ مشخص‌شده از لبهٔ چپ نزدیک‌ترین ancestor دارای position قرار بگیرد. در اینجا، فاصلهٔ مشخص‌شده برابر با عرض عنصر anchor است و نزدیک‌ترین ancestor دارای position، عنصر `<body>` است؛ بنابراین infobox در سمت راست anchor نمایش داده می‌شود.
- مقدار `margin-left` را به `calc(anchor-size(width)/4)` تنظیم کنید. این باعث می‌شود infobox همیشه یک حاشیهٔ چپ به اندازهٔ یک‌چهارم عرض anchor از آن جدا کند.

```css
.anchor:hover,
.anchor:focus {
  width: 300px;
}

.infobox {
  top: anchor(top);
  left: anchor-size(width);
  margin-left: calc(anchor-size(width) / 4);
}
```

با فشردن کلید Tab به anchor بروید یا نشانگر ماوس را روی آن ببرید؛ می‌بینید که موقعیت و حاشیهٔ چپ infobox متناسب با عرض عنصر anchor بزرگ می‌شود.

## همچنین ببینید

- [CSS anchor positioning](/en-US/docs/Web/CSS/Guides/Anchor_positioning) ماژول
- [Fallback options and conditional hiding for overflow](/en-US/docs/Web/CSS/Guides/Anchor_positioning/Try_options_hiding) راهنما
- [Learn: Positioning](/en-US/docs/Learn_web_development/Core/CSS_layout/Positioning)
- [CSS logical properties and values](/en-US/docs/Web/CSS/Guides/Logical_properties_and_values) ماژول
- [Learn: Sizing items in CSS](/en-US/docs/Learn_web_development/Core/Styling_basics/Sizing)