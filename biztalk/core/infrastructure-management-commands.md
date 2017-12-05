---
title: "基礎結構管理命令 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a2f1a88c-19fc-4384-b6bb-f95962a32921
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c82dc5cb65156af86e66abfeffef206f18add5cb
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="infrastructure-management-commands"></a><span data-ttu-id="19ff4-102">基礎結構管理命令</span><span class="sxs-lookup"><span data-stu-id="19ff4-102">Infrastructure Management Commands</span></span>
<span data-ttu-id="19ff4-103">BAM 管理 (BM) 公用程式組態命令可讓您取得及更新 BAM 組態。</span><span class="sxs-lookup"><span data-stu-id="19ff4-103">The BAM Management (BM) utility configuration commands allow you get and update the BAM configuration.</span></span>  
  
-   <span data-ttu-id="19ff4-104">取得組態： 取得 BAM 組態檔。</span><span class="sxs-lookup"><span data-stu-id="19ff4-104">get-config: Gets the BAM configuration file.</span></span>  
  
-   <span data-ttu-id="19ff4-105">更新設定： 更新 BAM 組態。</span><span class="sxs-lookup"><span data-stu-id="19ff4-105">update-config: Updates the BAM configuration.</span></span>  
  
-   <span data-ttu-id="19ff4-106">取得變更： 列出 BAM 基礎結構的變更。</span><span class="sxs-lookup"><span data-stu-id="19ff4-106">get-changes: Lists changes to the BAM infrastructure.</span></span>  
  
-   <span data-ttu-id="19ff4-107">get defxml： 取得包含 BAM 主要匯入資料庫中的所有成品的檔案。</span><span class="sxs-lookup"><span data-stu-id="19ff4-107">get-defxml: Gets a file containing all the artifacts in the BAM Primary Import database.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="19ff4-108">您可以藉由啟用任何 BM 公用程式命令的追蹤**-追蹤： 在 &#124; 關閉**切換參數。</span><span class="sxs-lookup"><span data-stu-id="19ff4-108">You can enable tracing on any BM utility command by including the **-Trace:on&#124;off** parameter switch.</span></span> <span data-ttu-id="19ff4-109">使用追蹤參數會覆寫組態檔中的追蹤設定。</span><span class="sxs-lookup"><span data-stu-id="19ff4-109">Using the Trace switch overrides the tracing settings in the configuration file.</span></span> <span data-ttu-id="19ff4-110">此參數可以搭配任何一般 BM 命令使用。</span><span class="sxs-lookup"><span data-stu-id="19ff4-110">The switch can be used in conjunction with any normal BM command.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="19ff4-111">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="19ff4-111">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="get-config-command"></a><span data-ttu-id="19ff4-112">get-config 命令</span><span class="sxs-lookup"><span data-stu-id="19ff4-112">get-config Command</span></span>  
 <span data-ttu-id="19ff4-113">**使用方式**</span><span class="sxs-lookup"><span data-stu-id="19ff4-113">**Usage**</span></span>  
  
 <span data-ttu-id="19ff4-114">**bm.exe get-config-FileName:\<輸出檔\>[-Server:\<伺服器\>] [-Database:\<資料庫\>]**</span><span class="sxs-lookup"><span data-stu-id="19ff4-114">**bm.exe get-config -FileName:\<output file\> [ -Server:\<server\> ][ -Database:\<database\> ]**</span></span>  
  
 <span data-ttu-id="19ff4-115">**參數**</span><span class="sxs-lookup"><span data-stu-id="19ff4-115">**Parameters**</span></span>  
  
|<span data-ttu-id="19ff4-116">參數</span><span class="sxs-lookup"><span data-stu-id="19ff4-116">Parameter</span></span>|<span data-ttu-id="19ff4-117">Description</span><span class="sxs-lookup"><span data-stu-id="19ff4-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="19ff4-118">檔案名稱：\<輸出檔\></span><span class="sxs-lookup"><span data-stu-id="19ff4-118">FileName:\<output file\></span></span>|<span data-ttu-id="19ff4-119">組態檔的儲存路徑和名稱。</span><span class="sxs-lookup"><span data-stu-id="19ff4-119">The path and name to which to save the configuration file.</span></span>|  
|<span data-ttu-id="19ff4-120">伺服器：\<伺服器\></span><span class="sxs-lookup"><span data-stu-id="19ff4-120">Server:\<server\></span></span>|<span data-ttu-id="19ff4-121">選擇性： 取得設定的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="19ff4-121">Optional: The name of the server from which to get the configuration.</span></span> <span data-ttu-id="19ff4-122">伺服器和執行 bm.exe 的電腦必須位在相同網域中。</span><span class="sxs-lookup"><span data-stu-id="19ff4-122">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="19ff4-123">如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。</span><span class="sxs-lookup"><span data-stu-id="19ff4-123">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="19ff4-124">資料庫：\<資料庫\></span><span class="sxs-lookup"><span data-stu-id="19ff4-124">Database:\<database\></span></span>|<span data-ttu-id="19ff4-125">選擇性： 取得設定的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="19ff4-125">Optional: The name of the database from which to get the configuration.</span></span> <span data-ttu-id="19ff4-126">如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。</span><span class="sxs-lookup"><span data-stu-id="19ff4-126">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="19ff4-127">擷取 BAM 組態 XML，並將它儲存在指定的檔案中。</span><span class="sxs-lookup"><span data-stu-id="19ff4-127">Retrieves the BAM configuration XML and saves it in the specified file.</span></span> <span data-ttu-id="19ff4-128">**Get-config**命令不會覆寫現有的檔案。</span><span class="sxs-lookup"><span data-stu-id="19ff4-128">The **get-config** command will not overwrite the existing file.</span></span>  
  
 <span data-ttu-id="19ff4-129">**範例**</span><span class="sxs-lookup"><span data-stu-id="19ff4-129">**Examples**</span></span>  
  
```  
bm.exe get-config -FileName:MyConfig.xml  
bm.exe get-config -FileName:BAMConfiguration.xml -Server:OrdersServer  
```  
  
## <a name="update-config-command"></a><span data-ttu-id="19ff4-130">update-config 命令</span><span class="sxs-lookup"><span data-stu-id="19ff4-130">update-config Command</span></span>  
 <span data-ttu-id="19ff4-131">**使用方式**</span><span class="sxs-lookup"><span data-stu-id="19ff4-131">**Usage**</span></span>  
  
 <span data-ttu-id="19ff4-132">**bm.exe 更新-config-FileName:\<組態檔\>**</span><span class="sxs-lookup"><span data-stu-id="19ff4-132">**bm.exe update-config -FileName:\<config file\>**</span></span>  
  
 <span data-ttu-id="19ff4-133">**參數**</span><span class="sxs-lookup"><span data-stu-id="19ff4-133">**Parameters**</span></span>  
  
|<span data-ttu-id="19ff4-134">參數</span><span class="sxs-lookup"><span data-stu-id="19ff4-134">Parameter</span></span>|<span data-ttu-id="19ff4-135">Description</span><span class="sxs-lookup"><span data-stu-id="19ff4-135">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="19ff4-136">檔案名稱：\<組態檔\></span><span class="sxs-lookup"><span data-stu-id="19ff4-136">FileName:\<config file\></span></span>|<span data-ttu-id="19ff4-137">用於更新 BAM 基礎結構的組態檔所在路徑和名稱。</span><span class="sxs-lookup"><span data-stu-id="19ff4-137">The path and name of the configuration file from which to update the BAM infrastructure.</span></span>|  
  
 <span data-ttu-id="19ff4-138">從含有 BAM 組態 XML 的檔案來更新本機電腦上的組態。</span><span class="sxs-lookup"><span data-stu-id="19ff4-138">Updates the configuration on the local computer from a file containing BAM configuration XML.</span></span> <span data-ttu-id="19ff4-139">您可以加入目前組態中不存在的伺服器和資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="19ff4-139">You can add server and database names that do not already exist in the current configuration.</span></span> <span data-ttu-id="19ff4-140">變更已部署動態基礎結構的伺服器或資料庫名稱會發生錯誤，且 bm.exe 將報告錯誤。</span><span class="sxs-lookup"><span data-stu-id="19ff4-140">Changing server or database names that already have dynamic infrastructure deployed in will fail and bm.exe will report an error.</span></span>  
  
 <span data-ttu-id="19ff4-141">如果您修改檔案所傳遞之警示的檔案放置位置，</span><span class="sxs-lookup"><span data-stu-id="19ff4-141">If you modify the file drop location for alerts delivered by file.</span></span> <span data-ttu-id="19ff4-142">就必須重新啟動 SQL Notifications Services。</span><span class="sxs-lookup"><span data-stu-id="19ff4-142">You must restart the SQL Notifications Services.</span></span> <span data-ttu-id="19ff4-143">如果 NS 服務未重新啟動，將會繼續傳遞警示至原始檔案放置位置。</span><span class="sxs-lookup"><span data-stu-id="19ff4-143">If the NS service is not restarted, alerts will continue being delivered to the original file drop location.</span></span>  
  
 <span data-ttu-id="19ff4-144">在 BAM 組態檔中修改底下這一行即可變更檔案放置位置。</span><span class="sxs-lookup"><span data-stu-id="19ff4-144">The file drop location is changed by modifying the following line of the BAM configuration file.</span></span>  
  
 <span data-ttu-id="19ff4-145">\<屬性名稱 ="FileDropUNC"\>\\\\< 電腦名稱\>\alerts\</Property\></span><span class="sxs-lookup"><span data-stu-id="19ff4-145">\<Property Name="FileDropUNC"\>\\\\<computer name\>\alerts\</Property\></span></span>  
  
 <span data-ttu-id="19ff4-146">如需更新參照的適當步驟，請參閱[備份和還原 BizTalk Server](../core/backing-up-and-restoring-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="19ff4-146">For appropriate steps to update the references, see [Backing Up and Restoring BizTalk Server](../core/backing-up-and-restoring-biztalk-server.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="19ff4-147">如果您已設定 BAM 警示，而在執行 update-database 命令時使用了不含 alerts 區段的 BAM 組態檔，則因 bm.exe 會覆寫組態，以致警示將不再發生作用。</span><span class="sxs-lookup"><span data-stu-id="19ff4-147">If you execute an update-database command, using a BAM configuration file that does not contain an alerts section, and you have already configured BAM Alerts, bm.exe will overwrite the configuration such that alerts will no longer function.</span></span>  
  
 <span data-ttu-id="19ff4-148">**範例**</span><span class="sxs-lookup"><span data-stu-id="19ff4-148">**Examples**</span></span>  
  
```  
bm.exe update-config -FileName:MyConfig.xml  
```  
  
## <a name="get-changes-command"></a><span data-ttu-id="19ff4-149">get-changes 命令</span><span class="sxs-lookup"><span data-stu-id="19ff4-149">get-changes Command</span></span>  
 <span data-ttu-id="19ff4-150">**使用方式**</span><span class="sxs-lookup"><span data-stu-id="19ff4-150">**Usage**</span></span>  
  
 <span data-ttu-id="19ff4-151">**bm.exe get 變更 [-Server:\<伺服器\>] [-Database:\<資料庫\>]**</span><span class="sxs-lookup"><span data-stu-id="19ff4-151">**bm.exe get-changes [ -Server:\<server\> ][ -Database:\<database\> ]**</span></span>  
  
 <span data-ttu-id="19ff4-152">**參數**</span><span class="sxs-lookup"><span data-stu-id="19ff4-152">**Parameters**</span></span>  
  
|<span data-ttu-id="19ff4-153">參數</span><span class="sxs-lookup"><span data-stu-id="19ff4-153">Parameter</span></span>|<span data-ttu-id="19ff4-154">Description</span><span class="sxs-lookup"><span data-stu-id="19ff4-154">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="19ff4-155">伺服器：\<伺服器\></span><span class="sxs-lookup"><span data-stu-id="19ff4-155">Server:\<server\></span></span>|<span data-ttu-id="19ff4-156">選擇性： 在 BAM 主要匯入資料庫所在的伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="19ff4-156">Optional: The name of the server on which the BAM Primary Import database resides.</span></span> <span data-ttu-id="19ff4-157">伺服器和執行 bm.exe 的電腦必須位在相同網域中。</span><span class="sxs-lookup"><span data-stu-id="19ff4-157">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="19ff4-158">如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。</span><span class="sxs-lookup"><span data-stu-id="19ff4-158">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="19ff4-159">資料庫：\<資料庫\></span><span class="sxs-lookup"><span data-stu-id="19ff4-159">Database:\<database\></span></span>|<span data-ttu-id="19ff4-160">選擇性： 如果未指定的名稱，bm.exe 會使用預設名稱 BamPrimaryImport。</span><span class="sxs-lookup"><span data-stu-id="19ff4-160">Optional: If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="19ff4-161">取得 BAM 主要匯入資料庫套用的變更清單。</span><span class="sxs-lookup"><span data-stu-id="19ff4-161">Gets a list of changes applied to the BAM Primary Import database.</span></span> <span data-ttu-id="19ff4-162">使用此命令可以稽核 BAM 基礎結構所做的變更。</span><span class="sxs-lookup"><span data-stu-id="19ff4-162">You can use this command to audit changes to the BAM Infrastructure.</span></span> <span data-ttu-id="19ff4-163">此命令會傳回下列資訊：</span><span class="sxs-lookup"><span data-stu-id="19ff4-163">The command returns the following information:</span></span>  
  
 <span data-ttu-id="19ff4-164">從事變更的命令類型，以及套用變更所依據的檔案。</span><span class="sxs-lookup"><span data-stu-id="19ff4-164">The command type of the change and the file from which the change was applied.</span></span>  
  
 <span data-ttu-id="19ff4-165">套用變更的使用者。</span><span class="sxs-lookup"><span data-stu-id="19ff4-165">Who applied the change.</span></span>  
  
 <span data-ttu-id="19ff4-166">已變更的活動。</span><span class="sxs-lookup"><span data-stu-id="19ff4-166">Which activities were changed.</span></span>  
  
 <span data-ttu-id="19ff4-167">已變更的檢視。</span><span class="sxs-lookup"><span data-stu-id="19ff4-167">Which views were changed.</span></span>  
  
 <span data-ttu-id="19ff4-168">**範例**</span><span class="sxs-lookup"><span data-stu-id="19ff4-168">**Examples**</span></span>  
  
```  
bm.exe get-changes  
```  
  
 <span data-ttu-id="19ff4-169">命令的輸出</span><span class="sxs-lookup"><span data-stu-id="19ff4-169">Output of command</span></span>  
  
 <span data-ttu-id="19ff4-170">\#1： 部署 c:\bam\ordermanagement.xml</span><span class="sxs-lookup"><span data-stu-id="19ff4-170">\#1: Deploy c:\bam\ordermanagement.xml</span></span>  
  
 <span data-ttu-id="19ff4-171">By domain\user at 12/30/2005 8:17:08 PM (v3.5.1536.0).</span><span class="sxs-lookup"><span data-stu-id="19ff4-171">By domain\user at 12/30/2005 8:17:08 PM (v3.5.1536.0).</span></span>  
  
 <span data-ttu-id="19ff4-172">活動: [ordermgmt]</span><span class="sxs-lookup"><span data-stu-id="19ff4-172">Activities: OrderMgmt</span></span>  
  
 <span data-ttu-id="19ff4-173">檢視： SalesManager</span><span class="sxs-lookup"><span data-stu-id="19ff4-173">Views: SalesManager</span></span>  
  
## <a name="get-defxml-command"></a><span data-ttu-id="19ff4-174">get-defxml 命令</span><span class="sxs-lookup"><span data-stu-id="19ff4-174">get-defxml Command</span></span>  
 <span data-ttu-id="19ff4-175">**使用方式**</span><span class="sxs-lookup"><span data-stu-id="19ff4-175">**Usage**</span></span>  
  
 <span data-ttu-id="19ff4-176">**bm.exe get defxml-FileName:\<輸出檔\>[-Server:\<伺服器\>] [-Database:\<資料庫\>]**</span><span class="sxs-lookup"><span data-stu-id="19ff4-176">**bm.exe get-defxml -FileName:\<output file\>[ -Server:\<server\> ][ -Database:\<database\> ]**</span></span>  
  
 <span data-ttu-id="19ff4-177">**參數**</span><span class="sxs-lookup"><span data-stu-id="19ff4-177">**Parameters**</span></span>  
  
|<span data-ttu-id="19ff4-178">參數</span><span class="sxs-lookup"><span data-stu-id="19ff4-178">Parameter</span></span>|<span data-ttu-id="19ff4-179">Description</span><span class="sxs-lookup"><span data-stu-id="19ff4-179">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="19ff4-180">檔案名稱：\<輸出檔\></span><span class="sxs-lookup"><span data-stu-id="19ff4-180">FileName:\<output file\></span></span>|<span data-ttu-id="19ff4-181">用來儲存定義的檔案所在路徑和名稱。</span><span class="sxs-lookup"><span data-stu-id="19ff4-181">The path and name of the file to which to save the definitions.</span></span>|  
|<span data-ttu-id="19ff4-182">伺服器：\<伺服器\></span><span class="sxs-lookup"><span data-stu-id="19ff4-182">Server:\<server\></span></span>|<span data-ttu-id="19ff4-183">選擇性： 定義取得來源的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="19ff4-183">Optional: The name of the server from which to get the definitions.</span></span> <span data-ttu-id="19ff4-184">伺服器和執行 bm.exe 的電腦必須位在相同網域中。</span><span class="sxs-lookup"><span data-stu-id="19ff4-184">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="19ff4-185">如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。</span><span class="sxs-lookup"><span data-stu-id="19ff4-185">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="19ff4-186">資料庫：\<資料庫\></span><span class="sxs-lookup"><span data-stu-id="19ff4-186">Database:\<database\></span></span>|<span data-ttu-id="19ff4-187">選擇性： 定義取得來源的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="19ff4-187">Optional: The name of the database from which to get the definitions.</span></span> <span data-ttu-id="19ff4-188">如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。</span><span class="sxs-lookup"><span data-stu-id="19ff4-188">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="19ff4-189">從 BAM 主要匯入資料庫擷取所有成品，然後另存為 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="19ff4-189">Retrieves all artifacts on from the BAM Primary Import database and saves them in a file as XML.</span></span> <span data-ttu-id="19ff4-190">此命令不會覆寫現有的檔案。</span><span class="sxs-lookup"><span data-stu-id="19ff4-190">The command will not overwrite existing files.</span></span>  
  
 <span data-ttu-id="19ff4-191">**範例**</span><span class="sxs-lookup"><span data-stu-id="19ff4-191">**Examples**</span></span>  
  
```  
bm.exe get-defxml -FileName:BAMDefinition.xml  
bm.exe get-defxml -FileName:MyDef.xml -Server:MyServer -Database:MyPI  
```  
  
## <a name="see-also"></a><span data-ttu-id="19ff4-192">請參閱</span><span class="sxs-lookup"><span data-stu-id="19ff4-192">See Also</span></span>  
 [<span data-ttu-id="19ff4-193">BAM 管理公用程式</span><span class="sxs-lookup"><span data-stu-id="19ff4-193">BAM Management Utility</span></span>](../core/bam-management-utility.md)