---
title: 匯入或匯出 BizTalk 設定使用設定儀表板 |Microsoft Docs
description: 使用 BizTalk Server 管理匯入或匯出 BizTalk Server 環境之間的設定
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cc2f0b44-d79b-4f95-811a-0843e3d6d1c8
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c2a825158f43ea085fd0e84aeb15001ea88b6d7f
ms.sourcegitcommit: 53b16fe6c1b1707ecf233dbd05f780653eb19419
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2018
ms.locfileid: "50752774"
---
# <a name="use-settings-dashboard-to-import-or-export-biztalk-settings"></a><span data-ttu-id="ab7c5-103">使用設定儀表板匯入或匯出 BizTalk 設定</span><span class="sxs-lookup"><span data-stu-id="ab7c5-103">Use Settings Dashboard to import or export BizTalk Settings</span></span> 

## <a name="overview"></a><span data-ttu-id="ab7c5-104">總覽</span><span class="sxs-lookup"><span data-stu-id="ab7c5-104">Overview</span></span>
<span data-ttu-id="ab7c5-105">您可以使用 BizTalk 設定儀表板，匯出 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 環境中的設定，再將設定匯入到其他 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 環境，進而縮短完成解決方案所需的整體時間。</span><span class="sxs-lookup"><span data-stu-id="ab7c5-105">Using the BizTalk Settings Dashboard, you can export the settings from a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment and import them to another [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment, thereby reducing the overall time-to-solution.</span></span> <span data-ttu-id="ab7c5-106">當系統管理員會試著在臨時環境中調整 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 效能，並會在達成想要的結果時將設定匯入實際執行環境的情況下，這種方式就特別有用。</span><span class="sxs-lookup"><span data-stu-id="ab7c5-106">This is especially useful in scenarios where the administrators try to tune [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] performance in a staging environment, and upon achieving the desired results, they can import the settings into a production environment.</span></span> <span data-ttu-id="ab7c5-107">本主題將提供使用 [設定儀表板] 匯入 BizTalk 群組、主控件和主控件執行個體設定的逐步程序。</span><span class="sxs-lookup"><span data-stu-id="ab7c5-107">This topic provides step-by-step procedure to import the BizTalk Group, Host, and Host Instance settings using Settings Dashboard.</span></span>  

> [!TIP]
> <span data-ttu-id="ab7c5-108">BTSTask 命令列公用程式也可以使用匯入或匯出工作群組、 主控件和主控件執行個體設定。</span><span class="sxs-lookup"><span data-stu-id="ab7c5-108">The BTSTask command-line utility can also be used to import or export the Group, Host, and Host Instance settings.</span></span> <span data-ttu-id="ab7c5-109">請參閱[匯入或匯出 BizTalk 設定使用 BTSTask](how-to-import-biztalk-settings-using-btstask.md)。</span><span class="sxs-lookup"><span data-stu-id="ab7c5-109">See [Import or export BizTalk Settings Using BTSTask](how-to-import-biztalk-settings-using-btstask.md).</span></span>

  
## <a name="prerequisites"></a><span data-ttu-id="ab7c5-110">先決條件</span><span class="sxs-lookup"><span data-stu-id="ab7c5-110">Prerequisites</span></span>  
 <span data-ttu-id="ab7c5-111">若要執行這項作業，您必須為 BizTalk Server 系統管理員群組的成員登入。</span><span class="sxs-lookup"><span data-stu-id="ab7c5-111">To perform this operation, you must be signed in as a member of the BizTalk Server Administrators group.</span></span>  
  
## <a name="import-the-biztalk-group-host-and-host-instance-settings"></a><span data-ttu-id="ab7c5-112">匯入 BizTalk 群組、 主機和主機執行個體設定</span><span class="sxs-lookup"><span data-stu-id="ab7c5-112">Import the BizTalk group, host, and host instance settings</span></span>  

> [!IMPORTANT]
>  <span data-ttu-id="ab7c5-113">若要從某個環境匯入 BizTalk Server 設定，您應該已經將這些設定儲存並匯出成 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="ab7c5-113">To import the BizTalk Server settings from a certain environment, you should have already saved and exported those settings in an XML file.</span></span> <span data-ttu-id="ab7c5-114">**匯出 BizTalk 設定**（在本主題中） 或[匯入或匯出 BizTalk 設定使用 BTSTask](how-to-import-biztalk-settings-using-btstask.md)可以幫助。</span><span class="sxs-lookup"><span data-stu-id="ab7c5-114">**Export BizTalk Settings** (in this topic) or [Import or export BizTalk Settings Using BTSTask](how-to-import-biztalk-settings-using-btstask.md) can help.</span></span>
  
 <span data-ttu-id="ab7c5-115">透過匯入 XML 檔案，您可以將必要的 BizTalk Server 設定複製到目標電腦上。</span><span class="sxs-lookup"><span data-stu-id="ab7c5-115">By importing the XML file, you can replicate the required BizTalk Server settings on the target machine.</span></span> <span data-ttu-id="ab7c5-116">您可以使用 [設定] 儀表板，匯入群組、主控件和主控件執行個體設定，並且將屬性相互對應。</span><span class="sxs-lookup"><span data-stu-id="ab7c5-116">Using the Settings dashboard, you can import the Group, Host, and Host Instance settings and map the properties of one to another.</span></span> <span data-ttu-id="ab7c5-117">以下是匯入設定的必要假設：</span><span class="sxs-lookup"><span data-stu-id="ab7c5-117">Following are the necessary assumptions for importing the settings:</span></span>  
  
-   <span data-ttu-id="ab7c5-118">來源環境與目的環境的 BizTalk Server 拓撲是一致的。</span><span class="sxs-lookup"><span data-stu-id="ab7c5-118">The BizTalk Server topology is consistent from the source environment to the destination environment.</span></span>  
  
-   <span data-ttu-id="ab7c5-119">來源環境和目的環境的主控件定義可相互對應。</span><span class="sxs-lookup"><span data-stu-id="ab7c5-119">The host definitions across source and destination environments can be mapped.</span></span> <span data-ttu-id="ab7c5-120">您應該要能夠將來源環境中的所有主控件與目的環境中的主控件相互對應。</span><span class="sxs-lookup"><span data-stu-id="ab7c5-120">You should be able to map all hosts in the source environment with those in the destination environment.</span></span>  
  
-   <span data-ttu-id="ab7c5-121">目的環境與來源環境有相似的硬體 (如果不完全相同)。</span><span class="sxs-lookup"><span data-stu-id="ab7c5-121">The destination environment has hardware similar (if not identical) to the source environment.</span></span> <span data-ttu-id="ab7c5-122">這很重要，因為部分設定的運作要仰賴基礎硬體。</span><span class="sxs-lookup"><span data-stu-id="ab7c5-122">This is essential as some of the settings depend on the underlying hardware.</span></span>  

### <a name="import-steps"></a><span data-ttu-id="ab7c5-123">匯入步驟</span><span class="sxs-lookup"><span data-stu-id="ab7c5-123">Import steps</span></span>
  
1. <span data-ttu-id="ab7c5-124">在  **BizTalk Server 管理主控台**，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，以滑鼠右鍵按一下**BizTalk 群組**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="ab7c5-124">In the **BizTalk Server Administration Console**, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], right-click **BizTalk Group**, and then click **Settings**.</span></span>  
  
2. <span data-ttu-id="ab7c5-125">在 [ **BizTalk 設定儀表板**] 對話方塊中，按一下**匯入**。</span><span class="sxs-lookup"><span data-stu-id="ab7c5-125">In the **BizTalk Settings Dashboard** dialog box, click **Import**.</span></span> <span data-ttu-id="ab7c5-126">**匯入設定精靈** 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="ab7c5-126">The **Import Settings Wizard** dialog box appears.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="ab7c5-127">**目的地群組**會顯示您要匯入設定的目標電腦的群組資訊。</span><span class="sxs-lookup"><span data-stu-id="ab7c5-127">The **Destination Group** displays the group information of the target machine where you want to import the settings.</span></span>  
  
    <span data-ttu-id="ab7c5-128">![指定匯入設定檔的位置](../core/media/importsettings-filelocation.jpg "ImportSettings_FileLocation")</span><span class="sxs-lookup"><span data-stu-id="ab7c5-128">![Specify the file location to import settings](../core/media/importsettings-filelocation.jpg "ImportSettings_FileLocation")</span></span>  
  
3. <span data-ttu-id="ab7c5-129">按一下 **指定檔案位置**頁面，然後再按一下![瀏覽設定檔案](../core/media/importsettings-filelocationbrowse.gif "ImportSettings_FileLocationBrowse")。</span><span class="sxs-lookup"><span data-stu-id="ab7c5-129">Click the **Specify File Location** page, and then click ![Browse the settings file](../core/media/importsettings-filelocationbrowse.gif "ImportSettings_FileLocationBrowse").</span></span> <span data-ttu-id="ab7c5-130">檔案總管隨即出現。</span><span class="sxs-lookup"><span data-stu-id="ab7c5-130">The file explorer appears.</span></span>  
  
4. <span data-ttu-id="ab7c5-131">選取包含來源環境設定的 XML 檔案，然後按一下**開啟**。</span><span class="sxs-lookup"><span data-stu-id="ab7c5-131">Select the XML file containing the source environment settings, and then click **Open**.</span></span> <span data-ttu-id="ab7c5-132">**檔案位置**顯示 XML 檔案的路徑並**來源群組**會填入來源電腦的群組資訊。</span><span class="sxs-lookup"><span data-stu-id="ab7c5-132">The **File Location** displays the path of the XML file and the **Source Group** is populated with the group information of the source machine.</span></span> <span data-ttu-id="ab7c5-133">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="ab7c5-133">Click **Next**.</span></span>  
  
5. <span data-ttu-id="ab7c5-134">在 **主控件對應**頁面上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="ab7c5-134">On the **Host Mapping** page, do the following:</span></span>  
  
   1.  <span data-ttu-id="ab7c5-135">從**目的地主機**清單中，選取您要指定來源主控件，然後再按一下目的地主機**新增**。</span><span class="sxs-lookup"><span data-stu-id="ab7c5-135">From the **Destination Hosts** list, select a destination host for which you want to specify the source host, and then click **Add**.</span></span>  
  
        <span data-ttu-id="ab7c5-136">![裝載對應](../core/media/importsettings-hostmapping.gif "ImportSettings_HostMapping")</span><span class="sxs-lookup"><span data-stu-id="ab7c5-136">![Host Mapping](../core/media/importsettings-hostmapping.gif "ImportSettings_HostMapping")</span></span>  
  
   2.  <span data-ttu-id="ab7c5-137">在 [**選取來源實體**] 對話方塊中，選取來源主控件，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="ab7c5-137">In the **Select Source Entity** dialog box, select the source host, and then click **OK**.</span></span>  
  
       > [!NOTE]
       >  <span data-ttu-id="ab7c5-138">若要對應至單一來源主控件的多個目的地主控件，重複步驟**5a**並**5b**。</span><span class="sxs-lookup"><span data-stu-id="ab7c5-138">To map multiple destination hosts to a single source host, repeat the steps **5a** and **5b**.</span></span>  
  
   3.  <span data-ttu-id="ab7c5-139">在 [**主控件對應**頁面上，按一下**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="ab7c5-139">In the **Host Mapping** page, click **Next**.</span></span>  
  
6. <span data-ttu-id="ab7c5-140">在 **主控件執行個體對應**頁面上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="ab7c5-140">In the **Host Instance Mapping** page, do the following:</span></span>  
  
   1.  <span data-ttu-id="ab7c5-141">從目的地主控件執行個體的清單中，選取 目的地主控件的執行個體，您要指定來源主控件執行個體，然後再按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="ab7c5-141">From the list of destination host instances, select a destination host instance for which you want to specify the source host instance, and then click **Add**.</span></span>  
  
       > [!NOTE]
       >  <span data-ttu-id="ab7c5-142">主控件執行個體只能對應至已在「主控件對應」中建立的相對應主控件。</span><span class="sxs-lookup"><span data-stu-id="ab7c5-142">Host instances can be mapped only to the corresponding host that has been created in the Host Mapping.</span></span> <span data-ttu-id="ab7c5-143">例如，如果您指定的對應所在**SourceHost1**對應至**DestinationHost1**，然後的執行個體**DestinationHost1**只能對應至執行個體**SourceHost1**。</span><span class="sxs-lookup"><span data-stu-id="ab7c5-143">For example, if you specify a mapping where **SourceHost1** is mapped to **DestinationHost1**, then the instances of **DestinationHost1** can only be mapped to the instances of **SourceHost1**.</span></span>  
       >   
       >  <span data-ttu-id="ab7c5-144">匯入精靈會管理上述條件約束，您需要遵守此條件約束，否則 BizTalk 工作會擲回錯誤。</span><span class="sxs-lookup"><span data-stu-id="ab7c5-144">The import wizard manages the above constraint, you need to follow this constraint else BizTalk tasks will throw errors.</span></span>  
       >   
       >  <span data-ttu-id="ab7c5-145">您需要使用慣例**hostname: Machinename**對應檔中指定主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="ab7c5-145">You need to use the convention **HostName:MachineName** to specify a host instance in a map file.</span></span> <span data-ttu-id="ab7c5-146">比方說， **Host1:Server1**對應中的檔案表示的執行個體**Host1**是執行中或位於**Server1**。</span><span class="sxs-lookup"><span data-stu-id="ab7c5-146">For example, **Host1:Server1** in a map file denotes that the instance of **Host1** is running or available on **Server1**.</span></span>  
  
        <span data-ttu-id="ab7c5-147">![主機執行個體對應](../core/media/importsettings-hostinstancemapping.gif "ImportSettings_HostInstanceMapping")</span><span class="sxs-lookup"><span data-stu-id="ab7c5-147">![Host Instance Mapping](../core/media/importsettings-hostinstancemapping.gif "ImportSettings_HostInstanceMapping")</span></span>  
  
   2.  <span data-ttu-id="ab7c5-148">在 [**選取來源實體**] 對話方塊中，選取來源主控件執行個體，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="ab7c5-148">In the **Select Source Entity** dialog box, select the source host instance, and then click **OK**.</span></span>  
  
       > [!NOTE]
       >  <span data-ttu-id="ab7c5-149">若要將多個目的地主控件執行個體對應至單一來源主控件執行個體中，重複步驟**6a**要**6b**。</span><span class="sxs-lookup"><span data-stu-id="ab7c5-149">To map multiple destination host instances to a single source host instance, repeat the steps **6a** to **6b**.</span></span>  
  
   3.  <span data-ttu-id="ab7c5-150">在 [**主控件執行個體對應**索引標籤上，按一下**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="ab7c5-150">In the **Host Instance Mapping** tab, click **Next**.</span></span>  
  
7. <span data-ttu-id="ab7c5-151">在 [**匯入摘要**] 對話方塊中，確認您所建立的目的地和來源環境的所有匯入設定是否為有需要，，然後按一下**匯入**。</span><span class="sxs-lookup"><span data-stu-id="ab7c5-151">In the **Import Summary** dialog box, verify if all the import settings for destination and source environments you created are as desired, and then click **Import**.</span></span> <span data-ttu-id="ab7c5-152">**進度**頁面會顯示匯入設定的進度。</span><span class="sxs-lookup"><span data-stu-id="ab7c5-152">The **Progress** page shows the progress of import of the settings.</span></span>  
  
   > [!WARNING]
   >  <span data-ttu-id="ab7c5-153">您無法復原匯入 BizTalk Server 設定的動作。</span><span class="sxs-lookup"><span data-stu-id="ab7c5-153">You cannot undo the import of BizTalk Server settings.</span></span> <span data-ttu-id="ab7c5-154">如果您按一下**匯入**，在起始從來源環境匯入設定到目的地環境的程序並**取消**已停用。</span><span class="sxs-lookup"><span data-stu-id="ab7c5-154">If you click **Import**, the process for importing the settings from source environment to destination environment is initiated and **Cancel** is disabled.</span></span> <span data-ttu-id="ab7c5-155">確認您要繼續執行匯入後，再按一下**匯入**。</span><span class="sxs-lookup"><span data-stu-id="ab7c5-155">Ensure you want to proceed with import before clicking **Import**.</span></span>  
  
8. <span data-ttu-id="ab7c5-156">在 **匯入結果**索引標籤上，檢查的群組、 主控件和主控件執行個體的設定，匯入狀態，然後按一下**完成**完成匯入作業。</span><span class="sxs-lookup"><span data-stu-id="ab7c5-156">In the **Import Results** tab, check the import status of the Group, Host, and Host Instance settings, and then click **Finish** to complete the import operation.</span></span> <span data-ttu-id="ab7c5-157">所有匯入的來源環境設定都會套用到目的環境。</span><span class="sxs-lookup"><span data-stu-id="ab7c5-157">All the imported source environment settings are applied to the destination environment.</span></span>  
  
    <span data-ttu-id="ab7c5-158">![匯入結果](../core/media/importsettings-importresults.gif "ImportSettings_ImportResults")</span><span class="sxs-lookup"><span data-stu-id="ab7c5-158">![Import Results](../core/media/importsettings-importresults.gif "ImportSettings_ImportResults")</span></span>  

## <a name="export-the-biztalk-group-host-and-host-instance-settings"></a><span data-ttu-id="ab7c5-159">匯出 BizTalk 群組、 主機和主機執行個體設定</span><span class="sxs-lookup"><span data-stu-id="ab7c5-159">Export the BizTalk group, host, and host instance settings</span></span>  

1. <span data-ttu-id="ab7c5-160">在  **BizTalk Server 管理主控台**，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，以滑鼠右鍵按一下**BizTalk 群組**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="ab7c5-160">In the **BizTalk Server Administration Console**, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], right-click **BizTalk Group**, and then click **Settings**.</span></span>  
  
2. <span data-ttu-id="ab7c5-161">在 [ **BizTalk 設定儀表板**] 對話方塊中，按一下**匯出**。</span><span class="sxs-lookup"><span data-stu-id="ab7c5-161">In the **BizTalk Settings Dashboard** dialog box, click **Export**.</span></span> <span data-ttu-id="ab7c5-162">[另存新檔] 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="ab7c5-162">The **Save As** dialog box appears.</span></span>  
  
3. <span data-ttu-id="ab7c5-163">瀏覽至您要儲存目前的 BizTalk 設定的位置。</span><span class="sxs-lookup"><span data-stu-id="ab7c5-163">Browse to the location where you want to save the current BizTalk settings.</span></span> <span data-ttu-id="ab7c5-164">輸入檔案名稱，選取 XML 格式的類型，然後按一下**儲存**。</span><span class="sxs-lookup"><span data-stu-id="ab7c5-164">Enter the filename, select the type as XML format, and then click **Save**.</span></span>  

> [!IMPORTANT]
>  <span data-ttu-id="ab7c5-165">我們不建議您手動更新 匯出的 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="ab7c5-165">We do not recommended manually updating the exported XML file.</span></span> <span data-ttu-id="ab7c5-166">當您匯入生產環境中更新的 XML 檔案時，匯入程序可能會失敗，因為某種資料類型不符或因手動編輯其他錯誤。</span><span class="sxs-lookup"><span data-stu-id="ab7c5-166">When you import an updated XML file to a production environment, the import process might fail due to some data type mismatch or other errors introduced by manual editing.</span></span>  

## <a name="see-also"></a><span data-ttu-id="ab7c5-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab7c5-167">See Also</span></span>  
 [<span data-ttu-id="ab7c5-168">針對 BizTalk Server 效能調整使用設定儀表板</span><span class="sxs-lookup"><span data-stu-id="ab7c5-168">Using Settings Dashboard for BizTalk Server Performance Tuning</span></span>](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md)
