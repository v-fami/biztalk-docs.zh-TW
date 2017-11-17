---
title: "解除安裝 BizTalk Server 上的 BizTalk RosettaNet 加速器 (BTARN) |Microsoft 文件 」"
description: "解除部署成品，並取消設定 BTARN 以移除 BizTalk Server 加速器"
author: MandiOhlinger
manager: anneta
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 
ms.author: mandia
ms.openlocfilehash: 8d289a3705eb0c127dc4d2637c2d6ffd3c122b36
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="uninstall-the-rosettanet-accelerator"></a><span data-ttu-id="94fae-103">解除安裝 RosettaNet 加速器</span><span class="sxs-lookup"><span data-stu-id="94fae-103">Uninstall the RosettaNet accelerator</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="94fae-104">開始之前</span><span class="sxs-lookup"><span data-stu-id="94fae-104">Before you begin</span></span>
  
* <span data-ttu-id="94fae-105">如果您只執行**Setup.exe**，解除安裝程序不會移除商務活動監控 (BAM) 成品、 BizTalk 成品、 網際網路資訊服務 (IIS) 虛擬目錄和應用程式集區。</span><span class="sxs-lookup"><span data-stu-id="94fae-105">If you only run **Setup.exe**, the uninstall process does not remove the Business Activity Monitoring (BAM) artifacts, the BizTalk artifacts, Internet Information Services (IIS) virtual directories, and application pools.</span></span>  
  
* <span data-ttu-id="94fae-106">如果您使用**回送**公用程式來建立鏡像協議，針對單一電腦部署，然後執行該工具搭配**/停用 <** **home 組織** **>** 選項後再中刪除夥伴**BTARN 管理主控台**。</span><span class="sxs-lookup"><span data-stu-id="94fae-106">If you used the **Loopback** utility to create mirror agreements for a single-computer deployment, then run the tool with the **/disable <** **home organization** **>** option before deleting the partners in the **BTARN Administration Console**.</span></span>  
  
* <span data-ttu-id="94fae-107">如果此伺服器是多電腦部署的一部分，不會執行**BtarnClean**公用程式或手動解除部署 BTARN 組件。</span><span class="sxs-lookup"><span data-stu-id="94fae-107">If this server is part of a multi-computer deployment, do not run the **BtarnClean** utility or manually undeploy the BTARN assemblies.</span></span> <span data-ttu-id="94fae-108">一部電腦上移除成品會中斷其他電腦的功能。</span><span class="sxs-lookup"><span data-stu-id="94fae-108">Removing the artifacts on one computer breaks the functionality of the other computers.</span></span>  <span data-ttu-id="94fae-109">如果您想要從所有伺服器解除安裝 BTARN，然後執行**BtarnClean**公用程式。</span><span class="sxs-lookup"><span data-stu-id="94fae-109">If you want to uninstall BTARN from all the servers, then run the **BtarnClean** utility.</span></span> 

  
## <a name="undeploy-the-artifacts"></a><span data-ttu-id="94fae-110">解除部署成品</span><span class="sxs-lookup"><span data-stu-id="94fae-110">Undeploy the artifacts</span></span>  

<span data-ttu-id="94fae-111">我們建議您備份之前解除部署 BAM 成品。</span><span class="sxs-lookup"><span data-stu-id="94fae-111">We recommend backing up your BAM artifacts before undeploying.</span></span> 

1. <span data-ttu-id="94fae-112">解除部署您部署的所有 BAM 成品：</span><span class="sxs-lookup"><span data-stu-id="94fae-112">Undeploy all the BAM artifacts that you deployed:</span></span>  
  
    1.  <span data-ttu-id="94fae-113">在命令提示字元執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="94fae-113">At the command prompt, run the following command:</span></span>  
  
         ```cd %ProgramFiles%\\<BizTalk Server installation directory\>\Tracking```
  
    2.  <span data-ttu-id="94fae-114">在已安裝追蹤 UI 的命令提示字元下，執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="94fae-114">At the command prompt where the tracking UI was installed, run the following command:</span></span>  
  
         ```bm remove-all DefinitionFile:"%ProgramFiles%\\<installation directory\>\BAMTracking\tracking.xml"```
  
        > [!NOTE]
        >  <span data-ttu-id="94fae-115">如需有關 BAM 的詳細資訊，請參閱[管理商務活動監控](../../core/managing-bam.md)</span><span class="sxs-lookup"><span data-stu-id="94fae-115">For more information about BAM, see [Managing Business Activity Monitoring](../../core/managing-bam.md)</span></span> 
  
2.  <span data-ttu-id="94fae-116">備份並刪除在 BTARN 管理主控台中的所有合約、 合作夥伴和主要組織。</span><span class="sxs-lookup"><span data-stu-id="94fae-116">Backup and delete all the agreements, partners, and home organizations from the BTARN Management Console.</span></span> <span data-ttu-id="94fae-117">請參閱使用的相關資訊 （在 「 BTARN 說明 」 的 [作業] 節點中） 的 < 管理 BTARN 組態 > 主題**BtarnConfig**公用程式備份協議和夥伴。</span><span class="sxs-lookup"><span data-stu-id="94fae-117">See the "Administering the BTARN Configuration" topic (in the Operations node of BTARN Help) for information about using the **BtarnConfig** utility to back up the agreements and partners.</span></span>  
  
    > [!NOTE]
    >  * <span data-ttu-id="94fae-118">停止和解除部署 BTARN 使用所建立的 BizTalk 成品[BtarnClean](btarnclean.md)公用程式。</span><span class="sxs-lookup"><span data-stu-id="94fae-118">Stop and undeploy the BizTalk artifacts created by BTARN by using the [BtarnClean](btarnclean.md) utility.</span></span>
    >  * <span data-ttu-id="94fae-119">移除您部署的任何其他成品。</span><span class="sxs-lookup"><span data-stu-id="94fae-119">Remove any additional artifacts that you deployed.</span></span> <span data-ttu-id="94fae-120">請參閱[解除部署 BizTalk 應用程式](../../core/undeploying-biztalk-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="94fae-120">See [Undeploying BizTalk Applications](../../core/undeploying-biztalk-applications.md) .</span></span>
  
3.  <span data-ttu-id="94fae-121">從 BTARN 安裝程式中，尋找 MSI\Program Files\Microsoft BizTalk Accelerator for RosettaNet\SDK 資料夾。</span><span class="sxs-lookup"><span data-stu-id="94fae-121">From the BTARN Setup, locate the MSI\Program Files\Microsoft BizTalk Accelerator for RosettaNet\SDK folder.</span></span> <span data-ttu-id="94fae-122">在 SDK 資料夾中，按兩下**BTARNClean.exe**，然後選取**Y**若要繼續，或**N**取消執行公用程式。</span><span class="sxs-lookup"><span data-stu-id="94fae-122">In the SDK folder, double-click **BTARNClean.exe**, and then select **Y** to continue, or **N** to cancel running the utility.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="94fae-123">如果您的伺服器是多電腦部署實例的一部分，可以略過步驟 3。</span><span class="sxs-lookup"><span data-stu-id="94fae-123">If your server is part of a multi-computer deployment scenario, you can skip step 3.</span></span> <span data-ttu-id="94fae-124">解除部署任何共用的資源將會中斷部署中其他伺服器的功能。</span><span class="sxs-lookup"><span data-stu-id="94fae-124">Undeploying any shared resources breaks the functionality on the other servers in the deployment.</span></span>  
  
4.  <span data-ttu-id="94fae-125">解除部署您所建立和部署的任何自訂組件。</span><span class="sxs-lookup"><span data-stu-id="94fae-125">Undeploy any custom assemblies that you created and deployed.</span></span>  
  
5.  <span data-ttu-id="94fae-126">在命令提示字元中，移至 files\microsoft BizTalk Server <your version>\Tracking。</span><span class="sxs-lookup"><span data-stu-id="94fae-126">At the command prompt, go to \Program Files\Microsoft BizTalk Server <your version>\Tracking.</span></span> <span data-ttu-id="94fae-127">執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="94fae-127">Run the following command:</span></span> 

    ```BM UNDEPLOY ALL <drive\>:\Program Files\\<installation directory\>\BAMTracking\tracking.xml```
  
## <a name="unconfigure-btarn"></a><span data-ttu-id="94fae-128">取消設定 BTARN</span><span class="sxs-lookup"><span data-stu-id="94fae-128">Unconfigure BTARN</span></span>
  
1.  <span data-ttu-id="94fae-129">找出並執行下列命令以取消設定 BTARN：</span><span class="sxs-lookup"><span data-stu-id="94fae-129">Locate and run the following to unconfigure BTARN:</span></span>  
  
     <span data-ttu-id="94fae-130">***< 磁碟機\>*****: \Program Files\\< 安裝目錄\>\Configuration.exe /u** </span><span class="sxs-lookup"><span data-stu-id="94fae-130">***<drive\>***  **:\Program Files\\<installation directory\>\Configuration.exe /u**</span></span>  
  
2.  <span data-ttu-id="94fae-131">在控制台中，按兩下**新增或移除程式**。</span><span class="sxs-lookup"><span data-stu-id="94fae-131">In Control Panel, double-click **Add or Remove Programs**.</span></span>  
  
3.  <span data-ttu-id="94fae-132">在**目前安裝的程式**清單中，按一下**Microsoft BizTalk Accelerator for RosettaNet**，然後按一下 **變更/移除**。</span><span class="sxs-lookup"><span data-stu-id="94fae-132">In the **Currently installed programs** list, click **Microsoft BizTalk Accelerator for RosettaNet**, and then click **Change/Remove**.</span></span>  
  
4.  <span data-ttu-id="94fae-133">在**程式維護**對話方塊中，選取**移除**，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="94fae-133">In the **Program Maintenance** dialog box, select **Remove**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="94fae-134">在**摘要**對話方塊中，按一下 **解除安裝**。</span><span class="sxs-lookup"><span data-stu-id="94fae-134">In the **Summary** dialog box, click **Uninstall**.</span></span>  
  
6.  <span data-ttu-id="94fae-135">在**已完成解除安裝**對話方塊中，按一下 **完成**。</span><span class="sxs-lookup"><span data-stu-id="94fae-135">In the **Uninstall Completed** dialog box, click **Finish**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="94fae-136">解除安裝程序不會移除 BTARN 資料庫 （BTARNARCHIVE、 BTARNCONFIG 和 BTARNDATA）。</span><span class="sxs-lookup"><span data-stu-id="94fae-136">The uninstallation process does not remove the BTARN databases (BTARNARCHIVE, BTARNCONFIG, and BTARNDATA).</span></span> <span data-ttu-id="94fae-137">您必須手動移除這些資料庫。</span><span class="sxs-lookup"><span data-stu-id="94fae-137">You must manually remove them.</span></span>  
  
7.  <span data-ttu-id="94fae-138">開啟**SQL Server Management Studio**。</span><span class="sxs-lookup"><span data-stu-id="94fae-138">Open **SQL Server Management Studio**.</span></span>  
  
8.  <span data-ttu-id="94fae-139">在**連接到伺服器**對話方塊中，按一下 **連接**。</span><span class="sxs-lookup"><span data-stu-id="94fae-139">In the **Connect to Server** dialog box, click **Connect**.</span></span>  
  
9. <span data-ttu-id="94fae-140">展開**資料庫**的左窗格中的節點。</span><span class="sxs-lookup"><span data-stu-id="94fae-140">Expand the **Databases** node in the left pane.</span></span> <span data-ttu-id="94fae-141">其中一個 BTARN 資料庫中，以滑鼠右鍵按一下，然後按一下 **刪除**。</span><span class="sxs-lookup"><span data-stu-id="94fae-141">Right-click one of the BTARN databases, and then click **Delete**.</span></span>  
  
10. <span data-ttu-id="94fae-142">在**刪除物件**對話方塊中，選取**關閉現有的連接**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="94fae-142">In the **Delete Object** dialog box, select **Close Existing Connections**, and then click **OK**.</span></span>  
  
