---
title: "Introduction to the CSS box model"
source: "https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Box_model/Introduction"
translated_by: "n8n + AI"
---

هنگام چیدمان یک سند، موتور رندر مرورگر هر عنصر را طبق استاندارد «مدل جعبهٔ پایهٔ CSS» (CSS basic box model) به شکل یک جعبهٔ مستطیلی نمایش می‌دهد. CSS اندازه، موقعیت و ویژگی‌های (رنگ، پس‌زمینه، اندازهٔ حاشیه و…) این جعبه‌ها را تعیین می‌کند.

هر جعبه از چهار بخش (یا _ناحیه_) تشکیل شده است که با لبه‌های مربوط به خود تعریف می‌شوند: _لبهٔ محتوا_، _لبهٔ padding_، _لبهٔ border_ و _لبهٔ margin_.

![مدل جعبه CSS](boxmodel.png)

## ناحیهٔ محتوا

**ناحیهٔ محتوا (content area)** که با لبهٔ محتوا محدود می‌شود، «محتوای واقعی» عنصر را دربر می‌گیرد؛ مثل متن، تصویر یا پخش‌کنندهٔ ویدیو. ابعاد آن برابر با _عرض محتوا_ (یا _عرض content-box_) و _ارتفاع محتوا_ (یا _ارتفاع content-box_) است. این ناحیه اغلب دارای رنگ یا تصویر پس‌زمینه است.

اگر ویژگی `box-sizing` روی `content-box` (پیش‌فرض) تنظیم شده باشد و عنصر یک عنصر block باشد، اندازهٔ ناحیهٔ محتوا را می‌توان به‌صورت صریح با ویژگی‌های `width`، `min-width`، `max-width`، `height`، `min-height` و `max-height` تعریف کرد.

## ناحیهٔ padding

**ناحیهٔ padding (padding area)** که با لبهٔ padding محدود می‌شود، ناحیهٔ محتوا را گسترش می‌دهد تا padding عنصر را شامل شود. ابعاد آن برابر با _عرض padding-box_ و _ارتفاع padding-box_ است.

ضخامت padding توسط ویژگی‌های `padding-top`، `padding-right`، `padding-bottom`، `padding-left` و ویژگی کوتاه‌نویس `padding` تعیین می‌شود.

## ناحیهٔ border

**ناحیهٔ border (border area)** که با لبهٔ border محدود می‌شود، ناحیهٔ padding را گسترش می‌دهد تا borderهای عنصر را شامل شود. ابعاد آن برابر با _عرض border-box_ و _ارتفاع border-box_ است.

ضخامت borderها توسط ویژگی‌های `border-width` و ویژگی کوتاه‌نویس `border` تعیین می‌شود. اگر ویژگی `box-sizing` روی `border-box` تنظیم شده باشد، اندازهٔ ناحیهٔ border را می‌توان به‌صورت صریح با ویژگی‌های `width`، `min-width`، `max-width`، `height`، `min-height` و `max-height` تعریف کرد. وقتی روی یک جعبه پس‌زمینه (`background-color` یا `background-image`) تنظیم شده باشد، تا لبهٔ بیرونی border گسترش می‌یابد (یعنی در ترتیب z در زیر border قرار می‌گیرد). این رفتار پیش‌فرض را می‌توان با ویژگی CSS `background-clip` تغییر داد.

## ناحیهٔ margin

**ناحیهٔ margin (margin area)** که با لبهٔ margin محدود می‌شود، ناحیهٔ border را گسترش می‌دهد تا یک ناحیهٔ خالی را شامل شود که برای جدا کردن عنصر از همسایگانش استفاده می‌شود. ابعاد آن برابر با _عرض margin-box_ و _ارتفاع margin-box_ است.

اندازهٔ ناحیهٔ margin توسط ویژگی‌های `margin-top`، `margin-right`، `margin-bottom`، `margin-left` و ویژگی کوتاه‌نویس `margin` تعیین می‌شود. وقتی [جمع‌شدن حاشیه‌ها (margin collapsing)](/en-US/docs/Web/CSS/Guides/Box_model/Margin_collapsing) رخ می‌دهد، ناحیهٔ margin به‌طور واضح تعریف نمی‌شود؛ زیرا marginها بین جعبه‌ها به اشتراک گذاشته می‌شوند.

در نهایت، توجه کنید که برای عناصر inline جایگزین‌نشده (non-replaced inline elements)، مقدار فضای اشغال‌شده (سهم در ارتفاع خط) توسط ویژگی `line-height` تعیین می‌شود؛ حتی اگر border و padding همچنان دور محتوا نمایش داده شوند.

## جستارهای وابسته

- [مدل جعبه CSS](/en-US/docs/Web/CSS/Guides/Box_model) ماژول
- [Layout و بلوک شامل](/en-US/docs/Web/CSS/Guides/Display/Containing_block)
- [آشنایی با آبشار CSS](/en-US/docs/Web/CSS/Guides/Cascade/Introduction)
- [یادگیری: مدیریت تعارض‌ها](/en-US/docs/Learn_web_development/Core/Styling_basics/Handling_conflicts)
- مفاهیم کلیدی CSS:
  - [سینتکس CSS](/en-US/docs/Web/CSS/Guides/Syntax/Introduction)
  - [At-ruleها](/en-US/docs/Web/CSS/Guides/Syntax/At-rules)
  - [کامنت‌ها](/en-US/docs/Web/CSS/Guides/Syntax/Comments)
  - [اختصاصیت](/en-US/docs/Web/CSS/Guides/Cascade/Specificity)
  - [ارث‌بری](/en-US/docs/Web/CSS/Guides/Cascade/Inheritance)
  - [حالت‌های چیدمان](/en-US/docs/Glossary/Layout_mode)
  - [مدل قالب‌بندی بصری](/en-US/docs/Web/CSS/Guides/Display/Visual_formatting_model)
  - [فروپاشی حاشیه](/en-US/docs/Web/CSS/Guides/Box_model/Margin_collapsing)
  - مقادیر:
    - [مقادیر اولیه](/en-US/docs/Web/CSS/Guides/Cascade/Property_value_processing#initial_value)
    - [مقادیر محاسبه‌شده](/en-US/docs/Web/CSS/Guides/Cascade/Property_value_processing#computed_value)
    - [مقادیر استفاده‌شده](/en-US/docs/Web/CSS/Guides/Cascade/Property_value_processing#used_value)
    - [مقادیر واقعی](/en-US/docs/Web/CSS/Guides/Cascade/Property_value_processing#actual_value)
  - [سینتکس تعریف مقدار](/en-US/docs/Web/CSS/Guides/Values_and_units/Value_definition_syntax)
  - [خصوصیت‌های shorthand](/en-US/docs/Web/CSS/Guides/Cascade/Shorthand_properties)