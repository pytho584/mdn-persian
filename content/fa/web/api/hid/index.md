---
title: "HID"
---

---
title: HID
slug: Web/API/HID
page-type: web-api-interface
status:
  - experimental
browser-compat: api.HID
---

{{securecontext_header}}{{APIRef("WebHID API")}}{{SeeCompatTable}}{{AvailableInWorkers("window_and_worker_except_shared")}}

**`HID`** 接口提供了用于连接 _HID 设备_、列出已连接的 HID 设备以及处理已连接 HID 设备的事件处理器的方法。

{{InheritanceDiagram}}

## 实例属性

_此接口还继承其父接口 {{domxref("EventTarget")}} 的属性。_

## 实例方法

_此接口还继承其父接口 {{domxref("EventTarget")}} 的方法。_

- {{domxref("HID.getDevices","getDevices()")}} {{Experimental_Inline}}
  - : 返回一个 {{jsxref("Promise")}}，它会解析为一个数组，包含用户先前在响应 {{domxref("HID.requestDevice","requestDevice()")}} 调用时被授予访问权限的已连接 HID 设备。
- {{domxref("HID.requestDevice","requestDevice()")}} {{Experimental_Inline}}
  - : 返回一个 {{jsxref("Promise")}}，它会解析为一个包含已连接 {{domxref("HIDDevice")}} 对象的数组。调用此函数将触发用户代理的权限流程，以便获得访问返回设备列表中所选一个设备的权限。

### 事件

- {{domxref("HID.connect_event", "connect")}} {{Experimental_Inline}}
  - : 当 HID 设备连接时触发。
- {{domxref("HID.disconnect_event", "disconnect")}} {{Experimental_Inline}}
  - : 当 HID 设备断开连接时触发。

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- [WebHID API](/en-US/docs/Web/API/WebHID_API)