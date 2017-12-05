---
title: "疑難排解 BAM |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e63299a8-5c74-4337-ba20-3213e0c6ea1f
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 92f13d938b0e0523ce6e20d6021bbca24595782f
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="troubleshooting-bam"></a><span data-ttu-id="f3b9c-102">疑難排解 BAM</span><span class="sxs-lookup"><span data-stu-id="f3b9c-102">Troubleshooting BAM</span></span>
<span data-ttu-id="f3b9c-103">本主題提供使用商務活動監控 (BAM) 時，可能會遇到的資訊可協助您疑難排解問題。</span><span class="sxs-lookup"><span data-stu-id="f3b9c-103">This topic provides information to help you troubleshoot problems you might encounter when using Business Activity Monitoring (BAM).</span></span>  
  
## <a name="bam-deployment-failed"></a><span data-ttu-id="f3b9c-104">BAM 部署失敗</span><span class="sxs-lookup"><span data-stu-id="f3b9c-104">BAM deployment failed</span></span>  
 <span data-ttu-id="f3b9c-105">如果您嘗試部署 BAM 定義，其中包含即時彙總 (RTA)，無法使用 SQL Server Analysis Services 時，Bm.exe 命令會顯示下列訊息：</span><span class="sxs-lookup"><span data-stu-id="f3b9c-105">If you attempt to deploy a BAM definition that includes a real-time aggregation (RTA) when SQL Server Analysis Services is not available, the Bm.exe command will display the following message:</span></span>  
  
 <span data-ttu-id="f3b9c-106">錯誤： BAM 部署失敗。</span><span class="sxs-lookup"><span data-stu-id="f3b9c-106">ERROR: BAM deployment failed.</span></span> <span data-ttu-id="f3b9c-107">無法建立連接。</span><span class="sxs-lookup"><span data-stu-id="f3b9c-107">A connection cannot be made.</span></span> <span data-ttu-id="f3b9c-108">請確定該伺服器正在執行。</span><span class="sxs-lookup"><span data-stu-id="f3b9c-108">Ensure that the server is running.</span></span> <span data-ttu-id="f3b9c-109">無法建立沒有連接，因為目標電腦主動拒絕連線 *\<IP 位址\>*。</span><span class="sxs-lookup"><span data-stu-id="f3b9c-109">No connection could be made because the target machine actively refused it *\<IP address\>*.</span></span>  
  
 <span data-ttu-id="f3b9c-110">這是因為 SQL Server Analysis Services 必須安裝和設定，且必須正在執行，才能部署 BAM 定義，其中包含 RTA。</span><span class="sxs-lookup"><span data-stu-id="f3b9c-110">This occurs because SQL Server Analysis Services must have been installed and configured, and must be running in order to deploy a BAM definition that includes an RTA.</span></span>  
  
## <a name="cannot-refresh-the-live-data-workbook"></a><span data-ttu-id="f3b9c-111">無法重新整理的即時資料活頁簿</span><span class="sxs-lookup"><span data-stu-id="f3b9c-111">Cannot refresh the live data workbook</span></span>  
 <span data-ttu-id="f3b9c-112">當您嘗試更新即時資料活頁簿中的資料時，Microsoft Office Excel 可能會顯示下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="f3b9c-112">When you try to refresh the data in a live data workbook, Microsoft Office Excel might display the following error:</span></span>  
  
 `XML for Analysis parser: The CurrentCatalog XML/A property was not specified.`  
  
 <span data-ttu-id="f3b9c-113">這是因為 BAM 增益集尚未加入至 Excel。</span><span class="sxs-lookup"><span data-stu-id="f3b9c-113">This occurs because the BAM add-in has not been added to Excel.</span></span>  
  
#### <a name="to-add-the-bam-add-in-to-excel"></a><span data-ttu-id="f3b9c-114">若要加入的 BAM 增益集至 Excel</span><span class="sxs-lookup"><span data-stu-id="f3b9c-114">To add the BAM add-in to Excel</span></span>  
  
1.  <span data-ttu-id="f3b9c-115">按一下**啟動**，指向 **所有程式**，指向  **Microsoft Office**，然後按一下  **Microsoft Office Excel**。</span><span class="sxs-lookup"><span data-stu-id="f3b9c-115">Click **Start**, point to **All Programs**, point to **Microsoft Office**, and then click **Microsoft Office Excel**.</span></span>  
  
2.  <span data-ttu-id="f3b9c-116">按一下**Microsoft Office 按鈕**，然後按一下  **Excel 選項**。</span><span class="sxs-lookup"><span data-stu-id="f3b9c-116">Click the **Microsoft Office Button**, and then click **Excel Options**.</span></span>  
  
3.  <span data-ttu-id="f3b9c-117">在**Excel 選項**對話方塊中，按一下 **增益集**。</span><span class="sxs-lookup"><span data-stu-id="f3b9c-117">In the **Excel Options** dialog box, click **Add-Ins**.</span></span>  
  
4.  <span data-ttu-id="f3b9c-118">在**增益集**] 窗格中，按一下 [**移**。</span><span class="sxs-lookup"><span data-stu-id="f3b9c-118">In the **Add-Ins** pane, click **Go**.</span></span>  
  
5.  <span data-ttu-id="f3b9c-119">在**增益集**對話方塊中，選取**商務活動監控**核取方塊，然後**確定**。</span><span class="sxs-lookup"><span data-stu-id="f3b9c-119">In the **Add-Ins** dialog box, select the **Business Activity Monitoring** check box, and then click **OK**.</span></span>  
  
     <span data-ttu-id="f3b9c-120">![新增 &#45; 增益集 對話方塊](../core/media/addins.gif "增益集")</span><span class="sxs-lookup"><span data-stu-id="f3b9c-120">![Add&#45;Ins dialog box](../core/media/addins.gif "AddIns")</span></span>  
  
## <a name="errorobject-library-invalid-or-contains-references-to-object-definitions-that-could-not-be-found-with-bam-excel-add-in-in-office"></a><span data-ttu-id="f3b9c-121">Office 的 BAM Excel 增益集發生錯誤：「物件程式庫無效或包含找不到的物件定義參照」。</span><span class="sxs-lookup"><span data-stu-id="f3b9c-121">Error:"Object library invalid or contains references to object definitions that could not be found" with BAM Excel Add-In in Office</span></span>  
 <span data-ttu-id="f3b9c-122">升級為 Microsoft Excel 後，嘗試使用 BAM Excel 增益集時，可能會發生這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="f3b9c-122">You may receive this error, when you try use the BAM Excel Add-In after you upgrade Microsoft Excel.</span></span>  
  
 <span data-ttu-id="f3b9c-123">**解決方式：**因為 BAM 增益集使用 ActiveX 控制項，您必須從下列目錄刪除任何快取的.exd 檔案：</span><span class="sxs-lookup"><span data-stu-id="f3b9c-123">**Resolution:** Since the BAM Add-In uses ActiveX controls, you have to delete any cached .exd files from the following directories:</span></span>  
  
-   <span data-ttu-id="f3b9c-124">C:\Documents and Settings\\< 使用者名稱\>\Application Data\Microsoft\Forms</span><span class="sxs-lookup"><span data-stu-id="f3b9c-124">C:\Documents and Settings\\<username\>\Application Data\Microsoft\Forms</span></span>  
  
-   <span data-ttu-id="f3b9c-125">C:\Documents and Settings\\< 使用者名稱\>\AppData\Local\Temp\VBE</span><span class="sxs-lookup"><span data-stu-id="f3b9c-125">C:\Documents and Settings\\<username\>\AppData\Local\Temp\VBE</span></span>  
  
## <a name="bam-portal-cannot-connect"></a><span data-ttu-id="f3b9c-126">BAM 入口網站無法連接</span><span class="sxs-lookup"><span data-stu-id="f3b9c-126">BAM portal cannot connect</span></span>  
 <span data-ttu-id="f3b9c-127">在[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]或[!INCLUDE[btsWinVista](../includes/btswinvista-md.md)]，您必須以系統管理員身分執行 BAM 入口網站。</span><span class="sxs-lookup"><span data-stu-id="f3b9c-127">In [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] or [!INCLUDE[btsWinVista](../includes/btswinvista-md.md)], you must run the BAM portal as an administrator.</span></span>  
  
#### <a name="to-run-the-bam-portal-on-windows-server-2008-r2-or-windows-7"></a><span data-ttu-id="f3b9c-128">若要在 Windows Server 2008 R2 或 Windows 7 上執行 BAM 入口網站</span><span class="sxs-lookup"><span data-stu-id="f3b9c-128">To run the BAM portal on Windows Server 2008 R2 or Windows 7</span></span>  
  
1.  <span data-ttu-id="f3b9c-129">按一下**啟動**，指向 **所有程式**，以滑鼠右鍵按一下**Internet Explorer**，然後按一下 **系統管理員身分執行**。</span><span class="sxs-lookup"><span data-stu-id="f3b9c-129">Click **Start**, point to **All Programs**, right-click **Internet Explorer**, and then click **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="f3b9c-130">在**使用者帳戶控制**對話方塊中，按一下 **繼續**。</span><span class="sxs-lookup"><span data-stu-id="f3b9c-130">In the **User Account Control** dialog box, click **Continue**.</span></span>  
  
3.  <span data-ttu-id="f3b9c-131">在 Internet Explorer 網址列中，輸入`http://<server>/BAM`，其中*\<伺服器\>*執行 BAM 入口網站之電腦的名稱。</span><span class="sxs-lookup"><span data-stu-id="f3b9c-131">In the Internet Explorer address bar, type `http://<server>/BAM`, where *\<server\>* is the name of the computer that is running the BAM portal.</span></span>  
  
## <a name="bam-portal-does-not-work-if-invalid-users-are-granted-permissions"></a><span data-ttu-id="f3b9c-132">BAM 入口網站無法運作如果無效的使用者授與權限</span><span class="sxs-lookup"><span data-stu-id="f3b9c-132">BAM portal does not work if invalid users are granted permissions</span></span>  
 <span data-ttu-id="f3b9c-133">如果從 AD 移除 AD 使用者擁有 BAM 檢視權限，然後在 BAM 入口網站未正確載入的任何使用者 （除了 DBO)。</span><span class="sxs-lookup"><span data-stu-id="f3b9c-133">If an AD user who has the BAM view permissions is removed from the AD, then the BAM portal does not load properly for any user (except DBO).</span></span>  
  
 <span data-ttu-id="f3b9c-134">若要解決此問題，請從對應的 bam_ {viewname} 檢視安全性角色中移除無效的使用者。</span><span class="sxs-lookup"><span data-stu-id="f3b9c-134">To resolve this issue, remove the invalid user from the corresponding bam_{viewname}view security role.</span></span>  
  
## <a name="cannot-export-or-import-a-bam-definition-to-localhost"></a><span data-ttu-id="f3b9c-135">無法匯入或匯出 BAM 定義為 localhost</span><span class="sxs-lookup"><span data-stu-id="f3b9c-135">Cannot export or import a BAM definition to localhost</span></span>  
 <span data-ttu-id="f3b9c-136">當您匯出 BAM 定義為 XML 時，您會看到下列錯誤訊息如果您嘗試將匯出到 localhost:</span><span class="sxs-lookup"><span data-stu-id="f3b9c-136">When you export a BAM definition as XML, you will see the following error message if you try to export to localhost:</span></span>  
  
 `The system cannot find the path specified.`  
  
 <span data-ttu-id="f3b9c-137">不支援匯出 BAM 定義為 localhost。</span><span class="sxs-lookup"><span data-stu-id="f3b9c-137">Exporting a BAM definition to localhost is not supported.</span></span> <span data-ttu-id="f3b9c-138">同樣地，不支援從 localhost 匯入 BAM 定義。</span><span class="sxs-lookup"><span data-stu-id="f3b9c-138">Similarly, importing a BAM definition from localhost is not supported.</span></span>  
  
## <a name="alerts-do-not-work-after-upgrading-sql-server-editions"></a><span data-ttu-id="f3b9c-139">升級 SQL Server 版本之後無法運作警示</span><span class="sxs-lookup"><span data-stu-id="f3b9c-139">Alerts do not work after upgrading SQL Server editions</span></span>  
 <span data-ttu-id="f3b9c-140">如果您已升級的一個版本[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]至另一個版本 （例如，從到 Enterprise Edition 的標準版） 時，不會重新啟動 BAM 警示。</span><span class="sxs-lookup"><span data-stu-id="f3b9c-140">If you have upgraded from one edition of [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] to another edition (for example, from Standard Edition to Enterprise Edition), BAM alerts will not restart.</span></span> <span data-ttu-id="f3b9c-141">若要修正這個問題，請刪除 BAM 警示並重新建立它們，或升級[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]通知服務。</span><span class="sxs-lookup"><span data-stu-id="f3b9c-141">To fix this problem, either delete the BAM alerts and re-create them, or upgrade the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Notification Service.</span></span>  
  
#### <a name="to-upgrade-the-sql-server-notification-service"></a><span data-ttu-id="f3b9c-142">若要升級 SQL Server Notification 服務</span><span class="sxs-lookup"><span data-stu-id="f3b9c-142">To upgrade the SQL Server Notification Service</span></span>  
  
1.  <span data-ttu-id="f3b9c-143">按一下**啟動**，按一下 **所有程式**，按一下  **Microsoft SQL Server 2005**，然後按一下  **Notification 服務的命令提示字元**。</span><span class="sxs-lookup"><span data-stu-id="f3b9c-143">Click **Start**, click **All Programs**, click **Microsoft SQL Server 2005**, and then click **Notification Service Command Prompt**.</span></span>  
  
2.  <span data-ttu-id="f3b9c-144">在命令提示字元中輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="f3b9c-144">Type the following command at the command prompt:</span></span>  
  
     `nscontrol.exe upgrade -name <instanceName>`  
  
## <a name="objectdisposedexception-exception"></a><span data-ttu-id="f3b9c-145">ObjectDisposedException 例外狀況</span><span class="sxs-lookup"><span data-stu-id="f3b9c-145">ObjectDisposedException Exception</span></span>  
 <span data-ttu-id="f3b9c-146">如果您的應用程式使用 BAM WF 3.5 攔截器，您可能會收到下列錯誤訊息： **System.ObjectDisposedException： 無法存取已處置的物件**。</span><span class="sxs-lookup"><span data-stu-id="f3b9c-146">If your application is using BAM WF 3.5 interceptor, you may receive the following error message: **System.ObjectDisposedException: Cannot access a disposed object**.</span></span> <span data-ttu-id="f3b9c-147">如需有關此錯誤訊息的詳細資訊，請參閱[ObjectDisposedException 例外狀況](http://go.microsoft.com/fwlink/?LinkID=195338)(http://go.microsoft.com/fwlink/?LinkID=195338)。</span><span class="sxs-lookup"><span data-stu-id="f3b9c-147">For more information about this error message, see [ObjectDisposedException Exception](http://go.microsoft.com/fwlink/?LinkID=195338) (http://go.microsoft.com/fwlink/?LinkID=195338).</span></span>   
<span data-ttu-id="f3b9c-148">若要解決此問題，安裝 hotfix 可從 960754 [http://go.microsoft.com/fwlink/?LinkID=195339](http://go.microsoft.com/fwlink/?LinkID=195339)。</span><span class="sxs-lookup"><span data-stu-id="f3b9c-148">To resolve this issue, install the hotfix 960754 available at [http://go.microsoft.com/fwlink/?LinkID=195339](http://go.microsoft.com/fwlink/?LinkID=195339).</span></span>  
  
## <a name="workbook-has-lost-its-vba-project-activex-controls-and-other-programmability-related-features"></a><span data-ttu-id="f3b9c-149">活頁簿已經失去其 VBA 專案、 ActiveX 控制項和其他相關的可程式性功能</span><span class="sxs-lookup"><span data-stu-id="f3b9c-149">Workbook has lost its VBA project, ActiveX controls and other programmability-related features</span></span>  
 <span data-ttu-id="f3b9c-150">當嘗試在 Microsoft Excel 中使用 BAM.xla 時，您可能會收到下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="f3b9c-150">When attempting to use BAM.xla in Microsoft Excel, you may get the following error:</span></span>  
  
 `This workbook has lost its VBA project, ActiveX controls and any other programmability-related features.`  
  
 <span data-ttu-id="f3b9c-151">若要解決此問題，請安裝**應用程式的 Visual Basic**選項在**Office 共用功能**與 Microsoft Office。</span><span class="sxs-lookup"><span data-stu-id="f3b9c-151">To resolve this issue, install the **Visual Basic for Applications** option under **Office Shared Features** with Microsoft Office.</span></span>  
  
## <a name="pivot-table-fails-to-get-the-data"></a><span data-ttu-id="f3b9c-152">無法取得資料的樞紐分析表</span><span class="sxs-lookup"><span data-stu-id="f3b9c-152">Pivot table fails to get the data</span></span>  
 <span data-ttu-id="f3b9c-153">您所部署的檢視上有存取 BAM 資料庫，以及角色的權限和權限。</span><span class="sxs-lookup"><span data-stu-id="f3b9c-153">You have permissions to access BAM databases, and also role and permissions on the views which are deployed.</span></span> <span data-ttu-id="f3b9c-154">[活動搜尋] 頁面如預期般運作，而且您看得到資料。</span><span class="sxs-lookup"><span data-stu-id="f3b9c-154">The Activity Search page works as expected and you can see the data.</span></span> <span data-ttu-id="f3b9c-155">但是，樞紐分析表中顯示下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="f3b9c-155">But, in the Pivot table, the following error is displayed:</span></span>  
  
```  
Failed to get data.  If available, errors returned from the provider are listed below.  
* The following system error occurred:  No connection could be made because the target machine actively refused it.  
```  
  
 <span data-ttu-id="f3b9c-156">若要解決此問題，請分別新增下列 DNS 設定：</span><span class="sxs-lookup"><span data-stu-id="f3b9c-156">To resolve this issue, add the respective DNS settings as follows:</span></span>  
  
1.  <span data-ttu-id="f3b9c-157">按一下**啟動**並移至**控制台**。</span><span class="sxs-lookup"><span data-stu-id="f3b9c-157">Click **Start** and go to **Control Panel**.</span></span>  
  
2.  <span data-ttu-id="f3b9c-158">按一下**網路和網際網路**，然後按一下 **網路連線**。</span><span class="sxs-lookup"><span data-stu-id="f3b9c-158">Click **Network and Internet** and then click **Network Connections**.</span></span>  
  
3.  <span data-ttu-id="f3b9c-159">以滑鼠右鍵按一下網路連線 （例如 區域連線），然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="f3b9c-159">Right-click on the network connection (like Local Area Connection), and select **Properties**.</span></span>  
  
4.  <span data-ttu-id="f3b9c-160">在**區域連線**頁面上，選取**網際網路通訊協定第 4 版 (TCP/IPv4)**，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="f3b9c-160">On the **Local Area Connection** page, select **Internet Protocol Version 4 (TCP/IPv4)**, and click **Properties**.</span></span>  
  
5.  <span data-ttu-id="f3b9c-161">按一下 **[進階]**。</span><span class="sxs-lookup"><span data-stu-id="f3b9c-161">Click **Advanced**.</span></span> <span data-ttu-id="f3b9c-162">在**進階 TCP/IP 設定**頁面上，按一下**DNS**  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="f3b9c-162">On the **Advance TCP/IP Settings** page, click the **DNS** tab.</span></span>  
  
6.  <span data-ttu-id="f3b9c-163">選取**附加這些 DNS 尾碼**然後新增必要的 DNS 尾碼。</span><span class="sxs-lookup"><span data-stu-id="f3b9c-163">Select **Append these DNS suffixes** and then add the required DNS suffixes.</span></span>  
  
7.  <span data-ttu-id="f3b9c-164">按一下**確定**並關閉所有開啟的視窗。</span><span class="sxs-lookup"><span data-stu-id="f3b9c-164">Click **OK** and close all the open windows.</span></span>  
  
## <a name="pivot-table-view-shows-all-values-as-0"></a><span data-ttu-id="f3b9c-165">樞紐分析表檢視將所有的值都顯示為 “0”</span><span class="sxs-lookup"><span data-stu-id="f3b9c-165">Pivot table view shows all values as “0”</span></span>  
 <span data-ttu-id="f3b9c-166">當您部署 BAM 入口網站時，[活動搜尋] 頁面會顯示預期的結果。</span><span class="sxs-lookup"><span data-stu-id="f3b9c-166">When you deploy the BAM portal, the Activity Search page displays expected results.</span></span> <span data-ttu-id="f3b9c-167">但是，樞紐分析表檢視卻將所有的值都顯示為 “0”。</span><span class="sxs-lookup"><span data-stu-id="f3b9c-167">But, the Pivot table view displays all values as “0”.</span></span> <span data-ttu-id="f3b9c-168">顯示的錯誤如下：</span><span class="sxs-lookup"><span data-stu-id="f3b9c-168">The following error is displayed:</span></span>  
  
```  
Failed to get data.  If available, errors returned from the provider are listed below.  
* Safety settings on this machine prohibit accessing a data source on another domain.  
```  
  
 <span data-ttu-id="f3b9c-169">若要解決此問題，請將網站新增至區域中，如下所示：</span><span class="sxs-lookup"><span data-stu-id="f3b9c-169">To resolve this issue, add the site to the zone as follows:</span></span>  
  
1.  <span data-ttu-id="f3b9c-170">在 Internet Explorer] 視窗中，按一下**工具**，然後按一下 [**網際網路選項**。</span><span class="sxs-lookup"><span data-stu-id="f3b9c-170">In the Internet Explorer window, click **Tools**, then click **Internet Options**.</span></span> <span data-ttu-id="f3b9c-171">按一下**安全性**索引標籤，然後選取**信任的網站**區域。</span><span class="sxs-lookup"><span data-stu-id="f3b9c-171">Click the **Security** tab, and then select the **Trusted sites** zone.</span></span>  
  
2.  <span data-ttu-id="f3b9c-172">按一下**自訂層級**設定區域的安全性層級。</span><span class="sxs-lookup"><span data-stu-id="f3b9c-172">Click **Custom level** to set the security level for the zone.</span></span>  
  
3.  <span data-ttu-id="f3b9c-173">在**設定**頁面的 **跨網域存取資料來源**選項，請按一下**提示**。</span><span class="sxs-lookup"><span data-stu-id="f3b9c-173">On the **Settings** page, under the **Access data sources across domains** option, click **Prompt**.</span></span> <span data-ttu-id="f3b9c-174">您將會在有元件需要此權限時收到提示。</span><span class="sxs-lookup"><span data-stu-id="f3b9c-174">You will be prompted when a component requires this permission.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3b9c-175">請參閱</span><span class="sxs-lookup"><span data-stu-id="f3b9c-175">See Also</span></span>  
 [<span data-ttu-id="f3b9c-176">使用商務活動監控</span><span class="sxs-lookup"><span data-stu-id="f3b9c-176">Using Business Activity Monitoring</span></span>](../core/using-business-activity-monitoring.md)