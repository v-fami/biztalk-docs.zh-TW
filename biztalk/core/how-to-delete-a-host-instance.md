---
title: 刪除主控件執行個體 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 35a06480-0962-4bdc-add2-56f979a2f1c9
caps.latest.revision: 23
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 798ea341ef61b15729dd15742eef7701641e7547
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22249198"
---
# <a name="delete-a-host-instance"></a><span data-ttu-id="5f075-102">刪除主控件執行個體</span><span class="sxs-lookup"><span data-stu-id="5f075-102">Delete a Host Instance</span></span>

## <a name="overview"></a><span data-ttu-id="5f075-103">概觀</span><span class="sxs-lookup"><span data-stu-id="5f075-103">Overview</span></span>
<span data-ttu-id="5f075-104">您可以使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台或 Windows Management Instrumentation (WMI) 刪除主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="5f075-104">You can use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console or Windows Management Instrumentation (WMI) to delete host instances.</span></span> <span data-ttu-id="5f075-105">如需主控件執行個體的詳細資訊，請參閱[主控件執行個體](../core/host-instances.md)。</span><span class="sxs-lookup"><span data-stu-id="5f075-105">For more information about host instances, see [Host Instances](../core/host-instances.md).</span></span> <span data-ttu-id="5f075-106">如需使用 WMI 刪除主控件執行個體的詳細資訊，請參閱**MSBTS_HostInstance (WMI)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="5f075-106">For information about using WMI to delete a host instance, see **MSBTS_HostInstance (WMI)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
 <span data-ttu-id="5f075-107">刪除主控件執行個體時，會從關聯的伺服器移除 BizTalk Server 執行階段的執行個體，且會更新 [BizTalk 管理] 資料庫，以從主控件移除該執行個體。</span><span class="sxs-lookup"><span data-stu-id="5f075-107">When you delete a host instance, the instance of the BizTalk Server runtime is removed from the associated server and the BizTalk Management database is updated to remove that instance from the host.</span></span>  
  
 <span data-ttu-id="5f075-108">為避免在刪除主控件執行個體時遺失訊息，BizTalk Server 會在實際移除執行個體之前完成所有處理作業。</span><span class="sxs-lookup"><span data-stu-id="5f075-108">To avoid losing messages when you delete a host instance, BizTalk Server completes all processing before the instance is actually removed.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="5f075-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="5f075-109">Prerequisites</span></span>  
 <span data-ttu-id="5f075-110">若要執行此程序，您必須以「系統管理員」群組及「BizTalk Server 系統管理員」群組的成員身分登入。</span><span class="sxs-lookup"><span data-stu-id="5f075-110">To perform this procedure, you must be logged on as a member of the Administrators group and the BizTalk Server Administrators group.</span></span>  
  
 <span data-ttu-id="5f075-111">此外，您也必須是下列資料庫所在伺服器的 db_securityadmin SQL Server 資料庫角色及 securityadmin SQL Server 角色的成員：</span><span class="sxs-lookup"><span data-stu-id="5f075-111">In addition, you must also be a member of the db_securityadmin SQL Server Database role and the securityadmin SQL Server Role on the server(s) where the following databases are:</span></span>  
  
-   <span data-ttu-id="5f075-112">BAM 主要匯入 (BAMPrimaryImport)</span><span class="sxs-lookup"><span data-stu-id="5f075-112">BAM Primary Import (BAMPrimaryImport)</span></span>  
  
-   <span data-ttu-id="5f075-113">BizTalk 管理 (BizTalkMgmtDb)</span><span class="sxs-lookup"><span data-stu-id="5f075-113">BizTalk Management (BizTalkMgmtDb)</span></span>  
  
-   <span data-ttu-id="5f075-114">BizTalk MessageBox (BizTalkMsgBoxDb) (全部)</span><span class="sxs-lookup"><span data-stu-id="5f075-114">BizTalk MessageBox (BizTalkMsgBoxDb) (all)</span></span>  
  
-   <span data-ttu-id="5f075-115">BizTalk 追蹤 (BizTalk DTADb)</span><span class="sxs-lookup"><span data-stu-id="5f075-115">BizTalk Tracking (BizTalk DTADb)</span></span>  
  
-   <span data-ttu-id="5f075-116">規則引擎 (BizTalkRuleEngineDb)</span><span class="sxs-lookup"><span data-stu-id="5f075-116">Rule Engine (BizTalkRuleEngineDb)</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="5f075-117">建議您使用 BizTalk Server 管理主控台或 Windows Management Instrumentation (WMI) 指令碼更新主控件執行個體的帳戶資訊。</span><span class="sxs-lookup"><span data-stu-id="5f075-117">We recommend that you update account information for host instances by using the BizTalk Server Administration Console or a Windows Management Instrumentation (WMI) script.</span></span> <span data-ttu-id="5f075-118">這樣可以確保 BizTalk Server 會更新 BizTalk Server 資料庫中的帳戶資訊，並且在資料庫和主控件執行個體之間維持同步的安全性組態。</span><span class="sxs-lookup"><span data-stu-id="5f075-118">This ensures that BizTalk Server can update the account information in the BizTalk Server databases and keep the security configuration between the databases and host instance synchronized.</span></span>  
  
## <a name="steps"></a><span data-ttu-id="5f075-119">步驟</span><span class="sxs-lookup"><span data-stu-id="5f075-119">Steps</span></span>
  
1.  <span data-ttu-id="5f075-120">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="5f075-120">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="5f075-121">在主控台樹狀目錄中，依序展開**BizTalk Server 管理**，展開 BizTalk 群組，按一下**平台設定**，然後按一下 **主控件執行個體**。</span><span class="sxs-lookup"><span data-stu-id="5f075-121">In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group, click **Platform Settings**, and then click **Host Instances**.</span></span>  
  
3.  <span data-ttu-id="5f075-122">在詳細資料窗格中，以滑鼠右鍵按一下您想要刪除，然後按一下 主控件執行個體**刪除**。</span><span class="sxs-lookup"><span data-stu-id="5f075-122">In the details pane, right-click the host instance you want to delete, and then click **Delete**.</span></span>  
  
4.  <span data-ttu-id="5f075-123">在**確認刪除主控件執行個體**對話方塊中，按一下 **是**。</span><span class="sxs-lookup"><span data-stu-id="5f075-123">In the **Confirm delete host instance** dialog box, click **Yes**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5f075-124">若 BizTalk Server 無法刪除主控件執行個體，則會顯示一個對話方塊，您可以在其中強制刪除主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="5f075-124">If BizTalk Server cannot delete the host instance, a dialog box appears in which you can force the deletion of the host instance.</span></span> <span data-ttu-id="5f075-125">閱讀所提供的資訊之後, 按**是**刪除主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="5f075-125">After reading the information provided, click **Yes** to delete the host instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f075-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f075-126">See Also</span></span>  
 <span data-ttu-id="5f075-127">[管理 BizTalk 主控件和主控件執行個體](../core/managing-biztalk-hosts-and-host-instances.md) </span><span class="sxs-lookup"><span data-stu-id="5f075-127">[Managing BizTalk Hosts and Host Instances](../core/managing-biztalk-hosts-and-host-instances.md) </span></span>  
 <span data-ttu-id="5f075-128">[如何新增主控件執行個體](../core/how-to-add-a-host-instance.md) </span><span class="sxs-lookup"><span data-stu-id="5f075-128">[How to Add a Host Instance](../core/how-to-add-a-host-instance.md) </span></span>  
 <span data-ttu-id="5f075-129">[如何啟動主控件執行個體](../core/how-to-start-a-host-instance.md) </span><span class="sxs-lookup"><span data-stu-id="5f075-129">[How to Start a Host Instance](../core/how-to-start-a-host-instance.md) </span></span>  
 <span data-ttu-id="5f075-130">[如何停止主控件執行個體](../core/how-to-stop-a-host-instance.md) </span><span class="sxs-lookup"><span data-stu-id="5f075-130">[How to Stop a Host Instance](../core/how-to-stop-a-host-instance.md) </span></span>  
 [<span data-ttu-id="5f075-131">如何修改主控件執行個體屬性</span><span class="sxs-lookup"><span data-stu-id="5f075-131">How to Modify Host Instance Properties</span></span>](../core/how-to-modify-host-instance-properties.md)