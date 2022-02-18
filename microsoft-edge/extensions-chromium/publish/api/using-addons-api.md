---
title: 使用 Microsoft Edge 外接程序 API (在个人预览版中)
description: REST 终结点，用于自动发布提交到加载项网站的加载项Microsoft Edge更新。
author: MSEdgeTeam
ms.author: msedgedevrel
ms.topic: conceptual
ms.prod: microsoft-edge
ms.date: 08/19/2021
ms.openlocfilehash: 4603e40aa8736caf94f5542b9b9757d32b157bd6
ms.sourcegitcommit: 9196a557626d92bd22cec4a604e9107ec2bfe709
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/18/2022
ms.locfileid: "12351054"
---
# <a name="using-the-microsoft-edge-add-ons-api-in-private-preview"></a>使用 Microsoft Edge 外接程序 API (在个人预览版中)

> [!NOTE]
> Microsoft Edge加载项 API 目前处于个人预览阶段。  " **发布 API** "页仅对私人预览版的参与者在合作伙伴中心显示。  加载项MICROSOFT EDGE API 正在积极开发中，路线图根据市场变化和客户反馈不断发展。  此处列出的计划并不详尽，可能会发生变化。

本文与 Microsoft Edge [加载项 API](addons-api-reference.md) 参考一起概述了建议Microsoft Edge加载项 API。  我们期待就建议的 API 合同提供建议和反馈。  请将你的反馈作为有关 [加载项 API 的问题提交](https://github.com/MicrosoftDocs/edge-developer/issues/new?title=[Add-ons%20API])。

加载项MICROSOFT EDGE API 提供了一组 REST 终结点，用于以编程方式发布提交到 Microsoft Edge 加载项网站的加载项更新。  可以使用这些 REST 终结点自动执行将加载项上载和发布到加载项Microsoft Edge的过程。


<!-- ====================================================================== -->
## <a name="terminology"></a>术语

| 术语 | 定义 |
|---|---|
| _operation_ | REST 操作，如 GET 或 PUT。 |
| _操作 ID_ | REST 操作 ID。 |
| _package_ | 包含`.zip`加载项Microsoft Edge包。 |
| _product_ | 一Microsoft Edge扩展或主题。  也称为加载项Microsoft Edge_加载项_。 |
| _产品 ID_ | 需要发布其草稿的产品的产品 ID。  产品 ID 是一个 128 位 GUID，与合作伙伴中心的产品相关联。  例如：`d34f98f5-f9b7-42b1-bebb-98707202b21d`。 |
| _提交_ | 要提交到合作伙伴中心的现有产品的更新。  产品每次更新都是提交`In Draft``In Review``In the Store`，无论状态是 、还是 (已发布) 。 |


<!-- ====================================================================== -->
## <a name="before-you-begin"></a>在开始之前

若要使用Microsoft Edge加载项 API，需要在 Microsoft 合作伙伴中心通过创建 API 凭据为项目启用 API。

> [!NOTE]
> " **发布 API** "页仅对私人预览版的参与者在合作伙伴中心显示。

1. 访问 Microsoft 合作伙伴中心并登录到已发布加载项的帐户。

1. 在 **"Microsoft Edge**"下，选择"**发布 API"**。

1. 在" **发布 API** "页中，单击" **创建 API 凭据"** 按钮。  此步骤可能需要几分钟。

   :::image type="content" source="../../media/create-api-credentials-button.png" alt-text="单击&quot;创建 API 凭据&quot;后合作伙伴中心的&quot;发布 API&quot;页面，现在显示客户端 ID、客户端密码和身份验证令牌 URL。" lightbox="../../media/create-api-credentials-button.png":::

   API 凭据现已创建;你已启用或续订了 API。  客户端 **ID**、**客户端密码**、到期日期**** 和**访问令牌 URL** 现在显示在"发布 API"页上。

1. 记下客户端 **ID**、 **客户端密码** 和 **访问令牌 URL**。  你将在下一步使用这些值，获取访问令牌。

> [!IMPORTANT]
> 请务必立即记下客户端密码，因为它仅在启用或续订 API 密码后（即 (API 凭据后立即) 。


<!-- ====================================================================== -->
## <a name="retrieving-the-access-token"></a>检索访问令牌

> [!NOTE]
> 当前Microsoft Edge预览版参与者可以使用加载项 API。


获取应用程序的必要授权后，获取 API 的访问令牌。  若要使用客户端凭据授予获取令牌，请将 POST 请求发送到 OAuth 令牌 (访问令牌 URL) 。  租户信息在以上开始步骤之前收到的 **URL 中提供** 。

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

有关详细信息，请参阅 [OAuth 2.0 客户端凭据流Microsoft 标识平台](/azure/active-directory/develop/v2-oauth2-client-creds-grant-flow#get-a-token)。


<!-- ====================================================================== -->
## <a name="using-the-api-endpoints"></a>使用 API 终结点

获取访问令牌后，可以使用 Microsoft Edge 加载项 API。  此 API 公开用于获取产品列表、更新产品和发布产品的终结点。

> [!NOTE]
> 没有用于创建新产品或更新产品元数据（如说明）的 API。  你必须在 Microsoft 合作伙伴中心手动完成这些任务。

API 在终结点上可用 https://api.addons.microsoftedge.microsoft.com


<!-- ====================================================================== -->
## <a name="uploading-a-package-to-update-an-existing-submission"></a>上载程序包以更新现有提交

使用此 API 更新加载项包。  此 API 上载程序包以更新加载项产品的现有草稿提交。

```rest
Endpoint: /v1/products/$productID/submissions/draft/package
Type: POST
Header Parameters: Authorization: Bearer $TOKEN; Content-Type: application/zip
Body content: the package file to upload
```

`$productID` 是你想要更新Microsoft Edge加载项的产品 ID。 

若要获取产品 ID，

1. 登录到 Microsoft 合作伙伴中心。

1. 转到 **Microsoft Edge** >  **Overview**。

1. 选择想要其产品 ID 的扩展。

   将 **打开"扩展概述** "页。  产品 ID 显示在页面中。   (产品 ID 还会在地址栏中的 URL `microsoftedge/` `/packages`中显示为 GUID，介于 和 .) 
 
1. 在" **扩展标识** "部分 (地址栏) ，选择并复制 **产品 ID**。

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

如果请求成功并且更新过程开始，您将收到一 `202 Accepted` 个包含标头的响应状态 `Location` 代码。  此位置标头 `operationID` 包含检查更新操作状态所需的 。

### <a name="see-also"></a>另请参阅

*  API 参考[：Upload包以更新现有提交](addons-api-reference.md#upload-a-package-to-update-an-existing-submission)


<!-- ====================================================================== -->
## <a name="checking-the-status-of-a-package-upload"></a>检查程序包上载的状态

使用此 API 检查程序包上载的状态。

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

*  API 参考 [：检查程序包上载的状态](addons-api-reference.md#check-the-status-of-a-package-upload)


<!-- ====================================================================== -->
## <a name="publishing-the-submission"></a>发布提交

使用此 API 将产品的当前草稿发布到Microsoft Edge加载项网站。

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

如果请求成功并且发布过程开始，您将收到一 `202 Accepted` 个包含标头的响应状态 `Location` 代码。  此位置标头 `operationID` 包含检查发布操作的状态所需的 。

### <a name="see-also"></a>另请参阅

*  API 参考 [：发布产品草稿提交](addons-api-reference.md#publish-the-product-draft-submission)


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

*  API 参考 [：检查发布状态](addons-api-reference.md#check-the-publishing-status)
