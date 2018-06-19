---
title: 雙向動作教學課程 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tutorials, PIPs
- double action tutorial, about the tutorial
- trading partners, tutorials
- double action tutorial
- tutorials, trading partners
- PIPs, tutorials
- tutorials, double action tutorial
ms.assetid: b692c043-82ef-46f4-8683-7ae1fd6e4421
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e5243fb2547f27b113e3096d6c93d233e22aae3e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22210118"
---
# <a name="double-action-tutorial"></a><span data-ttu-id="1b064-102">雙向動作教學課程</span><span class="sxs-lookup"><span data-stu-id="1b064-102">Double Action Tutorial</span></span>
<span data-ttu-id="1b064-103">本教學課程涵蓋了使用 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] 的端點對端點解決方案。</span><span class="sxs-lookup"><span data-stu-id="1b064-103">This tutorial covers an end-to-end solution using [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)].</span></span> <span data-ttu-id="1b064-104">其中詳細描述必須遵循的步驟，透過在兩家虛構公司之間建立交易夥伴實例，藉此實作 RosettaNet 相容解決方案：賣方組織 Contoso 與買方組織 Fabrikam。</span><span class="sxs-lookup"><span data-stu-id="1b064-104">The tutorial details the steps that you have to follow to implement a RosettaNet-compliant solution by creating a trading partner scenario between two fictitious companies: Contoso, the supplier organization, and Fabrikam, the buyer organization.</span></span>  
  
 <span data-ttu-id="1b064-105">本教學課程使用四種不同的交易夥伴介面程序 (PIP)：</span><span class="sxs-lookup"><span data-stu-id="1b064-105">This tutorial uses four different Partner Interface Processes (PIPs):</span></span>  
  
-   <span data-ttu-id="1b064-106">0C2 - 非同步測試要求</span><span class="sxs-lookup"><span data-stu-id="1b064-106">0C2 - Asynchronous Test Request</span></span>  
  
-   <span data-ttu-id="1b064-107">0C4 - 同步測試查詢</span><span class="sxs-lookup"><span data-stu-id="1b064-107">0C4 - Synchronous Test Query</span></span>  
  
-   <span data-ttu-id="1b064-108">3A2 - 要求報價以及可用性</span><span class="sxs-lookup"><span data-stu-id="1b064-108">3A2 - Request Price and Availability</span></span>  
  
-   <span data-ttu-id="1b064-109">3A4 - 訂單要求</span><span class="sxs-lookup"><span data-stu-id="1b064-109">3A4 - Request Purchase Order</span></span>  
  
 <span data-ttu-id="1b064-110">本教學課程涵蓋 RosettaNet 架構解決方案的幾個不同領域，包括使用 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 管理主控台、建立商務營運系統 (LOB) 應用程式，以及建立可用來整合「企業資源規劃」(Enterprise Resource Planning，ERP) 系統的自訂協調流程。</span><span class="sxs-lookup"><span data-stu-id="1b064-110">This tutorial addresses several distinct areas of a RosettaNet-based solution, including working with the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Management Console, creating line-of-business (LOB) applications, and creating custom orchestrations that you can use to integrate Enterprise Resource Planning (ERP) systems.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1b064-111">本節內容</span><span class="sxs-lookup"><span data-stu-id="1b064-111">In This Section</span></span>  
  
-   [<span data-ttu-id="1b064-112">準備進行雙向動作教學課程</span><span class="sxs-lookup"><span data-stu-id="1b064-112">Preparing for the Double Action Tutorial</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/preparing-for-the-double-action-tutorial.md)  
  
-   [<span data-ttu-id="1b064-113">建立與設定 Contoso 解決方案</span><span class="sxs-lookup"><span data-stu-id="1b064-113">Creating and Configuring the Contoso Solution</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/creating-and-configuring-the-contoso-solution.md)  
  
-   [<span data-ttu-id="1b064-114">建立與設定 Fabrikam 解決方案</span><span class="sxs-lookup"><span data-stu-id="1b064-114">Creating and Configuring the Fabrikam Solution</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/creating-and-configuring-the-fabrikam-solution.md)  
  
-   [<span data-ttu-id="1b064-115">測試雙向動作教學課程</span><span class="sxs-lookup"><span data-stu-id="1b064-115">Testing the Double Action Tutorial</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/testing-the-double-action-tutorial.md)