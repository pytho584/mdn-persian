---
title: "console"
slug: Web/API/console
page-type: web-api-interface
browser-compat: api.console
---

{{APIRef("Console API")}} {{AvailableInWorkers}}

شیء **`console`** دسترسی به کنسول اشکال‌زدایی (مثل [کنسول وب](https://firefox-source-docs.mozilla.org/devtools-user/web_console/index.html) در فایرفاکس) را فراهم می‌کند.

پیاده‌سازی‌های API کنسول ممکن است در محیط‌های اجرایی مختلف متفاوت باشند. به‌ویژه، برخی از متدهای console ممکن است در بعضی ویرایشگرهای آنلاین و IDE ها به‌شکل متفاوتی کار کنند یا اصلاً کار نکنند. برای مشاهدهٔ رفتار توصیف‌شده در این مستندات، متدها را در ابزارهای توسعه‌دهندهٔ مرورگر خود امتحان کنید، هرچند در آنجا نیز بین مرورگرها تفاوت‌هایی وجود دارد.

شیء `console` در هر حوزهٔ سراسری (global scope) در دسترس است. برای مثال:

```js
console.log("Failed to open the specified link");
```

## متدهای نمونه

- {{domxref("console/assert_static", "console.assert()")}}
  - : اگر اولین آرگومان `false` باشد، یک پیام خطا در کنسول ثبت می‌کند.
- {{domxref("console/clear_static", "console.clear()")}}
  - : کنسول را پاک می‌کند.
- {{domxref("console/count_static", "console.count()")}}
  - : تعداد دفعاتی که این خط با برچسب داده‌شده فراخوانی شده است را ثبت می‌کند.
- {{domxref("console/countReset_static", "console.countReset()")}}
  - : مقدار شمارنده با برچسب داده‌شده را بازنشانی می‌کند.
- {{domxref("console/debug_static", "console.debug()")}}
  - : پیامی را با سطح ثبت اشکال‌زدایی در کنسول خروجی می‌دهد.
- {{domxref("console/dir_static", "console.dir()")}}
  - : فهرست تعاملی از ویژگی‌های یک شیء جاوااسکریپتی مشخص را نمایش می‌دهد. این فهرست به شما امکان می‌دهد با مثلث‌های بازشو محتوای اشیاء فرزند را بررسی کنید.
- {{domxref("console/dirxml_static", "console.dirxml()")}}
  - : در صورت امکان، نمایشی از عنصر XML/HTML شیء مشخص‌شده، و در غیر این صورت نمایش شیء جاوااسکریپت را نشان می‌دهد.
- {{domxref("console/error_static", "console.error()")}}
  - : پیامی را با سطح ثبت خطا در کنسول خروجی می‌دهد.
- `console.exception()` {{Non-standard_inline}} {{deprecated_inline}}
  - : نام مستعار `console.error()` است.
- {{domxref("console/group_static", "console.group()")}}
  - : یک [گروه](#using_groups_in_the_console) جدید ایجاد می‌کند و تمام خروجی‌های بعدی را یک سطح تو رفتگی می‌دهد. برای بازگشت به سطح قبلی، `console.groupEnd()` را فراخوانی کنید.
- {{domxref("console/groupCollapsed_static", "console.groupCollapsed()")}}
  - : یک [گروه](#using_groups_in_the_console) جدید ایجاد می‌کند و تمام خروجی‌های بعدی را یک سطح تو رفتگی می‌دهد. با این حال، برخلاف `console.group()`، این گروه به‌صورت جمع‌شده شروع می‌شود و برای باز کردن آن باید از دکمهٔ بازشو استفاده کنید. برای بازگشت به سطح قبلی، `console.groupEnd()` را فراخوانی کنید.
- {{domxref("console/groupEnd_static", "console.groupEnd()")}}
  - : از [گروه](#using_groups_in_the_console) فعلی خارج می‌شود.
- {{domxref("console/info_static", "console.info()")}}
  - : پیامی را با سطح ثبت اطلاعات در کنسول خروجی می‌دهد.
- {{domxref("console/log_static", "console.log()")}}
  - : یک پیام را در کنسول خروجی می‌دهد.
- {{domxref("console/profile_static", "console.profile()")}} {{Non-standard_inline}}
  - : پروفایلر داخلی مرورگر را شروع می‌کند (مثلاً [ابزار عملکرد فایرفاکس](https://firefox-source-docs.mozilla.org/devtools-user/performance/index.html)). می‌توانید یک نام اختیاری برای پروفایل تعیین کنید.
- {{domxref("console/profileEnd_static", "console.profileEnd()")}} {{Non-standard_inline}}
  - : پروفایلر را متوقف می‌کند. می‌توانید پروفایل حاصل را در ابزار عملکرد مرورگر مشاهده کنید (مثلاً [ابزار عملکرد فایرفاکس](https://firefox-source-docs.mozilla.org/devtools-user/performance/index.html)).
- {{domxref("console/table_static", "console.table()")}}
  - : داده‌های جدولی را به‌صورت یک جدول نمایش می‌دهد.
- {{domxref("console/time_static", "console.time()")}}
  - : یک [تایمر](#timers) با نام مشخص‌شده به‌عنوان پارامتر ورودی شروع می‌کند. در یک صفحه می‌توان تا ۱۰٬۰۰۰ تایمر هم‌زمان اجرا کرد.
- {{domxref("console/timeEnd_static", "console.timeEnd()")}}
  - : [تایمر](#timers) مشخص‌شده را متوقف کرده و زمان سپری‌شده بر حسب میلی‌ثانیه از زمان شروع را ثبت می‌کند.
- {{domxref("console/timeLog_static", "console.timeLog()")}}
  - : مقدار [تایمر](#timers) مشخص‌شده را در کنسول ثبت می‌کند.
- {{domxref("console/timeStamp_static", "console.timeStamp()")}} {{Non-standard_inline}}
  - : یک نشانگر به خط زمانی ابزار عملکرد مرورگر اضافه می‌کند ([Chrome](https://developer.chrome.com/docs/devtools/performance/reference) یا [Firefox](https://profiler.firefox.com/docs/#/./guide-ui-tour-timeline)).
- {{domxref("console/trace_static", "console.trace()")}}
  - : یک [ردیابی پشته](#stack_traces) را خروجی می‌دهد.
- {{domxref("console/warn_static", "console.warn()")}}
  - : پیامی را با سطح ثبت هشدار در کنسول خروجی می‌دهد.

## مثال‌ها

### خروجی متن به کنسول

متداول‌ترین قابلیت کنسول، ثبت متن و سایر داده‌ها است. با استفاده از متدهای {{domxref("console/log_static", "console.log()")}}، {{domxref("console/info_static", "console.info()")}}، {{domxref("console/warn_static", "console.warn()")}}، {{domxref("console/error_static", "console.error()")}} یا {{domxref("console/debug_static", "console.debug()")}} می‌توانید دسته‌های مختلفی از خروجی تولید کنید. هر یک از این‌ها خروجی با استایل متفاوتی در لاگ ایجاد می‌کنند و می‌توانید از کنترل‌های فیلتر مرورگر خود برای مشاهدهٔ تنها انواع خروجی موردنظر استفاده کنید.

دو روش برای استفاده از هر یک از متدهای خروجی وجود دارد:

- تعداد متغیری آرگومان ارسال کنید که نمایش رشته‌ای آن‌ها در یک رشته ترکیب می‌شود و سپس در کنسول خروجی داده می‌شود.
- رشته‌ای حاوی صفر یا چند رشتهٔ جایگزین (substitution string) ارسال کنید و سپس تعداد متغیری آرگومان برای جایگزینی آن‌ها.

#### خروجی یک شیء

ساده‌ترین روش استفاده از متدهای ثبت، خروجی گرفتن از یک شیء واحد است:

```js
const someObject = { str: "Some text", id: 5 };
console.log(someObject);
```

خروجی چیزی شبیه به این است:

```plain
{str:"Some text", id:5}
```

مرورگر تا حد ممکن و به دلخواه خود اطلاعاتی دربارهٔ شیء نمایش می‌دهد. برای مثال، ممکن است حالت خصوصی (private state) شیء نیز نمایش داده شود. برخی انواع اشیاء، مانند عناصر DOM یا توابع، ممکن است به شکل خاصی نمایش داده شوند.

#### عکس فوری از اشیاء (Snapshotting)

اطلاعات مربوط به یک شیء به‌صورت تنبل (lazily) بازیابی می‌شود. یعنی پیام لاگ، محتوای شیء را در زمانی که برای اولین بار مشاهده می‌شود نشان می‌دهد، نه زمانی که ثبت شده است. برای مثال:

```js
const obj = {};
console.log(obj);
obj.prop = 123;
```

این کد خروجی `{}` را می‌دهد. با این حال، اگر جزئیات شیء را باز کنید، `prop: 123` را مشاهده خواهید کرد.

اگر قصد تغییر شیء خود را دارید و می‌خواهید از به‌روزرسانی اطلاعات ثبت‌شده جلوگیری کنید، می‌توانید قبل از ثبت، شیء را [شبیه‌سازی عمیق](/en-US/docs/Glossary/Deep_copy) کنید. یک روش رایج این است که آن را با {{jsxref("JSON.stringify()")}} و سپس {{jsxref("JSON.parse()")}} کنید:

```js
console.log(JSON.parse(JSON.stringify(obj)));
```

جایگزین‌های دیگری نیز وجود دارند که در مرورگرها کار می‌کنند، مانند {{DOMxRef("Window.structuredClone", "structuredClone()")}}، که در شبیه‌سازی انواع مختلف اشیاء مؤثرتر هستند.

#### خروجی چند شیء

همچنین می‌توانید با فهرست کردن چند شیء هنگام فراخوانی متد ثبت، آن‌ها را خروجی بگیرید، مانند این:

```js
const car = "Dodge Charger";
const someObject = { str: "Some text", id: 5 };
console.info("My first car was a", car, ". The object is:", someObject);
```

خروجی به این شکل خواهد بود:

```plain
My first car was a Dodge Charger . The object is: {str:"Some text", id:5}
```

#### استفاده از جایگزینی رشته‌ها

اولین پارامتر متدهای ثبت می‌تواند رشته‌ای حاوی صفر یا چند رشتهٔ جایگزین باشد. هر رشتهٔ جایگزین با مقدار آرگومان متناظر جایگزین می‌شود.

- `%o`
  - : یک شیء جاوااسکریپت را با سبک «قالب‌بندی بهینهٔ مفید» خروجی می‌دهد؛ برای مثال عناصر DOM ممکن است به همان شکلی که در عنصرنگار (element inspector) دیده می‌شوند نمایش داده شوند.
- `%O`
  - : یک شیء جاوااسکریپت را با سبک «قالب‌بندی عمومی اشیاء جاوااسکریپت» خروجی می‌دهد، معمولاً به‌صورت یک درخت بازشو. این مشابه {{domxref("console/dir_static", "console.dir()")}} است.
- `%d` یا `%i`
  - : یک عدد صحیح را خروجی می‌دهد.
- `%s`
  - : یک رشته را خروجی می‌دهد.
- `%f`
  - : یک مقدار اعشاری را خروجی می‌دهد.
- `%c`
  - : قوانین استایل CSS را بر تمام متن‌های بعدی اعمال می‌کند. به [استایل‌دهی خروجی کنسول](#styling_console_output) مراجعه کنید.

برخی مرورگرها ممکن است مشخص‌کننده‌های قالب اضافی نیز پیاده‌سازی کنند. برای مثال، Safari و Firefox از قالب‌بندی دقت به سبک C یعنی `%.<precision>f` پشتیبانی می‌کنند. برای مثال `console.log("Foo %.2f", 1.1)` عدد را با ۲ رقم اعشار خروجی می‌دهد: `Foo 1.10`، در حالی که `console.log("Foo %.2d", 1.1)` عدد را با دو رقم با اهمیت و صفر آغازین خروجی می‌دهد: `Foo 01`.

هر یک از این‌ها آرگومان بعد از رشتهٔ قالب را از فهرست پارامتر برمی‌دارد. برای مثال:

```js
for (let i = 0; i < 5; i++) {
  console.log("Hello, %s. You've called me %d times.", "Bob", i + 1);
}
```

خروجی به این شکل است:

```plain
Hello, Bob. You've called me 1 times.
Hello, Bob. You've called me 2 times.
Hello, Bob. You've called me 3 times.
Hello, Bob. You've called me 4 times.
Hello, Bob. You've called me 5 times.
```

#### استایل‌دهی خروجی کنسول

می‌توانید از دستور `%c` برای اعمال استایل CSS بر خروجی کنسول استفاده کنید:

```js
console.log(
  "This is %cMy stylish message",
  "color: yellow; font-style: italic; background-color: blue;padding: 2px",
);
```

متنی که قبل از دستور است تحت تأثیر قرار نمی‌گیرد، اما متن بعد از دستور با استفاده از اعلان‌های CSS موجود در پارامتر استایل می‌گیرد.

![Styled Text in Firefox console](css-styling.png)

می‌توانید `%c` را چند بار استفاده کنید:

<!-- cSpell:ignore corange cred -->

```js
console.log(
  "Multiple styles: %cred %corange",
  "color: red",
  "color: orange",
  "Additional unformatted message",
);
```

ویژگی‌های قابل استفاده همراه با نحو `%c` به شرح زیر هستند (حداقل در Firefox — ممکن است در مرورگرهای دیگر متفاوت باشند):

- {{cssxref("background")}} و معادل‌های longhand آن
- {{cssxref("border")}} و معادل‌های longhand آن
- {{cssxref("border-radius")}}
- {{cssxref("box-decoration-break")}}
- {{cssxref("box-shadow")}}
- {{cssxref("clear")}} و {{cssxref("float")}}
- {{cssxref("color")}}
- {{cssxref("cursor")}}
- {{cssxref("display")}}
- {{cssxref("font")}} و معادل‌های longhand آن
- {{cssxref("line-height")}}
- {{cssxref("margin")}}
- {{cssxref("outline")}} و معادل‌های longhand آن
- {{cssxref("padding")}}
- ویژگی‌های `text-*` مانند {{cssxref("text-transform")}}
- {{cssxref("white-space")}}
- {{cssxref("word-spacing")}} و {{cssxref("word-break")}}
- {{cssxref("writing-mode")}}

> [!NOTE]
> هر پیام کنسول به‌صورت پیش‌فرض مانند یک عنصر inline رفتار می‌کند. اگر می‌خواهید ویژگی‌هایی مانند `padding`، `margin` و غیره اثری داشته باشند، می‌توانید ویژگی `display` را روی `display: inline-block` تنظیم کنید.

> [!NOTE]
> برای پشتیبانی از هر دو طرح رنگ روشن و تیره، می‌توان هنگام مشخص‌کردن رنگ‌ها از {{cssxref("color_value/light-dark")}} استفاده کرد؛ برای مثال: `color: light-dark(#D00000, #FF4040);`

### استفاده از گروه‌ها در کنسول

می‌توانید از گروه‌های تودرتو برای سازمان‌دهی خروجی خود با ترکیب بصری مطالب مرتبط استفاده کنید. برای ایجاد یک بلوک تودرتوی جدید، `console.group()` را فراخوانی کنید. متد `console.groupCollapsed()` مشابه است، اما بلوک جدید را جمع‌شده ایجاد می‌کند و برای باز کردن آن برای خواندن، باید از دکمهٔ بازشو استفاده کنید.

برای خروج از گروه فعلی، `console.groupEnd()` را فراخوانی کنید. برای مثال، با این کد:

```js
console.log("This is the outer level");
console.group("First group");
console.log("In the first group");
console.group("Second group");
console.log("In the second group");
console.warn("Still in the second group");
console.groupEnd();
console.log("Back to the first group");
console.groupEnd();
console.debug("Back to the outer level");
```

خروجی به این شکل است:

![Demo of nested groups in Firefox console](console_g