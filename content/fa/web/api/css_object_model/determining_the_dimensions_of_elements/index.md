---
title: Determining the dimensions of elements
slug: Web/API/CSS_Object_Model/Determining_the_dimensions_of_elements
page-type: guide
---

{{DefaultAPISidebar("CSSOM")}}

برای تعیین عرض و ارتفاع عناصر، چندین ویژگی وجود دارد که می‌توانید به آن‌ها مراجعه کنید، و انتخاب ویژگی مناسب برای نیاز شما می‌تواند کمی گیج‌کننده باشد. هدف این مقاله کمک به شما در این تصمیم‌گیری است. توجه داشته باشید که همه این ویژگی‌ها فقط‌خواندنی هستند. اگر می‌خواهید عرض و ارتفاع یک عنصر را تنظیم کنید، از {{CSSxRef("width")}} و {{CSSxRef("height")}} یا ویژگی‌های جایگزین {{CSSxRef("min-width")}} و {{CSSxRef("max-width")}} و همچنین {{CSSxRef("min-height")}} و {{CSSxRef("max-height")}} استفاده کنید.

## چه مقدار فضا اشغال می‌کند؟

اگر نیاز دارید مجموع فضایی را که یک عنصر اشغال می‌کند بدانید — شامل عرض محتوای قابل‌مشاهده، نوارهای پیمایش (در صورت وجود)، padding و border — باید از ویژگی‌های {{DOMxRef("HTMLElement.offsetWidth")}} و {{DOMxRef("HTMLElement.offsetHeight")}} استفاده کنید. در بیشتر موارد، این مقادیر با عرض و ارتفاعِ {{DOMxRef("Element.getBoundingClientRect()")}} یکسان هستند، به شرطی که هیچ transform ای روی عنصر اعمال نشده باشد. در صورت وجود transform، ویژگی‌های `offsetWidth` و `offsetHeight` عرض و ارتفاع چیدمانی (layout) عنصر را برمی‌گردانند، در حالی که `getBoundingClientRect()` عرض و ارتفاع رندر شده را بازمی‌گرداند. به عنوان مثال، اگر عنصر دارای `width: 100px;` و `transform: scale(0.5);` باشد، `getBoundingClientRect()` عدد 50 را به عنوان عرض برمی‌گرداند، در حالی که `offsetWidth` عدد 100 را برمی‌گرداند. تفاوت دیگر این است که `offsetWidth` و `offsetHeight` مقادیر را به اعداد صحیح گرد می‌کنند، در حالی که `getBoundingClientRect()` مقادیر دقیق‌تری با اعشار ارائه می‌دهد.

![نحوه تعیین ویژگی‌های offsetWidth و offsetHeight با در نظر گرفتن padding، border و حاشیه خارجی (margin)](dimensions-offset.png)

## اندازه محتوای نمایش‌داده‌شده چقدر است؟

اگر نیاز دارید بدانید فضای اشغال‌شده توسط محتوای واقعاً نمایش‌داده‌شده چقدر است — شامل padding اما بدون border، حاشیه خارجی (margin) یا نوارهای پیمایش — باید از ویژگی‌های {{DOMxRef("Element.clientWidth")}} و {{DOMxRef("Element.clientHeight")}} استفاده کنید:

![نحوه تعیین ویژگی‌های clientWidth و clientHeight با در نظر گرفتن padding، border و حاشیه خارجی (margin)](dimensions-client.png)

## اندازه محتوا چقدر است؟

اگر نیاز دارید اندازه واقعی محتوا را بدانید، صرف‌نظر از اینکه چه مقدار از آن در حال حاضر قابل مشاهده است، باید از ویژگی‌های {{DOMxRef("Element.scrollWidth")}} و {{DOMxRef("Element.scrollHeight")}} استفاده کنید. این ویژگی‌ها عرض و ارتفاع کل محتوای یک عنصر را برمی‌گردانند، حتی اگر تنها بخشی از آن به دلیل استفاده از نوارهای پیمایش در حال حاضر قابل مشاهده باشد.

به عنوان مثال، اگر یک عنصر 600×400 پیکسلی در یک ظرف پیمایش‌پذیر 300×300 پیکسلی نمایش داده شود، `scrollWidth` مقدار 600 و `scrollHeight` مقدار 400 را برمی‌گرداند.

## همچنین ببینید

- مشخصات [The CSSOM View Module](https://drafts.csswg.org/cssom-view/)
- [MSDN: Measuring Element Dimension and Location](<https://learn.microsoft.com/en-us/previous-versions/hh781509(v=vs.85)>)