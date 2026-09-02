---
title: "MediaStreamTrack: clone() method"
short-title: clone()
slug: Web/API/MediaStreamTrack/clone
page-type: web-api-instance-method
browser-compat: api.MediaStreamTrack.clone
---

{{APIRef("Media Capture and Streams")}}

**`clone()`** メソッドは {{domxref("MediaStreamTrack")}} インターフェイスのメソッドで、この `MediaStreamTrack` の複製を作成します。この新しい `MediaStreamTrack` オブジェクトは、固有の {{domxref("MediaStreamTrack.id", "id")}} を除いて元のトラックと同一です。

## 構文

```js-nolint
clone()
```

### 引数

なし。

### 戻り値

`clone()` が呼び出された元のトラックと同一の新しい {{domxref("MediaStreamTrack")}} インスタンスですが、新しい固有の {{domxref("MediaStreamTrack.id", "id")}} を持ちます。

## 仕様書

{{Specifications}}

## ブラウザー互換性

{{Compat}}