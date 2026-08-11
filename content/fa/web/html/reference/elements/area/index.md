---
title: "<area> HTML image map area element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/area"
translated_by: "n8n + AI"
---

عنصر `<area>` در HTML، یک ناحیهٔ قابل کلیک را درون یک **image map** (نقشهٔ تصویری) تعریف می‌کند. image map به شما اجازه می‌دهد نواحی هندسی مختلفی را روی یک تصویر مشخص کنید و هر کدام را به یک **hyperlink** (پیوند) متصل نمایید.

این عنصر فقط درون یک عنصر `<map>` کاربرد دارد.

```html interactive-example
<map name="infographic">
  <area
    shape="poly"
    coords="129,0,260,95,129,138"
    href="https://developer.mozilla.org/docs/Web/HTTP"
    alt="HTTP" />
  <area
    shape="poly"
    coords="260,96,209,249,130,138"
    href="https://developer.mozilla.org/docs/Web/HTML"
    alt="HTML" />
  <area
    shape="poly"
    coords="209,249,49,249,130,139"
    href="https://developer.mozilla.org/docs/Web/JavaScript"
    alt="JavaScript" />
  <area
    shape="poly"
    coords="48,249,0,96,129,138"
    href="https://developer.mozilla.org/docs/Web/API"
    alt="Web APIs" />
  <area
    shape="poly"
    coords="0,95,128,0,128,137"
    href="https://developer.mozilla.org/docs/Web/CSS"
    alt="CSS" />
</map>
<img
  usemap="#infographic"
  src="/shared-assets/images/examples/mdn-info.png"
  alt="MDN infographic" />
```

```css interactive-example
img {
  display: block;
  margin: 0 auto;
  width: 260px;
  height: 260px;
}
```

## ویژگی‌ها (Attributes)

این عنصر از تمام [ویژگی‌های سراسری (global attributes)](/en-US/docs/Web/HTML/Reference/Global_attributes) پشتیبانی می‌کند. ویژگی‌های اختصاصی آن عبارتند از:

- `alt`
  - : یک متن جایگزین که در مرورگرهایی که تصویر را نمایش نمی‌دهند نشان داده می‌شود. این متن باید طوری نوشته شود که کاربر همان انتخابی را که از روی تصویر می‌کرد، از روی متن جایگزین نیز داشته باشد. این ویژگی فقط زمانی الزامی است که ویژگی [`href`](#href) استفاده شده باشد.
- `coords`
  - : مختصات ناحیه را بر اساس مقدار [`shape`](#shape) مشخص می‌کند. این ویژگی شامل اندازه، شکل و موقعیت `<area>` است. اگر `shape` برابر `default` باشد، نباید از `coords` استفاده کرد.
    - `rect`: مقدار به صورت `x1,y1,x2,y2` است. این مختصات گوشه‌های بالا-چپ و پایین-راست مستطیل را مشخص می‌کند. برای مثال در `<area shape="rect" coords="0,0,253,27" href="#" target="_blank" alt="Mozilla">`، مختصات `0,0` و `253,27` به ترتیب نشان‌دهندهٔ گوشه‌های بالا-چپ و پایین-راست هستند.
    - `circle`: مقدار به صورت `x,y,radius` است. مختصات مرکز دایره و شعاع آن را مشخص می‌کند. مثال: `<area shape="circle" coords="130,136,60" href="#" target="_blank" alt="MDN">`
    - `poly`: مقدار به صورت `x1,y1,x2,y2,..,xn,yn` است. مختصات لبه‌های چندضلعی را مشخص می‌کند. اگر اولین و آخرین جفت مختصات یکسان نباشند، مرورگر به‌طور خودکار آخرین جفت را تکرار می‌کند تا چندضلعی بسته شود.

    تمام مقادیر بر حسب پیکسل CSS هستند. [ابزار تولید شکل (shape generator)](/en-US/docs/Web/CSS/Guides/Shapes/Shape_generator) می‌تواند با انتخاب نقاط روی تصویری که آپلود می‌کنید، به شما در نوشتن `coords` کمک کند.

- `download`
  - : این ویژگی، اگر وجود داشته باشد، نشان می‌دهد که منبع لینک‌شده قرار است دانلود شود نه در مرورگر نمایش داده شود. برای توضیح کامل ویژگی `download` به [`download` در عنصر `<a>`](/en-US/docs/Web/HTML/Reference/Elements/a#download) مراجعه کنید.
- `href`
  - : مقصد ابرلینک برای این ناحیه است. مقدار آن یک URL معتبر است. این ویژگی می‌تواند حذف شود؛ اگر حذف شود، عنصر `<area>` یک ابرلینک را نشان نمی‌دهد.
- `interestfor`
  - : عنصر `<area>` را به عنوان **interest invoker** تعریف می‌کند. مقدار آن `id` عنصر هدف است که وقتی به عنصر invoker علاقه نشان داده شود یا از بین برود (مثلاً با هاور کردن/ترک هاور یا فوکوس/blur کردن) به نحوی تحت تأثیر قرار می‌گیرد (معمولاً نمایش داده می‌شود یا پنهان می‌شود). برای جزئیات و مثال‌های بیشتر به [استفاده از interest invokerها](/en-US/docs/Web/API/Popover_API/Using_interest_invokers) مراجعه کنید.
- `ping`
  - : شامل فهرستی از URLهاست که با فاصله جدا می‌شوند. وقتی ابرلینک دنبال شود، مرورگر درخواست‌های POST با بدنه `PING` را در پس‌زمینه به این URLها ارسال می‌کند. معمولاً برای ردیابی استفاده می‌شود.
- `referrerpolicy`
  - : رشته‌ای که مشخص می‌کند هنگام دریافت منبع، از کدام referrer استفاده شود:
    - `no-referrer`: هدر `Referer` ارسال نخواهد شد.
    - `no-referrer-when-downgrade`: هدر `Referer` به origin های بدون TLS (HTTPS) ارسال نخواهد شد.
    - `origin`: referrer ارسالی به origin صفحه ارجاع‌دهنده محدود می‌شود: [scheme](/en-US/docs/Learn_web_development/Howto/Web_mechanics/What_is_a_URL)، host و port آن.
    - `origin-when-cross-origin`: referrer ارسال‌شده به سایر origin ها به scheme، host و port محدود می‌شود. پیمایش‌های روی همان origin همچنان path را شامل می‌شوند.
    - `same-origin`: برای همان origin یک referrer ارسال می‌شود، اما درخواست‌های cross-origin هیچ information مرجع (referrer) نخواهند داشت.
    - `strict-origin`: فقط زمانی که سطح امنیت پروتکل ثابت بماند (HTTPS→HTTPS)، origin سند به عنوان referrer ارسال می‌شود؛ اما به مقصد با امنیت کمتر (HTTPS→HTTP) ارسال نمی‌شود.
    - `strict-origin-when-cross-origin` (پیش‌فرض): در یک درخواست same-origin، URL کامل ارسال می‌شود. فقط زمانی که سطح امنیت پروتکل ثابت است (HTTPS→HTTPS)، origin ارسال می‌شود. و به مقصد با امنیت کمتر (HTTPS→HTTP) هیچ هدری ارسال نمی‌شود.
    - `unsafe-url`: referrer شامل origin و path خواهد بود (اما نه [fragment](/en-US/docs/Web/API/HTMLAnchorElement/hash)، [password](/en-US/docs/Web/API/HTMLAnchorElement/password) یا [username](/en-US/docs/Web/API/HTMLAnchorElement/username)). **این مقدار ناامن است**، زیرا origin و path را از منابع محافظت‌شده با TLS به origin های ناامن نشت می‌دهد.

- [`rel`](#rel)
  - : برای anchorهایی که دارای attribute [`href`](#href) هستند، این attribute رابطهٔ شیء مقصد با شیء لینک را مشخص می‌کند. مقدار آن یک لیست جدا شده با فاصله از انواع لینک است. این مقادیر و معنایشان توسط یک مرجع معتبر ثبت می‌شوند که ممکن است برای نویسندهٔ سند معنا داشته باشد. رابطهٔ پیش‌فرض، در صورت عدم تعیین مقدار دیگر، void است. این attribute را فقط زمانی استفاده کنید که attribute [`href`](#href) وجود داشته باشد.

- `shape`
  - : شکل ناحیهٔ حساس (hot spot) مرتبط. مشخصات HTML مقادیر `rect` (ناحیهٔ مستطیلی)، `circle` (ناحیهٔ دایره‌ای)، `poly` (چندضلعی) و `default` (کل ناحیه فراتر از اشکال تعریف‌شده) را تعریف می‌کند.

- `target`
  - : یک کلمه کلیدی یا نام تعریف‌شده توسط نویسنده از {{Glossary("browsing context")}} (زمینه مرورگر) برای نمایش منبع لینک‌شده. کلمات کلیدی زیر معانی خاصی دارند:
    - `_self` (پیش‌فرض): منبع را در همان زمینه مرورگر فعلی نمایش بده.
    - `_blank`: منبع را در یک زمینه مرورگر جدید و بدون نام نمایش بده.
    - `_parent`: منبع را در زمینه مرورگر والدِ زمینه فعلی نمایش بده، اگر صفحه فعلی داخل یک فریم باشد. اگر والد وجود نداشته باشد، مانند `_self` عمل می‌کند.
    - `_top`: منبع را در بالاترین زمینه مرورگر (زمینه‌ای که جدِ زمینه فعلی است و والد ندارد) نمایش بده. اگر والد وجود نداشته باشد، مانند `_self` عمل می‌کند.

    این attribute را فقط زمانی استفاده کنید که attribute [`href`](#href) وجود داشته باشد.

    > [!NOTE]
    > تنظیم `target="_blank"` روی عناصر `<area>` به طور ضمنی همان رفتار `rel` را ایجاد می‌کند که معادل تنظیم [`rel="noopener"`](/en-US/docs/Web/HTML/Reference/Attributes/rel/noopener) است و `window.opener` را تنظیم نمی‌کند. وضعیت پشتیبانی را در بخش [سازگاری مرورگر](#browser_compatibility) ببینید.

## مثال

### تصویر با نواحی قابل کلیک

```html
<map name="primary">
  <area
    shape="circle"
    coords="75,75,75"
    href="left.html"
    alt="Click to go Left" />
  <area
    shape="circle"
    coords="275,75,75"
    href="right.html"
    alt="Click to go Right" />
</map>
<img
  usemap="#primary"
  src="https://dummyimage.com/350x150"
  alt="350 x 150 pic" />
```

## خلاصهٔ فنی

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories">دسته‌بندی محتوا</a>
      </th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content">محتوا جریانی (Flow content)</a>،
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content">محتوا عبارتی (Phrasing content)</a>.
      </td>
    </tr>
    <tr>
      <th scope="row">محتوای مجاز</th>
      <td>هیچ؛ این یک {{Glossary("void element")}} (عنصر تهی) است.</td>
    </tr>
    <tr>
      <th scope="row">حذف تگ</th>
      <td>باید یک تگ شروع داشته باشد و نباید تگ پایانی داشته باشد.</td>
    </tr>
    <tr>
      <th scope="row">والدین مجاز</th>
      <td>
        هر عنصری که <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content">محتوا عبارتی</a> را بپذیرد. عنصر <code>&#x3C;area></code> باید یک جدِ {{HTMLElement("map")}} داشته باشد، اما نیازی نیست والد مستقیم باشد.
      </td>
    </tr>
    <tr>
      <th scope="row">نقش ARIA ضمنی</th>
      <td>
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/link_role"><code>link</code></a> در صورت وجود attribute <a href="#href"><code>href</code></a>، در غیر این صورت
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/generic_role"><code>generic</code></a>
      </td>
    </tr>
    <tr>
      <th scope="row">نقش‌های ARIA مجاز</th>
      <td>هیچ <code>role</code> مجاز نیست</td>
    </tr>
    <tr>
      <th scope="row">رابط DOM</th>
      <td>{{domxref("HTMLAreaElement")}}</td>
    </tr>
  </tbody>
</table>

## مشخصات

## سازگاری با مرورگرها