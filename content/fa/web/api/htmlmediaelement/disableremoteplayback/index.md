---
title: "HTMLMediaElement: disableRemotePlayback property"
---

---
title: "HTMLMediaElement: disableRemotePlayback property"
short-title: disableRemotePlayback
slug: Web/API/HTMLMediaElement/disableRemotePlayback
page-type: web-api-instance-property
browser-compat: api.HTMLMediaElement.disableRemotePlayback
---

{{APIRef("Remote Playback API")}}

ویژگی **`disableRemotePlayback`** در رابط {{domxref("HTMLMediaElement")}} تعیین میکند که آیا عنصر رسانه مجاز به داشتن رابط پخش از راه دور است یا خیر.

## Value

یک مقدار بولی که نشان میدهد آیا عنصر رسانه میتواند رابط پخش از راه دور داشته باشد یا خیر. (`false` یعنی «غیرفعال نیست» که به معنای «فعال» است).

## Example

```js
const obj = document.createElement("audio");
obj.disableRemotePlayback = true;
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [ویژگی `disableremoteplayback` در عنصر `<audio>`](/en-US/docs/Web/HTML/Reference/Elements/audio#disableremoteplayback)
- [ویژگی `disableremoteplayback` در عنصر `<video>`](/en-US/docs/Web/HTML/Reference/Elements/video#disableremoteplayback)