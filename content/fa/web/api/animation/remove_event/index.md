---
title: "Animation: remove event"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Animation/remove_event"
translated_by: "n8n + AI"
---

---
title: "Animation: remove event"
short-title: remove
slug: Web/API/Animation/remove_event
page-type: web-api-event
browser-compat: api.Animation.remove_event
---

{{ APIRef("Web Animations") }}

رویداد **`remove`** از رابط {{domxref("Animation")}} زمانی فعال میشود که پویانمایی توسط مرورگر [بهطور خودکار حذف شود](/en-US/docs/Web/API/Web_Animations_API/Using_the_Web_Animations_API#automatically_removing_filling_animations).

## نحو (Syntax)

از نام رویداد در روشهایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی مدیریت رویداد تنظیم کنید.

```js-nolint
addEventListener("remove", (event) => { })

onremove = (event) => { }
```

## نوع رویداد

یک {{domxref("AnimationPlaybackEvent")}}. به ارث برده شده از {{domxref("Event")}}.

{{InheritanceDiagram("AnimationPlaybackEvent")}}

## مثالها

### حذف پویانماییهای جایگزینشده

در این مثال، یک عنصر `<button id="start">` و یک شنونده رویداد داریم که با هر بار حرکت ماوس اجرا میشود. مدیریتکننده رویداد {{domxref("Element.mousemove_event","mousemove")}} یک پویانمایی راهاندازی میکند که `<button>` را به موقعیت نشانگر ماوس متحرک میسازد. این میتواند به فهرست عظیمی از پویانماییها منجر شود که ممکن است نشت حافظه ایجاد کند. به همین دلیل، مرورگرهای مدرن بهطور خودکار پویانماییهای دارای `fill: forwards` را که توسط پویانماییهای دیگر بازنویسی میشوند، حذف میکنند.

تعداد پویانماییهای ایجادشده نمایش داده میشود. یک شنونده رویداد `remove` برای شمارش و نمایش تعداد پویانماییهای حذفشده نیز استفاده میشود.

همه پویانماییها بهجز یکی در نهایت باید حذف شوند.

#### HTML

```html
<button id="start">برای کشیدن کلیک کنید</button>
<br />
<button id="reset">بازنشانی مثال</button>
<p>
  برای شروع پویانمایی روی دکمه کلیک کنید (بهطور پیشفرض غیرفعال است تا از
  افرادی که با مشاهده چنین پویانماییهایی دچار میگرن میشوند محافظت کند).
</p>
<p>پویانماییهای ایجادشده: <span id="count-created">0</span></p>
<p>پویانماییهای حذفشده: <span id="count-removed">0</span></p>
```

#### CSS

```css
:root,
body {
  margin: 0;
  padding: 0;
  height: 100%;
}

button {
  margin: 0.5rem 0;
}
```

#### JavaScript

```js
const button = document.querySelector("#start");
let created = 0;
let removed = 0;

button.addEventListener(
  "click",
  () => {
    document.body.addEventListener("mousemove", (event) => {
      const animation = button.animate(
        { transform: `translate(${event.clientX}px, ${event.clientY}px)` },
        { duration: 500, fill: "forwards" },
      );
      created++;
      showCounts();

      // the remove event fires after the animation is removed
      animation.addEventListener("remove", () => {
        removed++;
        showCounts();
      });
    });
  },
  { once: true },
);

function showCounts() {
  document.getElementById("count-created").textContent = created;
  document.getElementById("count-removed").textContent = removed;
}

const reset = document.querySelector("#reset");
reset.addEventListener("click", () => {
  document.location.reload();
});
```

#### نتیجه

{{embedlivesample("Removing_replaced_animations","",250)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Web Animations API](/en-US/docs/Web/API/Web_Animations_API)
- {{domxref("Animation")}}, {{domxref("AnimationPlaybackEvent")}}
- {{domxref("Animation.replaceState")}}، برای بررسی اینکه آیا پویانمایی حذف شده است
- {{domxref("Animation.persist()")}}، برای جلوگیری از حذف یک پویانمایی