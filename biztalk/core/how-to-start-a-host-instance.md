---
title: 啟動主控件執行個體 |Microsoft 文件
description: 使用 BizTalk 管理 BizTalk Server 中啟動主控件執行個體
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a96a4362-2147-4b8e-a270-bf9a17477ba3
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dd5cccc48b33dda4b6458f8dfa8f56a84ad3cd62
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22255814"
---
# <a name="start-a-host-instance"></a><span data-ttu-id="e1aa3-103">啟動主控件執行個體</span><span class="sxs-lookup"><span data-stu-id="e1aa3-103">Start a Host Instance</span></span>
<span data-ttu-id="e1aa3-104">您可以使用 [[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台] 或 Windows Management Instrumentation (WMI) 來啟動主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="e1aa3-104">You can use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console or Windows Management Instrumentation (WMI) to start host instances.</span></span> <span data-ttu-id="e1aa3-105">在您新增或停止主控件執行個體之後，必須啟動它，這樣它才能執行，並將訊息路由至 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="e1aa3-105">After you add or stop a host instance, you must start it so that it is running and routing messages to the MessageBox databases.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e1aa3-106">您為主控件執行個體指定的服務帳戶應該是相關主控件 Windows 群組的成員。</span><span class="sxs-lookup"><span data-stu-id="e1aa3-106">The service account that you specify for a host instance should be a member of the Windows group for the associated host.</span></span> <span data-ttu-id="e1aa3-107">否則，主控件執行個體在執行階段可能沒有適當的權限或驗證。</span><span class="sxs-lookup"><span data-stu-id="e1aa3-107">Otherwise, the host instance may not have the appropriate permissions or authentication at run time.</span></span> <span data-ttu-id="e1aa3-108">此外，基於安全考量，帳戶應該要有最小權限，因為主控件執行個體裝載的協調流程可能會執行潛在的惡意自訂程式碼。</span><span class="sxs-lookup"><span data-stu-id="e1aa3-108">In addition, for security reasons, the account should have minimum privileges because orchestrations hosted by the host instance might execute potentially malicious custom code.</span></span>  
  
 <span data-ttu-id="e1aa3-109">如需主控件執行個體的詳細資訊，請參閱[主控件執行個體](../core/host-instances.md)。</span><span class="sxs-lookup"><span data-stu-id="e1aa3-109">For more information about host instances, see [Host Instances](../core/host-instances.md).</span></span> <span data-ttu-id="e1aa3-110">如需使用 WMI 啟動主控件執行個體的詳細資訊，請參閱**MSBTS_HostInstance (WMI)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="e1aa3-110">For information about using WMI to start a host instance, see **MSBTS_HostInstance (WMI)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
## <a name="prerequisites"></a><span data-ttu-id="e1aa3-111">必要條件</span><span class="sxs-lookup"><span data-stu-id="e1aa3-111">Prerequisites</span></span>  
 <span data-ttu-id="e1aa3-112">若要執行此程序，您必須以「系統管理員」群組及「BizTalk Server 系統管理員」群組的成員身分登入。</span><span class="sxs-lookup"><span data-stu-id="e1aa3-112">To perform this procedure, you must be logged on as a member of the Administrators group and the BizTalk Server Administrators group.</span></span>  
  
 <span data-ttu-id="e1aa3-113">此外，您也必須是下列資料庫所在伺服器的 db_securityadmin SQL Server 資料庫角色及 securityadmin SQL Server 角色的成員：</span><span class="sxs-lookup"><span data-stu-id="e1aa3-113">In addition, you must also be a member of the db_securityadmin SQL Server Database role and the securityadmin SQL Server Role on the server(s) where the following databases are:</span></span>  
  
-   <span data-ttu-id="e1aa3-114">BAM 主要匯入 (BAMPrimaryImport)</span><span class="sxs-lookup"><span data-stu-id="e1aa3-114">BAM Primary Import (BAMPrimaryImport)</span></span>  
  
-   <span data-ttu-id="e1aa3-115">BizTalk 管理 (BizTalkMgmtDb)</span><span class="sxs-lookup"><span data-stu-id="e1aa3-115">BizTalk Management (BizTalkMgmtDb)</span></span>  
  
-   <span data-ttu-id="e1aa3-116">BizTalk MessageBox (BizTalkMsgBoxDb) (全部)</span><span class="sxs-lookup"><span data-stu-id="e1aa3-116">BizTalk MessageBox (BizTalkMsgBoxDb) (all)</span></span>  
  
-   <span data-ttu-id="e1aa3-117">BizTalk 追蹤 (BizTalk DTADb)</span><span class="sxs-lookup"><span data-stu-id="e1aa3-117">BizTalk Tracking (BizTalk DTADb)</span></span>  
  
-   <span data-ttu-id="e1aa3-118">規則引擎 (BizTalkRuleEngineDb)</span><span class="sxs-lookup"><span data-stu-id="e1aa3-118">Rule Engine (BizTalkRuleEngineDb)</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="e1aa3-119">建議您使用 BizTalk Server 管理主控台或 Windows Management Instrumentation (WMI) 指令碼更新主控件執行個體的帳戶資訊。</span><span class="sxs-lookup"><span data-stu-id="e1aa3-119">We recommend that you update account information for host instances by using the BizTalk Server Administration Console or a Windows Management Instrumentation (WMI) script.</span></span> <span data-ttu-id="e1aa3-120">這樣可以確保 BizTalk Server 會更新 BizTalk Server 資料庫中的帳戶資訊，並且在資料庫和主控件執行個體之間維持同步的安全性組態。</span><span class="sxs-lookup"><span data-stu-id="e1aa3-120">This ensures that BizTalk Server can update the account information in the BizTalk Server databases and keep the security configuration between the databases and host instance synchronized.</span></span>  
  
## <a name="steps"></a><span data-ttu-id="e1aa3-121">步驟</span><span class="sxs-lookup"><span data-stu-id="e1aa3-121">Steps</span></span>
  
1.  <span data-ttu-id="e1aa3-122">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="e1aa3-122">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="e1aa3-123">在主控台樹狀目錄中，依序展開**BizTalk Server 管理**，展開 BizTalk 群組，按一下**平台設定**，然後按一下 **主控件執行個體**。</span><span class="sxs-lookup"><span data-stu-id="e1aa3-123">In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group, click **Platform Settings**, and then click **Host Instances**.</span></span>  
  
3.  <span data-ttu-id="e1aa3-124">在詳細資料窗格中，以滑鼠右鍵按一下您想要開始，然後按一下 主控件執行個體**啟動**。</span><span class="sxs-lookup"><span data-stu-id="e1aa3-124">In the details pane, right-click the host instance you want to start, and then click **Start**.</span></span>  
  
     <span data-ttu-id="e1aa3-125">主控件執行個體狀態會變更為**開始擱置**。</span><span class="sxs-lookup"><span data-stu-id="e1aa3-125">The status of the host instance changes to **Start pending**.</span></span> <span data-ttu-id="e1aa3-126">主控件執行個體啟動之後，狀態會變更為**執行**。</span><span class="sxs-lookup"><span data-stu-id="e1aa3-126">After the host instance initiates, the status changes to **Running**.</span></span>  
  
 <span data-ttu-id="e1aa3-127">在您啟動主控件執行個體之後，您可以停止它，以避免它將訊息遞送至 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="e1aa3-127">After you start a host instance, you can stop it to prevent it from routing messages to the MessageBox database.</span></span> <span data-ttu-id="e1aa3-128">您必須停止主控件執行個體，才能從指定的電腦移除 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="e1aa3-128">You must stop a host instance before you can remove BizTalk Server from a given computer.</span></span> <span data-ttu-id="e1aa3-129">如需停止主控件執行個體的詳細資訊，請參閱[如何停止主控件執行個體](../core/how-to-stop-a-host-instance.md)。</span><span class="sxs-lookup"><span data-stu-id="e1aa3-129">For information about stopping a host instance, see [How to Stop a Host Instance](../core/how-to-stop-a-host-instance.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1aa3-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1aa3-130">See Also</span></span>  
 <span data-ttu-id="e1aa3-131">[管理 BizTalk 主控件和主控件執行個體](../core/managing-biztalk-hosts-and-host-instances.md) </span><span class="sxs-lookup"><span data-stu-id="e1aa3-131">[Managing BizTalk Hosts and Host Instances](../core/managing-biztalk-hosts-and-host-instances.md) </span></span>  
 <span data-ttu-id="e1aa3-132">[新增主控件執行個體](../core/how-to-add-a-host-instance.md) </span><span class="sxs-lookup"><span data-stu-id="e1aa3-132">[Add a Host Instance](../core/how-to-add-a-host-instance.md) </span></span>  
 <span data-ttu-id="e1aa3-133">[停止主控件執行個體](../core/how-to-stop-a-host-instance.md) </span><span class="sxs-lookup"><span data-stu-id="e1aa3-133">[Stop a Host Instance](../core/how-to-stop-a-host-instance.md) </span></span>  
 <span data-ttu-id="e1aa3-134">[刪除主控件執行個體](../core/how-to-delete-a-host-instance.md) </span><span class="sxs-lookup"><span data-stu-id="e1aa3-134">[Delete a Host Instance](../core/how-to-delete-a-host-instance.md) </span></span>  
 [<span data-ttu-id="e1aa3-135">修改主控件執行個體屬性</span><span class="sxs-lookup"><span data-stu-id="e1aa3-135">Modify Host Instance Properties</span></span>](../core/how-to-modify-host-instance-properties.md)