---
title: "BatteryManager"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BatteryManager"
translated_by: "n8n + AI"
---

---
title: BatteryManager
slug: Web/API/BatteryManager
page-type: web-api-interface
browser-compat: api.BatteryManager
---

{{ApiRef("Battery API")}}{{securecontext_header}}

**`BatteryManager`** 接口（属于 {{domxref("Battery Status API", "", "", "nocode")}}）提供关于系统电池电量级别的信息。{{domxref("navigator.getBattery()")}} 方法返回一个 promise，该 promise 解析为一个 `BatteryManager` 接口。

自 Chrome 103 起，{{domxref("Battery Status API", "", "", "nocode")}} 的 `BatteryManager` 接口仅暴露给安全上下文。

{{InheritanceDiagram}}

## 实例属性

_还从父接口 {{domxref("EventTarget")}} 继承属性。_

- {{domxref("BatteryManager.charging")}} {{ReadOnlyInline}}
  - : 一个布尔值，指示电池当前是否正在充电。
- {{domxref("BatteryManager.chargingTime")}} {{ReadOnlyInline}}
  - : 一个数字，表示距离电池充满电还需要的时间（以秒为单位），如果电池已充满电则为 0。
- {{domxref("BatteryManager.dischargingTime")}} {{ReadOnlyInline}}
  - : 一个数字，表示距离电池完全放电且系统挂起之前剩余的时间（以秒为单位）。
- {{domxref("BatteryManager.level")}} {{ReadOnlyInline}}
  - : 一个数字，表示系统电池电量级别，范围在 0.0 到 1.0 之间。

## 实例方法

_还从父接口 {{domxref("EventTarget")}} 继承方法。_

## 事件

_还从父接口 {{domxref("EventTarget")}} 继承事件。_

- {{domxref("BatteryManager/chargingchange_event", "chargingchange")}}
  - : 当电池充电状态（{{domxref("BatteryManager.charging", "charging")}} 属性）更新时触发。
- {{domxref("BatteryManager/chargingtimechange_event", "chargingtimechange")}}
  - : 当电池充电时间（{{domxref("BatteryManager.chargingTime", "chargingTime")}} 属性）更新时触发。
- {{domxref("BatteryManager/dischargingtimechange_event", "dischargingtimechange")}}
  - : 当电池放电时间（{{domxref("BatteryManager.dischargingTime", "dischargingTime")}} 属性）更新时触发。
- {{domxref("BatteryManager/levelchange_event", "levelchange")}}
  - : 当电池电量级别（{{domxref("BatteryManager.level", "level")}} 属性）更新时触发。

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- {{domxref("Battery Status API", "", "", "nocode")}}
- {{domxref("Navigator.getBattery()")}}