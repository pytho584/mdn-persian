---
title: "MediaStream: getAudioTracks() method"
short-title: getAudioTracks()
slug: Web/API/MediaStream/getAudioTracks
page-type: web-api-instance-method
browser-compat: api.MediaStream.getAudioTracks
---

{{APIRef("Media Capture and Streams")}}

**`getAudioTracks()`** メソッドは、{{domxref("MediaStream")}} インターフェイスのメソッドで、このストリームの[トラックセット](https://w3c.github.io/mediacapture-main/#dfn-track-set)内にある {{domxref("MediaStreamTrack")}} オブジェクトのうち、{{domxref("MediaStreamTrack.kind")}} が `audio` であるものをすべて表す配列を返します。

## 構文

```js-nolint
getAudioTracks()
```

### 引数

なし。

### 戻り値

{{domxref("MediaStreamTrack")}} オブジェクトの配列で、ストリームに含まれる音声トラックごとに 1 つずつ格納されます。音声トラックとは、{{domxref("MediaStreamTrack.kind", "kind")}} プロパティが `audio` であるトラックです。ストリームに音声トラックが含まれない場合、配列は空です。

> [!NOTE]
> 返されるトラックの順序は仕様で定義されておらず、`getAudioTracks()` を呼び出すたびに変わる可能性があります。

この API の初期のバージョンでは、音声ストリームのリストの各エントリの型として特別な `AudioStreamTrack` インターフェイスが使われていましたが、その後、これはメインの {{domxref("MediaStreamTrack")}} インターフェイスに統合されました。

## 例

この例では、{{domxref("MediaDevices.getUserMedia", "getUserMedia()")}} を使ってウェブカメラの音声と映像をストリームで取得し、そのストリームを {{HTMLElement("video")}} 要素に割り当ててから、タイマーを設定し、期限が切れるとストリーム内で見つかった最初の音声トラックを停止します。

```js
navigator.mediaDevices
  .getUserMedia({ audio: true, video: true })
  .then((mediaStream) => {
    document.querySelector("video").srcObject = mediaStream;
    // 5 秒後に音声ストリームを停止
    setTimeout(() => {
      const tracks = mediaStream.getAudioTracks();
      tracks[0].stop();
    }, 5000);
  });
```

## 仕様書

{{Specifications}}

## ブラウザー互換性

{{Compat}}