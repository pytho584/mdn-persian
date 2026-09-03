---
title: "NDEFRecord"
---

---
title: NDEFRecord
slug: Web/API/NDEFRecord
page-type: web-api-interface
status:
  - experimental
browser-compat: api.NDEFRecord
---

{{SecureContext_Header}}{{SeeCompatTable}}{{APIRef("Web NFC API")}}

**`NDEFRecord`** 接口属于 [Web NFC API](/en-US/docs/Web/API/Web_NFC_API)，提供可从兼容 NFC 设备（例如支持 NDEF 的 NFC 标签）读取或写入的数据。

## 构造函数

- {{DOMxRef("NDEFRecord.NDEFRecord", "NDEFRecord()")}} {{Experimental_Inline}}
  - : 返回一个新的 `NDEFRecord` 实例。

## 实例属性

- {{DOMxRef("NDEFRecord.recordType")}} {{Experimental_Inline}} {{ReadOnlyInline}}
  - : 返回记录的类型。记录必须具有标准的已知类型名称，如 `"empty"`、`"text"`、`"url"`、`"smart-poster"`、`"absolute-url"`、`"mime"` 或 `"unknown"`，或者具有外部类型名称，外部类型名称由域名、冒号 (":") 和自定义类型名称组成。
- {{DOMxRef("NDEFRecord.mediaType")}} {{Experimental_Inline}} {{ReadOnlyInline}}
  - : 返回记录的 {{Glossary("MIME type", "MIME 类型")}}。如果 `recordType` 不等于 `"mime"`，则此值为 `null`。
- {{DOMxRef("NDEFRecord.id")}} {{Experimental_Inline}} {{ReadOnlyInline}}
  - : 返回记录标识符，它是一个用于标识记录的绝对或相对 URL。
    > [!NOTE]
    > 标识符的唯一性仅由记录的生成者保证。
- {{DOMxRef("NDEFRecord.data")}} {{Experimental_Inline}} {{ReadOnlyInline}}
  - : 返回一个 {{jsxref("DataView")}}，其中包含记录负载的原始字节。
- {{DOMxRef("NDEFRecord.encoding")}} {{Experimental_Inline}} {{ReadOnlyInline}}
  - : 返回文本负载的编码，否则返回 `null`。
- {{DOMxRef("NDEFRecord.lang")}} {{Experimental_Inline}} {{ReadOnlyInline}}
  - : 返回文本负载的语言；如果未提供，则返回 `null`。

## 实例方法

- {{DOMxRef("NDEFRecord.toRecords", "NDEFRecord.toRecords()")}} {{Experimental_Inline}}
  - : 将 {{DOMxRef("NDEFRecord.data")}} 转换为记录序列。这允许解析可能包含嵌套记录的记录类型的负载，例如智能海报和外部类型记录。

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}