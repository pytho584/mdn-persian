---
title: FileSystemObserver
slug: Web/API/FileSystemObserver
page-type: web-api-interface
status:
  - experimental
  - non-standard
browser-compat: api.FileSystemObserver
---

{{securecontext_header}}{{APIRef("File System API")}}{{SeeCompatTable}}{{non-standard_header}}

接口 **`FileSystemObserver`** 属于 {{domxref("File System API", "File System API", "", "nocode")}}，提供了一种机制来观察用户可见文件系统和[源私有文件系统](/en-US/docs/Web/API/File_System_API/Origin_private_file_system)（OPFS）的变化。这意味着 Web 应用无需轮询文件系统即可发现文件或文件夹结构的变化，从而避免了耗时且浪费资源的操作。

## 构造函数

- {{domxref("FileSystemObserver.FileSystemObserver", "FileSystemObserver()")}} {{Experimental_Inline}} {{non-standard_inline}}
  - : 创建一个新的 `FileSystemObserver` 对象实例。

## 实例方法

- {{domxref("FileSystemObserver.disconnect", "disconnect()")}} {{Experimental_Inline}} {{non-standard_inline}}
  - : 停止观察文件系统。
- {{domxref("FileSystemObserver.observe", "observe()")}} {{Experimental_Inline}} {{non-standard_inline}}
  - : 开始观察指定文件或目录的变化。

## 示例

> [!NOTE]
> 有关完整的可运行示例，请参阅 [File System Observer Demo](https://mdn.github.io/dom-examples/file-system-api/filesystemobserver/)（[源代码](https://github.com/mdn/dom-examples/tree/main/file-system-api/filesystemobserver)）。

### 初始化 `FileSystemObserver`

在开始观察文件或目录变化之前，您需要先初始化一个 `FileSystemObserver` 来处理观察操作。这可以通过 {{domxref("FileSystemObserver.FileSystemObserver", "FileSystemObserver()")}} 构造函数完成，该构造函数接受一个回调函数作为参数：

```js
const observer = new FileSystemObserver(callback);
```

[回调函数](/en-US/docs/Web/API/FileSystemObserver/FileSystemObserver#callback)的主体可以按您的需求定义，以返回并处理文件变化观察记录：

```js
const callback = (records, observer) => {
  for (const record of records) {
    console.log("Change detected:", record);
    const reportContent = `Change observed to ${record.changedHandle.kind} ${record.changedHandle.name}. Type: ${record.type}.`;
    sendReport(reportContent); // Some kind of user-defined reporting function
  }

  observer.disconnect();
};
```

### 观察文件或目录

一旦拥有了 `FileSystemObserver` 实例，您就可以通过调用 {{domxref("FileSystemObserver.observe()")}} 方法来开始观察文件系统条目的变化。

您可以将 {{domxref("FileSystemFileHandle")}} 或 {{domxref("FileSystemDirectoryHandle")}} 传递给 `observe()`，以观察用户可见文件系统或[源私有文件系统](/en-US/docs/Web/API/File_System_API/Origin_private_file_system)（OPFS）中的文件或目录。这些对象的实例可以通过例如 {{domxref("Window.showSaveFilePicker()")}} 或 {{domxref("Window.showDirectoryPicker()")}} 让用户选择文件或目录时获得：

```js
// Observe a file
async function observeFile() {
  const fileHandle = await window.showSaveFilePicker();

  await observer.observe(fileHandle);
}

// Observe a directory
async function observeDirectory() {
  const directoryHandle = await window.showDirectoryPicker();

  await observer.observe(directoryHandle);
}
```

您还可以通过将 {{domxref("FileSystemSyncAccessHandle")}} 传递给 `observe()` 来观察 OPFS 的变化：

```js
// Observe an OPFS file system entry
async function observeOPFSFile() {
  const root = await navigator.storage.getDirectory();
  const draftHandle = await root.getFileHandle("draft.txt", { create: true });
  const syncHandle = await draftHandle.createSyncAccessHandle();

  await observer.observe(syncHandle);
}
```

### 停止观察文件系统

当您想要停止观察文件系统条目的变化时，可以调用 {{domxref("FileSystemObserver.disconnect()")}}：

```js
observer.disconnect();
```

## 规范

目前不属于任何规范的一部分。相关规范 PR 请参见 [https://github.com/whatwg/fs/pull/165](https://github.com/whatwg/fs/pull/165)。

## 浏览器兼容性

{{Compat}}

## 参见

- [File System API](/en-US/docs/Web/API/File_System_API)
- [The File System Observer API origin trial](https://developer.chrome.com/blog/file-system-observer#stop-observing-the-file-system)（developer.chrome.com，2024）