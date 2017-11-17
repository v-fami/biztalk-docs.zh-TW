---
title: "安全性摘要 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: security
ms.assetid: 357ebf63-a35e-4ce4-a754-be880946f9fc
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b5d327de93941278b9b1dcecc9378183c6a2f77a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="security-summary"></a><span data-ttu-id="aaaf6-102">安全性摘要</span><span class="sxs-lookup"><span data-stu-id="aaaf6-102">Security Summary</span></span>
## <a name="overview"></a><span data-ttu-id="aaaf6-103">概觀</span><span class="sxs-lookup"><span data-stu-id="aaaf6-103">Overview</span></span>
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="aaaf6-104">[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]提供開發和執行階段元件，以便提供 SWIFT 訊息和自動化功能的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="aaaf6-104"> [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] provides development and runtime components to facilitate BizTalk applications that provide SWIFT messaging and automation functionality.</span></span> <span data-ttu-id="aaaf6-105">使用開發的應用程式[!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]是 BizTalk 應用程式和受保護的原生[!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)]， [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]， [!INCLUDE[btsWinSharePointSvcsNoVersion](../../includes/btswinsharepointsvcsnoversion-md.md)]，與 IIS/ASP[!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)]安全性功能。</span><span class="sxs-lookup"><span data-stu-id="aaaf6-105">Applications developed by using [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] are BizTalk applications and are secured by native [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)], [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)], [!INCLUDE[btsWinSharePointSvcsNoVersion](../../includes/btswinsharepointsvcsnoversion-md.md)], and IIS/ASP[!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] security features.</span></span>  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="aaaf6-106">藉由使用既定加密的網際網路通訊的標準和通訊協定保護隱私權的系統項目。</span><span class="sxs-lookup"><span data-stu-id="aaaf6-106"> protects privacy of system elements by using de facto Internet encrypted communications standards and protocols.</span></span> <span data-ttu-id="aaaf6-107">使用簽章憑證，來保護通訊參與者、 處理序和資訊[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]驗證 」 和 「 企業單一登入。</span><span class="sxs-lookup"><span data-stu-id="aaaf6-107">Communication participants, processes, and information are secured by using signing certificates, [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Authentication, and Enterprise Single Sign-On.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="aaaf6-108">也會強制執行的資源使用的授權機制例如[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]角色和[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]驗證和 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="aaaf6-108"> also enforces authorization of resource usage with mechanisms such as [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] Roles and [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Authentication, and the MessageBox database.</span></span>  
  
 <span data-ttu-id="aaaf6-109">除了原生[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]安全性功能，[!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]定義並強制執行安全性的建立、 修復、 核准及 SWIFT 訊息商務使用者所提交的語意。</span><span class="sxs-lookup"><span data-stu-id="aaaf6-109">In addition to native [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] security features, [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] defines and enforces security semantics for the creation, repair, approval, and submission of SWIFT messages by business users.</span></span> <span data-ttu-id="aaaf6-110">此使用者層級安全性會強制執行使用[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]用數位簽章上的使用者工作站上，以及憑證和資料完整性驗證技術[!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]伺服器上的執行階段服務。</span><span class="sxs-lookup"><span data-stu-id="aaaf6-110">This user-level security is enforced by using [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] digital signing technologies on the user workstation, and certificate and data integrity verification by [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] runtime services on the server.</span></span>  
  
 <span data-ttu-id="aaaf6-111">在一起，[!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)]和[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]提供平台、 基礎結構與工具設計、 開發和執行安全 SWIFT 傳訊和工作流程自動化系統。</span><span class="sxs-lookup"><span data-stu-id="aaaf6-111">Together, [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)] and [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] provide the platform, infrastructure, and tools for designing, developing, and executing secure SWIFT messaging and workflow automation systems.</span></span>  
  
## <a name="more-information"></a><span data-ttu-id="aaaf6-112">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="aaaf6-112">More information</span></span>  
 <span data-ttu-id="aaaf6-113">如需安全性做法的資訊，請參閱下列各項：</span><span class="sxs-lookup"><span data-stu-id="aaaf6-113">For information about security best practices, see the following:</span></span>  
  
-   <span data-ttu-id="aaaf6-114">Technet 資訊安全資源中心：</span><span class="sxs-lookup"><span data-stu-id="aaaf6-114">TechNet Security Resource Center:</span></span>  
  
     [<span data-ttu-id="aaaf6-115">http://go.microsoft.com/fwlink/p/?LinkId=27741</span><span class="sxs-lookup"><span data-stu-id="aaaf6-115">http://go.microsoft.com/fwlink/p/?LinkId=27741</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=27741)  
  

-   <span data-ttu-id="aaaf6-116">示範如何使用工具，來實作中所述的最佳作法的 Symantec 安全性指南 》[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]安全性操作指南 》 [!INCLUDE[btsWin2kSvr](../../includes/btswin2ksvr-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="aaaf6-116">Symantec security guide showing how to use their tools to implement the best practices described in [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Security Operations Guide for [!INCLUDE[btsWin2kSvr](../../includes/btswin2ksvr-md.md)]:</span></span>  
  
     [<span data-ttu-id="aaaf6-117">http://go.microsoft.com/fwlink/p/?LinkId=28274</span><span class="sxs-lookup"><span data-stu-id="aaaf6-117">http://go.microsoft.com/fwlink/p/?LinkId=28274</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=28274)  

  
-   <span data-ttu-id="aaaf6-118">資訊[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]安全性通知服務：</span><span class="sxs-lookup"><span data-stu-id="aaaf6-118">Information about the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Security Notification Service:</span></span>  
  
     [<span data-ttu-id="aaaf6-119">http://go.microsoft.com/fwlink/p/?LinkId=27744</span><span class="sxs-lookup"><span data-stu-id="aaaf6-119">http://go.microsoft.com/fwlink/p/?LinkId=27744</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=27744)  
  
  
## <a name="see-also"></a><span data-ttu-id="aaaf6-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aaaf6-120">See Also</span></span>  
[<span data-ttu-id="aaaf6-121">執行階段、 訊息修復、 FIN 回應和傳訊</span><span class="sxs-lookup"><span data-stu-id="aaaf6-121">Runtime, message repair, FIN response, and messaging</span></span>](../../adapters-and-accelerators/accelerator-swift/runtime-message-repair-fin-response-and-messaging.md)