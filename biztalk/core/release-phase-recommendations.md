---
title: 發行階段建議 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c5ac72aa-decd-4b3e-be34-e585e54568b3
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 46a38a8a06fac8dc35fed4d965ea9b7952c5fdfe
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22268702"
---
# <a name="release-phase-recommendations"></a><span data-ttu-id="4a502-102">發行階段建議</span><span class="sxs-lookup"><span data-stu-id="4a502-102">Release Phase Recommendations</span></span>
<span data-ttu-id="4a502-103">發行階段包括將目前已驗證完成的系統傳播到生產硬體。</span><span class="sxs-lookup"><span data-stu-id="4a502-103">The release phase involves propagating the now validated system onto the production hardware.</span></span>  
  
## <a name="propagate-test-bed-optimizations-to-production-systems"></a><span data-ttu-id="4a502-104">將測試台最佳化傳播至生產系統</span><span class="sxs-lookup"><span data-stu-id="4a502-104">Propagate Test Bed Optimizations to Production Systems</span></span>  
 <span data-ttu-id="4a502-105">將系統成品和組態傳播到生產硬體並啟動其處理程序是相當簡單的程序。</span><span class="sxs-lookup"><span data-stu-id="4a502-105">Propagating the system artifacts and configuration onto the production hardware and starting it up to process is a relatively straightforward process.</span></span> <span data-ttu-id="4a502-106">不過，在實際應用時，可能很容易忽略此階段必須考量的下列效能相關事項：</span><span class="sxs-lookup"><span data-stu-id="4a502-106">However, in practice, there are things to consider regarding performance during this phase that can be easily missed:</span></span>  
  
-   <span data-ttu-id="4a502-107">**請確認已傳播平台最佳化**。</span><span class="sxs-lookup"><span data-stu-id="4a502-107">**Verify that platform optimizations are propagated**.</span></span> <span data-ttu-id="4a502-108">在實作及驗證期間，通常會實作任何數目的平台層級效能最佳化。</span><span class="sxs-lookup"><span data-stu-id="4a502-108">During implementation and verification, it is common to implement any number of platform level performance optimizations.</span></span>  
  
     <span data-ttu-id="4a502-109">比方說，當使用例如 HTTP 外掛式配接器在 Internet Information Server (IIS) 中，有數個可用的配接器將在其中執行的 IIS 中的處理序數目增加，例如的一般效能最佳化。</span><span class="sxs-lookup"><span data-stu-id="4a502-109">For example, when using an isolated adapter such as HTTP on Internet Information Server (IIS), there are a number of common performance optimizations that can be used such as increasing the number of processes in IIS in which the adapters will run.</span></span> <span data-ttu-id="4a502-110">這一類在發行之前找到的效能最佳化，全都必須加以追蹤並傳播到生產環境。</span><span class="sxs-lookup"><span data-stu-id="4a502-110">Any such performance optimizations found before release must be tracked and propagated to the production environment as well.</span></span>  
  
-   <span data-ttu-id="4a502-111">**設定並自動化資料備份、 記錄傳送、 資料保留組態和清除作業**。</span><span class="sxs-lookup"><span data-stu-id="4a502-111">**Set up and automate data backup, log shipping, data retention configurations, and purging tasks**.</span></span> <span data-ttu-id="4a502-112">在進行生產憑證的過程中，資料庫 (例如 BizTalk 追蹤資料庫和 BAM 資料庫) 備份及清除的頻率是持續性的關鍵，因此必須將這些設定移轉到尚無這種設定的生產環境。</span><span class="sxs-lookup"><span data-stu-id="4a502-112">As part of certification for production, the frequency at which databases are backed up and purged (for example, the BizTalk Tracking database and BAM database) is key to sustainability so those settings must be migrated to production they don’t already exist there.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a502-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4a502-113">See Also</span></span>  
 <span data-ttu-id="4a502-114">[依階段的專案規劃建議](../core/project-planning-recommendations-by-phase.md) </span><span class="sxs-lookup"><span data-stu-id="4a502-114">[Project Planning Recommendations by Phase](../core/project-planning-recommendations-by-phase.md) </span></span>  
 <span data-ttu-id="4a502-115">[需求階段建議](../core/requirements-phase-recommendations.md) </span><span class="sxs-lookup"><span data-stu-id="4a502-115">[Requirements Phase Recommendations](../core/requirements-phase-recommendations.md) </span></span>  
 <span data-ttu-id="4a502-116">[設計階段建議](../core/design-phase-recommendations.md) </span><span class="sxs-lookup"><span data-stu-id="4a502-116">[Design Phase Recommendations](../core/design-phase-recommendations.md) </span></span>  
 <span data-ttu-id="4a502-117">[實作階段建議](../core/implementation-phase-recommendations.md) </span><span class="sxs-lookup"><span data-stu-id="4a502-117">[Implementation Phase Recommendations](../core/implementation-phase-recommendations.md) </span></span>  
 [<span data-ttu-id="4a502-118">驗證階段建議</span><span class="sxs-lookup"><span data-stu-id="4a502-118">Verification Phase Recommendations</span></span>](../core/verification-phase-recommendations.md)