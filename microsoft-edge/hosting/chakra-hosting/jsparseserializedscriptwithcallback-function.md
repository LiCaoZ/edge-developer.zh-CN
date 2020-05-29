---
description: 分析序列化脚本并返回表示脚本的函数。 仅当需要时，才提供延迟加载脚本源的功能。
title: JsParseSerializedScriptWithCallback 函数 |Microsoft 文档
ms.custom: ''
ms.date: 01/18/2017
ms.prod: microsoft-edge
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0a93ecfb-4b82-4a85-b24c-6816db2332ea
caps.latest.revision: 5
author: MSEdgeTeam
ms.author: msedgedevrel
manager: ''
ms.openlocfilehash: ad6d635722f0b3fea8b19f8d16679b402d1fd56e
ms.sourcegitcommit: 6860234c25a8be863b7f29a54838e78e120dbb62
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2020
ms.locfileid: "10564213"
---
# <span data-ttu-id="292d5-104">JsParseSerializedScriptWithCallback 函数</span><span class="sxs-lookup"><span data-stu-id="292d5-104">JsParseSerializedScriptWithCallback Function</span></span>
<span data-ttu-id="292d5-105">分析序列化脚本并返回表示脚本的函数。</span><span class="sxs-lookup"><span data-stu-id="292d5-105">Parses a serialized script and returns a function representing the script.</span></span> <span data-ttu-id="292d5-106">仅当需要时，才提供延迟加载脚本源的功能。</span><span class="sxs-lookup"><span data-stu-id="292d5-106">Provides the ability to lazy load the script source only if/when it is needed.</span></span>  
  
## <span data-ttu-id="292d5-107">语法</span><span class="sxs-lookup"><span data-stu-id="292d5-107">Syntax</span></span>  
  
```cpp  
STDAPI_(JsErrorCode) JsParseSerializedScriptWithCallback(  
  _In_ JsSerializedScriptLoadSourceCallback scriptLoadCallback,  
  _In_ JsSerializedScriptUnloadCallback scriptUnloadCallback,  
  _In_ BYTE *buffer,  
  _In_ JsSourceContext sourceContext,  
  _In_z_ const wchar_t *sourceUrl,  
  _Out_ JsValueRef * result  
);  
  
```  
  
#### <span data-ttu-id="292d5-108">参数</span><span class="sxs-lookup"><span data-stu-id="292d5-108">Parameters</span></span>  
 `scriptLoadCallback`  
 <span data-ttu-id="292d5-109">回调需要加载脚本的源代码时调用。</span><span class="sxs-lookup"><span data-stu-id="292d5-109">Callback called when the source code of the script needs to be loaded.</span></span>  
  
 `scriptUnloadCallback`  
 <span data-ttu-id="292d5-110">当不再需要序列化脚本和源代码时调用回调。</span><span class="sxs-lookup"><span data-stu-id="292d5-110">Callback called when the serialized script and source code are no longer needed.</span></span>  
  
 `buffer`  
 <span data-ttu-id="292d5-111">序列化脚本。</span><span class="sxs-lookup"><span data-stu-id="292d5-111">The serialized script.</span></span>  
  
 `sourceContext`  
 <span data-ttu-id="292d5-112">标识可由可调试脚本上下文使用的脚本的 cookie。</span><span class="sxs-lookup"><span data-stu-id="292d5-112">A cookie identifying the script that can be used by debuggable script contexts.</span></span>     <span data-ttu-id="292d5-113">此上下文将传递到 scriptLoadCallback 和 scriptUnloadCallback。</span><span class="sxs-lookup"><span data-stu-id="292d5-113">This context will passed into scriptLoadCallback and scriptUnloadCallback.</span></span>  
  
 `sourceUrl`  
 <span data-ttu-id="292d5-114">脚本的来源位置。</span><span class="sxs-lookup"><span data-stu-id="292d5-114">The location the script came from.</span></span>  
  
 `result`  
 <span data-ttu-id="292d5-115">表示脚本代码的函数。</span><span class="sxs-lookup"><span data-stu-id="292d5-115">A function representing the script code.</span></span>  
  
## <span data-ttu-id="292d5-116">返回值</span><span class="sxs-lookup"><span data-stu-id="292d5-116">Return Value</span></span>  
 <span data-ttu-id="292d5-117">`JsNoError`如果操作成功，则为代码，否则为失败代码。</span><span class="sxs-lookup"><span data-stu-id="292d5-117">The code `JsNoError` if the operation succeeded, a failure code otherwise.</span></span>  
  
## <span data-ttu-id="292d5-118">备注</span><span class="sxs-lookup"><span data-stu-id="292d5-118">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="292d5-119">此 API 尚不可用于应用商店应用。</span><span class="sxs-lookup"><span data-stu-id="292d5-119">This API is not yet available for Store apps.</span></span>  
  
 <span data-ttu-id="292d5-120">需要活动脚本上下文。</span><span class="sxs-lookup"><span data-stu-id="292d5-120">Requires an active script context.</span></span>  
  
 <span data-ttu-id="292d5-121">运行时将一直保留到缓冲区，直到从缓冲区创建的所有函数的所有实例都被垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="292d5-121">The runtime will hold on to the buffer until all instances of any functions created from     the buffer are garbage collected.</span></span>  <span data-ttu-id="292d5-122">然后，它将调用 scriptUnloadCallback 以通知呼叫者安全释放。</span><span class="sxs-lookup"><span data-stu-id="292d5-122">It will then call scriptUnloadCallback to inform the     caller that it is safe to release.</span></span>  
  
## <span data-ttu-id="292d5-123">要求</span><span class="sxs-lookup"><span data-stu-id="292d5-123">Requirements</span></span>  
 <span data-ttu-id="292d5-124">**页眉：** jsrt</span><span class="sxs-lookup"><span data-stu-id="292d5-124">**Header:** jsrt.h</span></span>  
  
## <span data-ttu-id="292d5-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="292d5-125">See Also</span></span>  
 [<span data-ttu-id="292d5-126">参考（JavaScript 运行时）</span><span class="sxs-lookup"><span data-stu-id="292d5-126">Reference (JavaScript Runtime)</span></span>](../chakra-hosting/reference-javascript-runtime.md)