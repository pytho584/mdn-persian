---
title: "FontData: blob() method"
short-title: blob()
slug: Web/API/FontData/blob
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.FontData.blob
---

{{APIRef("Local Font Access API")}}{{SeeCompatTable}}

**`blob()`** 方法属于 {{domxref("FontData")}} 接口，返回一个 {{jsxref("Promise")}}，该 Promise 会兑现为一个包含底层字体文件原始字节的 {{domxref("Blob")}}。

## 语法

```js-nolint
blob()
```

### 参数

无。

### 返回值

一个 {{jsxref("Promise")}}，兑现为一个包含底层字体文件原始字节的 {{domxref("Blob")}}。

## 示例

`blob()` 方法提供对底层 [SFNT](https://en.wikipedia.org/wiki/SFNT) 数据的访问——这是一种字体文件格式，可以包含其他字体格式，如 PostScript、TrueType、OpenType 或 Web Open Font Format (WOFF)。

```js
async function computeOutlineFormat() {
  try {
    const availableFonts = await window.queryLocalFonts({
      postscriptNames: ["ComicSansMS"],
    });
    for (const fontData of availableFonts) {
      // `blob()` returns a Blob containing valid and complete
      // SFNT-wrapped font data.
      const sfnt = await fontData.blob();
      // Slice out only the bytes we need: the first 4 bytes are the SFNT
      // version info.
      // Spec: https://learn.microsoft.com/en-us/typography/opentype/spec/otff#organization-of-an-opentype-font
      const sfntVersion = await sfnt.slice(0, 4).text();

      let outlineFormat = "UNKNOWN";
      switch (sfntVersion) {
        case "\x00\x01\x00\x00":
        case "true":
        case "typ1":
          outlineFormat = "truetype";
          break;
        case "OTTO":
          outlineFormat = "cff";
          break;
      }
      console.log("Outline format:", outlineFormat);
    }
  } catch (err) {
    console.error(err.name, err.message);
  }
}
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- [使用本地字体进行高级排版](https://developer.chrome.com/docs/capabilities/web-apis/local-fonts)
- {{cssxref("@font-face")}}