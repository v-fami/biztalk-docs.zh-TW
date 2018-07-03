---
title: 變更主控件執行個體屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a35ca0c8-89b3-483a-b2fc-c8f43a8864d1
caps.latest.revision: 22
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 53a64257f752e161963539256dcaca3f7f8f1077
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37003343"
---
# <a name="update-host-instance-properties"></a><span data-ttu-id="56e7e-102">更新主控件執行個體屬性</span><span class="sxs-lookup"><span data-stu-id="56e7e-102">Update Host Instance Properties</span></span>

## <a name="overview"></a><span data-ttu-id="56e7e-103">概觀</span><span class="sxs-lookup"><span data-stu-id="56e7e-103">Overview</span></span>
<span data-ttu-id="56e7e-104">您可以使用 BizTalk Server 管理主控台或 Windows Management Instrumentation (WMI) 來修改主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="56e7e-104">You can use the BizTalk Server Administration Console or Windows Management Instrumentation (WMI) to modify host instances.</span></span> <span data-ttu-id="56e7e-105">您可以修改執行主控件執行個體的服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="56e7e-105">You can modify the service account running a host instance.</span></span> <span data-ttu-id="56e7e-106">您也可以停用主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="56e7e-106">You can also disable a host instance.</span></span> <span data-ttu-id="56e7e-107">例如，若您想要保留主控件執行個體的設定，但不想將它啟動，您可以停用它。</span><span class="sxs-lookup"><span data-stu-id="56e7e-107">For example, if you want to preserve the settings for a host instance and you do not want it to start, you can disable it.</span></span> <span data-ttu-id="56e7e-108">如需主控件執行個體的詳細資訊，請參閱[主控件執行個體](../core/host-instances.md)。</span><span class="sxs-lookup"><span data-stu-id="56e7e-108">For more information about host instances, see [Host Instances](../core/host-instances.md).</span></span>  
  
 <span data-ttu-id="56e7e-109">信任與不信任的主控件之主控件執行個體無法使用相同的服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="56e7e-109">Host instances of trusted hosts and host instances of non-trusted hosts cannot use the same service accounts.</span></span> <span data-ttu-id="56e7e-110">若您想要變更主控件執行個體的信任設定，而主控件執行個體使用其他主控件執行個體使用的服務帳戶，您可以執行下列任何一項動作：</span><span class="sxs-lookup"><span data-stu-id="56e7e-110">If you want to change the trust setting of a host instance and the host instance uses a service account that other host instances use, you can do one of the following:</span></span>  
  
-   <span data-ttu-id="56e7e-111">您可以變更主控件執行個體的服務帳戶，將該主控件執行個體的信任設定變更為新的服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="56e7e-111">You can change the service account of the host instance for which you want to change the trust settings to a new service account.</span></span>  
  
-   <span data-ttu-id="56e7e-112">您可以將主控件執行個體的服務帳戶變更為其他具有相同信任設定的主控件執行個體所使用的現有服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="56e7e-112">You can change the service account of the host instance to an existing service account that other host instances with the same trust setting use.</span></span>  
  
-   <span data-ttu-id="56e7e-113">您可以刪除主控件執行個體，然後以不同的信任設定與服務帳戶重新建立它。</span><span class="sxs-lookup"><span data-stu-id="56e7e-113">You can delete the host instance, and re-create it with a different trust setting and service account.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="56e7e-114">您必須更新主控件執行個體的屬性來變更主控件執行個體的認證。</span><span class="sxs-lookup"><span data-stu-id="56e7e-114">You must change the credentials for a host instance by updating the properties of the host instance.</span></span> <span data-ttu-id="56e7e-115">如果您變更對應服務的認證，則您為主控件執行個體指定的服務帳戶必須是主控件上的群組成員。</span><span class="sxs-lookup"><span data-stu-id="56e7e-115">If you change the credentials of the corresponding service, the service account you specify for the host instance must be a member of the group on the host.</span></span> <span data-ttu-id="56e7e-116">請不要使用「服務」嵌入式管理單元或「電腦管理」主控台來變更主控件執行個體的認證，否則主控件執行個體可能無法正確運作。</span><span class="sxs-lookup"><span data-stu-id="56e7e-116">Do not use the Services snap-in or the Computer Management console to change the credentials of host instance, otherwise the host instance may not function properly.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="56e7e-117">若您變更主控件執行個體的認證，也必須變更對應的 SQL Server 認證。</span><span class="sxs-lookup"><span data-stu-id="56e7e-117">If you change the credentials of a host instance, you must also change the corresponding SQL Server credentials.</span></span> <span data-ttu-id="56e7e-118">若您不更新 SQL Server 認證，主控件執行個體將不會正確運作。</span><span class="sxs-lookup"><span data-stu-id="56e7e-118">If you do not update the SQL Server credentials, the host instance will not function properly.</span></span>  
  
 <span data-ttu-id="56e7e-119">如需使用 WMI 修改主控件執行個體的資訊，請參閱**MSBTS_HostInstance (WMI)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="56e7e-119">For information about using WMI to modify a host instance, see **MSBTS_HostInstance (WMI)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
## <a name="prerequisites"></a><span data-ttu-id="56e7e-120">必要條件</span><span class="sxs-lookup"><span data-stu-id="56e7e-120">Prerequisites</span></span>  
 <span data-ttu-id="56e7e-121">若要執行此程序，您必須以「系統管理員」群組及「BizTalk Server 系統管理員」群組的成員身分登入。</span><span class="sxs-lookup"><span data-stu-id="56e7e-121">To perform this procedure, you must be logged on as a member of the Administrators group and the BizTalk Server Administrators group.</span></span>  
  
 <span data-ttu-id="56e7e-122">此外，您也必須是下列資料庫所在伺服器的 db_securityadmin SQL Server 資料庫角色及 securityadmin SQL Server 角色的成員：</span><span class="sxs-lookup"><span data-stu-id="56e7e-122">In addition, you must also be a member of the db_securityadmin SQL Server Database role and the securityadmin SQL Server Role on the server(s) where the following databases are:</span></span>  
  
-   <span data-ttu-id="56e7e-123">BAM 主要匯入 (BAMPrimaryImport)</span><span class="sxs-lookup"><span data-stu-id="56e7e-123">BAM Primary Import (BAMPrimaryImport)</span></span>  
  
-   <span data-ttu-id="56e7e-124">BizTalk 管理 (BizTalkMgmtDb)</span><span class="sxs-lookup"><span data-stu-id="56e7e-124">BizTalk Management (BizTalkMgmtDb)</span></span>  
  
-   <span data-ttu-id="56e7e-125">BizTalk MessageBox (BizTalkMsgBoxDb) (全部)</span><span class="sxs-lookup"><span data-stu-id="56e7e-125">BizTalk MessageBox (BizTalkMsgBoxDb) (all)</span></span>  
  
-   <span data-ttu-id="56e7e-126">BizTalk 追蹤 (BizTalk DTADb)</span><span class="sxs-lookup"><span data-stu-id="56e7e-126">BizTalk Tracking (BizTalk DTADb)</span></span>  
  
-   <span data-ttu-id="56e7e-127">規則引擎 (BizTalkRuleEngineDb)</span><span class="sxs-lookup"><span data-stu-id="56e7e-127">Rule Engine (BizTalkRuleEngineDb)</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="56e7e-128">建議您使用 BizTalk Server 管理主控台或 Windows Management Instrumentation (WMI) 指令碼更新主控件執行個體的帳戶資訊。</span><span class="sxs-lookup"><span data-stu-id="56e7e-128">We recommend that you update account information for host instances by using the BizTalk Server Administration Console or a Windows Management Instrumentation (WMI) script.</span></span> <span data-ttu-id="56e7e-129">這樣可以確保 BizTalk Server 會更新 BizTalk Server 資料庫中的帳戶資訊，並且在資料庫和主控件執行個體之間維持同步的安全性組態。</span><span class="sxs-lookup"><span data-stu-id="56e7e-129">This ensures that BizTalk Server can update the account information in the BizTalk Server databases and keep the security configuration between the databases and host instance synchronized.</span></span>  
  
## <a name="steps"></a><span data-ttu-id="56e7e-130">步驟</span><span class="sxs-lookup"><span data-stu-id="56e7e-130">Steps</span></span>
  
1. <span data-ttu-id="56e7e-131">按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="56e7e-131">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2. <span data-ttu-id="56e7e-132">在主控台樹狀目錄中，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]、 BizTalk 群組，按一下**平台設定**，然後按一下**主控件執行個體**。</span><span class="sxs-lookup"><span data-stu-id="56e7e-132">In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the BizTalk group, click **Platform Settings**, and then click **Host Instances**.</span></span>  
  
3. <span data-ttu-id="56e7e-133">在 詳細資料 窗格中，以滑鼠右鍵按一下您要修改，然後按一下 主控件執行個體**屬性**。</span><span class="sxs-lookup"><span data-stu-id="56e7e-133">In the details pane, right-click the host instance you want to modify, and then click **Properties**.</span></span>  
  
4. <span data-ttu-id="56e7e-134">在 [**主控件執行個體屬性**] 對話方塊中，按一下**設定**修改服務帳戶資訊。</span><span class="sxs-lookup"><span data-stu-id="56e7e-134">In the **Host Instance Properties** dialog box, click **Configure** to modify the service account information.</span></span>  
  
5. <span data-ttu-id="56e7e-135">在 **登入認證**對話方塊方塊中，輸入帳戶名稱和密碼的帳戶底下的主控件執行個體將會執行，，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="56e7e-135">In the **Logon Credentials** dialog box, enter the account name and password of the account under which the host instance will run, and then click **OK**.</span></span>  
  
6. <span data-ttu-id="56e7e-136">在 [**主控件執行個體屬性**] 對話方塊中，執行下列命令，，然後按一下**確定**:</span><span class="sxs-lookup"><span data-stu-id="56e7e-136">In the **Host Instance Properties** dialog box, do the following, and then click **OK**:</span></span>  
  
   |<span data-ttu-id="56e7e-137">使用</span><span class="sxs-lookup"><span data-stu-id="56e7e-137">Use this</span></span>|<span data-ttu-id="56e7e-138">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="56e7e-138">To do this</span></span>|  
   |--------------|----------------|  
   |<span data-ttu-id="56e7e-139">**主機名稱**</span><span class="sxs-lookup"><span data-stu-id="56e7e-139">**Host name**</span></span>|<span data-ttu-id="56e7e-140">顯示和所選取的伺服器相關聯的主控件名稱。</span><span class="sxs-lookup"><span data-stu-id="56e7e-140">Displays the name of the host associated with the selected server.</span></span>|  
   |<span data-ttu-id="56e7e-141">**Server**</span><span class="sxs-lookup"><span data-stu-id="56e7e-141">**Server**</span></span>|<span data-ttu-id="56e7e-142">顯示與所選取的主控件相關聯的伺服器。</span><span class="sxs-lookup"><span data-stu-id="56e7e-142">Displays the server associated with the selected host.</span></span>|  
   |<span data-ttu-id="56e7e-143">**登入**</span><span class="sxs-lookup"><span data-stu-id="56e7e-143">**Logon**</span></span>|<span data-ttu-id="56e7e-144">顯示將執行主控件執行個體的新服務帳戶之帳戶名稱。</span><span class="sxs-lookup"><span data-stu-id="56e7e-144">Displays the account name of the new service account under which the host instance will run.</span></span>|  
   |<span data-ttu-id="56e7e-145">**設定**</span><span class="sxs-lookup"><span data-stu-id="56e7e-145">**Configure**</span></span>|<span data-ttu-id="56e7e-146">按一下即可顯示**登入認證**對話方塊中，您可以在其中輸入的帳戶名稱和密碼將執行主控件執行個體的帳戶。</span><span class="sxs-lookup"><span data-stu-id="56e7e-146">Click to display the **Logon Credentials** dialog box, where you can enter the account name and password of the account under which the host instance will run.</span></span>|  
   |<span data-ttu-id="56e7e-147">**停用主控件執行個體無法啟動**</span><span class="sxs-lookup"><span data-stu-id="56e7e-147">**Disable host instance from starting**</span></span>|<span data-ttu-id="56e7e-148">選取此核取方塊將選取主控件的狀態由啟用變更為停用。</span><span class="sxs-lookup"><span data-stu-id="56e7e-148">Select this check box to change the status of the selected host from enabled to disabled.</span></span> <span data-ttu-id="56e7e-149">若您不要主控件執行個體啟動，但是要保留其設定時，停用主控件執行個體就非常有用。</span><span class="sxs-lookup"><span data-stu-id="56e7e-149">Disabling a host instance is useful if you do not want the host instance to start, but you do want to preserve its settings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="56e7e-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="56e7e-150">See Also</span></span>  
 <span data-ttu-id="56e7e-151">[管理 BizTalk 主控件和主控件執行個體](../core/managing-biztalk-hosts-and-host-instances.md) </span><span class="sxs-lookup"><span data-stu-id="56e7e-151">[Managing BizTalk Hosts and Host Instances](../core/managing-biztalk-hosts-and-host-instances.md) </span></span>  
 <span data-ttu-id="56e7e-152">[新增主控件執行個體](../core/how-to-add-a-host-instance.md) </span><span class="sxs-lookup"><span data-stu-id="56e7e-152">[Add a Host Instance](../core/how-to-add-a-host-instance.md) </span></span>  
 <span data-ttu-id="56e7e-153">[啟動主控件執行個體](../core/how-to-start-a-host-instance.md) </span><span class="sxs-lookup"><span data-stu-id="56e7e-153">[Start a Host Instance](../core/how-to-start-a-host-instance.md) </span></span>  
 <span data-ttu-id="56e7e-154">[停止主控件執行個體](../core/how-to-stop-a-host-instance.md) </span><span class="sxs-lookup"><span data-stu-id="56e7e-154">[Stop a Host Instance](../core/how-to-stop-a-host-instance.md) </span></span>  
 [<span data-ttu-id="56e7e-155">刪除主控件執行個體</span><span class="sxs-lookup"><span data-stu-id="56e7e-155">Delete a Host Instance</span></span>](../core/how-to-delete-a-host-instance.md)