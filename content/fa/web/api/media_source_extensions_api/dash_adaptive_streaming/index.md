---
title: "پخش تطبیقی DASH برای ویدیوی HTML"
slug: Web/API/Media_Source_Extensions_API/DASH_Adaptive_Streaming
page-type: guide
---

{{DefaultAPISidebar("Media Source Extensions")}}

پخش تطبیقی پویا از طریق HTTP (DASH) یک پروتکل پخش تطبیقی است. این بدان معناست که به جریان ویدیو اجازه می‌دهد تا بر اساس عملکرد شبکه، بین نرخ‌های بیت مختلف جابجا شود تا ویدیو به پخش خود ادامه دهد.

ابتدا باید فایل ویدیوی WebM خود را به یک مانیفست DASH به همراه فایل‌های ویدیویی متناظر با نرخ‌های بیت مختلف تبدیل کنید. برای شروع، فقط به برنامه FFmpeg از [ffmpeg.org](https://www.ffmpeg.org/) نیاز دارید که دارای پشتیبانی از libvpx و libvorbis برای ویدیو و صدای WebM باشد، حداقل نسخه 2.5 (احتمالاً؛ این مورد با نسخه 3.2.5 آزمایش شده است).

ابتدا از فایل WebM موجود خود برای ایجاد یک فایل صوتی و چندین فایل ویدیویی استفاده کنید. در مثال زیر، فایل **_in.video_** می‌تواند هر ظرفی باشد که حداقل یک جریان صوتی و یک جریان ویدیویی داشته باشد که توسط FFmpeg قابل رمزگشایی باشد.

فایل صوتی را با استفاده از دستور زیر ایجاد کنید:

```bash
ffmpeg -i in.video -vn -acodec libvorbis -ab 128k -dash 1 my_audio.webm
```

هر نوع ویدیویی را ایجاد کنید.

```bash
ffmpeg -i in.video -c:v libvpx-vp9 -keyint_min 150 -g 150 -tile-columns 4 -frame-parallel 1 -f webm -dash 1 \
-an -vf scale=160:90 -b:v 250k -dash 1 video_160x90_250k.webm
```

```bash
ffmpeg -i in.video -c:v libvpx-vp9 -keyint_min 150 -g 150 -tile-columns 4 -frame-parallel 1  -f webm -dash 1 \
-an -vf scale=320:180 -b:v 500k -dash 1 video_320x180_500k.webm
```

```bash
ffmpeg -i in.video -c:v libvpx-vp9 -keyint_min 150 -g 150 -tile-columns 4 -frame-parallel 1  -f webm -dash 1 \
-an -vf scale=640:360 -b:v 750k -dash 1 video_640x360_750k.webm
```

```bash
ffmpeg -i in.video -c:v libvpx-vp9 -keyint_min 150 -g 150 -tile-columns 4 -frame-parallel 1  -f webm -dash 1 \
-an -vf scale=640:360 -b:v 1000k -dash 1 video_640x360_1000k.webm
```

```bash
ffmpeg -i in.video -c:v libvpx-vp9 -keyint_min 150 -g 150 -tile-columns 4 -frame-parallel 1  -f webm -dash 1 \
-an -vf scale=1280:720 -b:v 1500k -dash 1 video_1280x720_1500k.webm
```

یا می‌توانید همه را در یک دستور انجام دهید.

```bash
ffmpeg -i in.video -c:v libvpx-vp9 -keyint_min 150 \
-g 150 -tile-columns 4 -frame-parallel 1 -f webm -dash 1 \
-an -vf scale=160:90 -b:v 250k -dash 1 video_160x90_250k.webm \
-an -vf scale=320:180 -b:v 500k -dash 1 video_320x180_500k.webm \
-an -vf scale=640:360 -b:v 750k -dash 1 video_640x360_750k.webm \
-an -vf scale=640:360 -b:v 1000k -dash 1 video_640x360_1000k.webm \
-an -vf scale=1280:720 -b:v 1500k -dash 1 video_1280x720_1500k.webm
```

سپس، فایل مانیفست را ایجاد کنید.

```bash
ffmpeg \
  -f webm_dash_manifest -i video_160x90_250k.webm \
  -f webm_dash_manifest -i video_320x180_500k.webm \
  -f webm_dash_manifest -i video_640x360_750k.webm \
  -f webm_dash_manifest -i video_1280x720_1500k.webm \
  -f webm_dash_manifest -i my_audio.webm \
  -c copy \
  -map 0 -map 1 -map 2 -map 3 -map 4 \
  -f webm_dash_manifest \
  -adaptation_sets "id=0,streams=0,1,2,3 id=1,streams=4" \
  my_video_manifest.mpd
```

آرگومان‌های `-map` با فایل‌های ورودی به ترتیبی که داده شده‌اند مطابقت دارند؛ باید برای هر فایل یک مورد داشته باشید. آرگومان `-adaptation_sets` آن‌ها را به مجموعه‌های تطبیقی (adaptation sets) اختصاص می‌دهد؛ به عنوان مثال، این دستور یک مجموعه (0) ایجاد می‌کند که شامل جریان‌های 0، 1، 2 و 3 (ویدیوها) است، و مجموعه دیگری (1) که فقط شامل جریان 4، یعنی جریان صوتی است.

فایل مانیفست و فایل‌های ویدیویی مرتبط را روی سرور وب یا CDN خود قرار دهید. DASH از طریق HTTP کار می‌کند، بنابراین تا زمانی که سرور HTTP شما از درخواست‌های بایت رنج (byte range requests) پشتیبانی می‌کند و برای ارائه فایل‌های `.mpd` با `Content-Type: application/dash+xml` تنظیم شده است، همه چیز آماده است.

سپس، برای اتصال صحیح این فایل `.mpd` به عنصر `<video>` خود، به یک کتابخانه جاوااسکریپتی مانند dash.js نیاز دارید، زیرا هیچ مرورگری به صورت بومی از DASH پشتیبانی نمی‌کند. برای آشنایی با نحوه تنظیم صفحه خود برای استفاده از آن، [راهنمای شروع سریع dash.js](https://dashif.org/dash.js/pages/quickstart/) را مطالعه کنید.

## همچنین ببینید

- [مشخصات WebM DASH در پروژه WebM](https://wiki.webmproject.org/adaptive-streaming/webm-dash-specification)
- [انجمن صنعت DASH](https://dashif.org/)
- [توضیحات پروژه WebM در مورد نحوه ایجاد فایل‌های DASH با FFMPEG](https://wiki.webmproject.org/adaptive-streaming/instructions-to-playback-adaptive-webm-using-dash)