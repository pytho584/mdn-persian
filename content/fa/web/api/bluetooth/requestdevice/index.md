---
title: "Bluetooth: requestDevice() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Bluetooth/requestDevice"
translated_by: "n8n + AI"
---

---
title: "Bluetooth: requestDevice() method"
short-title: requestDevice()
slug: Web/API/Bluetooth/requestDevice
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.Bluetooth.requestDevice
---

{{APIRef("Bluetooth API")}}{{SeeCompatTable}}{{securecontext_header}}

متد **`Bluetooth.requestDevice()`** از رابط {{domxref("Bluetooth")}} یک {{jsxref("Promise")}} برمی‌گرداند که با یک شیء {{domxref("BluetoothDevice")}} مطابق با گزینه‌های مشخص‌شده تکمیل می‌شود. اگر رابط کاربری انتخاب‌گر وجود نداشته باشد، این متد اولین دستگاهی را که با معیارها مطابقت دارد برمی‌گرداند.

## نحو (Syntax)

```js-nolint
requestDevice()
requestDevice(options)
```

### پارامترها

- `options` {{optional_inline}}
  - : یک شیء که گزینه‌هایی را برای انتخاب یک دستگاه مناسب تنظیم می‌کند.
    گزینه‌های موجود عبارت‌اند از:
    - `filters` {{optional_inline}}
      - : آرایه‌ای از اشیاء فیلتر که ویژگی‌های دستگاه‌هایی را که مطابقت داده می‌شوند نشان می‌دهد.
        برای مطابقت با یک شیء فیلتر، یک دستگاه باید با تمام مقادیر فیلتر مطابقت داشته باشد: تمام `services`، `name`، `namePrefix` و غیره مشخص‌شده.

        هر فیلتر از آرایه‌ای از اشیاء با ویژگی‌های زیر تشکیل شده است:
        - `services` {{optional_inline}}
          - : آرایه‌ای از مقادیر که خدمات GATT (پروفایل ویژگی عمومی) بلوتوث را نشان می‌دهد که یک دستگاه بلوتوث باید پشتیبانی کند.
            هر مقدار می‌تواند یک نام معتبر از [لیست خدمات اختصاص‌داده‌شده GATT](https://github.com/WebBluetoothCG/registries/blob/master/gatt_assigned_services.txt) باشد، مانند `'battery_service'` یا `'blood_pressure'`.
            همچنین می‌توانید یک UUID کامل سرویس مانند `'0000180F-0000-1000-8000-00805f9b34fb'` یا نام مستعار کوتاه 16 بیتی (`0x180F`) یا 32 بیتی را ارسال کنید.
            توجه داشته باشید که اینها همان مقادیری هستند که می‌توان به {{domxref("BluetoothUUID/getService_static","BluetoothUUID.getService()")}} ارسال کرد.

        - `name` {{optional_inline}}
          - : رشته‌ای حاوی نام دقیق دستگاهی که باید با آن مطابقت داده شود.
        - `namePrefix` {{optional_inline}}
          - : رشته‌ای حاوی پیشوند نام که باید با آن مطابقت داده شود.
            تمام دستگاه‌هایی که نامشان با این رشته شروع می‌شود مطابقت داده می‌شوند.
        - `manufacturerData` {{optional_inline}}
          - : آرایه‌ای از اشیاء که با داده‌های تولیدکننده در بسته‌های تبلیغاتی بلوتوث کم‌مصرف (BLE) مطابقت دارند. <!-- BluetoothManufacturerDataFilterInit -->
            هر شیء فیلتر دارای ویژگی‌های زیر است:
            - `companyIdentifier`
              - : یک عدد اجباری که تولیدکننده دستگاه را شناسایی می‌کند.
                شناسه‌های شرکت در [اعداد اختصاص‌داده‌شده](https://www.bluetooth.com/specifications/assigned-numbers/) مشخصات بلوتوث، بخش 7 فهرست شده‌اند.
                به عنوان مثال، برای مطابقت با دستگاه‌های تولید شده توسط "Digianswer A/S"، با عدد هگز اختصاص‌داده‌شده `0x000C`، باید `12` را مشخص کنید.
            - `dataPrefix` {{optional_inline}}
              - : پیشوند داده.
                یک بافر حاوی مقادیری که باید با مقادیر ابتدای داده‌های تولیدکننده تبلیغاتی مطابقت داده شوند.
            - `mask` {{optional_inline}}
              - : این به شما امکان می‌دهد با ماسک کردن برخی بایت‌های `dataPrefix` داده سرویس، با بایت‌های موجود در داده‌های تولیدکننده مطابقت دهید.

        - `serviceData` {{optional_inline}} <!-- BluetoothServiceDataFilterInit -->
          - : آرایه‌ای از اشیاء که با داده‌های سرویس در بسته‌های تبلیغاتی بلوتوث کم‌مصرف (BLE) مطابقت دارند.<!-- BluetoothServiceDataFilterInit -->
            هر شیء فیلتر دارای ویژگی‌های زیر است:
            - `service`
              - : نام سرویس GATT، UUID سرویس، یا فرم 16 بیتی یا 32 بیتی UUID.
                این همان مقادیری را می‌گیرد که عناصر آرایه [`services`](#services).
            - `dataPrefix` {{optional_inline}}
              - : پیشوند داده.
                یک بافر حاوی مقادیری که باید با مقادیر ابتدای داده‌های سرویس تبلیغاتی مطابقت داده شوند.
            - `mask` {{optional_inline}}
              - : این به شما امکان می‌دهد با ماسک کردن برخی بایت‌های `dataPrefix` داده سرویس، با بایت‌های موجود در داده‌های سرویس مطابقت دهید.

    - `exclusionFilters` {{optional_inline}}
      - : آرایه‌ای از اشیاء فیلتر که ویژگی‌های دستگاه‌هایی را نشان می‌دهد که از مطابقت حذف خواهند شد.
        ویژگی‌های عناصر آرایه همانند [`filters`](#filters) است.
    - `optionalServices` {{optional_inline}}
      - : آرایه‌ای از شناسه‌های سرویس اختیاری.

        شناسه‌ها همان مقادیری را می‌گیرند که عناصر آرایه [`services`](#services) (نام سرویس GATT، UUID سرویس، یا فرم کوتاه 16 بیتی یا 32 بیتی UUID).

    - `optionalManufacturerData` {{optional_inline}}
      - : یک آرایه اختیاری از کدهای صحیح تولیدکننده.
        این همان مقادیری را می‌گیرد که [`companyIdentifier`](#companyidentifier).

        از این داده‌ها برای فیلتر کردن دستگاه‌ها استفاده نمی‌شود، اما تبلیغاتی که با مجموعه مشخص‌شده مطابقت دارند همچنان در رویدادهای `advertisementreceived` تحویل داده می‌شوند.
        این مفید است زیرا به کد اجازه می‌دهد علاقه‌مندی به داده‌های دریافت‌شده از دستگاه‌های بلوتوث را بدون محدود کردن فیلتری که کنترل می‌کند کدام دستگاه‌ها در اعلان مجوز به کاربر نمایش داده می‌شوند، مشخص کند.

    - `acceptAllDevices` {{optional_inline}}
      - : یک مقدار بولی که نشان می‌دهد اسکریپت درخواست‌دهنده می‌تواند تمام دستگاه‌های بلوتوث را بپذیرد.
        پیش‌فرض `false` است.

        این گزینه زمانی مناسب است که دستگاه‌ها اطلاعات کافی برای مفید بودن فیلتر کردن را تبلیغ نکرده‌اند.
        وقتی `acceptAllDevices` روی `true` تنظیم شده است، باید تمام [`filters`](#filters) و [`exclusionFilters`](#exclusionfilters) را حذف کنید، و باید [`optionalServices`](#optionalservices) را تنظیم کنید تا بتوانید از دستگاه بازگشتی _استفاده_ کنید.

پس از اینکه کاربر دستگاهی را برای جفت‌سازی در مبدأ فعلی انتخاب کرد، فقط دسترسی به خدماتی مجاز است که UUID آن در لیست خدمات در هر عنصر از [`filters.services`](#services) یا در [`optionalServices`](#optionalservices) فهرست شده باشد.
بنابراین مهم است که خدمات مورد نیاز را فهرست کنید.
به ویژه، هنگام فیلتر کردن فقط با [`name`](#name) باید به خاطر داشته باشید که خدمات مورد نظر را نیز در [`optionalServices`](#optionalservices) مشخص کنید.

> [!NOTE]
> اگرچه آرگومان `options` از نظر فنی اختیاری است، اما برای بازگرداندن هر نتیجه‌ای باید یا مقداری برای `filters` تنظیم کنید یا `acceptAllDevices` را روی `true` قرار دهید.

### مقدار بازگشتی

یک {{jsxref("Promise")}} به یک شیء {{domxref("BluetoothDevice")}}.

### استثناها (Exceptions)

- {{jsxref("TypeError")}}
  - : اگر `options` ارائه‌شده معنی‌دار نباشند پرتاب می‌شود.
    به عنوان مثال، اگر `options.filters` وجود داشته باشد و `options.acceptAllDevices` برابر `true` باشد، `options.filters` وجود نداشته باشد و `options.acceptAllDevices` برابر `false` باشد، یا `options.filters` برابر `[]` باشد.
- `NotFoundError` {{domxref("DOMException")}}
  - : اگر هیچ دستگاه بلوتوثی که با گزینه‌های مشخص‌شده مطابقت داشته باشد وجود نداشته باشد پرتاب می‌شود.
- `SecurityError` {{domxref("DOMException")}}
  - : اگر این عملیات در این زمینه به دلیل [ملاحظات امنیتی](/en-US/docs/Web/API/Web_Bluetooth_API#security_considerations)، مانند فراخوانی از یک مبدأ ناامن، مجاز نباشد پرتاب می‌شود.

## مثال‌ها

```js
// Discovery options match any devices advertising:
// - The standard heart rate service.
// - Both 16-bit service IDs 0x1802 and 0x1803.
// - A proprietary 128-bit UUID service c48e6067-5295-48d3-8d5c-0395f61792b1.
// - Devices with name "ExampleName".
// - Devices with name starting with "Prefix".
//
// And enables access to the battery service if devices
// include it, even if devices do not advertise that service.
let options = {
  filters: [
    { services: ["heart_rate"] },
    { services: [0x1802, 0x1803] },
    { services: ["c48e6067-5295-48d3-8d5c-0395f61792b1"] },
    { name: "ExampleName" },
    { namePrefix: "Prefix" },
  ],
  optionalServices: ["battery_service"],
};

navigator.bluetooth
  .requestDevice(options)
  .then((device) => {
    console.log(`Name: ${device.name}`);
    // Do something with the device.
  })
  .catch((error) => console.error(`Something went wrong. ${error}`));
```

[مثال‌های دقیق‌تر](https://webbluetoothcg.github.io/web-bluetooth/#example-filter-by-services) در مشخصات و همچنین در [ارتباط با دستگاه‌های بلوتوث از طریق جاوااسکریپت](https://developer.chrome.com/docs/capabilities/bluetooth) در _developer.chrome.com_ موجود است.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [ارتباط با دستگاه‌های بلوتوث از طریق جاوااسکریپت](https://developer.chrome.com/docs/capabilities/bluetooth) در _developer.chrome.com_.