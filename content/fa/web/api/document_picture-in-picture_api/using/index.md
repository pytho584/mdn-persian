---
title: Using the Document Picture-in-Picture API
slug: Web/API/Document_Picture-in-Picture_API/Using
page-type: guide
---

{{DefaultAPISidebar("Document Picture-in-Picture API")}}

این راهنما، نمونه‌ای از کاربرد معمول {{domxref("Document Picture-in-Picture API", "Document Picture-in-Picture API", "", "nocode")}} را شرح می‌دهد.

> [!NOTE]
> می‌توانید نسخهٔ نمایشی این مقاله را در [Document Picture-in-Picture API Example](https://mdn.github.io/dom-examples/document-picture-in-picture/) ببینید (همچنین [کد منبع](https://github.com/mdn/dom-examples/tree/main/document-picture-in-picture) کامل را ببینید).

## نمونه HTML

HTML زیر یک پخش‌کنندهٔ ویدیوی پایه را تنظیم می‌کند.

```html
<div id="container">
  <p class="in-pip-message">
    Video player is currently in the separate Picture-in-Picture window.
  </p>
  <div id="player">
    <video
      src="assets/bigbuckbunny.mp4"
      id="video"
      controls
      width="320"></video>

    <div id="credits">
      <a href="https://peach.blender.org/download/" target="_blank">
        Video by Blender </a
      >;
      <a href="https://peach.blender.org/about/" target="_blank">
        licensed CC-BY 3.0
      </a>
    </div>

    <div id="control-bar">
      <p class="no-picture-in-picture">
        Document Picture-in-Picture API not available
      </p>

      <p></p>
    </div>
  </div>
</div>
```

## شناسایی قابلیت

برای بررسی پشتیبانی از Document Picture-in-Picture API، می‌توانید بررسی کنید که آیا `documentPictureInPicture` روی `window` موجود است:

```js
if ("documentPictureInPicture" in window) {
  document.querySelector(".no-picture-in-picture").remove();

  const togglePipButton = document.createElement("button");
  togglePipButton.textContent = "Toggle Picture-in-Picture";
  togglePipButton.addEventListener("click", togglePictureInPicture);

  document.getElementById("control-bar").appendChild(togglePipButton);
}
```

اگر در دسترس باشد، پیام «Document Picture-in-Picture API در دسترس نیست» را حذف می‌کنیم و به‌جای آن یک عنصر {{htmlelement("button")}} برای باز کردن پخش‌کنندهٔ ویدیو در یک پنجرهٔ Document Picture-in-Picture اضافه می‌کنیم.

## باز کردن پنجرهٔ Picture-in-Picture

جاوااسکریپت زیر تابع {{domxref("DocumentPictureInPicture.requestWindow", "window.documentPictureInPicture.requestWindow()")}} را برای باز کردن یک پنجرهٔ خالی Picture-in-Picture فراخوانی می‌کند. {{jsxref("Promise")}} بازگشتی با یک شیء {{domxref("Window")}} از نوع Picture-in-Picture تکمیل می‌شود. پخش‌کنندهٔ ویدیو با استفاده از {{domxref("Element.append()")}} به آن پنجره منتقل می‌شود و پیامی نمایش می‌دهیم که به کاربر اطلاع می‌دهد جابه‌جایی انجام شده است.

گزینه‌های `width` و `height` در `requestWindow()` اندازهٔ پنجرهٔ Picture-in-Picture را به مقدار دلخواه تنظیم می‌کنند. مرورگرها ممکن است این مقادیر را اگر برای اندازهٔ پنجرهٔ کاربرپسند خیلی بزرگ یا خیلی کوچک باشند، محدود (clamp) کنند.

```js
async function togglePictureInPicture() {
  // Early return if there's already a Picture-in-Picture window open
  if (window.documentPictureInPicture.window) {
    return;
  }

  // Open a Picture-in-Picture window.
  const pipWindow = await window.documentPictureInPicture.requestWindow({
    width: videoPlayer.clientWidth,
    height: videoPlayer.clientHeight,
  });

  // …

  // Move the player to the Picture-in-Picture window.
  pipWindow.document.body.append(videoPlayer);

  // Display a message to say it has been moved
  inPipMessage.style.display = "block";
}
```

## کپی کردن style sheet ها به پنجرهٔ Picture-in-Picture

برای کپی کردن همهٔ style sheet های CSS از پنجرهٔ مبدأ، در تمام style sheetهایی که به‌صورت پیوندی یا تعبیه‌شده در سند وجود دارند (از طریق {{domxref("Document.styleSheets")}}) پیمایش کنید و آن‌ها را به پنجرهٔ Picture-in-Picture اضافه کنید. توجه داشته باشید که این یک کپی یک‌باره است.

```js
// …

// Copy style sheets over from the initial document
// so that the player looks the same.
[...document.styleSheets].forEach((styleSheet) => {
  try {
    const cssRules = [...styleSheet.cssRules]
      .map((rule) => rule.cssText)
      .join("");
    const style = document.createElement("style");

    style.textContent = cssRules;
    pipWindow.document.head.appendChild(style);
  } catch (e) {
    const link = document.createElement("link");

    link.rel = "stylesheet";
    link.type = styleSheet.type;
    link.media = styleSheet.media;
    link.href = styleSheet.href;
    pipWindow.document.head.appendChild(link);
  }
});

// …
```

## هدف قرار دادن استایل‌ها در حالت Picture-in-Picture

مقدار `picture-in-picture` از [media feature](/en-US/docs/Web/CSS/Reference/At-rules/@media#media_features) مربوط به {{cssxref("@media/display-mode", "display-mode")}} به توسعه‌دهندگان اجازه می‌دهد CSS را بر اساس نمایش یا عدم نمایش سند در حالت Picture-in-Picture روی آن اعمال کنند. کاربرد اولیه به این شکل است:

```css
@media (display-mode: picture-in-picture) {
  body {
    background: red;
  }
}
```

این قطعه، پس‌زمینهٔ `<body>` سند را فقط زمانی که در حالت Picture-in-Picture نمایش داده می‌شود قرمز می‌کند.

در [نسخهٔ نمایشی ما](https://mdn.github.io/dom-examples/document-picture-in-picture/)، مقدار `display-mode: picture-in-picture` را با media feature مربوط به {{cssxref("@media/prefers-color-scheme", "prefers-color-scheme")}} ترکیب می‌کنیم تا طرح‌های رنگی روشن و تیره ایجاد کنیم که بر اساس اولویت طرح رنگی کاربر، فقط زمانی که برنامه در حالت Picture-in-Picture نمایش داده می‌شود اعمال می‌شوند.

```css
@media (display-mode: picture-in-picture) and (prefers-color-scheme: light) {
  body {
    background: antiquewhite;
  }
}

@media (display-mode: picture-in-picture) and (prefers-color-scheme: dark) {
  body {
    background: #333333;
  }

  a {
    color: antiquewhite;
  }
}
```

## مدیریت بسته‌شدن پنجرهٔ Picture-in-Picture

کدی که با فشار دوبارهٔ دکمه، پنجرهٔ Picture-in-Picture را دوباره می‌بندد به این شکل است:

```js
inPipMessage.style.display = "none";
playerContainer.append(videoPlayer);
window.documentPictureInPicture.window.close();
```

در اینجا تغییرات DOM را معکوس می‌کنیم — پیام را پنهان می‌کنیم و پخش‌کنندهٔ ویدیو را به ظرف پخش‌کننده در پنجرهٔ اصلی برنامه برمی‌گردانیم. همچنین پنجرهٔ Picture-in-Picture را به‌صورت برنامه‌ای (programmatically) با استفاده از متد {{domxref("Window.close()")}} می‌بندیم.

با این حال، باید حالتی را نیز در نظر بگیرید که کاربر با فشردن کنترل بستنِ عرضه‌شده توسط مرورگر روی خود پنجره، پنجرهٔ Picture-in-Picture را می‌بندد. می‌توانید این حالت را با شناسایی زمان بسته‌شدن پنجره از طریق رویداد [`pagehide`](/en-US/docs/Web/API/Window/pagehide_event) مدیریت کنید:

```js
pipWindow.addEventListener("pagehide", (event) => {
  inPipMessage.style.display = "none";
  playerContainer.append(videoPlayer);
});
```

> [!NOTE]
> می‌توانید کنترل بستنِ عرضه‌شده توسط مرورگر را با قرار دادن مقدار `true` برای ویژگی [`disallowReturnToOpener`](/en-US/docs/Web/API/DocumentPictureInPicture/requestWindow#disallowreturntoopener) در شیء options هنگام فراخوانی `DocumentPictureInPicture.requestWindow()` برای باز کردن پنجرهٔ Picture-in-Picture پنهان کنید.

## گوش دادن به ورود وب‌سایت به حالت Picture-in-Picture

برای دانستن اینکه چه زمانی یک پنجرهٔ Picture-in-Picture باز شده است، به رویداد {{domxref("DocumentPictureInPicture.enter_event", "enter")}} روی نمونهٔ `DocumentPictureInPicture` گوش دهید.

در نسخهٔ نمایشی ما، از رویداد `enter` برای افزودن دکمهٔ تغییر وضعیت صدا (mute) به پنجرهٔ Picture-in-Picture استفاده می‌کنیم:

```js
documentPictureInPicture.addEventListener("enter", (event) => {
  const pipWindow = event.window;
  console.log("Video player has entered the pip window");

  const pipMuteButton = pipWindow.document.createElement("button");
  pipMuteButton.textContent = "Mute";
  pipMuteButton.addEventListener("click", () => {
    const pipVideo = pipWindow.document.querySelector("#video");
    if (!pipVideo.muted) {
      pipVideo.muted = true;
      pipMuteButton.textContent = "Unmute";
    } else {
      pipVideo.muted = false;
      pipMuteButton.textContent = "Mute";
    }
  });

  pipWindow.document.body.append(pipMuteButton);
});
```

> [!NOTE]
> شیء رویداد {{domxref("DocumentPictureInPictureEvent")}} دارای ویژگی `window` برای دسترسی به پنجرهٔ Picture-in-Picture است.

## دسترسی به عناصر و مدیریت رویدادها

می‌توانید به عناصر موجود در پنجرهٔ Picture-in-Picture به چند روش مختلف دسترسی داشته باشید:

- نمونهٔ {{domxref("Window")}} که توسط متد {{domxref("DocumentPictureInPicture.requestWindow()")}} بازگردانده می‌شود، همان‌طور که در بالا دیدید.
- از طریق ویژگی `window` در شیء رویداد {{domxref("DocumentPictureInPictureEvent")}} (در رویداد {{domxref("DocumentPictureInPicture.enter_event", "enter")}})، همان‌طور که در بالا دیدید.
- از طریق ویژگی {{domxref("DocumentPictureInPicture.window")}}:

```js
const pipWindow = window.documentPictureInPicture.window;
if (pipWindow) {
  // Mute video playing in the Picture-in-Picture window.
  const pipVideo = pipWindow.document.querySelector("#video");
  pipVideo.muted = true;
}
```

هنگامی که ارجاعی به نمونهٔ `window` مربوط به Picture-in-Picture دارید، می‌توانید DOM را دستکاری کنید (مثلاً دکمه بسازید) و به رویدادهای ورودی کاربر (مانند [`click`](/en-US/docs/Web/API/Element/click_event)) پاسخ دهید، دقیقاً مانند کاری که به‌طور عادی در بافت پنجرهٔ معمولی مرورگر انجام می‌دهید.