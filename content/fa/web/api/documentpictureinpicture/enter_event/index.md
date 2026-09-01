---
title: "DocumentPictureInPicture: enter event"
---

---
title: "DocumentPictureInPicture: enter event"
short-title: enter
slug: Web/API/DocumentPictureInPicture/enter_event
page-type: web-api-event
browser-compat: api.DocumentPictureInPicture.enter_event
---

{{APIRef("Document Picture-in-Picture API")}}{{SecureContext_Header}}

رویداد **`enter`** از رابط {{domxref("DocumentPictureInPicture")}} هنگامی فعال می‌شود که پنجرهٔ تصویر‑در‑تصویر با موفقیت باز شود.

## نحو

برای دریافت این رویداد می‌توانید از نام رویداد در متدهایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک خاصیت مدیریت رویداد تنظیم کنید.

```js-nolint
addEventListener("enter", (event) => { })

onenter = (event) => { }
```

## نوع رویداد

یک {{domxref("DocumentPictureInPictureEvent")}}.

## مثال‌ها

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

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Document Picture-in-Picture API", "Document Picture-in-Picture API", "", "nocode")}}
- [استفاده از API تصویر‑در‑تصویر سند](/en-US/docs/Web/API/Document_Picture-in-Picture_API/Using)