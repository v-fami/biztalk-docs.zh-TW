---
title: "活動管理命令 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 34db54f3-4116-49de-880b-c9891a38d2e7
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 18caccaf5207b5a63d0272c5d9e0277270c3e04c
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="activity-management-commands"></a><span data-ttu-id="3376b-102">活動管理命令</span><span class="sxs-lookup"><span data-stu-id="3376b-102">Activity Management Commands</span></span>
<span data-ttu-id="3376b-103">BAM 管理公用程式活動管理命令可讓您使用已部署的活動。</span><span class="sxs-lookup"><span data-stu-id="3376b-103">The BAM Management utility activity management commands allow you to work with deployed activities.</span></span>  
  
-   <span data-ttu-id="3376b-104">取得活動： 取得已部署的活動清單。</span><span class="sxs-lookup"><span data-stu-id="3376b-104">get-activities: Gets a list of deployed activities.</span></span>  
  
-   <span data-ttu-id="3376b-105">移除活動： 將活動中移除。</span><span class="sxs-lookup"><span data-stu-id="3376b-105">remove-activity: Removes an activity.</span></span>  
  
-   <span data-ttu-id="3376b-106">get activitywindow： 取得活動的持續時間。</span><span class="sxs-lookup"><span data-stu-id="3376b-106">get-activitywindow: Gets the duration for an activity.</span></span>  
  
-   <span data-ttu-id="3376b-107">設定 activitywindow： 設定活動的活動持續時間。</span><span class="sxs-lookup"><span data-stu-id="3376b-107">set-activitywindow: Sets the activity duration for an activity.</span></span>  
  
-   <span data-ttu-id="3376b-108">取得索引： 取得索引的清單。</span><span class="sxs-lookup"><span data-stu-id="3376b-108">get-index: Gets the list of indexes.</span></span>  
  
-   <span data-ttu-id="3376b-109">建立索引： 建立新的索引。</span><span class="sxs-lookup"><span data-stu-id="3376b-109">create-index: Creates a new index.</span></span>  
  
-   <span data-ttu-id="3376b-110">刪除索引： 刪除索引。</span><span class="sxs-lookup"><span data-stu-id="3376b-110">delete-index: Deletes an index.</span></span>  
  
-   <span data-ttu-id="3376b-111">get 封存： 取得封存 」 活動的行為。</span><span class="sxs-lookup"><span data-stu-id="3376b-111">get-archive: Gets the behavior of archived activity.</span></span>  
  
-   <span data-ttu-id="3376b-112">設定封存： 設定封存 」 活動的行為。</span><span class="sxs-lookup"><span data-stu-id="3376b-112">set-archive: Sets the behavior of archived activity.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3376b-113">您可以藉由啟用任何 BAM 公用程式命令的追蹤**-追蹤： 在 &#124; 關閉**切換參數。</span><span class="sxs-lookup"><span data-stu-id="3376b-113">You can enable tracing on any BAM utility command by including the **-Trace:on&#124;off** parameter switch.</span></span> <span data-ttu-id="3376b-114">使用追蹤參數會覆寫組態檔中的追蹤設定。</span><span class="sxs-lookup"><span data-stu-id="3376b-114">Using the Trace switch overrides the tracing settings in the configuration file.</span></span> <span data-ttu-id="3376b-115">此參數可以搭配任何一般 BAM 命令使用。</span><span class="sxs-lookup"><span data-stu-id="3376b-115">The switch can be used in conjunction with any normal BAM command.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3376b-116">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="3376b-116">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="get-activities-command"></a><span data-ttu-id="3376b-117">get-activities 命令</span><span class="sxs-lookup"><span data-stu-id="3376b-117">get-activities Command</span></span>  
 <span data-ttu-id="3376b-118">**使用方式**</span><span class="sxs-lookup"><span data-stu-id="3376b-118">**Usage**</span></span>  
  
 <span data-ttu-id="3376b-119">**bm.exe get 活動 [-檢視：\<檢視名稱\>] [-Server:\<伺服器\>] [-Database:\<資料庫\>]**</span><span class="sxs-lookup"><span data-stu-id="3376b-119">**bm.exe get-activities [ -View:\<view name\> ][ -Server:\<server\> ][ -Database:\<database\> ]**</span></span>  
  
 <span data-ttu-id="3376b-120">**參數**</span><span class="sxs-lookup"><span data-stu-id="3376b-120">**Parameters**</span></span>  
  
|<span data-ttu-id="3376b-121">參數</span><span class="sxs-lookup"><span data-stu-id="3376b-121">Parameter</span></span>|<span data-ttu-id="3376b-122">Description</span><span class="sxs-lookup"><span data-stu-id="3376b-122">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3376b-123">名稱：\<活動名稱\></span><span class="sxs-lookup"><span data-stu-id="3376b-123">Name:\<activity name\></span></span>|<span data-ttu-id="3376b-124">要移除的活動名稱。</span><span class="sxs-lookup"><span data-stu-id="3376b-124">The name of the activity to remove.</span></span>|  
|<span data-ttu-id="3376b-125">伺服器：\<伺服器\></span><span class="sxs-lookup"><span data-stu-id="3376b-125">Server:\<server\></span></span>|<span data-ttu-id="3376b-126">選擇性： 要從其中取得活動清單的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="3376b-126">Optional: The name of the server from which to get the list of activities.</span></span> <span data-ttu-id="3376b-127">伺服器和執行 bm.exe 的電腦必須位在相同網域中。</span><span class="sxs-lookup"><span data-stu-id="3376b-127">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="3376b-128">如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。</span><span class="sxs-lookup"><span data-stu-id="3376b-128">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="3376b-129">資料庫：\<資料庫\></span><span class="sxs-lookup"><span data-stu-id="3376b-129">Database:\<database\></span></span>|<span data-ttu-id="3376b-130">選擇性： 要從中取得活動清單的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="3376b-130">Optional: The name of the database from which to get the list of activities.</span></span> <span data-ttu-id="3376b-131">如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。</span><span class="sxs-lookup"><span data-stu-id="3376b-131">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="3376b-132">列出在執行此命令之電腦上部署的活動。</span><span class="sxs-lookup"><span data-stu-id="3376b-132">Lists the activities deployed on the computer on which the command is executed.</span></span>  
  
 <span data-ttu-id="3376b-133">**範例**</span><span class="sxs-lookup"><span data-stu-id="3376b-133">**Examples**</span></span>  
  
```  
bm.exe get-activities -View:SalesManagerView  
bm.exe get-activities -Server:MyServer -Database:MyPrimaryImport  
```  
  
## <a name="remove-activity-command"></a><span data-ttu-id="3376b-134">remove-activity 命令</span><span class="sxs-lookup"><span data-stu-id="3376b-134">remove-activity Command</span></span>  
 <span data-ttu-id="3376b-135">**使用方式**</span><span class="sxs-lookup"><span data-stu-id="3376b-135">**Usage**</span></span>  
  
 <span data-ttu-id="3376b-136">**bm.exe 移除活動的名稱：\<活動名稱\>[-Server:\<伺服器\>] [-Database:\<資料庫\>]**</span><span class="sxs-lookup"><span data-stu-id="3376b-136">**bm.exe remove-activity -Name:\<activity name\>[ -Server:\<server\> ][ -Database:\<database\> ]**</span></span>  
  
 <span data-ttu-id="3376b-137">**參數**</span><span class="sxs-lookup"><span data-stu-id="3376b-137">**Parameters**</span></span>  
  
|<span data-ttu-id="3376b-138">參數</span><span class="sxs-lookup"><span data-stu-id="3376b-138">Parameter</span></span>|<span data-ttu-id="3376b-139">Description</span><span class="sxs-lookup"><span data-stu-id="3376b-139">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3376b-140">名稱：\<活動名稱\></span><span class="sxs-lookup"><span data-stu-id="3376b-140">Name:\<activity name\></span></span>|<span data-ttu-id="3376b-141">要移除的活動名稱。</span><span class="sxs-lookup"><span data-stu-id="3376b-141">The name of the activity to remove.</span></span>|  
|<span data-ttu-id="3376b-142">伺服器：\<伺服器\></span><span class="sxs-lookup"><span data-stu-id="3376b-142">Server:\<server\></span></span>|<span data-ttu-id="3376b-143">選擇性： 要移除之活動的來源伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="3376b-143">Optional: The name of the server from which to remove the activity.</span></span> <span data-ttu-id="3376b-144">伺服器和執行 bm.exe 的電腦必須位在相同網域中。</span><span class="sxs-lookup"><span data-stu-id="3376b-144">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="3376b-145">如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。</span><span class="sxs-lookup"><span data-stu-id="3376b-145">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="3376b-146">資料庫：\<資料庫\></span><span class="sxs-lookup"><span data-stu-id="3376b-146">Database:\<database\></span></span>|<span data-ttu-id="3376b-147">選擇性： 要從中移除活動的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="3376b-147">Optional: The name of the database from which to remove the activity.</span></span> <span data-ttu-id="3376b-148">如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。</span><span class="sxs-lookup"><span data-stu-id="3376b-148">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="3376b-149">從 BAM 主要匯入資料庫移除指定的活動。</span><span class="sxs-lookup"><span data-stu-id="3376b-149">Removes the specified activity from the BAM Primary Import database.</span></span> <span data-ttu-id="3376b-150">如果活動有相依檢視，命令將會失敗並報告錯誤。</span><span class="sxs-lookup"><span data-stu-id="3376b-150">If the activity has dependent views, the command will fail and report an error.</span></span> <span data-ttu-id="3376b-151">請先使用 remove-view 命令移除所有相依檢視，然後再度執行 remove-activity 命令。</span><span class="sxs-lookup"><span data-stu-id="3376b-151">Use the remove-view command to remove all the dependent views and execute the remove-activity command again.</span></span>  
  
 <span data-ttu-id="3376b-152">**範例**</span><span class="sxs-lookup"><span data-stu-id="3376b-152">**Examples**</span></span>  
  
```  
bm.exe remove-activity -Name:PurchaseOrder  
bm.exe remove-activity -Name:PO -Server:MyServer -Database:MyPrimaryImport  
```  
  
## <a name="get-activitywindow-command"></a><span data-ttu-id="3376b-153">get-activitywindow 命令</span><span class="sxs-lookup"><span data-stu-id="3376b-153">get-activitywindow Command</span></span>  
 <span data-ttu-id="3376b-154">**使用方式**</span><span class="sxs-lookup"><span data-stu-id="3376b-154">**Usage**</span></span>  
  
 <span data-ttu-id="3376b-155">**bm.exe get activitywindow-活動：\<活動名稱\>[-Server:\<伺服器\>] [-Database:\<資料庫\>]**</span><span class="sxs-lookup"><span data-stu-id="3376b-155">**bm.exe get-activitywindow -Activity:\<activity name\>[ -Server:\<server\> ][ -Database:\<database\> ]**</span></span>  
  
 <span data-ttu-id="3376b-156">**參數**</span><span class="sxs-lookup"><span data-stu-id="3376b-156">**Parameters**</span></span>  
  
|<span data-ttu-id="3376b-157">參數</span><span class="sxs-lookup"><span data-stu-id="3376b-157">Parameter</span></span>|<span data-ttu-id="3376b-158">Description</span><span class="sxs-lookup"><span data-stu-id="3376b-158">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3376b-159">活動：\<活動名稱\></span><span class="sxs-lookup"><span data-stu-id="3376b-159">Activity:\<activity name\></span></span>|<span data-ttu-id="3376b-160">活動的名稱。</span><span class="sxs-lookup"><span data-stu-id="3376b-160">The name of the .activity.</span></span>|  
|<span data-ttu-id="3376b-161">伺服器：\<伺服器\></span><span class="sxs-lookup"><span data-stu-id="3376b-161">Server:\<server\></span></span>|<span data-ttu-id="3376b-162">選擇性： 活動所在的伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="3376b-162">Optional: The name of the server on which the activity resides.</span></span> <span data-ttu-id="3376b-163">伺服器和執行 bm.exe 的電腦必須位在相同網域中。</span><span class="sxs-lookup"><span data-stu-id="3376b-163">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="3376b-164">如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。</span><span class="sxs-lookup"><span data-stu-id="3376b-164">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="3376b-165">資料庫：\<資料庫\></span><span class="sxs-lookup"><span data-stu-id="3376b-165">Database:\<database\></span></span>|<span data-ttu-id="3376b-166">選擇性： 活動所在資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="3376b-166">Optional: The name of the database on which the activity resides.</span></span> <span data-ttu-id="3376b-167">如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。</span><span class="sxs-lookup"><span data-stu-id="3376b-167">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="3376b-168">顯示指定活動的持續時間。</span><span class="sxs-lookup"><span data-stu-id="3376b-168">Displays the duration for the specified activity.</span></span> <span data-ttu-id="3376b-169">這個命令會傳回持續時間的長度以及測量持續時間所用的單位。</span><span class="sxs-lookup"><span data-stu-id="3376b-169">The command returns the length of the duration and the units by which the duration is measured.</span></span>  
  
 <span data-ttu-id="3376b-170">**範例**</span><span class="sxs-lookup"><span data-stu-id="3376b-170">**Examples**</span></span>  
  
```  
bm.exe get-activitywindow -Activity:PurchaseOrder  
bm.exe get-activitywindow -Activity:PO -Server:Ship -Database:ShipDatabase  
```  
  
## <a name="set-activitywindow-command"></a><span data-ttu-id="3376b-171">set-activitywindow 命令</span><span class="sxs-lookup"><span data-stu-id="3376b-171">set-activitywindow Command</span></span>  
 <span data-ttu-id="3376b-172">**使用方式**</span><span class="sxs-lookup"><span data-stu-id="3376b-172">**Usage**</span></span>  
  
 <span data-ttu-id="3376b-173">**bm.exe 組 activitywindow-活動：\<活動名稱\>-TimeLength:\<整數\>-TimeUnit： 月份 &#124; 天 &#124;小時 &#124;分鐘 [-Server:\<伺服器\>] [-Database:\<資料庫\>]**</span><span class="sxs-lookup"><span data-stu-id="3376b-173">**bm.exe set-activitywindow -Activity:\<activity name\> -TimeLength:\<integer number\> -TimeUnit:Month&#124;Day&#124;Hour&#124;Minute[ -Server:\<server\> ][ -Database:\<database\> ]**</span></span>  
  
 <span data-ttu-id="3376b-174">**參數**</span><span class="sxs-lookup"><span data-stu-id="3376b-174">**Parameters**</span></span>  
  
|<span data-ttu-id="3376b-175">參數</span><span class="sxs-lookup"><span data-stu-id="3376b-175">Parameter</span></span>|<span data-ttu-id="3376b-176">Description</span><span class="sxs-lookup"><span data-stu-id="3376b-176">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3376b-177">活動：\<活動名稱\></span><span class="sxs-lookup"><span data-stu-id="3376b-177">Activity:\<activity name\></span></span>|<span data-ttu-id="3376b-178">活動的名稱。</span><span class="sxs-lookup"><span data-stu-id="3376b-178">The name of the activity.</span></span>|  
|<span data-ttu-id="3376b-179">TimeLength:\<整數數字\></span><span class="sxs-lookup"><span data-stu-id="3376b-179">TimeLength:\<integer number\></span></span>|<span data-ttu-id="3376b-180">活動的持續時間。</span><span class="sxs-lookup"><span data-stu-id="3376b-180">The duration for the activity.</span></span>|  
|<span data-ttu-id="3376b-181">TimeUnit:Month &#124; 天 &#124;小時 &#124;分鐘</span><span class="sxs-lookup"><span data-stu-id="3376b-181">TimeUnit:Month&#124;Day&#124;Hour&#124;Minute</span></span>|<span data-ttu-id="3376b-182">持續時間的計量單位。</span><span class="sxs-lookup"><span data-stu-id="3376b-182">The unit measure for the duration.</span></span>|  
|<span data-ttu-id="3376b-183">伺服器：\<伺服器\></span><span class="sxs-lookup"><span data-stu-id="3376b-183">Server:\<server\></span></span>|<span data-ttu-id="3376b-184">選擇性： 活動所在的伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="3376b-184">Optional: The name of the server on which the activity resides.</span></span> <span data-ttu-id="3376b-185">伺服器和執行 bm.exe 的電腦必須位在相同網域中。</span><span class="sxs-lookup"><span data-stu-id="3376b-185">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="3376b-186">如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。</span><span class="sxs-lookup"><span data-stu-id="3376b-186">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="3376b-187">資料庫：\<資料庫\></span><span class="sxs-lookup"><span data-stu-id="3376b-187">Database:\<database\></span></span>|<span data-ttu-id="3376b-188">選擇性： 活動所在資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="3376b-188">Optional: The name of the database on which the activity resides.</span></span> <span data-ttu-id="3376b-189">如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。</span><span class="sxs-lookup"><span data-stu-id="3376b-189">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="3376b-190">設定指定活動的持續時間。</span><span class="sxs-lookup"><span data-stu-id="3376b-190">Sets the duration for the specified activity.</span></span>  
  
 <span data-ttu-id="3376b-191">**範例**</span><span class="sxs-lookup"><span data-stu-id="3376b-191">**Examples**</span></span>  
  
```  
bm.exe set-activitywindow -Activity:PurchaseOrder -TimeLength:6 -TimeUnit:Day  
bm.exe set-activitywindow -Activity:PurchaseOrder -TimeLength:1 -TimeUnit:Month  
```  
  
## <a name="get-index-command"></a><span data-ttu-id="3376b-192">get-index 命令</span><span class="sxs-lookup"><span data-stu-id="3376b-192">get-index Command</span></span>  
 <span data-ttu-id="3376b-193">**使用方式**</span><span class="sxs-lookup"><span data-stu-id="3376b-193">**Usage**</span></span>  
  
 <span data-ttu-id="3376b-194">**bm.exe get 索引的活動：\<活動名稱\>[-Server:\<伺服器\>] [-Database:\<資料庫\>]**</span><span class="sxs-lookup"><span data-stu-id="3376b-194">**bm.exe get-index -Activity:\<activity name\>[ -Server:\<server\> ][ -Database:\<database\> ]**</span></span>  
  
 <span data-ttu-id="3376b-195">**參數**</span><span class="sxs-lookup"><span data-stu-id="3376b-195">**Parameters**</span></span>  
  
|<span data-ttu-id="3376b-196">參數</span><span class="sxs-lookup"><span data-stu-id="3376b-196">Parameter</span></span>|<span data-ttu-id="3376b-197">Description</span><span class="sxs-lookup"><span data-stu-id="3376b-197">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3376b-198">活動：\<活動名稱\></span><span class="sxs-lookup"><span data-stu-id="3376b-198">Activity:\<activity name\></span></span>|<span data-ttu-id="3376b-199">活動的名稱。</span><span class="sxs-lookup"><span data-stu-id="3376b-199">The name of the activity.</span></span>|  
|<span data-ttu-id="3376b-200">伺服器：\<伺服器\></span><span class="sxs-lookup"><span data-stu-id="3376b-200">Server:\<server\></span></span>|<span data-ttu-id="3376b-201">選擇性： 活動所在的伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="3376b-201">Optional: The name of the server on which the activity resides.</span></span> <span data-ttu-id="3376b-202">伺服器和執行 bm.exe 的電腦必須位在相同網域中。</span><span class="sxs-lookup"><span data-stu-id="3376b-202">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="3376b-203">如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。</span><span class="sxs-lookup"><span data-stu-id="3376b-203">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="3376b-204">資料庫：\<資料庫\></span><span class="sxs-lookup"><span data-stu-id="3376b-204">Database:\<database\></span></span>|<span data-ttu-id="3376b-205">選擇性： 活動所在資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="3376b-205">Optional: The name of the database on which the activity resides.</span></span> <span data-ttu-id="3376b-206">如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。</span><span class="sxs-lookup"><span data-stu-id="3376b-206">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="3376b-207">列出已針對指定之活動建立的所有索引。</span><span class="sxs-lookup"><span data-stu-id="3376b-207">Lists all the indexes that have been created for the specified activity.</span></span>  
  
 <span data-ttu-id="3376b-208">**範例**</span><span class="sxs-lookup"><span data-stu-id="3376b-208">**Examples**</span></span>  
  
```  
bm.exe get-index -Activity:PurchaseOrder  
bm.exe get-index -Activity:PurchaseOrder -Server:Ship -Database:ShipDatabase  
```  
  
## <a name="create-index-command"></a><span data-ttu-id="3376b-209">create-index 命令</span><span class="sxs-lookup"><span data-stu-id="3376b-209">create-index Command</span></span>  
 <span data-ttu-id="3376b-210">**使用方式**</span><span class="sxs-lookup"><span data-stu-id="3376b-210">**Usage**</span></span>  
  
 <span data-ttu-id="3376b-211">**bm.exe 建立-IndexName:\<索引名稱\>-活動：\<活動名稱\>-檢查點：\<checkpoint1\>[，\<checkpoint2\>...][-Server:\<伺服器\>] [-Database:\<資料庫\>]**</span><span class="sxs-lookup"><span data-stu-id="3376b-211">**bm.exe create-index -IndexName:\<index name\> -Activity:\<activity name\> -Checkpoint:\<checkpoint1\>[,\<checkpoint2\>...][ -Server:\<server\> ][ -Database:\<database\> ]**</span></span>  
  
 <span data-ttu-id="3376b-212">**參數**</span><span class="sxs-lookup"><span data-stu-id="3376b-212">**Parameters**</span></span>  
  
|<span data-ttu-id="3376b-213">參數</span><span class="sxs-lookup"><span data-stu-id="3376b-213">Parameter</span></span>|<span data-ttu-id="3376b-214">Description</span><span class="sxs-lookup"><span data-stu-id="3376b-214">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3376b-215">IndexName:\<索引名稱\></span><span class="sxs-lookup"><span data-stu-id="3376b-215">IndexName:\<index name\></span></span>|<span data-ttu-id="3376b-216">新索引的名稱。</span><span class="sxs-lookup"><span data-stu-id="3376b-216">The name of the new index.</span></span>|  
|<span data-ttu-id="3376b-217">活動：\<活動名稱\></span><span class="sxs-lookup"><span data-stu-id="3376b-217">Activity:\<activity name\></span></span>|<span data-ttu-id="3376b-218">建立索引的活動名稱。</span><span class="sxs-lookup"><span data-stu-id="3376b-218">The name of the activity for which the index is created.</span></span>|  
|<span data-ttu-id="3376b-219">檢查點：\<checkpoint1\>[，\<checkpoint2\>...]</span><span class="sxs-lookup"><span data-stu-id="3376b-219">Checkpoint:\<checkpoint1\>[,\<checkpoint2\>...]</span></span>|<span data-ttu-id="3376b-220">索引的檢查點清單 (以逗號分隔)。</span><span class="sxs-lookup"><span data-stu-id="3376b-220">A comma-delimited list of checkpoints for the index.</span></span>|  
|<span data-ttu-id="3376b-221">伺服器：\<伺服器\></span><span class="sxs-lookup"><span data-stu-id="3376b-221">Server:\<server\></span></span>|<span data-ttu-id="3376b-222">選擇性： 活動所在的伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="3376b-222">Optional: The name of the server on which the activity resides.</span></span> <span data-ttu-id="3376b-223">伺服器和執行 bm.exe 的電腦必須位在相同網域中。</span><span class="sxs-lookup"><span data-stu-id="3376b-223">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="3376b-224">如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。</span><span class="sxs-lookup"><span data-stu-id="3376b-224">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="3376b-225">資料庫：\<資料庫\></span><span class="sxs-lookup"><span data-stu-id="3376b-225">Database:\<database\></span></span>|<span data-ttu-id="3376b-226">選擇性： 活動所在資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="3376b-226">Optional: The name of the database on which the activity resides.</span></span> <span data-ttu-id="3376b-227">如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。</span><span class="sxs-lookup"><span data-stu-id="3376b-227">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="3376b-228">使用指定的檢查點，為指定的活動建立索引。</span><span class="sxs-lookup"><span data-stu-id="3376b-228">Creates an index for the specified activity using the specified checkpoints.</span></span>  
  
 <span data-ttu-id="3376b-229">**範例**</span><span class="sxs-lookup"><span data-stu-id="3376b-229">**Examples**</span></span>  
  
```  
bm.exe create-index -IndexName:Idx1 -Activity:PO -Checkpoint:State,City  
bm.exe create-index -IndexName:Idx2 -Activity:PO -Checkpoint:Amount -Server:S1  
```  
  
## <a name="delete-index-command"></a><span data-ttu-id="3376b-230">delete-index 命令</span><span class="sxs-lookup"><span data-stu-id="3376b-230">delete-index Command</span></span>  
 <span data-ttu-id="3376b-231">**使用方式**</span><span class="sxs-lookup"><span data-stu-id="3376b-231">**Usage**</span></span>  
  
 <span data-ttu-id="3376b-232">**bm.exe delete-IndexName:\<索引名稱\>-活動：\<活動名稱\>[-Server:\<伺服器\>] [-Database:\<資料庫\>]**</span><span class="sxs-lookup"><span data-stu-id="3376b-232">**bm.exe delete-index -IndexName:\<index name\> -Activity:\<activity name\>[ -Server:\<server\> ][ -Database:\<database\> ]**</span></span>  
  
 <span data-ttu-id="3376b-233">**參數**</span><span class="sxs-lookup"><span data-stu-id="3376b-233">**Parameters**</span></span>  
  
|<span data-ttu-id="3376b-234">參數</span><span class="sxs-lookup"><span data-stu-id="3376b-234">Parameter</span></span>|<span data-ttu-id="3376b-235">Description</span><span class="sxs-lookup"><span data-stu-id="3376b-235">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3376b-236">IndexName:\<索引名稱\></span><span class="sxs-lookup"><span data-stu-id="3376b-236">IndexName:\<index name\></span></span>|<span data-ttu-id="3376b-237">要刪除之索引的名稱。</span><span class="sxs-lookup"><span data-stu-id="3376b-237">The name of the index to delete.</span></span>|  
|<span data-ttu-id="3376b-238">活動：\<活動名稱\></span><span class="sxs-lookup"><span data-stu-id="3376b-238">Activity:\<activity name\></span></span>|<span data-ttu-id="3376b-239">要刪除索引之活動的名稱。</span><span class="sxs-lookup"><span data-stu-id="3376b-239">The name of the activity for which the index is deleted.</span></span>|  
|<span data-ttu-id="3376b-240">伺服器：\<伺服器\></span><span class="sxs-lookup"><span data-stu-id="3376b-240">Server:\<server\></span></span>|<span data-ttu-id="3376b-241">選擇性： 活動所在的伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="3376b-241">Optional: The name of the server on which the activity resides.</span></span> <span data-ttu-id="3376b-242">伺服器和執行 bm.exe 的電腦必須位在相同網域中。</span><span class="sxs-lookup"><span data-stu-id="3376b-242">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="3376b-243">如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。</span><span class="sxs-lookup"><span data-stu-id="3376b-243">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="3376b-244">資料庫：\<資料庫\></span><span class="sxs-lookup"><span data-stu-id="3376b-244">Database:\<database\></span></span>|<span data-ttu-id="3376b-245">選擇性： 活動所在資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="3376b-245">Optional: The name of the database on which the activity resides.</span></span> <span data-ttu-id="3376b-246">如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。</span><span class="sxs-lookup"><span data-stu-id="3376b-246">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="3376b-247">從指定的活動刪除具有指定名稱的指定索引。</span><span class="sxs-lookup"><span data-stu-id="3376b-247">Deletes the specified index with the given name from the specified activity.</span></span>  
  
 <span data-ttu-id="3376b-248">**範例**</span><span class="sxs-lookup"><span data-stu-id="3376b-248">**Examples**</span></span>  
  
```  
bm.exe delete-index -IndexName:Idx1 -Activity:PO  
bm.exe delete-index -IndexName:Idx2 -Activity:PO -Server:S1 -Database:BamPI1  
```  
  
## <a name="set-archive-command"></a><span data-ttu-id="3376b-249">set-archive 命令</span><span class="sxs-lookup"><span data-stu-id="3376b-249">set-archive Command</span></span>  
 <span data-ttu-id="3376b-250">**使用方式**</span><span class="sxs-lookup"><span data-stu-id="3376b-250">**Usage**</span></span>  
  
 <span data-ttu-id="3376b-251">**bm.exe get 封存-活動：\<活動\>[-Server:\<伺服器\>] [-Database:\<資料庫\>]**</span><span class="sxs-lookup"><span data-stu-id="3376b-251">**bm.exe get-archive -Activity:\<activity\> [-Server:\<server\>] [-Database:\<database\>]**</span></span>  
  
 <span data-ttu-id="3376b-252">**參數**</span><span class="sxs-lookup"><span data-stu-id="3376b-252">**Parameters**</span></span>  
  
|<span data-ttu-id="3376b-253">參數</span><span class="sxs-lookup"><span data-stu-id="3376b-253">Parameter</span></span>|<span data-ttu-id="3376b-254">Description</span><span class="sxs-lookup"><span data-stu-id="3376b-254">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3376b-255">活動：\<活動名稱\></span><span class="sxs-lookup"><span data-stu-id="3376b-255">Activity:\<activity name\></span></span>|<span data-ttu-id="3376b-256">活動的行為是要顯示的名稱。</span><span class="sxs-lookup"><span data-stu-id="3376b-256">The name of the activity for which the behavior is to be displayed.</span></span>|  
|<span data-ttu-id="3376b-257">伺服器：\<伺服器\></span><span class="sxs-lookup"><span data-stu-id="3376b-257">Server:\<server\></span></span>|<span data-ttu-id="3376b-258">選擇性： 活動所在的伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="3376b-258">Optional: The name of the server on which the activity resides.</span></span> <span data-ttu-id="3376b-259">伺服器和執行 bm.exe 的電腦必須位在相同網域中。</span><span class="sxs-lookup"><span data-stu-id="3376b-259">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="3376b-260">如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。</span><span class="sxs-lookup"><span data-stu-id="3376b-260">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="3376b-261">資料庫：\<資料庫\></span><span class="sxs-lookup"><span data-stu-id="3376b-261">Database:\<database\></span></span>|<span data-ttu-id="3376b-262">選擇性： 活動所在資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="3376b-262">Optional: The name of the database on which the activity resides.</span></span> <span data-ttu-id="3376b-263">如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。</span><span class="sxs-lookup"><span data-stu-id="3376b-263">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="3376b-264">取得指定的活動，封存套件的行為是否封存的封裝將會封存 orpurge 活動資料。</span><span class="sxs-lookup"><span data-stu-id="3376b-264">Gets the behavior of the archiving package for the specified activity, whether the archiving package will archive orpurge activity data.</span></span>  
  
 <span data-ttu-id="3376b-265">**範例**</span><span class="sxs-lookup"><span data-stu-id="3376b-265">**Examples**</span></span>  
  
```  
bm.exe get-archive -Activity:PurchaseOrder  
```  
  
## <a name="set-archive-command"></a><span data-ttu-id="3376b-266">set-archive 命令</span><span class="sxs-lookup"><span data-stu-id="3376b-266">set-archive Command</span></span>  
 <span data-ttu-id="3376b-267">**使用方式**</span><span class="sxs-lookup"><span data-stu-id="3376b-267">**Usage**</span></span>  
  
 <span data-ttu-id="3376b-268">**bm.exe 組封存-活動：\<活動\>-ShouldArchive:，則為 True [-Server:\<伺服器\>] [-Database:\<資料庫\>]**</span><span class="sxs-lookup"><span data-stu-id="3376b-268">**bm.exe set-archive -Activity:\<activity\> -ShouldArchive:True [-Server:\<server\>] [-Database:\<database\>]**</span></span>  
  
 <span data-ttu-id="3376b-269">**參數**</span><span class="sxs-lookup"><span data-stu-id="3376b-269">**Parameters**</span></span>  
  
|<span data-ttu-id="3376b-270">參數</span><span class="sxs-lookup"><span data-stu-id="3376b-270">Parameter</span></span>|<span data-ttu-id="3376b-271">Description</span><span class="sxs-lookup"><span data-stu-id="3376b-271">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3376b-272">活動：\<活動名稱\></span><span class="sxs-lookup"><span data-stu-id="3376b-272">Activity:\<activity name\></span></span>|<span data-ttu-id="3376b-273">活動的行為是要顯示的名稱。</span><span class="sxs-lookup"><span data-stu-id="3376b-273">The name of the activity for which the behavior is to be displayed.</span></span>|  
|<span data-ttu-id="3376b-274">ShouldArchive: True</span><span class="sxs-lookup"><span data-stu-id="3376b-274">ShouldArchive: True</span></span>|<span data-ttu-id="3376b-275">如果設為 True，該活動移到封存資料庫。</span><span class="sxs-lookup"><span data-stu-id="3376b-275">If set to True, the activity is moved to Archive DB.</span></span> <span data-ttu-id="3376b-276">如果設定為 False，活動會清除。</span><span class="sxs-lookup"><span data-stu-id="3376b-276">If set to False, the activity is purged.</span></span>|  
|<span data-ttu-id="3376b-277">伺服器：\<伺服器\></span><span class="sxs-lookup"><span data-stu-id="3376b-277">Server:\<server\></span></span>|<span data-ttu-id="3376b-278">選擇性： 活動所在的伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="3376b-278">Optional: The name of the server on which the activity resides.</span></span> <span data-ttu-id="3376b-279">伺服器和執行 bm.exe 的電腦必須位在相同網域中。</span><span class="sxs-lookup"><span data-stu-id="3376b-279">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="3376b-280">如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。</span><span class="sxs-lookup"><span data-stu-id="3376b-280">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="3376b-281">資料庫：\<資料庫\></span><span class="sxs-lookup"><span data-stu-id="3376b-281">Database:\<database\></span></span>|<span data-ttu-id="3376b-282">選擇性： 活動所在資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="3376b-282">Optional: The name of the database on which the activity resides.</span></span> <span data-ttu-id="3376b-283">如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。</span><span class="sxs-lookup"><span data-stu-id="3376b-283">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="3376b-284">設定封存封裝，因此活動資料會移到封存資料庫 」 活動的行為。</span><span class="sxs-lookup"><span data-stu-id="3376b-284">Sets the behavior of the archiving package for the activity specified so that activity data is moved into the Archive DB.</span></span> <span data-ttu-id="3376b-285">根據預設，此行為是設定新部署的活動。</span><span class="sxs-lookup"><span data-stu-id="3376b-285">By default, this behavior is set for new activities that are deployed.</span></span>  
  
 <span data-ttu-id="3376b-286">**範例**</span><span class="sxs-lookup"><span data-stu-id="3376b-286">**Examples**</span></span>  
  
 <span data-ttu-id="3376b-287">若要清除的 BAM 活動資料，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="3376b-287">To purge the BAM activity data, execute the following:</span></span>  
  
```  
bm.exe set-archive -Activity:PurchaseOrder -ShouldArchive:False  
```  
  
 <span data-ttu-id="3376b-288">若要將 BAM 活動資料移到 BAMArchive 資料庫，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="3376b-288">To move the BAM activity data to the BAMArchive database, execute the following:</span></span>  
  
```  
bm.exe set-archive -Activity:PurchaseOrder -ShouldArchive:True  
```  
  
## <a name="see-also"></a><span data-ttu-id="3376b-289">請參閱</span><span class="sxs-lookup"><span data-stu-id="3376b-289">See Also</span></span>  
 [<span data-ttu-id="3376b-290">BAM 管理公用程式</span><span class="sxs-lookup"><span data-stu-id="3376b-290">BAM Management Utility</span></span>](../core/bam-management-utility.md)