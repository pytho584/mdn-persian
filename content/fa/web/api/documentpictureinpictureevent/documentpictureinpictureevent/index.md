---
title: "DocumentPictureInPictureEvent: DocumentPictureInPictureEvent() constructor"
short-title: DocumentPictureInPictureEvent()
slug: Web/API/DocumentPictureInPictureEvent/DocumentPictureInPictureEvent
page-type: web-api-constructor
browser-compat: api.DocumentPictureInPictureEvent.DocumentPictureInPictureEvent
---

{{APIRef("Document Picture-in-Picture API")}}{{SecureContext_Header}}

سازنده‌ی **`DocumentPictureInPictureEvent()`** یک نمونه‌ی جدید از شیء {{domxref("DocumentPictureInPictureEvent")}} ایجاد می‌کند.

## نحو (Syntax)

```js-nolint
new DocumentPictureInPictureEvent(type, init)
```

### پارامترها

- `type`
  - : یک رشته (string) که نشان‌دهنده‌ی نوع رویداد است. در مورد `DocumentPictureInPictureEvent` این همیشه `enter` است.
- `init`
  - : یک شیء شامل ویژگی‌های زیر:
    - `window`
      - : یک نمونه از {{domxref("Window")}} که نمایانگر زمینه‌ی مرور (browsing context) درون پنجره‌ی `DocumentPictureInPicture` است که رویداد روی آن فعال شده است.

## مثال‌ها

توسعه‌دهنده معمولاً از این سازنده به صورت دستی استفاده نمی‌کند. یک شیء جدید `DocumentPictureInPictureEvent` زمانی ساخته می‌شود که یک handler در نتیجه‌ی فعال شدن رویداد {{domxref("DocumentPictureInPicture.enter_event", "enter")}} فراخوانی شود.

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

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Document Picture-in-Picture API", "Document Picture-in-Picture API", "", "nocode")}}
- [استفاده از Document Picture-in-Picture API](/en-US/docs/Web/API/Document_Picture-in-Picture_API/Using)