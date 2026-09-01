---
title: "FileSystemSyncAccessHandle: close() method"
short-title: close()
slug: Web/API/FileSystemSyncAccessHandle/close
page-type: web-api-instance-method
browser-compat: api.FileSystemSyncAccessHandle.close
---

{{securecontext_header}}{{APIRef("File System API")}}{{AvailableInWorkers("dedicated")}}

**`close()`** 属于 {{domxref("FileSystemSyncAccessHandle")}} 接口的方法，用于关闭一个已打开的同步文件句柄，使其无法再执行任何后续操作，并释放与该文件句柄相关联的文件上的独占锁。

> [!NOTE]
> 在早期版本的规范中，`close()`、{{domxref("FileSystemSyncAccessHandle.flush()", "flush()")}}、{{domxref("FileSystemSyncAccessHandle.getSize()", "getSize()")}} 和 {{domxref("FileSystemSyncAccessHandle.truncate()", "truncate()")}} 被错误地规定为异步方法；一些旧版本浏览器也正是以异步方式实现它们的。不过，目前所有支持这些方法的浏览器都将它们实现为同步方法。

## 语法

```js-nolint
close()
```

### 参数

无。

### 返回值

无（{{jsxref('undefined')}}）。

### 异常

无。

## 示例

以下异步事件处理函数位于 Web Worker 内部。当收到来自主线程的消息时，它会执行以下操作：

- 创建一个同步文件访问句柄。
- 获取文件大小并创建一个 {{jsxref("ArrayBuffer")}} 来容纳文件内容。
- 将文件内容读入缓冲区。
- 对消息进行编码并写入文件末尾。
- 将更改持久化到磁盘，并关闭访问句柄。

```js
onmessage = async (e) => {
  // Retrieve message sent to work from main script
  const message = e.data;

  // Get handle to draft file
  const root = await navigator.storage.getDirectory();
  const draftHandle = await root.getFileHandle("draft.txt", { create: true });
  // Get sync access handle
  const accessHandle = await draftHandle.createSyncAccessHandle();

  // Get size of the file.
  const fileSize = accessHandle.getSize();
  // Read file content to a buffer.
  const buffer = new DataView(new ArrayBuffer(fileSize));
  const readBuffer = accessHandle.read(buffer, { at: 0 });

  // Write the message to the end of the file.
  const encoder = new TextEncoder();
  const encodedMessage = encoder.encode(message);
  const writeBuffer = accessHandle.write(encodedMessage, { at: readBuffer });

  // Persist changes to disk.
  accessHandle.flush();

  // Always close FileSystemSyncAccessHandle if done.
  accessHandle.close();
};
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- [File System API](/en-US/docs/Web/API/File_System_API)
- [The File System Access API: simplifying access to local files](https://developer.chrome.com/docs/capabilities/web-apis/file-system-access)