---
title: "DocumentPictureInPictureEvent: window property"
short-title: window
slug: Web/API/DocumentPictureInPictureEvent/window
page-type: web-api-instance-property
browser-compat: api.DocumentPictureInPictureEvent.window
---

{{APIRef("Document Picture-in-Picture API")}}{{SecureContext_Header}}

ویژگی فقط‌خواندنی **`window`** در رابط {{domxref("DocumentPictureInPictureEvent")}} یک نمونه از {{domxref("Window")}} را برمی‌گرداند که بافت مرور (browsing context) داخل پنجره `DocumentPictureInPicture` را نشان می‌دهد؛ همان پنجره‌ای که رویداد روی آن رخ داده است.

## مقدار

یک نمونه از شیء {{domxref("Window")}}.

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
- [استفاده از Document Picture-in-Picture API](/en-US/docs/Web/API/Document_Picture-in-Picture_API/Using)