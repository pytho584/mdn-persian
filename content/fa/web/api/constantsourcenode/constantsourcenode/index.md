---
title: "ConstantSourceNode: ConstantSourceNode() constructor"
short-title: ConstantSourceNode()
slug: Web/API/ConstantSourceNode/ConstantSourceNode
page-type: web-api-constructor
browser-compat: api.ConstantSourceNode.ConstantSourceNode
---

{{APIRef("Web Audio API")}}

سازندهٔ **`ConstantSourceNode()`** یک نمونهٔ جدید از شیء {{domxref("ConstantSourceNode")}} می‌سازد که یک منبع صوتی را نشان می‌دهد که به‌طور مداوم نمونه‌هایی با مقادیر یکسان تولید می‌کند.

## Syntax

```js-nolint
new ConstantSourceNode(context, options)
```

### پارامترها

- `context`
  - : یک {{domxref("AudioContext")}} که نشان‌دهندهٔ بافت صوتی است که می‌خواهید گره به آن مرتبط شود.
- `options`
  - : یک شیء دیکشنری `ConstantSourceOptions` که ویژگی‌های مورد نظر برای `ConstantSourceNode` را تعریف می‌کند:
    - `offset`
      - : یک {{domxref("AudioParam")}} فقط‌خواندنی که مقدار ثابت تولیدشده توسط منبع را مشخص می‌کند. مقدار پیش‌فرض 1.0 است. محدودهٔ معمول از 1.0- تا 1.0 است، اما مقدار می‌تواند هر عددی از `-Infinity` تا `Infinity` باشد.

## مثال‌ها

در این مثال، یک بافت صوتی ساخته می‌شود و سپس یک `ConstantSourceNode` با مقدار اولیهٔ `offset` برابر با 0.5 ایجاد می‌شود.

```js
let audioContext = new AudioContext();

let myConstantSource = new ConstantSourceNode(audioContext, { offset: 0.5 });
```

> [!NOTE]
> `ConstantSourceNode` جدیدی که توسط سازنده ساخته می‌شود دارای
> [`channelCount`](/en-US/docs/Web/API/AudioNode/channelCount) برابر با
> 2 است.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}