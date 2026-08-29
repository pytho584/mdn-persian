```markdown
# CSS آبشاری و وراثت

ماژول **آبشاری و وراثت در CSS** قوانین تخصیص مقادیر به ویژگی‌ها را از طریق مکانیزم‌های آبشاری (Cascading) و وراثت (Inheritance) تعریف می‌کند. این ماژول مشخص می‌کند که چگونه مقدار نهایی (مقدار مشخص‌شده) برای همهٔ ویژگی‌ها روی همهٔ عناصر پیدا می‌شود.

یکی از اصول بنیادی طراحی CSS، آبشاری بودن قوانین است. این اصل به چندین برگهٔ سبک (style sheet) اجازه می‌دهد که روی نمایش یک سند تأثیر بگذارند. اعلان‌های مقدار-ویژگی در CSS مشخص می‌کنند که یک سند چگونه رندر شود. ممکن است چندین اعلان، مقادیر متفاوتی را برای یک عنصر و ویژگی مشخص تعیین کنند، اما تنها یک مقدار می‌تواند به هر ویژگی CSS اعمال شود. ماژول آبشاری CSS نحوهٔ حل این تضادها را تعریف می‌کند.

برعکس این حالت نیز رخ می‌دهد. گاهی هیچ اعلانی برای تعیین مقدار یک ویژگی وجود ندارد. ماژول آبشاری CSS تعیین می‌کند که این مقادیر缺失 چگونه باید از طریق وراثت یا از مقدار اولیهٔ ویژگی تنظیم شوند.

> [!NOTE]
> قوانین مربوط به یافتن مقادیر مشخص‌شده در زمینهٔ صفحه (page context) و جعبه‌های حاشیهٔ آن در [ماژول صفحه‌آرایی CSS](/fa/docs/Web/CSS/Guides/Paged_media) توضیح داده شده است.

---

## 📋 مرجع

### ویژگی‌ها

| ویژگی | توضیح |
|-------|-------|
| {{cssxref("all")}} | بازنشانی همهٔ ویژگی‌های یک عنصر به حالت اولیه، وراثتی، یا لغو. |

---

### قوانین (@at-rules) و توصیف‌گرها

| قاعده/توصیف‌گر | توضیح |
|----------------|-------|
| {{cssxref("@import")}} | وارد کردن برگه‌های سبک خارجی. |
| {{cssxref("@layer")}} | تعریف لایه‌های آبشاری برای مدیریت اولویت سبک‌ها. |

---

### کلیدواژه‌ها

| کلیدواژه | توضیح |
|----------|-------|
| {{cssxref("initial")}} | مقدار اولیهٔ ویژگی را اعمال می‌کند. |
| {{cssxref("inherit")}} | مقدار را از عنصر والد به ارث می‌برد. |
| {{cssxref("revert")}} | مقدار را به مقدار پیش‌فرض مرورگر بازمی‌گرداند. |
| {{cssxref("revert-layer")}} | مقدار را به مقدار لایهٔ قبلی در آبشار بازمی‌گرداند. |
| {{cssxref("unset")}} | اگر ویژگی ارث‌بر است، مقدار را به ارث می‌برد؛ در غیر این صورت مقدار اولیه را اعمال می‌کند. |
| {{cssxref("important", "!important")}} | نشانه‌ای برای اولویت بالاتر در آبشار. |

---

### رابط‌ها (Interfaces)

| رابط | توضیح |
|------|-------|
| {{DOMXRef("CSSLayerBlockRule")}} | نمایانگر یک بلوک لایه در CSS. |
| {{DOMXRef("CSSGroupingRule")}} | نمایانگر قوانین گروهی در CSS. |
| {{DOMXRef("CSSLayerStatementRule")}} | نمایانگر یک عبارت لایه در CSS. |
| {{DOMXRef("CSSRule")}} | رابط پایه برای همهٔ قوانین CSS. |

---

### اصطلاحات واژه‌نامه

| اصطلاح | توضیح |
|--------|-------|
| [مقدار واقعی (Actual value)](/fa/docs/Web/CSS/Guides/Cascade/Property_value_processing#actual_value) | مقداری که پس از اعمال همهٔ محاسبات نهایی، در رندر نهایی استفاده می‌شود. |
| [لایهٔ ناشناس (Anonymous layer)](/fa/docs/Learn_web_development/Core/Styling_basics/Cascade_layers#the_layer_block_at-rule_for_named_and_anonymous_layers) | لایه‌ای که نام مشخصی ندارد. |
| [خاستگاه نویسنده (Author origin)](/fa/docs/Web/CSS/Guides/Cascade/Introduction#author_stylesheets) | سبک‌هایی که توسط نویسندهٔ صفحه (توسعه‌دهنده) نوشته می‌شوند. |
| [آبشار (Cascade)](/fa/docs/Web/CSS/Guides/Cascade/Introduction) | الگوریتمی که نحوهٔ ترکیب مقادیر ویژگی‌ها از منابع مختلف را تعیین می‌کند. |
| [مقدار محاسبه‌شده (Computed value)](/fa/docs/Web/CSS/Guides/Cascade/Property_value_processing#computed_value) | مقداری که پس از محاسبات اولیه (بدون در نظر گرفتن چیدمان) به دست می‌آید. |
| [مقدار اولیه (Initial value)](/fa/docs/Web/CSS/Guides/Cascade/Property_value_processing#initial_value) | مقدار پیش‌فرض یک ویژگی در صورت عدم وجود مقدار دیگر. |
| [لایهٔ نام‌دار (Named layer)](/fa/docs/Learn_web_development/Core/Styling_basics/Cascade_layers#the_layer_statement_at-rule_for_named_layers) | لایه‌ای که با یک نام مشخص تعریف می‌شود. |
| [مقدار نهایی (Resolved value)](/fa/docs/Web/CSS/Guides/Cascade/Property_value_processing#resolved_value) | مقداری که پس از اعمال همهٔ قوانین به دست می‌آید. |
| [ویژگی‌های فشرده (Shorthand properties)](/fa/docs/Web/CSS/Guides/Cascade/Shorthand_properties) | ویژگی‌هایی که چندین ویژگی را در یک عبارت جمع می‌کنند (مانند `margin`). |
| [اختصاصیت (Specificity)](/fa/docs/Web/CSS/Guides/Cascade/Specificity) | وزنی که به انتخابگرها تعلق می‌گیرد و اولویت را تعیین می‌کند. |
| [مقدار مشخص‌شده (Specified value)](/fa/docs/Web/CSS/Guides/Cascade/Property_value_processing#specified_value) | مقداری که از طریق اعلان‌های CSS یا وراثت به دست می‌آید. |
| {{glossary("style origin", "خاستگاه سبک")}} | منبع سبک (مرورگر، کاربر، یا نویسنده). |
| [مقدار استفاده‌شده (Used value)](/fa/docs/Web/CSS/Guides/Cascade/Property_value_processing#used_value) | مقداری که پس از اعمال چیدمان نهایی به دست می‌آید. |
| [خاستگاه کاربر (User origin)](/fa/docs/Web/CSS/Guides/Cascade/Introduction#user_stylesheets) | سبک‌هایی که توسط کاربر (مثلاً از طریق تنظیمات مرورگر) اعمال می‌شوند. |
| [خاستگاه عامل کاربر (User-agent origin)](/fa/docs/Web/CSS/Guides/Cascade/Introduction#user-agent_stylesheets) | سبک‌های پیش‌فرض مرورگر. |

---

## 📚 راهنماها

| عنوان راهنما | توضیح |
|--------------|-------|
| [آشنایی با آبشار CSS](/fa/docs/Web/CSS/Guides/Cascade/Introduction) | راهنمای الگوریتم آبشار که تعیین می‌کند عامل کاربر چگونه مقادیر ویژگی‌ها را از منابع مختلف ترکیب کند. |
| [وراثت در CSS](/fa/docs/Web/CSS/Guides/Cascade/Inheritance) | راهنمای وراثت در CSS. |
| [یادگیری: مدیریت تضادها](/fa/docs/Learn_web_development/Core/Styling_basics/Handling_conflicts) | مفاهیم بنیادی CSS — آبشار، اختصاصیت و وراثت — که نحوهٔ اعمال CSS به HTML و حل تضادها را کنترل می‌کنند. |
| [یادگیری: لایه‌های آبشاری](/fa/docs/Learn_web_development/Core/Styling_basics/Cascade_layers) | آشنایی با [لایه‌های آبشاری](/fa/docs/Web/CSS/Reference/At-rules/@layer)، یک ویژگی پیشرفته‌تر که بر اساس مفاهیم بنیادی [آبشار CSS](/fa/docs/Web/CSS/Guides/Cascade/Introduction) و [اختصاصیت CSS](/fa/docs/Web/CSS/Guides/Cascade/Specificity) ساخته شده است. |

---

## 🔗 مفاهیم مرتبط

| مفهوم | توضیح |
|-------|-------|
| [سبک‌های متصل به عنصر (Element-attached styles)](/fa/docs/Web/HTML/Reference/Global_attributes/style) | استفاده از ویژگی `style` درون‌خطی روی عناصر HTML. |
| [سبک‌های درون‌خطی و آبشار](/fa/docs/Web/CSS/Guides/Cascade/Introduction#inline_styles) | نحوهٔ تأثیر سبک‌های درون‌خطی در اولویت آبشار. |
| [قوانین شرطی برای @import](/fa/docs/Web/CSS/Reference/At-rules/@import#importing_css_rules_conditional_on_media_queries) | وارد کردن شرطی فایل‌های CSS بر اساس شرط‌های رسانه (media queries). |
| [نحو تعریف مقدار](/fa/docs/Web/CSS/Guides/Values_and_units/Value_definition_syntax) | نحو استاندارد برای تعریف مقادیر قابل‌قبول در CSS. |

---

## 📐 مشخصات

مشخصات فنی در لینک‌های زیر قابل مشاهده است:

- [CSS Cascade Level 5](https://drafts.csswg.org/css-cascade-5/)
- [CSS Cascade Level 6](https://drafts.csswg.org/css-cascade-6/)

---

## 👀 همچنین ببینید

- ماژول [انتخابگرهای CSS](/fa/docs/Web/CSS/Guides/Selectors)
- ماژول [شبه‌عناصر CSS](/fa/docs/Web/CSS/Guides/Pseudo-elements)
- ماژول [صفحه‌آرایی CSS](/fa/docs/Web/CSS/Guides/Paged_media)
- ماژول [قوانین شرطی CSS](/fa/docs/Web/CSS/Guides/Conditional_rules)
- ماژول [تودرتو در CSS](/fa/docs/Web/CSS/Guides/Nesting)
- [ویژگی‌های فشرده](/fa/docs/Web/CSS/Guides/Cascade/Shorthand_properties)
```

---

### 📌 توضیح اضافه (برای درک بهتر)

این ماژول یکی از مهم‌ترین مفاهیم CSS را پوشش می‌دهد:

- **آبشار (Cascade)**: وقتی چندین قانون CSS به یک عنصر اشاره می‌کنند، مرورگر باید تصمیم بگیرد کدام یک اعمال شود. ترتیب اولویت به این صورت است:
  1. **اهمیت** (`!important` بالاترین اولویت را دارد)
  2. **خاستگاه** (مرورگر < کاربر < نویسنده)
  3. **اختصاصیت** (انتخابگرهای خاص‌تر وزن بیشتری دارند)
  4. **ترتیب ظاهر شدن** (قوانین آخرین اولویت بیشتری دارند)

- **وراثت (Inheritance)**: برخی ویژگی‌ها (مانند `color` و `font-family`) به‌طور خودکار از والد به فرزند منتقل می‌شوند، مگر اینکه مقدار دیگری برای فرزند تعیین شود.

- **لایه‌های آبشاری (Cascade Layers)**: امکان دسته‌بندی سبک‌ها و کنترل دقیق‌تر اولویت آن‌ها را فراهم می‌کند، بدون اینکه نیاز به افزایش اختصاصیت یا استفاده از `!important` باشد.
