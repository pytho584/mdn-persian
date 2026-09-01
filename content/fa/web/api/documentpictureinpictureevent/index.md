---
title: "DocumentPictureInPictureEvent"
---

---
title: DocumentPictureInPictureEvent
slug: Web/API/DocumentPictureInPictureEvent
page-type: web-api-interface
browser-compat: api.DocumentPictureInPictureEvent
---

{{APIRef("Document Picture-in-Picture API")}}{{SecureContext_Header}}

رابطِ **`DocumentPictureInPictureEvent`** از {{domxref("Document Picture-in-Picture API", "Document Picture-in-Picture API", "", "nocode")}}، شیء رویداد برای رویداد {{domxref("DocumentPictureInPicture/enter_event", "enter")}} است که هنگام باز شدن پنجرهٔ تصویر-در-تصویر فعال می‌شود.

{{InheritanceDiagram}}

## سازنده

- {{domxref("DocumentPictureInPictureEvent.DocumentPictureInPictureEvent", "DocumentPictureInPictureEvent()")}}
  - : یک نمونهٔ جدید از شیء `DocumentPictureInPictureEvent` ایجاد می‌کند.

## ویژگی‌های نمونه

_ویژگی‌ها را از والد خود، {{DOMxRef("Event")}}، به ارث می‌برد._

- {{domxref("DocumentPictureInPictureEvent.window", "window")}} {{ReadOnlyInline}}
  - : یک نمونه از {{domxref("Window")}} را برمی‌گرداند که بافتار مرور داخل پنجرهٔ `DocumentPictureInPicture` را که رویداد روی آن فعال شده است، نشان می‌دهد.

## متدهای نمونه

_متدها را از والد خود، {{DOMxRef("Event")}}، به ارث می‌برد._

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
- [استفاده از API Document Picture-in-Picture](/en-US/docs/Web/API/Document_Picture-in-Picture_API/Using)