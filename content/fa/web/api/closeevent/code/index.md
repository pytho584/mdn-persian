---
title: "CloseEvent: code property"
short-title: code
slug: Web/API/CloseEvent/code
page-type: web-api-instance-property
browser-compat: api.CloseEvent.code
---

{{APIRef("Websockets API")}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`code`** در رابط {{domxref("CloseEvent")}} یک [کد بستن اتصال وب‌سوکت](https://www.rfc-editor.org/info/rfc6455/#section-7.1.5) را برمی‌گرداند که دلیل بسته شدن اتصال را نشان می‌دهد.

## مقدار

یک عدد صحیح [کد بستن اتصال وب‌سوکت](https://www.rfc-editor.org/info/rfc6455/#section-7.1.5) در بازه `1000` تا `4999` که دلیل بسته شدن اتصال را نشان می‌دهد.

<table class="no-markdown">
  <thead>
    <tr>
      <th>کد وضعیت</th>
      <th>معنی</th>
      <th>توضیحات</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>0</code>–<code>999</code></td>
      <td></td>
      <td>استفاده نشده است.</td>
    </tr>
    <tr>
      <td><code>1000</code></td>
      <td>Normal Closure</td>
      <td>
        اتصال با موفقیت هدفی را که برای آن ایجاد شده بود تکمیل کرد.
      </td>
    </tr>
    <tr>
      <td><code>1001</code></td>
      <td>Going Away</td>
      <td>
        نقطه پایانی (endpoint) در حال خروج است، یا به دلیل خطای سرور یا به این دلیل که مرورگر در حال دور شدن از صفحه‌ای است که اتصال را باز کرده است.
      </td>
    </tr>
    <tr>
      <td><code>1002</code></td>
      <td>Protocol error</td>
      <td>
        نقطه پایانی به دلیل خطای پروتکل، اتصال را قطع می‌کند.
      </td>
    </tr>
    <tr>
      <td><code>1003</code></td>
      <td>Unsupported Data</td>
      <td>
        اتصال به این دلیل خاتمه می‌یابد که نقطه پایانی داده‌ای از نوعی دریافت کرده است که نمی‌تواند بپذیرد. (به عنوان مثال، یک نقطه پایانی متنی، داده دودویی دریافت کرده است.)
      </td>
    </tr>
    <tr>
      <td><code>1004</code></td>
      <td>Reserved</td>
      <td>
        <strong>رزرو شده.</strong> ممکن است معنایی در آینده تعریف شود.
      </td>
    </tr>
    <tr>
      <td><code>1005</code></td>
      <td>No Status Received</td>
      <td>
        <strong>رزرو شده.</strong> نشان می‌دهد که هیچ کد وضعیتی ارائه نشده است، حتی با اینکه انتظار می‌رفت.
      </td>
    </tr>
    <tr>
      <td><code>1006</code></td>
      <td>Abnormal Closure</td>
      <td>
        <strong>رزرو شده.</strong> نشان می‌دهد که اتصال به شکلی غیرعادی بسته شده است (یعنی بدون ارسال فریم بستن) در حالی که کد وضعیت مورد انتظار بود.
      </td>
    </tr>
    <tr>
      <td><code>1007</code></td>
      <td>Invalid frame payload data</td>
      <td>
        نقطه پایانی اتصال را به این دلیل قطع می‌کند که پیامی دریافت شده که حاوی داده‌های ناسازگار است (مثلاً داده‌های غیر UTF-8 در یک پیام متنی).
      </td>
    </tr>
    <tr>
      <td><code>1008</code></td>
      <td>Policy Violation</td>
      <td>
        نقطه پایانی اتصال را به این دلیل قطع می‌کند که پیامی دریافت کرده که سیاست آن را نقض می‌کند. این یک کد وضعیت عمومی است و زمانی استفاده می‌شود که کدهای 1003 و 1009 مناسب نباشند.
      </td>
    </tr>
    <tr>
      <td><code>1009</code></td>
      <td>Message Too Big</td>
      <td>
        نقطه پایانی اتصال را به این دلیل قطع می‌کند که یک فریم داده که بیش از حد بزرگ است دریافت شده است.
      </td>
    </tr>
    <tr>
      <td><code>1010</code></td>
      <td>Mandatory Ext.</td>
      <td>
        کلاینت اتصال را به این دلیل قطع می‌کند که انتظار داشت سرور یک یا چند افزونه (extension) را مذاکره کند، اما سرور این کار را نکرد.
      </td>
    </tr>
    <tr>
      <td><code>1011</code></td>
      <td>Internal Error</td>
      <td>
        سرور اتصال را به این دلیل قطع می‌کند که با یک شرایط غیرمنتظره مواجه شده که آن را از انجام درخواست بازداشته است.
      </td>
    </tr>
    <tr>
      <td><code>1012</code></td>
      <td><a href="https://mailarchive.ietf.org/arch/msg/hybi/P_1vbD9uyHl63nbIIbFxKMfSwcM/">Service Restart</a></td>
      <td>
        سرور اتصال را به این دلیل قطع می‌کند که در حال راه‌اندازی مجدد است.
      </td>
    </tr>
    <tr>
      <td><code>1013</code></td>
      <td><a href="https://mailarchive.ietf.org/arch/msg/hybi/P_1vbD9uyHl63nbIIbFxKMfSwcM/">Try Again Later</a></td>
      <td>
        سرور اتصال را به دلیل یک شرایط موقت قطع می‌کند، مثلاً بیش از حد بارگذاری شده و در حال کنار گذاشتن برخی از کلاینت‌های خود است.
      </td>
    </tr>
    <tr>
      <td><code>1014</code></td>
      <td><a href="https://mailarchive.ietf.org/arch/msg/hybi/VOLI2xp4tzFnIFYespe6oOtpFXA/">Bad Gateway</a></td>
      <td>
        سرور به عنوان دروازه (gateway) یا پروکسی عمل می‌کرد و پاسخ نامعتبری از سرور بالادست (upstream) دریافت کرد. این مشابه کد وضعیت HTTP 502 است.
      </td>
    </tr>
    <tr>
      <td><code>1015</code></td>
      <td>TLS handshake</td>
      <td>
        <strong>رزرو شده.</strong> نشان می‌دهد که اتصال به دلیل شکست در انجام دست‌دهی TLS بسته شده است (مثلاً گواهی سرور قابل تأیید نیست).
      </td>
    </tr>
    <tr>
      <td><code>1016</code>–<code>2999</code></td>
      <td></td>
      <td>
        برای تعریف توسط بازبینی‌های آینده مشخصات پروتکل وب‌سوکت و برای تعریف توسط مشخصات افزونه‌ها.
      </td>
    </tr>
    <tr>
      <td><code>3000</code>–<code>3999</code></td>
      <td></td>
      <td>
        برای استفاده توسط کتابخانه‌ها، چارچوب‌ها و برنامه‌ها. این کدهای وضعیت <a href="https://www.iana.org/assignments/websocket/websocket.xml#close-code-number">مستقیماً در IANA ثبت شده‌اند</a>. تفسیر این کدها توسط پروتکل وب‌سوکت تعریف نشده است.
      </td>
    </tr>
    <tr>
      <td><code>4000</code>–<code>4999</code></td>
      <td></td>
      <td>
        برای استفاده خصوصی است و بنابراین نمی‌توانند ثبت شوند. چنین کدهایی را می‌توان با توافقات قبلی بین برنامه‌های وب‌سوکت استفاده کرد. تفسیر این کدها توسط پروتکل وب‌سوکت تعریف نشده است.
      </td>
    </tr>
  </tbody>
</table>

## مثال‌ها

مثال زیر مقدار `code` را در کنسول چاپ می‌کند.

```js
WebSocket.onclose = (event) => {
  console.log(event.code);
};
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [RFC 6455](https://www.rfc-editor.org/info/rfc6455/) (مشخصات پروتکل وب‌سوکت)
- [WebSocket Close Code Number Registry](https://www.iana.org/assignments/websocket/websocket.xml#close-code-number) (IANA)