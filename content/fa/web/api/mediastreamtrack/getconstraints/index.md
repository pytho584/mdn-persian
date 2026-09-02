---
title: "MediaStreamTrack: getConstraints() method"
short-title: getConstraints()
slug: Web/API/MediaStreamTrack/getConstraints
page-type: web-api-instance-method
browser-compat: api.MediaStreamTrack.getConstraints
---

{{APIRef("Media Capture and Streams")}}

**`getConstraints()`** 方法屬於 {{domxref("MediaStreamTrack")}} 介面，會回傳一個 {{domxref('MediaTrackConstraints')}} 物件，其中包含先前透過呼叫 {{domxref("MediaStreamTrack.applyConstraints", "applyConstraints()")}} 為該軌道設定的最新限制。這些限制表示網站或應用程式已指定的、對所包含的可限制屬性而言為必要或可接受的值與值範圍。

限制可用於確保媒體符合您偏好的某些準則。例如，您可能偏好高畫質影片，但要求影格率略低，以幫助將資料速率保持在不會過度負荷網路的範圍內。限制也可以指定理想及/或可接受的大小或大小範圍。如需如何操作可限制屬性的詳細資訊，請參閱[能力、限制與設定](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints)。

## 語法

```js-nolint
getConstraints()
```

### 參數

無。

### 回傳值

一個 {{domxref('MediaTrackConstraints')}} 物件，表示網站或應用程式最近透過 {{domxref("MediaStreamTrack.applyConstraints", "applyConstraints()")}} 設定的可限制屬性。回傳物件中的屬性依設定時的順序列出，且僅包含網站或應用程式明確設定的屬性。

> [!NOTE]
> 回傳的限制集合不一定描述媒體的實際狀態。即使其中某些限制無法滿足，它們仍會以網站程式碼原本設定的形式包含在回傳物件中。若要取得所有可限制屬性的目前使用中設定，您應該改為呼叫 {{domxref("MediaStreamTrack.getSettings", "getSettings()")}}。

## 範例

此範例取得軌道的目前限制，設定 {{domxref("MediaTrackConstraints.facingMode", "facingMode")}}，然後套用更新後的限制。

```js
function switchCameras(track, camera) {
  const constraints = track.getConstraints();
  constraints.facingMode = camera;
  track.applyConstraints(constraints);
}
```

## 規格

{{Specifications}}

## 瀏覽器相容性

{{Compat}}