---
title: 安全性摘要 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- security
ms.assetid: 357ebf63-a35e-4ce4-a754-be880946f9fc
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: df0062eca25e95c41c07d2e8dbf9ccac0a4694a3
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36995351"
---
# <a name="security-summary"></a><span data-ttu-id="45c08-102">安全性摘要</span><span class="sxs-lookup"><span data-stu-id="45c08-102">Security Summary</span></span>
## <a name="overview"></a><span data-ttu-id="45c08-103">概觀</span><span class="sxs-lookup"><span data-stu-id="45c08-103">Overview</span></span>
<span data-ttu-id="45c08-104">Microsoft[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]提供開發和執行階段元件，以便提供傳訊和自動化功能的 SWIFT 的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="45c08-104">Microsoft [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] provides development and runtime components to facilitate BizTalk applications that provide SWIFT messaging and automation functionality.</span></span> <span data-ttu-id="45c08-105">使用所開發的應用程式[!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]是 BizTalk 應用程式和受保護的原生[!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)]， [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]， [!INCLUDE[btsWinSharePointSvcsNoVersion](../../includes/btswinsharepointsvcsnoversion-md.md)]，和 IIS/ASP[!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)]安全性功能。</span><span class="sxs-lookup"><span data-stu-id="45c08-105">Applications developed by using [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] are BizTalk applications and are secured by native [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)], [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)], [!INCLUDE[btsWinSharePointSvcsNoVersion](../../includes/btswinsharepointsvcsnoversion-md.md)], and IIS/ASP[!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] security features.</span></span>  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="45c08-106"> 使用實際的通訊加密的網際網路標準和通訊協定，以保護隱私權的系統項目。</span><span class="sxs-lookup"><span data-stu-id="45c08-106"> protects privacy of system elements by using de facto Internet encrypted communications standards and protocols.</span></span> <span data-ttu-id="45c08-107">通訊參與者、 流程和資訊保護使用簽署憑證，[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]驗證 」 和 「 企業單一登入。</span><span class="sxs-lookup"><span data-stu-id="45c08-107">Communication participants, processes, and information are secured by using signing certificates, [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Authentication, and Enterprise Single Sign-On.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="45c08-108"> 也會強制執行的資源使用的授權機制，例如[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]角色和[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]驗證和 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="45c08-108"> also enforces authorization of resource usage with mechanisms such as [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] Roles and [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Authentication, and the MessageBox database.</span></span>  
  
 <span data-ttu-id="45c08-109">除了原生[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]安全性功能，[!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]定義並強制執行安全性建立、 修復、 核准及商務使用者的 SWIFT 訊息提交語意。</span><span class="sxs-lookup"><span data-stu-id="45c08-109">In addition to native [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] security features, [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] defines and enforces security semantics for the creation, repair, approval, and submission of SWIFT messages by business users.</span></span> <span data-ttu-id="45c08-110">使用強制執行此使用者層級安全性[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]數位簽章上由使用者工作站，以及憑證和資料完整性驗證技術[!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]伺服器上的執行階段服務。</span><span class="sxs-lookup"><span data-stu-id="45c08-110">This user-level security is enforced by using [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] digital signing technologies on the user workstation, and certificate and data integrity verification by [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] runtime services on the server.</span></span>  
  
 <span data-ttu-id="45c08-111">共同[!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)]和[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]提供平台、 基礎結構與工具設計、 開發及執行保護 SWIFT 訊息和工作流程自動化系統。</span><span class="sxs-lookup"><span data-stu-id="45c08-111">Together, [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)] and [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] provide the platform, infrastructure, and tools for designing, developing, and executing secure SWIFT messaging and workflow automation systems.</span></span>  
  
## <a name="more-information"></a><span data-ttu-id="45c08-112">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="45c08-112">More information</span></span>  
 <span data-ttu-id="45c08-113">如需安全性最佳做法資訊，請參閱下列各項：</span><span class="sxs-lookup"><span data-stu-id="45c08-113">For information about security best practices, see the following:</span></span>  
  
- <span data-ttu-id="45c08-114">TechNet Security Resource Center:</span><span class="sxs-lookup"><span data-stu-id="45c08-114">TechNet Security Resource Center:</span></span>  
  
   [http://go.microsoft.com/fwlink/p/?LinkId=27741](http://go.microsoft.com/fwlink/p/?LinkId=27741)  
  

- <span data-ttu-id="45c08-115">示範如何使用工具，以實作 Microsoft 安全性操作指南中所述的最佳作法的 Symantec 安全性指南[!INCLUDE[btsWin2kSvr](../../includes/btswin2ksvr-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="45c08-115">Symantec security guide showing how to use their tools to implement the best practices described in Microsoft Security Operations Guide for [!INCLUDE[btsWin2kSvr](../../includes/btswin2ksvr-md.md)]:</span></span>  
  
   [http://go.microsoft.com/fwlink/p/?LinkId=28274](http://go.microsoft.com/fwlink/p/?LinkId=28274)  

  
- <span data-ttu-id="45c08-116">Microsoft 安全性通知服務的相關資訊：</span><span class="sxs-lookup"><span data-stu-id="45c08-116">Information about the Microsoft Security Notification Service:</span></span>  
  
   [http://go.microsoft.com/fwlink/p/?LinkId=27744](http://go.microsoft.com/fwlink/p/?LinkId=27744)  
  
  
## <a name="see-also"></a><span data-ttu-id="45c08-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="45c08-117">See Also</span></span>  
[<span data-ttu-id="45c08-118">執行階段、訊息修復、FIN 回應和傳訊</span><span class="sxs-lookup"><span data-stu-id="45c08-118">Runtime, message repair, FIN response, and messaging</span></span>](../../adapters-and-accelerators/accelerator-swift/runtime-message-repair-fin-response-and-messaging.md)