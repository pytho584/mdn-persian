---
title: "KeyboardEvent: code property"
short-title: code
slug: Web/API/KeyboardEvent/code
page-type: web-api-instance-property
browser-compat: api.KeyboardEvent.code
---

{{APIRef("UI Events")}}

ویژگی `KeyboardEvent.code` یک کلید فیزیکی روی صفحه‌کلید را نشان می‌دهد (در مقابل کاراکتری که با فشردن کلید تولید می‌شود). به عبارت دیگر، این ویژگی مقداری را برمی‌گرداند که با چیدمان صفحه‌کلید یا وضعیت کلیدهای اصلاح‌کننده تغییر نمی‌کند.

اگر دستگاه ورودی، صفحه‌کلید فیزیکی نباشد، بلکه یک صفحه‌کلید مجازی یا دستگاه دسترس‌پذیری باشد، مقدار بازگردانده‌شده توسط مرورگر به‌گونه‌ای تعیین می‌شود که تا حد ممکن با آنچه در صفحه‌کلید فیزیکی رخ می‌دهد مطابقت داشته باشد، تا سازگاری بین دستگاه‌های ورودی فیزیکی و مجازی بیشینه شود.

این ویژگی زمانی مفید است که بخواهید کلیدها را بر اساس موقعیت فیزیکی آن‌ها روی دستگاه ورودی مدیریت کنید، نه بر اساس کاراکترهای مرتبط با آن کلیدها. این کار به‌ویژه در نوشتن کد برای مدیریت ورودی بازی‌هایی رایج است که با استفاده از کلیدهای صفحه‌کلید، محیطی شبیه به گیم‌پد را شبیه‌سازی می‌کنند. با این حال، توجه داشته باشید که نمی‌توانید از مقدار گزارش‌شده توسط `KeyboardEvent.code` برای تعیین کاراکتر تولیدشده توسط ضربه کلید استفاده کنید، زیرا نام کد کلید ممکن است با کاراکتر واقعی چاپ‌شده روی کلید یا کاراکتری که هنگام فشردن کلید توسط رایانه تولید می‌شود، مطابقت نداشته باشد.

برای مثال، `code` بازگردانده‌شده برای کلید <kbd>Q</kbd> در صفحه‌کلید با چیدمان QWERTY مقدار `"KeyQ"` است، اما همین مقدار `code` در صفحه‌کلیدهای Dvorak نمایانگر کلید <kbd>'</kbd> و در صفحه‌کلیدهای AZERTY نمایانگر کلید <kbd>A</kbd> است. بنابراین اگر کاربران از چیدمان صفحه‌کلید مورد انتظار استفاده نکنند، استفاده از مقدار `code` برای تعیین نام کلید برای آن‌ها غیرممکن می‌شود.

برای تعیین اینکه کدام کاراکتر با رویداد کلید مطابقت دارد، به‌جای آن از ویژگی {{domxref("KeyboardEvent.key")}} استفاده کنید.

## مقدار

مقادیر کد برای Windows، Linux و macOS در صفحه [مقادیر کد KeyboardEvent](/en-US/docs/Web/API/UI_Events/Keyboard_event_code_values) فهرست شده‌اند.

## مثال‌ها

### آزمایش KeyboardEvent

#### HTML

```html
<p>
  Press keys on the keyboard to see what the KeyboardEvent's key and code values
  are for each one.
</p>
<div id="output" tabindex="0"></div>
```

#### CSS

```css
#output {
  font-family: "Helvetica", "Arial", sans-serif;
  border: 1px solid black;
  width: 95%;
  margin: auto;
}
#output:focus-visible {
  outline: 3px solid dodgerblue;
}
```

#### JavaScript

```js
window.addEventListener("keydown", (event) => {
  const p = document.createElement("p");
  p.textContent = `KeyboardEvent: key='${event.key}' | code='${event.code}'`;
  document.getElementById("output").appendChild(p);
  window.scrollTo(0, document.body.scrollHeight);
});
```

#### امتحان کنید

برای اطمینان از اینکه ضربه‌های کلید به نمونه می‌رسند، قبل از فشردن کلیدها، روی جعبه خروجی زیر کلیک کنید یا آن را فوکوس کنید.

{{ EmbedLiveSample('Exercising_KeyboardEvent', 600, 300) }}

### مدیریت رویدادهای صفحه‌کلید در یک بازی

این مثال یک شنونده رویداد برای رویدادهای {{domxref("Element/keydown_event", "keydown")}} ایجاد می‌کند که ورودی صفحه‌کلید را برای بازی‌ای مدیریت می‌کند که از چیدمان استاندارد صفحه‌کلید «WASD» برای حرکت به جلو، چپ، عقب و راست استفاده می‌کند. این کار از نظر فیزیکی از همان چهار کلید استفاده می‌کند، صرف‌نظر از اینکه کاراکترهای واقعی متناظر چه هستند، مثلاً اگر کاربر از صفحه‌کلید AZERTY استفاده کند.

#### HTML

```html
<p>Use the WASD (ZQSD on AZERTY) keys to move and steer.</p>
<svg
  xmlns="http://www.w3.org/2000/svg"
  version="1.1"
  class="world"
  tabindex="0">
  <polygon id="spaceship" points="15,0 0,30 30,30" />
</svg>
```

#### CSS

```css
.world {
  margin: 0px;
  padding: 0px;
  background-color: black;
  width: 400px;
  height: 400px;
}
.world:focus-visible {
  outline: 5px solid dodgerblue;
}
#spaceship {
  fill: orange;
  stroke: red;
  stroke-width: 2px;
}
```

#### JavaScript

بخش اول کد جاوااسکریپت چند متغیر را تعریف می‌کند که از آن‌ها استفاده خواهیم کرد. `shipSize` برای سهولت، اندازه سفینه‌ای را که بازیکن جابه‌جا می‌کند نگه می‌دارد. `position` برای پیگیری موقعیت سفینه در میدان بازی استفاده می‌شود. `moveRate` تعداد پیکسل‌هایی است که هر ضربه کلید سفینه را به جلو و عقب می‌برد، و `turnRate` تعداد درجه چرخشی است که کنترل‌های چپ و راست در هر ضربه کلید اعمال می‌کنند. `angle` مقدار فعلی چرخش اعمال‌شده به سفینه بر حسب درجه است؛ از ۰ درجه (اشاره به سمت بالا) شروع می‌شود. در نهایت، `spaceship` به عنصری با شناسه `"spaceship"` اشاره می‌کند که همان چندضلعی SVG نمایانگر سفینه‌ای است که بازیکن کنترل می‌کند.

```js
let shipSize = {
  width: 30,
  height: 30,
};

let position = {
  x: 200,
  y: 200,
};

let moveRate = 9;
let turnRate = 5;

let angle = 0;

let spaceship = document.getElementById("spaceship");
```

سپس تابع `updatePosition()` می‌آید. این تابع به‌عنوان ورودی، مسافتی را می‌گیرد که سفینه باید جابه‌جا شود؛ جایی که مثبت به معنای حرکت به جلو و منفی به معنای حرکت به عقب است. این تابع موقعیت جدید سفینه را بر اساس مسافت جابه‌جایی و جهت فعلی سفینه محاسبه می‌کند. همچنین اطمینان می‌دهد که سفینه به‌جای ناپدید شدن، از مرزهای میدان بازی عبور کرده و در سمت مقابل ظاهر می‌شود.

```js
function updatePosition(offset) {
  let rad = angle * (Math.PI / 180);
  position.x += Math.sin(rad) * offset;
  position.y -= Math.cos(rad) * offset;

  if (position.x < 0) {
    position.x = 399;
  } else if (position.x > 399) {
    position.x = 0;
  }

  if (position.y < 0) {
    position.y = 399;
  } else if (position.y > 399) {
    position.y = 0;
  }
}
```

تابع `refresh()` با استفاده از [تبدیل SVG](/en-US/docs/Web/SVG/Reference/Attribute/transform) اعمال چرخش و موقعیت را مدیریت می‌کند.

```js
function refresh() {
  let x = position.x - shipSize.width / 2;
  let y = position.y - shipSize.height / 2;
  let transform = `translate(${x} ${y}) rotate(${angle} 15 15) `;

  spaceship.setAttribute("transform", transform);
}
refresh();
```

در پایان، از متد `addEventListener()` برای شروع گوش دادن به رویدادهای {{domxref("Element/keydown_event", "keydown")}} استفاده می‌شود؛ با هر کلید، موقعیت سفینه و زاویه چرخش به‌روزرسانی می‌شود و سپس `refresh()` برای رسم سفینه در موقعیت و زاویه جدید فراخوانی می‌شود.

```js
window.addEventListener("keydown", (event) => {
  if (event.defaultPrevented) {
    return; // Do nothing if event already handled
  }

  switch (event.code) {
    case "KeyS":
    case "ArrowDown":
      // Handle "back"
      updatePosition(-moveRate);
      break;
    case "KeyW":
    case "ArrowUp":
      // Handle "forward"
      updatePosition(moveRate);
      break;
    case "KeyA":
    case "ArrowLeft":
      // Handle "turn left"
      angle -= turnRate;
      break;
    case "KeyD":
    case "ArrowRight":
      // Handle "turn right"
      angle += turnRate;
      break;
  }

  refresh();

  if (event.code !== "Tab") {
    // Consume the event so it doesn't get handled twice,
    // as long as the user isn't trying to move focus away
    event.preventDefault();
  }
});
```

#### امتحان کنید

برای اطمینان از اینکه ضربه‌های کلید به کد نمونه می‌رسند، قبل از فشردن کلیدها، روی میدان بازی سیاه‌رنگ زیر کلیک کنید یا آن را فوکوس کنید.

{{EmbedLiveSample("Handle_keyboard_events_in_a_game", 420, 460)}}

راه‌های مختلفی برای بهتر کردن این کد وجود دارد. بیشتر بازی‌های واقعی به‌جای اتکا به تکرار کلید، رویدادهای {{domxref("Element/keydown_event", "keydown")}} را زیر نظر می‌گیرند، هنگام وقوع آن حرکت را شروع می‌کنند و وقتی رویداد متناظر {{domxref("Element/keyup_event", "keyup")}} رخ می‌دهد، حرکت را متوقف می‌کنند. این کار هم حرکت نرم‌تر و سریع‌تری را ممکن می‌سازد و هم به بازیکن اجازه می‌دهد همزمان حرکت کند و بچرخد. همچنین می‌توان از ترنزیشن‌ها یا انیمیشن‌ها برای نرم‌تر کردن حرکت سفینه استفاده کرد.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}