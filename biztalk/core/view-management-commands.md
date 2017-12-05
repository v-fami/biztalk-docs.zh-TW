---
title: "檢視管理命令 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52f25ee3-9bb3-4682-a9ff-cac8c25f58c3
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6ced7a9ac58fa0375e3eaefa49832e6c23ba1a73
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="view-management-commands"></a><span data-ttu-id="9f1b4-102">檢視管理命令</span><span class="sxs-lookup"><span data-stu-id="9f1b4-102">View Management Commands</span></span>
<span data-ttu-id="9f1b4-103">[BAM 管理] 公用程式檢視管理命令可讓您使用已部署的檢視。</span><span class="sxs-lookup"><span data-stu-id="9f1b4-103">The BAM Management utility view management commands allow you to work with deployed views.</span></span>  
  
-   <span data-ttu-id="9f1b4-104">取得檢視表： 列出所有已部署的檢視。</span><span class="sxs-lookup"><span data-stu-id="9f1b4-104">get-views: Lists all the deployed views.</span></span>  
  
-   <span data-ttu-id="9f1b4-105">移除檢視： 移除已部署的檢視。</span><span class="sxs-lookup"><span data-stu-id="9f1b4-105">remove-view: Removes a deployed view.</span></span>  
  
-   <span data-ttu-id="9f1b4-106">get rtawindow： 在檢視上取得的持續時間。</span><span class="sxs-lookup"><span data-stu-id="9f1b4-106">get-rtawindow: Gets the duration on a view.</span></span>  
  
-   <span data-ttu-id="9f1b4-107">設定 rtawindow： 在檢視上設定的持續時間。</span><span class="sxs-lookup"><span data-stu-id="9f1b4-107">set-rtawindow: Sets the duration on a view.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9f1b4-108">您可以藉由啟用任何 BM 公用程式命令的追蹤**-追蹤： 在 &#124; 關閉**切換參數。</span><span class="sxs-lookup"><span data-stu-id="9f1b4-108">You can enable tracing on any BM utility command by including the **-Trace:on&#124;off** parameter switch.</span></span> <span data-ttu-id="9f1b4-109">使用追蹤參數會覆寫組態檔中的追蹤設定。</span><span class="sxs-lookup"><span data-stu-id="9f1b4-109">Using the Trace switch overrides the tracing settings in the configuration file.</span></span> <span data-ttu-id="9f1b4-110">此參數可以搭配任何一般 BM 命令使用。</span><span class="sxs-lookup"><span data-stu-id="9f1b4-110">The switch can be used in conjunction with any normal BM command.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9f1b4-111">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="9f1b4-111">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="get-views-command"></a><span data-ttu-id="9f1b4-112">get-views 命令</span><span class="sxs-lookup"><span data-stu-id="9f1b4-112">get-views Command</span></span>  
 <span data-ttu-id="9f1b4-113">**使用方式**</span><span class="sxs-lookup"><span data-stu-id="9f1b4-113">**Usage**</span></span>  
  
 <span data-ttu-id="9f1b4-114">**bm.exe get 檢視 [-活動：\<活動名稱\>] [-Server:\<伺服器\>] [-Database:\<資料庫\>]**</span><span class="sxs-lookup"><span data-stu-id="9f1b4-114">**bm.exe get-views [ -Activity:\<activity name\> ][ -Server:\<server\> ][ -Database:\<database\> ]**</span></span>  
  
 <span data-ttu-id="9f1b4-115">**參數**</span><span class="sxs-lookup"><span data-stu-id="9f1b4-115">**Parameters**</span></span>  
  
|<span data-ttu-id="9f1b4-116">參數</span><span class="sxs-lookup"><span data-stu-id="9f1b4-116">Parameter</span></span>|<span data-ttu-id="9f1b4-117">Description</span><span class="sxs-lookup"><span data-stu-id="9f1b4-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9f1b4-118">活動：\<活動名稱\></span><span class="sxs-lookup"><span data-stu-id="9f1b4-118">Activity:\<activity name\></span></span>|<span data-ttu-id="9f1b4-119">要列出其檢視的活動名稱。</span><span class="sxs-lookup"><span data-stu-id="9f1b4-119">The name of the activity from which to list the views.</span></span>|  
|<span data-ttu-id="9f1b4-120">伺服器：\<伺服器\></span><span class="sxs-lookup"><span data-stu-id="9f1b4-120">Server:\<server\></span></span>|<span data-ttu-id="9f1b4-121">選擇性： 取得檢視的清單的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="9f1b4-121">Optional: The name of the server from which to get the list of views.</span></span> <span data-ttu-id="9f1b4-122">伺服器和執行 bm.exe 的電腦必須位在相同網域中。</span><span class="sxs-lookup"><span data-stu-id="9f1b4-122">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="9f1b4-123">如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。</span><span class="sxs-lookup"><span data-stu-id="9f1b4-123">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="9f1b4-124">資料庫：\<資料庫\></span><span class="sxs-lookup"><span data-stu-id="9f1b4-124">Database:\<database\></span></span>|<span data-ttu-id="9f1b4-125">選擇性： 取得的檢視清單之資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="9f1b4-125">Optional: The name of the database from which to get the list of views.</span></span> <span data-ttu-id="9f1b4-126">如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。</span><span class="sxs-lookup"><span data-stu-id="9f1b4-126">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="9f1b4-127">列出在執行此命令的電腦上部署的檢視。</span><span class="sxs-lookup"><span data-stu-id="9f1b4-127">Lists the views deployed on the computer on which the command is executed.</span></span>  
  
 <span data-ttu-id="9f1b4-128">**範例**</span><span class="sxs-lookup"><span data-stu-id="9f1b4-128">**Examples**</span></span>  
  
```  
bm.exe get-views -Activity:PO1  
bm.exe get-views -Server:MyServer -Database:MyPrimaryImport  
```  
  
## <a name="remove-view-command"></a><span data-ttu-id="9f1b4-129">remove-view 命令</span><span class="sxs-lookup"><span data-stu-id="9f1b4-129">remove-view Command</span></span>  
 <span data-ttu-id="9f1b4-130">**使用方式**</span><span class="sxs-lookup"><span data-stu-id="9f1b4-130">**Usage**</span></span>  
  
 <span data-ttu-id="9f1b4-131">**bm.exe 移除檢視-名稱：\<檢視名稱\>[-Server:\<伺服器\>] [-Database:\<資料庫\>]**</span><span class="sxs-lookup"><span data-stu-id="9f1b4-131">**bm.exe remove-view -Name:\<view name\> [ -Server:\<server\> ][ -Database:\<database\> ]**</span></span>  
  
 <span data-ttu-id="9f1b4-132">**參數**</span><span class="sxs-lookup"><span data-stu-id="9f1b4-132">**Parameters**</span></span>  
  
|<span data-ttu-id="9f1b4-133">參數</span><span class="sxs-lookup"><span data-stu-id="9f1b4-133">Parameter</span></span>|<span data-ttu-id="9f1b4-134">Description</span><span class="sxs-lookup"><span data-stu-id="9f1b4-134">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9f1b4-135">名稱：\<檢視表名稱\></span><span class="sxs-lookup"><span data-stu-id="9f1b4-135">Name:\<view name\></span></span>|<span data-ttu-id="9f1b4-136">要移除的檢視名稱。</span><span class="sxs-lookup"><span data-stu-id="9f1b4-136">The name of the view to remove.</span></span>|  
|<span data-ttu-id="9f1b4-137">伺服器：\<伺服器\></span><span class="sxs-lookup"><span data-stu-id="9f1b4-137">Server:\<server\></span></span>|<span data-ttu-id="9f1b4-138">選擇性： 要移除其檢視的來源伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="9f1b4-138">Optional: The name of the server from which to remove the view.</span></span> <span data-ttu-id="9f1b4-139">伺服器和執行 bm.exe 的電腦必須位在相同網域中。</span><span class="sxs-lookup"><span data-stu-id="9f1b4-139">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="9f1b4-140">如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。</span><span class="sxs-lookup"><span data-stu-id="9f1b4-140">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="9f1b4-141">資料庫：\<資料庫\></span><span class="sxs-lookup"><span data-stu-id="9f1b4-141">Database:\<database\></span></span>|<span data-ttu-id="9f1b4-142">選擇性： 要從中移除其檢視的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="9f1b4-142">Optional: The name of the database from which to remove the view.</span></span> <span data-ttu-id="9f1b4-143">如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。</span><span class="sxs-lookup"><span data-stu-id="9f1b4-143">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="9f1b4-144">從 BAM 主要匯入資料庫移除指定的檢視。</span><span class="sxs-lookup"><span data-stu-id="9f1b4-144">Removes the specified view from the BAM Primary Import database.</span></span> <span data-ttu-id="9f1b4-145">如果檢視有相依警示，就會一併移除這些警示。</span><span class="sxs-lookup"><span data-stu-id="9f1b4-145">If the view has dependent alerts, they are removed at the same time.</span></span>  
  
 <span data-ttu-id="9f1b4-146">**範例**</span><span class="sxs-lookup"><span data-stu-id="9f1b4-146">**Examples**</span></span>  
  
```  
bm.exe remove-view -Name:POView  
bm.exe remove-view -Name:MyView -Server:MyServer -Database:MyPrimaryImport  
```  
  
## <a name="get-rtawindow-command"></a><span data-ttu-id="9f1b4-147">get-rtawindow 命令</span><span class="sxs-lookup"><span data-stu-id="9f1b4-147">get-rtawindow Command</span></span>  
 <span data-ttu-id="9f1b4-148">**使用方式**</span><span class="sxs-lookup"><span data-stu-id="9f1b4-148">**Usage**</span></span>  
  
 <span data-ttu-id="9f1b4-149">**bm.exe get rtawindow-檢視：\<檢視名稱\>-活動：\<活動名稱\>Rta:\<RTA 名稱\>[-Server:\<伺服器\>] [-Database:\<資料庫\>]**</span><span class="sxs-lookup"><span data-stu-id="9f1b4-149">**bm.exe get-rtawindow -View:\<view name\> -Activity:\<activity name\> -Rta:\<RTA name\>[ -Server:\<server\> ][ -Database:\<database\> ]**</span></span>  
  
 <span data-ttu-id="9f1b4-150">**參數**</span><span class="sxs-lookup"><span data-stu-id="9f1b4-150">**Parameters**</span></span>  
  
|<span data-ttu-id="9f1b4-151">參數</span><span class="sxs-lookup"><span data-stu-id="9f1b4-151">Parameter</span></span>|<span data-ttu-id="9f1b4-152">Description</span><span class="sxs-lookup"><span data-stu-id="9f1b4-152">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9f1b4-153">檢視：\<檢視表名稱\></span><span class="sxs-lookup"><span data-stu-id="9f1b4-153">View:\<view name\></span></span>|<span data-ttu-id="9f1b4-154">檢視名稱。</span><span class="sxs-lookup"><span data-stu-id="9f1b4-154">The view name.</span></span>|  
|<span data-ttu-id="9f1b4-155">活動：\<活動名稱\></span><span class="sxs-lookup"><span data-stu-id="9f1b4-155">Activity:\<activity name\></span></span>|<span data-ttu-id="9f1b4-156">活動名稱。</span><span class="sxs-lookup"><span data-stu-id="9f1b4-156">The activity name.</span></span>|  
|<span data-ttu-id="9f1b4-157">Rta:\<RTA 名稱\></span><span class="sxs-lookup"><span data-stu-id="9f1b4-157">Rta:\<RTA name\></span></span>|<span data-ttu-id="9f1b4-158">即時彙總名稱。</span><span class="sxs-lookup"><span data-stu-id="9f1b4-158">The real-time aggregation name.</span></span>|  
|<span data-ttu-id="9f1b4-159">伺服器：\<伺服器\></span><span class="sxs-lookup"><span data-stu-id="9f1b4-159">Server:\<server\></span></span>|<span data-ttu-id="9f1b4-160">選擇性： 活動所在的伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="9f1b4-160">Optional: The name of the server on which the activity resides.</span></span> <span data-ttu-id="9f1b4-161">伺服器和執行 bm.exe 的電腦必須位在相同網域中。</span><span class="sxs-lookup"><span data-stu-id="9f1b4-161">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="9f1b4-162">如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。</span><span class="sxs-lookup"><span data-stu-id="9f1b4-162">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="9f1b4-163">資料庫：\<資料庫\></span><span class="sxs-lookup"><span data-stu-id="9f1b4-163">Database:\<database\></span></span>|<span data-ttu-id="9f1b4-164">選擇性： 活動所在資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="9f1b4-164">Optional: The name of the database on which the activity resides.</span></span> <span data-ttu-id="9f1b4-165">如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。</span><span class="sxs-lookup"><span data-stu-id="9f1b4-165">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="9f1b4-166">顯示指定之即時彙總的持續時間。</span><span class="sxs-lookup"><span data-stu-id="9f1b4-166">Displays the duration of the specified real-time aggregation.</span></span> <span data-ttu-id="9f1b4-167">這個命令會傳回持續時間的長度以及測量持續時間所用的單位。</span><span class="sxs-lookup"><span data-stu-id="9f1b4-167">The command returns the length of the duration and the units by which the duration is measured.</span></span>  
  
 <span data-ttu-id="9f1b4-168">**範例**</span><span class="sxs-lookup"><span data-stu-id="9f1b4-168">**Examples**</span></span>  
  
```  
bm.exe get-rtawindow -View:ManagerView -Activity:PO -Rta:Rta1  
bm.exe get-rtawindow -View:V1 -Activity:A2 -Rta:R3 -Server:S1 -Database:BamPI  
```  
  
## <a name="set-rtawindow-command"></a><span data-ttu-id="9f1b4-169">set-rtawindow 命令</span><span class="sxs-lookup"><span data-stu-id="9f1b4-169">set-rtawindow Command</span></span>  
 <span data-ttu-id="9f1b4-170">**使用方式**</span><span class="sxs-lookup"><span data-stu-id="9f1b4-170">**Usage**</span></span>  
  
 <span data-ttu-id="9f1b4-171">**bm.exe 組 rtawindow-檢視：\<檢視名稱\>-活動：\<活動名稱\>-Name:\<RTA 名稱\>-TimeLength:\<整數數字\>-TimeUnit:Day &#124;小時 &#124;分鐘 [-Server:\<伺服器\>] [-Database:\<資料庫\>]**</span><span class="sxs-lookup"><span data-stu-id="9f1b4-171">**bm.exe set-rtawindow -View:\<view name\> -Activity:\<activity name\> -Name:\<RTA name\> -TimeLength:\<integer number\>-TimeUnit:Day&#124;Hour&#124;Minute[ -Server:\<server\> ][ -Database:\<database\> ]**</span></span>  
  
 <span data-ttu-id="9f1b4-172">**參數**</span><span class="sxs-lookup"><span data-stu-id="9f1b4-172">**Parameters**</span></span>  
  
|<span data-ttu-id="9f1b4-173">參數</span><span class="sxs-lookup"><span data-stu-id="9f1b4-173">Parameter</span></span>|<span data-ttu-id="9f1b4-174">Description</span><span class="sxs-lookup"><span data-stu-id="9f1b4-174">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9f1b4-175">檢視：\<檢視表名稱\></span><span class="sxs-lookup"><span data-stu-id="9f1b4-175">View:\<view name\></span></span>|<span data-ttu-id="9f1b4-176">檢視名稱。</span><span class="sxs-lookup"><span data-stu-id="9f1b4-176">The view name.</span></span>|  
|<span data-ttu-id="9f1b4-177">活動：\<活動名稱\></span><span class="sxs-lookup"><span data-stu-id="9f1b4-177">Activity:\<activity name\></span></span>|<span data-ttu-id="9f1b4-178">活動名稱。</span><span class="sxs-lookup"><span data-stu-id="9f1b4-178">The activity name.</span></span>|  
|<span data-ttu-id="9f1b4-179">名稱：\<RTA 名稱\></span><span class="sxs-lookup"><span data-stu-id="9f1b4-179">Name:\<RTA name\></span></span>|<span data-ttu-id="9f1b4-180">即時彙總名稱。</span><span class="sxs-lookup"><span data-stu-id="9f1b4-180">The real-time aggregation name.</span></span>|  
|<span data-ttu-id="9f1b4-181">TimeLength:\<整數數字\></span><span class="sxs-lookup"><span data-stu-id="9f1b4-181">TimeLength:\<integer number\></span></span>|<span data-ttu-id="9f1b4-182">即時彙總的持續時間。</span><span class="sxs-lookup"><span data-stu-id="9f1b4-182">The duration for the real-time aggregation.</span></span>|  
|<span data-ttu-id="9f1b4-183">TimeUnit:Month &#124; 天 &#124;小時 &#124;分鐘</span><span class="sxs-lookup"><span data-stu-id="9f1b4-183">TimeUnit:Month&#124;Day&#124;Hour&#124;Minute</span></span>|<span data-ttu-id="9f1b4-184">視窗持續時間的計量單位。</span><span class="sxs-lookup"><span data-stu-id="9f1b4-184">The unit measure for the window duration.</span></span>|  
|<span data-ttu-id="9f1b4-185">伺服器：\<伺服器\></span><span class="sxs-lookup"><span data-stu-id="9f1b4-185">Server:\<server\></span></span>|<span data-ttu-id="9f1b4-186">選擇性： 活動所在的伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="9f1b4-186">Optional: The name of the server on which the activity resides.</span></span> <span data-ttu-id="9f1b4-187">伺服器必須位在相同的網域執行 bm.exe 的電腦。</span><span class="sxs-lookup"><span data-stu-id="9f1b4-187">The server must be in the same domain as the machine from which you are running bm.exe.</span></span> <span data-ttu-id="9f1b4-188">如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。</span><span class="sxs-lookup"><span data-stu-id="9f1b4-188">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="9f1b4-189">資料庫：\<資料庫\></span><span class="sxs-lookup"><span data-stu-id="9f1b4-189">Database:\<database\></span></span>|<span data-ttu-id="9f1b4-190">選擇性： 活動所在資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="9f1b4-190">Optional: The name of the database on which the activity resides.</span></span> <span data-ttu-id="9f1b4-191">如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。</span><span class="sxs-lookup"><span data-stu-id="9f1b4-191">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="9f1b4-192">設定指定之即時彙總的持續時間。</span><span class="sxs-lookup"><span data-stu-id="9f1b4-192">Sets the duration for the specified real-time aggregation.</span></span>  
  
 <span data-ttu-id="9f1b4-193">**範例**</span><span class="sxs-lookup"><span data-stu-id="9f1b4-193">**Examples**</span></span>  
  
```  
bm.exe set-rtawindow -View:V -Activity:A -Name:R -TimeLength:5 -TimeUnit:Minute  
bm.exe set-rtawindow -View:V -Activity:A -Name:R -TimeLength:1 -TimeUnit:Hour  
```  
  
## <a name="see-also"></a><span data-ttu-id="9f1b4-194">請參閱</span><span class="sxs-lookup"><span data-stu-id="9f1b4-194">See Also</span></span>  
 [<span data-ttu-id="9f1b4-195">BAM 管理公用程式</span><span class="sxs-lookup"><span data-stu-id="9f1b4-195">BAM Management Utility</span></span>](../core/bam-management-utility.md)