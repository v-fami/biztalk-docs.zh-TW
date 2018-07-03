---
title: 如何修改主控件設定 |Microsoft Docs
description: 變更以改善效能和節流設定的 BizTalk Server 管理 中的 BizTalk 主控件設定
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0759b3a0-560e-4a11-92e6-9de0e15f463b
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 93b2ea993e044d1cb18efcc73f631e8ba3fcb8ff
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36975839"
---
# <a name="update-biztalk-host-settings"></a><span data-ttu-id="8ba69-103">更新 BizTalk 主控件設定</span><span class="sxs-lookup"><span data-stu-id="8ba69-103">Update BizTalk host settings</span></span>

## <a name="overview"></a><span data-ttu-id="8ba69-104">概觀</span><span class="sxs-lookup"><span data-stu-id="8ba69-104">Overview</span></span>
<span data-ttu-id="8ba69-105">您可以使用「設定儀表板」修改某個主控件在整個 BizTalk 群組中的組態資訊。</span><span class="sxs-lookup"><span data-stu-id="8ba69-105">Using the Settings Dashboard, you can modify the configuration information of a given host, across a BizTalk group.</span></span> <span data-ttu-id="8ba69-106">本主題提供在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中修改主控件層級效能設定的逐步程序。</span><span class="sxs-lookup"><span data-stu-id="8ba69-106">This topic provides the step-by-step procedure to modify the host-level performance settings in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8ba69-107">您也可以修改群組與主控件執行個體設定。</span><span class="sxs-lookup"><span data-stu-id="8ba69-107">You can also modify the group and host instance settings.</span></span> <span data-ttu-id="8ba69-108">如需有關如何修改設定的資訊，請參閱[使用設定儀表板進行 BizTalk Server 效能調整](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md)。</span><span class="sxs-lookup"><span data-stu-id="8ba69-108">For information about how to modify the settings, see [Using Settings Dashboard for BizTalk Server Performance Tuning](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md).</span></span>  
  
 <span data-ttu-id="8ba69-109">您可以將目前的 BizTalk Server 設定匯出至 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="8ba69-109">The current BizTalk Server settings can be exported to an XML file.</span></span> <span data-ttu-id="8ba69-110">稍後您可以將這些設定匯入到「設定儀表板」，而不需設定新值。</span><span class="sxs-lookup"><span data-stu-id="8ba69-110">Later, you can import those settings to the Settings Dashboard instead of setting up new values.</span></span> <span data-ttu-id="8ba69-111">如需匯入[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]設定，請參閱[匯入或匯出 BizTalk 設定使用設定儀表板](how-to-import-biztalk-settings-using-settings-dashboard.md)並[匯入或匯出 BizTalk 設定使用 BTSTask](how-to-import-biztalk-settings-using-btstask.md)。</span><span class="sxs-lookup"><span data-stu-id="8ba69-111">For information on importing the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] settings, see [Import or export BizTalk Settings Using Settings Dashboard](how-to-import-biztalk-settings-using-settings-dashboard.md) and [Import or export BizTalk Settings Using BTSTask](how-to-import-biztalk-settings-using-btstask.md).</span></span> 
  
## <a name="prerequisites"></a><span data-ttu-id="8ba69-112">必要條件</span><span class="sxs-lookup"><span data-stu-id="8ba69-112">Prerequisites</span></span>  
 <span data-ttu-id="8ba69-113">若要執行這項作業，您必須為 BizTalk Server 系統管理員群組的成員登入。</span><span class="sxs-lookup"><span data-stu-id="8ba69-113">To perform this operation, you must be signed in as a member of the BizTalk Server Administrators group.</span></span>  
  
## <a name="update-the-host-level-settings"></a><span data-ttu-id="8ba69-114">更新的主機層級設定</span><span class="sxs-lookup"><span data-stu-id="8ba69-114">Update the host-level settings</span></span>  
  
1. <span data-ttu-id="8ba69-115">在  **BizTalk Server 管理主控台**，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，以滑鼠右鍵按一下**BizTalk 群組**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="8ba69-115">In the **BizTalk Server Administration Console**, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], right-click **BizTalk Group**, and then click **Settings**.</span></span>  
  
2. <span data-ttu-id="8ba69-116">在  **BizTalk 設定儀表板**對話方塊的 **主機**頁面上，執行下列一或多個項目。</span><span class="sxs-lookup"><span data-stu-id="8ba69-116">In the **BizTalk Settings Dashboard** dialog box, on the **Hosts** page, do one or more of the following.</span></span>  
  
   -   <span data-ttu-id="8ba69-117">修改 BizTalk 主控件的一般效能設定。</span><span class="sxs-lookup"><span data-stu-id="8ba69-117">Modify the general performance settings of the BizTalk host.</span></span> <span data-ttu-id="8ba69-118">請參閱[如何修改一般設定](../core/how-to-modify-general-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="8ba69-118">See [How to Modify General Settings](../core/how-to-modify-general-settings.md).</span></span>  
  
   -   <span data-ttu-id="8ba69-119">修改 BizTalk 主控件的資源型節流設定。</span><span class="sxs-lookup"><span data-stu-id="8ba69-119">Modify the resource-based throttling settings of the BizTalk host.</span></span> <span data-ttu-id="8ba69-120">請參閱[如何修改資源型節流設定](../core/how-to-modify-resource-based-throttling-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="8ba69-120">See [How to Modify Resource Based Throttling Settings](../core/how-to-modify-resource-based-throttling-settings.md).</span></span>  
  
   -   <span data-ttu-id="8ba69-121">修改 BizTalk 主控件，根據速率的節流設定。</span><span class="sxs-lookup"><span data-stu-id="8ba69-121">Modify the rate-based throttling settings of the BizTalk host.</span></span> <span data-ttu-id="8ba69-122">請參閱[如何修改速率型節流設定](../core/how-to-modify-rate-based-throttling-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="8ba69-122">See [How to Modify Rate Based Throttling Settings](../core/how-to-modify-rate-based-throttling-settings.md).</span></span>  
  
   -   <span data-ttu-id="8ba69-123">修改 BizTalk 主控件的協調流程節流設定。</span><span class="sxs-lookup"><span data-stu-id="8ba69-123">Modify the orchestration throttling settings of the BizTalk host.</span></span> <span data-ttu-id="8ba69-124">請參閱[如何修改協調流程節流設定](../core/how-to-modify-orchestration-throttling-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="8ba69-124">See [How to Modify Orchestration Throttling Settings](../core/how-to-modify-orchestration-throttling-settings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ba69-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ba69-125">See Also</span></span>  
 [<span data-ttu-id="8ba69-126">使用設定儀表板調整 BizTalk Server 效能</span><span class="sxs-lookup"><span data-stu-id="8ba69-126">Use Settings Dashboard for BizTalk Server Performance Tuning</span></span>](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md)