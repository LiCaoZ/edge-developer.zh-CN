---
title: 使用 Microsoft Edge 加载项 API
description: REST 终结点，用于自动将更新发布到提交到 Microsoft Edge 加载项网站的加载项。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 03/17/2022
ms.openlocfilehash: 0dffcd8ceb05c3221587403cc875ad93574328ed
ms.sourcegitcommit: 108b9a0673be978d89bc99d923582f569a43f6fe
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/06/2022
ms.locfileid: "12635309"
---
# <a name="using-the-microsoft-edge-add-ons-api"></a>使用 Microsoft Edge 加载项 API 

Microsoft Edge 加载项 API 提供一组 REST 终结点，用于以编程方式将更新发布到提交到 Microsoft Edge 加载项网站的加载项。  可以使用这些 REST 终结点自动将加载项上载和发布到 Microsoft Edge 加载项网站。  在合作伙伴中心使用 **“发布 API** ”页。

若要提交建议和反馈，请输入 [有关加载项 API 的问题](https://github.com/MicrosoftDocs/edge-developer/issues/new?title=[Add-ons%20API])。


<!-- ====================================================================== -->
## <a name="terminology"></a>术语

| 术语 | 定义 |
|---|---|
| _操作_ | REST 操作，例如 GET 或 PUT。 |
| _操作 ID_ | REST 操作的 ID。 |
| _package_ | `.zip`包含 Microsoft Edge 加载项文件的包。 |
| _产品_ | Microsoft Edge 扩展或主题。  也称为 Microsoft Edge _加载项_。 |
| _产品 ID_ | 需要发布草稿的产品的产品 ID。  产品 ID 是与合作伙伴中心的产品关联的 128 位 GUID。  例如：`d34f98f5-f9b7-42b1-bebb-98707202b21d`。 |
| _提交_ | 正在提交到合作伙伴中心现有产品的更新。  每次更新产品都是提交，无论状态是`In Draft``In Review`，还是`In the Store` (发布的) 。 |


<!-- ====================================================================== -->
## <a name="before-you-begin"></a>在开始之前

若要使用 Microsoft Edge 加载项 API，需要通过创建 API 凭据在 Microsoft 合作伙伴中心为项目启用 API，如下所示：

1. 访问 Microsoft 合作伙伴中心并登录到已从中发布加载项的帐户。

1. 在 **Microsoft Edge** 程序下，选择 **“发布 API**”。

1. 在 **“发布 API** ”页中，单击 **“创建 API 凭据** ”按钮。  此步骤可能需要几分钟时间。

   ![单击“创建 API 凭据”后合作伙伴中心的“发布 API”页，现在显示客户端 ID、客户端机密和身份验证令牌 URL。](../../media/create-api-credentials-button.png)

   现已创建 API 凭据;已启用或续订 API。  **客户端 ID**、**客户端机密**、**到期日期**和**访问令牌 URL** 现在显示在“发布 API”页上。

1. 记下 **客户端 ID**、 **客户端机密** 和 **访问令牌 URL**。  下一步将使用这些值来获取访问令牌。

> [!IMPORTANT]
> 请务必立即记下客户端密码，因为它仅在启用或续订 API (后立即可见，即在创建 API 凭据后) 。


<!-- ====================================================================== -->
## <a name="retrieving-the-access-token"></a>检索访问令牌



获取应用程序所需的授权后，获取 API 的访问令牌。  若要使用客户端凭据授予获取令牌，请将 POST 请求发送到访问令牌 URL (OAuth 令牌) 。  租户信息在上一 **步开始之前** 收到的 URL 中可用。

```rest
Endpoint: https://login.microsoftonline.com/5c9eedce-81bc-42f3-8823-48ba6258b391/oauth2/v2.0/token
Type: POST
Header Parameters: Content-Type: application/x-www-form-urlencoded
```

### <a name="sample-request"></a>示例请求

```console
> curl \
-X POST \
-H "Content-Type: application/x-www-form-urlencoded" \
-d "client_id={$Client_ID}" \
-d "scope=https://api.addons.microsoftedge.microsoft.com/.default" \
-d "client_secret={$Client_Secret}" \
-d "grant_type=client_credentials" \
-v \
https://login.microsoftonline.com/5c9eedce-81bc-42f3-8823-48ba6258b391/oauth2/v2.0/token
```

### <a name="sample-response"></a>示例响应

```json
{
  "token_type": "Bearer",
  "expires_in": 3599,
  "access_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsIng1dCI6Ik1uQ19WWmNBVGZNNXBP..."
}
```

有关详细信息，请参阅 [Microsoft 标识平台 上的 OAuth 2.0 客户端凭据流](/azure/active-directory/develop/v2-oauth2-client-creds-grant-flow#get-a-token)。


<!-- ====================================================================== -->
## <a name="using-the-api-endpoints"></a>使用 API 终结点

获得访问令牌后，可以使用 Microsoft Edge 加载项 API。  此 API 公开用于获取产品列表、更新产品和发布产品的终结点。

> [!NOTE]
> 没有用于创建新产品或更新产品的元数据的 API，例如说明。  必须在 Microsoft 合作伙伴中心手动完成这些任务。

API 在终结点可用 `https://api.addons.microsoftedge.microsoft.com`


<!-- ====================================================================== -->
## <a name="uploading-a-package-to-update-an-existing-submission"></a>上传包以更新现有提交

使用此 API 更新加载项的包。  此 API 上传一个包以更新加载项产品的现有草稿提交。

```rest
Endpoint: /v1/products/$productID/submissions/draft/package
Type: POST
Header Parameters: Authorization: Bearer $TOKEN; Content-Type: application/zip
Body content: the package file to upload
```

`$productID` 是要更新的 Microsoft Edge 加载项的产品 ID。 

若要获取产品 ID，请执行以下操作：

1. 登录到 Microsoft 合作伙伴中心。

1. 转到 **Microsoft Edge** > **概述**。

1. 选择要为其提供产品 ID 的扩展。

   **“扩展概述**”页随即打开。  产品 ID 显示在页面中。   (产品 ID 在地址栏`microsoftedge/``/packages`和 .) 之间的 URL 中也显示为 GUID
 
1. 在 **“扩展标识** ”部分 (或从地址栏) 中，选择并复制 **产品 ID**。

### <a name="sample-request"></a>示例请求

```console
> curl \
-H "Authorization: Bearer $TOKEN" \
-H "Content-Type: application/zip" \
-X POST \
-T $FILE_NAME \
-v \
https://api.addons.microsoftedge.microsoft.com/v1/products/$productID/submissions/draft/package
```

如果请求成功且更新过程开始，则会收到带有 `202 Accepted` 标头的 `Location` 响应状态代码。  此位置标头包含 `operationID` 检查更新操作状态所需的标头。

### <a name="see-also"></a>另请参阅

*  API 参考： [上传包以更新现有提交](addons-api-reference.md#upload-a-package-to-update-an-existing-submission)


<!-- ====================================================================== -->
## <a name="checking-the-status-of-a-package-upload"></a>检查包上传的状态

使用此 API 检查包上传的状态。

```rest
Endpoint: /v1/products/$productID/submissions/draft/package/operations/$operationID
Type: GET
Header Parameters: Authorization: Bearer $TOKEN
```

### <a name="sample-request"></a>示例请求

```console
> curl \
-H "Authorization: Bearer $TOKEN" \
-X GET \
-v \
https://api.addons.microsoftedge.microsoft.com/v1/products/$productID/submissions/draft/package/operations/$operationID
```

### <a name="see-also"></a>另请参阅

*  API 参考： [检查包上传的状态](addons-api-reference.md#check-the-status-of-a-package-upload)


<!-- ====================================================================== -->
## <a name="publishing-the-submission"></a>发布提交

使用此 API 将产品当前草稿发布到 Microsoft Edge 加载项网站。

```rest
Endpoint: /v1/products/$productID/submissions
Type: POST
Header Parameters: Authorization: Bearer $TOKEN
Body content: Notes for certification, in JSON format
```

### <a name="sample-request"></a>示例请求

```console
> curl \
-H "Authorization: Bearer $TOKEN" \
-X POST \
-d '{ "notes"="text value" }' \
-v \
https://api.addons.microsoftedge.microsoft.com/v1/products/$productID/submissions
```

如果请求成功且发布过程开始，则会收到带有 `202 Accepted` 标头的 `Location` 响应状态代码。  此位置标头包含 `operationID` 检查发布操作状态所需的标头。

### <a name="see-also"></a>另请参阅

*  API 参考： [发布产品草稿提交](addons-api-reference.md#publish-the-product-draft-submission)


<!-- ====================================================================== -->
## <a name="checking-the-publishing-status"></a>检查发布状态

使用此 API 检查发布操作的状态。

```rest
Endpoint: /v1/products/$productID/submissions/operations/$operationID
Type: GET
Header Parameters: Authorization: Bearer $TOKEN
```

### <a name="sample-request"></a>示例请求

```console
> curl \
-H "Authorization: Bearer $TOKEN" \
-X GET \
-v \
https://api.addons.microsoftedge.microsoft.com/v1/products/$productID/submissions/operations/{operationID}
```

### <a name="see-also"></a>另请参阅

*  [使用 Microsoft Edge 加载项 API：检查发布状态](addons-api-reference.md#check-the-publishing-status)
