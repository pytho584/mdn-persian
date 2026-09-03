---
title: "استفاده از فراخوان‌های علاقه‌مندی"
---

---
title: Using interest invokers
slug: Web/API/Popover_API/Using_interest_invokers
page-type: guide
---

{{DefaultAPISidebar("Popover API")}}

**فراخوان‌های علاقه‌مندی** (Interest invokers) سازوکاری را برای به‌روزرسانی یک رابط کاربری یا اجرای کد سفارشی هنگامی که کاربر به یک عنصر «علاقه نشان می‌دهد» یا «علاقه‌اش را از دست می‌دهد» (مثلاً با هاور کردن یا برداشتن هاور از روی آن) فراهم می‌کنند. این فراخوان‌ها معمولاً برای نمایش و پنهان‌کردن پاپ‌اورها استفاده می‌شوند. این راهنما مفاهیم پشت فراخوان‌های علاقه‌مندی، موارد استفاده از آن‌ها و نحوه استفاده از آن‌ها را توضیح می‌دهد.

## مفاهیم

API پاپ‌اور قابلیت نمایش یک پاپ‌اور را زمانی فراهم می‌کند که یک عنصر کنترلی مرتبط (که **فراخوان** یا invoker نامیده می‌شود) فعال شود، برای مثال وقتی روی آن کلیک می‌شود. این ویژگی برای نمایش عناصر رابط کاربری مانند پنجره‌های مودال و پنل‌های اطلاعاتی مفید است. می‌توانید [پاپ‌اورهای اعلانی ایجاد کنید](/en-US/docs/Web/API/Popover_API/Using#creating_declarative_popovers) با استفاده از ویژگی [`popover`](/en-US/docs/Web/HTML/Reference/Global_attributes/popover) به همراه [`popovertarget`](/en-US/docs/Web/HTML/Reference/Elements/button#popovertarget) یا [`commandfor`](/en-US/docs/Web/HTML/Reference/Elements/button#commandfor).

علاوه بر این پاپ‌اورهای مبتنی بر فعال‌سازی، یک نیاز رایج نیز وجود دارد: نمایش یک پاپ‌اور وقتی که کاربر روی یک عنصر کنترلی هاور می‌کند یا آن را فوکوس می‌کند – تعاملاتی که نشان‌دهنده علاقه کاربر هستند. برای مثال، بسیاری از سایت‌های اجتماعی و انجمنی به کاربران اجازه می‌دهند روی پیوندی به صفحه پروفایل یک شخص یا گروه هاور کنند تا پاپ‌اوری با اطلاعات بیشتر نمایش داده شود. این پیش‌نمایش سریع به کاربران کمک می‌کند تصمیم بگیرند که آیا می‌خواهند به صفحه کامل بروند یا نه. چنین پاپ‌اورهایی ممکن است حاوی اقدامات سریع نیز باشند، مانند «دنبال کردن» یا «عضویت در گروه»، که به کاربران امکان می‌دهد بدون از دست دادن زمینه فعلی خود اقدامی انجام دهند.

فراخوان‌های علاقه‌مندی به مرورگر این امکان را می‌دهند که رفتار پاپ‌اور مبتنی بر علاقه را به روشی سازگار و قابل دسترس، بدون نیاز به جاوااسکریپت، فراهم کند. مرورگر تعیین می‌کند که چه زمانی کاربر به یک عنصر علاقه نشان می‌دهد و بنابراین چه زمانی باید اقدامی انجام شود. «نشان دادن علاقه» معمولاً زمانی رخ می‌دهد که کاربر عنصر را هاور می‌کند، فوکوس می‌کند یا مدت‌ها فشار می‌دهد (ماهیت دقیق «علاقه» ممکن است در مرورگرهای مختلف متفاوت باشد)، و «از دست دادن علاقه» معمولاً زمانی اتفاق می‌افتد که کاربر تعامل با عنصر را متوقف کند.

مرورگر همچنین رویدادهایی را هنگام کسب یا از دست دادن علاقه شلیک می‌کند، بنابراین می‌توانید در پاسخ، کد سفارشی اجرا کنید. علاوه بر این، این ویژگی شامل ویژگی‌ها و انتخابگرهای CSS برای استایل‌دهی به عناصر بر اساس علاقه است.

> [!NOTE]
> در دستگاه‌هایی که کلید <kbd>Esc</kbd> در دسترس است، فشار دادن آن همه علاقه‌مندی‌ها را لغو می‌کند. این یک سازوکار فرار کلی فراهم می‌کند اگر تعامل حواس‌پرت‌کننده یا ناخواسته شود.

همچنین می‌توانید از فراخوان‌های علاقه‌مندی برای اجرای کد سفارشی در [موارد غیر پاپ‌اوری](#استفاده-از-فراخوان‌های-علاقه‌مندی-بدون-پاپ‌اور) استفاده کنید. با این حال، این راهنما عمدتاً بر پاپ‌اورها تمرکز دارد، زیرا آن‌ها رایج‌ترین کاربرد فراخوان‌های علاقه‌مندی هستند.

## ایجاد یک فراخوان علاقه‌مندی

ایجاد یک فراخوان علاقه‌مندی به صورت اعلانی دارای دو شرط زیر است:

- یک **عنصر فراخوان**: این عنصری است که کاربر با آن تعامل می‌کند تا علاقه خود را نشان دهد و اقدامی را فعال کند، مانند نمایش یا پنهان‌کردن یک پاپ‌اور. عنصر فراخوان باید ویژگی [`interestfor`](/en-US/docs/Web/HTML/Reference/Elements/a#interestfor) را داشته باشد که مقدار آن `id` عنصر هدف است. عنصر فراخوان می‌تواند یک عنصر HTML {{htmlelement("a")}}، {{htmlelement("button")}} یا {{htmlelement("area")}} باشد، یا یک عنصر SVG [`<a>`](/en-US/docs/Web/SVG/Reference/Element/a).

- یک **عنصر هدف**: این عنصری است که وقتی علاقه کسب یا از دست می‌رود، تحت تأثیر قرار می‌گیرد یا کنترل می‌شود. عنصر هدف باید دارای یک `id` باشد و می‌تواند تقریباً هر نوع عنصری باشد. دادن ویژگی `popover` به این عنصر، آن را به یک پاپ‌اور تبدیل می‌کند.

  > [!NOTE]
  > همچنین می‌توانید عنصر هدف را به صورت برنامه‌نویسی‌شده تنظیم کنید، با تنظیم ویژگی DOM ای `interestForElement` عنصر فراخوان به یک ارجاع به عنصر هدف. برای اطلاعات بیشتر، بخش [API جاوااسکریپت برای فراخوان‌های علاقه‌مندی](#api-جاوااسکریپت-برای-فراخوان‌های-علاقه‌مندی) را در ادامه این راهنما ببینید.

بیایید به یک مثال ساده نگاه کنیم. در اینجا، **عنصر فراخوان** یک پیوند است و **عنصر هدف** یک پاراگراف با ویژگی `popover` است.

```css hidden live-sample___basic-interest-invoker live-sample___interest-invoker-popover-interaction live-sample___interest-invoker-styling live-sample___interest-invoker-api live-sample___non-popover live-sample___link-preview-popover
.no-interest-invokers body::before {
  content: "Your browser doesn't support interest invokers.";
  background-color: wheat;
  display: block;
  padding: 10px 0;
  width: 100%;
  text-align: center;
}
```

```js hidden live-sample___basic-interest-invoker live-sample___interest-invoker-popover-interaction live-sample___interest-invoker-styling live-sample___interest-invoker-api live-sample___non-popover live-sample___link-preview-popover
const supported = Object.hasOwn(
  HTMLButtonElement.prototype,
  "interestForElement",
);
if (!supported) {
  document.querySelector("html").classList.add("no-interest-invokers");
}
```

```html live-sample___basic-interest-invoker
<p>Some text with a <a href="#" interestfor="mypopover">link</a>.</p>
<p id="mypopover" popover>A short preview with some quick info</p>
```

تنظیم ویژگی `popover` روی عنصر هدف باعث می‌شود که آن (از طریق {{cssxref("display", "display: none")}}) پنهان شود و در مرکز صفحه قرار گیرد. نشان دادن علاقه به عنصر فراخوان (پیوند) باعث ظاهر شدن پاپ‌اور می‌شود.

این به صورت زیر رندر می‌شود. سعی کنید با پیوند تعامل کنید:

{{embedlivesample("basic-interest-invoker", "100%", "150")}}

توجه کنید که چگونه پاپ‌اور وقتی پیوند هاور می‌شود، فوکوس می‌شود یا مدت‌ها فشار داده می‌شود ظاهر می‌شود و وقتی تعامل متوقف می‌شود ناپدید می‌شود. در مقابل، اگر پیوند به جای آن فعال شود، مثلاً با یک کلیک ماوس، مانند یک پیوند معمولی رفتار می‌کند – با این تفاوت که در این مثال به جایی نمی‌رود.

مقدار ویژگی `popover` در این مثال بر رفتار پاپ‌اور تأثیر نمی‌گذارد. با این حال، وقتی پاپ‌اورهای فراخوان علاقه‌مندی را با پاپ‌اورهای معمولی ترکیب می‌کنید مهم می‌شود، همانطور که در بخش بعدی نشان داده شده است.

## ترکیب فراخوان‌های علاقه‌مندی با پاپ‌اورهای مبتنی بر فعال‌سازی

می‌توانید فراخوان‌های علاقه‌مندی را با پاپ‌اورهای معمولی روی همان عنصر کنترلی ترکیب کنید. در مثال زیر، یک عنصر {{htmlelement("button")}} به عنوان یک فراخوان علاقه‌مندی با استفاده از ویژگی `interestfor` تنظیم شده است، به این معنی که وقتی کاربر به آن علاقه نشان می‌دهد، یک tooltip نمایش می‌دهد. اگر دکمه کلیک شود، یک پاپ‌اور متفاوت را که توسط ویژگی `commandfor` ارجاع شده است نمایش می‌دهد یا پنهان می‌کند. ویژگی [`command`](/en-US/docs/Web/HTML/Reference/Elements/button#command) روی `toggle-popover` تنظیم شده است و به دکمه اجازه می‌دهد چندین بار فشار داده شود تا پاپ‌اور بین حالت‌های نمایش داده‌شده و پنهان خود جابه‌جا شود.

```css hidden live-sample___interest-invoker-popover-interaction
#my-tooltip {
  position-area: right;
}

#my-infobox {
  position-area: bottom;
}
```

```html live-sample___interest-invoker-popover-interaction
<p>
  Some content including a
  <button
    interestfor="my-tooltip"
    commandfor="my-infobox"
    command="toggle-popover">
    button
  </button>
</p>
<p id="my-tooltip" popover="hint">A hover tooltip</p>
<p id="my-infobox" popover>
  An infobox that also contains some control buttons<br />
  <button>Button 1</button> <button>Button 2</button>
</p>
```

این به صورت زیر رندر می‌شود:

{{embedlivesample("interest-invoker-popover-interaction", "100%", "150")}}

می‌توانید به دکمه علاقه نشان دهید تا tooltip نمایش داده شود، و روی دکمه کلیک کنید تا infobox ظاهر شود. توجه کنید که مقادیر `popover` در اینجا مهم هستند — پاپ‌اور tooltip روی [`popover="hint"`](/en-US/docs/Web/API/Popover_API/Using#using_hint_popover_state) تنظیم شده است، در حالی که infobox فقط روی `popover` (معادل `popover="auto"`) تنظیم شده است. این اجازه می‌دهد tooltip حتی زمانی که infobox نمایش داده می‌شود قابل مشاهده بماند. اگر هر دو پاپ‌اور روی `auto` تنظیم می‌شدند، نمی‌توانستید هم tooltip و هم infobox را همزمان ببینید. در یک رابط کاربری، مفید است که بتوانید چندین tooltip را بدون مخفی‌کردن بخش‌هایی از رابط کاربری که قبلاً باز کرده‌اید مشاهده کنید.

## استایل‌دهی به فراخوان‌های علاقه‌مندی

هنگام استایل‌دهی به پاپ‌اورهایی که با فراخوان‌های علاقه‌مندی استفاده می‌شوند، می‌توانید از همان تکنیک‌های استایل‌دهی مشابه هر پاپ‌اور دیگری استفاده کنید (به [استایل‌دهی به پاپ‌اورها](/en-US/docs/Web/API/Popover_API/Using#styling_popovers) مراجعه کنید)، از جمله [استفاده از positioning لنگر](/en-US/docs/Web/API/Popover_API/Using#popover_anchor_positioning) برای قرار دادن پاپ‌اورها نسبت به فراخوان‌ها و [انیمیشن‌دادن به پاپ‌اورها](/en-US/docs/Web/API/Popover_API/Using#animating_popovers).

با این حال، برخی ویژگی‌های CSS خاص فراخوان‌های علاقه‌مندی وجود دارند:

- ویژگی ساده {{cssxref("interest-delay")}} و ویژگی‌های بلندمرتبه مرتبط با آن {{cssxref("interest-delay-start")}} و {{cssxref("interest-delay-end")}}: این‌ها می‌توانند برای افزودن تأخیر بین کسب یا از دست دادن علاقه توسط کاربر و اقدام مرورگر بر اساس آن تغییر — برای مثال، نمایش یا پنهان‌کردن یک پاپ‌اور — استفاده شوند.
- شبه‌کلاس‌های {{cssxref(":interest-source")}} و {{cssxref(":interest-target")}}: این‌ها می‌توانند برای اعمال استایل به ترتیب به فراخوان علاقه‌مندی و عنصر هدف مرتبط آن استفاده شوند، فقط زمانی که علاقه نشان داده شده است.

بیایید به یک مثال ساده نگاه کنیم که نحوه کار این ویژگی‌ها را نشان می‌دهد.

ما دو دکمه و یک tooltip تعریف کرده‌ایم. tooltip زمانی نمایش داده می‌شود یا پنهان می‌شود که کاربر به هر یک از دو دکمه علاقه نشان دهد یا علاقه‌اش را از دست بدهد.

```html live-sample___interest-invoker-styling
<p>
  <button interestfor="my-tooltip">Button 1</button>
  <button interestfor="my-tooltip">Button 2</button>
</p>
<p id="my-tooltip" popover="hint">A hover tooltip</p>
```

در CSS، ما یک `interest-delay` با مقدار `1s 2s` روی `<button>` تنظیم کرده‌ایم — این یک تأخیر ۱ ثانیه‌ای قبل از ظاهر شدن tooltip وقتی کاربر علاقه نشان می‌دهد، و یک تأخیر ۲ ثانیه‌ای قبل از ناپدید شدن آن وقتی کاربر علاقه‌اش را از دست می‌دهد ایجاد می‌کند. ما همچنین از انتخابگر `button:interest-source` استفاده کرده‌ایم تا {{cssxref("background-color")}} دکمه‌ها را وقتی علاقه نشان داده می‌شود به `orange` تغییر دهیم.

```css live-sample___interest-invoker-styling
button {
  interest-delay: 1s 2s;
}

button:interest-source {
  background-color: orange;
}
```

سپس، ما شبه‌کلاس `:interest-source` را با شبه‌کلاس {{cssxref(":has()")}} ترکیب کرده‌ایم تا `interest-delay-start: 0s` را به همه دکمه‌های داخل پاراگراف اعمال کنیم، اما فقط زمانی که پاراگراف حاوی دکمه‌ای است که علاقه روی آن نشان داده شده است (یعنی دکمه‌ای که با `button:interest-source` مطابقت دارد). این یک تکنیک مفید است — اینکه پاپ‌اور به محض نشان دادن علاقه روی هر دکمه ظاهر شود، تجربه کاربری آزاردهنده‌ای ایجاد می‌کند، اما پس از اینکه کاربر به یک دکمه علاقه نشان داد، راحت است که بتواند به سرعت بین پاپ‌اورهای مختلف جابه‌جا شود.

```css live-sample___interest-invoker-styling
p:has(button:interest-source) button {
  interest-delay-start: 0s;
}
```

ما همچنین یک {{cssxref("position-area")}} با مقدار `bottom` روی tooltip تنظیم کرده‌ایم تا زیر دکمه ظاهر شود. این امکان‌پذیر است زیرا مرتبط‌کردن هر پاپ‌اور با فراخوان علاقه‌مندی خود، یک مرجع لنگر ضمنی بین آن‌ها ایجاد می‌کند (برای جزئیات بیشتر به [موقعیت‌دهی لنگر پاپ‌