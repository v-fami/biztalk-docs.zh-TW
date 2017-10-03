---
title: "部署商務程序管理解決方案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying, process management solution tutorial
- process management solution tutorial, deploying
ms.assetid: e033e0cd-0333-4f16-a4a0-eaae9ce98fcc
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a0a61048ecb90876b251657f00361c35587a7ec1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="deploying-the-business-process-management-solution"></a><span data-ttu-id="9300a-102">部署商務程序管理解決方案</span><span class="sxs-lookup"><span data-stu-id="9300a-102">Deploying the Business Process Management Solution</span></span>
<span data-ttu-id="9300a-103">商務程序管理 (BPM) 解決方案顯示在 BizTalk 應用程式中建構程序管理員的方式。</span><span class="sxs-lookup"><span data-stu-id="9300a-103">The Business Process Management (BPM) solution shows one way to construct a process manager in a BizTalk application.</span></span> <span data-ttu-id="9300a-104">解決方案使用元件以選取和控制訂單處理階段的順序。</span><span class="sxs-lookup"><span data-stu-id="9300a-104">The solution uses a component to select and control the sequence of stages in order processing.</span></span> <span data-ttu-id="9300a-105">解決方案會在傳遞訂單以進行處理之前，接收訂單 (可能用於新的服務、升級或服務終止)、加以記錄和確認訂單。</span><span class="sxs-lookup"><span data-stu-id="9300a-105">The solution takes an order—which may be for a new service, an upgrade, or termination of service—logs it, and acknowledges the order before passing it on for processing.</span></span> <span data-ttu-id="9300a-106">處理包含一或多個處理訂單的階段。</span><span class="sxs-lookup"><span data-stu-id="9300a-106">The processing consists of one or more stages that handle the order.</span></span> <span data-ttu-id="9300a-107">最後，解決方案會將回應傳回至原始訂單要求。</span><span class="sxs-lookup"><span data-stu-id="9300a-107">Finally, the solution returns a response to the original order request.</span></span>  
  
 <span data-ttu-id="9300a-108">此部署指南描述如何在一部開發電腦和多部實際執行伺服器上安裝和執行商務程序管理解決方案。</span><span class="sxs-lookup"><span data-stu-id="9300a-108">This deployment guide describes how to install and run the business process management solution on a development computer and multiple production servers.</span></span>  
  
 <span data-ttu-id="9300a-109">如需有關商務程序管理解決方案的詳細資訊，請參閱[了解商務程序管理解決方案](../core/understanding-the-business-process-management-solution.md)。</span><span class="sxs-lookup"><span data-stu-id="9300a-109">For more information about the business process management solution, see [Understanding the Business Process Management Solution](../core/understanding-the-business-process-management-solution.md).</span></span>  
  
 <span data-ttu-id="9300a-110">**讀取器的指引**</span><span class="sxs-lookup"><span data-stu-id="9300a-110">**Reader Guidance**</span></span>  
  
 <span data-ttu-id="9300a-111">本文件假設您已熟悉 BizTalk Server、Windows Server 和 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="9300a-111">This document assumes that you are familiar with BizTalk Server, Windows Server, and Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span> <span data-ttu-id="9300a-112">同時假設您也瞭解企業應用程式整合和 Web 服務的基本概念。</span><span class="sxs-lookup"><span data-stu-id="9300a-112">It also assumes that you understand basic concepts about enterprise application integration and Web services.</span></span> <span data-ttu-id="9300a-113">此外，建議您要熟悉使用 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 建置應用程式的方式，並熟悉建立專案、設定參考以及使用偵錯模式以偵錯和測試解決方案等工作。</span><span class="sxs-lookup"><span data-stu-id="9300a-113">Additionally, we recommend that you are familiar with how to build applications by using [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] and that you are familiar with creating projects, setting references, and using the debug mode to debug and test your solution.</span></span> <span data-ttu-id="9300a-114">用於 IT 專業人員和開發人員技術及知識的相關資訊，請參閱[必要條件技術和知識](../core/prerequisite-skills-and-knowledge5.md)。</span><span class="sxs-lookup"><span data-stu-id="9300a-114">For more information about the prerequisite skills and knowledge for IT professionals and developers, see [Prerequisite Skills and Knowledge](../core/prerequisite-skills-and-knowledge5.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9300a-115">本節內容</span><span class="sxs-lookup"><span data-stu-id="9300a-115">In This Section</span></span>  
  
-   [<span data-ttu-id="9300a-116">商務程序管理解決方案的開發人員電腦設定</span><span class="sxs-lookup"><span data-stu-id="9300a-116">Developer Machine Setup for the Business Process Management Solution</span></span>](../core/developer-machine-setup-for-the-business-process-management-solution.md)