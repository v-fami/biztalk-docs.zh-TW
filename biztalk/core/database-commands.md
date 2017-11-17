---
title: "資料庫命令 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 60c54131-0793-45a9-822a-554cd4fc05a2
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a7ec623c49c90fc0fddcbab7b6ee9b4e7ea0ef58
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="database-commands"></a><span data-ttu-id="b284d-102">資料庫命令</span><span class="sxs-lookup"><span data-stu-id="b284d-102">Database Commands</span></span>
<span data-ttu-id="b284d-103">BAM 管理公用程式資料庫命令可讓您使用 BAM 資料庫：</span><span class="sxs-lookup"><span data-stu-id="b284d-103">The BAM Management utility database commands allow you to work with the BAM databases:</span></span>  
  
-   <span data-ttu-id="b284d-104">安裝程式資料庫： 建立 BAM 專屬資料庫。</span><span class="sxs-lookup"><span data-stu-id="b284d-104">setup-databases: Creates the BAM-specific databases.</span></span>  
  
-   <span data-ttu-id="b284d-105">移轉 sql： 移轉您的 BAM 資料庫：</span><span class="sxs-lookup"><span data-stu-id="b284d-105">migrate-sql: Migrates your BAM databases from:</span></span>  
  
    -   <span data-ttu-id="b284d-106">Microsoft SQL server 2008 的 Microsoft SQL Server 2000</span><span class="sxs-lookup"><span data-stu-id="b284d-106">Microsoft SQL Server 2000 to Microsoft SQL Server 2008</span></span>  
  
    -   <span data-ttu-id="b284d-107">Microsoft SQL server 2008 的 Microsoft SQL Server 2005</span><span class="sxs-lookup"><span data-stu-id="b284d-107">Microsoft SQL Server 2005 to Microsoft SQL Server 2008</span></span>  
  
-   <span data-ttu-id="b284d-108">啟用參考： 啟用分散式 BAM 主要匯入資料庫的參考。</span><span class="sxs-lookup"><span data-stu-id="b284d-108">enable-reference: Enables a reference to a distributed BAM Primary Import database.</span></span>  
  
-   <span data-ttu-id="b284d-109">取得參考： 取得一份分散式 BAM 主要匯入資料庫的參考。</span><span class="sxs-lookup"><span data-stu-id="b284d-109">get-references: Gets a list of references to distributed BAM Primary Import databases.</span></span>  
  
-   <span data-ttu-id="b284d-110">停用參考： 停用 BAM 主要匯入資料庫的參考。</span><span class="sxs-lookup"><span data-stu-id="b284d-110">disable-reference: Disables a reference to a BAM Primary Import database.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b284d-111">您可以藉由啟用任何 BM 公用程式命令的追蹤**-追蹤： 在 &#124; 關閉**切換參數。</span><span class="sxs-lookup"><span data-stu-id="b284d-111">You can enable tracing on any BM utility command by including the **-Trace:on&#124;off** parameter switch.</span></span> <span data-ttu-id="b284d-112">使用追蹤參數會覆寫組態檔中的追蹤設定。</span><span class="sxs-lookup"><span data-stu-id="b284d-112">Using the Trace switch overrides the tracing settings in the configuration file.</span></span> <span data-ttu-id="b284d-113">此參數可以搭配任何一般 BM 命令使用。</span><span class="sxs-lookup"><span data-stu-id="b284d-113">The switch can be used in conjunction with any normal BM command.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b284d-114">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="b284d-114">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="setup-databases-command"></a><span data-ttu-id="b284d-115">setup-databases 命令</span><span class="sxs-lookup"><span data-stu-id="b284d-115">setup-databases Command</span></span>  
 <span data-ttu-id="b284d-116">**使用方式**</span><span class="sxs-lookup"><span data-stu-id="b284d-116">**Usage**</span></span>  
  
 <span data-ttu-id="b284d-117">**bm.exe 安裝程式資料庫 ConfigFile:\<組態檔 > [-NSUser:\<通知服務使用者名稱 >] [-NSUserPassword:\<通知服務使用者密碼 >]**</span><span class="sxs-lookup"><span data-stu-id="b284d-117">**bm.exe setup-databases-ConfigFile:\<configuration file>[ -NSUser:\<notifications service user name> ][ -NSUserPassword:\<notifications service user password> ]**</span></span>  
  
 <span data-ttu-id="b284d-118">**參數**</span><span class="sxs-lookup"><span data-stu-id="b284d-118">**Parameters**</span></span>  
  
|<span data-ttu-id="b284d-119">參數</span><span class="sxs-lookup"><span data-stu-id="b284d-119">Parameter</span></span>|<span data-ttu-id="b284d-120">Description</span><span class="sxs-lookup"><span data-stu-id="b284d-120">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b284d-121">ConfigFile:\<組態檔 ></span><span class="sxs-lookup"><span data-stu-id="b284d-121">ConfigFile:\<configuration file></span></span>|<span data-ttu-id="b284d-122">建立資料庫所依據的 BAM 組態檔。</span><span class="sxs-lookup"><span data-stu-id="b284d-122">The BAM configuration file from which to create the database.</span></span>|  
|<span data-ttu-id="b284d-123">NSUser:\<通知服務使用者名稱 ></span><span class="sxs-lookup"><span data-stu-id="b284d-123">NSUser:\<notifications service user name></span></span>|<span data-ttu-id="b284d-124">選擇性： 具有建立資料庫的權限之通知服務使用者的使用者識別碼。</span><span class="sxs-lookup"><span data-stu-id="b284d-124">Optional: The user ID of a notifications services user with permissions to create databases.</span></span>|  
|<span data-ttu-id="b284d-125">NSUserPassword</span><span class="sxs-lookup"><span data-stu-id="b284d-125">NSUserPassword</span></span>|<span data-ttu-id="b284d-126">選擇性： 指定之通知服務使用者的密碼。</span><span class="sxs-lookup"><span data-stu-id="b284d-126">Optional: The password for the specified notifications services user.</span></span>|  
  
 <span data-ttu-id="b284d-127">如果組態檔中描述的資料庫 (BAM 主要匯入、BAM 星狀結構描述、BAM 封存、BAM 分析和警示) 不存在，會建立所有資料庫。</span><span class="sxs-lookup"><span data-stu-id="b284d-127">Creates the databases described in the configuration file (BAM Primary Import, BAM Star Schema, BAM Archive, BAM Analysis, and alerts) if they do not already exist.</span></span> <span data-ttu-id="b284d-128">資料庫建立之後，命令即建立關聯的 BAM 中繼資料資料表和預存程序。</span><span class="sxs-lookup"><span data-stu-id="b284d-128">Once the databases are created, the command creates the associated BAM metadata tables and stored procedures.</span></span>  
  
 <span data-ttu-id="b284d-129">如果設定 BAM 警示，則 NSUser 和 NSUserPassword 皆為必要參數。</span><span class="sxs-lookup"><span data-stu-id="b284d-129">The NSUser and NSUserPassword parameters are required if you are setting up BAM alerts.</span></span> <span data-ttu-id="b284d-130">如果沒有在命令列指定 NSUserPassword，bm.exe 會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="b284d-130">If the NSUserPassword is not specified on the command line, bm.exe prompts you for the password.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b284d-131">命令完成之後，追蹤記錄中可能會有來自 AlertModule 的例外狀況：</span><span class="sxs-lookup"><span data-stu-id="b284d-131">After the completion of the command, you may note an exception from the AlertModule in the trace log:</span></span>  
>   
>  <span data-ttu-id="b284d-132">「指定的帳戶是資料庫擁有者。</span><span class="sxs-lookup"><span data-stu-id="b284d-132">"The specified account is the Database Owner.</span></span> <span data-ttu-id="b284d-133">資料庫擁有者永遠可以存取檢視，而且無法加入檢視或從檢視移除。」</span><span class="sxs-lookup"><span data-stu-id="b284d-133">The Database owner always has access to the view and cannot be added to or removed from the view."</span></span>  
>   
>  <span data-ttu-id="b284d-134">此外，您可能還會看到 NotificationServices #19001 事件提出的警告。</span><span class="sxs-lookup"><span data-stu-id="b284d-134">In addition, you may see a warning in the event from NotificationServices #19001.</span></span>  
>   
>  <span data-ttu-id="b284d-135">如果命令執行期間沒有回報錯誤，您就可以放心地忽略這些通知事項。</span><span class="sxs-lookup"><span data-stu-id="b284d-135">If no errors were reported during the execution of the command, you can safely disregard these notices.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b284d-136">如果您已設定 BAM 警示，而在執行 setup-database 命令時使用了不含 alerts 區段的 BAM 組態檔，則因 bm.exe 會覆寫組態，以致警示將不再發生作用。</span><span class="sxs-lookup"><span data-stu-id="b284d-136">If you execute a setup-database command, using a BAM configuration file that does not contain an alerts section, and you have already configured BAM Alerts, bm.exe will overwrite the configuration such that alerts will no longer function.</span></span>  
  
 <span data-ttu-id="b284d-137">若要安裝 BAM 資料庫，您必須對裝載 BAMPrimaryImport、BAMStarSchema 和 BAMArchive 資料庫的 Microsoft SQL Server 擁有系統管理員權限。</span><span class="sxs-lookup"><span data-stu-id="b284d-137">To set up the BAM databases you must have administrator permissions on the Microsoft SQL server hosting the BAMPrimaryImport, BAMStarSchema, and BAMArchive databases.</span></span> <span data-ttu-id="b284d-138">若要安裝 SQL Notification Services 資料庫，您必須擁有系統管理員權限，並且隸屬於本機系統管理員群組及任何其他已設定的系統管理員群組 (例如 BTS Admins 群組)。</span><span class="sxs-lookup"><span data-stu-id="b284d-138">To set up SQL Notification Services databases, you must have administrator permissions and be a member of the local administrators group, as well as be a member of any other additional administrative groups that have been configured, such as the BTS Admins group.</span></span>  
  
 <span data-ttu-id="b284d-139">**範例**</span><span class="sxs-lookup"><span data-stu-id="b284d-139">**Examples**</span></span>  
  
```  
bm.exe setup-databases -ConfigFile:BamConfiguration.xml  
bm.exe setup-databases -ConfigFile:cfg.xml -NSUser:domain\user1  
```  
  
## <a name="migrate-sql-command"></a><span data-ttu-id="b284d-140">migrate-sql 命令</span><span class="sxs-lookup"><span data-stu-id="b284d-140">migrate-sql Command</span></span>  
 <span data-ttu-id="b284d-141">**使用方式**</span><span class="sxs-lookup"><span data-stu-id="b284d-141">**Usage**</span></span>  
  
 <span data-ttu-id="b284d-142">**bm.exe 移轉 sql-從： sql2000-至： sql2008 [-NSUser:\<通知服務使用者名稱 >] [-NSUserPassword:\<通知服務使用者密碼 >] [-Server:\<伺服器 >] [-Database:\<資料庫 >]**</span><span class="sxs-lookup"><span data-stu-id="b284d-142">**bm.exe migrate-sql -From:sql2000 -To:sql2008 [ -NSUser:\<notifications service user name> ][ -NSUserPassword:\<notifications service user password> ][ -Server:\<server> ][ -Database:\<database> ]**</span></span>  
  
 <span data-ttu-id="b284d-143">\-或者-</span><span class="sxs-lookup"><span data-stu-id="b284d-143">\- Or -</span></span>  
  
 <span data-ttu-id="b284d-144">**bm.exe 移轉 sql-從： sql2005-至： sql2008 [-NSUser:\<通知服務使用者名稱 >] [-NSUserPassword:\<通知服務使用者密碼 >] [-Server:\<伺服器 >] [-Database:\<資料庫 >]**</span><span class="sxs-lookup"><span data-stu-id="b284d-144">**bm.exe migrate-sql -From:sql2005 -To:sql2008 [ -NSUser:\<notifications service user name> ][ -NSUserPassword:\<notifications service user password> ][ -Server:\<server> ][ -Database:\<database> ]**</span></span>  
  
 <span data-ttu-id="b284d-145">**參數**</span><span class="sxs-lookup"><span data-stu-id="b284d-145">**Parameters**</span></span>  
  
|<span data-ttu-id="b284d-146">參數</span><span class="sxs-lookup"><span data-stu-id="b284d-146">Parameter</span></span>|<span data-ttu-id="b284d-147">Description</span><span class="sxs-lookup"><span data-stu-id="b284d-147">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b284d-148">從： sql2000</span><span class="sxs-lookup"><span data-stu-id="b284d-148">From: sql2000</span></span>|<span data-ttu-id="b284d-149">指定從 Microsoft SQL Server 2000 資料庫進行轉換。</span><span class="sxs-lookup"><span data-stu-id="b284d-149">Specifies that you are converting from a Microsoft SQL Server 2000 database.</span></span>|  
|<span data-ttu-id="b284d-150">若要： sql2008</span><span class="sxs-lookup"><span data-stu-id="b284d-150">To:sql2008</span></span>|<span data-ttu-id="b284d-151">指定轉換到 Microsoft SQL Server 2008 資料庫。</span><span class="sxs-lookup"><span data-stu-id="b284d-151">Specifies that you are converting to a Microsoft SQL Server 2008 database.</span></span>|  
|<span data-ttu-id="b284d-152">從： sql2005</span><span class="sxs-lookup"><span data-stu-id="b284d-152">From: sql2005</span></span>|<span data-ttu-id="b284d-153">指定您想要從 Microsoft SQL Server 2005 資料庫進行轉換。</span><span class="sxs-lookup"><span data-stu-id="b284d-153">Specifies that you are converting from a Microsoft SQL Server 2005 database.</span></span>|  
|<span data-ttu-id="b284d-154">若要： sql2008</span><span class="sxs-lookup"><span data-stu-id="b284d-154">To:sql2008</span></span>|<span data-ttu-id="b284d-155">指定轉換到 Microsoft SQL Server 2008 資料庫。</span><span class="sxs-lookup"><span data-stu-id="b284d-155">Specifies that you are converting to a Microsoft SQL Server 2008 database.</span></span>|  
|<span data-ttu-id="b284d-156">NSUser:\<通知服務使用者名稱 ></span><span class="sxs-lookup"><span data-stu-id="b284d-156">NSUser:\<notifications service user name></span></span>|<span data-ttu-id="b284d-157">選擇性： 有建立資料庫的權限之通知服務使用者的使用者識別碼。</span><span class="sxs-lookup"><span data-stu-id="b284d-157">Optional: The user ID of a Notifications Services user with permissions to create databases.</span></span>|  
|<span data-ttu-id="b284d-158">NSUserPassword</span><span class="sxs-lookup"><span data-stu-id="b284d-158">NSUserPassword</span></span>|<span data-ttu-id="b284d-159">選擇性： 指定通知服務使用者的密碼。</span><span class="sxs-lookup"><span data-stu-id="b284d-159">Optional: The password for the specified Notifications Services user.</span></span>|  
|<span data-ttu-id="b284d-160">伺服器：\<伺服器 ></span><span class="sxs-lookup"><span data-stu-id="b284d-160">Server:\<server></span></span>|<span data-ttu-id="b284d-161">選擇性： 將轉換的資料庫所在的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="b284d-161">Optional: The name of the server on which the converted database will reside.</span></span> <span data-ttu-id="b284d-162">伺服器和裝載 Microsoft SQL Server 2008 資料庫的電腦必須位在相同網域中。</span><span class="sxs-lookup"><span data-stu-id="b284d-162">The server must be in the same domain as the computer hosting the Microsoft SQL Server 2008 database.</span></span> <span data-ttu-id="b284d-163">如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。</span><span class="sxs-lookup"><span data-stu-id="b284d-163">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="b284d-164">資料庫：\<資料庫 ></span><span class="sxs-lookup"><span data-stu-id="b284d-164">Database:\<database></span></span>|<span data-ttu-id="b284d-165">選擇性： 然後命名的轉換的資料庫。</span><span class="sxs-lookup"><span data-stu-id="b284d-165">Optional: Then name of the converted database.</span></span> <span data-ttu-id="b284d-166">如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。</span><span class="sxs-lookup"><span data-stu-id="b284d-166">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="b284d-167">將 BAM 基礎結構從 Microsoft SQL Server 2000 或 Microsoft SQL Server 2005 移轉至 Microsoft SQL Server 2008。</span><span class="sxs-lookup"><span data-stu-id="b284d-167">Migrates the BAM infrastructure from Microsoft SQL Server 2000 or Microsoft SQL Server 2005 to Microsoft SQL Server 2008.</span></span> <span data-ttu-id="b284d-168">從 Microsoft SQL Server 2000 或 Microsoft SQL Server 2005 中將您的資料庫伺服器和 Analysis server 升級至 Microsoft SQL Server 2008 之後，請使用此命令。</span><span class="sxs-lookup"><span data-stu-id="b284d-168">Use this command after you upgrade your database server and Analysis server from Microsoft SQL Server 2000 or Microsoft SQL Server 2005 to Microsoft SQL Server 2008.</span></span>  
  
 <span data-ttu-id="b284d-169">如果設定 BAM 警示，則 NSUser 和 NSUserPassword 皆為必要參數。</span><span class="sxs-lookup"><span data-stu-id="b284d-169">The NSUser and NSUserPassword parameters are required if BAM alerts are configured.</span></span> <span data-ttu-id="b284d-170">如果沒有在命令列指定 NSUserPassword，bm.exe 會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="b284d-170">If the NSUserPassword is not specified on the command line, bm.exe prompts you for the password.</span></span>  
  
 <span data-ttu-id="b284d-171">若要移轉 SQL Server Notification Services 資料庫，您必須擁有系統管理員權限，並且隸屬於本機系統管理員群組及任何其他已設定的系統管理員群組 (例如 BTS Admins 群組)。</span><span class="sxs-lookup"><span data-stu-id="b284d-171">To migrate the SQL Server Notification Services databases, you must have administrator permissions and be a member of the local administrators group, as well as be a member of any other additional administrative groups that have been configured, such as the BTS Admins group.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b284d-172">如果您收到錯誤訊息 「 錯誤： 無法在電腦上啟動服務 NS$ BAMAlerts '\<電腦名稱 >'。</span><span class="sxs-lookup"><span data-stu-id="b284d-172">If you receive the error message "ERROR: Cannot start service NS$BAMAlerts on computer '\<computer name>'.</span></span> <span data-ttu-id="b284d-173">服務並未及時回應啟動或控制要求」，請嘗試手動重新啟動服務。</span><span class="sxs-lookup"><span data-stu-id="b284d-173">The service did not respond to the start or control request in a timely fashion.", try restarting the service manually.</span></span> <span data-ttu-id="b284d-174">如果 SQL Server 在移轉期間非常忙碌，可能無法重新啟動服務。</span><span class="sxs-lookup"><span data-stu-id="b284d-174">If the SQL Server is extremely busy during a migration, the service may not restart.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b284d-175">若要在有安裝 Notification Services 的電腦上執行 migrate-sql 命令，您必須隸屬於該電腦上的本機系統管理員群組。</span><span class="sxs-lookup"><span data-stu-id="b284d-175">To run the migrate-sql command on the computer where Notification Services is installed, you must belong to the Local Administrators group on that computer.</span></span>  
  
 <span data-ttu-id="b284d-176">**範例**</span><span class="sxs-lookup"><span data-stu-id="b284d-176">**Examples**</span></span>  
  
```  
bm.exe migrate-sql -From:sql2000 -To:sql2008 -NSUser:domain\user1  
bm.exe migrate-sql -From:sql2000 -To:sql2008 -Server:MyServer -Database:db1  
```  
  
```  
bm.exe migrate-sql -From:sql2005 -To:sql2008 -NSUser:domain\user1  
bm.exe migrate-sql -From:sql2005 -To:sql2008 -Server:MyServer -Database:db1  
```  
  
## <a name="enable-reference-command"></a><span data-ttu-id="b284d-177">enable-reference 命令</span><span class="sxs-lookup"><span data-stu-id="b284d-177">enable-reference Command</span></span>  
 <span data-ttu-id="b284d-178">**使用方式**</span><span class="sxs-lookup"><span data-stu-id="b284d-178">**Usage**</span></span>  
  
 <span data-ttu-id="b284d-179">**bm.exe 啟用參考 TargetServer:\<目標伺服器 >-TargetDatabase:\<目標資料庫 > [-Server:\<伺服器 >] [-Database:\<資料庫 >]**</span><span class="sxs-lookup"><span data-stu-id="b284d-179">**bm.exe enable-reference -TargetServer:\<target server> -TargetDatabase:\<target database>[ -Server:\<server> ][ -Database:\<database> ]**</span></span>  
  
 <span data-ttu-id="b284d-180">**參數**</span><span class="sxs-lookup"><span data-stu-id="b284d-180">**Parameters**</span></span>  
  
|<span data-ttu-id="b284d-181">參數</span><span class="sxs-lookup"><span data-stu-id="b284d-181">Parameter</span></span>|<span data-ttu-id="b284d-182">Description</span><span class="sxs-lookup"><span data-stu-id="b284d-182">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b284d-183">TargetServer:\<目標伺服器 ></span><span class="sxs-lookup"><span data-stu-id="b284d-183">TargetServer:\<target server></span></span>|<span data-ttu-id="b284d-184">啟用參考的對象伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="b284d-184">The name of the server to which the reference is enabled.</span></span> <span data-ttu-id="b284d-185">伺服器和執行 bm.exe 的電腦必須位在相同網域中。</span><span class="sxs-lookup"><span data-stu-id="b284d-185">The server must be in the same domain as the computer from which you are running bm.exe.</span></span>|  
|<span data-ttu-id="b284d-186">TargetDatabase:\<目標資料庫 ></span><span class="sxs-lookup"><span data-stu-id="b284d-186">TargetDatabase:\<target database></span></span>|<span data-ttu-id="b284d-187">啟用參考的對象資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="b284d-187">The name of the database to which the reference is enabled.</span></span>|  
|<span data-ttu-id="b284d-188">伺服器：\<伺服器 ></span><span class="sxs-lookup"><span data-stu-id="b284d-188">Server:\<server></span></span>|<span data-ttu-id="b284d-189">選擇性： 目標伺服器和資料庫啟用參考的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="b284d-189">Optional: The name of the server which will have a reference enabled to the target server and database.</span></span> <span data-ttu-id="b284d-190">如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。</span><span class="sxs-lookup"><span data-stu-id="b284d-190">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="b284d-191">資料庫：\<資料庫 ></span><span class="sxs-lookup"><span data-stu-id="b284d-191">Database:\<database></span></span>|<span data-ttu-id="b284d-192">選擇性： 目標伺服器和資料庫啟用參考的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="b284d-192">Optional: The name of the database which will have a reference enabled to the target server and database.</span></span> <span data-ttu-id="b284d-193">如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。</span><span class="sxs-lookup"><span data-stu-id="b284d-193">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="b284d-194">啟用其他分散式 BAM 主要匯入資料庫的參考。</span><span class="sxs-lookup"><span data-stu-id="b284d-194">Enables a reference to another distributed BAM Primary Import database.</span></span> <span data-ttu-id="b284d-195">這可讓您從目前的資料庫訂閱目標 BAM 主要匯入資料庫上的檢視和活動中繼資料。</span><span class="sxs-lookup"><span data-stu-id="b284d-195">This allows subscriptions from the current database to the view and activity metadata on the target BAM Primary Import database.</span></span> <span data-ttu-id="b284d-196">藉此即可瀏覽分散式活動。</span><span class="sxs-lookup"><span data-stu-id="b284d-196">You use this to enable navigation of the distributed activities.</span></span>  
  
 <span data-ttu-id="b284d-197">您可以將目標伺服器指定為 SQL Server 的執行個體，例如 'mymachine2\myinstance'。</span><span class="sxs-lookup"><span data-stu-id="b284d-197">You can specify the target server as an instance of SQL Server, for example, 'mymachine2\myinstance'.</span></span>  
  
 <span data-ttu-id="b284d-198">**範例**</span><span class="sxs-lookup"><span data-stu-id="b284d-198">**Examples**</span></span>  
  
```  
bm.exe enable-reference -TargetServer:MySrv -TargetDatabase:BamPrimaryImport  
bm.exe enable-reference -TargetServer:s2 -TargetDatabase:db1 -Server:s1  
```  
  
## <a name="get-references-command"></a><span data-ttu-id="b284d-199">get-references 命令</span><span class="sxs-lookup"><span data-stu-id="b284d-199">get-references Command</span></span>  
 <span data-ttu-id="b284d-200">**使用方式**</span><span class="sxs-lookup"><span data-stu-id="b284d-200">**Usage**</span></span>  
  
 <span data-ttu-id="b284d-201">**bm.exe get 參考 [-Server:\<伺服器 >] [-Database:\<資料庫 >]**</span><span class="sxs-lookup"><span data-stu-id="b284d-201">**bm.exe get-references [ -Server:\<server> ][ -Database:\<database> ]**</span></span>  
  
 <span data-ttu-id="b284d-202">**參數**</span><span class="sxs-lookup"><span data-stu-id="b284d-202">**Parameters**</span></span>  
  
|<span data-ttu-id="b284d-203">參數</span><span class="sxs-lookup"><span data-stu-id="b284d-203">Parameter</span></span>|<span data-ttu-id="b284d-204">Description</span><span class="sxs-lookup"><span data-stu-id="b284d-204">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b284d-205">伺服器：\<伺服器 ></span><span class="sxs-lookup"><span data-stu-id="b284d-205">Server:\<server></span></span>|<span data-ttu-id="b284d-206">選擇性： 若要取得的參考清單所在的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="b284d-206">Optional: The name of the server on which to get a list of references.</span></span> <span data-ttu-id="b284d-207">伺服器和執行 bm.exe 的電腦必須位在相同網域中。</span><span class="sxs-lookup"><span data-stu-id="b284d-207">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="b284d-208">如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。</span><span class="sxs-lookup"><span data-stu-id="b284d-208">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="b284d-209">資料庫：\<資料庫 ></span><span class="sxs-lookup"><span data-stu-id="b284d-209">Database:\<database></span></span>|<span data-ttu-id="b284d-210">選擇性： 要取得的參考清單上的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="b284d-210">Optional: The name of the database on which to get a list of references.</span></span> <span data-ttu-id="b284d-211">如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。</span><span class="sxs-lookup"><span data-stu-id="b284d-211">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="b284d-212">列出執行此命令的電腦已啟用的參考。</span><span class="sxs-lookup"><span data-stu-id="b284d-212">Lists the references enabled on the computer on which the command is executed.</span></span>  
  
 <span data-ttu-id="b284d-213">**範例**</span><span class="sxs-lookup"><span data-stu-id="b284d-213">**Examples**</span></span>  
  
```  
bm.exe get-references  
bm.exe get-references -Server:MyServer -Database:MyPrimaryImport  
```  
  
## <a name="disable-reference-command"></a><span data-ttu-id="b284d-214">disable-reference 命令</span><span class="sxs-lookup"><span data-stu-id="b284d-214">disable-reference Command</span></span>  
 <span data-ttu-id="b284d-215">**使用方式**</span><span class="sxs-lookup"><span data-stu-id="b284d-215">**Usage**</span></span>  
  
 <span data-ttu-id="b284d-216">**bm.exe 停用參考 TargetServer:\<目標伺服器 >-TargetDatabase:\<目標資料庫 > [-Server:\<伺服器 >] [-Database:\<資料庫 >]**</span><span class="sxs-lookup"><span data-stu-id="b284d-216">**bm.exe disable-reference -TargetServer:\<target server> -TargetDatabase:\<target database>[ -Server:\<server> ][ -Database:\<database> ]**</span></span>  
  
 <span data-ttu-id="b284d-217">**參數**</span><span class="sxs-lookup"><span data-stu-id="b284d-217">**Parameters**</span></span>  
  
|<span data-ttu-id="b284d-218">參數</span><span class="sxs-lookup"><span data-stu-id="b284d-218">Parameter</span></span>|<span data-ttu-id="b284d-219">Description</span><span class="sxs-lookup"><span data-stu-id="b284d-219">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b284d-220">TargetServer:\<目標伺服器 ></span><span class="sxs-lookup"><span data-stu-id="b284d-220">TargetServer:\<target server></span></span>|<span data-ttu-id="b284d-221">停用參考的對象伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="b284d-221">The name of the server on which to disable the references.</span></span> <span data-ttu-id="b284d-222">伺服器和執行 bm.exe 的電腦必須位在相同網域中。</span><span class="sxs-lookup"><span data-stu-id="b284d-222">The server must be in the same domain as the computer from which you are running bm.exe.</span></span>|  
|<span data-ttu-id="b284d-223">TargetDatabase:\<目標資料庫 ></span><span class="sxs-lookup"><span data-stu-id="b284d-223">TargetDatabase:\<target database></span></span>|<span data-ttu-id="b284d-224">停用參考的對象資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="b284d-224">The name of the database on which to disable the references.</span></span>|  
|<span data-ttu-id="b284d-225">伺服器：\<伺服器 ></span><span class="sxs-lookup"><span data-stu-id="b284d-225">Server:\<server></span></span>|<span data-ttu-id="b284d-226">選擇性： 在它會參考到目標伺服器和資料庫要停用伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="b284d-226">Optional: The name of the server on which references to the target server and database are to be disabled.</span></span> <span data-ttu-id="b284d-227">伺服器和執行 bm.exe 的電腦必須位在相同網域中。</span><span class="sxs-lookup"><span data-stu-id="b284d-227">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="b284d-228">如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。</span><span class="sxs-lookup"><span data-stu-id="b284d-228">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="b284d-229">資料庫：\<資料庫 ></span><span class="sxs-lookup"><span data-stu-id="b284d-229">Database:\<database></span></span>|<span data-ttu-id="b284d-230">選擇性： 在它會參考到目標伺服器和資料庫要停用資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="b284d-230">Optional: The name of the database on which references to the target server and database are to be disabled.</span></span> <span data-ttu-id="b284d-231">如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。</span><span class="sxs-lookup"><span data-stu-id="b284d-231">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="b284d-232">停用目標伺服器上其他分散式 BAM 主要匯入資料庫的參考。</span><span class="sxs-lookup"><span data-stu-id="b284d-232">Disables a reference to another distributed BAM Primary Import database on the target server.</span></span>  
  
 <span data-ttu-id="b284d-233">您可以將目標伺服器指定為 SQL Server 的執行個體，例如 'mymachine2\myinstance'。</span><span class="sxs-lookup"><span data-stu-id="b284d-233">You can specify the target server as an instance of SQL Server, for example, 'mymachine2\myinstance'.</span></span>  
  
 <span data-ttu-id="b284d-234">**範例**</span><span class="sxs-lookup"><span data-stu-id="b284d-234">**Examples**</span></span>  
  
```  
bm.exe disable-reference -TargetServer:MySrv -TargetDatabase:BamPI  
bm.exe disable-reference -TargetServer:s2 -TargetDatabase:db1 -Server:s1  
```  
  
## <a name="see-also"></a><span data-ttu-id="b284d-235">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b284d-235">See Also</span></span>  
 [<span data-ttu-id="b284d-236">BAM 管理公用程式</span><span class="sxs-lookup"><span data-stu-id="b284d-236">BAM Management Utility</span></span>](../core/bam-management-utility.md)