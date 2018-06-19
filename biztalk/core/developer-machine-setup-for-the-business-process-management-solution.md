---
title: 商務程序管理解決方案的開發人員電腦設定 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- developer servers
- process management solution tutorial, developer servers
- process management solution tutorial, deploying
ms.assetid: cf975323-53ec-45a8-9f68-80ad423f298b
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1e2491d755062828a3204d895fa7be7552ef06d5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22238878"
---
# <a name="developer-machine-setup-for-the-business-process-management-solution"></a><span data-ttu-id="01aea-102">商務程序管理解決方案的開發人員電腦設定</span><span class="sxs-lookup"><span data-stu-id="01aea-102">Developer Machine Setup for the Business Process Management Solution</span></span>
<span data-ttu-id="01aea-103">商務程序管理 (BPM) 解決方案顯示在 BizTalk 應用程式中建構程序管理員的方式。</span><span class="sxs-lookup"><span data-stu-id="01aea-103">The Business Process Management (BPM) solution shows one way to construct a process manager in a BizTalk application.</span></span> <span data-ttu-id="01aea-104">解決方案使用元件以選取和控制訂單處理階段的順序。</span><span class="sxs-lookup"><span data-stu-id="01aea-104">The solution uses a component to select and control the sequence of stages in order processing.</span></span> <span data-ttu-id="01aea-105">解決方案會在傳遞訂單以進行處理之前，接收訂單 (可能用於新的服務、升級或服務終止)、加以記錄和認可訂單。</span><span class="sxs-lookup"><span data-stu-id="01aea-105">The solution takes an order—which may be for new service, an upgrade, or termination of service—logs it, and acknowledges the order before passing it on for processing.</span></span> <span data-ttu-id="01aea-106">處理包含一或多個處理訂單的階段。</span><span class="sxs-lookup"><span data-stu-id="01aea-106">The processing consists of one or more stages that handle the order.</span></span> <span data-ttu-id="01aea-107">最後，解決方案會將回應傳回至原始訂單要求。</span><span class="sxs-lookup"><span data-stu-id="01aea-107">Finally, the solution returns a response to the original order request.</span></span>  
  
 <span data-ttu-id="01aea-108">身為開發人員，您首先會取得在單一電腦上執行的實例。</span><span class="sxs-lookup"><span data-stu-id="01aea-108">As a developer, you first get the scenario running on a single computer.</span></span> <span data-ttu-id="01aea-109">在單一電腦上測試功能之後，您將會與 IT 專業人員討論如何將解決方案部署至實際執行伺服器。</span><span class="sxs-lookup"><span data-stu-id="01aea-109">After testing functionalities on the single computer, you will discuss how to deploy the solution on production servers with IT professionals.</span></span> <span data-ttu-id="01aea-110">您必須協助他們設計系統架構以滿足服務需求，如高可用性、更好的效能和易於維護。</span><span class="sxs-lookup"><span data-stu-id="01aea-110">You need to help them to design the system architecture to satisfy service requirements such as high availability, better performance, and easier maintenance.</span></span> <span data-ttu-id="01aea-111">然後您將會根據設計準備實際執行部署的資源。</span><span class="sxs-lookup"><span data-stu-id="01aea-111">You will then prepare resources for production deployment based on the design.</span></span>  
  
 <span data-ttu-id="01aea-112">此部署指南說明如何在單一電腦上安裝和測試商務程序管理解決方案。</span><span class="sxs-lookup"><span data-stu-id="01aea-112">This deployment guide describes how to install and test the business process management solution on a single computer.</span></span>  
  
 <span data-ttu-id="01aea-113">如需有關商務程序管理解決方案的詳細資訊，請參閱[了解商務程序管理解決方案](../core/understanding-the-business-process-management-solution.md)。</span><span class="sxs-lookup"><span data-stu-id="01aea-113">For more information about the business process management solution, see [Understanding the Business Process Management Solution](../core/understanding-the-business-process-management-solution.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="01aea-114">本節內容</span><span class="sxs-lookup"><span data-stu-id="01aea-114">In This Section</span></span>  
  
-   [<span data-ttu-id="01aea-115">安裝商務程序管理解決方案之前</span><span class="sxs-lookup"><span data-stu-id="01aea-115">Before Installing the Business Process Management Solution</span></span>](../core/before-installing-the-business-process-management-solution.md)  
  
-   [<span data-ttu-id="01aea-116">如何安裝商務程序管理解決方案</span><span class="sxs-lookup"><span data-stu-id="01aea-116">How to Install the Business Process Management Solution</span></span>](../core/how-to-install-the-business-process-management-solution.md)  
  
-   [<span data-ttu-id="01aea-117">如何執行商務程序管理解決方案</span><span class="sxs-lookup"><span data-stu-id="01aea-117">How to Run the Business Process Management Solution</span></span>](../core/how-to-run-the-business-process-management-solution.md)