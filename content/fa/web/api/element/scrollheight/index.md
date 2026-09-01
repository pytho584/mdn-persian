---
title: "Element: scrollHeight property"
short-title: scrollHeight
slug: Web/API/Element/scrollHeight
page-type: web-api-instance-property
browser-compat: api.Element.scrollHeight
---

{{APIRef("DOM")}}

ویژگی فقط‌خواندنی **`scrollHeight`** در رابط {{domxref("Element")}} اندازه‌گیری ارتفاع محتوای یک عنصر است؛ از جمله محتوایی که به دلیل سرریز (overflow) در صفحه نمایش قابل مشاهده نیست.

![نمای دید کاربر یک عنصر است با چهار ناحیه مشخص‌شده به نام‌های padding-top، border-top، border-bottom، padding-bottom. ارتفاع اسکرول از padding بالای ظرف (container) تا انتهای padding پایین می‌رود، بسیار فراتر از بالا و پایین نمای دید.](scrollheight.png)

مقدار `scrollHeight` برابر است با حداقل ارتفاعی که عنصر برای جا دادن تمام محتوا در نمای دید بدون استفاده از نوار پیمایش عمودی لازم دارد. ارتفاع به همان روش {{domxref("Element.clientHeight", "clientHeight")}} اندازه‌گیری می‌شود: شامل `padding` عنصر است، اما `border`، `margin` یا نوار پیمایش افقی (در صورت وجود) را شامل نمی‌شود. همچنین ممکن است ارتفاع شبه‌عنصرهایی مانند {{cssxref("::before")}} یا {{cssxref("::after")}} را نیز شامل شود. اگر محتوای عنصر بدون نیاز به نوار پیمایش عمودی جا شود، `scrollHeight` آن برابر با {{domxref("Element.clientHeight", "clientHeight")}} است.

## مقدار

یک عدد صحیح.

## مسائل و راه‌حل‌ها

### تعیین اینکه آیا یک عنصر به‌طور کامل پیمایش شده است

`scrollTop` عددی است که می‌تواند اعشار داشته باشد، در حالی که `scrollHeight` و `clientHeight` اعداد گردشده (صحیح) هستند — بنابراین تنها راه تعیین اینکه ناحیه پیمایش به پایین رسیده است، بررسی نزدیکی مقدار پیمایش به یک آستانه مشخص (در این مثال `1`) است:

```js
Math.abs(element.scrollHeight - element.clientHeight - element.scrollTop) <= 1;
```

کد زیر همیشه کار نخواهد کرد، زیرا `scrollTop` ممکن است اعشار داشته باشد:

```js
element.scrollHeight - Math.abs(element.scrollTop) === element.clientHeight;
```

### تعیین اینکه آیا محتوای یک عنصر سرریز می‌کند

این تابع یک مقدار بولین برمی‌گرداند که نشان می‌دهد آیا محتوای یک عنصر از مرزهای خود سرریز می‌کند یا خیر:

```js
function isOverflowing(element) {
  return element.scrollHeight > element.clientHeight;
}
```

سپس، ممکن است بخواهید بررسی کنید که آیا عنصر در این حالت قابل پیمایش است:

```js
function isScrollable(element) {
  return (
    isOverflowing(element) &&
    ["scroll", "auto"].includes(window.getComputedStyle(element).overflowY)
  );
}
```

## مثال‌ها

### بررسی اینکه کاربر متنی را خوانده است

این تساوی، همراه با رویداد {{domxref("Element.scroll_event", "scroll")}}، می‌تواند برای تعیین اینکه آیا کاربر متنی را خوانده است مفید باشد (همچنین به ویژگی‌های {{domxref("element.scrollTop")}} و {{domxref("element.clientHeight")}} مراجعه کنید).

چک‌باکس در نسخه نمایشی زیر غیرفعال است و تا زمانی که محتوای پاراگراف پیمایش نشده باشد، نمی‌توان آن را برای اعلام موافقت علامت زد. پس از علامت زدن، دکمه «بعدی» برای ادامه قابل کلیک می‌شود.

#### HTML

```html
<form id="form" name="registration">
  <p id="info">Read all text to agree</p>
  <div id="very-important-read">
    <p>
      Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod
      tempor incididunt ut labore et dolore magna aliqua. Feugiat sed lectus
      vestibulum mattis. Id consectetur purus ut faucibus pulvinar elementum
      integer enim neque. Metus vulputate eu scelerisque felis imperdiet. Massa
      massa ultricies mi quis hendrerit dolor magna eget est. Rhoncus aenean vel
      elit scelerisque mauris pellentesque. Volutpat est velit egestas dui id
      ornare arcu. Id cursus metus aliquam eleifend mi in. Condimentum lacinia
      quis vel eros donec ac. Feugiat pretium nibh ipsum consequat nisl vel
      pretium lectus.
    </p>
    <p>
      Sit amet volutpat consequat mauris nunc congue nisi vitae. Viverra
      accumsan in nisl nisi scelerisque. Enim ut tellus elementum sagittis
      vitae. Dolor sed viverra ipsum nunc aliquet bibendum enim facilisis. Nisi
      scelerisque eu ultrices vitae. Sem fringilla ut morbi tincidunt augue
      interdum velit. Senectus et netus et malesuada fames ac turpis egestas.
      Nunc non blandit massa enim nec. At augue eget arcu dictum varius duis at.
      Dictumst quisque sagittis purus sit amet. Ut eu sem integer vitae justo.
      Mollis aliquam ut porttitor leo a diam sollicitudin. Mollis nunc sed id
      semper risus in. Eu volutpat odio facilisis mauris sit. Augue interdum
      velit euismod in pellentesque massa placerat duis. Aliquam faucibus purus
      in massa tempor nec feugiat. Nisl rhoncus mattis rhoncus urna neque
      viverra justo. Leo duis ut diam quam nulla. Ultrices dui sapien eget mi
      proin sed libero enim.
    </p>
    <p>
      Cras adipiscing enim eu turpis egestas. Est ultricies integer quis auctor
      elit. Tempor id eu nisl nunc mi ipsum. Non nisi est sit amet facilisis.
      Nisl suscipit adipiscing bibendum est ultricies integer quis. Habitant
      morbi tristique senectus et netus et malesuada. Etiam erat velit
      scelerisque in dictum non consectetur a erat. Diam sollicitudin tempor id
      eu nisl. Aenean vel elit scelerisque mauris pellentesque pulvinar
      pellentesque habitant. A pellentesque sit amet porttitor. Viverra aliquet
      eget sit amet tellus cras. Eu ultrices vitae auctor eu.
    </p>
    <p>
      Fames ac turpis egestas sed tempus. Id donec ultrices tincidunt arcu non
      sodales. Congue mauris rhoncus aenean vel elit scelerisque mauris
      pellentesque. Velit scelerisque in dictum non consectetur a erat nam.
      Auctor elit sed vulputate mi sit amet mauris commodo. Mauris ultrices eros
      in cursus turpis massa tincidunt. Dui sapien eget mi proin sed libero enim
      sed faucibus. Ipsum dolor sit amet consectetur adipiscing elit
      pellentesque habitant. Amet massa vitae tortor condimentum. Feugiat nisl
      pretium fusce id velit. Malesuada proin libero nunc consequat interdum
      varius sit. Quam nulla porttitor massa id neque aliquam vestibulum morbi
      blandit. Gravida arcu ac tortor dignissim convallis aenean et tortor at.
      Dapibus ultrices in iaculis nunc sed. Fermentum et sollicitudin ac orci
      phasellus egestas tellus. Proin libero nunc consequat interdum varius sit
      amet mattis. Sed viverra ipsum nunc aliquet bibendum.
    </p>
  </div>
  <p>
    <input type="checkbox" id="agree" name="accept" disabled />
    <label for="agree">I agree</label>
    <input type="submit" id="next-step" value="Next" disabled />
  </p>
</form>
```

#### CSS

```css
#info {
  margin: 5px;
  display: inline-block;
  font-style: italic;
}

#very-important-read {
  height: 130px;
  padding: 5px;
  border: 2px solid #00b4c5;
  border-radius: 5px;
  overflow: scroll;
}
```

#### JavaScript

```js
const info = document.getElementById("info");
const toAgree = document.getElementById("agree");
const toNextStep = document.getElementById("next-step");
const veryImportantRead = document.getElementById("very-important-read");

// Check if user has scrolled the element to the bottom
function isRead(element) {
  return (
    Math.abs(element.scrollHeight - element.clientHeight - element.scrollTop) <=
    1
  );
}

function checkScrollToBottom(element) {
  if (isRead(element)) {
    info.innerText = "You have read all text. Agree to continue.";
    toAgree.disabled = false;
  }
}

toAgree.addEventListener("change", (e) => {
  toNextStep.disabled = !e.target.checked;
});

veryImportantRead.addEventListener("scroll", () => {
  checkScrollToBottom(veryImportantRead);
});

toNextStep.addEventListener("click", () => {
  if (toAgree.checked) {
    toNextStep.value = "Done!";
  }
});
```

#### نتیجه

{{EmbedLiveSample('Checking_that_the_user_has_read_a_text', 640, 250)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [تعیین ابعاد عناصر](/en-US/docs/Web/API/CSS_Object_Model/Determining_the_dimensions_of_elements)
- {{domxref("HTMLElement.offsetHeight")}}
- {{domxref("Element.clientHeight")}}
- {{domxref("Element.scrollWidth")}}
- {{domxref("Element.scrollLeft")}}
- {{domxref("Element.scrollTop")}}
- {{domxref("Element.getBoundingClientRect()")}}
- {{domxref("Element.scrollTo()")}}