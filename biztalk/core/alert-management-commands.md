---
title: "警示管理命令 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a96d8de7-a918-4737-aa35-4e1abf6bb08f
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f419e7a0019287383080c319961b8a3831d27bb4
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="alert-management-commands"></a><span data-ttu-id="bd479-102">警示管理命令</span><span class="sxs-lookup"><span data-stu-id="bd479-102">Alert Management Commands</span></span>
<span data-ttu-id="bd479-103">BAM 管理公用程式的警示管理命令可讓您使用已部署的警示。</span><span class="sxs-lookup"><span data-stu-id="bd479-103">The BAM management utility alert management commands allow you to work with deployed alerts.</span></span>  
  
-   <span data-ttu-id="bd479-104">取得警示： 取得已部署的警示清單。</span><span class="sxs-lookup"><span data-stu-id="bd479-104">get-alerts: Get a list of deployed alerts.</span></span>  
  
-   <span data-ttu-id="bd479-105">移除警示： 移除警示。</span><span class="sxs-lookup"><span data-stu-id="bd479-105">remove-alerts: Removes an alert.</span></span>  
  
-   <span data-ttu-id="bd479-106">啟用警示： 可讓檢視上的警示。</span><span class="sxs-lookup"><span data-stu-id="bd479-106">enable-alerts: Enables alerts on a view.</span></span>  
  
-   <span data-ttu-id="bd479-107">停用警示： 停用檢視上的警示。</span><span class="sxs-lookup"><span data-stu-id="bd479-107">disable-alerts: Disables alerts on a view.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bd479-108">您可以藉由啟用任何 BM 公用程式命令的追蹤**-追蹤： 在 &#124; 關閉**切換參數。</span><span class="sxs-lookup"><span data-stu-id="bd479-108">You can enable tracing on any BM utility command by including the **-Trace:on&#124;off** parameter switch.</span></span> <span data-ttu-id="bd479-109">使用追蹤參數會覆寫組態檔中的追蹤設定。</span><span class="sxs-lookup"><span data-stu-id="bd479-109">Using the Trace switch overrides the tracing settings in the configuration file.</span></span> <span data-ttu-id="bd479-110">此參數可以搭配任何一般 BM 命令使用。</span><span class="sxs-lookup"><span data-stu-id="bd479-110">The switch can be used in conjunction with any normal BM command.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bd479-111">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="bd479-111">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="get-alerts-command"></a><span data-ttu-id="bd479-112">get-alerts 命令</span><span class="sxs-lookup"><span data-stu-id="bd479-112">get-alerts Command</span></span>  
 <span data-ttu-id="bd479-113">**使用方式**</span><span class="sxs-lookup"><span data-stu-id="bd479-113">**Usage**</span></span>  
  
 <span data-ttu-id="bd479-114">**bm.exe get 警示 [-檢視：\<檢視名稱\>] [-Server:\<伺服器\>] [-Database:\<資料庫\>]**</span><span class="sxs-lookup"><span data-stu-id="bd479-114">**bm.exe get-alerts [ -View:\<view name\> ][ -Server:\<server\> ][ -Database:\<database\> ]**</span></span>  
  
 <span data-ttu-id="bd479-115">**參數**</span><span class="sxs-lookup"><span data-stu-id="bd479-115">**Parameters**</span></span>  
  
|<span data-ttu-id="bd479-116">參數</span><span class="sxs-lookup"><span data-stu-id="bd479-116">Parameter</span></span>|<span data-ttu-id="bd479-117">Description</span><span class="sxs-lookup"><span data-stu-id="bd479-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bd479-118">檢視：\<檢視表名稱\></span><span class="sxs-lookup"><span data-stu-id="bd479-118">View:\<view name\></span></span>|<span data-ttu-id="bd479-119">警示清單取得來源的檢視名稱。</span><span class="sxs-lookup"><span data-stu-id="bd479-119">The name of the view from which to get the list of alerts.</span></span>|  
|<span data-ttu-id="bd479-120">伺服器：\<伺服器\></span><span class="sxs-lookup"><span data-stu-id="bd479-120">Server:\<server\></span></span>|<span data-ttu-id="bd479-121">選擇性： 檢視所在的伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="bd479-121">Optional: The name of the server on which the view resides.</span></span> <span data-ttu-id="bd479-122">伺服器和執行 bm.exe 的電腦必須位在相同網域中。</span><span class="sxs-lookup"><span data-stu-id="bd479-122">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="bd479-123">如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。</span><span class="sxs-lookup"><span data-stu-id="bd479-123">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="bd479-124">資料庫：\<資料庫\></span><span class="sxs-lookup"><span data-stu-id="bd479-124">Database:\<database\></span></span>|<span data-ttu-id="bd479-125">選擇性： 檢視所在的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="bd479-125">Optional: The name of the database on which the view resides.</span></span> <span data-ttu-id="bd479-126">如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。</span><span class="sxs-lookup"><span data-stu-id="bd479-126">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="bd479-127">列出執行此命令的電腦上已定義的警示。</span><span class="sxs-lookup"><span data-stu-id="bd479-127">Lists the alerts defined on the computer on which the command is executed.</span></span>  
  
 <span data-ttu-id="bd479-128">**範例**</span><span class="sxs-lookup"><span data-stu-id="bd479-128">**Examples**</span></span>  
  
```  
bm.exe get-alerts -View:ManagerView  
bm.exe get-alerts -Server:MyServer -Database:MyPrimaryImport  
```  
  
## <a name="remove-alerts-command"></a><span data-ttu-id="bd479-129">remove-alerts 命令</span><span class="sxs-lookup"><span data-stu-id="bd479-129">remove-alerts Command</span></span>  
 <span data-ttu-id="bd479-130">**使用方式**</span><span class="sxs-lookup"><span data-stu-id="bd479-130">**Usage**</span></span>  
  
 <span data-ttu-id="bd479-131">**bm.exe 移除警示的檢視：\<檢視名稱\>[-Server:\<伺服器\>] [-資料庫：\<資料庫\>]**</span><span class="sxs-lookup"><span data-stu-id="bd479-131">**bm.exe remove-alerts -View:\<view name\>[ -Server:\<server\> ][ -Database:\<database\> ]**</span></span>  
  
 <span data-ttu-id="bd479-132">**參數**</span><span class="sxs-lookup"><span data-stu-id="bd479-132">**Parameters**</span></span>  
  
|<span data-ttu-id="bd479-133">參數</span><span class="sxs-lookup"><span data-stu-id="bd479-133">Parameter</span></span>|<span data-ttu-id="bd479-134">Description</span><span class="sxs-lookup"><span data-stu-id="bd479-134">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bd479-135">檢視：\<檢視表名稱\></span><span class="sxs-lookup"><span data-stu-id="bd479-135">View:\<view name\></span></span>|<span data-ttu-id="bd479-136">要移除警示的檢視名稱。</span><span class="sxs-lookup"><span data-stu-id="bd479-136">The name of the view from which to remove alerts.</span></span>|  
|<span data-ttu-id="bd479-137">伺服器：\<伺服器\></span><span class="sxs-lookup"><span data-stu-id="bd479-137">Server:\<server\></span></span>|<span data-ttu-id="bd479-138">選擇性： 檢視所在的伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="bd479-138">Optional: The name of the server on which the view resides.</span></span> <span data-ttu-id="bd479-139">伺服器和執行 bm.exe 的電腦必須位在相同網域中。</span><span class="sxs-lookup"><span data-stu-id="bd479-139">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="bd479-140">如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。</span><span class="sxs-lookup"><span data-stu-id="bd479-140">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="bd479-141">資料庫：\<資料庫\></span><span class="sxs-lookup"><span data-stu-id="bd479-141">Database:\<database\></span></span>|<span data-ttu-id="bd479-142">選擇性： 檢視所在的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="bd479-142">Optional: The name of the database on which the view resides.</span></span> <span data-ttu-id="bd479-143">如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。</span><span class="sxs-lookup"><span data-stu-id="bd479-143">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="bd479-144">移除指定之檢視上的所有警示。</span><span class="sxs-lookup"><span data-stu-id="bd479-144">Removes all alerts on the specified view.</span></span>  
  
 <span data-ttu-id="bd479-145">**範例**</span><span class="sxs-lookup"><span data-stu-id="bd479-145">**Examples**</span></span>  
  
```  
bm.exe remove-alerts -View:SalesManagerView  
bm.exe remove-alerts -View:Shipments -Server:Ship1  
```  
  
## <a name="enable-alerts-command"></a><span data-ttu-id="bd479-146">enable-alerts 命令</span><span class="sxs-lookup"><span data-stu-id="bd479-146">enable-alerts Command</span></span>  
 <span data-ttu-id="bd479-147">**使用方式**</span><span class="sxs-lookup"><span data-stu-id="bd479-147">**Usage**</span></span>  
  
 <span data-ttu-id="bd479-148">**bm.exe 啟用警示的檢視：\<檢視名稱\>[-Server:\<伺服器\>] [-資料庫：\<資料庫\>]**</span><span class="sxs-lookup"><span data-stu-id="bd479-148">**bm.exe enable-alerts -View:\<view name\>[ -Server:\<server\> ][ -Database:\<database\> ]**</span></span>  
  
 <span data-ttu-id="bd479-149">**參數**</span><span class="sxs-lookup"><span data-stu-id="bd479-149">**Parameters**</span></span>  
  
|<span data-ttu-id="bd479-150">參數</span><span class="sxs-lookup"><span data-stu-id="bd479-150">Parameter</span></span>|<span data-ttu-id="bd479-151">Description</span><span class="sxs-lookup"><span data-stu-id="bd479-151">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bd479-152">檢視：\<檢視表名稱\></span><span class="sxs-lookup"><span data-stu-id="bd479-152">View:\<view name\></span></span>|<span data-ttu-id="bd479-153">要啟用警示的檢視名稱。</span><span class="sxs-lookup"><span data-stu-id="bd479-153">The name of the view on which to enable alerts.</span></span>|  
|<span data-ttu-id="bd479-154">伺服器：\<伺服器\></span><span class="sxs-lookup"><span data-stu-id="bd479-154">Server:\<server\></span></span>|<span data-ttu-id="bd479-155">選擇性： 檢視所在的伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="bd479-155">Optional: The name of the server on which the view resides.</span></span> <span data-ttu-id="bd479-156">伺服器和執行 bm.exe 的電腦必須位在相同網域中。</span><span class="sxs-lookup"><span data-stu-id="bd479-156">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="bd479-157">如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。</span><span class="sxs-lookup"><span data-stu-id="bd479-157">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="bd479-158">資料庫：\<資料庫\></span><span class="sxs-lookup"><span data-stu-id="bd479-158">Database:\<database\></span></span>|<span data-ttu-id="bd479-159">選擇性： 檢視所在的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="bd479-159">Optional: The name of the database on which the view resides.</span></span> <span data-ttu-id="bd479-160">如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。</span><span class="sxs-lookup"><span data-stu-id="bd479-160">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="bd479-161">啟用指定之檢視上的警示。</span><span class="sxs-lookup"><span data-stu-id="bd479-161">Enables alerts on the specified view.</span></span>  
  
 <span data-ttu-id="bd479-162">**範例**</span><span class="sxs-lookup"><span data-stu-id="bd479-162">**Examples**</span></span>  
  
```  
bm.exe enable-alerts -View:SalesManagerView  
bm.exe enable-alerts -View:SalesManagerView -Server:s1 -Database:db2  
```  
  
## <a name="disable-alerts-command"></a><span data-ttu-id="bd479-163">disable-alerts 命令</span><span class="sxs-lookup"><span data-stu-id="bd479-163">disable-alerts Command</span></span>  
 <span data-ttu-id="bd479-164">**使用方式**</span><span class="sxs-lookup"><span data-stu-id="bd479-164">**Usage**</span></span>  
  
 <span data-ttu-id="bd479-165">**bm.exe 停用警示的檢視：\<檢視名稱\>[-Server:\<伺服器\>] [-資料庫：\<資料庫\>]**</span><span class="sxs-lookup"><span data-stu-id="bd479-165">**bm.exe disable-alerts -View:\<view name\>[ -Server:\<server\> ][ -Database:\<database\> ]**</span></span>  
  
 <span data-ttu-id="bd479-166">**參數**</span><span class="sxs-lookup"><span data-stu-id="bd479-166">**Parameters**</span></span>  
  
|<span data-ttu-id="bd479-167">參數</span><span class="sxs-lookup"><span data-stu-id="bd479-167">Parameter</span></span>|<span data-ttu-id="bd479-168">Description</span><span class="sxs-lookup"><span data-stu-id="bd479-168">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bd479-169">檢視：\<檢視表名稱\></span><span class="sxs-lookup"><span data-stu-id="bd479-169">View:\<view name\></span></span>|<span data-ttu-id="bd479-170">要停用警示的檢視名稱。</span><span class="sxs-lookup"><span data-stu-id="bd479-170">The name of the view on which to disable alerts.</span></span>|  
|<span data-ttu-id="bd479-171">伺服器：\<伺服器\></span><span class="sxs-lookup"><span data-stu-id="bd479-171">Server:\<server\></span></span>|<span data-ttu-id="bd479-172">選擇性： 檢視所在的伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="bd479-172">Optional: The name of the server on which the view resides.</span></span> <span data-ttu-id="bd479-173">伺服器和執行 bm.exe 的電腦必須位在相同網域中。</span><span class="sxs-lookup"><span data-stu-id="bd479-173">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="bd479-174">如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。</span><span class="sxs-lookup"><span data-stu-id="bd479-174">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="bd479-175">資料庫：\<資料庫\></span><span class="sxs-lookup"><span data-stu-id="bd479-175">Database:\<database\></span></span>|<span data-ttu-id="bd479-176">選擇性： 檢視所在的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="bd479-176">Optional: The name of the database on which the view resides.</span></span> <span data-ttu-id="bd479-177">如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。</span><span class="sxs-lookup"><span data-stu-id="bd479-177">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="bd479-178">停用指定之檢視上的警示。</span><span class="sxs-lookup"><span data-stu-id="bd479-178">Disables alerts on the specified view.</span></span>  
  
 <span data-ttu-id="bd479-179">**範例**</span><span class="sxs-lookup"><span data-stu-id="bd479-179">**Examples**</span></span>  
  
```  
bm.exe disable-alerts -View:SalesManagerView  
bm.exe disable-alerts -View:SalesManagerView -Server:s1 -Database:db2  
```  
  
## <a name="see-also"></a><span data-ttu-id="bd479-180">請參閱</span><span class="sxs-lookup"><span data-stu-id="bd479-180">See Also</span></span>  
 [<span data-ttu-id="bd479-181">BAM 管理公用程式</span><span class="sxs-lookup"><span data-stu-id="bd479-181">BAM Management Utility</span></span>](../core/bam-management-utility.md)