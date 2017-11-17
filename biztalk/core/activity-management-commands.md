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
ms.openlocfilehash: d90c5f394ed32b68f4f9b747c580fac02e22a8ed
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="activity-management-commands"></a><span data-ttu-id="4fdb9-102">活動管理命令</span><span class="sxs-lookup"><span data-stu-id="4fdb9-102">Activity Management Commands</span></span>
<span data-ttu-id="4fdb9-103">BAM 管理公用程式活動管理命令可讓您使用已部署的活動。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-103">The BAM Management utility activity management commands allow you to work with deployed activities.</span></span>  
  
-   <span data-ttu-id="4fdb9-104">取得活動： 取得已部署的活動清單。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-104">get-activities: Gets a list of deployed activities.</span></span>  
  
-   <span data-ttu-id="4fdb9-105">移除活動： 將活動中移除。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-105">remove-activity: Removes an activity.</span></span>  
  
-   <span data-ttu-id="4fdb9-106">get activitywindow： 取得活動的持續時間。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-106">get-activitywindow: Gets the duration for an activity.</span></span>  
  
-   <span data-ttu-id="4fdb9-107">設定 activitywindow： 設定活動的活動持續時間。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-107">set-activitywindow: Sets the activity duration for an activity.</span></span>  
  
-   <span data-ttu-id="4fdb9-108">取得索引： 取得索引的清單。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-108">get-index: Gets the list of indexes.</span></span>  
  
-   <span data-ttu-id="4fdb9-109">建立索引： 建立新的索引。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-109">create-index: Creates a new index.</span></span>  
  
-   <span data-ttu-id="4fdb9-110">刪除索引： 刪除索引。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-110">delete-index: Deletes an index.</span></span>  
  
-   <span data-ttu-id="4fdb9-111">get 封存： 取得封存 」 活動的行為。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-111">get-archive: Gets the behavior of archived activity.</span></span>  
  
-   <span data-ttu-id="4fdb9-112">設定封存： 設定封存 」 活動的行為。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-112">set-archive: Sets the behavior of archived activity.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4fdb9-113">您可以藉由啟用任何 BAM 公用程式命令的追蹤**-追蹤： 在 &#124; 關閉**切換參數。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-113">You can enable tracing on any BAM utility command by including the **-Trace:on&#124;off** parameter switch.</span></span> <span data-ttu-id="4fdb9-114">使用追蹤參數會覆寫組態檔中的追蹤設定。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-114">Using the Trace switch overrides the tracing settings in the configuration file.</span></span> <span data-ttu-id="4fdb9-115">此參數可以搭配任何一般 BAM 命令使用。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-115">The switch can be used in conjunction with any normal BAM command.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4fdb9-116">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-116">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="get-activities-command"></a><span data-ttu-id="4fdb9-117">get-activities 命令</span><span class="sxs-lookup"><span data-stu-id="4fdb9-117">get-activities Command</span></span>  
 <span data-ttu-id="4fdb9-118">**使用方式**</span><span class="sxs-lookup"><span data-stu-id="4fdb9-118">**Usage**</span></span>  
  
 <span data-ttu-id="4fdb9-119">**bm.exe get 活動 [-檢視：\<檢視名稱 >] [-Server:\<伺服器 >] [-Database:\<資料庫 >]**</span><span class="sxs-lookup"><span data-stu-id="4fdb9-119">**bm.exe get-activities [ -View:\<view name> ][ -Server:\<server> ][ -Database:\<database> ]**</span></span>  
  
 <span data-ttu-id="4fdb9-120">**參數**</span><span class="sxs-lookup"><span data-stu-id="4fdb9-120">**Parameters**</span></span>  
  
|<span data-ttu-id="4fdb9-121">參數</span><span class="sxs-lookup"><span data-stu-id="4fdb9-121">Parameter</span></span>|<span data-ttu-id="4fdb9-122">Description</span><span class="sxs-lookup"><span data-stu-id="4fdb9-122">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4fdb9-123">名稱：\<活動名稱 ></span><span class="sxs-lookup"><span data-stu-id="4fdb9-123">Name:\<activity name></span></span>|<span data-ttu-id="4fdb9-124">要移除的活動名稱。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-124">The name of the activity to remove.</span></span>|  
|<span data-ttu-id="4fdb9-125">伺服器：\<伺服器 ></span><span class="sxs-lookup"><span data-stu-id="4fdb9-125">Server:\<server></span></span>|<span data-ttu-id="4fdb9-126">選擇性： 要從其中取得活動清單的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-126">Optional: The name of the server from which to get the list of activities.</span></span> <span data-ttu-id="4fdb9-127">伺服器和執行 bm.exe 的電腦必須位在相同網域中。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-127">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="4fdb9-128">如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-128">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="4fdb9-129">資料庫：\<資料庫 ></span><span class="sxs-lookup"><span data-stu-id="4fdb9-129">Database:\<database></span></span>|<span data-ttu-id="4fdb9-130">選擇性： 要從中取得活動清單的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-130">Optional: The name of the database from which to get the list of activities.</span></span> <span data-ttu-id="4fdb9-131">如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-131">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="4fdb9-132">列出在執行此命令之電腦上部署的活動。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-132">Lists the activities deployed on the computer on which the command is executed.</span></span>  
  
 <span data-ttu-id="4fdb9-133">**範例**</span><span class="sxs-lookup"><span data-stu-id="4fdb9-133">**Examples**</span></span>  
  
```  
bm.exe get-activities -View:SalesManagerView  
bm.exe get-activities -Server:MyServer -Database:MyPrimaryImport  
```  
  
## <a name="remove-activity-command"></a><span data-ttu-id="4fdb9-134">remove-activity 命令</span><span class="sxs-lookup"><span data-stu-id="4fdb9-134">remove-activity Command</span></span>  
 <span data-ttu-id="4fdb9-135">**使用方式**</span><span class="sxs-lookup"><span data-stu-id="4fdb9-135">**Usage**</span></span>  
  
 <span data-ttu-id="4fdb9-136">**bm.exe 移除活動的名稱：\<活動名稱 > [-Server:\<伺服器 >] [-Database:\<資料庫 >]**</span><span class="sxs-lookup"><span data-stu-id="4fdb9-136">**bm.exe remove-activity -Name:\<activity name>[ -Server:\<server> ][ -Database:\<database> ]**</span></span>  
  
 <span data-ttu-id="4fdb9-137">**參數**</span><span class="sxs-lookup"><span data-stu-id="4fdb9-137">**Parameters**</span></span>  
  
|<span data-ttu-id="4fdb9-138">參數</span><span class="sxs-lookup"><span data-stu-id="4fdb9-138">Parameter</span></span>|<span data-ttu-id="4fdb9-139">Description</span><span class="sxs-lookup"><span data-stu-id="4fdb9-139">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4fdb9-140">名稱：\<活動名稱 ></span><span class="sxs-lookup"><span data-stu-id="4fdb9-140">Name:\<activity name></span></span>|<span data-ttu-id="4fdb9-141">要移除的活動名稱。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-141">The name of the activity to remove.</span></span>|  
|<span data-ttu-id="4fdb9-142">伺服器：\<伺服器 ></span><span class="sxs-lookup"><span data-stu-id="4fdb9-142">Server:\<server></span></span>|<span data-ttu-id="4fdb9-143">選擇性： 要移除之活動的來源伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-143">Optional: The name of the server from which to remove the activity.</span></span> <span data-ttu-id="4fdb9-144">伺服器和執行 bm.exe 的電腦必須位在相同網域中。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-144">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="4fdb9-145">如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-145">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="4fdb9-146">資料庫：\<資料庫 ></span><span class="sxs-lookup"><span data-stu-id="4fdb9-146">Database:\<database></span></span>|<span data-ttu-id="4fdb9-147">選擇性： 要從中移除活動的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-147">Optional: The name of the database from which to remove the activity.</span></span> <span data-ttu-id="4fdb9-148">如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-148">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="4fdb9-149">從 BAM 主要匯入資料庫移除指定的活動。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-149">Removes the specified activity from the BAM Primary Import database.</span></span> <span data-ttu-id="4fdb9-150">如果活動有相依檢視，命令將會失敗並報告錯誤。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-150">If the activity has dependent views, the command will fail and report an error.</span></span> <span data-ttu-id="4fdb9-151">請先使用 remove-view 命令移除所有相依檢視，然後再度執行 remove-activity 命令。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-151">Use the remove-view command to remove all the dependent views and execute the remove-activity command again.</span></span>  
  
 <span data-ttu-id="4fdb9-152">**範例**</span><span class="sxs-lookup"><span data-stu-id="4fdb9-152">**Examples**</span></span>  
  
```  
bm.exe remove-activity -Name:PurchaseOrder  
bm.exe remove-activity -Name:PO -Server:MyServer -Database:MyPrimaryImport  
```  
  
## <a name="get-activitywindow-command"></a><span data-ttu-id="4fdb9-153">get-activitywindow 命令</span><span class="sxs-lookup"><span data-stu-id="4fdb9-153">get-activitywindow Command</span></span>  
 <span data-ttu-id="4fdb9-154">**使用方式**</span><span class="sxs-lookup"><span data-stu-id="4fdb9-154">**Usage**</span></span>  
  
 <span data-ttu-id="4fdb9-155">**bm.exe get activitywindow-活動：\<活動名稱 > [-Server:\<伺服器 >] [-Database:\<資料庫 >]**</span><span class="sxs-lookup"><span data-stu-id="4fdb9-155">**bm.exe get-activitywindow -Activity:\<activity name>[ -Server:\<server> ][ -Database:\<database> ]**</span></span>  
  
 <span data-ttu-id="4fdb9-156">**參數**</span><span class="sxs-lookup"><span data-stu-id="4fdb9-156">**Parameters**</span></span>  
  
|<span data-ttu-id="4fdb9-157">參數</span><span class="sxs-lookup"><span data-stu-id="4fdb9-157">Parameter</span></span>|<span data-ttu-id="4fdb9-158">Description</span><span class="sxs-lookup"><span data-stu-id="4fdb9-158">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4fdb9-159">活動：\<活動名稱 ></span><span class="sxs-lookup"><span data-stu-id="4fdb9-159">Activity:\<activity name></span></span>|<span data-ttu-id="4fdb9-160">活動的名稱。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-160">The name of the .activity.</span></span>|  
|<span data-ttu-id="4fdb9-161">伺服器：\<伺服器 ></span><span class="sxs-lookup"><span data-stu-id="4fdb9-161">Server:\<server></span></span>|<span data-ttu-id="4fdb9-162">選擇性： 活動所在的伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-162">Optional: The name of the server on which the activity resides.</span></span> <span data-ttu-id="4fdb9-163">伺服器和執行 bm.exe 的電腦必須位在相同網域中。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-163">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="4fdb9-164">如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-164">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="4fdb9-165">資料庫：\<資料庫 ></span><span class="sxs-lookup"><span data-stu-id="4fdb9-165">Database:\<database></span></span>|<span data-ttu-id="4fdb9-166">選擇性： 活動所在資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-166">Optional: The name of the database on which the activity resides.</span></span> <span data-ttu-id="4fdb9-167">如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-167">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="4fdb9-168">顯示指定活動的持續時間。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-168">Displays the duration for the specified activity.</span></span> <span data-ttu-id="4fdb9-169">這個命令會傳回持續時間的長度以及測量持續時間所用的單位。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-169">The command returns the length of the duration and the units by which the duration is measured.</span></span>  
  
 <span data-ttu-id="4fdb9-170">**範例**</span><span class="sxs-lookup"><span data-stu-id="4fdb9-170">**Examples**</span></span>  
  
```  
bm.exe get-activitywindow -Activity:PurchaseOrder  
bm.exe get-activitywindow -Activity:PO -Server:Ship -Database:ShipDatabase  
```  
  
## <a name="set-activitywindow-command"></a><span data-ttu-id="4fdb9-171">set-activitywindow 命令</span><span class="sxs-lookup"><span data-stu-id="4fdb9-171">set-activitywindow Command</span></span>  
 <span data-ttu-id="4fdb9-172">**使用方式**</span><span class="sxs-lookup"><span data-stu-id="4fdb9-172">**Usage**</span></span>  
  
 <span data-ttu-id="4fdb9-173">**bm.exe 組 activitywindow-活動：\<活動名稱 >-TimeLength:\<整數數字 >-TimeUnit： 月份 &#124; 天 &#124;小時 &#124;分鐘 [-Server:\<伺服器 >] [-Database:\<資料庫 >]**</span><span class="sxs-lookup"><span data-stu-id="4fdb9-173">**bm.exe set-activitywindow -Activity:\<activity name> -TimeLength:\<integer number> -TimeUnit:Month&#124;Day&#124;Hour&#124;Minute[ -Server:\<server> ][ -Database:\<database> ]**</span></span>  
  
 <span data-ttu-id="4fdb9-174">**參數**</span><span class="sxs-lookup"><span data-stu-id="4fdb9-174">**Parameters**</span></span>  
  
|<span data-ttu-id="4fdb9-175">參數</span><span class="sxs-lookup"><span data-stu-id="4fdb9-175">Parameter</span></span>|<span data-ttu-id="4fdb9-176">Description</span><span class="sxs-lookup"><span data-stu-id="4fdb9-176">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4fdb9-177">活動：\<活動名稱 ></span><span class="sxs-lookup"><span data-stu-id="4fdb9-177">Activity:\<activity name></span></span>|<span data-ttu-id="4fdb9-178">活動的名稱。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-178">The name of the activity.</span></span>|  
|<span data-ttu-id="4fdb9-179">TimeLength:\<整數數字 ></span><span class="sxs-lookup"><span data-stu-id="4fdb9-179">TimeLength:\<integer number></span></span>|<span data-ttu-id="4fdb9-180">活動的持續時間。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-180">The duration for the activity.</span></span>|  
|<span data-ttu-id="4fdb9-181">TimeUnit:Month &#124; 天 &#124;小時 &#124;分鐘</span><span class="sxs-lookup"><span data-stu-id="4fdb9-181">TimeUnit:Month&#124;Day&#124;Hour&#124;Minute</span></span>|<span data-ttu-id="4fdb9-182">持續時間的計量單位。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-182">The unit measure for the duration.</span></span>|  
|<span data-ttu-id="4fdb9-183">伺服器：\<伺服器 ></span><span class="sxs-lookup"><span data-stu-id="4fdb9-183">Server:\<server></span></span>|<span data-ttu-id="4fdb9-184">選擇性： 活動所在的伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-184">Optional: The name of the server on which the activity resides.</span></span> <span data-ttu-id="4fdb9-185">伺服器和執行 bm.exe 的電腦必須位在相同網域中。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-185">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="4fdb9-186">如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-186">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="4fdb9-187">資料庫：\<資料庫 ></span><span class="sxs-lookup"><span data-stu-id="4fdb9-187">Database:\<database></span></span>|<span data-ttu-id="4fdb9-188">選擇性： 活動所在資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-188">Optional: The name of the database on which the activity resides.</span></span> <span data-ttu-id="4fdb9-189">如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-189">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="4fdb9-190">設定指定活動的持續時間。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-190">Sets the duration for the specified activity.</span></span>  
  
 <span data-ttu-id="4fdb9-191">**範例**</span><span class="sxs-lookup"><span data-stu-id="4fdb9-191">**Examples**</span></span>  
  
```  
bm.exe set-activitywindow -Activity:PurchaseOrder -TimeLength:6 -TimeUnit:Day  
bm.exe set-activitywindow -Activity:PurchaseOrder -TimeLength:1 -TimeUnit:Month  
```  
  
## <a name="get-index-command"></a><span data-ttu-id="4fdb9-192">get-index 命令</span><span class="sxs-lookup"><span data-stu-id="4fdb9-192">get-index Command</span></span>  
 <span data-ttu-id="4fdb9-193">**使用方式**</span><span class="sxs-lookup"><span data-stu-id="4fdb9-193">**Usage**</span></span>  
  
 <span data-ttu-id="4fdb9-194">**bm.exe get 索引的活動：\<活動名稱 > [-Server:\<伺服器 >] [-Database:\<資料庫 >]**</span><span class="sxs-lookup"><span data-stu-id="4fdb9-194">**bm.exe get-index -Activity:\<activity name>[ -Server:\<server> ][ -Database:\<database> ]**</span></span>  
  
 <span data-ttu-id="4fdb9-195">**參數**</span><span class="sxs-lookup"><span data-stu-id="4fdb9-195">**Parameters**</span></span>  
  
|<span data-ttu-id="4fdb9-196">參數</span><span class="sxs-lookup"><span data-stu-id="4fdb9-196">Parameter</span></span>|<span data-ttu-id="4fdb9-197">Description</span><span class="sxs-lookup"><span data-stu-id="4fdb9-197">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4fdb9-198">活動：\<活動名稱 ></span><span class="sxs-lookup"><span data-stu-id="4fdb9-198">Activity:\<activity name></span></span>|<span data-ttu-id="4fdb9-199">活動的名稱。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-199">The name of the activity.</span></span>|  
|<span data-ttu-id="4fdb9-200">伺服器：\<伺服器 ></span><span class="sxs-lookup"><span data-stu-id="4fdb9-200">Server:\<server></span></span>|<span data-ttu-id="4fdb9-201">選擇性： 活動所在的伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-201">Optional: The name of the server on which the activity resides.</span></span> <span data-ttu-id="4fdb9-202">伺服器和執行 bm.exe 的電腦必須位在相同網域中。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-202">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="4fdb9-203">如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-203">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="4fdb9-204">資料庫：\<資料庫 ></span><span class="sxs-lookup"><span data-stu-id="4fdb9-204">Database:\<database></span></span>|<span data-ttu-id="4fdb9-205">選擇性： 活動所在資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-205">Optional: The name of the database on which the activity resides.</span></span> <span data-ttu-id="4fdb9-206">如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-206">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="4fdb9-207">列出已針對指定之活動建立的所有索引。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-207">Lists all the indexes that have been created for the specified activity.</span></span>  
  
 <span data-ttu-id="4fdb9-208">**範例**</span><span class="sxs-lookup"><span data-stu-id="4fdb9-208">**Examples**</span></span>  
  
```  
bm.exe get-index -Activity:PurchaseOrder  
bm.exe get-index -Activity:PurchaseOrder -Server:Ship -Database:ShipDatabase  
```  
  
## <a name="create-index-command"></a><span data-ttu-id="4fdb9-209">create-index 命令</span><span class="sxs-lookup"><span data-stu-id="4fdb9-209">create-index Command</span></span>  
 <span data-ttu-id="4fdb9-210">**使用方式**</span><span class="sxs-lookup"><span data-stu-id="4fdb9-210">**Usage**</span></span>  
  
 <span data-ttu-id="4fdb9-211">**bm.exe 建立-IndexName:\<索引名稱 >-活動：\<活動名稱 >-檢查點：\<checkpoint1 > [，\<checkpoint2 >...][-Server:\<伺服器 >] [-Database:\<資料庫 >]**</span><span class="sxs-lookup"><span data-stu-id="4fdb9-211">**bm.exe create-index -IndexName:\<index name> -Activity:\<activity name> -Checkpoint:\<checkpoint1>[,\<checkpoint2>...][ -Server:\<server> ][ -Database:\<database> ]**</span></span>  
  
 <span data-ttu-id="4fdb9-212">**參數**</span><span class="sxs-lookup"><span data-stu-id="4fdb9-212">**Parameters**</span></span>  
  
|<span data-ttu-id="4fdb9-213">參數</span><span class="sxs-lookup"><span data-stu-id="4fdb9-213">Parameter</span></span>|<span data-ttu-id="4fdb9-214">Description</span><span class="sxs-lookup"><span data-stu-id="4fdb9-214">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4fdb9-215">IndexName:\<索引名稱 ></span><span class="sxs-lookup"><span data-stu-id="4fdb9-215">IndexName:\<index name></span></span>|<span data-ttu-id="4fdb9-216">新索引的名稱。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-216">The name of the new index.</span></span>|  
|<span data-ttu-id="4fdb9-217">活動：\<活動名稱 ></span><span class="sxs-lookup"><span data-stu-id="4fdb9-217">Activity:\<activity name></span></span>|<span data-ttu-id="4fdb9-218">建立索引的活動名稱。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-218">The name of the activity for which the index is created.</span></span>|  
|<span data-ttu-id="4fdb9-219">檢查點：\<checkpoint1 > [，\<checkpoint2 >...]</span><span class="sxs-lookup"><span data-stu-id="4fdb9-219">Checkpoint:\<checkpoint1>[,\<checkpoint2>...]</span></span>|<span data-ttu-id="4fdb9-220">索引的檢查點清單 (以逗號分隔)。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-220">A comma-delimited list of checkpoints for the index.</span></span>|  
|<span data-ttu-id="4fdb9-221">伺服器：\<伺服器 ></span><span class="sxs-lookup"><span data-stu-id="4fdb9-221">Server:\<server></span></span>|<span data-ttu-id="4fdb9-222">選擇性： 活動所在的伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-222">Optional: The name of the server on which the activity resides.</span></span> <span data-ttu-id="4fdb9-223">伺服器和執行 bm.exe 的電腦必須位在相同網域中。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-223">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="4fdb9-224">如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-224">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="4fdb9-225">資料庫：\<資料庫 ></span><span class="sxs-lookup"><span data-stu-id="4fdb9-225">Database:\<database></span></span>|<span data-ttu-id="4fdb9-226">選擇性： 活動所在資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-226">Optional: The name of the database on which the activity resides.</span></span> <span data-ttu-id="4fdb9-227">如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-227">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="4fdb9-228">使用指定的檢查點，為指定的活動建立索引。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-228">Creates an index for the specified activity using the specified checkpoints.</span></span>  
  
 <span data-ttu-id="4fdb9-229">**範例**</span><span class="sxs-lookup"><span data-stu-id="4fdb9-229">**Examples**</span></span>  
  
```  
bm.exe create-index -IndexName:Idx1 -Activity:PO -Checkpoint:State,City  
bm.exe create-index -IndexName:Idx2 -Activity:PO -Checkpoint:Amount -Server:S1  
```  
  
## <a name="delete-index-command"></a><span data-ttu-id="4fdb9-230">delete-index 命令</span><span class="sxs-lookup"><span data-stu-id="4fdb9-230">delete-index Command</span></span>  
 <span data-ttu-id="4fdb9-231">**使用方式**</span><span class="sxs-lookup"><span data-stu-id="4fdb9-231">**Usage**</span></span>  
  
 <span data-ttu-id="4fdb9-232">**bm.exe delete-IndexName:\<索引名稱 >-活動：\<活動名稱 > [-Server:\<伺服器 >] [-Database:\<資料庫 >]**</span><span class="sxs-lookup"><span data-stu-id="4fdb9-232">**bm.exe delete-index -IndexName:\<index name> -Activity:\<activity name>[ -Server:\<server> ][ -Database:\<database> ]**</span></span>  
  
 <span data-ttu-id="4fdb9-233">**參數**</span><span class="sxs-lookup"><span data-stu-id="4fdb9-233">**Parameters**</span></span>  
  
|<span data-ttu-id="4fdb9-234">參數</span><span class="sxs-lookup"><span data-stu-id="4fdb9-234">Parameter</span></span>|<span data-ttu-id="4fdb9-235">Description</span><span class="sxs-lookup"><span data-stu-id="4fdb9-235">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4fdb9-236">IndexName:\<索引名稱 ></span><span class="sxs-lookup"><span data-stu-id="4fdb9-236">IndexName:\<index name></span></span>|<span data-ttu-id="4fdb9-237">要刪除之索引的名稱。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-237">The name of the index to delete.</span></span>|  
|<span data-ttu-id="4fdb9-238">活動：\<活動名稱 ></span><span class="sxs-lookup"><span data-stu-id="4fdb9-238">Activity:\<activity name></span></span>|<span data-ttu-id="4fdb9-239">要刪除索引之活動的名稱。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-239">The name of the activity for which the index is deleted.</span></span>|  
|<span data-ttu-id="4fdb9-240">伺服器：\<伺服器 ></span><span class="sxs-lookup"><span data-stu-id="4fdb9-240">Server:\<server></span></span>|<span data-ttu-id="4fdb9-241">選擇性： 活動所在的伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-241">Optional: The name of the server on which the activity resides.</span></span> <span data-ttu-id="4fdb9-242">伺服器和執行 bm.exe 的電腦必須位在相同網域中。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-242">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="4fdb9-243">如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-243">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="4fdb9-244">資料庫：\<資料庫 ></span><span class="sxs-lookup"><span data-stu-id="4fdb9-244">Database:\<database></span></span>|<span data-ttu-id="4fdb9-245">選擇性： 活動所在資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-245">Optional: The name of the database on which the activity resides.</span></span> <span data-ttu-id="4fdb9-246">如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-246">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="4fdb9-247">從指定的活動刪除具有指定名稱的指定索引。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-247">Deletes the specified index with the given name from the specified activity.</span></span>  
  
 <span data-ttu-id="4fdb9-248">**範例**</span><span class="sxs-lookup"><span data-stu-id="4fdb9-248">**Examples**</span></span>  
  
```  
bm.exe delete-index -IndexName:Idx1 -Activity:PO  
bm.exe delete-index -IndexName:Idx2 -Activity:PO -Server:S1 -Database:BamPI1  
```  
  
## <a name="set-archive-command"></a><span data-ttu-id="4fdb9-249">set-archive 命令</span><span class="sxs-lookup"><span data-stu-id="4fdb9-249">set-archive Command</span></span>  
 <span data-ttu-id="4fdb9-250">**使用方式**</span><span class="sxs-lookup"><span data-stu-id="4fdb9-250">**Usage**</span></span>  
  
 <span data-ttu-id="4fdb9-251">**bm.exe get 封存-活動：\<活動 > [-Server:\<伺服器 >] [-Database:\<資料庫 >]**</span><span class="sxs-lookup"><span data-stu-id="4fdb9-251">**bm.exe get-archive -Activity:\<activity> [-Server:\<server>] [-Database:\<database>]**</span></span>  
  
 <span data-ttu-id="4fdb9-252">**參數**</span><span class="sxs-lookup"><span data-stu-id="4fdb9-252">**Parameters**</span></span>  
  
|<span data-ttu-id="4fdb9-253">參數</span><span class="sxs-lookup"><span data-stu-id="4fdb9-253">Parameter</span></span>|<span data-ttu-id="4fdb9-254">Description</span><span class="sxs-lookup"><span data-stu-id="4fdb9-254">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4fdb9-255">活動：\<活動名稱 ></span><span class="sxs-lookup"><span data-stu-id="4fdb9-255">Activity:\<activity name></span></span>|<span data-ttu-id="4fdb9-256">活動的行為是要顯示的名稱。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-256">The name of the activity for which the behavior is to be displayed.</span></span>|  
|<span data-ttu-id="4fdb9-257">伺服器：\<伺服器 ></span><span class="sxs-lookup"><span data-stu-id="4fdb9-257">Server:\<server></span></span>|<span data-ttu-id="4fdb9-258">選擇性： 活動所在的伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-258">Optional: The name of the server on which the activity resides.</span></span> <span data-ttu-id="4fdb9-259">伺服器和執行 bm.exe 的電腦必須位在相同網域中。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-259">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="4fdb9-260">如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-260">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="4fdb9-261">資料庫：\<資料庫 ></span><span class="sxs-lookup"><span data-stu-id="4fdb9-261">Database:\<database></span></span>|<span data-ttu-id="4fdb9-262">選擇性： 活動所在資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-262">Optional: The name of the database on which the activity resides.</span></span> <span data-ttu-id="4fdb9-263">如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-263">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="4fdb9-264">取得指定的活動，封存套件的行為是否封存的封裝將會封存 orpurge 活動資料。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-264">Gets the behavior of the archiving package for the specified activity, whether the archiving package will archive orpurge activity data.</span></span>  
  
 <span data-ttu-id="4fdb9-265">**範例**</span><span class="sxs-lookup"><span data-stu-id="4fdb9-265">**Examples**</span></span>  
  
```  
bm.exe get-archive -Activity:PurchaseOrder  
```  
  
## <a name="set-archive-command"></a><span data-ttu-id="4fdb9-266">set-archive 命令</span><span class="sxs-lookup"><span data-stu-id="4fdb9-266">set-archive Command</span></span>  
 <span data-ttu-id="4fdb9-267">**使用方式**</span><span class="sxs-lookup"><span data-stu-id="4fdb9-267">**Usage**</span></span>  
  
 <span data-ttu-id="4fdb9-268">**bm.exe 組封存-活動：\<活動 >-ShouldArchive:，則為 True [-Server:\<伺服器 >] [-Database:\<資料庫 >]**</span><span class="sxs-lookup"><span data-stu-id="4fdb9-268">**bm.exe set-archive -Activity:\<activity> -ShouldArchive:True [-Server:\<server>] [-Database:\<database>]**</span></span>  
  
 <span data-ttu-id="4fdb9-269">**參數**</span><span class="sxs-lookup"><span data-stu-id="4fdb9-269">**Parameters**</span></span>  
  
|<span data-ttu-id="4fdb9-270">參數</span><span class="sxs-lookup"><span data-stu-id="4fdb9-270">Parameter</span></span>|<span data-ttu-id="4fdb9-271">Description</span><span class="sxs-lookup"><span data-stu-id="4fdb9-271">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4fdb9-272">活動：\<活動名稱 ></span><span class="sxs-lookup"><span data-stu-id="4fdb9-272">Activity:\<activity name></span></span>|<span data-ttu-id="4fdb9-273">活動的行為是要顯示的名稱。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-273">The name of the activity for which the behavior is to be displayed.</span></span>|  
|<span data-ttu-id="4fdb9-274">ShouldArchive: True</span><span class="sxs-lookup"><span data-stu-id="4fdb9-274">ShouldArchive: True</span></span>|<span data-ttu-id="4fdb9-275">如果設為 True，該活動移到封存資料庫。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-275">If set to True, the activity is moved to Archive DB.</span></span> <span data-ttu-id="4fdb9-276">如果設定為 False，活動會清除。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-276">If set to False, the activity is purged.</span></span>|  
|<span data-ttu-id="4fdb9-277">伺服器：\<伺服器 ></span><span class="sxs-lookup"><span data-stu-id="4fdb9-277">Server:\<server></span></span>|<span data-ttu-id="4fdb9-278">選擇性： 活動所在的伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-278">Optional: The name of the server on which the activity resides.</span></span> <span data-ttu-id="4fdb9-279">伺服器和執行 bm.exe 的電腦必須位在相同網域中。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-279">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="4fdb9-280">如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-280">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="4fdb9-281">資料庫：\<資料庫 ></span><span class="sxs-lookup"><span data-stu-id="4fdb9-281">Database:\<database></span></span>|<span data-ttu-id="4fdb9-282">選擇性： 活動所在資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-282">Optional: The name of the database on which the activity resides.</span></span> <span data-ttu-id="4fdb9-283">如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-283">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="4fdb9-284">設定封存封裝，因此活動資料會移到封存資料庫 」 活動的行為。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-284">Sets the behavior of the archiving package for the activity specified so that activity data is moved into the Archive DB.</span></span> <span data-ttu-id="4fdb9-285">根據預設，此行為是設定新部署的活動。</span><span class="sxs-lookup"><span data-stu-id="4fdb9-285">By default, this behavior is set for new activities that are deployed.</span></span>  
  
 <span data-ttu-id="4fdb9-286">**範例**</span><span class="sxs-lookup"><span data-stu-id="4fdb9-286">**Examples**</span></span>  
  
 <span data-ttu-id="4fdb9-287">若要清除的 BAM 活動資料，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="4fdb9-287">To purge the BAM activity data, execute the following:</span></span>  
  
```  
bm.exe set-archive -Activity:PurchaseOrder -ShouldArchive:False  
```  
  
 <span data-ttu-id="4fdb9-288">若要將 BAM 活動資料移到 BAMArchive 資料庫，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="4fdb9-288">To move the BAM activity data to the BAMArchive database, execute the following:</span></span>  
  
```  
bm.exe set-archive -Activity:PurchaseOrder -ShouldArchive:True  
```  
  
## <a name="see-also"></a><span data-ttu-id="4fdb9-289">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4fdb9-289">See Also</span></span>  
 [<span data-ttu-id="4fdb9-290">BAM 管理公用程式</span><span class="sxs-lookup"><span data-stu-id="4fdb9-290">BAM Management Utility</span></span>](../core/bam-management-utility.md)