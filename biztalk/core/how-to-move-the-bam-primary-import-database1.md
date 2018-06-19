---
title: 如何移動 BAM 主要匯入 Database1 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- migrating, Primary Import database [BAM]
- Primary Import database [BAM], migrating
ms.assetid: fab13fea-5c35-4a9f-977d-cc45545c54b2
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6a63c556bfb95f4b22a3256540d3ecb336a17f7f
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25972660"
---
# <a name="how-to-move-the-bam-primary-import-database"></a><span data-ttu-id="81b4e-102">如何移動 BAM 主要匯入資料庫</span><span class="sxs-lookup"><span data-stu-id="81b4e-102">How to Move the BAM Primary Import Database</span></span>
<span data-ttu-id="81b4e-103">您可以使用這個程序，將 BAM 主要匯入資料庫移動到其他伺服器。</span><span class="sxs-lookup"><span data-stu-id="81b4e-103">You can use this procedure to move the BAM Primary Import database to another server.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="81b4e-104">必要條件</span><span class="sxs-lookup"><span data-stu-id="81b4e-104">Prerequisites</span></span>  
 <span data-ttu-id="81b4e-105">您必須以 SQL Server 系統管理員 (sysadmin) 固定伺服器角色成員的帳戶登入來執行這個程序。</span><span class="sxs-lookup"><span data-stu-id="81b4e-105">You must be logged on with an account that is a member of the SQL Server sysadmin fixed server role to perform this procedure.</span></span>  
  
### <a name="to-move-the-bam-primary-import-database"></a><span data-ttu-id="81b4e-106">移動 BAM 主要匯入資料庫</span><span class="sxs-lookup"><span data-stu-id="81b4e-106">To move the BAM Primary Import database</span></span>  
  
1.  <span data-ttu-id="81b4e-107">停止所有 BizTalk Server 服務。</span><span class="sxs-lookup"><span data-stu-id="81b4e-107">Stop all BizTalk Server services.</span></span> <span data-ttu-id="81b4e-108">如需詳細資訊，請參閱[如何啟動、 停止、 暫停、 繼續或重新啟動 BizTalk Server 服務](../core/how-to-start-stop-pause-resume-or-restart-biztalk-server-services.md)。</span><span class="sxs-lookup"><span data-stu-id="81b4e-108">For more information, see [How to Start, Stop, Pause, Resume, or Restart BizTalk Server Services](../core/how-to-start-stop-pause-resume-or-restart-biztalk-server-services.md).</span></span>  
  
2.  <span data-ttu-id="81b4e-109">停止 IIS 服務。</span><span class="sxs-lookup"><span data-stu-id="81b4e-109">Stop the IIS service.</span></span>  
  
3.  <span data-ttu-id="81b4e-110">停止 BAM 警示 Notification Service：</span><span class="sxs-lookup"><span data-stu-id="81b4e-110">Stop the BAM Alerts Notification Service:</span></span>  
  
    1.  <span data-ttu-id="81b4e-111">按一下**啟動**，按一下 **執行**，型別**cmd**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="81b4e-111">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
    2.  <span data-ttu-id="81b4e-112">在命令提示字元中，輸入：</span><span class="sxs-lookup"><span data-stu-id="81b4e-112">At the command prompt, type:</span></span>  
  
        ```  
        Net stop NS$BamAlerts  
        ```  
  
4.  <span data-ttu-id="81b4e-113">依照 SQL Server 線上叢書 》 中的指示，將舊的伺服器上備份 BAM 主要匯入資料庫。</span><span class="sxs-lookup"><span data-stu-id="81b4e-113">Follow the instructions in SQL Server Books Online to back up the BAM Primary Import database on the old server.</span></span>  
  
5.  <span data-ttu-id="81b4e-114">將 BAM 主要匯入資料庫複製到新的 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="81b4e-114">Copy the BAM Primary Import database to the new SQL Server.</span></span>  
  
6.  <span data-ttu-id="81b4e-115">依照 SQL Server 線上叢書 》 中的指示來還原 BAM 主要匯入資料庫，新的伺服器上。</span><span class="sxs-lookup"><span data-stu-id="81b4e-115">Follow the instructions in SQL Server Books Online to restore the BAM Primary Import database on the new server.</span></span>  
  
7.  <span data-ttu-id="81b4e-116">在執行 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的電腦中，瀏覽至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="81b4e-116">On a computer running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], browse to the following folder:</span></span>  
  
     [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="81b4e-117">Schema\Restore</span><span class="sxs-lookup"><span data-stu-id="81b4e-117">Schema\Restore</span></span>  
  
8.  <span data-ttu-id="81b4e-118">以滑鼠右鍵按一下**SampleUpdateInfo.xml**，然後按一下 **編輯**。</span><span class="sxs-lookup"><span data-stu-id="81b4e-118">Right-click **SampleUpdateInfo.xml**, and then click **Edit**.</span></span>  
  
9. <span data-ttu-id="81b4e-119">在主要匯入資料庫區段中的檔案，取代 **"SourceServer"** 然後取代與來源系統的名稱取代 **"DestinationServer"** 目的系統的名稱。</span><span class="sxs-lookup"><span data-stu-id="81b4e-119">In the Primary Import Database section of the file, replace **"SourceServer"** with the name of the source system, and then replace **"DestinationServer"** with the name of the destination system.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="81b4e-120">在來源及目的系統的名稱兩端加上引號。</span><span class="sxs-lookup"><span data-stu-id="81b4e-120">Include the quotation marks around the name of the source and destination systems.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="81b4e-121">如果重新命名了任何 BizTalk Server 資料庫，您也必須視情況適當更新資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="81b4e-121">If you renamed any of the BizTalk Server databases, you must also update the database names as appropriate.</span></span>  
  
10. <span data-ttu-id="81b4e-122">取消在 XML 檔案中下列幾行的註解標記：</span><span class="sxs-lookup"><span data-stu-id="81b4e-122">Uncomment the following lines in the xml file:</span></span>  
  
    ```  
    - <UpdateConfiguration>  
      <MessageBoxDB oldDBName="BizTalkMsgboxDb" oldDBServer="Server01" newDBName="BizTalkMsgboxDb" newDBServer="Server01" IsMaster="1" />   
      <TrackingDB oldDBName="BizTalkDTADb" oldDBServer="Server01" newDBName="BizTalkDTADb" newDBServer="Server01" />   
      <ManagementDB oldDBName="BizTalkMgmtDb" oldDBServer="Server01" newDBName="BizTalkMgmtDb" newDBServer="Server01" />   
    - <BAM>  
    - <DeploymentUnit Name="OldPrimaryImportDatabase">  
      <Property Name="ServerName">Server01</Property>   
      <Property Name="DatabaseName">BAMPrimaryImport</Property>   
      </DeploymentUnit>  
    - <DeploymentUnit Name="PrimaryImportDatabase">  
      <Property Name="ServerName">Server02</Property>   
      <Property Name="DatabaseName">BAMPrimaryImport</Property>   
      </DeploymentUnit>  
    - <DeploymentUnit Name="ArchivingDatabase">  
      <Property Name="ServerName">Server01</Property>   
      <Property Name="DatabaseName">BAMArchive</Property>   
      </DeploymentUnit>  
    - <DeploymentUnit Name="AnalysisDatabase">  
      <Property Name="ServerName">Server01</Property>   
      <Property Name="DatabaseName">BAMAnalysis</Property>   
      </DeploymentUnit>  
    - <DeploymentUnit Name="StarSchemaDatabase">  
      <Property Name="ServerName">Server01</Property>   
      <Property Name="DatabaseName">BAMStarSchema</Property>   
      </DeploymentUnit>  
    - <DeploymentUnit Name="Alert">  
      <Property Name="DBServer">Server01</Property>   
      <Property Name="InstanceDatabaseName">BAMAlerts</Property>   
      </DeploymentUnit>  
      </BAM>  
    - <OtherDatabases>  
      <Database Name="SSO" oldDBName="SSODB" oldDBServer="Server01" newDBName="SSODB" newDBServer="Server01" />   
      </OtherDatabases>  
      </UpdateConfiguration>  
    ```  
  
11. <span data-ttu-id="81b4e-123">完成檔案的編輯後，請加以儲存並結束。</span><span class="sxs-lookup"><span data-stu-id="81b4e-123">When you are finished editing the file, save it and exit.</span></span>  
  
12. <span data-ttu-id="81b4e-124">按一下**啟動**，按一下 **執行**，型別**cmd**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="81b4e-124">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
13. <span data-ttu-id="81b4e-125">在命令提示字元中，瀏覽至下列目錄：</span><span class="sxs-lookup"><span data-stu-id="81b4e-125">At the command prompt, navigate to the following directory:</span></span>  
  
     [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="81b4e-126">Schema\Restore</span><span class="sxs-lookup"><span data-stu-id="81b4e-126">Schema\Restore</span></span>  
  
14. <span data-ttu-id="81b4e-127">在命令提示字元中，輸入：</span><span class="sxs-lookup"><span data-stu-id="81b4e-127">At the command prompt, type:</span></span>  
  
     <span data-ttu-id="81b4e-128">**cscript UpdateDatabase.vbs SampleUpdateInfo.xml**</span><span class="sxs-lookup"><span data-stu-id="81b4e-128">**cscript UpdateDatabase.vbs SampleUpdateInfo.xml**</span></span>  
  
15. <span data-ttu-id="81b4e-129">更新 BAM 主要匯入資料庫在所有 BAM Livedata Microsoft Excel 檔案中的參考。</span><span class="sxs-lookup"><span data-stu-id="81b4e-129">Update the reference to BAM Primary Import Database in all BAM Livedata Microsoft Excel files.</span></span> <span data-ttu-id="81b4e-130">對於每個檔案：</span><span class="sxs-lookup"><span data-stu-id="81b4e-130">For each file:</span></span>  
  
    1.  <span data-ttu-id="81b4e-131">開啟 Excel 即時資料檔案。</span><span class="sxs-lookup"><span data-stu-id="81b4e-131">Open the Excel live data file.</span></span> <span data-ttu-id="81b4e-132">此檔案名稱是以 _LiveData.xls 結尾。</span><span class="sxs-lookup"><span data-stu-id="81b4e-132">The file name ends with _LiveData.xls.</span></span>  
  
    2.  <span data-ttu-id="81b4e-133">在**BAM**功能表上，按一下  **BAM DB 連線**。</span><span class="sxs-lookup"><span data-stu-id="81b4e-133">On the **BAM** menu, click **BAM DB Connection**.</span></span>  
  
    3.  <span data-ttu-id="81b4e-134">在**選取 BAM 資料庫**對話方塊中，輸入 SQL Server 和 BAMPrimaryImport 資料庫，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="81b4e-134">In the **Select BAM Database** dialog box, enter the SQL Server and BAMPrimaryImport database, and then click **OK**.</span></span>  
  
    4.  <span data-ttu-id="81b4e-135">在**檔案**功能表上，按一下 **關閉並返回 Microsoft Excel**。</span><span class="sxs-lookup"><span data-stu-id="81b4e-135">On the **File** menu, click **Close and Return to Microsoft Excel**.</span></span>  
  
    5.  <span data-ttu-id="81b4e-136">在 [檔案] 功能表上，按一下 [儲存]。</span><span class="sxs-lookup"><span data-stu-id="81b4e-136">On the **File** menu, click **Save**.</span></span>  
  
16. <span data-ttu-id="81b4e-137">依照下列步驟，更新所有 BAM 分析 DTS 封裝中的伺服器及資料庫名稱，這些名稱會加上 "BAM_AN_" 或 "BAM_DM_" 做為前置詞：</span><span class="sxs-lookup"><span data-stu-id="81b4e-137">Update the server and database names in all BAM analysis DTS packages, which are prefixed with "BAM_AN_" or "BAM_DM_" by following these steps:</span></span>  
  
    1.  <span data-ttu-id="81b4e-138">在裝載 BAM 的伺服器上，開啟 SQL Server Enterprise Manager。</span><span class="sxs-lookup"><span data-stu-id="81b4e-138">On the server hosting BAM, open SQL Server Enterprise Manager.</span></span>  
  
    2.  <span data-ttu-id="81b4e-139">開啟**Data Transformation Services**資料夾。</span><span class="sxs-lookup"><span data-stu-id="81b4e-139">Open the **Data Transformation Services** folder.</span></span>  
  
    3.  <span data-ttu-id="81b4e-140">開啟**本機封裝**資料夾，然後開啟 DTS 封裝。</span><span class="sxs-lookup"><span data-stu-id="81b4e-140">Open the **Local Packages** folder, and then open the DTS packages.</span></span>  
  
    4.  <span data-ttu-id="81b4e-141">在**封裝**功能表上，按一下 **屬性**。</span><span class="sxs-lookup"><span data-stu-id="81b4e-141">On the **Package** menu, click **Properties**.</span></span>  
  
    5.  <span data-ttu-id="81b4e-142">在**全域變數**索引標籤上，更新主要匯入伺服器和資料庫的值。</span><span class="sxs-lookup"><span data-stu-id="81b4e-142">On the **Global Variables** tab, update the values for the primary import server and database.</span></span>  
  
    6.  <span data-ttu-id="81b4e-143">變更下列幾行以符合新的伺服器和資料庫：</span><span class="sxs-lookup"><span data-stu-id="81b4e-143">Change the following lines to match your new server and database:</span></span>  
  
         <span data-ttu-id="81b4e-144">PrimaryImportServer ="*\<ServerName\>*"</span><span class="sxs-lookup"><span data-stu-id="81b4e-144">PrimaryImportServer= "*\<ServerName\>*"</span></span>  
  
         <span data-ttu-id="81b4e-145">PrimaryImportDatabase ="*\<DatabaseName\>*"</span><span class="sxs-lookup"><span data-stu-id="81b4e-145">PrimaryImportDatabase = "*\<DatabaseName\>*"</span></span>  
  
17. <span data-ttu-id="81b4e-146">啟動所有的 BizTalk Server 服務。</span><span class="sxs-lookup"><span data-stu-id="81b4e-146">Start all BizTalk Server services.</span></span> <span data-ttu-id="81b4e-147">如需詳細資訊，請參閱[如何啟動、 停止、 暫停、 繼續或重新啟動 BizTalk Server 服務](../core/how-to-start-stop-pause-resume-or-restart-biztalk-server-services.md)。</span><span class="sxs-lookup"><span data-stu-id="81b4e-147">For more information, see [How to Start, Stop, Pause, Resume, or Restart BizTalk Server Services](../core/how-to-start-stop-pause-resume-or-restart-biztalk-server-services.md).</span></span>  
  
18. <span data-ttu-id="81b4e-148">啟動 IIS 服務。</span><span class="sxs-lookup"><span data-stu-id="81b4e-148">Start the IIS service.</span></span>  
  
19. <span data-ttu-id="81b4e-149">啟動 BAM 警示 Notification Service：</span><span class="sxs-lookup"><span data-stu-id="81b4e-149">Start the BAM Alerts Notification Service:</span></span>  
  
    1.  <span data-ttu-id="81b4e-150">按一下**啟動**，按一下 **執行**，型別**cmd**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="81b4e-150">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
    2.  <span data-ttu-id="81b4e-151">在命令提示字元中，輸入：</span><span class="sxs-lookup"><span data-stu-id="81b4e-151">At the command prompt, type:</span></span>  
  
        ```  
        Net start NS$BamAlerts  
        ```  
  
## <a name="see-also"></a><span data-ttu-id="81b4e-152">請參閱</span><span class="sxs-lookup"><span data-stu-id="81b4e-152">See Also</span></span>  
 [<span data-ttu-id="81b4e-153">移動 BizTalk Server 資料庫</span><span class="sxs-lookup"><span data-stu-id="81b4e-153">Moving BizTalk Server Databases</span></span>](../core/moving-biztalk-server-databases.md)