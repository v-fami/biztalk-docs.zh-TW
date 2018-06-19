---
title: 部署 BAM 定義 （觀察模型） 命令 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: df7914f3-7a92-4ab2-bd0e-94a2eed4825e
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0dba1e1a4f54b3b33ebca8297cfe9beef7c4f868
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25973188"
---
# <a name="deployment-of-bam-definition-observation-model-commands"></a><span data-ttu-id="52118-102">BAM 定義的部署 (觀察模型) 命令</span><span class="sxs-lookup"><span data-stu-id="52118-102">Deployment of BAM Definition (Observation Model) Commands</span></span>
<span data-ttu-id="52118-103">BAM 管理公用程式部署命令可用來套用、修改和移除定義。</span><span class="sxs-lookup"><span data-stu-id="52118-103">The BAM management utility deployment commands allow you to apply, modify, and remove definitions.</span></span>  
  
-   <span data-ttu-id="52118-104">deploy-all-definitionfile： 部署 BAM 定義。</span><span class="sxs-lookup"><span data-stu-id="52118-104">deploy-all: Deploys a BAM definition.</span></span>  
  
-   <span data-ttu-id="52118-105">更新所有： 更新 BAM 定義。</span><span class="sxs-lookup"><span data-stu-id="52118-105">update-all: Updates a BAM definition.</span></span>  
  
-   <span data-ttu-id="52118-106">移除 all： 移除 BAM 定義。</span><span class="sxs-lookup"><span data-stu-id="52118-106">remove-all: Removes a BAM definition.</span></span>  
  
-   <span data-ttu-id="52118-107">更新 livedataworkbook： 更新即時資料活頁簿中的資料庫連接資訊。</span><span class="sxs-lookup"><span data-stu-id="52118-107">update-livedataworkbook: Updates the database connection information in a live data workbook.</span></span>  
  
-   <span data-ttu-id="52118-108">重新產生 livedataworkbook： 重新產生即時資料活頁簿，伺服器上的。</span><span class="sxs-lookup"><span data-stu-id="52118-108">regenerate-livedataworkbook: Regenerates the live data workbook on the server.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="52118-109">您可以藉由啟用任何 BM 公用程式命令的追蹤 **-追蹤： 在 &#124; 關閉**切換參數。</span><span class="sxs-lookup"><span data-stu-id="52118-109">You can enable tracing on any BM utility command by including the **-Trace:on&#124;off** parameter switch.</span></span> <span data-ttu-id="52118-110">使用追蹤參數會覆寫組態檔中的追蹤設定。</span><span class="sxs-lookup"><span data-stu-id="52118-110">Using the Trace switch overrides the tracing settings in the configuration file.</span></span> <span data-ttu-id="52118-111">此參數可以搭配任何一般 BM 命令使用。</span><span class="sxs-lookup"><span data-stu-id="52118-111">The switch can be used in conjunction with any normal BM command.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="52118-112">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="52118-112">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="deploy-all-command"></a><span data-ttu-id="52118-113">deploy-all 命令</span><span class="sxs-lookup"><span data-stu-id="52118-113">deploy-all Command</span></span>  
 <span data-ttu-id="52118-114">**使用方式**</span><span class="sxs-lookup"><span data-stu-id="52118-114">**Usage**</span></span>  
  
 <span data-ttu-id="52118-115">**bm.exe deploy-all-definitionfile-DefinitionFile:\<def 檔\>[-Server:\<伺服器\>] [-Database:\<資料庫\>]**</span><span class="sxs-lookup"><span data-stu-id="52118-115">**bm.exe deploy-all -DefinitionFile:\<def file\>[ -Server:\<server\> ][ -Database:\<database\> ]**</span></span>  
  
 <span data-ttu-id="52118-116">**參數**</span><span class="sxs-lookup"><span data-stu-id="52118-116">**Parameters**</span></span>  
  
|<span data-ttu-id="52118-117">參數</span><span class="sxs-lookup"><span data-stu-id="52118-117">Parameter</span></span>|<span data-ttu-id="52118-118">Description</span><span class="sxs-lookup"><span data-stu-id="52118-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="52118-119">DefinitionFile:\<def 檔案\></span><span class="sxs-lookup"><span data-stu-id="52118-119">DefinitionFile:\<def file\></span></span>|<span data-ttu-id="52118-120">含有所要部署之定義的檔案所在路徑和名稱。</span><span class="sxs-lookup"><span data-stu-id="52118-120">The path and name of the file containing the definitions to deploy.</span></span>|  
|<span data-ttu-id="52118-121">伺服器：\<伺服器\></span><span class="sxs-lookup"><span data-stu-id="52118-121">Server:\<server\></span></span>|<span data-ttu-id="52118-122">選擇性： 要用來將定義部署的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="52118-122">Optional: The name of the server to which to deploy the definitions.</span></span> <span data-ttu-id="52118-123">伺服器和執行 bm.exe 的電腦必須位在相同網域中。</span><span class="sxs-lookup"><span data-stu-id="52118-123">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="52118-124">如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。</span><span class="sxs-lookup"><span data-stu-id="52118-124">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="52118-125">資料庫：\<資料庫\></span><span class="sxs-lookup"><span data-stu-id="52118-125">Database:\<database\></span></span>|<span data-ttu-id="52118-126">選擇性： 要用來將定義部署的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="52118-126">Optional: The name of the database to which to deploy the definitions.</span></span> <span data-ttu-id="52118-127">如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。</span><span class="sxs-lookup"><span data-stu-id="52118-127">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="52118-128">從指定的 BAM 定義 XML 檔案部署所有成品至指定的伺服器和資料庫。</span><span class="sxs-lookup"><span data-stu-id="52118-128">Deploys all artifacts from the specified BAM definition XML file to the specified server and database.</span></span> <span data-ttu-id="52118-129">檔案可以是包含 BAM 定義 XML 的文字檔或 BAM Excel 活頁簿。</span><span class="sxs-lookup"><span data-stu-id="52118-129">The file can be a text file containing the BAM definition XML or a BAM Excel workbook.</span></span> <span data-ttu-id="52118-130">定義檔必須只包含新成品。</span><span class="sxs-lookup"><span data-stu-id="52118-130">The definition file must include only new artifacts.</span></span> <span data-ttu-id="52118-131">如果檔案包含已部署的成品，部署將會失敗並報告錯誤。</span><span class="sxs-lookup"><span data-stu-id="52118-131">If the file contains artifacts that have already been deployed, the deployment will fail and report an error.</span></span>  
  
 <span data-ttu-id="52118-132">**部署 BAM 定義的考量**</span><span class="sxs-lookup"><span data-stu-id="52118-132">**Considerations for deploying BAM definitions**</span></span>  
  
 <span data-ttu-id="52118-133">部署警示訂閱時，訂閱者的使用者識別碼必須指定成「網域\使用者」格式。</span><span class="sxs-lookup"><span data-stu-id="52118-133">When deploying alert subscriptions, user IDs of the subscribers must be specified in a domain\user format.</span></span>  
  
 <span data-ttu-id="52118-134">分散式的交易協調器 (DTC) 服務必須執行所在之電腦上**deploy-all-definitionfile**發出命令。</span><span class="sxs-lookup"><span data-stu-id="52118-134">The distributed transaction coordinator (DTC) service must be running on the computer on which the **deploy-all** command is issued.</span></span>  
  
 <span data-ttu-id="52118-135">部署定義時，BAM 管理公用程式對於即時彙總 (RTA) 檢視僅支援 14 個維度層級。</span><span class="sxs-lookup"><span data-stu-id="52118-135">When deploying a definition the BAM Management utility only supports 14 dimension levels in Real-Time Aggregation (RTA) view.</span></span> <span data-ttu-id="52118-136">部署的層級數若超出此限，將傳回「部署失敗」錯誤。</span><span class="sxs-lookup"><span data-stu-id="52118-136">Deploying additional levels returns a Deployment failed error.</span></span>  
  
 <span data-ttu-id="52118-137">如果您用不同的語言設定來定義多個檢視，再將方案部署至採用單一語言的伺服器，就無法解除部署這些檢視。</span><span class="sxs-lookup"><span data-stu-id="52118-137">If you define multiple views that use different language settings and deploy your solution to a server that uses a single language, the views will be undeployable.</span></span> <span data-ttu-id="52118-138">唯有當任何的排程彙總都不需仰賴 BAM 定義提供 OLAP 的情況下，才支援這種做法。</span><span class="sxs-lookup"><span data-stu-id="52118-138">This scenario is supported only in a case where you don't have scheduled aggregations that require OLAP as part of the BAM definition.</span></span>  
  
 <span data-ttu-id="52118-139">如果啟用 BAM 警示，BAM 管理公用程式會將部署的活動檢視總數限制為 49 個。</span><span class="sxs-lookup"><span data-stu-id="52118-139">The BAM management utility limits you to 49 deployed activity views when BAM Alerts are enabled.</span></span> <span data-ttu-id="52118-140">活動檢視總數的計算方式為：各檢視分別乘以其上層活動的數目之後加總。</span><span class="sxs-lookup"><span data-stu-id="52118-140">The number of activity views is calculated as the Summation 1..N of View(n) multiplied by the number of parent activities.</span></span>  <span data-ttu-id="52118-141">例如，如果您部署了涉及兩個活動的單一檢視，就視同兩個活動檢視。</span><span class="sxs-lookup"><span data-stu-id="52118-141">For example, if you deploy a view that is based on two activities, you get two activity views.</span></span>  <span data-ttu-id="52118-142">假設您部署兩個檢視，其中之一跨越兩個活動，而另一檢視涉及單一活動，則總計為 3 個活動檢視。</span><span class="sxs-lookup"><span data-stu-id="52118-142">If you deploy two views, one of which spans two activities and the other based on a single activity, you have 3 activity views.</span></span>  
  
 <span data-ttu-id="52118-143">如果 BAM 定義將多個樞紐分析表定義成相同的 RTA 與 Cube 名稱組合，BAM 管理公用程式會封鎖該定義的部署作業。</span><span class="sxs-lookup"><span data-stu-id="52118-143">The BAM Management utility blocks deployment of BAM definitions which have multiple PivotTable reports which are defined on the same RTA and cube name combination.</span></span> <span data-ttu-id="52118-144">Bm.exe 將終止部署並傳回下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="52118-144">Bm.exe will terminate the deployment and return the following error:</span></span>  
  
 <span data-ttu-id="52118-145">正在部署檢視...錯誤： BAM 部署失敗。</span><span class="sxs-lookup"><span data-stu-id="52118-145">Deploying View... ERROR: The BAM deployment failed.</span></span>  
  
 <span data-ttu-id="52118-146">指定的 RTA 和 Cube 只能定義一個樞紐分析檢視。</span><span class="sxs-lookup"><span data-stu-id="52118-146">Only one PivotTable view can be defined on a given RTA and cube.</span></span>  
  
 <span data-ttu-id="52118-147">以下所列的名稱都是保留字，如果使用將導致定義部署失敗：</span><span class="sxs-lookup"><span data-stu-id="52118-147">The following list of names are reserved and will cause the definition deployment to fail:</span></span>  
  
-   <span data-ttu-id="52118-148">RecordID</span><span class="sxs-lookup"><span data-stu-id="52118-148">RecordID</span></span>  
  
-   <span data-ttu-id="52118-149">ActivityID</span><span class="sxs-lookup"><span data-stu-id="52118-149">ActivityID</span></span>  
  
-   <span data-ttu-id="52118-150">IsVisible</span><span class="sxs-lookup"><span data-stu-id="52118-150">IsVisible</span></span>  
  
-   <span data-ttu-id="52118-151">IsComplete</span><span class="sxs-lookup"><span data-stu-id="52118-151">IsComplete</span></span>  
  
-   <span data-ttu-id="52118-152">LastModified</span><span class="sxs-lookup"><span data-stu-id="52118-152">LastModified</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="52118-153">如果 bm.exe 在部署期間遇到錯誤，便會終止部署並將檢視和活動所做的變更回復。</span><span class="sxs-lookup"><span data-stu-id="52118-153">If bm.exe encounters an error during the deployment, the deployment is terminated and changes to the views and activities are rolled back.</span></span> <span data-ttu-id="52118-154">OLAP Cube 所做的變更則不會回復，因為 OLAP 不支援交易式部署。</span><span class="sxs-lookup"><span data-stu-id="52118-154">Changes to OLAP cubes are not rolled back since OLAP does not support transactional deployment.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="52118-155">在採用某地區設定的電腦上所建立的 BAM 定義，只能部署至同樣設定為該地區設定的電腦。</span><span class="sxs-lookup"><span data-stu-id="52118-155">BAM definitions created on a computer using one locale setting cannot be deployed to a computer configured with a different locale setting.</span></span> <span data-ttu-id="52118-156">例如，若在設定為英文地區設定的電腦上使用 Microsoft Excel 英文版產生 BAM 定義，就不能部署至採用日文地區設定的日文電腦。</span><span class="sxs-lookup"><span data-stu-id="52118-156">For example, a BAM definition generated using an English language version of Microsoft Excel on a computer configured with a EN locale setting cannot be deployed on a computer configured for Japanese using a JA locale setting.</span></span>  
  
 <span data-ttu-id="52118-157">**範例**</span><span class="sxs-lookup"><span data-stu-id="52118-157">**Examples**</span></span>  
  
```  
bm.exe deploy-all -DefinitionFile:MyDef.xml  
bm.exe deploy-all -DefinitionFile:MyWorkbook.xls -Server:machine1  
```  
  
## <a name="update-all-command"></a><span data-ttu-id="52118-158">update-all 命令</span><span class="sxs-lookup"><span data-stu-id="52118-158">update-all Command</span></span>  
 <span data-ttu-id="52118-159">**使用方式**</span><span class="sxs-lookup"><span data-stu-id="52118-159">**Usage**</span></span>  
  
 <span data-ttu-id="52118-160">**bm.exe 更新所有-DefinitionFile:\<def 檔\>[-Server:\<伺服器\>] [-Database:\<資料庫\>]**</span><span class="sxs-lookup"><span data-stu-id="52118-160">**bm.exe update-all -DefinitionFile:\<def file\>[ -Server:\<server\> ][ -Database:\<database\> ]**</span></span>  
  
 <span data-ttu-id="52118-161">**參數**</span><span class="sxs-lookup"><span data-stu-id="52118-161">**Parameters**</span></span>  
  
|<span data-ttu-id="52118-162">參數</span><span class="sxs-lookup"><span data-stu-id="52118-162">Parameter</span></span>|<span data-ttu-id="52118-163">Description</span><span class="sxs-lookup"><span data-stu-id="52118-163">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="52118-164">DefinitionFile:\<def 檔案\></span><span class="sxs-lookup"><span data-stu-id="52118-164">DefinitionFile:\<def file\></span></span>|<span data-ttu-id="52118-165">含有執行更新所需之定義的檔案所在路徑和名稱。</span><span class="sxs-lookup"><span data-stu-id="52118-165">The path and name of the file containing the definitions from which to perform the update.</span></span>|  
|<span data-ttu-id="52118-166">伺服器：\<伺服器\></span><span class="sxs-lookup"><span data-stu-id="52118-166">Server:\<server\></span></span>|<span data-ttu-id="52118-167">選擇性： 要部署定義更新的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="52118-167">Optional: The name of the server to which to deploy the definition updates.</span></span> <span data-ttu-id="52118-168">伺服器和執行 bm.exe 的電腦必須位在相同網域中。</span><span class="sxs-lookup"><span data-stu-id="52118-168">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="52118-169">如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。</span><span class="sxs-lookup"><span data-stu-id="52118-169">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="52118-170">資料庫：\<資料庫\></span><span class="sxs-lookup"><span data-stu-id="52118-170">Database:\<database\></span></span>|<span data-ttu-id="52118-171">選擇性： 要部署定義更新至資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="52118-171">Optional: The name of the database to which to deploy the definition updates.</span></span> <span data-ttu-id="52118-172">如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。</span><span class="sxs-lookup"><span data-stu-id="52118-172">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="52118-173">從 BAM 定義 XML 更新特定成品。</span><span class="sxs-lookup"><span data-stu-id="52118-173">Updates certain artifacts from the BAM definition XML.</span></span> <span data-ttu-id="52118-174">檔案可以是包含 BAM 定義 XML 的文字檔或 BAM Excel 活頁簿。</span><span class="sxs-lookup"><span data-stu-id="52118-174">The file can be a text file containing the BAM definition XML or a BAM Excel workbook.</span></span> <span data-ttu-id="52118-175">更新不會刪除目前定義檔中未描述的成品。</span><span class="sxs-lookup"><span data-stu-id="52118-175">The update does not delete artifacts that are not described in the current definition file.</span></span> <span data-ttu-id="52118-176">這可將新的檢查點加入活動，但不能從已部署的活動卸除檢查點。</span><span class="sxs-lookup"><span data-stu-id="52118-176">It can add new checkpoints to activities, but cannot drop checkpoints from deployed activities.</span></span> <span data-ttu-id="52118-177">更新不能重新命名檢查點，也不能變更檢查點屬性。</span><span class="sxs-lookup"><span data-stu-id="52118-177">The update can neither rename checkpoints nor change checkpoint properties.</span></span>  
  
 <span data-ttu-id="52118-178">一旦部署活動之後，可在活動上採取的動作便會受到限制。</span><span class="sxs-lookup"><span data-stu-id="52118-178">Once an activity has been deployed, the actions you can take on an activity become restricted.</span></span> <span data-ttu-id="52118-179">特別是，您不可以從活動刪除項目，除非您準備請系統管理員解除部署整個 BAM 活動和檢視集，然後再重新部署。</span><span class="sxs-lookup"><span data-stu-id="52118-179">Specifically, you cannot delete items from an activity unless you are prepared to have your administrator undeploy the entire BAM activity and view sets and then redeploy them.</span></span> <span data-ttu-id="52118-180">這樣可能會造成暫時看不見資料或資料遺失，除非系統管理員執行資料備份與還原。</span><span class="sxs-lookup"><span data-stu-id="52118-180">This can cause an interruption of visibility and loss of data unless the administrator does a backup and restore of the data.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="52118-181">您無法使用此命令在現有的檢視中加入新活動。</span><span class="sxs-lookup"><span data-stu-id="52118-181">You cannot use this command to add new activities to an existing view.</span></span> <span data-ttu-id="52118-182">若要在檢視中加入活動，您必須建立新檢視以包含新活動。</span><span class="sxs-lookup"><span data-stu-id="52118-182">To add a view to an activity you must create a new view that includes the new activity.</span></span> <span data-ttu-id="52118-183">然後您就可以解除部署舊檢視，但須注意的是 OLAP 資料歷程記錄將隨之遺失。</span><span class="sxs-lookup"><span data-stu-id="52118-183">You can then undeploy the old view, but be aware that you will then lose your OLAP data history.</span></span>  
  
 <span data-ttu-id="52118-184">**範例**</span><span class="sxs-lookup"><span data-stu-id="52118-184">**Examples**</span></span>  
  
```  
bm.exe update-all -DefinitionFile:MyDef.xml  
bm.exe update-all -DefinitionFile:MyWorkbook.xls -Server:machine1  
```  
  
## <a name="remove-all-command"></a><span data-ttu-id="52118-185">remove-all 命令</span><span class="sxs-lookup"><span data-stu-id="52118-185">remove-all Command</span></span>  
 <span data-ttu-id="52118-186">**使用方式**</span><span class="sxs-lookup"><span data-stu-id="52118-186">**Usage**</span></span>  
  
 <span data-ttu-id="52118-187">**bm.exe 移除 all DefinitionFile:\<def 檔\>[-Server:\<伺服器\>] [-Database:\<資料庫\>]**</span><span class="sxs-lookup"><span data-stu-id="52118-187">**bm.exe remove-all DefinitionFile:\<def file\> [ -Server:\<server\> ][ -Database:\<database\> ]**</span></span>  
  
 <span data-ttu-id="52118-188">**參數**</span><span class="sxs-lookup"><span data-stu-id="52118-188">**Parameters**</span></span>  
  
|<span data-ttu-id="52118-189">參數</span><span class="sxs-lookup"><span data-stu-id="52118-189">Parameter</span></span>|<span data-ttu-id="52118-190">Description</span><span class="sxs-lookup"><span data-stu-id="52118-190">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="52118-191">DefinitionFile:\<def 檔案\></span><span class="sxs-lookup"><span data-stu-id="52118-191">DefinitionFile:\<def file\></span></span>|<span data-ttu-id="52118-192">含有所要移除之定義的檔案所在路徑和名稱。</span><span class="sxs-lookup"><span data-stu-id="52118-192">The path and name of the file containing the definitions to remove.</span></span>|  
|<span data-ttu-id="52118-193">伺服器：\<伺服器\></span><span class="sxs-lookup"><span data-stu-id="52118-193">Server:\<server\></span></span>|<span data-ttu-id="52118-194">選擇性： 移除定義的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="52118-194">Optional: The name of the server from which the definitions will be removed.</span></span> <span data-ttu-id="52118-195">伺服器和執行 bm.exe 的電腦必須位在相同網域中。</span><span class="sxs-lookup"><span data-stu-id="52118-195">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="52118-196">如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。</span><span class="sxs-lookup"><span data-stu-id="52118-196">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="52118-197">資料庫：\<資料庫\></span><span class="sxs-lookup"><span data-stu-id="52118-197">Database:\<database\></span></span>|<span data-ttu-id="52118-198">選擇性： 移除定義的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="52118-198">Optional: The name of the database from which the definitions will be removed.</span></span> <span data-ttu-id="52118-199">如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。</span><span class="sxs-lookup"><span data-stu-id="52118-199">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="52118-200">移除 BAM 定義 XML 檔案指定的所有成品。</span><span class="sxs-lookup"><span data-stu-id="52118-200">Removes all artifacts specified in the BAM definition XML file.</span></span> <span data-ttu-id="52118-201">檔案可以是包含 BAM 定義 XML 的文字檔或 BAM Excel 活頁簿。</span><span class="sxs-lookup"><span data-stu-id="52118-201">The file can be a text file containing the BAM definition XML or a BAM Excel workbook.</span></span> <span data-ttu-id="52118-202">每個成品的定義都必須完全符合用於部署的原始定義。</span><span class="sxs-lookup"><span data-stu-id="52118-202">The definition for each artifact must exactly match the original definition that was used for deployment.</span></span>  
  
 <span data-ttu-id="52118-203">**範例**</span><span class="sxs-lookup"><span data-stu-id="52118-203">**Examples**</span></span>  
  
```  
bm.exe remove-all -DefinitionFile:MyDef.xml  
bm.exe remove-all -DefinitionFile:MyWorkbook.xls -Server:machine1  
```  
  
## <a name="update-livedataworkbook-command"></a><span data-ttu-id="52118-204">update-livedataworkbook 命令</span><span class="sxs-lookup"><span data-stu-id="52118-204">update-livedataworkbook Command</span></span>  
 <span data-ttu-id="52118-205">**使用方式**</span><span class="sxs-lookup"><span data-stu-id="52118-205">**Usage**</span></span>  
  
 <span data-ttu-id="52118-206">**bm.exe 更新 livedataworkbook-名稱：\<即時資料活頁簿檔案名稱\>[-Server:\<伺服器\>] [-Database:\<資料庫\>]**</span><span class="sxs-lookup"><span data-stu-id="52118-206">**bm.exe update-livedataworkbook -Name:\<livedata workbook file name\>[ -Server:\<server\> ][ -Database:\<database\> ]**</span></span>  
  
 <span data-ttu-id="52118-207">**參數**</span><span class="sxs-lookup"><span data-stu-id="52118-207">**Parameters**</span></span>  
  
|<span data-ttu-id="52118-208">參數</span><span class="sxs-lookup"><span data-stu-id="52118-208">Parameter</span></span>|<span data-ttu-id="52118-209">Description</span><span class="sxs-lookup"><span data-stu-id="52118-209">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="52118-210">名稱：\<即時資料活頁簿\></span><span class="sxs-lookup"><span data-stu-id="52118-210">Name:\<livedata workbook\></span></span>|<span data-ttu-id="52118-211">要更新的現有即時活頁簿的名稱。</span><span class="sxs-lookup"><span data-stu-id="52118-211">The name of the existing live workbook to update.</span></span>|  
|<span data-ttu-id="52118-212">伺服器：\<伺服器\></span><span class="sxs-lookup"><span data-stu-id="52118-212">Server:\<server\></span></span>|<span data-ttu-id="52118-213">選擇性： 在活頁簿所在的伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="52118-213">Optional: The name of the server on which the workbook resides.</span></span> <span data-ttu-id="52118-214">伺服器和執行 bm.exe 的電腦必須位在相同網域中。</span><span class="sxs-lookup"><span data-stu-id="52118-214">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="52118-215">如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。</span><span class="sxs-lookup"><span data-stu-id="52118-215">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="52118-216">資料庫：\<資料庫\></span><span class="sxs-lookup"><span data-stu-id="52118-216">Database:\<database\></span></span>|<span data-ttu-id="52118-217">選擇性： 在活頁簿所在資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="52118-217">Optional: The name of the database on which the workbook resides.</span></span> <span data-ttu-id="52118-218">如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。</span><span class="sxs-lookup"><span data-stu-id="52118-218">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="52118-219">更新指定的 BAM 即時資料活頁簿中的 BAM 主要匯入資料庫連線資訊。</span><span class="sxs-lookup"><span data-stu-id="52118-219">Updates the BAM Primary Import database connection information in the specified BAM live data workbook.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="52118-220">在設定新的連線字串時，必須重新啟動 TDDS 服務以確保服務能辨識所做的變更。</span><span class="sxs-lookup"><span data-stu-id="52118-220">When configuring new connection string, you must restart the TDDS service to ensure that the service recognizes the change.</span></span> <span data-ttu-id="52118-221">如需 TDDS 服務的詳細資訊，請參閱[BAM 事件匯流排服務預存程序](../core/bam-event-bus-service-stored-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="52118-221">For more information on the TDDS service, see [BAM Event Bus Service Stored Procedures](../core/bam-event-bus-service-stored-procedures.md).</span></span>  
  
 <span data-ttu-id="52118-222">**範例**</span><span class="sxs-lookup"><span data-stu-id="52118-222">**Examples**</span></span>  
  
```  
bm.exe update-livedataworkbook -Name:SalesManager_Live.xls  
bm.exe update-livedataworkbook -Name:SalesManager_Live.xls -Server:SalesSrv  
```  
  
## <a name="regenerate-livedataworkbook-command"></a><span data-ttu-id="52118-223">regenerate-livedataworkbook 命令</span><span class="sxs-lookup"><span data-stu-id="52118-223">regenerate-livedataworkbook Command</span></span>  
 <span data-ttu-id="52118-224">**使用方式**</span><span class="sxs-lookup"><span data-stu-id="52118-224">**Usage**</span></span>  
  
 <span data-ttu-id="52118-225">**bm.exe regenerate livedataworkbook WorkbookName:\<即時資料活頁簿檔案名稱\>[-Server:\<伺服器\>] [-Database:\<資料庫\>]**</span><span class="sxs-lookup"><span data-stu-id="52118-225">**bm.exe regenerate-livedataworkbook -WorkbookName:\<livedata workbook file name\>[ -Server:\<server\> ][ -Database:\<database\> ]**</span></span>  
  
 <span data-ttu-id="52118-226">**參數**</span><span class="sxs-lookup"><span data-stu-id="52118-226">**Parameters**</span></span>  
  
|<span data-ttu-id="52118-227">參數</span><span class="sxs-lookup"><span data-stu-id="52118-227">Parameter</span></span>|<span data-ttu-id="52118-228">Description</span><span class="sxs-lookup"><span data-stu-id="52118-228">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="52118-229">WorkbookName:\<即時資料活頁簿檔案名稱\></span><span class="sxs-lookup"><span data-stu-id="52118-229">WorkbookName:\<livedata workbook file name\></span></span>|<span data-ttu-id="52118-230">要更新的活頁簿的名稱。</span><span class="sxs-lookup"><span data-stu-id="52118-230">The name of the workbook to update.</span></span>|  
|<span data-ttu-id="52118-231">伺服器：\<伺服器\></span><span class="sxs-lookup"><span data-stu-id="52118-231">Server:\<server\></span></span>|<span data-ttu-id="52118-232">選擇性： 在活頁簿所在的伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="52118-232">Optional: The name of the server on which the workbook resides.</span></span> <span data-ttu-id="52118-233">伺服器和執行 bm.exe 的電腦必須位在相同網域中。</span><span class="sxs-lookup"><span data-stu-id="52118-233">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="52118-234">如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。</span><span class="sxs-lookup"><span data-stu-id="52118-234">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="52118-235">資料庫：\<資料庫\></span><span class="sxs-lookup"><span data-stu-id="52118-235">Database:\<database\></span></span>|<span data-ttu-id="52118-236">選擇性： 在活頁簿所在資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="52118-236">Optional: The name of the database on which the workbook resides.</span></span> <span data-ttu-id="52118-237">如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。</span><span class="sxs-lookup"><span data-stu-id="52118-237">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="52118-238">產生 BAM 即時資料活頁簿但不部署活頁簿。</span><span class="sxs-lookup"><span data-stu-id="52118-238">Generates a BAM live data workbook but does not deploy the workbook.</span></span>  
  
 <span data-ttu-id="52118-239">範例</span><span class="sxs-lookup"><span data-stu-id="52118-239">Examples</span></span>  
  
```  
bm.exe regenerate-livedataworkbook -WorkbookName:SalesManager_Live.xls  
bm.exe regenerate-livedataworkbook -WorkbookName:SM_Live.xls -Server:S1  
```  
  
## <a name="see-also"></a><span data-ttu-id="52118-240">請參閱</span><span class="sxs-lookup"><span data-stu-id="52118-240">See Also</span></span>  
 [<span data-ttu-id="52118-241">BAM 管理公用程式</span><span class="sxs-lookup"><span data-stu-id="52118-241">BAM Management Utility</span></span>](../core/bam-management-utility.md)