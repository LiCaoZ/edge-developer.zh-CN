---
description: REST 终结点，用于自动发布提交到加载项网站的Microsoft Edge更新。
title: 使用Microsoft Edge加载项 API
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 08/19/2021
ms.topic: conceptual
ms.prod: microsoft-edge
keywords: edge-chromium， 扩展开发， 浏览器扩展， 加载项， 合作伙伴中心， 开发人员， 加载项 api， 发布 api
ms.openlocfilehash: d43ccbd44d9d66b6c00250d1fd2e504187d6dc87
ms.sourcegitcommit: b0604ac0d43cef4df04256bed3a375febc45d1a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2021
ms.locfileid: "12156520"
---
# <a name="using-the-microsoft-edge-add-ons-api-under-development"></a>使用Microsoft Edge加载项 API (开发) 

> [!NOTE]
> 本文是一个请求注释。  Microsoft Edge加载项 API 尚无法进行测试，并且合作伙伴中心尚未提供"发布 API"页。  加载项MICROSOFT EDGE API 正在积极开发中，路线图根据市场变化和客户反馈不断发展。  此处列出的计划并不详尽，可能会发生变化。

本文与 Microsoft Edge[加载项 API](addons-api-reference.md)参考一起概述了建议Microsoft Edge加载项 API。  我们期待就建议的 API 合同提供建议和反馈。  请将你的反馈作为有关 [加载项 API 的问题提交](https://github.com/MicrosoftDocs/edge-developer/issues/new?title=[Add-ons%20API])。

加载项MICROSOFT EDGE API 提供了一组 REST 终结点，用于以编程方式发布提交到 Microsoft Edge 加载项网站的加载项更新。  可以使用这些 REST 终结点自动执行将加载项上载和发布到加载项Microsoft Edge的过程。


<!-- ====================================================================== -->
## <a name="terminology"></a>术语

| 术语 | 定义 |
|---|---|
| _operation_ | REST 操作，如 GET 或 PUT。 |
| _操作 ID_ | REST 操作 ID。 |
| _package_ | `.zip`包含加载项Microsoft Edge包。 |
| _product_ | 一Microsoft Edge扩展或主题。  也称为加载项Microsoft Edge_加载项_。 |
| _产品 ID_ | 需要发布其草稿的产品的产品 ID。  产品 ID 是一个 128 位 GUID，与合作伙伴中心的产品相关联。  例如：`d34f98f5-f9b7-42b1-bebb-98707202b21d`。 |
| _提交_ | 要提交到合作伙伴中心的现有产品的更新。  产品每次更新都是提交，无论状态是 、还是 (`In Draft` `In Review` `In the Store` 已发布) 。 |


<!-- ====================================================================== -->
## <a name="before-you-begin"></a>在开始之前

若要使用Microsoft Edge加载项 API，你需要在 Microsoft 合作伙伴中心中为项目启用 API。

> [!NOTE]
> 发布 **API** UI 在合作伙伴中心尚不存在。

1. 访问 Microsoft 合作伙伴中心并登录到已发布加载项的帐户。

1. 在 **"Microsoft Edge**程序"下，选择"**发布 API"。**

1. 在 **"发布 API"** 页中，选择" **创建 API 凭据"** 按钮以生成 API 凭据。  此步骤可能需要几分钟时间。  启用 API 后，客户端**ID、****客户端密码**和身份验证令牌**URL**会显示在此页面上。

1. 请注意**ClientID、Client** **Secret**和**Auth Token URL。**  你将在下一步中使用它们获取访问令牌。


<!-- ====================================================================== -->
## <a name="retrieving-the-access-token"></a>检索访问令牌

> [!NOTE]
> 尚未Microsoft Edge加载项 API 进行测试。

获取应用程序的必要授权后，获取 API 的访问令牌。  若要使用客户端凭据授予获取令牌，请将 POST 请求发送到身份验证令牌 URL。  租户信息在以上开始步骤之前收到的 URL **中提供** 。

```rest
Endpoint: https://login.microsoftonline.com/{tenant}/oauth2/v2.0/token
Type: POST
Header Parameters: Content-Type: application/x-www-form-urlencoded
```

### <a name="sample-request"></a>示例请求

```console
> curl \
-X POST \
-H "Content-Type: application/x-www-form-urlencoded" \
-d "client_id={$Client_ID}" \
-d "scope=https://addons.edge.microsoft.com/.default" \
-d "client_secret={$Client_Secret}" \
-d "grant_type=client_credentials" \
-v \
https://login.microsoftonline.com/{tenant}/oauth2/v2.0/token
```

### <a name="sample-response"></a>示例响应

```json
{
  "token_type": "Bearer",
  "expires_in": 3599,
  "access_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsIng1dCI6Ik1uQ19WWmNBVGZNNXBP..."
}
```

有关详细信息，请导航到[OAuth 2.0 客户端凭据流。Microsoft 标识平台。](/azure/active-directory/develop/v2-oauth2-client-creds-grant-flow#get-a-token)


<!-- ====================================================================== -->
## <a name="using-the-api-endpoints"></a>使用 API 终结点

获取访问令牌后，可以使用 Microsoft Edge 加载项 API。  此 API 公开用于获取产品列表、更新产品和发布产品的终结点。

> [!NOTE]
> 没有用于创建新产品或更新产品元数据（如说明）的 API。  你必须在 Microsoft 合作伙伴中心手动完成这些任务。

以下示例使用域 ，它是占位符，当 API 在生产中可用 `https://addons.edge.microsoft.com/api` 时可能会替换。


<!-- ====================================================================== -->
## <a name="uploading-a-package-to-update-an-existing-submission"></a>上载程序包以更新现有提交

使用此 API 更新加载项包。  此 API 上载程序包以更新加载项产品的现有草稿提交。

```rest
Endpoint: /v1/products/$productID/submissions/draft/package
Type: PUT
Header Parameters: Authorization: Bearer $TOKEN; Content-Type: application/zip
Body content: the package file to upload
```

`$productID` 是你想要Microsoft Edge加载项的 ID。  可以通过以下任一方式获取产品 ID：

*  登录到 Microsoft 合作伙伴中心。  导航到**Microsoft Edge >** 概述"，然后选择想要其产品 ID 的扩展。  扩展概述页面将打开。  URL 中的 GUID 是产品 ID。

*  调用 `/products` API 获取所有产品及其产品 ID 的列表。  有关 API 详细信息 `/products` ，请导航到"[获取产品列表"。](addons-api-reference.md#get-the-list-of-products)

### <a name="sample-request"></a>示例请求

```console
> curl \
-H "Authorization: Bearer $TOKEN" \
-H "Content-Type: application/zip" \
-X PUT \
-T $FILE_NAME \
-v \
https://addons.edge.microsoft.com/api/v1/products/$productID/submissions/draft/package
```

如果请求成功并且更新过程开始，您将收到一个包含标头 `202 Accepted` 的响应状态 `Location` 代码。  若要了解操作的状态，请 `GET` 对 标头中的 URL 提出 `Location` 请求。

API 参考[：Upload包以更新现有提交](addons-api-reference.md#upload-a-package-to-update-an-existing-submission)


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
https://addons.edge.microsoft.com/api/v1/products/$productID/submissions/draft/package/operations/$operationID
```

API 参考 [：检查程序包上载的状态](addons-api-reference.md#check-the-status-of-a-package-upload)


<!-- ====================================================================== -->
## <a name="publishing-the-submission"></a>发布提交

使用此 API 将产品的当前草稿发布到 Microsoft Edge 加载项网站。

```rest
Endpoint: /v1/products/$productID/submissions
Type: POST
Header Parameters: Authorization: Bearer $TOKEN
Body content: Notes for certification, in plain text format
```

### <a name="sample-request"></a>示例请求

```console
> curl \
-H "Authorization: Bearer $TOKEN" \
-X POST \
-d "certificationNotes=text value" \
-v \
https://addons.edge.microsoft.com/api/v1/products/$productID/submissions
```

如果请求成功且发布过程开始，您将收到一个包含标头 `202 Accepted` 的响应状态 `Location` 代码。   若要了解操作的状态，请 `GET` 对 标头中的 URL 提出 `Location` 请求。

API 参考 [：发布产品草稿提交](addons-api-reference.md#publish-the-product-draft-submission)


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
-v \ https://addons.edge.microsoft.com/api/v1/products/$productID/submissions/operations/{operationID}
```

API 参考 [：检查发布状态](addons-api-reference.md#check-the-publishing-status)
