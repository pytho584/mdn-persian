---
title: "Element: auxclick event"
short-title: auxclick
slug: Web/API/Element/auxclick_event
page-type: web-api-event
browser-compat: api.Element.auxclick_event
---

{{APIRef("UI Events")}}

رویداد **`auxclick`** روی یک {{domxref("Element")}} زمانی شلیک می‌شود که یک دکمه غیراصلی از دستگاه اشاره‌گر (هر دکمه ماوس به جز دکمه اصلی - معمولاً چپ‌ترین دکمه) درون همان عنصر فشار داده و رها شود.

رویداد `auxclick` پس از رویدادهای {{domxref("Element/mousedown_event", "mousedown")}} و {{domxref("Element/mouseup_event", "mouseup")}} به ترتیب شلیک می‌شود.

## نحو

از نام رویداد در متدهایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("auxclick", (event) => { })

onauxclick = (event) => { }
```

## نوع رویداد

یک {{domxref("PointerEvent")}} که از {{domxref("MouseEvent")}} ارث‌بری می‌کند.

{{InheritanceDiagram("PointerEvent")}}

> [!NOTE]
> در نسخه‌های قبلی مشخصات، نوع رویداد برای این رویداد یک {{domxref("MouseEvent")}} بود. برای اطلاعات بیشتر [سازگاری مرورگر](#browser_compatibility) را بررسی کنید.

## جلوگیری از اقدامات پیش‌فرض

برای اکثر مرورگرهایی که کلیک وسط را به باز کردن لینک در تب جدید نسبت می‌دهند، از جمله فایرفاکس، می‌توان با فراخوانی {{domxref("Event.preventDefault()", "preventDefault()")}} درون یک کنترل‌کننده رویداد `auxclick` این رفتار را لغو کرد.

هنگام گوش دادن به رویدادهای `auxclick` روی عناصری که ورودی یا ناوبری را پشتیبانی نمی‌کنند، اغلب می‌خواهید به صراحت از سایر اقدامات پیش‌فرض که به عمل پایین دکمه وسط ماوس نگاشت شده‌اند جلوگیری کنید. در ویندوز این معمولاً اسکرول خودکار است و در macOS و لینوکس معمولاً چسباندن کلیپ‌بورد است. این کار را می‌توان با جلوگیری از رفتار پیش‌فرض رویداد {{domxref("Element/mousedown_event", "mousedown")}} یا {{domxref("Element/pointerdown_event", "pointerdown")}} انجام داد.

علاوه بر این، ممکن است نیاز داشته باشید از باز شدن منوی زمینه سیستم پس از کلیک راست جلوگیری کنید. به دلیل تفاوت‌های زمانی بین سیستم‌عامل‌ها، این نیز یک رفتار پیش‌فرض قابل جلوگیری برای `auxclick` نیست. در عوض، این کار را می‌توان با جلوگیری از رفتار پیش‌فرض رویداد {{domxref("Element/contextmenu_event", "contextmenu")}} انجام داد.

## مثال‌ها

در این مثال ما توابعی را برای دو کنترل‌کننده رویداد تعریف می‌کنیم - {{domxref("Element.click_event", "onclick")}} و `onauxclick`. اولی رنگ پس‌زمینه دکمه را تغییر می‌دهد، در حالی که دومی رنگ پیش‌زمینه (متن) دکمه را تغییر می‌دهد. همچنین می‌توانید این دو تابع را در عمل با امتحان کردن دمو با یک ماوس چند دکمه‌ای ببینید ([مشاهده زنده در GitHub](https://mdn.github.io/dom-examples/auxclick/)؛ همچنین [کد منبع](https://github.com/mdn/dom-examples/blob/main/auxclick/index.html) را ببینید).

### JavaScript

```js
let button = document.querySelector("button");
let html = document.querySelector("html");

function random(number) {
  return Math.floor(Math.random() * number);
}

function randomColor() {
  return `rgb(${random(255)} ${random(255)} ${random(255)})`;
}

button.onclick = () => {
  button.style.backgroundColor = randomColor();
};

button.onauxclick = (e) => {
  e.preventDefault();
  button.style.color = randomColor();
};

button.oncontextmenu = (e) => {
  e.preventDefault();
};
```

### HTML

```html
<button>Click me!</button>
```

```css hidden
html {
  height: 100%;
  overflow: hidden;
}

body {
  height: inherit;
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 0;
}

button {
  border: 0;
  background-color: white;
  font-size: 8vw;
  display: block;
  width: 100%;
  height: 100%;
  letter-spacing: 0.5rem;
}
```

{{EmbedLiveSample("Examples", 640, 300)}}

> [!NOTE]
> اگر از ماوس سه دکمه‌ای استفاده می‌کنید، متوجه خواهید شد که کنترل‌کننده `onauxclick` زمانی اجرا می‌شود که هر یک از دکمه‌های غیرچپ ماوس کلیک شوند (معمولاً شامل هر دکمه "ویژه" روی ماوس‌های بازی نیز می‌شود).

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [یادگیری: مقدمه‌ای بر رویدادها](/en-US/docs/Learn_web_development/Core/Scripting/Events)
- {{domxref("Element/click_event", "click")}}
- {{domxref("Element/contextmenu_event", "contextmenu")}}
- {{domxref("Element/dblclick_event", "dblclick")}}
- {{domxref("Element/mousedown_event", "mousedown")}}
- {{domxref("Element/mouseup_event", "mouseup")}}
- {{domxref("Element/pointerdown_event", "pointerdown")}}
- {{domxref("Element/pointerup_event", "pointerup")}}