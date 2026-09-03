---
title: "NDEFRecord: toRecords() method"
short-title: toRecords()
slug: Web/API/NDEFRecord/toRecords
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.NDEFRecord.toRecords
---

{{SecureContext_Header}}{{SeeCompatTable}}{{APIRef("Web NFC API")}}

**`toRecords()`** メソッドは、{{DOMxRef("NDEFRecord")}} インターフェイスのメソッドで、{{DOMxRef("NDEFRecord.data")}} を {{DOMxRef("NDEFRecord.recordType")}} に基づいてレコードのシーケンスに変換し、その結果を返します。これにより、スマートポスターや外部型レコードなど、ネストされたレコードを含む可能性のあるレコードタイプのペイロードを解析できます。

## 構文

```js-nolint
toRecords()
```

### 引数

なし。

### 戻り値

{{DOMxRef("NDEFRecord")}} のリスト。

### 例外

- `NotSupported` {{domxref("DOMException")}}
  - : {{Glossary("User Agent")}} が、この {{DOMxRef("NDEFRecord.data")}} と {{DOMxRef("NDEFRecord.recordType")}} の組み合わせを解析する方法を知らないことを示します。

## 例

NDEF メッセージをペイロードとして持つ外部レコードを読み取る

この例では、外部型レコードを使用して、アプリケーション定義のレコードを作成します。これらのレコードには、ペイロードとして {{domxref("NDEFMessage")}} を含めることができ、独自の {{domxref("NDEFRecord")}} オブジェクト（アプリケーションのコンテキストで使用されるローカル型を含む）を持ちます。スマートポスターレコード型もペイロードとして NDEF メッセージを含むことに注意してください。

NDEF はレコードの順序を保証しないため、ペイロードとして NDEF メッセージを持つ外部型レコードを使用すると、関連データをカプセル化するのに役立ちます。

この例では、ソーシャル投稿用の外部レコードを読み取る方法を示します。このレコードには、{{domxref("NDEFMessage")}} が含まれており、テキストレコードと、スマートポスターから借用した定義を持つローカル型 "act"（アクション）のレコードが含まれていますが、ローカルアプリケーションのコンテキストで使用されます。

```js
const ndefReader = new NDEFReader();
await ndefReader.scan();
ndefReader.onreading = (event) => {
  const externalRecord = event.message.records.find(
    (record) => record.type === "example.com:smart-poster",
  );

  let action, text;

  for (const record of externalRecord.toRecords()) {
    if (record.recordType === "text") {
      const decoder = new TextDecoder(record.encoding);
      text = decoder.decode(record.data);
    } else if (record.recordType === ":act") {
      action = record.data.getUint8(0);
    }
  }

  switch (action) {
    case 0: // アクションを実行
      console.log(`「${text}」をタイムラインに投稿`);
      break;
    case 1: // 後で保存
      console.log(`「${text}」を下書きとして保存`);
      break;
    case 2: // 編集用に開く
      console.log(`「${text}」を含む編集可能な投稿を表示`);
      break;
  }
};
```

## 仕様書

{{Specifications}}

## ブラウザー互換性

{{Compat}}