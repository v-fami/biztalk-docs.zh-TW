---
title: "實作會反白顯示的商務處理管理解決方案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: process management solution tutorial, implementing
ms.assetid: 3558db0e-d7f6-4c10-bd58-1601bd44e73f
caps.latest.revision: "24"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: decad6f68398cca2d0b88c4904d3e63c075749b3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="implementation-highlights-of-the-business-process-management-solution"></a><span data-ttu-id="a06b0-102">商務程序管理解決方案的實作重點</span><span class="sxs-lookup"><span data-stu-id="a06b0-102">Implementation Highlights of the Business Process Management Solution</span></span>
<span data-ttu-id="a06b0-103">本節將更詳細地描述與實作相關的解決方案項目。</span><span class="sxs-lookup"><span data-stu-id="a06b0-103">This section describes the implementation-related elements of the solution in greater detail.</span></span> <span data-ttu-id="a06b0-104">這些元素包括商務規則架構的處理階段數目如何**OrderManager**與處理階段使用的通訊**OrderHandler**物件，以及如何應用程式使用 Ops 配接器。</span><span class="sxs-lookup"><span data-stu-id="a06b0-104">These elements include the Business Rules Framework, the number of processing stages, how the **OrderManager** communicates with the processing stages, the use of the **OrderHandler** object, and how the application uses the Ops Adapter.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a06b0-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="a06b0-105">In This Section</span></span>  
  
-   [<span data-ttu-id="a06b0-106">使用商務規則驗證</span><span class="sxs-lookup"><span data-stu-id="a06b0-106">Validation with Business Rules</span></span>](../core/validation-with-business-rules.md)  
  
-   [<span data-ttu-id="a06b0-107">處理階段數目</span><span class="sxs-lookup"><span data-stu-id="a06b0-107">Number of Processing Stages</span></span>](../core/number-of-processing-stages.md)  
  
-   [<span data-ttu-id="a06b0-108">反向處理直接夥伴繫結</span><span class="sxs-lookup"><span data-stu-id="a06b0-108">Inverse Direct Partner Binding</span></span>](../core/inverse-direct-partner-binding.md)  
  
-   [<span data-ttu-id="a06b0-109">OrderBroker 與 OrderManager 之間的通訊</span><span class="sxs-lookup"><span data-stu-id="a06b0-109">Communication between OrderBroker and OrderManager</span></span>](../core/communication-between-orderbroker-and-ordermanager.md)  
  
-   [<span data-ttu-id="a06b0-110">商務程序管理解決方案中有效使用 SSO</span><span class="sxs-lookup"><span data-stu-id="a06b0-110">Using SSO Efficiently in the Business Process Management Solution</span></span>](../core/using-sso-efficiently-in-the-business-process-management-solution.md)  
  
-   [<span data-ttu-id="a06b0-111">使用訂單處理常式物件與後端系統通訊</span><span class="sxs-lookup"><span data-stu-id="a06b0-111">Using the Order Handler Object to Communicate with Backend Systems</span></span>](../core/using-the-order-handler-object-to-communicate-with-backend-systems.md)  
  
-   [<span data-ttu-id="a06b0-112">合併 XML 文件</span><span class="sxs-lookup"><span data-stu-id="a06b0-112">Merging XML Documents</span></span>](../core/merging-xml-documents.md)  
  
-   [<span data-ttu-id="a06b0-113">Ops 配接器</span><span class="sxs-lookup"><span data-stu-id="a06b0-113">The Ops Adapter</span></span>](../core/the-ops-adapter.md)  
  
-   [<span data-ttu-id="a06b0-114">Recaller 物件</span><span class="sxs-lookup"><span data-stu-id="a06b0-114">The Recaller Object</span></span>](../core/the-recaller-object.md)