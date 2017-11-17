---
title: "管理 BizTalk Server 中的 BAM 入口網站 |Microsoft 文件"
Description: "安裝和設定 BizTalk Server 中的 BAM 入口網站的概觀"
ms.custom: 
ms.date: 08/15/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3a08aa85-3a45-4a8c-bdb5-5615ca097ce1
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9d7908c9c7ce8e4b731e0b88569e3dc3fb228a1d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="manage-the-bam-portal"></a><span data-ttu-id="88e68-103">管理 BAM 入口網站</span><span class="sxs-lookup"><span data-stu-id="88e68-103">Manage the BAM portal</span></span>

## <a name="set-up-bam-portal"></a><span data-ttu-id="88e68-104">設定 BAM 入口網站</span><span class="sxs-lookup"><span data-stu-id="88e68-104">Set up BAM portal</span></span>
<span data-ttu-id="88e68-105">系統管理員設定 BAM 入口網站執行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝。</span><span class="sxs-lookup"><span data-stu-id="88e68-105">Administrators set up the BAM portal by running the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation.</span></span> <span data-ttu-id="88e68-106">請使用 BizTalk Server 組態工具指定是否啟用 BAM，並指定 Web 服務帳戶、可檢視入口網站的 Windows 群組，以及裝載入口網站的網站。</span><span class="sxs-lookup"><span data-stu-id="88e68-106">Use the BizTalk Server configuration tool to specify whether BAM is enabled, and to specify the Web service accounts, the Windows groups that can view portal, and the Web site that will host the portal.</span></span> <span data-ttu-id="88e68-107">當設定好 BAM 入口網站而又需要更新 BAM 入口網站組態時，您可以使用組態工具更新組態設定，例如入口網站使用者群組、應用程式集區帳戶和管理 Web 服務使用者。</span><span class="sxs-lookup"><span data-stu-id="88e68-107">If it becomes necessary to update the BAM portal configuration once you have set up the BAM portal, you use the configuration tool to update the configuration settings such as the portal users group, the Application Pool account, and the management Web services user.</span></span>  
  
 <span data-ttu-id="88e68-108">如需有關安裝 BAM 入口網站的詳細資訊，請參閱[安裝及設定在多重電腦環境中的 BAM](http://social.technet.microsoft.com/wiki/contents/articles/1888.install-and-configure-bam-business-activity-monitoring-in-a-multi-computer-environment.aspx)。</span><span class="sxs-lookup"><span data-stu-id="88e68-108">For more information about installing the BAM portal, see [Install and Configure BAM in Multiple Computer Environments](http://social.technet.microsoft.com/wiki/contents/articles/1888.install-and-configure-bam-business-activity-monitoring-in-a-multi-computer-environment.aspx).</span></span>  
  
 <span data-ttu-id="88e68-109">如需有關如何設定 BAM 入口網站的詳細資訊，請參閱[設定 BizTalk Server](../install-and-config-guides/configure-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="88e68-109">For more information about configuring the BAM portal, see [Configure BizTalk Server](../install-and-config-guides/configure-biztalk-server.md).</span></span>
  
 <span data-ttu-id="88e68-110">BAM 入口網站有許多可自訂的設定，可以透過修改 webconfig.xml 檔案來存取。</span><span class="sxs-lookup"><span data-stu-id="88e68-110">The BAM portal has many customizable settings that are accessed by modifying the webconfig.xml file.</span></span> <span data-ttu-id="88e68-111">這些設定控制了 BAM 入口網站的效能和運作。</span><span class="sxs-lookup"><span data-stu-id="88e68-111">These settings control the performance and operation of the BAM portal.</span></span> <span data-ttu-id="88e68-112">本節的其餘部分將說明如何自訂 BAM 入口網站組態。</span><span class="sxs-lookup"><span data-stu-id="88e68-112">This rest of this section describes how to customize your BAM portal configuration.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="88e68-113">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="88e68-113">Next steps</span></span> 
  
-   [<span data-ttu-id="88e68-114">自訂 BAM 入口網站組態</span><span class="sxs-lookup"><span data-stu-id="88e68-114">Customizing the BAM Portal Configuration</span></span>](../core/customizing-the-bam-portal-configuration.md)  
  
-   [<span data-ttu-id="88e68-115">如何在 NLB 叢集上設定 BAM 入口網站工作</span><span class="sxs-lookup"><span data-stu-id="88e68-115">How to Configure the BAM Portal to Work on an NLB Cluster</span></span>](../core/how-to-configure-the-bam-portal-to-work-on-an-nlb-cluster.md)  
  
## <a name="see-also"></a><span data-ttu-id="88e68-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="88e68-116">See Also</span></span>  
 [<span data-ttu-id="88e68-117">管理 BAM 動態基礎結構</span><span class="sxs-lookup"><span data-stu-id="88e68-117">Managing the BAM Dynamic Infrastructure</span></span>](../core/managing-the-bam-dynamic-infrastructure.md)