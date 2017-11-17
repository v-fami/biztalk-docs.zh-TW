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
ms.openlocfilehash: 4b0a641c6d461d02f8db3e0fb0112321e0657e44
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="view-management-commands"></a><span data-ttu-id="51f8b-102">檢視管理命令</span><span class="sxs-lookup"><span data-stu-id="51f8b-102">View Management Commands</span></span>
<span data-ttu-id="51f8b-103">[BAM 管理] 公用程式檢視管理命令可讓您使用已部署的檢視。</span><span class="sxs-lookup"><span data-stu-id="51f8b-103">The BAM Management utility view management commands allow you to work with deployed views.</span></span>  
  
-   <span data-ttu-id="51f8b-104">取得檢視表： 列出所有已部署的檢視。</span><span class="sxs-lookup"><span data-stu-id="51f8b-104">get-views: Lists all the deployed views.</span></span>  
  
-   <span data-ttu-id="51f8b-105">移除檢視： 移除已部署的檢視。</span><span class="sxs-lookup"><span data-stu-id="51f8b-105">remove-view: Removes a deployed view.</span></span>  
  
-   <span data-ttu-id="51f8b-106">get rtawindow： 在檢視上取得的持續時間。</span><span class="sxs-lookup"><span data-stu-id="51f8b-106">get-rtawindow: Gets the duration on a view.</span></span>  
  
-   <span data-ttu-id="51f8b-107">設定 rtawindow： 在檢視上設定的持續時間。</span><span class="sxs-lookup"><span data-stu-id="51f8b-107">set-rtawindow: Sets the duration on a view.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="51f8b-108">您可以藉由啟用任何 BM 公用程式命令的追蹤**-追蹤： 在 &#124; 關閉**切換參數。</span><span class="sxs-lookup"><span data-stu-id="51f8b-108">You can enable tracing on any BM utility command by including the **-Trace:on&#124;off** parameter switch.</span></span> <span data-ttu-id="51f8b-109">使用追蹤參數會覆寫組態檔中的追蹤設定。</span><span class="sxs-lookup"><span data-stu-id="51f8b-109">Using the Trace switch overrides the tracing settings in the configuration file.</span></span> <span data-ttu-id="51f8b-110">此參數可以搭配任何一般 BM 命令使用。</span><span class="sxs-lookup"><span data-stu-id="51f8b-110">The switch can be used in conjunction with any normal BM command.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="51f8b-111">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="51f8b-111">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="get-views-command"></a><span data-ttu-id="51f8b-112">get-views 命令</span><span class="sxs-lookup"><span data-stu-id="51f8b-112">get-views Command</span></span>  
 <span data-ttu-id="51f8b-113">**使用方式**</span><span class="sxs-lookup"><span data-stu-id="51f8b-113">**Usage**</span></span>  
  
 <span data-ttu-id="51f8b-114">**bm.exe get 檢視 [-活動：\<活動名稱 >] [-Server:\<伺服器 >] [-Database:\<資料庫 >]**</span><span class="sxs-lookup"><span data-stu-id="51f8b-114">**bm.exe get-views [ -Activity:\<activity name> ][ -Server:\<server> ][ -Database:\<database> ]**</span></span>  
  
 <span data-ttu-id="51f8b-115">**參數**</span><span class="sxs-lookup"><span data-stu-id="51f8b-115">**Parameters**</span></span>  
  
|<span data-ttu-id="51f8b-116">參數</span><span class="sxs-lookup"><span data-stu-id="51f8b-116">Parameter</span></span>|<span data-ttu-id="51f8b-117">Description</span><span class="sxs-lookup"><span data-stu-id="51f8b-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="51f8b-118">活動：\<活動名稱 ></span><span class="sxs-lookup"><span data-stu-id="51f8b-118">Activity:\<activity name></span></span>|<span data-ttu-id="51f8b-119">要列出其檢視的活動名稱。</span><span class="sxs-lookup"><span data-stu-id="51f8b-119">The name of the activity from which to list the views.</span></span>|  
|<span data-ttu-id="51f8b-120">伺服器：\<伺服器 ></span><span class="sxs-lookup"><span data-stu-id="51f8b-120">Server:\<server></span></span>|<span data-ttu-id="51f8b-121">選擇性： 取得檢視的清單的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="51f8b-121">Optional: The name of the server from which to get the list of views.</span></span> <span data-ttu-id="51f8b-122">伺服器和執行 bm.exe 的電腦必須位在相同網域中。</span><span class="sxs-lookup"><span data-stu-id="51f8b-122">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="51f8b-123">如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。</span><span class="sxs-lookup"><span data-stu-id="51f8b-123">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="51f8b-124">資料庫：\<資料庫 ></span><span class="sxs-lookup"><span data-stu-id="51f8b-124">Database:\<database></span></span>|<span data-ttu-id="51f8b-125">選擇性： 取得的檢視清單之資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="51f8b-125">Optional: The name of the database from which to get the list of views.</span></span> <span data-ttu-id="51f8b-126">如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。</span><span class="sxs-lookup"><span data-stu-id="51f8b-126">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="51f8b-127">列出在執行此命令的電腦上部署的檢視。</span><span class="sxs-lookup"><span data-stu-id="51f8b-127">Lists the views deployed on the computer on which the command is executed.</span></span>  
  
 <span data-ttu-id="51f8b-128">**範例**</span><span class="sxs-lookup"><span data-stu-id="51f8b-128">**Examples**</span></span>  
  
```  
bm.exe get-views -Activity:PO1  
bm.exe get-views -Server:MyServer -Database:MyPrimaryImport  
```  
  
## <a name="remove-view-command"></a><span data-ttu-id="51f8b-129">remove-view 命令</span><span class="sxs-lookup"><span data-stu-id="51f8b-129">remove-view Command</span></span>  
 <span data-ttu-id="51f8b-130">**使用方式**</span><span class="sxs-lookup"><span data-stu-id="51f8b-130">**Usage**</span></span>  
  
 <span data-ttu-id="51f8b-131">**bm.exe 移除檢視-名稱：\<檢視名稱 > [-Server:\<伺服器 >] [-Database:\<資料庫 >]**</span><span class="sxs-lookup"><span data-stu-id="51f8b-131">**bm.exe remove-view -Name:\<view name> [ -Server:\<server> ][ -Database:\<database> ]**</span></span>  
  
 <span data-ttu-id="51f8b-132">**參數**</span><span class="sxs-lookup"><span data-stu-id="51f8b-132">**Parameters**</span></span>  
  
|<span data-ttu-id="51f8b-133">參數</span><span class="sxs-lookup"><span data-stu-id="51f8b-133">Parameter</span></span>|<span data-ttu-id="51f8b-134">Description</span><span class="sxs-lookup"><span data-stu-id="51f8b-134">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="51f8b-135">名稱：\<檢視名稱 ></span><span class="sxs-lookup"><span data-stu-id="51f8b-135">Name:\<view name></span></span>|<span data-ttu-id="51f8b-136">要移除的檢視名稱。</span><span class="sxs-lookup"><span data-stu-id="51f8b-136">The name of the view to remove.</span></span>|  
|<span data-ttu-id="51f8b-137">伺服器：\<伺服器 ></span><span class="sxs-lookup"><span data-stu-id="51f8b-137">Server:\<server></span></span>|<span data-ttu-id="51f8b-138">選擇性： 要移除其檢視的來源伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="51f8b-138">Optional: The name of the server from which to remove the view.</span></span> <span data-ttu-id="51f8b-139">伺服器和執行 bm.exe 的電腦必須位在相同網域中。</span><span class="sxs-lookup"><span data-stu-id="51f8b-139">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="51f8b-140">如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。</span><span class="sxs-lookup"><span data-stu-id="51f8b-140">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="51f8b-141">資料庫：\<資料庫 ></span><span class="sxs-lookup"><span data-stu-id="51f8b-141">Database:\<database></span></span>|<span data-ttu-id="51f8b-142">選擇性： 要從中移除其檢視的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="51f8b-142">Optional: The name of the database from which to remove the view.</span></span> <span data-ttu-id="51f8b-143">如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。</span><span class="sxs-lookup"><span data-stu-id="51f8b-143">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="51f8b-144">從 BAM 主要匯入資料庫移除指定的檢視。</span><span class="sxs-lookup"><span data-stu-id="51f8b-144">Removes the specified view from the BAM Primary Import database.</span></span> <span data-ttu-id="51f8b-145">如果檢視有相依警示，就會一併移除這些警示。</span><span class="sxs-lookup"><span data-stu-id="51f8b-145">If the view has dependent alerts, they are removed at the same time.</span></span>  
  
 <span data-ttu-id="51f8b-146">**範例**</span><span class="sxs-lookup"><span data-stu-id="51f8b-146">**Examples**</span></span>  
  
```  
bm.exe remove-view -Name:POView  
bm.exe remove-view -Name:MyView -Server:MyServer -Database:MyPrimaryImport  
```  
  
## <a name="get-rtawindow-command"></a><span data-ttu-id="51f8b-147">get-rtawindow 命令</span><span class="sxs-lookup"><span data-stu-id="51f8b-147">get-rtawindow Command</span></span>  
 <span data-ttu-id="51f8b-148">**使用方式**</span><span class="sxs-lookup"><span data-stu-id="51f8b-148">**Usage**</span></span>  
  
 <span data-ttu-id="51f8b-149">**bm.exe get rtawindow-檢視：\<檢視名稱 >-活動：\<活動名稱 >-Rta:\<RTA 名稱 > [-Server:\<伺服器 >] [-資料庫：\<資料庫 >]**</span><span class="sxs-lookup"><span data-stu-id="51f8b-149">**bm.exe get-rtawindow -View:\<view name> -Activity:\<activity name> -Rta:\<RTA name>[ -Server:\<server> ][ -Database:\<database> ]**</span></span>  
  
 <span data-ttu-id="51f8b-150">**參數**</span><span class="sxs-lookup"><span data-stu-id="51f8b-150">**Parameters**</span></span>  
  
|<span data-ttu-id="51f8b-151">參數</span><span class="sxs-lookup"><span data-stu-id="51f8b-151">Parameter</span></span>|<span data-ttu-id="51f8b-152">Description</span><span class="sxs-lookup"><span data-stu-id="51f8b-152">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="51f8b-153">檢視：\<檢視名稱 ></span><span class="sxs-lookup"><span data-stu-id="51f8b-153">View:\<view name></span></span>|<span data-ttu-id="51f8b-154">檢視名稱。</span><span class="sxs-lookup"><span data-stu-id="51f8b-154">The view name.</span></span>|  
|<span data-ttu-id="51f8b-155">活動：\<活動名稱 ></span><span class="sxs-lookup"><span data-stu-id="51f8b-155">Activity:\<activity name></span></span>|<span data-ttu-id="51f8b-156">活動名稱。</span><span class="sxs-lookup"><span data-stu-id="51f8b-156">The activity name.</span></span>|  
|<span data-ttu-id="51f8b-157">Rta:\<RTA 名稱 ></span><span class="sxs-lookup"><span data-stu-id="51f8b-157">Rta:\<RTA name></span></span>|<span data-ttu-id="51f8b-158">即時彙總名稱。</span><span class="sxs-lookup"><span data-stu-id="51f8b-158">The real-time aggregation name.</span></span>|  
|<span data-ttu-id="51f8b-159">伺服器：\<伺服器 ></span><span class="sxs-lookup"><span data-stu-id="51f8b-159">Server:\<server></span></span>|<span data-ttu-id="51f8b-160">選擇性： 活動所在的伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="51f8b-160">Optional: The name of the server on which the activity resides.</span></span> <span data-ttu-id="51f8b-161">伺服器和執行 bm.exe 的電腦必須位在相同網域中。</span><span class="sxs-lookup"><span data-stu-id="51f8b-161">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="51f8b-162">如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。</span><span class="sxs-lookup"><span data-stu-id="51f8b-162">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="51f8b-163">資料庫：\<資料庫 ></span><span class="sxs-lookup"><span data-stu-id="51f8b-163">Database:\<database></span></span>|<span data-ttu-id="51f8b-164">選擇性： 活動所在資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="51f8b-164">Optional: The name of the database on which the activity resides.</span></span> <span data-ttu-id="51f8b-165">如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。</span><span class="sxs-lookup"><span data-stu-id="51f8b-165">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="51f8b-166">顯示指定之即時彙總的持續時間。</span><span class="sxs-lookup"><span data-stu-id="51f8b-166">Displays the duration of the specified real-time aggregation.</span></span> <span data-ttu-id="51f8b-167">這個命令會傳回持續時間的長度以及測量持續時間所用的單位。</span><span class="sxs-lookup"><span data-stu-id="51f8b-167">The command returns the length of the duration and the units by which the duration is measured.</span></span>  
  
 <span data-ttu-id="51f8b-168">**範例**</span><span class="sxs-lookup"><span data-stu-id="51f8b-168">**Examples**</span></span>  
  
```  
bm.exe get-rtawindow -View:ManagerView -Activity:PO -Rta:Rta1  
bm.exe get-rtawindow -View:V1 -Activity:A2 -Rta:R3 -Server:S1 -Database:BamPI  
```  
  
## <a name="set-rtawindow-command"></a><span data-ttu-id="51f8b-169">set-rtawindow 命令</span><span class="sxs-lookup"><span data-stu-id="51f8b-169">set-rtawindow Command</span></span>  
 <span data-ttu-id="51f8b-170">**使用方式**</span><span class="sxs-lookup"><span data-stu-id="51f8b-170">**Usage**</span></span>  
  
 <span data-ttu-id="51f8b-171">**bm.exe 組 rtawindow-檢視：\<檢視名稱 >-活動：\<活動名稱 >-Name:\<RTA 名稱 >-TimeLength:\<整數數字 >-TimeUnit:Day &#124;小時 &#124;分鐘 [-Server:\<伺服器 >] [-Database:\<資料庫 >]**</span><span class="sxs-lookup"><span data-stu-id="51f8b-171">**bm.exe set-rtawindow -View:\<view name> -Activity:\<activity name> -Name:\<RTA name> -TimeLength:\<integer number>-TimeUnit:Day&#124;Hour&#124;Minute[ -Server:\<server> ][ -Database:\<database> ]**</span></span>  
  
 <span data-ttu-id="51f8b-172">**參數**</span><span class="sxs-lookup"><span data-stu-id="51f8b-172">**Parameters**</span></span>  
  
|<span data-ttu-id="51f8b-173">參數</span><span class="sxs-lookup"><span data-stu-id="51f8b-173">Parameter</span></span>|<span data-ttu-id="51f8b-174">Description</span><span class="sxs-lookup"><span data-stu-id="51f8b-174">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="51f8b-175">檢視：\<檢視名稱 ></span><span class="sxs-lookup"><span data-stu-id="51f8b-175">View:\<view name></span></span>|<span data-ttu-id="51f8b-176">檢視名稱。</span><span class="sxs-lookup"><span data-stu-id="51f8b-176">The view name.</span></span>|  
|<span data-ttu-id="51f8b-177">活動：\<活動名稱 ></span><span class="sxs-lookup"><span data-stu-id="51f8b-177">Activity:\<activity name></span></span>|<span data-ttu-id="51f8b-178">活動名稱。</span><span class="sxs-lookup"><span data-stu-id="51f8b-178">The activity name.</span></span>|  
|<span data-ttu-id="51f8b-179">名稱：\<RTA 名稱 ></span><span class="sxs-lookup"><span data-stu-id="51f8b-179">Name:\<RTA name></span></span>|<span data-ttu-id="51f8b-180">即時彙總名稱。</span><span class="sxs-lookup"><span data-stu-id="51f8b-180">The real-time aggregation name.</span></span>|  
|<span data-ttu-id="51f8b-181">TimeLength:\<整數數字 ></span><span class="sxs-lookup"><span data-stu-id="51f8b-181">TimeLength:\<integer number></span></span>|<span data-ttu-id="51f8b-182">即時彙總的持續時間。</span><span class="sxs-lookup"><span data-stu-id="51f8b-182">The duration for the real-time aggregation.</span></span>|  
|<span data-ttu-id="51f8b-183">TimeUnit:Month &#124; 天 &#124;小時 &#124;分鐘</span><span class="sxs-lookup"><span data-stu-id="51f8b-183">TimeUnit:Month&#124;Day&#124;Hour&#124;Minute</span></span>|<span data-ttu-id="51f8b-184">視窗持續時間的計量單位。</span><span class="sxs-lookup"><span data-stu-id="51f8b-184">The unit measure for the window duration.</span></span>|  
|<span data-ttu-id="51f8b-185">伺服器：\<伺服器 ></span><span class="sxs-lookup"><span data-stu-id="51f8b-185">Server:\<server></span></span>|<span data-ttu-id="51f8b-186">選擇性： 活動所在的伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="51f8b-186">Optional: The name of the server on which the activity resides.</span></span> <span data-ttu-id="51f8b-187">伺服器必須位在相同的網域執行 bm.exe 的電腦。</span><span class="sxs-lookup"><span data-stu-id="51f8b-187">The server must be in the same domain as the machine from which you are running bm.exe.</span></span> <span data-ttu-id="51f8b-188">如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。</span><span class="sxs-lookup"><span data-stu-id="51f8b-188">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="51f8b-189">資料庫：\<資料庫 ></span><span class="sxs-lookup"><span data-stu-id="51f8b-189">Database:\<database></span></span>|<span data-ttu-id="51f8b-190">選擇性： 活動所在資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="51f8b-190">Optional: The name of the database on which the activity resides.</span></span> <span data-ttu-id="51f8b-191">如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。</span><span class="sxs-lookup"><span data-stu-id="51f8b-191">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="51f8b-192">設定指定之即時彙總的持續時間。</span><span class="sxs-lookup"><span data-stu-id="51f8b-192">Sets the duration for the specified real-time aggregation.</span></span>  
  
 <span data-ttu-id="51f8b-193">**範例**</span><span class="sxs-lookup"><span data-stu-id="51f8b-193">**Examples**</span></span>  
  
```  
bm.exe set-rtawindow -View:V -Activity:A -Name:R -TimeLength:5 -TimeUnit:Minute  
bm.exe set-rtawindow -View:V -Activity:A -Name:R -TimeLength:1 -TimeUnit:Hour  
```  
  
## <a name="see-also"></a><span data-ttu-id="51f8b-194">另請參閱</span><span class="sxs-lookup"><span data-stu-id="51f8b-194">See Also</span></span>  
 [<span data-ttu-id="51f8b-195">BAM 管理公用程式</span><span class="sxs-lookup"><span data-stu-id="51f8b-195">BAM Management Utility</span></span>](../core/bam-management-utility.md)