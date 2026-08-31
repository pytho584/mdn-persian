---
title: "BackgroundFetchEvent"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BackgroundFetchEvent"
translated_by: "n8n + AI"
---

---
title: BackgroundFetchEvent
slug: Web/API/BackgroundFetchEvent
page-type: web-api-interface
status:
  - experimental
browser-compat: api.BackgroundFetchEvent
---

{{APIRef("Background Fetch API")}}{{SeeCompatTable}}{{AvailableInWorkers("service")}}

**`BackgroundFetchEvent`** 接口屬於 {{domxref('Background Fetch API', "", "", "nocode")}}，是分派在 {{domxref("ServiceWorkerGlobalScope", "service worker 全域範圍", "", "nocode")}} 上的背景擷取事件的型別。

它是傳遞給 {{domxref("ServiceWorkerGlobalScope/backgroundfetchclick_event", "backgroundfetchclick")}} 事件和 {{domxref("ServiceWorkerGlobalScope/backgroundfetchabort_event", "backgroundfetchabort")}} 事件的事件型別。

{{InheritanceDiagram}}

## 建構子

- {{domxref("BackgroundFetchEvent.BackgroundFetchEvent()", "BackgroundFetchEvent()")}} {{Experimental_Inline}}
  - : 建立一個新的 `BackgroundFetchEvent` 物件。此建構子通常不會被使用，因為瀏覽器會自行建立這些物件，並將它們提供給背景擷取事件的回呼函式。

## 實體屬性

_也繼承自其父類別 {{domxref("ExtendableEvent")}} 的屬性。_

- {{domxref("BackgroundFetchEvent.registration")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : 回傳初始化事件時所使用的 {{domxref("BackgroundFetchRegistration")}}。

## 實體方法

_也繼承自其父類別 {{domxref("ExtendableEvent")}} 的方法。_

無。

## 範例

在此範例中，如果使用者按一下顯示下載進度的使用者介面，將開啟一個新視窗。目前的 {{domxref("BackgroundFetchRegistration")}} 透過呼叫 `event.registration` 來取得。

```js
addEventListener("backgroundfetchclick", (event) => {
  const bgFetch = event.registration;

  if (bgFetch.result === "success") {
    clients.openWindow("/latest-podcasts");
  } else {
    clients.openWindow("/download-progress");
  }
});
```

## 規格

{{Specifications}}

## 瀏覽器相容性

{{Compat}}