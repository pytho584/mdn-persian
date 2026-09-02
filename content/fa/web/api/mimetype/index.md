---
title: "MimeType"
---

---
title: MimeType
slug: Web/API/MimeType
page-type: web-api-interface
status:
  - deprecated
browser-compat: api.MimeType
---

{{APIRef("HTML DOM")}}{{Deprecated_Header}}

**`MimeType`** 接口提供與特定外掛程式關聯的 MIME 類型相關資訊。{{domxref("Navigator.mimeTypes")}} 會回傳此物件的陣列。

## 執行個體屬性

- {{domxref("MimeType.type")}} {{Deprecated_Inline}}
  - : 回傳關聯外掛程式的 MIME 類型。
- {{domxref("MimeType.description")}} {{Deprecated_Inline}}
  - : 回傳關聯外掛程式的描述；如果沒有描述，則回傳空字串。
- {{domxref("MimeType.suffixes")}} {{Deprecated_Inline}}
  - : 一個字串，包含外掛程式所顯示資料的有效副檔名；如果某個副檔名對特定模組無效，則回傳空字串。例如，瀏覽器的內容解密模組可能會出現在外掛程式清單中，但支援的副檔名可能比預期的更多，因此它可能回傳空字串。
- {{domxref("MimeType.enabledPlugin")}} {{Deprecated_Inline}}
  - : 回傳一個 {{domxref("Plugin")}} 實例，其中包含外掛程式本身的資訊。

## 規範

{{Specifications}}

## 瀏覽器相容性

{{Compat}}