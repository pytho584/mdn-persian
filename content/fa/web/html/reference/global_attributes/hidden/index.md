---
title: "hidden HTML global attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Global_attributes/hidden"
translated_by: "n8n + AI"
---

The **`hidden`** [ویژگی سراسری](/en-US/docs/Web/HTML/Reference/Global_attributes) یک ویژگی شمارشی (enumerated) است که به مرورگر اعلام می‌کند محتوای عنصر را رندر نکند. برای مثال می‌توان از آن برای پنهان کردن بخش‌هایی از صفحه که تا تکمیل فرایند ورود به سیستم قابل استفاده نیستند استفاده کرد.

```html interactive-example
<p>
  This content should be read right now, as it is important. I am so glad you
  are able to find it!
</p>

<p hidden>
  This content is not relevant to this page right now, so should not be seen.
  Nothing to see here. Nada.
</p>
```

```css interactive-example
p {
  background: #ffe8d4;
  border: 1px solid #f69d3c;
  padding: 5px;
  border-radius: 5px;
}
```

## Description

ویژگی `hidden` مشخص می‌کند که محتوای یک عنصر نباید به کاربر نمایش داده شود. این ویژگی یکی از مقادیر زیر را می‌پذیرد:

- کلیدواژه `hidden`
- کلیدواژه `until-found`
- یک رشته خالی یا بدون مقدار

مقادیر نامعتبر برای `hidden` نیز عنصر را در وضعیت _hidden_ قرار می‌دهند. بنابراین، همه عناصر زیر در وضعیت [_hidden_](#the_hidden_state) هستند:

```html
<span hidden>I'm hidden</span>
<span hidden="">I'm also hidden</span>
<span hidden="hidden">I'm hidden too!</span>
<span hidden="bananas">I'm equally as hidden!</span>
```

کلیدواژه `until-found` عنصر را در وضعیت [_hidden until found_](#the_hidden_until_found_state) قرار می‌دهد:

```html
<span hidden="until-found">I'm hidden until found</span>
```

### The hidden state

وضعیت _hidden_ نشان می‌دهد که عنصر در حال حاضر برای صفحه مرتبط نیست، یا برای اعلام محتوایی استفاده می‌شود که قرار است توسط بخش‌های دیگر صفحه دوباره استفاده شود و نباید مستقیماً به کاربر نمایش داده شود. مرورگر عناصری را که در وضعیت _hidden_ هستند رندر نمی‌کند.

مرورگرها ممکن است وضعیت _hidden_ را با `display: none` پیاده‌سازی کنند؛ در این صورت عنصر در چیدمان (layout) صفحه شرکت نمی‌کند. همچنین تغییر مقدار ویژگی CSS `display` روی یک عنصر پنهان، وضعیت _hidden_ را بازنویسی می‌کند. برای مثال، عناصری که `display: block` دارند با وجود ویژگی `hidden` نمایش داده می‌شوند.

### The hidden until found state

در وضعیت _hidden until found_، عنصر پنهان است اما محتوای آن برای قابلیت «یافتن در صفحه» (Find in page) مرورگر یا برای پیمایش به قطعه (fragment navigation) قابل دسترسی خواهد بود. وقتی این قابلیت‌ها باعث پیمایش به یک عنصر در زیردرخت _hidden until found_ شوند، مرورگر این کارها را انجام می‌دهد:

1. رویداد [`beforematch`](/en-US/docs/Web/API/Element/beforematch_event) روی عنصر پنهان صادر می‌شود
2. ویژگی `hidden` را از عنصر حذف می‌کند
3. به عنصر اسکرول می‌کند

این امکان به شما می‌دهد بخشی از محتوا را جمع کنید، اما همچنان به کاربران اجازه دهید از طریق جستجو یا پیمایش آن را پیدا کنند.

مرورگرها معمولاً _hidden until found_ را با `content-visibility: hidden` پیاده‌سازی می‌کنند. یعنی برخلاف عناصر در وضعیت _hidden_، عناصر در وضعیت _hidden until-found_ جعبه (box) تولید می‌کنند و:

- در چیدمان صفحه شرکت می‌کنند
- margin، border، padding و پس‌زمینه آن‌ها رندر می‌شود

همچنین، برای اینکه عنصر آشکار شود، باید تحت تأثیر [layout containment](/en-US/docs/Web/CSS/Guides/Containment) باشد. اگر عنصر در وضعیت _hidden until found_ مقدار `display` برابر `none`، `contents` یا `inline` داشته باشد، با «یافتن در صفحه» یا پیمایش به قطعه آشکار نمی‌شود.

## Usage notes

ویژگی `hidden` نباید فقط برای پنهان کردن محتوا از یک روش نمایش خاص استفاده شود. اگر چیزی به‌عنوان پنهان علامت‌گذاری شود، از همه روش‌های نمایش پنهان است؛ از جمله، برای مثال، صفحه‌خوان‌ها (screen readers).

عناصر پنهان (hidden) نباید از طریق عناصر visible لینک شوند، مگر اینکه از `hidden="until-found"` استفاده شده باشد.
برای مثال، استفاده از attribute `href` برای لینک دادن به یک بخش دارای attribute `hidden` نادرست است. اگر محتوا قابل استفاده یا مرتبط نیست، نباید لینک شود.

با این حال، استفاده از ARIA attribute با نام [`aria-describedby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-describedby) برای اشاره به توضیحات پنهان مجاز است. اگرچه پنهان بودن توضیحات به این معناست که به‌تنهایی کاربرد ندارند، اما وقتی به این شکل ارجاع داده شوند می‌توانند زمینهٔ مفیدی فراهم کنند.

به همین ترتیب، یک عنصر canvas با attribute `hidden` می‌تواند توسط یک موتور گرافیکی مبتنی بر اسکریپت به‌عنوان بافر خارج از صفحه استفاده شود، و یک کنترل فرم می‌تواند با استفاده از attribute form خود به یک عنصر فرم پنهان ارجاع دهد.

در نهایت، توجه کنید که عناصری که فرزند یک عنصر پنهان هستند همچنان فعال می‌مانند؛ یعنی عناصر `script` همچنان می‌توانند اجرا شوند و عناصر فرم می‌توانند ارسال شوند:

```html
<div hidden>
  <script>
    console.warn("Boo! I'm hidden *and* running!");
  </script>
</div>
```

## مثال‌ها

### استفاده از ویژگی hidden

در این مثال، سه عنصر {{HTMLElement("div")}} داریم. اولی و سومی پنهان نیستند، اما دومی دارای attribute `hidden` است.
توجه کنید که عنصر پنهان، box (جعبه) تولیدشده ندارد.

```html
<div>I'm not hidden</div>
<div hidden>I'm hiding!</div>
<div>I'm not hidden, either</div>
```

```css hidden
div {
  height: 40px;
  width: 300px;
  border: 5px dashed black;
  margin: 1rem 0;
  padding: 1rem;
  font-size: 2rem;
}
```

### استفاده از مقدار until-found

در این مثال، سه عنصر {{HTMLElement("div")}} داریم.
اولی و سومی قابل مشاهده هستند، در حالی که دومی دارای attribute های `hidden="until-found"` و `id="until-found-box"` است.
عنصری که id آن `until-found-box` است، حاشیهٔ نقطه‌چین قرمز و پس‌زمینهٔ خاکستری دارد.

همچنین یک لینک داریم که به fragment `"until-found-box"` اشاره می‌کند و کد جاوااسکریپتی که به رویداد `beforematch` روی آن عنصر پنهان گوش می‌دهد.
هندلر رویداد، محتوای متنی box را تغییر می‌دهد تا عملی را نشان دهد که هنگام برداشته شدن حالت _hidden until found_ رخ می‌دهد.

#### HTML

```html
<a href="#until-found-box">Go to hidden content</a>

<div>I'm not hidden</div>
<div id="until-found-box" hidden="until-found">Hidden until found</div>
<div>I'm not hidden, either</div>
```

```html hidden
<button id="reset">Reset</button>
```

#### CSS

```css
div {
  height: 40px;
  width: 300px;
  border: 5px dashed black;
  margin: 1rem 0;
  padding: 1rem;
  font-size: 2rem;
}

div#until-found-box {
  color: red;
  border: 5px dotted red;
  background-color: lightgray;
}
```

```css hidden
#until-found-box {
  scroll-margin-top: 200px;
}
```

#### JavaScript

```js
const untilFound = document.querySelector("#until-found-box");
untilFound.addEventListener(
  "beforematch",
  () => (untilFound.textContent = "I've been revealed!"),
);
```

```js hidden
document.querySelector("#reset").addEventListener("click", () => {
  document.location.hash = "";
  document.location.reload();
});
```

#### نتیجه

با کلیک روی لینک «Go to hidden content»، به عنصر _hidden until found_ هدایت می‌شوید. رویداد `beforematch` فعال می‌شود، محتوای متنی به‌روز می‌شود و عنصر قابل مشاهده می‌گردد.
توجه کنید که اگرچه محتوای عنصر پنهان است، خود عنصر همچنان یک box تولیدشده دارد که در چیدمان فضا اشغال می‌کند و پس‌زمینه و حاشیه آن رندر می‌شود.

برای اجرای مجدد مثال، روی «Reset» کلیک کنید.

- ویژگی [`HTMLElement.hidden`](https://developer.mozilla.org/en-US/docs/Web/API/HTMLElement/hidden)
- همهٔ [ویژگی‌های سراسری (global attributes)](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Global_attributes)
- ویژگی [`aria-hidden`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-hidden)
- رویداد [`beforematch`](https://developer.mozilla.org/en-US/docs/Web/API/Element/beforematch_event)