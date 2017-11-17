---
title: "使用者管理命令 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: feb12226-a4da-4fc5-93a1-aced239f60a9
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 79f908933015fa07e2ecf77a2e61d31227f73e62
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="user-management-commands"></a><span data-ttu-id="ef244-102">使用者管理命令</span><span class="sxs-lookup"><span data-stu-id="ef244-102">User Management Commands</span></span>
<span data-ttu-id="ef244-103">BAM 管理公用程式的警示使用者管理命令可讓您取得、新增及移除使用者。</span><span class="sxs-lookup"><span data-stu-id="ef244-103">The BAM Management utility alert user management commands allow you to get, add, and remove users.</span></span>  
  
-   <span data-ttu-id="ef244-104">取得帳戶： 取得所有使用者和群組可以存取指定的檢視的清單。</span><span class="sxs-lookup"><span data-stu-id="ef244-104">get-accounts: Gets a list of all users and groups that can access a specified view.</span></span>  
  
-   <span data-ttu-id="ef244-105">新增帳戶： 授與存取指定的使用者或群組的權限，以指定的檢視。</span><span class="sxs-lookup"><span data-stu-id="ef244-105">add-account: Grants access rights for the specified user or group to the specified view.</span></span>  
  
-   <span data-ttu-id="ef244-106">移除帳戶： 移除存取權限的使用者或群組，從指定的檢視。</span><span class="sxs-lookup"><span data-stu-id="ef244-106">remove-account: Removes access rights for a user or group from a specified view.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ef244-107">您可以藉由啟用任何 BM 公用程式命令的追蹤**-追蹤： 在 &#124; 關閉**切換參數。</span><span class="sxs-lookup"><span data-stu-id="ef244-107">You can enable tracing on any BM utility command by including the **-Trace:on&#124;off** parameter switch.</span></span> <span data-ttu-id="ef244-108">使用追蹤參數會覆寫組態檔中的追蹤設定。</span><span class="sxs-lookup"><span data-stu-id="ef244-108">Using the Trace switch overrides the tracing settings in the configuration file.</span></span> <span data-ttu-id="ef244-109">此參數可以搭配任何一般 BM 命令使用。</span><span class="sxs-lookup"><span data-stu-id="ef244-109">The switch can be used in conjunction with any normal BM command.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ef244-110">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="ef244-110">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="get-accounts-command"></a><span data-ttu-id="ef244-111">get-accounts 命令</span><span class="sxs-lookup"><span data-stu-id="ef244-111">get-accounts Command</span></span>  
 <span data-ttu-id="ef244-112">**使用方式**</span><span class="sxs-lookup"><span data-stu-id="ef244-112">**Usage**</span></span>  
  
 <span data-ttu-id="ef244-113">**bm.exe get 帳戶-檢視：\<檢視名稱 > [-Server:\<伺服器 >] [-Database:\<資料庫 >]**</span><span class="sxs-lookup"><span data-stu-id="ef244-113">**bm.exe get-accounts -View:\<view name>[ -Server:\<server> ][ -Database:\<database> ]**</span></span>  
  
 <span data-ttu-id="ef244-114">**參數**</span><span class="sxs-lookup"><span data-stu-id="ef244-114">**Parameters**</span></span>  
  
|<span data-ttu-id="ef244-115">參數</span><span class="sxs-lookup"><span data-stu-id="ef244-115">Parameter</span></span>|<span data-ttu-id="ef244-116">Description</span><span class="sxs-lookup"><span data-stu-id="ef244-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ef244-117">檢視：\<檢視名稱 ></span><span class="sxs-lookup"><span data-stu-id="ef244-117">View:\<view name></span></span>|<span data-ttu-id="ef244-118">要列出其帳戶的檢視名稱。</span><span class="sxs-lookup"><span data-stu-id="ef244-118">The name of the view for which to list accounts.</span></span>|  
|<span data-ttu-id="ef244-119">伺服器：\<伺服器 ></span><span class="sxs-lookup"><span data-stu-id="ef244-119">Server:\<server></span></span>|<span data-ttu-id="ef244-120">選擇性： 要從中擷取帳戶的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="ef244-120">Optional: The name of the server from which to retrieve the accounts.</span></span> <span data-ttu-id="ef244-121">伺服器和執行 bm.exe 的電腦必須位在相同網域中。</span><span class="sxs-lookup"><span data-stu-id="ef244-121">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="ef244-122">如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。</span><span class="sxs-lookup"><span data-stu-id="ef244-122">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="ef244-123">資料庫：\<資料庫 ></span><span class="sxs-lookup"><span data-stu-id="ef244-123">Database:\<database></span></span>|<span data-ttu-id="ef244-124">選擇性： 要從中擷取帳戶的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="ef244-124">Optional: The name of the database from which to retrieve the accounts.</span></span> <span data-ttu-id="ef244-125">如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。</span><span class="sxs-lookup"><span data-stu-id="ef244-125">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="ef244-126">列出可存取特定檢視的所有使用者和群組。</span><span class="sxs-lookup"><span data-stu-id="ef244-126">Lists all users and groups that can access the specified view.</span></span>  
  
 <span data-ttu-id="ef244-127">**範例**</span><span class="sxs-lookup"><span data-stu-id="ef244-127">**Examples**</span></span>  
  
 `bm.exe get-accounts -View:PurchaseOrder`  
  
 `bm.exe get-accounts -View:ShipmentOrder -Server:Ship -Database:ShipDatabase`  
  
## <a name="add-account-command"></a><span data-ttu-id="ef244-128">add-account 命令</span><span class="sxs-lookup"><span data-stu-id="ef244-128">add-account Command</span></span>  
 <span data-ttu-id="ef244-129">**使用方式**</span><span class="sxs-lookup"><span data-stu-id="ef244-129">**Usage**</span></span>  
  
 <span data-ttu-id="ef244-130">**bm.exe 新增帳戶-AccountName:\<帳戶名稱 >-檢視：\<檢視名稱 > [-Server:\<伺服器 >] [-Database:\<資料庫 >]**</span><span class="sxs-lookup"><span data-stu-id="ef244-130">**bm.exe add-account -AccountName:\<account name> -View:\<view name>[ -Server:\<server> ][ -Database:\<database> ]**</span></span>  
  
 <span data-ttu-id="ef244-131">**參數**</span><span class="sxs-lookup"><span data-stu-id="ef244-131">**Parameters**</span></span>  
  
|<span data-ttu-id="ef244-132">參數</span><span class="sxs-lookup"><span data-stu-id="ef244-132">Parameter</span></span>|<span data-ttu-id="ef244-133">Description</span><span class="sxs-lookup"><span data-stu-id="ef244-133">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ef244-134">AccountName:<帳戶名稱</span><span class="sxs-lookup"><span data-stu-id="ef244-134">AccountName:<account name</span></span>|<span data-ttu-id="ef244-135">要對其授與權限的帳戶名稱。</span><span class="sxs-lookup"><span data-stu-id="ef244-135">The name of the account to which rights are granted.</span></span>|  
|<span data-ttu-id="ef244-136">檢視：\<檢視名稱 ></span><span class="sxs-lookup"><span data-stu-id="ef244-136">View:\<view name></span></span>|<span data-ttu-id="ef244-137">要對其授與權限的檢視名稱。</span><span class="sxs-lookup"><span data-stu-id="ef244-137">The name of the view to which rights are granted.</span></span>|  
|<span data-ttu-id="ef244-138">伺服器：\<伺服器 ></span><span class="sxs-lookup"><span data-stu-id="ef244-138">Server:\<server></span></span>|<span data-ttu-id="ef244-139">選擇性： 檢視所在的伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="ef244-139">Optional: The name of the server on which the view resides.</span></span> <span data-ttu-id="ef244-140">伺服器和執行 bm.exe 的電腦必須位在相同網域中。</span><span class="sxs-lookup"><span data-stu-id="ef244-140">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="ef244-141">如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。</span><span class="sxs-lookup"><span data-stu-id="ef244-141">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="ef244-142">資料庫：\<資料庫 ></span><span class="sxs-lookup"><span data-stu-id="ef244-142">Database:\<database></span></span>|<span data-ttu-id="ef244-143">選擇性： 檢視所在的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="ef244-143">Optional: The name of the database on which the view resides.</span></span> <span data-ttu-id="ef244-144">如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。</span><span class="sxs-lookup"><span data-stu-id="ef244-144">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="ef244-145">授與指定的使用者或群組存取特定檢視的權限。</span><span class="sxs-lookup"><span data-stu-id="ef244-145">Grants the specified user or group access rights to the specified view.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ef244-146">如果您使用即時彙總 (Rta)，使用者會新增與**新增帳戶**命令不會自動授予 SQL Server 登入權限。</span><span class="sxs-lookup"><span data-stu-id="ef244-146">If you are using Real Time Aggregations (RTAs), users added with **add-account** command are not automatically granted logon rights to SQL Server.</span></span> <span data-ttu-id="ef244-147">如果您使用 RTA，請考慮建立一個 Windows 使用者群組，並在該群組中加入所有需要查看 RTA 檢視的使用者。</span><span class="sxs-lookup"><span data-stu-id="ef244-147">If you are using RTAs, consider establishing a Windows user group that contains all of the users that need to see views of the RTAs.</span></span> <span data-ttu-id="ef244-148">然後，授與該群組對裝載 BAM 主要匯入資料庫的 SQL 伺服器擁有明確的 SQL Server 登入權限。</span><span class="sxs-lookup"><span data-stu-id="ef244-148">Grant that group explicit SQL Server logon rights on the SQL server hosting the BAM Primary Import databases.</span></span>  
  
 <span data-ttu-id="ef244-149">**範例**</span><span class="sxs-lookup"><span data-stu-id="ef244-149">**Examples**</span></span>  
  
```  
bm.exe add-account -AccountName:john -View:PurchaseOrder  
bm.exe add-account -AccountName:Agents -View:PO -Server:Srv1 -Database:Db2  
```  
  
## <a name="remove-account-command"></a><span data-ttu-id="ef244-150">remove-account 命令</span><span class="sxs-lookup"><span data-stu-id="ef244-150">remove-account Command</span></span>  
 <span data-ttu-id="ef244-151">**使用方式**</span><span class="sxs-lookup"><span data-stu-id="ef244-151">**Usage**</span></span>  
  
 <span data-ttu-id="ef244-152">**bm.exe 移除帳戶-AccountName:\<帳戶名稱 >-檢視：\<檢視名稱 > [-Server:\<伺服器 >] [-Database:\<資料庫 >]**</span><span class="sxs-lookup"><span data-stu-id="ef244-152">**bm.exe remove-account -AccountName:\<account name> -View:\<view name>[ -Server:\<server> ][ -Database:\<database> ]**</span></span>  
  
 <span data-ttu-id="ef244-153">**參數**</span><span class="sxs-lookup"><span data-stu-id="ef244-153">**Parameters**</span></span>  
  
|<span data-ttu-id="ef244-154">參數</span><span class="sxs-lookup"><span data-stu-id="ef244-154">Parameter</span></span>|<span data-ttu-id="ef244-155">Description</span><span class="sxs-lookup"><span data-stu-id="ef244-155">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ef244-156">AccountName:\<帳戶名稱 ></span><span class="sxs-lookup"><span data-stu-id="ef244-156">AccountName:\<account name></span></span>|<span data-ttu-id="ef244-157">要移除其檢視存取權限的帳戶名稱。</span><span class="sxs-lookup"><span data-stu-id="ef244-157">The name of the account from which to remove rights to the view.</span></span>|  
|<span data-ttu-id="ef244-158">檢視：\<檢視名稱 ></span><span class="sxs-lookup"><span data-stu-id="ef244-158">View:\<view name></span></span>|<span data-ttu-id="ef244-159">要對其移除權限的檢視名稱。</span><span class="sxs-lookup"><span data-stu-id="ef244-159">The name of the view to which rights are removed.</span></span>|  
|<span data-ttu-id="ef244-160">伺服器：\<伺服器 ></span><span class="sxs-lookup"><span data-stu-id="ef244-160">Server:\<server></span></span>|<span data-ttu-id="ef244-161">選擇性： 檢視所在的伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="ef244-161">Optional: The name of the server on which the view resides.</span></span> <span data-ttu-id="ef244-162">伺服器和執行 bm.exe 的電腦必須位在相同網域中。</span><span class="sxs-lookup"><span data-stu-id="ef244-162">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="ef244-163">如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。</span><span class="sxs-lookup"><span data-stu-id="ef244-163">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="ef244-164">資料庫：\<資料庫 ></span><span class="sxs-lookup"><span data-stu-id="ef244-164">Database:\<database></span></span>|<span data-ttu-id="ef244-165">選擇性： 檢視所在的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="ef244-165">Optional: The name of the database on which the view resides.</span></span> <span data-ttu-id="ef244-166">如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。</span><span class="sxs-lookup"><span data-stu-id="ef244-166">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="ef244-167">移除使用者或群組對特定檢視的存取權。</span><span class="sxs-lookup"><span data-stu-id="ef244-167">Removes access rights for a user or group from a specified view.</span></span> <span data-ttu-id="ef244-168">從檢視移除帳戶會從指定檢視所定義的警示移除該帳戶及其所有成員。</span><span class="sxs-lookup"><span data-stu-id="ef244-168">Removing an account from a view removes that account and all of its members from alerts defined for the specified view.</span></span> <span data-ttu-id="ef244-169">如果該帳戶是特定警示的唯一擁有者，則目前的使用者 (admin) 將成為這些警示的新擁有者。</span><span class="sxs-lookup"><span data-stu-id="ef244-169">If that account is the sole owner of an alert, the current user (admin) becomes the new owner of the alert.</span></span>  
  
 <span data-ttu-id="ef244-170">**範例**</span><span class="sxs-lookup"><span data-stu-id="ef244-170">**Examples**</span></span>  
  
```  
bm.exe remove-account -AccountName:john -View:PurchaseOrder  
bm.exe remove-account -AccountName:Agents -View:PO -Server:Srv1 -Database:Db2  
```  
  
## <a name="see-also"></a><span data-ttu-id="ef244-171">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ef244-171">See Also</span></span>  
 [<span data-ttu-id="ef244-172">BAM 管理公用程式</span><span class="sxs-lookup"><span data-stu-id="ef244-172">BAM Management Utility</span></span>](../core/bam-management-utility.md)