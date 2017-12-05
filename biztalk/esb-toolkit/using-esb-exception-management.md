---
title: "使用 ESB 例外狀況管理 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: de6ce411-2d34-4fd8-9644-6fbc9cec266d
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c4eff5a729b8c8ca191b2185180e312f9e895c02
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="using-esb-exception-management"></a><span data-ttu-id="bec3b-102">使用 ESB 例外管理</span><span class="sxs-lookup"><span data-stu-id="bec3b-102">Using ESB Exception Management</span></span>
<span data-ttu-id="bec3b-103">範圍的內容，並在數個不同的處理階段，在 ESB 期間可能會發生錯誤和例外狀況。</span><span class="sxs-lookup"><span data-stu-id="bec3b-103">Errors and exceptions can occur in a range of contexts and during a number of different processing stages in an ESB.</span></span> <span data-ttu-id="bec3b-104">本節提供處理例外狀況的相關資訊，並說明您如何發行透過 ESB 管理入口網站的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="bec3b-104">This section provides information about handling exceptions and describes how you can publish details through the ESB Management Portal.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="bec3b-105">概觀</span><span class="sxs-lookup"><span data-stu-id="bec3b-105">Overview</span></span>  
 <span data-ttu-id="bec3b-106">有許多種方式可以處理 BizTalk Server 解決方案，包括使用架構，例如企業程式庫中的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="bec3b-106">There are many ways to handle exceptions in a BizTalk Server solution, including using frameworks such as the Enterprise Library.</span></span> <span data-ttu-id="bec3b-107">不過，在 ESB 與 BizTalk Server 開發時，您以訊息為基礎的環境中運作。</span><span class="sxs-lookup"><span data-stu-id="bec3b-107">However, when developing with ESB and BizTalk Server, you are working in a message-based environment.</span></span> <span data-ttu-id="bec3b-108">BizTalk 解決方案中的所有項目是訊息導向和 BizTalk 開發人員認為訊息導向的方式。</span><span class="sxs-lookup"><span data-stu-id="bec3b-108">Everything in a BizTalk solution is message-oriented, and BizTalk developers think in a message-oriented way.</span></span> <span data-ttu-id="bec3b-109">因此，[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]實作例外狀況處理的訊息導向方法。</span><span class="sxs-lookup"><span data-stu-id="bec3b-109">Therefore, the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] implements a message-oriented approach to exception handling.</span></span>  
  
 <span data-ttu-id="bec3b-110">ESB 例外狀況管理 Framework 會遵循設計模式，提供有彈性的方法例外狀況監視，可讓來自方案之外的錯誤回應，可能是在業務單位層級。</span><span class="sxs-lookup"><span data-stu-id="bec3b-110">The ESB Exception Management Framework follows a design pattern that provides a flexible approach to exception monitoring and enables error responses to originate from outside of the solution—perhaps at business-unit level.</span></span>  
  
 <span data-ttu-id="bec3b-111">下列主題將討論 ESB 例外狀況管理架構，在更多詳細資料：</span><span class="sxs-lookup"><span data-stu-id="bec3b-111">The following topics discuss the ESB Exception Management Framework in more detail:</span></span>  
  
-   [<span data-ttu-id="bec3b-112">ESB 例外狀況管理架構的設計</span><span class="sxs-lookup"><span data-stu-id="bec3b-112">Design of the ESB Exception Management Framework</span></span>](../esb-toolkit/design-of-the-esb-exception-management-framework.md)  
  
-   [<span data-ttu-id="bec3b-113">例外狀況管理架構的元件</span><span class="sxs-lookup"><span data-stu-id="bec3b-113">The Components of the Exception Management Framework</span></span>](../esb-toolkit/the-components-of-the-exception-management-framework.md)  
  
-   [<span data-ttu-id="bec3b-114">使用例外狀況管理架構</span><span class="sxs-lookup"><span data-stu-id="bec3b-114">Using the Exception Management Framework</span></span>](../esb-toolkit/using-the-exception-management-framework.md)  
  
-   [<span data-ttu-id="bec3b-115">建立自訂例外狀況處理常式</span><span class="sxs-lookup"><span data-stu-id="bec3b-115">Creating Custom Exception Handlers</span></span>](../esb-toolkit/creating-custom-exception-handlers.md)