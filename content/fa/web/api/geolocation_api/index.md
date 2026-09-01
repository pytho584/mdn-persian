---
title: Geolocation API
slug: Web/API/Geolocation_API
page-type: web-api-overview
browser-compat: api.Geolocation
---

{{securecontext_header}}{{DefaultAPISidebar("Geolocation API")}}

**Geolocation API** 允许用户自愿将他们的位置信息提供给网络应用。出于隐私原因，在报告位置信息时，应用需要征求用户的许可。

希望使用 `Geolocation` 对象的 WebExtensions 必须在其 manifest 中添加 `"geolocation"` 权限。用户的操作系统将在首次请求时提示用户允许位置访问。

> [!NOTE]
> {{htmlelement("geolocation")}} 元素提供了一种访问和处理地理位置数据的替代机制，解决了 Geolocation API 的一些缺点：它提供了一致的用户界面，以及更直观的权限管理流程。

## 概念与用法

在您的 Web 应用中，您经常需要获取用户的位置信息，例如在地图上标记其位置，或显示与其位置相关的个性化信息。

通过调用 {{domxref("Navigator.geolocation", "navigator.geolocation")}} 即可访问 Geolocation API；这将导致用户浏览器询问他们是否允许访问其位置数据。如果他们同意，浏览器将使用设备上可用的最佳功能（例如 GPS）来访问此信息。

开发者现在可以通过以下几种方式来访问此位置信息：

- {{domxref("Geolocation.getCurrentPosition()")}}：获取设备的当前位置。
- {{domxref("Geolocation.watchPosition()")}}：注册一个处理函数，该函数将在设备位置每次变化时自动调用，并返回更新的位置。

在两种情况下，方法调用最多接受三个参数：

- 必需的 success 回调：如果位置检索成功，则该回调执行，其唯一参数是一个 {{domxref("GeolocationPosition")}} 对象，用于提供对位置数据的访问。
- 可选的 error 回调：如果位置检索失败，则该回调执行，其唯一参数是一个 {{domxref("GeolocationPositionError")}} 对象，用于提供关于出错原因的信息。
- 一个可选的对象，用于提供位置数据检索的选项。

有关 Geolocation 使用的更多信息，请参阅[使用 Geolocation API](/en-US/docs/Web/API/Geolocation_API/Using_the_Geolocation_API)。

## 接口

- {{domxref("Geolocation")}}
  - : 该 API 的主类——包含用于获取用户当前位置、监视位置变化以及清除先前设置的监视的方法。
- {{domxref("GeolocationPosition")}}
  - : 表示用户的位置。成功调用 {{domxref("Geolocation")}} 中的某个方法后，在 success 回调中会返回一个 `GeolocationPosition` 实例，其中包含一个时间戳和一个 {{domxref("GeolocationCoordinates")}} 对象实例。
- {{domxref("GeolocationCoordinates")}}
  - : 表示用户位置的坐标；`GeolocationCoordinates` 实例包含纬度、经度以及其他重要的相关信息。
- {{domxref("GeolocationPositionError")}}
  - : 当对 {{domxref("Geolocation")}} 中的某个方法进行不成功的调用时，会在 error 回调中返回一个 `GeolocationPositionError`，其中包含错误代码和错误消息。

### 对其他接口的扩展

- {{domxref("Navigator.geolocation")}}
  - : API 的入口点。返回一个 {{domxref("Geolocation")}} 对象实例，通过它能够访问所有其他功能。

## 安全注意事项

Geolocation API 允许用户在[安全上下文](/en-US/docs/Web/Security/Defenses/Secure_Contexts)中以编程方式访问位置信息。

进一步的访问控制可由[权限策略](/en-US/docs/Web/HTTP/Guides/Permissions_Policy)指令 {{HTTPHeader("Permissions-Policy/geolocation","geolocation")}} 进行。默认情况下，`geolocation` 的允许列表为 `self`，意味着仅允许同源嵌套框架访问位置信息。若要允许第三方使用，可以通过设置 `Permissions-Policy` 响应头来授予特定第三方来源权限：

```http
Permissions-Policy: geolocation=(self b.example.com)
```

随后需要在 iframe 元素上添加 `allow="geolocation"` 属性，且其来源需为该第三方来源：

```html
<iframe src="https://b.example.com" allow="geolocation"></iframe>
```

地理位置数据可能会泄露设备所有者不愿分享的信息。因此，在调用 {{domxref("Geolocation.getCurrentPosition()")}} 或 {{domxref("Geolocation.watchPosition()")}} 时，必须通过提示获得用户的明确许可（除非权限状态已经是 `granted` 或 `denied`）。已授予权限的生命周期取决于用户代理，可能基于时间、会话，甚至可能是永久的。可以使用[权限 API](/en-US/docs/Web/API/Permissions_API) 的 `geolocation` 权限来测试位置信息的访问权限是 `granted`、`denied` 还是 `prompt`（需要用户确认提示）。

## 示例

示例代码请参阅[使用 Geolocation API](/en-US/docs/Web/API/Geolocation_API/Using_the_Geolocation_API#examples)。

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

### 可用性

由于基于 Wi-Fi 的定位通常由 Google 提供，默认的 Geolocation API 在中国可能不可用。您可以使用本地第三方服务提供商，例如[百度](https://lbsyun.baidu.com/index.php?title=jspopular/guide/geolocation)、[高德](https://lbs.amap.com/api/javascript-api/guide/services/geolocation#geolocation)或[腾讯](https://lbs.qq.com/service/webService/webServiceGuide/position/webServiceIp)。这些服务使用用户的 IP 地址和/或本地应用来提供增强定位。

## 参见

- {{htmlelement("geolocation")}} 元素
- [使用 Geolocation API](/en-US/docs/Web/API/Geolocation_API/Using_the_Geolocation_API)
- [谁移动了我的地理位置？](https://hacks.mozilla.org/2013/10/who-moved-my-geolocation/)（Hacks 博客）