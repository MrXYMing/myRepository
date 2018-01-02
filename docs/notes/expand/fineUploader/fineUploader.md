#### API

#### 一、 Options

#### 1. CORE

##### 1.1 Core

|Name                         |Type              |默认值    |描述                         |
|:---                         |:----             |:----    |:----                        |
|autoUpload                   |Boolean           |true     |如果您希望稍后可以通过调用uploadStoredFiles（）方法来上传排队的项目，则设置为false。|
|button                       |HTMLElement       |null     |指定一个要用作“选择文件”按钮的元素。 不能是<button>。|
|debug                        |Boolean           |false    |这将导致日志消息被写入到window.console对象中|
|disableCancelForFormUploads  |Boolean           |false    |当使用表单上传器时，取消链接不会出现在文件旁边|
|formatFileName               |Function          |         |提供一个控制文件名显示的功能。 原始文件名被调用时被传递到函数中。 您的函数可能会返回一个修改的文件名。 请注意，这不会影响实际的文件名，只会显示文件名|
|maxConnections               |Integer           |3        |最大允许的并发请求|
|multiple                     |Boolean           |true     |如果为false，则会阻止用户同时选择或删除多个项目|

##### 1.2 blobs

|Name         |Type     |默认值               |描述                   |
|:---         |:----    |:----               |:----                 |
|defaultName  |String   |Misc data（杂项数据）|用于无名Blob的默认名称。|

##### 1.3 camera

|Name         |Type          |默认值  |描述                   |
|:---         |:----         |:----   |:----                 |
|button       |HTMLElement   |null    | null允许在iOS的默认按钮上访问摄像头。 否则提供一个额外的按钮容器元素来定位|
|ios          |Boolean       |false   | 在iOS（iPod，iPhone和iPad）设备上启用或禁用摄像头访问。 注意：启用此选项将禁用多个文件选择|


---

#### 2. UI

Fine Uploader UI模式有几个不同的选项，以及一些专门针对核心模式不具备的UI的选项。

Core模式中存在的任何选项也都以UI模式存在，并且在大多数情况下可以被覆盖

##### 2.1 UI

|Name         |Type          |默认值  |描述                   |
|:---         |:----         |:----   |:----                 |
|element      |HTMLElement   |null    | 默认放置区域的容器元素|
|listElement  |HTMLElement   |null    | 项目列表的容器元素|
|multiple     |Boolean       |true    | 如果为false，则会阻止用户同时选择或删除多个项目。 删除或选择其他项目将清除上传列表。 如果另一个已经上传，它将被取消。 要忽略而不是取消，只需在“验证”或“提交”事件处理程序中返回false即可|


---
#### 三、Events

#### 1. CORE & UI
Fine Uploader的事件系统使集成商可以在上传过程中的任何时刻执行任何操作。

##### 1.1 Syntax
```
callbacks: {
    onDelete: function(id) {
        // ...
    },
    onDeleteComplete: function(id, xhr, isError) {
        //...
    }
}
```

- **onAutoRetry**: 在每次失败项目的自动重试尝试之前调用
    1. id：当前文件的ID - `integer`；
    2. name：当前文件的名称 - `string`；
    3. attemptNumber：到目前为止，当前文件的重试次数 - `integer`。

- **onCancel**：当上传被取消时调用。 返回false以防止上传被取消。 如果在这里需要非阻塞的工作，也可以返回一个承诺。 在promise上调用`failure()`就等于返回false。 如果使用Promise，则取消请求的处理将被推迟，直到完成承诺。 由于在等待承诺完成时没有办法“暂停”正在进行的上传，所以上传可能实际上完成，直到承诺实际上已经满载
    1. id：当前文件的ID - `integer`；
    2. name：当前文件的名称 - `string`；

- **onComplete**：当完成上传时调用。`responseJSON`将包含来自服务器的原始响应，包括指示上传是否成功的“success”属性
    1. id：当前文件的ID - `integer`；
    2. name：当前文件的名称 - `string`；
    3. responseJSON：来自服务器的原始响应 - `object`；
    4. xhr：用于发出请求的对象 - `XMLHttpRequest or XDomainRequest`

- **onAllComplete**：当所有提交的项目已达到终止点时调用。 如果文件已被取消，拒绝或上传（失败或成功），则文件已达到终止点。 例如，如果组中的文件已暂停，并且组中的所有其他文件已成功上载，则不会为该组调用allComplete事件，直到该暂停文件被继续并完成上载过程或取消为止。 如果组中的所有文件都被取消或被拒绝，则不会调用此事件（即，如果没有任何文件达到qq.status.UPLOAD_SUCCESSFUL或qq.status.UPLOAD_FAILED的状态）
    1. succeeded：成功上传的组中所有文件的标识（status = `qq.status.UPLOAD_SUCCESSFUL`）- `Array`；
    2. failed：组中所有失败的文件的标识（status = `qq.status.UPLOAD_FAILED`）- `Array`。

- **onDelete**：在关联项目发送删除请求之前调用。 请注意，这不是影响删除请求的正确回调。 要做到这一点，请使用onSubmitDelete回调
    1. id：当前文件的ID - `integer`；

- **onDeleteComplete**：从服务器接收到删除文件请求的响应之后立即调用
    1. id：当前文件的ID - `integer`；
    2. xhr：用于发出请求的对象 - `XMLHttpRequest or XDomainRequest`；
    3. isError：如果发生错误，则返回true，否则返回false - `Boolean`。

- **onError**：在出现异常情况时调用（请参阅处理错误）
    1. id：当前文件的ID - `integer`；
    2. name：当前文件的名称 - `string`；
    3. errorReason：当前错误的原因 - `string`；
    4. xhr：用于发出请求的对象 - `XMLHttpRequest or XDomainRequest`；

    *处理错误：Fine Uploader有很多方式来回应错误信息。 默认情况下，当服务器响应没有将成功的密钥设置为true时，Fine Uploader会出现错误。 如果发生任何错误，则会调用onError回调*

- **onManualRetry**：在每次手动重试尝试之前调用。返回false以防止这个和所有将来的重试尝试在关联的项目上
    1. id：当前文件的ID - `integer`；
    2. name：当前文件的名称 - `string`；

- **onPasteReceived**：在接收到粘贴的图像时（在上传之前）调用。被粘贴的图像被表示为Blob。 如果在这里需要非阻塞的工作，也可以返回一个承诺。 如果使用Promise，成功参数的值必须是与粘贴图像关联的名称。 如果关联的尝试被标记为失败，那么您应该在Promise的失败回调中包含一个字符串来解释原因。**注意**：promptForName选项（如果为true）将有效地清除此回调的任何自定义实现。 这两个并不意味着一起使用。 此回调旨在提供一种替代方法来为粘贴的图像提供名称。 如果您正在使用Fine Uploader Core模式，则可以通过覆盖此回调的默认实现来显示自己的名称提示
    1. blob：封装从剪贴板粘贴的图像的对象 - `Blob`。

- **onProgress**：在上传过程中调用，但仅限于AJAX上传器。对于分块上传，这将被称为每个块。用于实施进度条。
    1. id：当前文件的ID - `integer`；
    2. name：当前文件的名称 - `string`；
    3. uploadedBytes：到目前为止上传的字节数 - `integer`；
    4. totalBytes：构成这个文件的总字节数 - `integer`。

- **onResume**：在恢复上传之前调用。 有关chunkData对象的更多信息，请参阅uploadChunk事件
    1. id：当前文件的ID - `integer`；
    2. name：当前文件的名称 - `string`；
    3. chunkData：当文件上传恢复时，下一个将发送的块 - `object`。

- **onSessionRequestComplete**：会话请求完成时调用。 响应将是包含响应数据的数组，如果响应中不包含有效的JSON，则返回null。 如果在响应中表示的任何文件项无法解析（由于语法错误，缺少名称/ UUID属性等），success参数将为false。请参阅初始文件列表功能页面了解更多详情
    1. response：原始响应数据 - `Array`；
    2. success：表示是否成功 - `Boolean`；
    3. xhrOrXdr：原始请求 - `XMLHttpRequest or XDomainRequest`。

- **onStatusChange**：当上传器提交的任何项目的状态发生变化时调用。状态值对应于qq.status对象中的状态值。 以供参考
    - SUBMITTED
    - QUEUED
    - UPLOADING
    - UPLOAD_RETRYING
    - UPLOAD_FAILED
    - UPLOAD_SUCCESSFUL
    - CANCELED
    - REJECTED
    - DELETED
    - DELETING
    - DELETE_FAILED
    - PAUSED

    1. id：当前文件的ID - `integer`；
    2. oldStatus：以前的项目状态 - `string`；
    3. newStatus：该项目的新状态 - `string`。

- **onSubmit**：当该项目被选中并且是上传的候选人时调用。这并不意味着该项目将被上传。 返回false以防止提交给上传者。 如果需要无阻塞的工作，可以使用promise。 这个项目的处理被推迟到promise完成。 如果一个promise被返回，一个失败的调用和返回false是一样的
    1. id：当前文件的ID - `integer`；
    2. name：当前文件的名称 - `string`；

- **onSubmitDelete**：在项目被标记为删除之前调用已经提交给上传者。如果需要无阻塞的工作，可以使用承诺。 这个项目的处理被推迟到承诺完成。 如果一个承诺被返回，一个失败的调用和返回false是一样的。使用此回调影响删除请求。 例如，您可以使用setDeleteParams API方法更改使用基础删除请求发送的自定义参数
    1. id：当前文件的ID - `integer`；

- **onSubmitted**：当项目成功提交给上传者时调用。如果有至少一个空闲连接（参见：maxConnections选项），并且b）autoUpload设置为true（请参阅autoUpload选项），则该文件将立即上载。当项目成功提交给上传者时调用。在处理“提交”事件之后调用回调而不返回错误的值。 在Fine Uploader Core模式中，通常可以安全地假定在调用此回调之前，UI中表示关联文件的关联元素已经被添加到DOM中。
    1. id：当前文件的ID - `integer`；
    2. name：当前文件的名称 - `string`；

- **onTotalProgress**：在一批上传过程中调用，但仅限于AJAX上传器。 这表示批处理中所有文件的总进度。用于实现一个聚合进度条
    1. totalUploadedBytes：到目前为止在这批中上传的字节数 - `integer`。
    2. totalBytes：包含批处理中所有文件的总字节数 - `integer`。

- **onUpload**：在项目开始上传到服务器之前调用。
    1. id：当前文件的ID - `integer`；
    2. name：当前文件的名称 - `string`；

- **onUploadChunk**：在块请求发送之前调用。传递到“uploadChunk”事件处理程序的chunkData对象具有4个属性：
    - partIndex - 关联分区的从0开始的索引。
    - startByte - 当前块的字节偏移量。
    - endByte - 当前块的最后一个字节。
    - totalParts - 与File或Blob关联的分区总数。

    1. id：当前文件的ID - `integer`；
    2. name：当前文件的名称 - `string`；
    3. chunkData：封装当前要上传的数据块的对象 - `object`。

- **onUploadChunkSuccess**：这与完整的事件类似，除了在每个块成功上传后调用。有关chunkData对象的更多信息，请参阅uploadChunk事件
    1. id：当前文件的ID - `integer`；
    2. chunkData：封装当前要上传的数据块的对象 - `object`；
    3. responseJSON：来自服务器的原始响应 - `object`；
    4. xhr：用于发出请求的对象 - `XMLHttpRequest or XDomainRequest`

- **onValidate**：为每个选中，删除或添加文件提交的文件调用一次。此回调总是在默认的Fine Uploader验证器执行之前调用。如果在validateBatch事件处理程序中返回false，或者stopOnFirstInvalidFile验证选项为true，并且验证事件处理程序已为项目返回false，则不会调用此事件。如果需要无阻塞的工作，可以使用承诺。 这个项目的处理被推迟到承诺完成。 如果一个承诺被返回，一个失败的调用和返回false是一样的。一个buttonContainer元素将被作为最后一个参数传递，只要该文件是使用Fine Uploader跟踪的按钮提交的。blobData对象有两个属性：名称和大小。 对于没有File API支持的浏览器，size属性将是未定义的
    1. data：具有名称和大小属性的对象 - `object`。
    2. buttonContainer：如果使用追踪按钮将文件提交给Fine Uploader，则该按钮对应于相应的文件 - `HTMLElement`。

- **onValidateBatch**：此回调总是在默认的Fine Uploader验证器执行之前调用。如果在validateBatch事件处理程序中返回false，或者stopOnFirstInvalidFile验证选项为true，并且验证事件处理程序已为项目返回false，则不会调用此事件。如果需要无阻塞的工作，可以使用承诺。 这个项目的处理被推迟到承诺完成。 如果一个承诺被返回，一个失败的调用和返回false是一样的。一个buttonContainer元素将被作为最后一个参数传递，只要该文件是使用Fine Uploader跟踪的按钮提交的。fileOrBlobDataArray对象有两个属性：名称和大小。 对于没有File API支持的浏览器，size属性将是未定义的
    1. fileOrBlobDataArray：具有名称和大小属性的对象数组 - `Array`；
    2. buttonContainer：如果使用追踪按钮将文件提交给Fine Uploader，则该按钮对应于相应的文件 - `HTMLElement`。