---
title: "BAM 通知的命令列指令碼服務組態檔 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6aa4a460-58f9-439d-af28-0a9cb2288236
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b22607193ed7c345388a6435e2d58c16b8986370
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="bam-command-line-script-for-notification-services-configuration-files"></a><span data-ttu-id="c3e30-102">用於處理 Notification Services 組態檔的 BAM 命令列指令碼</span><span class="sxs-lookup"><span data-stu-id="c3e30-102">BAM Command-Line Script for Notification Services Configuration Files</span></span>
<span data-ttu-id="c3e30-103">系統管理員可使用 ProcessBamNSFiles.vbs 指令碼，以針對 BAM 警示自訂 SQL Server Notification Services 的行為。</span><span class="sxs-lookup"><span data-stu-id="c3e30-103">Administrators use the ProcessBamNSFiles.vbs script to customize the behavior of SQL Server Notification Services for BAM alerts.</span></span> <span data-ttu-id="c3e30-104">使用這個指令碼可以取得 Notification Services 應用程式定義檔 (ADF) 及 Notification Services 組態檔。</span><span class="sxs-lookup"><span data-stu-id="c3e30-104">You can use the script to obtain the Notification Services application definition file (ADF) and Notification Services configuration file.</span></span> <span data-ttu-id="c3e30-105">而在修改這些檔案後，您也可以利用指令碼套用變更。</span><span class="sxs-lookup"><span data-stu-id="c3e30-105">These files can be modified and then the script can be used to apply the changes.</span></span>  
  
 <span data-ttu-id="c3e30-106">請從 Notification Services 命令提示字元執行指令碼，而不要從一般的命令提示字元執行。</span><span class="sxs-lookup"><span data-stu-id="c3e30-106">You run the script from a Notification Services command prompt and not from a typical command prompt.</span></span> <span data-ttu-id="c3e30-107">若從一般的命令提示字元執行指令碼，指令碼將無法正確執行。</span><span class="sxs-lookup"><span data-stu-id="c3e30-107">Running the script from a typical command prompt will cause the script to execute incorrectly.</span></span> <span data-ttu-id="c3e30-108">執行指令碼時，所有的參數皆為必要項。</span><span class="sxs-lookup"><span data-stu-id="c3e30-108">When running the script all parameters are mandatory.</span></span>  
  
## <a name="get-command"></a><span data-ttu-id="c3e30-109">Get 命令</span><span class="sxs-lookup"><span data-stu-id="c3e30-109">Get command</span></span>  
 <span data-ttu-id="c3e30-110">**使用方式**</span><span class="sxs-lookup"><span data-stu-id="c3e30-110">**Usage**</span></span>  
  
 <span data-ttu-id="c3e30-111">**cscript ProcessBamNSFiles-Get\<組態檔路徑\> \<ADF 檔案路徑\>\<主要匯入伺服器\>\<主要匯入資料庫  \>**</span><span class="sxs-lookup"><span data-stu-id="c3e30-111">**cscript ProcessBamNSFiles -Get \<configuration file path\> \<ADF file path\>  \<primary import server\> \<primary import database\>**</span></span>  
  
|<span data-ttu-id="c3e30-112">參數</span><span class="sxs-lookup"><span data-stu-id="c3e30-112">Parameter</span></span>|<span data-ttu-id="c3e30-113">Description</span><span class="sxs-lookup"><span data-stu-id="c3e30-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c3e30-114">組態檔路徑</span><span class="sxs-lookup"><span data-stu-id="c3e30-114">configuration file path</span></span>|<span data-ttu-id="c3e30-115">指定組態檔的儲存位置和名稱。</span><span class="sxs-lookup"><span data-stu-id="c3e30-115">Specifies the name and location in which to store the configuration file.</span></span>|  
|<span data-ttu-id="c3e30-116">ADF 檔案路徑</span><span class="sxs-lookup"><span data-stu-id="c3e30-116">ADF file path</span></span>|<span data-ttu-id="c3e30-117">指定 ADF 檔案的儲存位置和名稱。</span><span class="sxs-lookup"><span data-stu-id="c3e30-117">Specifies the name and location in which to store the ADF file.</span></span>|  
|<span data-ttu-id="c3e30-118">主要匯入伺服器</span><span class="sxs-lookup"><span data-stu-id="c3e30-118">primary import server</span></span>|<span data-ttu-id="c3e30-119">儲存 BAM 主要匯入資料庫之電腦的名稱。</span><span class="sxs-lookup"><span data-stu-id="c3e30-119">Name of the computer on which the BAM Primary Import database is stored.</span></span>|  
|<span data-ttu-id="c3e30-120">主要匯入資料庫</span><span class="sxs-lookup"><span data-stu-id="c3e30-120">primary import database</span></span>|<span data-ttu-id="c3e30-121">BAM 主要匯入資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="c3e30-121">Name of the BAM Primary Import database.</span></span>|  
  
 <span data-ttu-id="c3e30-122">從 BAM 主要匯入資料庫擷取 Notification Services 組態檔及應用程式定義檔，然後儲存至指定的位置。</span><span class="sxs-lookup"><span data-stu-id="c3e30-122">Retrieves the Notification Services configuration and application definition files from the BAM Primary Import database and saves them to specified paths.</span></span>  
  
## <a name="update-command"></a><span data-ttu-id="c3e30-123">Update 命令</span><span class="sxs-lookup"><span data-stu-id="c3e30-123">Update command</span></span>  
 <span data-ttu-id="c3e30-124">**使用方式**</span><span class="sxs-lookup"><span data-stu-id="c3e30-124">**Usage**</span></span>  
  
 <span data-ttu-id="c3e30-125">**cscript ProcessBamNSFiles-Update \<configfilepath\> \<組態檔路徑\>\<primaryimport 伺服器\>\<主要匯入資料庫  \>**</span><span class="sxs-lookup"><span data-stu-id="c3e30-125">**cscript ProcessBamNSFiles -Update \<configfilepath\> \<adffilepath\>  \<primaryimport server\> \<primary import db\>**</span></span>  
  
|<span data-ttu-id="c3e30-126">參數</span><span class="sxs-lookup"><span data-stu-id="c3e30-126">Parameter</span></span>|<span data-ttu-id="c3e30-127">Description</span><span class="sxs-lookup"><span data-stu-id="c3e30-127">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c3e30-128">組態檔路徑</span><span class="sxs-lookup"><span data-stu-id="c3e30-128">configuration file path</span></span>|<span data-ttu-id="c3e30-129">指定用於更新 Notification Services 組態資訊的檔案位置和名稱。</span><span class="sxs-lookup"><span data-stu-id="c3e30-129">Specifies the name and location from which to update the Notification Services configuration information.</span></span>|  
|<span data-ttu-id="c3e30-130">ADF 檔案路徑</span><span class="sxs-lookup"><span data-stu-id="c3e30-130">ADF file path</span></span>|<span data-ttu-id="c3e30-131">指定用於更新 ADF 資訊的檔案位置和名稱。</span><span class="sxs-lookup"><span data-stu-id="c3e30-131">Specifies the name and location from which to update the ADF information.</span></span>|  
|<span data-ttu-id="c3e30-132">主要匯入伺服器</span><span class="sxs-lookup"><span data-stu-id="c3e30-132">primary import server</span></span>|<span data-ttu-id="c3e30-133">儲存 BAM 主要匯入資料庫之電腦的名稱。</span><span class="sxs-lookup"><span data-stu-id="c3e30-133">Name of the computer on which the BAM Primary Import database is stored.</span></span>|  
|<span data-ttu-id="c3e30-134">主要匯入資料庫</span><span class="sxs-lookup"><span data-stu-id="c3e30-134">primary import database</span></span>|<span data-ttu-id="c3e30-135">BAM 主要匯入資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="c3e30-135">Name of the BAM Primary Import database.</span></span>|  
  
 <span data-ttu-id="c3e30-136">呼叫 Notification Services 並將其設定更新為指定檔案中的資訊。</span><span class="sxs-lookup"><span data-stu-id="c3e30-136">Calls Notification Services and updates the settings with the information in the specified files.</span></span> <span data-ttu-id="c3e30-137">組態檔及 ADF 檔案均儲存於 BAM 主要匯入資料庫。</span><span class="sxs-lookup"><span data-stu-id="c3e30-137">The configuration and ADF files are stored in the BAM Primary Import database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3e30-138">請參閱</span><span class="sxs-lookup"><span data-stu-id="c3e30-138">See Also</span></span>  
 [<span data-ttu-id="c3e30-139">BAM 命令列工具</span><span class="sxs-lookup"><span data-stu-id="c3e30-139">BAM Command-Line Tools</span></span>](../core/bam-command-line-tools.md)