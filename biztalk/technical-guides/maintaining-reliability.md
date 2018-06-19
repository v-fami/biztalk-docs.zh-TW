---
title: 維護可靠性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 09cdce13-a75b-44d7-8388-7a868bb51c69
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eb1f956c0f3b09ee51d3dd9d05f64dbd3eeeab3d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22299646"
---
# <a name="maintaining-reliability"></a><span data-ttu-id="2a355-102">維護可靠性</span><span class="sxs-lookup"><span data-stu-id="2a355-102">Maintaining Reliability</span></span>
<span data-ttu-id="2a355-103">本節提供有關如何解決的可靠性問題的資訊[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統。</span><span class="sxs-lookup"><span data-stu-id="2a355-103">This section provides information about how you can resolve reliability issues with a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] system.</span></span> <span data-ttu-id="2a355-104">這些問題可能會發現在會執行例行的維護工作檢查[常式維護檢查清單](../technical-guides/routine-maintenance-checklists.md)本文件一節。</span><span class="sxs-lookup"><span data-stu-id="2a355-104">These issues may be discovered by the routine maintenance checks that are performed in the [Routine Maintenance Checklists](../technical-guides/routine-maintenance-checklists.md) section of this document.</span></span>  
  
 <span data-ttu-id="2a355-105">除了本節中的主題，這份文件中的其他主題位址可靠性問題。</span><span class="sxs-lookup"><span data-stu-id="2a355-105">In addition to the topics in this section, other topics in this document address reliability issues.</span></span> <span data-ttu-id="2a355-106">這些主題中所列[相關章節](../technical-guides/maintaining-reliability.md#BKMK_Related)下方。</span><span class="sxs-lookup"><span data-stu-id="2a355-106">These topics are listed in [Related Sections](../technical-guides/maintaining-reliability.md#BKMK_Related) below.</span></span>  
  
## <a name="testing-group-failover"></a><span data-ttu-id="2a355-107">測試群組容錯移轉</span><span class="sxs-lookup"><span data-stu-id="2a355-107">Testing Group Failover</span></span>  
 <span data-ttu-id="2a355-108">執行本節中的程序，應每月執行的可靠性檢查的一部分。</span><span class="sxs-lookup"><span data-stu-id="2a355-108">Perform the procedures in this section as part of the reliability checks that should be performed monthly.</span></span> <span data-ttu-id="2a355-109">這些程序包括測試群組的容錯移轉原則，以及測試是否可以進行容錯移轉群組資源。</span><span class="sxs-lookup"><span data-stu-id="2a355-109">These procedures include testing the group failover policy, and testing whether the group resources can fail over.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2a355-110">如果電腦已加入網域，Domain Admins 群組的成員才能執行此程序。</span><span class="sxs-lookup"><span data-stu-id="2a355-110">If the computer is joined to a domain, members of the Domain Admins group should be able to perform this procedure.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2a355-111">本章節內容中執行的程序，您必須登入本機電腦上 Administrators 群組的成員身分，或者必須已被委派適當的權限。</span><span class="sxs-lookup"><span data-stu-id="2a355-111">To perform the procedures in this section, you must be logged on as a member of the Administrators group on the local computer, or you must have been delegated the appropriate authority.</span></span>  
  
 <span data-ttu-id="2a355-112">執行下列步驟，以測試在執行 Windows Server 2008 電腦上的群組容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="2a355-112">Perform the following steps to test group failover on computers running Windows Server 2008.</span></span>  
  
#### <a name="to-test-a-group-failover-policy"></a><span data-ttu-id="2a355-113">若要測試群組容錯移轉原則</span><span class="sxs-lookup"><span data-stu-id="2a355-113">To test a group failover policy</span></span>  
  
1.  <span data-ttu-id="2a355-114">請確定您已安裝**容錯移轉叢集**功能在至少兩部電腦上執行 Windows Server 2008，以便建立 Windows 容錯移轉叢集的兩個節點。</span><span class="sxs-lookup"><span data-stu-id="2a355-114">Make sure you have installed the **Failover Clustering** feature on at least two computer running Windows Server 2008 so as to create a two node Windows Failover Cluster.</span></span> <span data-ttu-id="2a355-115">如需有關如何安裝這項功能的指示，請參閱[安裝容錯移轉叢集功能](http://go.microsoft.com/fwlink/?LinkId=157259)(http://go.microsoft.com/fwlink/?LinkId=157259)。</span><span class="sxs-lookup"><span data-stu-id="2a355-115">For instructions on how to install this feature, see [Install the Failover Clustering Feature](http://go.microsoft.com/fwlink/?LinkId=157259) (http://go.microsoft.com/fwlink/?LinkId=157259).</span></span>  
  
2.  <span data-ttu-id="2a355-116">開啟 依序按一下 容錯移轉叢集管理**啟動**，然後按一下**系統管理工具**，然後按一下**容錯移轉叢集管理**。</span><span class="sxs-lookup"><span data-stu-id="2a355-116">Open Failover Cluster Management by clicking **Start**, clicking **Administrative Tools**, and then clicking **Failover Cluster Management**.</span></span>  
  
3.  <span data-ttu-id="2a355-117">在主控台樹狀目錄中，展開 [叢集節點，再展開**服務和應用程式**] 節點，以滑鼠右鍵按一下要容錯移轉，然後按一下應用程式的叢集執行個體**屬性**。</span><span class="sxs-lookup"><span data-stu-id="2a355-117">In the console tree, expand the cluster node, expand the **Services and Applications** node, right-click the clustered instance of the application to be failed over, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="2a355-118">在**容錯移轉**索引標籤上，設定**指定期間內的最大失敗次數**為 0，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="2a355-118">On the **Failover** tab, set **Maximum failures in the specified period** to 0, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="2a355-119">在主控台樹狀目錄中，依序展開**服務和應用程式**節點。</span><span class="sxs-lookup"><span data-stu-id="2a355-119">In the console tree, expand the **Services and Applications** node.</span></span>  
  
6.  <span data-ttu-id="2a355-120">在詳細資料窗格中，以滑鼠右鍵按一下資源，然後**屬性**。</span><span class="sxs-lookup"><span data-stu-id="2a355-120">In the details pane, right-click a resource, and then click **Properties**.</span></span>  
  
7.  <span data-ttu-id="2a355-121">在**原則**索引標籤上，設定**指定期間內重新啟動次數上限**為 0，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="2a355-121">On the **Policies** tab, set **Maximum restarts in the specified period** to 0, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="2a355-122">以滑鼠右鍵按一下資源，請按一下**其他動作**，然後按一下**模擬的失敗，此資源的**。</span><span class="sxs-lookup"><span data-stu-id="2a355-122">Right-click the resource, click **More Actions**, and then click **Simulate Failure of this resource**.</span></span> <span data-ttu-id="2a355-123">請確認是否群組會做出反應根據您在上一個步驟中指定的原則。</span><span class="sxs-lookup"><span data-stu-id="2a355-123">Verify whether the group reacts based on the policy you specified in the previous step.</span></span>  
  
9. <span data-ttu-id="2a355-124">以滑鼠右鍵按一下要容錯移轉，然後按一下應用程式的叢集執行個體**屬性**。</span><span class="sxs-lookup"><span data-stu-id="2a355-124">Right-click the clustered instance of the application to be failed over, and then click **Properties**.</span></span>  
  
10. <span data-ttu-id="2a355-125">在**容錯移轉**索引標籤上，設定**指定期間內的最大失敗次數**為 1，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="2a355-125">On the **Failover** tab, set **Maximum failures in the specified period** to 1, and then click **OK**.</span></span>  
  
11. <span data-ttu-id="2a355-126">以滑鼠右鍵按一下資源，並選取**將此資源上線**。</span><span class="sxs-lookup"><span data-stu-id="2a355-126">Right-click the resource and select **Bring this resource online**.</span></span>  
  
#### <a name="to-test-whether-group-resources-can-fail-over"></a><span data-ttu-id="2a355-127">若要測試是否可以進行容錯移轉群組資源</span><span class="sxs-lookup"><span data-stu-id="2a355-127">To test whether group resources can fail over</span></span>  
  
1.  <span data-ttu-id="2a355-128">請確定您已安裝**容錯移轉叢集**執行 Windows Server 2008 的電腦上的功能。</span><span class="sxs-lookup"><span data-stu-id="2a355-128">Make sure you have installed the **Failover Clustering** feature on the computer running Windows Server 2008.</span></span> <span data-ttu-id="2a355-129">如需有關如何安裝這項功能的指示，請參閱[安裝容錯移轉叢集功能](http://go.microsoft.com/fwlink/?LinkId=157259)(http://go.microsoft.com/fwlink/?LinkId=157259)。</span><span class="sxs-lookup"><span data-stu-id="2a355-129">For instructions on how to install this feature, see [Install the Failover Clustering Feature](http://go.microsoft.com/fwlink/?LinkId=157259) (http://go.microsoft.com/fwlink/?LinkId=157259).</span></span>  
  
2.  <span data-ttu-id="2a355-130">開啟 依序按一下 容錯移轉叢集管理**啟動**，然後按一下**系統管理工具**，然後按一下**容錯移轉叢集管理**。</span><span class="sxs-lookup"><span data-stu-id="2a355-130">Open Failover Cluster Management by clicking **Start**, clicking **Administrative Tools**, and then clicking **Failover Cluster Management**.</span></span>  
  
3.  <span data-ttu-id="2a355-131">在主控台樹狀目錄中，展開 [叢集節點，再展開**服務和應用程式**] 節點，然後按一下應用程式容錯移轉叢集執行個體。</span><span class="sxs-lookup"><span data-stu-id="2a355-131">In the console tree, expand the cluster node, expand the **Services and Applications** node, and then click the clustered instance of the application to be failed over.</span></span>  
  
4.  <span data-ttu-id="2a355-132">在**動作**功能表上，按一下 **將此服務或應用程式到另一個節點移動**，然後按一下目標應用程式的容錯移轉節點。</span><span class="sxs-lookup"><span data-stu-id="2a355-132">On the **Action** menu, click **Move this service or application to another node**, and then click the node to which the application will be failed over.</span></span>  
  
5.  <span data-ttu-id="2a355-133">在**請確認動作**對話方塊方塊中，選擇將移至所選節點的應用程式。</span><span class="sxs-lookup"><span data-stu-id="2a355-133">In the **Please confirm action** dialog box, choose to move the application to selected node.</span></span>  
  
6.  <span data-ttu-id="2a355-134">確定您移至應用程式的節點會列出針對**目前擁有者**應用程式的詳細資料窗格中。</span><span class="sxs-lookup"><span data-stu-id="2a355-134">Make sure that the node to which you moved the application to is listed against the **Current Owner** in the details pane of the application.</span></span>  
  
##  <a name="BKMK_BTSGrp"></a><span data-ttu-id="2a355-135">確保多部伺服器是 BizTalk 群組的一部分</span><span class="sxs-lookup"><span data-stu-id="2a355-135">Ensuring Multiple Servers Are Part of a BizTalk Group</span></span>  
 <span data-ttu-id="2a355-136">若要確保系統的可靠性，至少兩個實體 BizTalk 伺服器應該是 BizTalk 群組的一部分。</span><span class="sxs-lookup"><span data-stu-id="2a355-136">To ensure the reliability of a system, at least two physical BizTalk servers should be part of the BizTalk group.</span></span>  <span data-ttu-id="2a355-137">如果您要將伺服器新增至 BizTalk 群組，請注意下列事項：</span><span class="sxs-lookup"><span data-stu-id="2a355-137">If you need to add a server to a BizTalk group, keep the following in mind:</span></span>  
  
-   <span data-ttu-id="2a355-138">一部伺服器僅能與一個 BizTalk 群組關聯。</span><span class="sxs-lookup"><span data-stu-id="2a355-138">A server can only be associated with one BizTalk group.</span></span> <span data-ttu-id="2a355-139">如果伺服器已經屬於其他群組，您必須先從目前的群組移除該伺服器，才可將其新增至新群組。</span><span class="sxs-lookup"><span data-stu-id="2a355-139">If a server already belongs to another group, you must first remove that server from its current group before you can add it to a new group.</span></span> <span data-ttu-id="2a355-140">如需從 BizTalk 群組移除伺服器的詳細資訊，請參閱 < 如何將移除伺服器從群組"[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助在[http://go.microsoft.com/fwlink/?LinkId=155577](http://go.microsoft.com/fwlink/?LinkId=155577)。</span><span class="sxs-lookup"><span data-stu-id="2a355-140">For more information about removing a server from a BizTalk group, see "How to Remove a Server from a Group" in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help at [http://go.microsoft.com/fwlink/?LinkId=155577](http://go.microsoft.com/fwlink/?LinkId=155577).</span></span>  
  
-   <span data-ttu-id="2a355-141">與 BizTalk Server 環境中不同伺服器建立關聯的 BizTalk 群組，除了交換訊息之外並不會互動。</span><span class="sxs-lookup"><span data-stu-id="2a355-141">BizTalk groups associated with different servers in a BizTalk Server environment do not interact except to exchange messages.</span></span>  
  
-   <span data-ttu-id="2a355-142">BizTalk Server 執行階段必須安裝在您想新增至 BizTalk 群組的電腦上。</span><span class="sxs-lookup"><span data-stu-id="2a355-142">The BizTalk Server runtime must be installed on the computer you want to add to the BizTalk group.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2a355-143">若要執行本主題中的程序，您必須為 SSO 系統管理員群組的成員，以及 Windows Administrators 群組的成員登入。</span><span class="sxs-lookup"><span data-stu-id="2a355-143">To perform the procedures in this topic, you must be logged on as a member of the SSO Administrators group and as a member of the Windows Administrators group.</span></span>  
  
#### <a name="to-determine-whether-at-least-two-physical-biztalk-servers-are-part-of-the-biztalk-group"></a><span data-ttu-id="2a355-144">若要判斷是否在至少兩部實體 BizTalk 伺服器屬於 BizTalk 群組</span><span class="sxs-lookup"><span data-stu-id="2a355-144">To determine whether at least two physical BizTalk servers are part of the BizTalk group</span></span>  
  
1.  <span data-ttu-id="2a355-145">開啟[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台按一下**啟動**、 指向**所有程式**、 指向**Microsoft [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]** ，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="2a355-145">Open the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console by clicking **Start**, pointing to **All Programs**, pointing to **Microsoft [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]**, and then clicking **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="2a355-146">展開[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]] 節點，展開 [ **BizTalk 群組** 節點，然後展開**平台設定**節點。</span><span class="sxs-lookup"><span data-stu-id="2a355-146">Expand the [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] node, expand the **BizTalk Group** node, and then expand the **Platform Settings** node.</span></span>  
  
3.  <span data-ttu-id="2a355-147">按一下**伺服器**節點。</span><span class="sxs-lookup"><span data-stu-id="2a355-147">Click the **Servers** node.</span></span> <span data-ttu-id="2a355-148">請確認多部伺服器會列在**伺服器**窗格。</span><span class="sxs-lookup"><span data-stu-id="2a355-148">Verify that more than one server is listed in the **Servers** pane.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2a355-149">若要檢視伺服器的相關資訊，請以滑鼠右鍵按一下伺服器，指向**檢視**，然後按一下**群組中樞頁面**。</span><span class="sxs-lookup"><span data-stu-id="2a355-149">To view information about the server, right-click the server, point to **View**, and then click **Group Hub Page**.</span></span>  
  
#### <a name="to-add-a-server-to-a-biztalk-group"></a><span data-ttu-id="2a355-150">將伺服器新增至 BizTalk 群組</span><span class="sxs-lookup"><span data-stu-id="2a355-150">To add a server to a BizTalk group</span></span>  
  
1.  <span data-ttu-id="2a355-151">您想要新增至 BizTalk 群組的電腦，按一下**啟動**，按一下 **所有程式**，按一下  **Microsoft [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]** ，然後按一下 **BizTalk Server 組態**。</span><span class="sxs-lookup"><span data-stu-id="2a355-151">On the computer that you want to add to a BizTalk group, click **Start**, click **All Programs**, click **Microsoft [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]**, and then click **BizTalk Server Configuration**.</span></span>  
  
2.  <span data-ttu-id="2a355-152">在**Microsoft BizTalk Server 2010 組態**，選取**自訂組態**。</span><span class="sxs-lookup"><span data-stu-id="2a355-152">In **Microsoft BizTalk Server 2010 Configuration**, select **Custom configuration**.</span></span>  
  
3.  <span data-ttu-id="2a355-153">在**資料庫伺服器名稱**，輸入伺服器正要的 BizTalk 群組的 SQL server 的名稱。</span><span class="sxs-lookup"><span data-stu-id="2a355-153">In **Database server name**, type the name of the SQL server for the BizTalk group that the server is joining.</span></span>  
  
4.  <span data-ttu-id="2a355-154">在**服務認證**，輸入適當的使用者名稱和密碼，服務會使用，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="2a355-154">In **Service credential**, type the appropriate user name and password that the services will use, and then click **Configure**.</span></span>  
  
5.  <span data-ttu-id="2a355-155">在畫面左側的導覽樹狀目錄中，按一下 **企業單一登入**。</span><span class="sxs-lookup"><span data-stu-id="2a355-155">In the navigation tree on the left side of the screen, click **Enterprise SSO**.</span></span>  
  
6.  <span data-ttu-id="2a355-156">在**企業單一登入**頁面上，按一下**加入現有的 SSO 系統**。</span><span class="sxs-lookup"><span data-stu-id="2a355-156">On the **Enterprise Single Sign-On** page, click **Join an existing SSO system**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2a355-157">確定伺服器名稱和資料庫名稱是指向伺服器正要的 BizTalk 群組的主要 SSO 資料庫伺服器。</span><span class="sxs-lookup"><span data-stu-id="2a355-157">Ensure that the server name and database name point to the master SSO database server for the BizTalk group that the server is joining.</span></span>  
  
7.  <span data-ttu-id="2a355-158">在畫面左側的導覽樹狀目錄中，按一下 **群組**。</span><span class="sxs-lookup"><span data-stu-id="2a355-158">In the navigation tree on the left side of the screen, click **Group**.</span></span>  
  
8.  <span data-ttu-id="2a355-159">在**群組**頁面上，按一下**加入現有的 BizTalk 群組**。</span><span class="sxs-lookup"><span data-stu-id="2a355-159">On the **Group** page, click **Join an existing BizTalk Group**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2a355-160">確定伺服器名稱和資料庫名稱是指向伺服器正要 BizTalk 群組的資料庫。</span><span class="sxs-lookup"><span data-stu-id="2a355-160">Ensure that the server name and database name point to the databases for the BizTalk group that the server is joining.</span></span>  
  
9. <span data-ttu-id="2a355-161">在功能表列上，按一下 **套用組態**設定這部電腦上的企業單一登入和群組。</span><span class="sxs-lookup"><span data-stu-id="2a355-161">On the menu bar, click **Apply Configuration** to configure both Enterprise Single Sign-On and the group on this computer.</span></span>  
  
##  <a name="BKMK_Related"></a> <span data-ttu-id="2a355-162">相關章節</span><span class="sxs-lookup"><span data-stu-id="2a355-162">Related Sections</span></span>  
  
-   <span data-ttu-id="2a355-163">檢查硬體 RAID 中失敗的磁碟的相關資訊，請參閱 < 檢視磁碟屬性 > 中的 Windows Server 2003 產品說明在[http://go.microsoft.com/fwlink/?linkid=104161](http://go.microsoft.com/fwlink/?linkid=104161)。</span><span class="sxs-lookup"><span data-stu-id="2a355-163">For information about checking for failed disks in the hardware RAID, see "View Disk Properties" in the Windows Server 2003 product Help at [http://go.microsoft.com/fwlink/?linkid=104161](http://go.microsoft.com/fwlink/?linkid=104161).</span></span>  
  
-   <span data-ttu-id="2a355-164">如需手動檢查擱置的訊息資訊，請參閱 < Investigating 協調流程、 連接埠和訊息失敗 」 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助在[http://go.microsoft.com/fwlink/?LinkID=154512](http://go.microsoft.com/fwlink/?LinkID=154512)。</span><span class="sxs-lookup"><span data-stu-id="2a355-164">For information about manually checking for suspended messages, see "Investigating Orchestration, Port, and Message Failures" in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help at [http://go.microsoft.com/fwlink/?LinkID=154512](http://go.microsoft.com/fwlink/?LinkID=154512).</span></span>  
  
-   <span data-ttu-id="2a355-165">如需確保每個主機有兩個以上的實體 BizTalk 伺服器上執行的執行個體資訊，請參閱[高可用性的 BizTalk 主控件](../technical-guides/high-availability-for-biztalk-hosts.md)。</span><span class="sxs-lookup"><span data-stu-id="2a355-165">For information about ensuring that each host has an instance running on at least two physical BizTalk servers, see [High Availability for BizTalk Hosts](../technical-guides/high-availability-for-biztalk-hosts.md).</span></span>  
  
-   <span data-ttu-id="2a355-166">如需確保每個主機有兩個以上的實體 BizTalk 伺服器上執行的執行個體資訊，請參閱[調整出接收主機](../technical-guides/scaling-out-receiving-hosts.md)。</span><span class="sxs-lookup"><span data-stu-id="2a355-166">For information about ensuring that each host has an instance running on at least two physical BizTalk servers, see [Scaling Out Receiving Hosts](../technical-guides/scaling-out-receiving-hosts.md).</span></span>  
  
-   <span data-ttu-id="2a355-167">如需已經過測試，確保所有的叢集服務該容錯移轉的相關資訊，請參閱[叢集主要密碼伺服器](../technical-guides/clustering-the-master-secret-server.md)。</span><span class="sxs-lookup"><span data-stu-id="2a355-167">For information about ensuring that failover for all clustered services has been tested, see [Clustering the Master Secret Server](../technical-guides/clustering-the-master-secret-server.md).</span></span>  
  
-   <span data-ttu-id="2a355-168">如需確保 SQL 服務 下，叢集的 BizTalk 資料庫資訊，請參閱[叢集 BizTalk Server Databases2](../technical-guides/clustering-the-biztalk-server-databases2.md)。</span><span class="sxs-lookup"><span data-stu-id="2a355-168">For information about ensuring that the BizTalk databases are clustered under SQL Services, see [Clustering the BizTalk Server Databases2](../technical-guides/clustering-the-biztalk-server-databases2.md).</span></span>  
  
-   <span data-ttu-id="2a355-169">如需判斷是否 （需要不同的主控件） 正在使用任何不穩定的程式碼的詳細資訊，請參閱[高可用性的 BizTalk 主控件](../technical-guides/high-availability-for-biztalk-hosts.md)。</span><span class="sxs-lookup"><span data-stu-id="2a355-169">For information about determining whether any unstable code is being used (requiring separate hosts), see [High Availability for BizTalk Hosts](../technical-guides/high-availability-for-biztalk-hosts.md).</span></span>  
  
-   <span data-ttu-id="2a355-170">如需執行的所有新的 BizTalk 應用程式功能測試的資訊，請參閱[測試應用程式](../technical-guides/testing-an-application.md)</span><span class="sxs-lookup"><span data-stu-id="2a355-170">For information about performing functional testing of all new BizTalk applications, see [Testing an Application](../technical-guides/testing-an-application.md)</span></span>