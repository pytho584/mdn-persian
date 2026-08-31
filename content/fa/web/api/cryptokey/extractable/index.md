---
title: "CryptoKey: extractable property"
short-title: extractable
slug: Web/API/CryptoKey/extractable
page-type: web-api-instance-property
browser-compat: api.CryptoKey.extractable
---

{{APIRef("Web Crypto API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`extractable`** از رابط {{DOMxRef("CryptoKey")}} مشخص می‌کند که آیا کلید را می‌توان با استفاده از [`SubtleCrypto.exportKey()`](/en-US/docs/Web/API/SubtleCrypto/exportKey) یا [`SubtleCrypto.wrapKey()`](/en-US/docs/Web/API/SubtleCrypto/wrapKey) استخراج کرد یا خیر.

اگر کلید قابل استخراج نباشد، استفاده از [`exportKey()`](/en-US/docs/Web/API/SubtleCrypto/exportKey) یا [`wrapKey()`](/en-US/docs/Web/API/SubtleCrypto/wrapKey) برای استخراج آن یک استثنا ایجاد می‌کند.

## مقدار

یک مقدار بولین که اگر کلید قابل استخراج باشد `true` و در غیر این صورت `false` است.

## مثال‌ها

در این مثال، اگر کلید قابل استخراج نباشد، دکمه _Export_ غیرفعال می‌شود و هیچ شنونده‌ای به آن اضافه نمی‌شود.

```js
// Export the given key and write it into the "exported-key" space.
async function exportCryptoKey(key) {
  const exported = await window.crypto.subtle.exportKey("raw", key);
  const exportedKeyBuffer = new Uint8Array(exported);

  const exportKeyOutput = document.querySelector(".exported-key");
  exportKeyOutput.textContent = `[${exportedKeyBuffer}]`;
}

// Enable or disable the exportButton if the key is extractable or not
function setExportButton(key) {
  const exportButton = document.querySelector(".raw");

  // Disable the button if the key is not extractable
  exportButton.disabled = !key.extractable;
  if (key.extractable) {
    // Add an event listener to extract the key
    exportButton.addEventListener("click", () => {
      exportCryptoKey(key);
    });
  }
}

// Generate an encrypt/decrypt secret key,
// then enable and set up an event listener on the "Export" button.
window.crypto.subtle
  .generateKey(
    {
      name: "AES-GCM",
      length: 256,
    },
    true,
    ["encrypt", "decrypt"],
  )
  .then(setExportButton(key));
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}