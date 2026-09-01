---
title: "HTMLGeolocationElement"
---

---
title: HTMLGeolocationElement
slug: Web/API/HTMLGeolocationElement
page-type: web-api-interface
status:
  - experimental
browser-compat: api.HTMLGeolocationElement
---

{{APIRef("HTML DOM")}}{{SeeCompatTable}}

**`HTMLGeolocationElement`** 接口属于 [HTML DOM API](/en-US/docs/Web/API/HTML_DOM_API)，表示 {{htmlelement("geolocation")}} 元素，并提供对其属性和事件的访问。

该元素基于 {{domxref("HTMLElement")}} 接口，并继承其属性和方法。

> [!NOTE]
> `<geolocation>` 元素和 `HTMLGeolocationElement` 接口允许用户以比旧的 [Geolocation API](/en-US/docs/Web/API/Geolocation_API) 更一致、更直观的方式与页面共享其位置数据。

{{InheritanceDiagram}}

## 构造函数

- {{domxref("HTMLGeolocationElement.HTMLGeolocationElement", "HTMLGeolocationElement()")}} {{experimental_inline}}
  - : 创建一个新的 `HTMLGeolocationElement` 对象实例。注意，此构造函数不会直接调用，而是通过诸如 {{domxref("Document.createElement()")}} 之类的 DOM 方法调用。

## 实例属性

_同时继承其父接口 {{domxref("HTMLElement")}} 的属性。_

- {{domxref("HTMLGeolocationElement.autolocate", "autolocate")}} {{experimental_inline}}
  - : 一个布尔值，指示当 `<geolocation>` 元素渲染后，浏览器是否应在先前已授予权限的情况下立即请求位置数据。反映 `<geolocation>` 的 [`autolocate`](/en-US/docs/Web/HTML/Reference/Elements/geolocation#autolocate) 属性。
- {{domxref("HTMLGeolocationElement.error", "error")}} {{readonlyinline}} {{experimental_inline}}
  - : 一个 {{domxref("GeolocationPositionError")}} 对象，在检索数据失败时表示错误信息。
- {{domxref("HTMLGeolocationElement.initialPermissionStatus", "initialPermissionStatus")}} {{readonlyinline}} {{experimental_inline}}
  - : 一个枚举值，表示页面首次加载时 `geolocation` 功能的权限状态。
- {{domxref("HTMLGeolocationElement.invalidReason", "invalidReason")}} {{readonlyinline}} {{experimental_inline}}
  - : 一个枚举值，表示 `<geolocation>` 元素无效（[被阻止](/en-US/docs/Web/HTML/Reference/Elements/geolocation#geolocation_blocking)）的原因（如果确实如此）。
- {{domxref("HTMLGeolocationElement.isValid", "isValid")}} {{readonlyinline}} {{experimental_inline}}
  - : 一个布尔值，指示 `<geolocation>` 元素是有效还是无效（被阻止）。
- {{domxref("HTMLGeolocationElement.permissionStatus", "permissionStatus")}} {{readonlyinline}} {{experimental_inline}}
  - : 一个字符串，表示 `geolocation` 功能的当前权限状态。
- {{domxref("HTMLGeolocationElement.position", "position")}} {{readonlyinline}} {{experimental_inline}}
  - : 一个 {{domxref("GeolocationPosition")}} 对象，在成功检索位置数据时表示用户的位置。
- {{domxref("HTMLGeolocationElement.watch", "watch")}} {{experimental_inline}}
  - : 一个布尔值，指示浏览器是否应在设备位置变化时持续更新用户的位置数据，还是只检索一次。反映 `<geolocation>` 的 [`watch`](/en-US/docs/Web/HTML/Reference/Elements/geolocation#watch) 属性。

## 实例方法

_继承其父接口 {{domxref("HTMLElement")}} 的方法。_

## 事件

_同时继承其父接口 {{domxref("HTMLElement")}} 的事件。_

- {{domxref("HTMLGeolocationElement.location_event", "location")}} {{experimental_inline}}
  - : 当浏览器收到位置数据，或位置数据请求失败时收到错误信息时触发。
- {{domxref("HTMLGeolocationElement.promptaction_event", "promptaction")}} {{experimental_inline}}
  - : 当用户激活 `<geolocation>` 元素并从生成的对话框中选择一个选项（授予或拒绝 `geolocation` 权限）时触发。
- {{domxref("HTMLGeolocationElement.promptdismiss_event", "promptdismiss")}} {{experimental_inline}}
  - : 当用户激活 `<geolocation>` 元素并通过按下“关闭”按钮或 <kbd>Esc</kbd> 键关闭生成的对话框时触发。
- {{domxref("HTMLGeolocationElement.validationstatuschange_event", "validationstatuschange")}} {{experimental_inline}}
  - : 当 `<geolocation>` 元素的 {{domxref("HTMLGeolocationElement.isValid", "isValid")}} 值更改时触发。

## 描述

`HTMLGeolocationElement` 接口表示 {{htmlelement("geolocation")}} 元素，该元素创建一个交互式控件，允许用户与页面共享其位置数据。

当用户激活该控件时，会看到一个对话框，请求他们允许共享位置数据。如果他们授予权限，浏览器将尝试在后台使用 Geolocation API 检索用户的位置数据。

默认情况下，浏览器只请求一次位置数据，就像调用了 {{domxref("Geolocation.getCurrentPosition()")}} 方法一样。但是，如果 [`watch`](/en-US/docs/Web/HTML/Reference/Elements/geolocation#watch) 属性设置为 `true`，浏览器会在设备位置变化时更新数据，就像调用了 {{domxref("Geolocation.watchPosition()")}} 一样。

当数据请求返回时，会触发 {{domxref("HTMLGeolocationElement.location_event", "location")}} 事件，使您可以做出适当的响应，例如获取数据并将位置绘制在地图上。

- 如果成功检索到位置数据，则可通过 {{domxref("HTMLGeolocationElement.position")}} 属性获取，该属性包含一个 {{domxref("GeolocationPosition")}} 对象。
- 如果检索数据失败，则可通过 {{domxref("HTMLGeolocationElement.error")}} 属性获取错误信息，该属性包含一个 {{domxref("GeolocationPositionError")}} 对象。

通过 {{domxref("HTMLGeolocationElement.promptaction_event", "promptaction")}} 和 {{domxref("HTMLGeolocationElement.promptdismiss_event", "promptdismiss")}} 事件，您可以响应用户与 `<geolocation>` 对话框的交互，例如在用户拒绝访问数据时请求他们做出不同的选择。

当[阻止器](/en-US/docs/Web/HTML/Reference/Elements/geolocation#geolocation_blocking)在 {{htmlelement("geolocation")}} 元素上生效时，该元素将被阻止发挥功能（无效），可能是暂时性的，也可能是永久性的，具体取决于原因。您可以通过查询 {{domxref("HTMLGeolocationElement.isValid")}} 属性来检查其是否无效。您还可以通过 {{domxref("HTMLGeolocationElement.invalidReason")}} 属性获取其无效的原因——有关可能原因的完整列表，请参阅该页面。

## 示例

### 基本用法

有关使用 `<geolocation>` 元素及其关联的 `HTMLGeolocationElement` 对象返回位置数据的最小示例，请参阅我们的[基本示例](https://mdn.github.io/dom-examples/geolocation-element/basic-example/)（[源代码](https://github.com/mdn/dom-examples/tree/main/geolocation-element/basic-example)）和[基本 watch 示例](https://mdn.github.io/dom-examples/geolocation-element/basic-watch-example/)（[源代码](https://github.com/mdn/dom-examples/tree/main/geolocation-element/basic-watch-example)）。

有关详细教程，请参阅 [`<geolocation>`](/en-US/docs/Web/HTML/Reference/Elements/geolocation#basic_usage_example) 参考页面。

### 嵌入地图示例

此示例使用 `<geolocation>` 元素检索您当前的位置，并将其绘制在使用 [Leaflet JS](https://leafletjs.com/) 渲染的地图上。该示例还使用一个普通的 `<button>` 回退方案，以便在不支持该元素的浏览器中检索位置数据。

#### HTML

我们包含一个带有 `autolocate` 属性的 `<geolocation>` 元素，这样浏览器会在先前已授予 `geolocation` 权限的情况下自动尝试检索位置数据。在 `<geolocation>` 元素内部，我们嵌套了一个 {{htmlelement("button")}} 回退按钮，在不支持 `<geolocation>` 的浏览器中会渲染该按钮，以便请求位置数据。

```html
<geolocation autolocate>
  <button id="fallback">Use location</button>
</geolocation>
```

接下来，我们包含一个 {{htmlelement("p")}} 元素，用于输出状态消息和错误信息。

```html
<p id="status">Status:</p>
```

最后，我们包含一个 {{htmlelement("div")}} 元素，用于渲染地图。

```html
<div id="map"></div>
```

#### JavaScript

在脚本中，我们首先获取状态 `<p>` 元素的引用：

```js
const statusElem = document.querySelector("#status");
```

接下来，我们通过测试 `typeof HTMLGeolocationElement === "function"` 来检测是否支持 `<geolocation>` 元素：

```js
if (typeof HTMLGeolocationElement === "function") {
  // <geolocation> is supported
} else {
  // <geolocation> is not supported; use fallback button
}
```

如果支持 `<geolocation>`，则执行 `if` 块。它首先获取 `<geolocation>` 元素的引用：

```js
const geo = document.querySelector("geolocation");
```

接下来，我们向生成的 `HTMLGeolocationElement` 对象添加一个 {{domxref("HTMLGeolocationElement.location_event", "location")}} 事件监听器，以检测位置数据请求何时返回。如果数据成功返回，我们通过 {{domxref("HTMLGeolocationElement.position")}} 属性访问它，并获取纬度和经度值。我们将这些值记录到控制台，然后将它们传递给 `drawMap()` 函数（稍后定义）以及 `HTMLGeolocationElement` 对象的引用，从而将它们绘制在地图上。如果数据请求失败，我们通过 {{domxref("HTMLGeolocationElement.error")}} 属性访问错误，并将错误消息记录到控制台。

```js
geo.addEventListener("location", () => {
  if (geo.position) {
    console.log(
      `${geo.position.coords.latitude},${geo.position.coords.longitude}`,
    );
    drawMap(geo.position.coords.latitude, geo.position.coords.longitude, geo);
  } else if (geo.error) {
    console.log(geo.error.message);
  }
});
```

接下来，我们向生成的 `HTMLGeolocationElement` 对象添加 {{domxref("HTMLGeolocationElement.promptdismiss_event", "promptdismiss")}} 和 {{domxref("HTMLGeolocationElement.promptaction_event", "promptaction")}} 事件监听器。这些监听器允许我们在用户关闭 `<geolocation>` 提示或从提示中选择某个选项时运行相应的函数。

```js
geo.addEventListener("promptdismiss", notifyUserRetrySelection);
geo.addEventListener("promptaction", notifyUserGrantPermission);
```

最后，对于 `if` 块，我们定义前面两个事件监听器中引用的 `notifyUserRetrySelection()` 和 `notifyUserGrantPermission()` 函数。前者向状态段落打印一条消息，告诉用户再次按下按钮并允许位置访问，因为在这种情况下，我们总是希望他们重试。后者使用 {{domxref("HTMLGeolocationElement.permissionStatus")}} 属性检查权限状态是否为 `denied` 或 `prompt`，如果是，则请求他们再次按下按钮并允许位置访问。如果他们已授予权限，则无需询问。

```js
function notifyUserRetrySelection() {
  statusElem.textContent =
    'Please press the "Use location" button again and allow location for this site.';
}

function notifyUserGrantPermission() {
  if (geo.permissionStatus === "denied" || geo.permissionStatus === "prompt") {
    statusElem.textContent =
      'Please press the "Use location" button again and allow location for this site.';
  }
}
```

如果不支持 `<geolocation>`，则执行 `else` 块。它首先获取回退 `<button>` 元素的引用：

```js
const fallback = document.querySelector("#fallback");
```

接下来，我们向生成的 `HTMLButtonElement` 对象添加一个 `click` 事件处理器。在其中，我们使用 {{domxref("Geolocation.getCurrentPosition()")}} 调用来模拟 `HTMLGeolocationElement` 代码路径中的成功和失败情况。结果相同——我们要么通过将位置数据传递给 `drawMap()` 函数（以及 `HTMLButtonElement` 对象的引用）将其绘制在地图上，要么将错误消息打印到状态段落中。

```js
fallback.addEventListener("click", () => {
  navigator.geolocation.getCurrentPosition(
    (position) => {
      drawMap(position.coords.latitude, position.coords.longitude, fallback);
    },
    (error) => {
      statusElem.textContent += `${error.message}, `;
    },
  );
});
```

最后一步是定义 `drawMap()` 函数，该函数接受纬度和经度数据作为参数，以及触发命令的按钮的引用。函数体使用 [Leaflet JS](https://leafletjs.com/) 代码（有关说明，请参阅 [Leaflet Quick Start Guide](https://leafletjs.com/examples/quick-start/)）将用户的位置绘制在地图上，向状态段落打印成功消息，并隐藏按钮。最后一步是为了在用户成功后再次按下按钮时避免代码出错而进行的简化。

```js
function drawMap(lat, long, btn) {
  const map = L.map("map").setView([lat, long], 13);
  L.tileLayer("https://tile.openstreetmap.org/{z}/{x}/{y}.png", {
    maxZoom: 19,
    attribution:
      '&copy; <a href="http://www.openstreetmap.org/copyright">OpenStreetMap</a>',
  }).addTo(map);
  const marker = L.marker([lat, long]).addTo(map);

  statusElem.textContent = "Map drawn successfully.";
  btn.style.display = "none";
}
```

#### 结果

请参阅此代码的[在线运行示例](https://mdn.github.io/dom-examples/geolocation-element/embedded-map/)（[源代码](https://github.com/mdn/dom-examples/tree/main/geolocation-element/embedded-map)）。如果可能，请在支持的浏览器和不支持的浏览器中查看演示，并注意在允许使用 `geolocation` 权限时权限对话框流程的差异。

还可以尝试以下操作：

- 在您允许了 `geolocation` 权限并看到地图渲染后，尝试使用可用的浏览器控件撤销该权限，然后刷新页面以重置示例。
- 现在尝试拒绝使用 `geolocation` 的权限或关闭权限对话框，并注意我们先前设置的 `promptdismiss` 和 `promptaction` 事件监听器如何导致向状态段落打印一条消息，以帮助用户使用页面。

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- {{htmlelement("geolocation")}} 元素
- {{httpheader("Permissions-Policy/geolocation", "geolocation")}} [权限策略](/en-US/docs/Web/HTTP/Guides/Permissions_Policy)
- [Geolocation API](/en-US/docs/Web/API/Geolocation_API)
- [Permissions API](/en-US/docs/Web/API/Permissions_API)
- [Introducing the `<geolocation>` HTML element](https://developer.chrome.com/blog/geolocation-html-element) 位于 developer.chrome.com (2026)