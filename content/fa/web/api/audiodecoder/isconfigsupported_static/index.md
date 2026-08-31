---
title: "AudioDecoder: isConfigSupported() static method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioDecoder/isConfigSupported_static"
translated_by: "n8n + AI"
---

---
title: "AudioDecoder: isConfigSupported() static method"
short-title: isConfigSupported()
slug: Web/API/AudioDecoder/isConfigSupported_static
page-type: web-api-static-method
browser-compat: api.AudioDecoder.isConfigSupported_static
---

{{APIRef("WebCodecs API")}}{{SecureContext_Header}}{{AvailableInWorkers("window_and_dedicated")}}

**`isConfigSupported()`** 静态方法属于 {{domxref("AudioDecoder")}} 接口，用于检查给定的配置是否受支持（即 {{domxref("AudioDecoder")}} 对象能否使用该配置成功初始化）。

## 语法

```js-nolint
AudioDecoder.isConfigSupported(config)
```

### 参数

- `config`
  - : 由 {{domxref("AudioDecoder.configure")}} 接受的字典对象。

### 返回值

一个 {{jsxref("Promise")}}，解析为包含以下成员的对象：

- `supported`
  - : 布尔值，如果给定的配置被解码器支持，则为 `true`。
- `config`
  - : 给定配置的副本，其中包含解码器能识别的所有字段。

### 异常

- {{jsxref("TypeError")}}
  - : 如果提供的 `config` 无效则抛出；即缺少必需值（例如空的 `codec` 字段）或包含无效值（例如负的 `sampleRate`）。

## 示例

以下示例测试浏览器是否支持多种音频编解码器。

```js
const codecs = ["mp4a.40.2", "mp3", "alaw", "ulaw"];
const configs = [];
for (const codec of codecs) {
  configs.push({
    codec,
    sampleRate: 48000,
    numberOfChannels: 1,
    not_supported_field: 123,
  });
}
for (const config of configs) {
  const support = await AudioDecoder.isConfigSupported(config);
  console.log(
    `AudioDecoder's config ${JSON.stringify(support.config)} support: ${
      support.supported
    }`,
  );
}
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}