---
title: 更新主控件執行個體設定 |Microsoft 文件
description: 變更主控件執行個體設定在 「 BizTalk Server 系統管理員
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2338255b-cc13-4f6a-86c3-9ecc666c43e5
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d85635f7f7a3b2cfe05abaf041cac07913b36f96
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22254374"
---
# <a name="update-biztalk-host-instance-settings"></a><span data-ttu-id="56ab0-103">更新 BizTalk 主控件執行個體設定</span><span class="sxs-lookup"><span data-stu-id="56ab0-103">Update BizTalk host instance settings</span></span>

## <a name="overview"></a><span data-ttu-id="56ab0-104">概觀</span><span class="sxs-lookup"><span data-stu-id="56ab0-104">Overview</span></span>
<span data-ttu-id="56ab0-105">使用 [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)]，您就可以跨 BizTalk 群組修改指定主控件執行個體的組態資訊。</span><span class="sxs-lookup"><span data-stu-id="56ab0-105">Using the [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)], you can modify the configuration information of a given host instance, across a BizTalk group.</span></span> <span data-ttu-id="56ab0-106">此主題中提供的逐步程序，可讓您修改 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中的主控件執行個體層級效能設定。</span><span class="sxs-lookup"><span data-stu-id="56ab0-106">This topic provides the step-by-step procedure to modify the host instance level performance settings in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
 <span data-ttu-id="56ab0-107">您通常會將 BizTalk 設定 (來自來源環境) 儲存為 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="56ab0-107">Often you have the BizTalk settings (from a source environment) saved as an XML file.</span></span> <span data-ttu-id="56ab0-108">XML 檔案中包含的資訊可讓您複寫目標電腦上的設定。</span><span class="sxs-lookup"><span data-stu-id="56ab0-108">The XML file contains information that allows you to replicate the settings on the target machine.</span></span> <span data-ttu-id="56ab0-109">您可以將那些設定匯入「設定儀表板」，而不用設定新的值。</span><span class="sxs-lookup"><span data-stu-id="56ab0-109">You can import those settings to Settings Dashboard, instead of setting up new values.</span></span> <span data-ttu-id="56ab0-110">而另一方面，在為 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 設定新值之後，您可以將它們匯出成 XML 檔案，以用於另一部電腦。</span><span class="sxs-lookup"><span data-stu-id="56ab0-110">On the other hand, after setting up new values for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you can export them to an XML file to be used in another machine.</span></span>  
  
 <span data-ttu-id="56ab0-111">如需有關匯入詳細[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]設定，請參閱[匯入或匯出 BizTalk 設定使用設定儀表板](how-to-import-biztalk-settings-using-settings-dashboard.md)和[匯入或匯出 BizTalk 設定使用 BTSTask](how-to-import-biztalk-settings-using-btstask.md)。</span><span class="sxs-lookup"><span data-stu-id="56ab0-111">For information on importing the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] settings, see [Import or export BizTalk Settings Using Settings Dashboard](how-to-import-biztalk-settings-using-settings-dashboard.md) and [Import or export BizTalk Settings Using BTSTask](how-to-import-biztalk-settings-using-btstask.md).</span></span> 
  
## <a name="prerequisites"></a><span data-ttu-id="56ab0-112">必要條件</span><span class="sxs-lookup"><span data-stu-id="56ab0-112">Prerequisites</span></span>  
 <span data-ttu-id="56ab0-113">若要執行這項作業，您必須為 BizTalk Server 系統管理員群組的成員登入。</span><span class="sxs-lookup"><span data-stu-id="56ab0-113">To perform this operation, you must be signed in as a member of the BizTalk Server Administrators group.</span></span>  
  
## <a name="update-the-host-instance-level-settings"></a><span data-ttu-id="56ab0-114">更新主控件執行個體層級設定</span><span class="sxs-lookup"><span data-stu-id="56ab0-114">Update the host instance level settings</span></span>  
  
1.  <span data-ttu-id="56ab0-115">在**BizTalk Server 管理主控台**，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，以滑鼠右鍵按一下**BizTalk 群組**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="56ab0-115">In the **BizTalk Server Administration Console**, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], right-click **BizTalk Group**, and then click **Settings**.</span></span>  
  
2.  <span data-ttu-id="56ab0-116">在**BizTalk 設定儀表板**對話方塊**主控件執行個體**索引標籤上，執行下列任一項：</span><span class="sxs-lookup"><span data-stu-id="56ab0-116">In the **BizTalk Settings Dashboard** dialog box, on the **Host Instances** tab, do any of the following:</span></span>  
  
    -   <span data-ttu-id="56ab0-117">修改主控件執行個體的 .NET CLR 設定。</span><span class="sxs-lookup"><span data-stu-id="56ab0-117">Modify the .NET CLR settings for a host instance.</span></span> <span data-ttu-id="56ab0-118">請參閱[變更.NET CLR 設定](../core/how-to-modify-net-clr-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="56ab0-118">See [Change the .NET CLR Settings](../core/how-to-modify-net-clr-settings.md).</span></span>  
  
    -   <span data-ttu-id="56ab0-119">修改協調流程記憶體節流設定。</span><span class="sxs-lookup"><span data-stu-id="56ab0-119">Modify the orchestration memory throttling settings.</span></span> <span data-ttu-id="56ab0-120">請參閱[變更協調流程記憶體節流設定](../core/how-to-modify-orchestration-memory-throttling-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="56ab0-120">See [Change the Orchestration Memory Throttling Settings](../core/how-to-modify-orchestration-memory-throttling-settings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56ab0-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="56ab0-121">See Also</span></span>  
 [<span data-ttu-id="56ab0-122">使用設定儀表板，以便讓 BizTalk Server 效能調整</span><span class="sxs-lookup"><span data-stu-id="56ab0-122">Use Settings Dashboard for BizTalk Server Performance Tuning</span></span>](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md)