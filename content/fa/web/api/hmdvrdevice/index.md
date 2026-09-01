---
title: HMDVRDevice
slug: Web/API/HMDVRDevice
page-type: web-api-interface
status:
  - deprecated
  - non-standard
browser-compat: api.HMDVRDevice
---

{{APIRef("WebVR API")}}{{Deprecated_Header}}{{Non-standard_Header}}

**`HMDVRDevice`** 接口屬於 [WebVR API](/en-US/docs/Web/API/WebVR_API)，代表頭戴式顯示器，提供有關每隻眼睛的資訊，並允許我們修改目前的視野。

## 實體方法

- {{domxref("HMDVRDevice.getEyeParameters()")}} {{Deprecated_Inline}} {{Non-standard_Inline}}
  - : 傳回指定眼睛（「left」或「right」）的目前參數——例如視野資訊——儲存在 {{domxref("VREyeParameters")}} 物件中。
- {{domxref("HMDVRDevice.setFieldOfView()")}} {{Deprecated_Inline}} {{Non-standard_Inline}}
  - : 設定雙眼的視野。

## 實體屬性

_此介面本身沒有定義任何屬性，但會繼承其父介面 {{domxref("VRDisplay")}} 的屬性。_

- `VRDisplay.hardwareUnitId` {{ReadOnlyInline}}
  - : 傳回此 `VRDevice` 所屬整體硬體單元的唯一硬體 ID。屬於同一實體硬體的所有裝置都會具有相同的 `hardwareUnitId`。
- {{domxref("VRDisplay.displayId")}} {{ReadOnlyInline}}
  - : 傳回此特定 `VRDevice` 的 ID。此 ID 不應在瀏覽器重新啟動後變更，以便可根據它儲存組態資料。
- {{domxref("VRDisplay.displayName")}} {{ReadOnlyInline}}
  - : 可讀的人類可讀名稱，用於識別 `VRDevice`。

## 範例

以下範例取自 WebVR 規範，會找出第一個可用的 `HMDVRDevice` 及其關聯的 {{domxref("PositionSensorVRDevice")}}（如果有的話）。

```js
navigator.getVRDevices().then((devices) => {
  for (const device of devices) {
    if (device instanceof HMDVRDevice) {
      gHMD = device;
      break;
    }
  }

  if (gHMD) {
    for (const device of devices) {
      if (
        device instanceof PositionSensorVRDevice &&
        device.hardwareUnitId === gHMD.hardwareUnitId
      ) {
        gPositionSensor = devices[i];
        break;
      }
    }
  }
});
```

## 瀏覽器相容性

{{Compat}}

## 參見

- [WebVR API](/en-US/docs/Web/API/WebVR_API)