---
title: 實作自動化的測試 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d4ba540e-789d-49bf-af4b-87e6f37ab96f
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aee97d5c44ebd32ca5b325af386fb1a8754f5b20
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22298046"
---
# <a name="implementing-automated-testing"></a><span data-ttu-id="3f464-102">實作自動化的測試</span><span class="sxs-lookup"><span data-stu-id="3f464-102">Implementing Automated Testing</span></span>
<span data-ttu-id="3f464-103">BizTalk Server 解決方案通常會部署在 「 任務關鍵性 」 案例中，藉此 BizTalk 解決方案是企業的核心元件。</span><span class="sxs-lookup"><span data-stu-id="3f464-103">BizTalk Server solutions are often deployed in “mission-critical” scenarios, whereby the BizTalk solution is a core component of the business.</span></span> <span data-ttu-id="3f464-104">在這些情況下，持續的效能與穩定性的 BizTalk 解決方案是重要的商務需求，如果 BizTalk 解決方案失敗，相關聯的停機時間成本皆屬於顯著。</span><span class="sxs-lookup"><span data-stu-id="3f464-104">In these scenarios, the continual performance and stability of the BizTalk solution is a key business requirement; if the BizTalk solution fails, the associated downtime costs are significant.</span></span> <span data-ttu-id="3f464-105">在這種情況下，它最重要的是方案將放入實際執行之前經過徹底測試 BizTalk 解決方案。</span><span class="sxs-lookup"><span data-stu-id="3f464-105">In such scenarios, it is of paramount importance that the BizTalk solution be thoroughly tested before the solution is placed into production.</span></span> <span data-ttu-id="3f464-106">相較於未測試或不足以測試解決方案所產生的停機時間成本與正確測試方案相關聯的成本都很小。</span><span class="sxs-lookup"><span data-stu-id="3f464-106">The costs associated with properly testing the solution are small compared to the downtime costs resulting from not testing or insufficiently testing the solution.</span></span> <span data-ttu-id="3f464-107">因此，BizTalk Server 解決方案的測試是說是任何 BizTalk Server 方案部署的最重要階段。</span><span class="sxs-lookup"><span data-stu-id="3f464-107">Therefore, the testing of a BizTalk Server solution is arguably the most important phase of any BizTalk Server solution deployment.</span></span>  
  
 <span data-ttu-id="3f464-108">本章節描述在生產環境中執行方案之前，先測試 BizTalk 解決方案的適當方法。</span><span class="sxs-lookup"><span data-stu-id="3f464-108">This section describes the proper methodology for testing a BizTalk solution before running the solution in a production environment.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3f464-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="3f464-109">In This Section</span></span>  
  
-   [<span data-ttu-id="3f464-110">它為何如此重要至測試</span><span class="sxs-lookup"><span data-stu-id="3f464-110">Why It Is Important to Test</span></span>](../technical-guides/why-it-is-important-to-test.md)  
  
-   [<span data-ttu-id="3f464-111">自動化建置程序</span><span class="sxs-lookup"><span data-stu-id="3f464-111">Automating the Build Process</span></span>](../technical-guides/automating-the-build-process.md)  
  
-   [<span data-ttu-id="3f464-112">使用 BizUnit 促進自動化測試</span><span class="sxs-lookup"><span data-stu-id="3f464-112">Using BizUnit to Facilitate Automated Testing</span></span>](../technical-guides/using-bizunit-to-facilitate-automated-testing.md)  
  
-   [<span data-ttu-id="3f464-113">使用 Visual Studio，以促進自動化測試</span><span class="sxs-lookup"><span data-stu-id="3f464-113">Using Visual Studio to Facilitate Automated Testing</span></span>](../technical-guides/using-visual-studio-to-facilitate-automated-testing.md)