---
title: "<input type=\"image\"> HTML attribute value"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/input/image"
translated_by: "n8n + AI"
---

المان‌های `<input>` از نوع **`image`** برای ساخت دکمه‌های ارسال گرافیکی استفاده می‌شوند؛ یعنی دکمه‌های ارسالی که به‌جای متن، به‌صورت یک تصویر نمایش داده می‌شوند.

```html interactive-example
<p>Sign in to your account:</p>

<div>
  <label for="userId">User ID</label>
  <input type="text" id="userId" name="userId" />
</div>

<input
  type="image"
  id="image"
  alt="Login"
  src="/shared-assets/images/examples/login-button.png" />
```

```css interactive-example
label {
  font-size: 0.8rem;
}

label,
input[type="image"] {
  margin-top: 1rem;
}

input[type="image"] {
  width: 80px;
}
```

## مقدار

المان‌های `<input type="image">` ویژگی (attribute) `value` را نمی‌پذیرند. مسیر تصویری که قرار است نمایش داده شود، در ویژگی `src` مشخص می‌شود.

## ویژگی‌های اضافی

علاوه بر ویژگی‌هایی که بین همه المان‌های `<input>` مشترک است، ورودی‌های دکمه‌ی `image` از ویژگی‌های زیر پشتیبانی می‌کنند.

### alt

ویژگی `alt` یک رشته‌ی جایگزین برای برچسب دکمه فراهم می‌کند تا زمانی که تصویر قابل نمایش نباشد (به دلیل خطا، یا اگر user agent نتواند یا طوری تنظیم شده باشد که تصاویر را نشان ندهد، یا اگر کاربر از دستگاه خواندن صفحه استفاده کند) استفاده شود. اگر این ویژگی ارائه شود، باید یک رشته‌ی غیرخالی مناسب به‌عنوان برچسب دکمه باشد.

مثلاً اگر یک دکمه گرافیکی دارید که تصویری با آیکون و/یا متن تصویری «Login Now» را نشان می‌دهد، باید ویژگی `alt` را هم به چیزی مثل `Login Now` تنظیم کنید.

> [!NOTE]
> اگرچه ویژگی `alt` از نظر فنی اختیاری است، بهتر است همیشه آن را اضافه کنید تا قابلیت استفاده محتوای خود را به حداکثر برسانید.

از نظر عملکردی، ویژگی `alt` در المان `<input type="image">` دقیقاً مانند ویژگی [`alt`](/en-US/docs/Web/HTML/Reference/Elements/img#alt) در المان‌های `<img>` عمل می‌کند.

### formaction

یک رشته که نشانی اینترنتی (URL) ارسال داده‌ها را مشخص می‌کند. این ویژگی بر attribute [`action`](/en-US/docs/Web/HTML/Reference/Elements/form#action) در المان `<form>` که مالک `<input>` است، اولویت دارد.

این ویژگی روی [`<input type="submit">`](/en-US/docs/Web/HTML/Reference/Elements/input/submit) و المان‌های `<button>` نیز در دسترس است.

### formenctype

یک رشته که روش رمزنگاری (encoding) مورد استفاده برای ارسال داده‌های فرم به سرور را مشخص می‌کند. سه مقدار مجاز وجود دارد:

- `application/x-www-form-urlencoded`
  - : این مقدار پیش‌فرض است و داده‌های فرم را به صورت یک رشته ارسال می‌کند؛ ابتدا متن با الگوریتمی مثل `encodeURI()` درصدگذاری (percent-encoding) می‌شود.
- `multipart/form-data`
  - : از API مربوط به `FormData` برای مدیریت داده‌ها استفاده می‌کند و امکان ارسال فایل‌ها به سرور را فراهم می‌سازد. اگر فرم شما شامل هر المان `<input>` با [`type`](/en-US/docs/Web/HTML/Reference/Elements/input#type) برابر با `file` (یعنی [`<input type="file">`](/en-US/docs/Web/HTML/Reference/Elements/input/file)) باشد، _باید_ از این نوع encoding استفاده کنید.
- `text/plain`
  - : متن ساده؛ عمدتاً فقط برای اشکال‌زدایی مفید است، چون می‌توانید به‌راحتی داده‌هایی را که قرار است ارسال شوند ببینید.

اگر مشخص شود، مقدار attribute `formenctype` بر attribute [`enctype`](/en-US/docs/Web/HTML/Reference/Elements/form#enctype) فرم والد غلبه می‌کند.

این attribute همچنین روی [`<input type="submit">`](/en-US/docs/Web/HTML/Reference/Elements/input/submit) و المان‌های `<button>` در دسترس است.

### formmethod

یک رشته که متد HTTP مورد استفاده برای ارسال داده‌های فرم را مشخص می‌کند؛ این مقدار بر هر attribute [`method`](/en-US/docs/Web/HTML/Reference/Elements/form#method) که روی فرم والد تنظیم شده است غلبه می‌کند. مقادیر مجاز عبارت‌اند از:

- `get`
  - : یک URL با شروع از آدرسی که در ویژگی `formaction` یا [`action`](/en-US/docs/Web/HTML/Reference/Elements/form#action) مشخص شده ساخته می‌شود؛ سپس یک علامت سؤال («?») به آن اضافه شده و داده‌های فرم، مطابق آنچه `formenctype` یا ویژگی [`enctype`](/en-US/docs/Web/HTML/Reference/Elements/form#enctype) مشخص می‌کند، به انتهای آن اضافه می‌شود. این URL با یک درخواست HTTP GET به سرور ارسال می‌شود. این روش برای فرم‌هایی مناسب است که فقط شامل نویسه‌های {{Glossary("ASCII")}} هستند و عوارض جانبی (side effect) ندارند. این مقدار پیش‌فرض است.
- `post`
  - : داده‌های فرم در بدنهٔ درخواستی که به آدرس مشخص‌شده در `formaction` یا [`action`](/en-US/docs/Web/HTML/Reference/Elements/form#action) فرستاده می‌شود قرار می‌گیرند و با یک درخواست HTTP POST ارسال می‌شوند. این روش از داده‌های پیچیده و پیوست فایل پشتیبانی می‌کند.
- `dialog`
  - : این روش برای نشان دادن این استفاده می‌شود که دکمه، دیالوگ مرتبط با input را می‌بندد و اصلاً داده‌های فرم را ارسال نمی‌کند.

این ویژگی روی [`<input type="submit">`](/en-US/docs/Web/HTML/Reference/Elements/input/submit) و عناصر {{HTMLElement("button")}} نیز موجود است.

### formnovalidate

یک ویژگی Boolean که اگر وجود داشته باشد، مشخص می‌کند که فرم نباید قبل از ارسال به سرور اعتبارسنجی شود. این ویژگی، مقدار [`novalidate`](/en-US/docs/Web/HTML/Reference/Elements/form#novalidate) را در فرم والد این عنصر نادیده می‌گیرد.

این ویژگی روی [`<input type="submit">`](/en-US/docs/Web/HTML/Reference/Elements/input/submit) و عناصر {{HTMLElement("button")}} نیز موجود است.

### formtarget

رشته‌ای که یک نام یا کلیدواژه را مشخص می‌کند که تعیین می‌کند پاسخ دریافتی پس از ارسال فرم در کجا نمایش داده شود. این رشته باید نام یک **browsing context** باشد (یعنی یک تب، پنجره یا {{HTMLElement("iframe")}}). مقداری که در اینجا مشخص می‌شود، هر مقدار `target` را در ویژگی [`target`](/en-US/docs/Web/HTML/Reference/Elements/form#target) روی {{HTMLElement("form")}} والد این input نادیده می‌گیرد.

علاوه بر نام‌های واقعی تب‌ها، پنجره‌ها یا iframeها، چند کلیدواژهٔ خاص نیز قابل استفاده هستند:

- `_self`
  - : پاسخ را در همان browsing context که حاوی فرم است بارگذاری می‌کند. این کار، سند جاری را با داده‌های دریافتی جایگزین می‌کند. اگر مقداری مشخص نشده باشد، این مقدار پیش‌فرض است.
- `_blank`
  - : پاسخ را در یک browsing context جدید و بدون نام بارگذاری می‌کند. معمولاً این یک تب جدید در همان پنجرهٔ سند جاری است، اما بسته به پیکربندی {{Glossary("user agent")}} ممکن است متفاوت باشد.
- `_parent`
  - : پاسخ را در browsing context والد context جاری بارگذاری می‌کند. اگر context پدری وجود نداشته باشد، مانند `_self` عمل می‌کند.
- `_top`
  - : پاسخ را در browsing context سطح بالا بارگذاری می‌کند؛ یعنی browsing context که بالاترین ancestor از context جاری است. اگر context جاری، همان context سطح بالا باشد، این مقدار مانند `_self` عمل می‌کند.

این ویژگی روی [`<input type="submit">`](/en-US/docs/Web/HTML/Reference/Elements/input/submit) و عناصر {{HTMLElement("button")}} نیز موجود است.

### height

عددی که ارتفاع تصویر مشخص‌شده در ویژگی `src` را بر حسب پیکسل CSS تعیین می‌کند.

### src

رشته‌ای که آدرس فایل تصویری را مشخص می‌کند که برای نمایش دکمهٔ ارسال گرافیکی استفاده می‌شود. وقتی کاربر با تصویر تعامل می‌کند، input مانند سایر دکمه‌ها رفتار می‌شود.

### width

عددی که عرض تصویر را بر حسب پیکسل CSS مشخص می‌کند.

## ویژگی‌های منسوخ

ویژگی زیر در HTML 4 برای inputهای `image` تعریف شده بود، اما توسط همهٔ مرورگرها پیاده‌سازی نشده و از آن زمان منسوخ شده است.

### usemap

اگر `usemap` مشخص شده باشد، باید نام یک image map (عنصر `<map>`) باشد که تعیین می‌کند از کدام image map برای تصویر استفاده شود. این روش قدیمی است و بهتر است برای استفاده از image mapها از عنصر `<img>` استفاده کنید.

## استفاده از ورودی‌های تصویری

المان `<input type="image">` یک [عنصر جایگزین‌شونده](glossary) است (عنصری که محتوای آن توسط لایه CSS تولید یا مستقیماً مدیریت نمی‌شود) و رفتاری مشابه یک عنصر معمولی `<img>` دارد، با این تفاوت که قابلیت‌های یک [دکمه ارسال (submit button)](/en-US/docs/Web/HTML/Reference/Elements/input/submit) را نیز دارد.

### ویژگی‌های ضروری ورودی تصویری

بیایید یک مثال ساده ببینیم که شامل تمام ویژگی‌های ضروری برای استفاده است (این ویژگی‌ها دقیقاً مانند عنصر `<img>` کار می‌کنند):

```html
<input
  id="image"
  type="image"
  width="100"
  height="30"
  alt="Login"
  src="https://raw.githubusercontent.com/mdn/learning-area/master/html/forms/image-type-example/login.png" />
```

{{ EmbedLiveSample('Essential_image_input_features', 600, 50) }}

- ویژگی [`src`](/en-US/docs/Web/HTML/Reference/Elements/input#src) برای تعیین مسیر تصویری که می‌خواهید روی دکمه نمایش داده شود استفاده می‌شود.
- ویژگی [`alt`](/en-US/docs/Web/HTML/Reference/Elements/input#alt) متن جایگزین تصویر را فراهم می‌کند تا کاربران screen reader بتوانند درک بهتری از کاربرد دکمه داشته باشند. همچنین اگر تصویر به هر دلیلی (مثلاً اشتباه بودن مسیر) نمایش داده نشود، این متن نشان داده می‌شود. در صورت امکان، از متنی استفاده کنید که با برچسبی که در یک دکمه submit معمولی می‌نوشتید مطابقت داشته باشد.
- ویژگی‌های [`width`](/en-US/docs/Web/HTML/Reference/Elements/input#width) و [`height`](/en-US/docs/Web/HTML/Reference/Elements/input#height) برای تعیین عرض و ارتفاع تصویر بر حسب پیکسل استفاده می‌شوند. اندازه دکمه برابر با اندازه تصویر است؛ اگر نیاز دارید ناحیه قابل کلیک (hit area) بزرگ‌تر از تصویر باشد، باید از CSS استفاده کنید (مثلاً {{cssxref("padding")}}). همچنین اگر فقط یک بعد را مشخص کنید، بعد دیگر به‌طور خودکار تنظیم می‌شود تا نسبت تصویر اصلی (aspect ratio) حفظ شود.

### لغو رفتارهای پیش‌فرض فرم

المان‌های `<input type="image">` – مانند [دکمه‌های submit معمولی](/en-US/docs/Web/HTML/Reference/Elements/input/submit) – می‌توانند تعدادی attribute دریافت کنند که رفتار پیش‌فرض فرم را لغو می‌کنند:

- `formaction`
  - : URI برنامه‌ای که اطلاعات ارسال‌شده توسط المان ورودی را پردازش می‌کند. این attribute، attribute [`action`](/en-US/docs/Web/HTML/Reference/Elements/form#action) فرم والد را لغو می‌کند.
- `formenctype`
  - : نوع محتوایی که برای ارسال فرم به سرور استفاده می‌شود را مشخص می‌کند. مقادیر ممکن:
    - `application/x-www-form-urlencoded`: مقدار پیش‌فرض اگر attribute مشخص نشده باشد.
    - `text/plain`.

    اگر این attribute مشخص شود، attribute [`enctype`](/en-US/docs/Web/HTML/Reference/Elements/form#enctype) فرم والد را لغو می‌کند.

- `formmethod`
  - : روش HTTP که مرورگر برای ارسال فرم استفاده می‌کند را مشخص می‌کند. مقادیر ممکن:
    - `post`: داده‌های فرم در بدنه درخواست قرار گرفته و به سرور ارسال می‌شود.
    - `get`: داده‌های فرم به URI attribute **`form`** اضافه می‌شود (با جداکننده '؟') و URI حاصل به سرور ارسال می‌شود. از این روش زمانی استفاده کنید که فرم عوارض جانبی نداشته و فقط شامل کاراکترهای ASCII است.

    اگر مشخص شود، این attribute attribute [`method`](/en-US/docs/Web/HTML/Reference/Elements/form#method) فرم والد را لغو می‌کند.

- `formnovalidate`
  - : یک ویژگی Boolean که مشخص می‌کند هنگام ارسال فرم، اعتبارسنجی انجام نشود. اگر این ویژگی مشخص شده باشد، بر ویژگی [`novalidate`](/en-US/docs/Web/HTML/Reference/Elements/form#novalidate) عنصر والد فرم (form owner) غلبه می‌کند.
- `formtarget`
  - : یک نام یا کلمه کلیدی که مشخص می‌کند پاسخ دریافت‌شده پس از ارسال فرم در کجا نمایش داده شود. این مقدار می‌تواند نام یک _browsing context_ (مثل تب، پنجره یا iframe) یا یکی از کلمات کلیدی زیر باشد. اگر این ویژگی مشخص شده باشد، بر ویژگی [`target`](/en-US/docs/Web/HTML/Reference/Elements/form#target) عنصر والد فرم غلبه می‌کند. کلمات کلیدی زیر معانی خاصی دارند:
    - `_self`: پاسخ را در همان browsing context فعلی بارگذاری می‌کند. این مقدار پیش‌فرض است اگر ویژگی指定 نشده باشد.
    - `_blank`: پاسخ را در یک browsing context جدید و بدون نام بارگذاری می‌کند.
    - `_parent`: پاسخ را در browsing context والد (والدِ) context فعلی بارگذاری می‌کند. اگر والد وجود نداشته باشد، این گزینه مانند `_self` عمل می‌کند.
    - `_top`: پاسخ را در browsing context سطح بالا (یعنی browsing context‌ای که ancestor context فعلی است و والد ندارد) بارگذاری می‌کند. اگر والد وجود نداشته باشد، این گزینه مانند `_self` عمل می‌کند.

### استفاده از داده‌های موقعیت x و y

وقتی فرمی را با دکمه‌ای که با `<input type="image">` ساخته شده ارسال می‌کنید، دو داده اضافی به طور خودکار توسط مرورگر به سرور ارسال می‌شود: `x` و `y`. می‌توانید این را در [مثال مختصات X Y](https://mdn.github.io/learning-area/html/forms/image-type-example/xy-coordinates-example.html) ببینید.

وقتی روی تصویر کلیک می‌کنید تا فرم ارسال شود، می‌بینید که داده‌ها به صورت پارامترهایی به URL اضافه می‌شوند، مثلاً `?x=52&y=55`. اگر ورودی تصویر دارای ویژگی [`name`](/en-US/docs/Web/HTML/Reference/Elements/input#name) باشد، نام مشخص‌شده با یک نقطه به عنوان جداکننده به هر کدام از مختصات اضافه می‌شود. مثلاً اگر `name` برابر `position` باشد، مختصات برگشتی در URL به صورت `?position.x=52&position.y=55` قالب‌بندی می‌شوند.

این مختصات X و Y نقطه‌ای از تصویر هستند که ماوس روی آن کلیک کرده تا فرم ارسال شود، جایی که (0,0) گوشه بالا-چپ تصویر است و در صورت ارسال بدون کلیک روی تصویر، این مقدار پیش‌فرض است. این مختصات زمانی مفید هستند که موقعیت کلیک روی تصویر اهمیت دارد، مثلاً می‌توانید یک نقشه داشته باشید که با کلیک، مختصات کلیک‌شده را به سرور ارسال کند. سپس کد سمت سرور تشخیص می‌دهد که چه مکانی کلیک شده و اطلاعاتی درباره مکان‌های نزدیک برمی‌گرداند.

در مثال بالا، می‌توانیم کد سمت سروری بنویسیم که با توجه به مختصات ارسالی تشخیص دهد چه رنگی کلیک شده است و تعداد رای‌های رنگ‌های محبوب را ثبت کند.

### تنظیم موقعیت و الگوریتم مقیاس‌گذاری تصویر

می‌توانید از ویژگی `object-position` برای تنظیم موقعیت تصویر درون قاب عنصر `<input>` و از ویژگی `object-fit` برای کنترل نحوه تنظیم اندازه تصویر درون قاب استفاده کنید. این به شما امکان می‌دهد یک قاب برای تصویر با استفاده از ویژگی‌های `width` و `height` تعیین کنید و سپس مکان و نحوه مقیاس‌گذاری (یا عدم مقیاس‌گذاری) تصویر را درون آن فضا تنظیم کنید.

## مثال‌ها

### یک فرم ورود (login)

مثال زیر همان دکمه قبلی را نشان می‌دهد، اما در زمینه یک فرم ورود معمولی.

#### HTML

### مثال پایه

```html
<form>
  <p>Login to your account</p>
  <div>
    <label for="userId">User ID</label>
    <input type="text" id="userId" name="userId" />
  </div>
  <div>
    <label for="pwd">Password</label>
    <input type="password" id="pwd" name="pwd" />
  </div>
  <div>
    <input
      id="image"
      type="image"
      src="https://raw.githubusercontent.com/mdn/learning-area/master/html/forms/image-type-example/login.png"
      alt="Login"
      width="100" />
  </div>
</form>
```

#### CSS

و حالا کمی CSS تا عناصر پایه مرتب‌تر چیده شوند:

```css
div {
  margin-bottom: 10px;
}

label {
  display: inline-block;
  width: 70px;
  text-align: right;
  padding-right: 10px;
}
```

### تنظیم موقعیت و مقیاس تصویر

در این مثال، مثال قبلی را تغییر می‌دهیم تا فضای بیشتری برای تصویر کنار بگذاریم و سپس اندازه و موقعیت واقعی تصویر را با استفاده از `object-fit` و `object-position` تنظیم کنیم.

#### HTML

```html
<form>
  <p>Login to your account</p>
  <div>
    <label for="userId">User ID</label>
    <input type="text" id="userId" name="userId" />
  </div>
  <div>
    <label for="pwd">Password</label>
    <input type="password" id="pwd" name="pwd" />
  </div>
  <div>
    <input
      id="image"
      type="image"
      src="https://raw.githubusercontent.com/mdn/learning-area/master/html/forms/image-type-example/login.png"
      alt="Login"
      width="200"
      height="100" />
  </div>
</form>
```

#### CSS

```css
div {
  margin-bottom: 10px;
}

label {
  display: inline-block;
  width: 70px;
  text-align: right;
  padding-right: 10px;
}

#image {
  object-position: right top;
  object-fit: contain;
  background-color: #dddddd;
}
```

در اینجا، `object-position` طوری تنظیم شده که تصویر در گوشه بالا-راست عنصر رسم شود؛ در حالی که `object-fit` برابر با `contain` است، یعنی تصویر باید در بزرگ‌ترین اندازه‌ای که بدون تغییر نسبت ابعاد در جعبه عنصر جا می‌شود رسم شود. توجه کنید که پس‌زمینه خاکستری عنصر همچنان در ناحیه‌ای که تصویر پوشش نداده دیده می‌شود.

## خلاصه فنی

| ویژگی | توضیح |
| --- | --- |
| **Value** | هیچ — نباید attribute ای به نام `value` مشخص شود. |
| **Events** | هیچ. |
| **Supported common attributes** | [`alt`](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/input#alt)، [`src`](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/input#src)، [`width`](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/input#width)، [`height`](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/input#height)، [`formaction`](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/input#formaction)، [`formenctype`](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/input#formenctype)، [`formmethod`](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/input#formmethod)، [`formnovalidate`](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/input#formmethod)، [`formtarget`](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/input#formtarget) |
| **IDL attributes** | هیچ. |
| **DOM interface** | `HTMLInputElement` |
| **Implicit ARIA Role** | [`button`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/button_role) |

- المان `<input>` و رابط `HTMLInputElement` که آن را پیاده‌سازی می‌کند.
- المان `<img>` در HTML
- موقعیت‌دهی و اندازه‌دهی تصویر در چارچوب المان `<input>`: `object-position` و `object-fit`