---
title: "Windows Communication Foundation 中的作業 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a1728d2f-ac74-446e-a36f-4b645a6e042a
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7c6b5344b8fb2c5a5ba7a68b112adb50133198c3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="operations-in-windows-communication-foundation"></a><span data-ttu-id="b1f45-102">Windows Communication Foundation 內的作業</span><span class="sxs-lookup"><span data-stu-id="b1f45-102">Operations in Windows Communication Foundation</span></span>
<span data-ttu-id="b1f45-103">本章節包含 BAM WCF 攔截器所支援的自訂作業。</span><span class="sxs-lookup"><span data-stu-id="b1f45-103">This section contains the custom operations supported by the BAM WCF interceptor.</span></span>  
  
 <span data-ttu-id="b1f45-104">請注意，如果作業名稱項目含有 Action 屬性：</span><span class="sxs-lookup"><span data-stu-id="b1f45-104">Note that if an operation name element contains an Action attribute:</span></span>  
  
1.  <span data-ttu-id="b1f45-105">針對用戶端和伺服器，作業名稱是以名稱屬性識別，</span><span class="sxs-lookup"><span data-stu-id="b1f45-105">The operation name is the one identified by the name attribute for both the client and the server,</span></span>  
  
2.  <span data-ttu-id="b1f45-106">針對回覆路徑 (回呼回覆)、用戶端回覆和服務回覆而言，作業名稱是以名稱屬性辨識。</span><span class="sxs-lookup"><span data-stu-id="b1f45-106">For reply paths (callback reply), client reply and service rely, the operation name is identified by the name attribute.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b1f45-107">回覆訊息會擁有一個節點，其名稱是在名稱屬性所指定之名稱附加 "Result" 字樣。</span><span class="sxs-lookup"><span data-stu-id="b1f45-107">Reply messages will have a node that is named by appending the word "Result" to the name specified by the name attribute.</span></span> <span data-ttu-id="b1f45-108">您必須確保 XPaths 反應此命名慣例。</span><span class="sxs-lookup"><span data-stu-id="b1f45-108">You must ensure that the XPaths reflect this naming convention.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b1f45-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="b1f45-109">In This Section</span></span>  
  
-   [<span data-ttu-id="b1f45-110">AutoGenerateCorrelationToken</span><span class="sxs-lookup"><span data-stu-id="b1f45-110">AutoGenerateCorrelationToken</span></span>](../core/autogeneratecorrelationtoken.md)  
  
-   [<span data-ttu-id="b1f45-111">GetContextProperty</span><span class="sxs-lookup"><span data-stu-id="b1f45-111">GetContextProperty</span></span>](../core/getcontextproperty1.md)  
  
-   [<span data-ttu-id="b1f45-112">GetEndpointName</span><span class="sxs-lookup"><span data-stu-id="b1f45-112">GetEndpointName</span></span>](../core/getendpointname.md)  
  
-   [<span data-ttu-id="b1f45-113">使用 GetOperationName</span><span class="sxs-lookup"><span data-stu-id="b1f45-113">GetOperationName</span></span>](../core/getoperationname.md)  
  
-   [<span data-ttu-id="b1f45-114">GetServiceContractCallPoint</span><span class="sxs-lookup"><span data-stu-id="b1f45-114">GetServiceContractCallPoint</span></span>](../core/getservicecontractcallpoint.md)  
  
-   [<span data-ttu-id="b1f45-115">XPath</span><span class="sxs-lookup"><span data-stu-id="b1f45-115">XPath</span></span>](../core/xpath.md)