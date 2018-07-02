---
title: BAM 入口網站的已知問題 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e681e910-c664-479c-86f3-a6ae0ec97775
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0533a1431ada4127e2b4746af19b0ccbaf4ecd39
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36973071"
---
# <a name="known-issues-in-the-bam-portal"></a><span data-ttu-id="ebbc7-102">BAM 入口網站中的已知問題</span><span class="sxs-lookup"><span data-stu-id="ebbc7-102">Known Issues in the BAM Portal</span></span>
<span data-ttu-id="ebbc7-103">此主題包含協助您辨識和解決在使用 BAM 入口網站時可能會發生的問題。</span><span class="sxs-lookup"><span data-stu-id="ebbc7-103">This topic contains information to help you identify and resolve issues that can occur while you are using the BAM portal.</span></span>  
  
## <a name="errors-occur-when-the-bam-portal-and-ie-are-on-the-same-computer-and-security-settings-are-low"></a><span data-ttu-id="ebbc7-104">BAM 入口網站和 IE 位於同一部電腦，且安全性設定為低時，會發生錯誤</span><span class="sxs-lookup"><span data-stu-id="ebbc7-104">Errors occur when the BAM Portal and IE are on the same computer, and Security Settings are Low</span></span>  
 <span data-ttu-id="ebbc7-105">**問題**</span><span class="sxs-lookup"><span data-stu-id="ebbc7-105">**Problem**</span></span>  
  
 <span data-ttu-id="ebbc7-106">使用 Internet Explorer 時，您可能會遇到的錯誤訊息**中的伺服器錯誤 ' / BAM' 應用程式**在下列情況下：</span><span class="sxs-lookup"><span data-stu-id="ebbc7-106">When using Internet Explorer, you may encounter the error message **Server Error in '/BAM' Application** under the following circumstances:</span></span>  
  
- <span data-ttu-id="ebbc7-107">按一下指向非現有活動執行個體的相關活動。</span><span class="sxs-lookup"><span data-stu-id="ebbc7-107">While clicking a related activity that points to a non-existing activity instance.</span></span>  
  
- <span data-ttu-id="ebbc7-108">在按一下時**儲存警示**按鈕，在下列案例：</span><span class="sxs-lookup"><span data-stu-id="ebbc7-108">While clicking the **Save Alert** button in the following scenario:</span></span>  
  
  -   <span data-ttu-id="ebbc7-109">您建立查詢 **[activitysearch]** 頁面，然後按一下**設定警示**。</span><span class="sxs-lookup"><span data-stu-id="ebbc7-109">You create a query on the **ActivitySearch** page and then click **Set Alert**.</span></span>  
  
  -   <span data-ttu-id="ebbc7-110">您完成警示欄位，然後按一下**儲存警示**。</span><span class="sxs-lookup"><span data-stu-id="ebbc7-110">You complete the alert fields and then click **Save Alert**.</span></span>  
  
  -   <span data-ttu-id="ebbc7-111">按一下 [上一步] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="ebbc7-111">You click the back button.</span></span>  
  
  -   <span data-ttu-id="ebbc7-112">您按一下**儲存警示**按鈕一次。</span><span class="sxs-lookup"><span data-stu-id="ebbc7-112">You click the **Save Alert** button again.</span></span>  
  
  <span data-ttu-id="ebbc7-113">**原因**</span><span class="sxs-lookup"><span data-stu-id="ebbc7-113">**Cause**</span></span>  
  
  <span data-ttu-id="ebbc7-114">當執行 Internet Explorer 安全性等級設定為低、 Web 要求會以低權限來執行。</span><span class="sxs-lookup"><span data-stu-id="ebbc7-114">When running Internet Explorer with the security level set to low, Web requests are executed with low privileges.</span></span> <span data-ttu-id="ebbc7-115">為了配合 Windows 整合安全性的問題，Internet Explorer 會通過具有很少權限的使用者 Token。</span><span class="sxs-lookup"><span data-stu-id="ebbc7-115">To fulfill the Windows integrated security challenge, Internet Explorer passes a user token with low privileges.</span></span>  
  
  <span data-ttu-id="ebbc7-116">如果您是在安裝 BAM 入口網站的同一部電腦上使用 Internet Explorer，而且在 Internet Explorer 中將安全性層級設定為低，則入口網站會模擬具有低權限 Token 的使用者。</span><span class="sxs-lookup"><span data-stu-id="ebbc7-116">If you are using Internet Explorer on the same computer as the one on which the BAM portal is installed, and you set the security level in Internet Explorer to low, the portal impersonates the user with the low privileges token.</span></span> <span data-ttu-id="ebbc7-117">這個 Token 沒有事件記錄檔的寫入權限。</span><span class="sxs-lookup"><span data-stu-id="ebbc7-117">This token does not have the permissions to write to the event log.</span></span> <span data-ttu-id="ebbc7-118">入口網站在遇到錯誤時，會嘗試將錯誤記到事件記錄檔，但無法這麼做，因為使用者 Token 降低的權限不足以存取事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="ebbc7-118">If the portal encounters an error, it attempts to log it to the event log and will fail since the reduced privileges of the user token are not sufficient to access the event log.</span></span>  
  
  <span data-ttu-id="ebbc7-119">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="ebbc7-119">**Resolution**</span></span>  
  
  <span data-ttu-id="ebbc7-120">如果您需要從本機電腦瀏覽，您應該加入http://localhost至受信任的站台清單。</span><span class="sxs-lookup"><span data-stu-id="ebbc7-120">If you need to browse from the local computer, you should add http://localhost to the list of trusted sites.</span></span>  
  
#### <a name="add-localhost-to-the-list-of-trusted-sites"></a><span data-ttu-id="ebbc7-121">新增 localhost 至信任的網站清單</span><span class="sxs-lookup"><span data-stu-id="ebbc7-121">Add localhost to the list of trusted sites</span></span>  
  
1.  <span data-ttu-id="ebbc7-122">在 Internet Explorer 中，按一下**工具**，然後按一下**網際網路選項**。</span><span class="sxs-lookup"><span data-stu-id="ebbc7-122">In Internet Explorer, click **Tools**, and then click **Internet Options**.</span></span>  
  
2.  <span data-ttu-id="ebbc7-123">按一下 **安全性**索引標籤，然後再按一下**信任的網站**中**選取要檢視或變更安全性設定的區域**視窗。</span><span class="sxs-lookup"><span data-stu-id="ebbc7-123">Click the **Security** tab, and then click **Trusted Sites** in the **Select a zone to view or change security settings** window.</span></span>  
  
3.  <span data-ttu-id="ebbc7-124">按一下 [**站台**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="ebbc7-124">Click the **Sites** button.</span></span>  
  
4.  <span data-ttu-id="ebbc7-125">在 **將這個網站新增到區域**文字方塊中，輸入**http://localhost**。</span><span class="sxs-lookup"><span data-stu-id="ebbc7-125">In the **Add this website to the zone** text box, type **http://localhost**.</span></span> <span data-ttu-id="ebbc7-126">如果**需要伺服器驗證 (https:) 的所有核取方塊**核取方塊，將其清除，然後按一下**新增** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="ebbc7-126">If the **Require server verification (https:) for all sites in this zone** check box is selected, clear it and then click the **Add** button.</span></span> <span data-ttu-id="ebbc7-127">「 網站 」 http://localhost，會出現在**網站**清單。</span><span class="sxs-lookup"><span data-stu-id="ebbc7-127">The site, http://localhost, will appear in the **Websites** list.</span></span>  
  
5.  <span data-ttu-id="ebbc7-128">如有必要，還原**需要伺服器驗證 (https:) 的這個區域中的所有網站**為其原始狀態的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="ebbc7-128">If necessary, restore the **Require server verification (https:) for all sites in this zone** check box to its original state.</span></span>  
  
6.  <span data-ttu-id="ebbc7-129">按一下 **關閉**按鈕，然後再按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="ebbc7-129">Click the **Close** button, and then click **OK**.</span></span>  
  
## <a name="bam-portal-aggregations-do-not-populate-existing-data-when-using-an-ip-address-as-a-url-in-internet-explorer"></a><span data-ttu-id="ebbc7-130">Bam 入口網站彙總不會填入現有的資料時使用的 IP 位址為 Internet Explorer 中的 URL</span><span class="sxs-lookup"><span data-stu-id="ebbc7-130">Bam Portal Aggregations Do Not Populate Existing Data When Using an IP Address as a URL in Internet Explorer</span></span>
 <span data-ttu-id="ebbc7-131">**問題**</span><span class="sxs-lookup"><span data-stu-id="ebbc7-131">**Problem**</span></span>  
  
 <span data-ttu-id="ebbc7-132">彙總時使用的 IP 位址做為 URL，使用 Internet Explorer，檢視 BAM 入口網站，顯示下列訊息: 「 沒有詳細資料。</span><span class="sxs-lookup"><span data-stu-id="ebbc7-132">When using an IP address as a URL with Internet Explorer to view the BAM portal, aggregations display the following message: "No detail.</span></span> <span data-ttu-id="ebbc7-133">無法處理查詢」。</span><span class="sxs-lookup"><span data-stu-id="ebbc7-133">The query could not be processed."</span></span>  
  
 <span data-ttu-id="ebbc7-134">**原因**</span><span class="sxs-lookup"><span data-stu-id="ebbc7-134">**Cause**</span></span>  
  
 <span data-ttu-id="ebbc7-135">在 Internet Explorer 中的預設安全性設定可能會防止存取使用 IPv4 和 IPv6 位址做為 Url 的網站。</span><span class="sxs-lookup"><span data-stu-id="ebbc7-135">The default security settings in Internet Explorer may prevent access to sites using IPv4 and IPv6 addresses as URLs.</span></span>  
  
 <span data-ttu-id="ebbc7-136">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="ebbc7-136">**Resolution**</span></span>  
  
 <span data-ttu-id="ebbc7-137">將網站位址加入至信任的網站清單，並且啟用存取各網域的資料來源。</span><span class="sxs-lookup"><span data-stu-id="ebbc7-137">Add the site address to the trusted sites list and enable access to data sources across domains.</span></span>  
  
#### <a name="add-the-ip-address-to-the-trusted-sites-list"></a><span data-ttu-id="ebbc7-138">將 IP 位址新增至信任的網站清單</span><span class="sxs-lookup"><span data-stu-id="ebbc7-138">Add the IP address to the trusted sites list</span></span>  
  
1.  <span data-ttu-id="ebbc7-139">在 Internet Explorer 中，按一下**工具**，然後按一下**網際網路選項**。</span><span class="sxs-lookup"><span data-stu-id="ebbc7-139">In Internet Explorer, click **Tools**, and then click **Internet Options**.</span></span>  
  
2.  <span data-ttu-id="ebbc7-140">按一下 **安全性**索引標籤，然後再按一下**信任的網站**安全性區域。</span><span class="sxs-lookup"><span data-stu-id="ebbc7-140">Click the **Security** tab, and then click the **Trusted sites** security zone.</span></span>  
  
3.  <span data-ttu-id="ebbc7-141">按一下 [**站台**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="ebbc7-141">Click the **Sites** button.</span></span>  
  
4.  <span data-ttu-id="ebbc7-142">在 **將這個網站新增到區域**，輸入 BAM 入口網站的 IP 位址，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="ebbc7-142">In **Add this website to the zone**, type the IP address of the BAM portal, and then click **Add**.</span></span>  
  
5.  <span data-ttu-id="ebbc7-143">按一下 [關閉]，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="ebbc7-143">Click **Close**, and then click **OK**.</span></span>  
  
#### <a name="enable-access-to-data-sources-across-domains"></a><span data-ttu-id="ebbc7-144">啟用各網域的資料來源的存取權</span><span class="sxs-lookup"><span data-stu-id="ebbc7-144">Enable access to data sources across domains</span></span>  
  
1.  <span data-ttu-id="ebbc7-145">在 Internet Explorer 中，按一下**工具**，然後按一下**網際網路選項**。</span><span class="sxs-lookup"><span data-stu-id="ebbc7-145">In Internet Explorer, click **Tools**, and then click **Internet Options**.</span></span>  
  
2.  <span data-ttu-id="ebbc7-146">按一下 **安全性**索引標籤，然後再按一下**信任的網站**安全性區域。</span><span class="sxs-lookup"><span data-stu-id="ebbc7-146">Click the **Security** tab, and then click the **Trusted Sites** security zone.</span></span>  
  
3.  <span data-ttu-id="ebbc7-147">按一下 **自訂層級**按鈕，您向下捲動至**其他**節點**設定**樹狀目錄中。</span><span class="sxs-lookup"><span data-stu-id="ebbc7-147">Click the **Custom Level** button as you scroll down to the **Miscellaneous** node of the **Settings** tree.</span></span>  
  
4.  <span data-ttu-id="ebbc7-148">在 **跨網域存取資料來源**節點中，按一下**啟用選項**按鈕，然後再按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="ebbc7-148">In the **Access data sources across domains** node, click the **Enable radio** button, and then click **OK**.</span></span>  
  
## <a name="bmexe-does-not-run-in-powershell"></a><span data-ttu-id="ebbc7-149">BM.exe 未在 PowerShell 中執行</span><span class="sxs-lookup"><span data-stu-id="ebbc7-149">BM.exe does not run in PowerShell</span></span>  
 <span data-ttu-id="ebbc7-150">**問題**</span><span class="sxs-lookup"><span data-stu-id="ebbc7-150">**Problem**</span></span>  
  
 <span data-ttu-id="ebbc7-151">下列命令在 PowerShell 中執行時擲出錯誤。</span><span class="sxs-lookup"><span data-stu-id="ebbc7-151">The following command throws an error when run in PowerShell.</span></span>  
  
```  
bm.exe get-config -FileName:config.xml  
```  
  
 <span data-ttu-id="ebbc7-152">**原因**</span><span class="sxs-lookup"><span data-stu-id="ebbc7-152">**Cause**</span></span>  
  
 <span data-ttu-id="ebbc7-153">PowerShell 找不到 .exe 和組態檔的路徑。</span><span class="sxs-lookup"><span data-stu-id="ebbc7-153">PowerShell could not locate the path of .exe and config files.</span></span>  
  
 <span data-ttu-id="ebbc7-154">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="ebbc7-154">**Resolution**</span></span>  
  
 <span data-ttu-id="ebbc7-155">如果您在 PowerShell 中使用 bm.exe，請指定 .exe 和組態檔的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="ebbc7-155">If you use bm.exe in PowerShell, specify the full path of .exe and config files.</span></span> <span data-ttu-id="ebbc7-156">例如：`bm.exe get-config -FileName:config.xml`應指定為`“%BizTalkPathTracking%”\bm.exe get-config -FileName:”%InstallDir%”\Tracking\config.xml`。</span><span class="sxs-lookup"><span data-stu-id="ebbc7-156">For example: `bm.exe get-config -FileName:config.xml` should be specified as `“%BizTalkPathTracking%”\bm.exe get-config -FileName:”%InstallDir%”\Tracking\config.xml`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebbc7-157">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ebbc7-157">See Also</span></span>  
 [<span data-ttu-id="ebbc7-158">規劃 BAM 入口網站</span><span class="sxs-lookup"><span data-stu-id="ebbc7-158">Planning for the BAM Portal</span></span>](../core/planning-for-the-bam-portal.md)