---
title: 停止主控件執行個體 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c1f2e0c1-a387-4182-82ef-e25f49ac509b
caps.latest.revision: 20
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 837b08c30263b48ad481c7e03820cfba0b6c0ecc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22255502"
---
# <a name="stop-a-host-instance"></a><span data-ttu-id="1f3f4-102">停止主控件執行個體</span><span class="sxs-lookup"><span data-stu-id="1f3f4-102">Stop a Host Instance</span></span>

## <a name="overview"></a><span data-ttu-id="1f3f4-103">概觀</span><span class="sxs-lookup"><span data-stu-id="1f3f4-103">Overview</span></span>
<span data-ttu-id="1f3f4-104">您可以使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台或 Windows Management Instrumentation (WMI)，來停止主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="1f3f4-104">You can use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console or Windows Management Instrumentation (WMI) to stop host instances.</span></span> <span data-ttu-id="1f3f4-105">您必須停止主控件執行個體，才能從電腦中刪除它或移除 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="1f3f4-105">You must stop a host instance before you can delete it or remove BizTalk Server from a computer.</span></span> <span data-ttu-id="1f3f4-106">您可以停止已安裝與啟動的主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="1f3f4-106">You can stop a host instance that is installed and started.</span></span> <span data-ttu-id="1f3f4-107">如需主控件執行個體的詳細資訊，請參閱[主控件執行個體](../core/host-instances.md)。</span><span class="sxs-lookup"><span data-stu-id="1f3f4-107">For more information about host instances, see [Host Instances](../core/host-instances.md).</span></span>  
  
 <span data-ttu-id="1f3f4-108">如需使用 WMI 來停止主控件執行個體資訊，請參閱**MSBTS_HostInstance (WMI)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="1f3f4-108">For information about using WMI to stop a host instance, see **MSBTS_HostInstance (WMI)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
## <a name="prerequisites"></a><span data-ttu-id="1f3f4-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="1f3f4-109">Prerequisites</span></span>  
 <span data-ttu-id="1f3f4-110">若要執行此程序，您必須以「系統管理員」群組及「BizTalk Server 系統管理員」群組的成員身分登入。</span><span class="sxs-lookup"><span data-stu-id="1f3f4-110">To perform this procedure, you must be logged on as a member of the Administrators group and the BizTalk Server Administrators group.</span></span>  
  
 <span data-ttu-id="1f3f4-111">此外，您也必須是下列資料庫所在伺服器的 db_securityadmin SQL Server 資料庫角色及 securityadmin SQL Server 角色的成員：</span><span class="sxs-lookup"><span data-stu-id="1f3f4-111">In addition, you must also be a member of the db_securityadmin SQL Server Database role and the securityadmin SQL Server Role on the server(s) where the following databases are:</span></span>  
  
-   <span data-ttu-id="1f3f4-112">BAM 主要匯入 (BAMPrimaryImport)</span><span class="sxs-lookup"><span data-stu-id="1f3f4-112">BAM Primary Import (BAMPrimaryImport)</span></span>  
  
-   <span data-ttu-id="1f3f4-113">BizTalk 管理 (BizTalkMgmtDb)</span><span class="sxs-lookup"><span data-stu-id="1f3f4-113">BizTalk Management (BizTalkMgmtDb)</span></span>  
  
-   <span data-ttu-id="1f3f4-114">BizTalk MessageBox (BizTalkMsgBoxDb) (全部)</span><span class="sxs-lookup"><span data-stu-id="1f3f4-114">BizTalk MessageBox (BizTalkMsgBoxDb) (all)</span></span>  
  
-   <span data-ttu-id="1f3f4-115">BizTalk 追蹤 (BizTalk DTADb)</span><span class="sxs-lookup"><span data-stu-id="1f3f4-115">BizTalk Tracking (BizTalk DTADb)</span></span>  
  
-   <span data-ttu-id="1f3f4-116">規則引擎 (BizTalkRuleEngineDb)</span><span class="sxs-lookup"><span data-stu-id="1f3f4-116">Rule Engine (BizTalkRuleEngineDb)</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="1f3f4-117">建議您使用 BizTalk Server 管理主控台或 Windows Management Instrumentation (WMI) 指令碼更新主控件執行個體的帳戶資訊。</span><span class="sxs-lookup"><span data-stu-id="1f3f4-117">We recommend that you update account information for host instances by using the BizTalk Server Administration Console or a Windows Management Instrumentation (WMI) script.</span></span> <span data-ttu-id="1f3f4-118">這樣可以確保 BizTalk Server 會更新 BizTalk Server 資料庫中的帳戶資訊，並且在資料庫和主控件執行個體之間維持同步的安全性組態。</span><span class="sxs-lookup"><span data-stu-id="1f3f4-118">This ensures that BizTalk Server can update the account information in the BizTalk Server databases and keep the security configuration between the databases and host instance synchronized.</span></span>  
  
## <a name="steps"></a><span data-ttu-id="1f3f4-119">步驟</span><span class="sxs-lookup"><span data-stu-id="1f3f4-119">Steps</span></span>
  
1.  <span data-ttu-id="1f3f4-120">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="1f3f4-120">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="1f3f4-121">在主控台樹狀目錄中，依序展開**BizTalk Server 管理**，展開 BizTalk 群組，按一下**平台設定**，然後按一下 **主控件執行個體**。</span><span class="sxs-lookup"><span data-stu-id="1f3f4-121">In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group, click **Platform Settings**, and then click **Host Instances**.</span></span>  
  
3.  <span data-ttu-id="1f3f4-122">在詳細資料窗格中，以滑鼠右鍵按一下您想要停止]，然後按一下 [主控件執行個體**停止**。</span><span class="sxs-lookup"><span data-stu-id="1f3f4-122">In the details pane, right-click the host instance you want to stop, and then click **Stop**.</span></span>  
  
     <span data-ttu-id="1f3f4-123">主控件執行個體狀態會變更為**已停止**。</span><span class="sxs-lookup"><span data-stu-id="1f3f4-123">The status of the host instance changes to **Stopped**.</span></span>  
  
 <span data-ttu-id="1f3f4-124">在您停止主控件執行個體之後，您可以啟動、刪除它或從電腦中移除 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="1f3f4-124">After you stop a host instance, you can start it, delete it, or remove BizTalk Server from the computer.</span></span> <span data-ttu-id="1f3f4-125">如需啟動主控件執行個體的相關資訊，請參閱[如何啟動主控件執行個體](../core/how-to-start-a-host-instance.md)。</span><span class="sxs-lookup"><span data-stu-id="1f3f4-125">For information about starting a host instance, see [How to Start a Host Instance](../core/how-to-start-a-host-instance.md).</span></span> <span data-ttu-id="1f3f4-126">如需刪除主控件執行個體的詳細資訊，請參閱[如何刪除主控件執行個體](../core/how-to-delete-a-host-instance.md)。</span><span class="sxs-lookup"><span data-stu-id="1f3f4-126">For information about deleting a host instance, see [How to Delete a Host Instance](../core/how-to-delete-a-host-instance.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f3f4-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1f3f4-127">See Also</span></span>  
 <span data-ttu-id="1f3f4-128">[管理 BizTalk 主控件和主控件執行個體](../core/managing-biztalk-hosts-and-host-instances.md) </span><span class="sxs-lookup"><span data-stu-id="1f3f4-128">[Managing BizTalk Hosts and Host Instances](../core/managing-biztalk-hosts-and-host-instances.md) </span></span>  
 <span data-ttu-id="1f3f4-129">[如何新增主控件執行個體](../core/how-to-add-a-host-instance.md) </span><span class="sxs-lookup"><span data-stu-id="1f3f4-129">[How to Add a Host Instance](../core/how-to-add-a-host-instance.md) </span></span>  
 <span data-ttu-id="1f3f4-130">[如何啟動主控件執行個體](../core/how-to-start-a-host-instance.md) </span><span class="sxs-lookup"><span data-stu-id="1f3f4-130">[How to Start a Host Instance](../core/how-to-start-a-host-instance.md) </span></span>  
 <span data-ttu-id="1f3f4-131">[如何刪除主控件執行個體](../core/how-to-delete-a-host-instance.md) </span><span class="sxs-lookup"><span data-stu-id="1f3f4-131">[How to Delete a Host Instance](../core/how-to-delete-a-host-instance.md) </span></span>  
 [<span data-ttu-id="1f3f4-132">如何修改主控件執行個體屬性</span><span class="sxs-lookup"><span data-stu-id="1f3f4-132">How to Modify Host Instance Properties</span></span>](../core/how-to-modify-host-instance-properties.md)