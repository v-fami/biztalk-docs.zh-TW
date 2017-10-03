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
ms.openlocfilehash: 0b73129d884fea81bdb64609de5e95570275a344
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="alert-management-commands"></a><span data-ttu-id="7fa90-102">警示管理命令</span><span class="sxs-lookup"><span data-stu-id="7fa90-102">Alert Management Commands</span></span>
<span data-ttu-id="7fa90-103">BAM 管理公用程式的警示管理命令可讓您使用已部署的警示。</span><span class="sxs-lookup"><span data-stu-id="7fa90-103">The BAM management utility alert management commands allow you to work with deployed alerts.</span></span>  
  
-   <span data-ttu-id="7fa90-104">取得警示： 取得已部署的警示清單。</span><span class="sxs-lookup"><span data-stu-id="7fa90-104">get-alerts: Get a list of deployed alerts.</span></span>  
  
-   <span data-ttu-id="7fa90-105">移除警示： 移除警示。</span><span class="sxs-lookup"><span data-stu-id="7fa90-105">remove-alerts: Removes an alert.</span></span>  
  
-   <span data-ttu-id="7fa90-106">啟用警示： 可讓檢視上的警示。</span><span class="sxs-lookup"><span data-stu-id="7fa90-106">enable-alerts: Enables alerts on a view.</span></span>  
  
-   <span data-ttu-id="7fa90-107">停用警示： 停用檢視上的警示。</span><span class="sxs-lookup"><span data-stu-id="7fa90-107">disable-alerts: Disables alerts on a view.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7fa90-108">您可以藉由啟用任何 BM 公用程式命令的追蹤**-追蹤： 在 &#124; 關閉**切換參數。</span><span class="sxs-lookup"><span data-stu-id="7fa90-108">You can enable tracing on any BM utility command by including the **-Trace:on&#124;off** parameter switch.</span></span> <span data-ttu-id="7fa90-109">使用追蹤參數會覆寫組態檔中的追蹤設定。</span><span class="sxs-lookup"><span data-stu-id="7fa90-109">Using the Trace switch overrides the tracing settings in the configuration file.</span></span> <span data-ttu-id="7fa90-110">此參數可以搭配任何一般 BM 命令使用。</span><span class="sxs-lookup"><span data-stu-id="7fa90-110">The switch can be used in conjunction with any normal BM command.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7fa90-111">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="7fa90-111">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="get-alerts-command"></a><span data-ttu-id="7fa90-112">get-alerts 命令</span><span class="sxs-lookup"><span data-stu-id="7fa90-112">get-alerts Command</span></span>  
 <span data-ttu-id="7fa90-113">**使用方式**</span><span class="sxs-lookup"><span data-stu-id="7fa90-113">**Usage**</span></span>  
  
 <span data-ttu-id="7fa90-114">**bm.exe get 警示 [-檢視：\<檢視名稱 >] [-Server:\<伺服器 >] [-Database:\<資料庫 >]**</span><span class="sxs-lookup"><span data-stu-id="7fa90-114">**bm.exe get-alerts [ -View:\<view name> ][ -Server:\<server> ][ -Database:\<database> ]**</span></span>  
  
 <span data-ttu-id="7fa90-115">**參數**</span><span class="sxs-lookup"><span data-stu-id="7fa90-115">**Parameters**</span></span>  
  
|<span data-ttu-id="7fa90-116">參數</span><span class="sxs-lookup"><span data-stu-id="7fa90-116">Parameter</span></span>|<span data-ttu-id="7fa90-117">Description</span><span class="sxs-lookup"><span data-stu-id="7fa90-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7fa90-118">檢視：\<檢視名稱 ></span><span class="sxs-lookup"><span data-stu-id="7fa90-118">View:\<view name></span></span>|<span data-ttu-id="7fa90-119">警示清單取得來源的檢視名稱。</span><span class="sxs-lookup"><span data-stu-id="7fa90-119">The name of the view from which to get the list of alerts.</span></span>|  
|<span data-ttu-id="7fa90-120">伺服器：\<伺服器 ></span><span class="sxs-lookup"><span data-stu-id="7fa90-120">Server:\<server></span></span>|<span data-ttu-id="7fa90-121">選擇性： 檢視所在的伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="7fa90-121">Optional: The name of the server on which the view resides.</span></span> <span data-ttu-id="7fa90-122">伺服器和執行 bm.exe 的電腦必須位在相同網域中。</span><span class="sxs-lookup"><span data-stu-id="7fa90-122">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="7fa90-123">如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。</span><span class="sxs-lookup"><span data-stu-id="7fa90-123">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="7fa90-124">資料庫：\<資料庫 ></span><span class="sxs-lookup"><span data-stu-id="7fa90-124">Database:\<database></span></span>|<span data-ttu-id="7fa90-125">選擇性： 檢視所在的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="7fa90-125">Optional: The name of the database on which the view resides.</span></span> <span data-ttu-id="7fa90-126">如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。</span><span class="sxs-lookup"><span data-stu-id="7fa90-126">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="7fa90-127">列出執行此命令的電腦上已定義的警示。</span><span class="sxs-lookup"><span data-stu-id="7fa90-127">Lists the alerts defined on the computer on which the command is executed.</span></span>  
  
 <span data-ttu-id="7fa90-128">**範例**</span><span class="sxs-lookup"><span data-stu-id="7fa90-128">**Examples**</span></span>  
  
```  
bm.exe get-alerts -View:ManagerView  
bm.exe get-alerts -Server:MyServer -Database:MyPrimaryImport  
```  
  
## <a name="remove-alerts-command"></a><span data-ttu-id="7fa90-129">remove-alerts 命令</span><span class="sxs-lookup"><span data-stu-id="7fa90-129">remove-alerts Command</span></span>  
 <span data-ttu-id="7fa90-130">**使用方式**</span><span class="sxs-lookup"><span data-stu-id="7fa90-130">**Usage**</span></span>  
  
 <span data-ttu-id="7fa90-131">**bm.exe 移除警示的檢視：\<檢視名稱 > [-Server:\<伺服器 >] [-資料庫：\<資料庫 >]**</span><span class="sxs-lookup"><span data-stu-id="7fa90-131">**bm.exe remove-alerts -View:\<view name>[ -Server:\<server> ][ -Database:\<database> ]**</span></span>  
  
 <span data-ttu-id="7fa90-132">**參數**</span><span class="sxs-lookup"><span data-stu-id="7fa90-132">**Parameters**</span></span>  
  
|<span data-ttu-id="7fa90-133">參數</span><span class="sxs-lookup"><span data-stu-id="7fa90-133">Parameter</span></span>|<span data-ttu-id="7fa90-134">Description</span><span class="sxs-lookup"><span data-stu-id="7fa90-134">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7fa90-135">檢視：\<檢視名稱 ></span><span class="sxs-lookup"><span data-stu-id="7fa90-135">View:\<view name></span></span>|<span data-ttu-id="7fa90-136">要移除警示的檢視名稱。</span><span class="sxs-lookup"><span data-stu-id="7fa90-136">The name of the view from which to remove alerts.</span></span>|  
|<span data-ttu-id="7fa90-137">伺服器：\<伺服器 ></span><span class="sxs-lookup"><span data-stu-id="7fa90-137">Server:\<server></span></span>|<span data-ttu-id="7fa90-138">選擇性： 檢視所在的伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="7fa90-138">Optional: The name of the server on which the view resides.</span></span> <span data-ttu-id="7fa90-139">伺服器和執行 bm.exe 的電腦必須位在相同網域中。</span><span class="sxs-lookup"><span data-stu-id="7fa90-139">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="7fa90-140">如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。</span><span class="sxs-lookup"><span data-stu-id="7fa90-140">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="7fa90-141">資料庫：\<資料庫 ></span><span class="sxs-lookup"><span data-stu-id="7fa90-141">Database:\<database></span></span>|<span data-ttu-id="7fa90-142">選擇性： 檢視所在的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="7fa90-142">Optional: The name of the database on which the view resides.</span></span> <span data-ttu-id="7fa90-143">如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。</span><span class="sxs-lookup"><span data-stu-id="7fa90-143">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="7fa90-144">移除指定之檢視上的所有警示。</span><span class="sxs-lookup"><span data-stu-id="7fa90-144">Removes all alerts on the specified view.</span></span>  
  
 <span data-ttu-id="7fa90-145">**範例**</span><span class="sxs-lookup"><span data-stu-id="7fa90-145">**Examples**</span></span>  
  
```  
bm.exe remove-alerts -View:SalesManagerView  
bm.exe remove-alerts -View:Shipments -Server:Ship1  
```  
  
## <a name="enable-alerts-command"></a><span data-ttu-id="7fa90-146">enable-alerts 命令</span><span class="sxs-lookup"><span data-stu-id="7fa90-146">enable-alerts Command</span></span>  
 <span data-ttu-id="7fa90-147">**使用方式**</span><span class="sxs-lookup"><span data-stu-id="7fa90-147">**Usage**</span></span>  
  
 <span data-ttu-id="7fa90-148">**bm.exe 啟用警示的檢視：\<檢視名稱 > [-Server:\<伺服器 >] [-資料庫：\<資料庫 >]**</span><span class="sxs-lookup"><span data-stu-id="7fa90-148">**bm.exe enable-alerts -View:\<view name>[ -Server:\<server> ][ -Database:\<database> ]**</span></span>  
  
 <span data-ttu-id="7fa90-149">**參數**</span><span class="sxs-lookup"><span data-stu-id="7fa90-149">**Parameters**</span></span>  
  
|<span data-ttu-id="7fa90-150">參數</span><span class="sxs-lookup"><span data-stu-id="7fa90-150">Parameter</span></span>|<span data-ttu-id="7fa90-151">Description</span><span class="sxs-lookup"><span data-stu-id="7fa90-151">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7fa90-152">檢視：\<檢視名稱 ></span><span class="sxs-lookup"><span data-stu-id="7fa90-152">View:\<view name></span></span>|<span data-ttu-id="7fa90-153">要啟用警示的檢視名稱。</span><span class="sxs-lookup"><span data-stu-id="7fa90-153">The name of the view on which to enable alerts.</span></span>|  
|<span data-ttu-id="7fa90-154">伺服器：\<伺服器 ></span><span class="sxs-lookup"><span data-stu-id="7fa90-154">Server:\<server></span></span>|<span data-ttu-id="7fa90-155">選擇性： 檢視所在的伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="7fa90-155">Optional: The name of the server on which the view resides.</span></span> <span data-ttu-id="7fa90-156">伺服器和執行 bm.exe 的電腦必須位在相同網域中。</span><span class="sxs-lookup"><span data-stu-id="7fa90-156">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="7fa90-157">如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。</span><span class="sxs-lookup"><span data-stu-id="7fa90-157">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="7fa90-158">資料庫：\<資料庫 ></span><span class="sxs-lookup"><span data-stu-id="7fa90-158">Database:\<database></span></span>|<span data-ttu-id="7fa90-159">選擇性： 檢視所在的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="7fa90-159">Optional: The name of the database on which the view resides.</span></span> <span data-ttu-id="7fa90-160">如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。</span><span class="sxs-lookup"><span data-stu-id="7fa90-160">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="7fa90-161">啟用指定之檢視上的警示。</span><span class="sxs-lookup"><span data-stu-id="7fa90-161">Enables alerts on the specified view.</span></span>  
  
 <span data-ttu-id="7fa90-162">**範例**</span><span class="sxs-lookup"><span data-stu-id="7fa90-162">**Examples**</span></span>  
  
```  
bm.exe enable-alerts -View:SalesManagerView  
bm.exe enable-alerts -View:SalesManagerView -Server:s1 -Database:db2  
```  
  
## <a name="disable-alerts-command"></a><span data-ttu-id="7fa90-163">disable-alerts 命令</span><span class="sxs-lookup"><span data-stu-id="7fa90-163">disable-alerts Command</span></span>  
 <span data-ttu-id="7fa90-164">**使用方式**</span><span class="sxs-lookup"><span data-stu-id="7fa90-164">**Usage**</span></span>  
  
 <span data-ttu-id="7fa90-165">**bm.exe 停用警示的檢視：\<檢視名稱 > [-Server:\<伺服器 >] [-資料庫：\<資料庫 >]**</span><span class="sxs-lookup"><span data-stu-id="7fa90-165">**bm.exe disable-alerts -View:\<view name>[ -Server:\<server> ][ -Database:\<database> ]**</span></span>  
  
 <span data-ttu-id="7fa90-166">**參數**</span><span class="sxs-lookup"><span data-stu-id="7fa90-166">**Parameters**</span></span>  
  
|<span data-ttu-id="7fa90-167">參數</span><span class="sxs-lookup"><span data-stu-id="7fa90-167">Parameter</span></span>|<span data-ttu-id="7fa90-168">Description</span><span class="sxs-lookup"><span data-stu-id="7fa90-168">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7fa90-169">檢視：\<檢視名稱 ></span><span class="sxs-lookup"><span data-stu-id="7fa90-169">View:\<view name></span></span>|<span data-ttu-id="7fa90-170">要停用警示的檢視名稱。</span><span class="sxs-lookup"><span data-stu-id="7fa90-170">The name of the view on which to disable alerts.</span></span>|  
|<span data-ttu-id="7fa90-171">伺服器：\<伺服器 ></span><span class="sxs-lookup"><span data-stu-id="7fa90-171">Server:\<server></span></span>|<span data-ttu-id="7fa90-172">選擇性： 檢視所在的伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="7fa90-172">Optional: The name of the server on which the view resides.</span></span> <span data-ttu-id="7fa90-173">伺服器和執行 bm.exe 的電腦必須位在相同網域中。</span><span class="sxs-lookup"><span data-stu-id="7fa90-173">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="7fa90-174">如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。</span><span class="sxs-lookup"><span data-stu-id="7fa90-174">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="7fa90-175">資料庫：\<資料庫 ></span><span class="sxs-lookup"><span data-stu-id="7fa90-175">Database:\<database></span></span>|<span data-ttu-id="7fa90-176">選擇性： 檢視所在的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="7fa90-176">Optional: The name of the database on which the view resides.</span></span> <span data-ttu-id="7fa90-177">如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。</span><span class="sxs-lookup"><span data-stu-id="7fa90-177">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="7fa90-178">停用指定之檢視上的警示。</span><span class="sxs-lookup"><span data-stu-id="7fa90-178">Disables alerts on the specified view.</span></span>  
  
 <span data-ttu-id="7fa90-179">**範例**</span><span class="sxs-lookup"><span data-stu-id="7fa90-179">**Examples**</span></span>  
  
```  
bm.exe disable-alerts -View:SalesManagerView  
bm.exe disable-alerts -View:SalesManagerView -Server:s1 -Database:db2  
```  
  
## <a name="see-also"></a><span data-ttu-id="7fa90-180">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7fa90-180">See Also</span></span>  
 [<span data-ttu-id="7fa90-181">BAM 管理公用程式</span><span class="sxs-lookup"><span data-stu-id="7fa90-181">BAM Management Utility</span></span>](../core/bam-management-utility.md)