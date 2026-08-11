---
title: "<track> HTML embed text track element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/track"
translated_by: "n8n + AI"
---

المان **`<track>`** در [HTML](/en-US/docs/Web/HTML) به عنوان فرزندِ المان‌های رسانه‌ای `<audio>` و `<video>` استفاده می‌شود. هر المان `track` به شما امکان می‌دهد یک track متنی زمان‌بندی‌شده (یا داده‌های مبتنی بر زمان) مشخص کنید که هم‌زمان با المان رسانه‌ای نمایش داده می‌شود؛ مثلاً برای قرار دادن زیرنویس یا زیرنویس بسته روی ویدیو یا در کنار trackهای صوتی.

برای یک المان رسانه‌ای می‌توان چندین track مشخص کرد که شامل انواع مختلف داده‌های متنی زمان‌بندی‌شده هستند، یا داده‌هایی که برای زبان‌های مختلف ترجمه شده‌اند. داده‌ای که استفاده می‌شود یا trackای است که به عنوان پیش‌فرض تعیین شده، یا بر اساس نوع و ترجمه‌ای است که با ترجیحات کاربر هماهنگ است.

این trackها با [قالب WebVTT](/en-US/docs/Web/API/WebVTT_API) (فایل‌های `.vtt`) — که مخفف Web Video Text Tracks است — فرمت می‌شوند.

```html interactive-example
<video controls src="/shared-assets/videos/friday.mp4">
  <track
    default
    kind="captions"
    srclang="en"
    label="English"
    src="/shared-assets/misc/friday.vtt" />
  Download the
  <a href="/shared-assets/videos/friday.mp4">MP4</a>
  video, and
  <a href="/shared-assets/misc/friday.vtt">subtitles</a>.
</video>
```

```css interactive-example
video {
  width: 250px;
}

video::cue {
  font-size: 1rem;
}
```

## ویژگی‌ها

این المان شامل [ویژگی‌های سراسری](/en-US/docs/Web/HTML/Reference/Global_attributes) است.

- `default`
  - : این ویژگی مشخص می‌کند که track باید فعال باشد، مگر اینکه ترجیحات کاربر نشان دهد track دیگری مناسب‌تر است. این ویژگی فقط می‌تواند روی یک المان `track` برای هر المان رسانه‌ای استفاده شود.
- `kind`
  - : نحوه استفاده از track متنی را مشخص می‌کند. اگر حذف شود، نوع پیش‌فرض `subtitles` است. اگر مقدار نامعتبر باشد، از `metadata` استفاده می‌شود.
    کلیدواژه‌های زیر مجاز هستند:
    - `subtitles`
      - : زیرنویس‌ها رونویسی یا ترجمه گفتگو را فراهم می‌کنند. آن‌ها زمانی مناسب هستند که صدا موجود است اما قابل درک نیست؛ مثلاً گفتار یا متنی که در یک فیلم انگلیسی‌زبان، انگلیسی نیست. زیرنویس‌ها ممکن است محتوای اضافی نیز داشته باشند، معمولاً اطلاعات پس‌زمینه بیشتر. به عنوان مثال، متن ابتدای فیلم‌های جنگ ستارگان یا تاریخ، زمان و مکان یک صحنه. اطلاعات زیرنویس‌ها مکمل صدا و تصویر است. اغلب در خود ویدیو جاسازی می‌شود، اما می‌تواند به‌صورت جداگانه نیز ارائه شود، به‌ویژه برای ترجمه کل فیلم.
    - `captions`
      - : زیرنویس بسته رونویسی یا ترجمه گفتگو، جلوه‌های صوتی، نشانه‌های موسیقی مرتبط و سایر اطلاعات صوتی مرتبط مانند منبع نشانه (مثلاً شخصیت، محیط) را فراهم می‌کند. آن‌ها زمانی مناسب هستند که صدا در دسترس نیست یا به وضوح قابل شنیدن نیست (مثلاً به دلیل بی‌صدا بودن، غرق شدن در نویز محیط، یا ناشنوا بودن کاربر).
    - `descriptions`
      - : توضیحات قسمت _ویدیویی_ منبع رسانه‌ای را خلاصه می‌کنند. این توضیحات برای این در نظر گرفته شده‌اند که وقتی بخش بصری مبهم، در دسترس یا قابل استفاده نیست، به صورت صوت درآیند (مثلاً به این دلیل که کاربر هنگام رانندگی بدون صفحه با برنامه تعامل می‌کند یا نابیناست).
    - `chapters`
      - : عنوان فصل‌ها برای زمانی استفاده می‌شوند که کاربر در حال پیمایش در منبع رسانه‌ای است.
    - `metadata`
      - : trackهایی که توسط اسکریپت‌ها استفاده می‌شوند. برای کاربر قابل مشاهده نیستند.

- `label`
  - : عنوان قابل خواندن برای کاربر که مرورگر هنگام فهرست کردن trackهای موجود از آن استفاده می‌کند.
- `src`
  - : آدرس فایل track (با پسوند `.vtt`). باید یک URL معتبر باشد. این ویژگی حتماً باید مشخص شود و مقدار URL آن باید با same origin سند یکسان باشد — مگر اینکه عنصر والد `<track>` یعنی `<audio>` یا `<video>` دارای ویژگی [`crossorigin`](/en-US/docs/Web/HTML/Reference/Attributes/crossorigin) باشد.
- `srclang`
  - : زبان داده‌های متنی track. باید یک [برچسب زبان معتبر بر اساس BCP 47](https://tools.ietf.org/html/bcp47) باشد. اگر ویژگی `kind` برابر با `subtitles` باشد، مقدار `srclang` حتماً باید مشخص شود.

## نکات استفاده

### انواع داده‌های track

نوع داده‌ای که `track` به رسانه اضافه می‌کند در ویژگی `kind` مشخص می‌شود. این ویژگی می‌تواند یکی از مقادیر `subtitles`، `captions`، `chapters` یا `metadata` باشد. عنصر به یک فایل منبع اشاره می‌کند که شامل متن زمان‌بندی‌شده است و مرورگر آن را در صورت درخواست کاربر برای داده‌های اضافی نمایش می‌دهد.

یک عنصر رسانه نمی‌تواند بیش از یک `track` با `kind`، `srclang` و `label` یکسان داشته باشد.

### تشخیص تغییرات cue

شیء زیرین `TextTrack` که توسط ویژگی `track` (از نوع `HTMLTrackElement.track`) نشان داده می‌شود، هر بار که cue فعال تغییر کند، یک رویداد `cuechange` دریافت می‌کند. این اتفاق حتی اگر track به یک عنصر رسانه متصل نباشد، رخ می‌دهد.

اگر track _به_ یک عنصر رسانه متصل باشد (یعنی از عنصر `<track>` به عنوان فرزند `<audio>` یا `<video>` استفاده شده باشد)، رویداد `cuechange` به `HTMLTrackElement` نیز ارسال می‌شود.

```js
let textTrackElem = document.getElementById("text-track");

textTrackElem.addEventListener("cuechange", (event) => {
  let cues = event.target.track.activeCues;
});
```

### افزودن track به صورت برنامه‌نویسی

رابط JavaScript که عنصر `<track>` را نمایش می‌دهد `HTMLTrackElement` است. track متن مرتبط با یک عنصر را می‌توان از طریق ویژگی `HTMLTrackElement.track` دریافت کرد که از نوع `TextTrack` است.

اشیاء `TextTrack` را می‌توان با استفاده از متد `HTMLMediaElement.addTextTrack()` به عناصر `HTMLVideoElement` یا `HTMLAudioElement` اضافه کرد. همچنین اشیاء `TextTrack` مرتبط با یک عنصر رسانه در یک `TextTrackList` ذخیره می‌شوند که با استفاده از ویژگی `HTMLMediaElement.textTracks` قابل دسترسی است.

## مثال‌ها

```html
<video controls poster="/images/sample.gif">
  <source src="sample.mp4" type="video/mp4" />
  <source src="sample.ogv" type="video/ogv" />
  <track kind="captions" src="sampleCaptions.vtt" srclang="en" />
  <track kind="chapters" src="sampleChapters.vtt" srclang="en" />
  <track kind="subtitles" src="sampleSubtitles_de.vtt" srclang="de" />
  <track kind="subtitles" src="sampleSubtitles_en.vtt" srclang="en" />
  <track kind="subtitles" src="sampleSubtitles_ja.vtt" srclang="ja" />
  <track kind="subtitles" src="sampleSubtitles_oz.vtt" srclang="oz" />
  <track kind="metadata" src="keyStage1.vtt" srclang="en" label="Key Stage 1" />
  <track kind="metadata" src="keyStage2.vtt" srclang="en" label="Key Stage 2" />
  <track kind="metadata" src="keyStage3.vtt" srclang="en" label="Key Stage 3" />
  <!-- Fallback -->
  …
</video>
```

## خلاصه فنی

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories">Content categories</a>
      </th>
      <td>هیچ</td>
    </tr>
    <tr>
      <th scope="row">محتوای مجاز</th>
      <td>هیچ؛ این یک void element است (عنصری که محتوا ندارد).</td>
    </tr>
    <tr>
      <th scope="row">حذف تگ</th>
      <td>باید تگ آغاز داشته باشد و نباید تگ پایانی داشته باشد.</td>
    </tr>
    <tr>
      <th scope="row">والدین مجاز</th>
      <td>
        <p>یک media element، مانند `<audio>` یا `<video>`.</p>
      </td>
    </tr>
    <tr>
      <th scope="row">نقش ARIA ضمنی</th>
      <td>
        <a href="https://w3c.github.io/html-aria/#dfn-no-corresponding-role">No corresponding role</a>
      </td>
    </tr>
    <tr>
      <th scope="row">نقش‌های ARIA مجاز</th>
      <td>هیچ <code>role</code> مجاز نیست.</td>
    </tr>
    <tr>
      <th scope="row">رابط DOM</th>
      <td><code>HTMLTrackElement</code></td>
    </tr>
  </tbody>
</table>

## مشخصات

## سازگاری مرورگر

## جستارهای وابسته

- [WebVTT text track format](/en-US/docs/Web/API/WebVTT_API)
- [`HTMLMediaElement.textTracks`](/en-US/docs/Web/API/HTMLMediaElement/textTracks)