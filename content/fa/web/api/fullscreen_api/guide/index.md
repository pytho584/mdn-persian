---
title: "Guide to the Fullscreen API"
---

{{DefaultAPISidebar("Fullscreen API")}}

این مقاله نحوه استفاده از [Fullscreen API](/en-US/docs/Web/API/Fullscreen_API) را برای قرار دادن یک عنصر مشخص در حالت تمام‌صفحه و همچنین تشخیص ورود یا خروج مرورگر از حالت تمام‌صفحه نشان می‌دهد.

## فعال‌سازی حالت تمام‌صفحه

با فرض یک عنصر که می‌خواهید در حالت تمام‌صفحه نمایش دهید (مثلاً یک {{HTMLElement("video")}})، می‌توانید با فراخوانی متد {{DOMxRef("Element.requestFullscreen", "requestFullscreen()")}} آن را در حالت تمام‌صفحه نمایش دهید.

این عنصر {{HTMLElement("video")}} را در نظر بگیرید:

```html
<video controls id="my-video">
  <source src="somevideo.webm" />
  <source src="somevideo.mp4" />
</video>
```

می‌توانیم آن ویدیو را به صورت زیر در حالت تمام‌صفحه قرار دهیم:

```js
const elem = document.getElementById("my-video");
if (elem.requestFullscreen) {
  elem.requestFullscreen();
}
```

این کد وجود متد `requestFullscreen()` را قبل از فراخوانی آن بررسی می‌کند.

هنگامی که یک عنصر در حالت تمام‌صفحه قرار می‌گیرد، با {{cssxref(":fullscreen")}} مطابقت داده می‌شود که برخی سبک‌های پیش‌فرض مانند اشغال کل صفحه را به آن اعمال می‌کند. همچنین در {{glossary("top layer")}} (لایه بالایی) قرار می‌گیرد.

اگر چندین عنصر برای نمایش در حالت تمام‌صفحه درخواست شوند، همه آن‌ها با {{cssxref(":fullscreen")}} مطابقت داده می‌شوند و در لایه بالایی هستند. آن‌ها روی هم انباشته می‌شوند، به طوری که عناصر جدیدتر در بالای عناصر قدیمی‌تر قرار می‌گیرند. جدیدترین عنصر درخواست‌شده نمایش داده می‌شود و توسط {{domxref("Document.fullscreenElement")}} بازگردانده می‌شود.

### اعلان (Notification)

هنگامی که حالت تمام‌صفحه با موفقیت فعال شود، سندی که حاوی عنصر است، یک رویداد {{domxref("Element/fullscreenchange_event", "fullscreenchange")}} دریافت می‌کند. هنگامی که از حالت تمام‌صفحه خارج می‌شوید، سند دوباره یک رویداد {{domxref("Document/fullscreenchange_event", "fullscreenchange")}} دریافت می‌کند. توجه داشته باشید که رویداد {{domxref("Document/fullscreenchange_event", "fullscreenchange")}} خود اطلاعاتی در مورد اینکه سند وارد حالت تمام‌صفحه می‌شود یا از آن خارج می‌شود، ارائه نمی‌دهد، اما اگر سند دارای یک {{DOMxRef("document.fullscreenElement", "fullscreenElement")}} غیر null باشد، متوجه می‌شوید که در حالت تمام‌صفحه هستید.

### زمانی که درخواست تمام‌صفحه شکست می‌خورد

تضمینی وجود ندارد که بتوانید به حالت تمام‌صفحه بروید. به عنوان مثال، عناصر {{HTMLElement("iframe")}} دارای ویژگی [`allowfullscreen`](/en-US/docs/Web/HTML/Reference/Elements/iframe#allowfullscreen) هستند تا اجازه دهند محتوای آن‌ها در حالت تمام‌صفحه نمایش داده شود. علاوه بر این، انواع خاصی از محتوا، مانند افزونه‌های پنجره‌ای (windowed plug-ins)، نمی‌توانند در حالت تمام‌صفحه نمایش داده شوند. تلاش برای قرار دادن عنصری که نمی‌تواند در حالت تمام‌صفحه نمایش داده شود (یا والد یا فرزند چنین عنصری) کار نخواهد کرد. در عوض، عنصری که درخواست تمام‌صفحه کرده است، یک رویداد `fullscreenerror` دریافت می‌کند. هنگامی که درخواست تمام‌صفحه شکست می‌خورد، فایرفاکس یک پیام خطا در کنسول وب (Web Console) ثبت می‌کند که دلیل شکست را توضیح می‌دهد. با این حال، در کروم و نسخه‌های جدیدتر اپرا، چنین هشداری تولید نمی‌شود.

> [!NOTE]
> درخواست‌های تمام‌صفحه باید از درون یک کنترل‌کننده رویداد (event handler) فراخوانی شوند، در غیر این صورت رد می‌شوند.

## خروج از حالت تمام‌صفحه

کاربر همیشه می‌تواند به میل خود از حالت تمام‌صفحه خارج شود؛ به بخش [نکاتی که کاربران شما باید بدانند](#things_your_users_want_to_know) مراجعه کنید. همچنین می‌توانید به صورت برنامه‌نویسی با فراخوانی متد {{DOMxRef("Document.exitFullscreen()")}} این کار را انجام دهید.

اگر چندین عنصر در حالت تمام‌صفحه وجود داشته باشند، فراخوانی `exitFullscreen()` فقط بالاترین عنصر را از حالت تمام‌صفحه خارج می‌کند و عنصر بعدی زیر آن را نمایان می‌سازد. فشار دادن <kbd>Esc</kbd> یا <kbd>F11</kbd> همه عناصر تمام‌صفحه را خارج می‌کند.

## سایر اطلاعات

{{DOMxRef("Document")}} اطلاعات اضافی دیگری را ارائه می‌دهد که می‌تواند هنگام توسعه برنامه‌های وب تمام‌صفحه مفید باشد:

- {{DOMxRef("Document.fullscreenElement")}} / {{DOMxRef("ShadowRoot.fullscreenElement")}}
  - : ویژگی `fullscreenElement` به شما {{DOMxRef("Element")}}ای را می‌گوید که در حال حاضر به صورت تمام‌صفحه نمایش داده می‌شود. اگر این مقدار non-null باشد، سند (یا shadow DOM) در حالت تمام‌صفحه است. اگر null باشد، سند (یا shadow DOM) در حالت تمام‌صفحه نیست.
- {{DOMxRef("Document.fullscreenEnabled")}}
  - : ویژگی `fullscreenEnabled` به شما می‌گوید که آیا سند در حال حاضر در وضعیتی است که امکان درخواست حالت تمام‌صفحه وجود دارد یا خیر.

### مقیاس‌گذاری viewport در مرورگرهای موبایل

برخی مرورگرهای موبایل در حالت تمام‌صفحه تنظیمات متا تگ viewport را نادیده گرفته و مقیاس‌گذاری کاربر را مسدود می‌کنند؛ به عنوان مثال: ژست "pinch to zoom" (نیشگون گرفتن برای بزرگ‌نمایی) ممکن است در صفحه‌ای که در حالت تمام‌صفحه ارائه شده است کار نکند — حتی اگر در حالت غیر تمام‌صفحه، صفحه با استفاده از pinch to zoom قابل مقیاس‌گذاری باشد.

## نکاتی که کاربران شما باید بدانند

حتماً به کاربران خود اطلاع دهید که می‌توانند کلید <kbd>Esc</kbd> (یا <kbd>F11</kbd>) را فشار دهند تا از حالت تمام‌صفحه خارج شوند.

علاوه بر این، رفتن به صفحه دیگر، تغییر زبانه (tab) یا جابجایی به برنامه دیگر (به عنوان مثال با استفاده از <kbd>Alt</kbd>-<kbd>Tab</kbd>) در حالت تمام‌صفحه نیز باعث خروج از حالت تمام‌صفحه می‌شود.

## مثال

مخزن GitHub [mdn/dom-examples](https://github.com/mdn/) شامل یک مثال کامل از Fullscreen API است.

[اجرای مثال](https://mdn.github.io/dom-examples/fullscreen-api/index.html) و [مرور کد منبع](https://github.com/mdn/dom-examples/tree/main/fullscreen-api).

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- [Using fullscreen mode](/en-US/docs/Web/API/Fullscreen_API)
- {{DOMxRef("Element.requestFullscreen()")}}
- {{DOMxRef("Document.exitFullscreen()")}}
- {{DOMxRef("Document.fullscreen")}}
- {{DOMxRef("Document.fullscreenElement")}}
- {{CSSxRef(":fullscreen")}}, {{CSSxRef("::backdrop")}}
- [`allowfullscreen`](/en-US/docs/Web/HTML/Reference/Elements/iframe#allowfullscreen)