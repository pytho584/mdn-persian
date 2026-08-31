---
title: "Managing screen orientation"
---

---
title: Managing screen orientation
slug: Web/API/CSS_Object_Model/Managing_screen_orientation
page-type: guide
---

{{DefaultAPISidebar("Screen Orientation API")}}

اصطلاح _جهت‌گیری صفحه_ به وضعیت [نمای دید (viewport)](/en-US/docs/Glossary/Viewport) مرورگر اشاره دارد: آیا در حالت افقی (landscape) است — یعنی عرض نمای دید بیشتر از ارتفاع آن است — یا در حالت عمودی (portrait) — یعنی ارتفاع نمای دید بیشتر از عرض آن است.

CSS ویژگی رسانه‌ای {{cssxref("@media/orientation")}} را فراهم می‌کند تا تنظیم چیدمان بر اساس جهت‌گیری صفحه امکان‌پذیر شود.

[Screen Orientation API](/en-US/docs/Web/API/Screen_Orientation_API) یک رابط برنامه‌نویسی جاوااسکریپتی برای کار با جهت‌گیری صفحه فراهم می‌کند — از جمله قابلیت قفل کردن نمای دید در یک جهت‌گیری خاص.

## تنظیم چیدمان بر اساس جهت‌گیری

یکی از رایج‌ترین موارد تغییر جهت‌گیری زمانی است که می‌خواهید چیدمان محتوای خود را بر اساس جهت‌گیری دستگاه اصلاح کنید. برای مثال، شاید بخواهید یک نوار دکمه در امتداد بزرگ‌ترین بُعد نمایشگر دستگاه کشیده شود. با استفاده از یک کوئری رسانه می‌توانید این کار را به‌سادگی و به‌طور خودکار انجام دهید.

بیایید مثالی با کد HTML زیر داشته باشیم:

```html
<ul id="toolbar">
  <li>A</li>
  <li>B</li>
  <li>C</li>
</ul>

<p>
  Lorem ipsum dolor sit amet, consectetur adipiscing elit. Duis lacinia nisi nec
  sem viverra vitae fringilla nulla ultricies. In ac est dolor, quis tincidunt
  leo. Cras commodo quam non tortor consectetur eget rutrum dolor ultricies. Ut
  interdum tristique dapibus. Nullam quis malesuada est.
</p>
```

CSS برای اعمال استایل‌های خاص بر اساس جهت‌گیری صفحه، به کوئری رسانه جهت‌گیری متکی است:

```css
/* First let's define some common styles */

html,
body {
  width: 100%;
  height: 100%;
}

body {
  border: 1px solid black;

  -moz-box-sizing: border-box;
  box-sizing: border-box;
}

p {
  font: 1em sans-serif;
  margin: 0;
  padding: 0.5em;
}

ul {
  list-style: none;

  font: 1em monospace;
  margin: 0;
  padding: 0.5em;

  -moz-box-sizing: border-box;
  box-sizing: border-box;

  background: black;
}

li {
  display: inline-block;
  margin: 0;
  padding: 0.5em;
  background: white;
}
```

وقتی تعدادی استایل مشترک داشته باشیم، می‌توانیم شروع به تعریف حالت خاصی برای جهت‌گیری کنیم:

```css
/* For portrait, we want the toolbar on top */

@media screen and (orientation: portrait) {
  #toolbar {
    width: 100%;
  }
}

/* For landscape, we want the toolbar stick on the left */

@media screen and (orientation: landscape) {
  #toolbar {
    position: fixed;
    width: 2.65em;
    height: 100%;
  }

  p {
    margin-left: 2em;
  }

  li + li {
    margin-top: 0.5em;
  }
}
```

و در اینجا نتیجه آمده است:

<table class="no-markdown">
  <thead>
    <tr>
      <th scope="col">عمودی</th>
      <th scope="col">افقی</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <div>
          {{ EmbedLiveSample('Adjusting_layout_based_on_the_orientation', 180, 350) }}
        </div>
      </td>
      <td>
        <div>
          {{ EmbedLiveSample('Adjusting_layout_based_on_the_orientation', 350, 180) }}
        </div>
      </td>
    </tr>
  </tbody>
</table>

> [!NOTE]
> کوئری رسانه جهت‌گیری در واقع بر اساس جهت‌گیری پنجره مرورگر (یا iframe) اعمال می‌شود، نه جهت‌گیری خود دستگاه.

## قفل کردن جهت‌گیری صفحه

برخی دستگاه‌ها (عمدتاً دستگاه‌های همراه) می‌توانند جهت‌گیری صفحه را به‌صورت پویا بر اساس جهت‌گیری خودشان تغییر دهند تا اطمینان حاصل شود که کاربر همیشه بتواند محتوای روی صفحه را بخواند. هرچند این رفتار برای محتوای متنی کاملاً مناسب است، برخی محتواها ممکن است تحت تأثیر منفی چنین تغییری قرار گیرند. برای مثال، بازی‌هایی که بر اساس جهت‌گیری دستگاه طراحی شده‌اند ممکن است با چنین تغییری به هم بریزند.

Screen Orientation API برای جلوگیری یا مدیریت چنین تغییری ساخته شده است.

### گوش دادن به تغییرات جهت‌گیری

هر بار که جهت‌گیری صفحه تغییر کند، رویداد {{domxref("ScreenOrientation.change_event", "change")}} در رابط {{domxref("ScreenOrientation")}} فعال می‌شود:

```js
screen.orientation.addEventListener("change", () => {
  console.log(`The orientation of the screen is: ${screen.orientation}`);
});
```

### جلوگیری از تغییر جهت‌گیری

هر برنامه وب می‌تواند صفحه را مطابق نیاز خود قفل کند. صفحه با استفاده از متد {{domxref("ScreenOrientation.lock()", "screen.orientation.lock()")}} قفل می‌شود و با متد {{domxref("ScreenOrientation.unlock()", "screen.orientation.unlock()")}} از قفل خارج می‌شود.

متد {{domxref("ScreenOrientation.lock()", "screen.orientation.lock()")}} یکی از مقادیر زیر را برای تعریف نوع قفل می‌پذیرد: `any`، `natural`، `portrait-primary`، `portrait-secondary`، `landscape-primary`، `landscape-secondary`، `portrait` و `landscape`:

```js
screen.orientation.lock();
```

این متد یک [وعده (promise)](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise) برمی‌گرداند که پس از موفقیت قفل، حل می‌شود.

> [!NOTE]
> قفل کردن صفحه به برنامه وب وابسته است. اگر برنامه A به حالت `landscape` قفل شده و برنامه B به حالت `portrait` قفل شده باشد، جابه‌جایی از برنامه A به B یا از B به A رویداد `change` را روی `ScreenOrientation` فعال نمی‌کند، زیرا هر دو برنامه جهت‌گیری‌ای را که داشتند حفظ می‌کنند.
>
> با این حال، قفل کردن جهت‌گیری ممکن است رویداد `change` را فعال کند اگر جهت‌گیری برای برآوردن الزامات قفل مجبور به تغییر باشد.

## جستارهای وابسته

- {{domxref("Screen.orientation", "screen.orientation")}}
- {{domxref("ScreenOrientation")}}
- رویداد {{DOMxRef("ScreenOrientation.change_event", "change")}} از {{domxref("ScreenOrientation")}}
- {{cssxref("@media/orientation")}}
