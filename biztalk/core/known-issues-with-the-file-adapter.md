---
title: "File 配接器的已知問題 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6aaf448c-0035-4648-910b-ae2f15106342
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2690803346efc5931a88acd70be9d24af107156f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="known-issues-with-the-file-adapter"></a><span data-ttu-id="1702c-102">FILE 配接器的已知問題</span><span class="sxs-lookup"><span data-stu-id="1702c-102">Known Issues with the File Adapter</span></span>
<span data-ttu-id="1702c-103">本節包含可幫助您避免錯誤的資訊。</span><span class="sxs-lookup"><span data-stu-id="1702c-103">This section contains information that may help you avoid errors.</span></span>  
  
## <a name="known-issues"></a><span data-ttu-id="1702c-104">已知問題</span><span class="sxs-lookup"><span data-stu-id="1702c-104">Known Issues</span></span>  
  
#### <a name="a-file-receive-location-is-disabled"></a><span data-ttu-id="1702c-105">FILE 接收位置已停用</span><span class="sxs-lookup"><span data-stu-id="1702c-105">A File Receive Location is Disabled</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="1702c-106">問題</span><span class="sxs-lookup"><span data-stu-id="1702c-106">Problem</span></span>  
 <span data-ttu-id="1702c-107">FILE 接收位置變成停用。</span><span class="sxs-lookup"><span data-stu-id="1702c-107">A File receive location becomes disabled.</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="1702c-108">原因</span><span class="sxs-lookup"><span data-stu-id="1702c-108">Cause</span></span>  
 <span data-ttu-id="1702c-109">發生下列任一情況時，FILE 接收配接器會停用接收位置：</span><span class="sxs-lookup"><span data-stu-id="1702c-109">The File receive adapter disables the receive location if any of the following occur:</span></span>  
  
-   <span data-ttu-id="1702c-110">由於指定的路徑不存在，FILE 接收配接器無法存取檔案系統或網路共用上的接收位置。</span><span class="sxs-lookup"><span data-stu-id="1702c-110">The File receive adapter cannot access the receive location on the file system or network share because the specified path does not exist.</span></span> <span data-ttu-id="1702c-111">存取網路共用時，若已耗盡所有的重試嘗試次數，FILE 接收配接器便會停用接收位置。</span><span class="sxs-lookup"><span data-stu-id="1702c-111">For a network share, the File receive adapter disables the receive location after all retry attempts have been exhausted.</span></span>  
  
-   <span data-ttu-id="1702c-112">由於相關主控件執行個體所使用的帳戶對特定位置沒有讀寫權限，因此 FILE 接收配接器無法存取檔案系統或網路共用上的接收位置。</span><span class="sxs-lookup"><span data-stu-id="1702c-112">The File receive adapter cannot access the receive location on the file system or network share because the account used by the associated host instance does not have read-write permission for that location.</span></span> <span data-ttu-id="1702c-113">存取網路共用時，若已耗盡所有的重試嘗試次數，FILE 接收配接器便會停用接收位置。</span><span class="sxs-lookup"><span data-stu-id="1702c-113">For a network share, the File receive adapter disables the receive location after all retry attempts have been exhausted.</span></span>  
  
-   <span data-ttu-id="1702c-114">接收位置上的檔案其名稱超過 256 個字元。</span><span class="sxs-lookup"><span data-stu-id="1702c-114">Files with names longer than 256 characters are encountered in the receive location.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="1702c-115">解決方案</span><span class="sxs-lookup"><span data-stu-id="1702c-115">Resolution</span></span>  
  
-   <span data-ttu-id="1702c-116">確定指定的路徑或共用存在。</span><span class="sxs-lookup"><span data-stu-id="1702c-116">Ensure that the specified path or share exists.</span></span>  
  
-   <span data-ttu-id="1702c-117">請確認帳戶做為**登入：**帳戶為 File 接收處理常式主控件執行個體具有讀取和寫入權限指定接收位置。</span><span class="sxs-lookup"><span data-stu-id="1702c-117">Ensure that the account used as the **Logon:** account for the File receive handler host instance has read and write permissions to the specified receive location.</span></span>  
  
-   <span data-ttu-id="1702c-118">確定寫入至 FILE 接收配接器監控之資料夾的檔案未超過 256 個字元的檔案名稱限制。</span><span class="sxs-lookup"><span data-stu-id="1702c-118">Ensure that files written to the folder monitored by the File receive adapter do not have file names exceeding 256 characters.</span></span>  
  
#### <a name="files-are-not-being-read-from-the-specified-receive-location"></a><span data-ttu-id="1702c-119">無法從指定的接收位置讀取檔案</span><span class="sxs-lookup"><span data-stu-id="1702c-119">Files Are Not Being Read from the Specified Receive Location</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="1702c-120">問題</span><span class="sxs-lookup"><span data-stu-id="1702c-120">Problem</span></span>  
 <span data-ttu-id="1702c-121">FILE 接收配接器無法從指定的接收位置讀取檔案。</span><span class="sxs-lookup"><span data-stu-id="1702c-121">The File receive adapter does not read a file from the specified receive location.</span></span> <span data-ttu-id="1702c-122">FILE 接收配接器若遇到上述類型的檔案，便會在事件日誌中記錄錯誤，並將檔案留在接收位置上。</span><span class="sxs-lookup"><span data-stu-id="1702c-122">When the File receive adapter encounters such a file, it logs an error in the event log and leaves the file in the receive location.</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="1702c-123">原因</span><span class="sxs-lookup"><span data-stu-id="1702c-123">Cause</span></span>  
 <span data-ttu-id="1702c-124">發生下列任一情況時，FILE 接收配接器不會從接收位置讀取檔案：</span><span class="sxs-lookup"><span data-stu-id="1702c-124">The File receive adapter does not read a file from the receive location if any of the following conditions are true:</span></span>  
  
-   <span data-ttu-id="1702c-125">檔案是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="1702c-125">The file is read-only.</span></span>  
  
-   <span data-ttu-id="1702c-126">檔案設有系統屬性。</span><span class="sxs-lookup"><span data-stu-id="1702c-126">The file has a system attribute.</span></span>  
  
-   <span data-ttu-id="1702c-127">FILE 接收配接器沒有讀寫檔案的權限。</span><span class="sxs-lookup"><span data-stu-id="1702c-127">The File receive adapter does not have permissions to read and write to the file.</span></span>  
  
-   <span data-ttu-id="1702c-128">接收位置上的檔案其名稱超過 256 個字元。</span><span class="sxs-lookup"><span data-stu-id="1702c-128">Files with names longer than 256 characters are encountered in the receive location.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="1702c-129">解決方案</span><span class="sxs-lookup"><span data-stu-id="1702c-129">Resolution</span></span>  
  
-   <span data-ttu-id="1702c-130">確定指定接收位置上的檔案未標示為「唯讀」。</span><span class="sxs-lookup"><span data-stu-id="1702c-130">Ensure that the files in the specified receive location are not marked as "read only".</span></span>  
  
-   <span data-ttu-id="1702c-131">確定指定接收位置上的檔案未標示有系統屬性。</span><span class="sxs-lookup"><span data-stu-id="1702c-131">Ensure that the files in the specified receive location are not marked with a system attribute.</span></span>  
  
-   <span data-ttu-id="1702c-132">請確認帳戶做為**登入：**帳戶為 File 接收處理常式主控件執行個體具有讀取和寫入權限指定接收位置。</span><span class="sxs-lookup"><span data-stu-id="1702c-132">Ensure that the account used as the **Logon:** account for the File receive handler host instance has read and write permissions to the specified receive location.</span></span>  
  
-   <span data-ttu-id="1702c-133">確定寫入至 FILE 接收配接器監控之資料夾的檔案未超過 256 個字元的檔案名稱限制。</span><span class="sxs-lookup"><span data-stu-id="1702c-133">Ensure that files written to the folder monitored by the File receive adapter do not have file names exceeding 256 characters.</span></span>  
  
#### <a name="messages-are-not-being-sent-by-the-file-send-adapter"></a><span data-ttu-id="1702c-134">FILE 傳送配接器並未送出訊息</span><span class="sxs-lookup"><span data-stu-id="1702c-134">Messages Are Not Being Sent by the File Send Adapter</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="1702c-135">問題</span><span class="sxs-lookup"><span data-stu-id="1702c-135">Problem</span></span>  
 <span data-ttu-id="1702c-136">FILE 傳送配接器無法傳送訊息至指定的目錄或檔案共用。</span><span class="sxs-lookup"><span data-stu-id="1702c-136">The File send adapter fails to send a message to the specified directory or file share.</span></span>  
  
 <span data-ttu-id="1702c-137">如果訊息無法寫入指定的目錄或檔案共用，便會在 BizTalk Server 電腦的事件日誌中記錄錯誤，並且會依照下列順序發生事件：</span><span class="sxs-lookup"><span data-stu-id="1702c-137">If a message fails to be written to the specified directory or file share, an error is written to the Event log of the BizTalk server computer and the following sequence of events occurs:</span></span>  
  
1.  <span data-ttu-id="1702c-138">FILE 傳送配接器會重試寫入作業。</span><span class="sxs-lookup"><span data-stu-id="1702c-138">The File send adapter will retry the write operation.</span></span>  
  
2.  <span data-ttu-id="1702c-139">FILE 配接器會使用備份傳輸 (如果已設定)，嘗試傳遞檔案。</span><span class="sxs-lookup"><span data-stu-id="1702c-139">The File adapter will attempt to deliver the file using the backup transport (if configured).</span></span>  
  
3.  <span data-ttu-id="1702c-140">訊息會寫入到擱置佇列。</span><span class="sxs-lookup"><span data-stu-id="1702c-140">The message will be written to the suspended queue.</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="1702c-141">原因</span><span class="sxs-lookup"><span data-stu-id="1702c-141">Cause</span></span>  
  
-   <span data-ttu-id="1702c-142">由於指定的路徑不存在，FILE 傳送配接器無法存取檔案系統或網路共用上的檔案傳送來源所在目錄。</span><span class="sxs-lookup"><span data-stu-id="1702c-142">The File send adapter cannot access the directory that files are sent from on the file system or network share because the specified path does not exist.</span></span>  
  
-   <span data-ttu-id="1702c-143">由於相關主控件執行個體對特定檔案或位置沒有寫入權限，因此 FILE 傳送配接器無法寫入檔案系統或網路共用上位於目的地位置的檔案。</span><span class="sxs-lookup"><span data-stu-id="1702c-143">The File send adapter cannot write to a file in the destination location on the file system or network share because the associated host instance does not have write permissions for that file or for that location.</span></span>  
  
-   <span data-ttu-id="1702c-144">File 傳送配接器無法寫入檔案中指定，因為它是唯讀或標示為**系統**檔案屬性。</span><span class="sxs-lookup"><span data-stu-id="1702c-144">The File send adapter cannot write to the file specified because it is read-only or is marked with the **system** file attribute.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="1702c-145">解決方案</span><span class="sxs-lookup"><span data-stu-id="1702c-145">Resolution</span></span>  
  
-   <span data-ttu-id="1702c-146">確定指定的路徑或共用存在。</span><span class="sxs-lookup"><span data-stu-id="1702c-146">Ensure that the specified path or share exists.</span></span>  
  
-   <span data-ttu-id="1702c-147">請確認帳戶做為**登入：**檔案傳送處理常式的主控件執行個體的帳戶具有讀取和寫入指定的目錄或檔案共用權限。</span><span class="sxs-lookup"><span data-stu-id="1702c-147">Ensure that the account used as the **Logon:** account for the File send handler host instance has read and write permissions to the specified directory or file share.</span></span>  
  
-   <span data-ttu-id="1702c-148">確定指定目錄或檔案共用上的現有檔案未標示有系統屬性。</span><span class="sxs-lookup"><span data-stu-id="1702c-148">Ensure that existing files in the specified directory or file share are not marked with the system attribute.</span></span>  
  
#### <a name="sending-a-file-using-the-file-adapter-is-very-slow"></a><span data-ttu-id="1702c-149">使用 FILE 配接器傳送檔案的速度非常慢</span><span class="sxs-lookup"><span data-stu-id="1702c-149">Sending a file using the File adapter is very slow</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="1702c-150">問題</span><span class="sxs-lookup"><span data-stu-id="1702c-150">Problem</span></span>  
 <span data-ttu-id="1702c-151">File 傳送配接器的效能會變慢時**允許寫入時快取**屬性設定為**False**。</span><span class="sxs-lookup"><span data-stu-id="1702c-151">Performance of the File send adapter is slower when the **Allow cache on write** property is set to **False**.</span></span> <span data-ttu-id="1702c-152">**允許寫入時快取**屬性設定為**False**預設。</span><span class="sxs-lookup"><span data-stu-id="1702c-152">The **Allow cache on write** property is set to **False** by default.</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="1702c-153">原因</span><span class="sxs-lookup"><span data-stu-id="1702c-153">Cause</span></span>  
 <span data-ttu-id="1702c-154">設定**允許寫入時快取**屬性**False**可以降低效能，因為這項設定不允許使用記憶體中快取檔案的作業系統。</span><span class="sxs-lookup"><span data-stu-id="1702c-154">Setting the **Allow cache on write** property to **False** can reduce performance as this setting disallows the use of in-memory caching of files by the operating system.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="1702c-155">解決方案</span><span class="sxs-lookup"><span data-stu-id="1702c-155">Resolution</span></span>  
 <span data-ttu-id="1702c-156">若要增加效能的檔案傳送配接器變更**允許寫入時快取**屬性**True** （核取方塊）。</span><span class="sxs-lookup"><span data-stu-id="1702c-156">To increase performance of the File send adapter change the **Allow cache on write** property to **True** (check the box).</span></span> <span data-ttu-id="1702c-157">如需有關**允許寫入時快取**屬性，請參閱[如何設定 File 傳送埠](http://msdn.microsoft.com/library/d801c5b7-da0a-4228-af0c-c2d450c251a9)。</span><span class="sxs-lookup"><span data-stu-id="1702c-157">For more information about the **Allow cache on write** property, see [How to Configure a File Send Port](http://msdn.microsoft.com/library/d801c5b7-da0a-4228-af0c-c2d450c251a9).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1702c-158">設定**允許寫入時快取**屬性**True**作業系統發生失敗時增加資料遺失的可能性。</span><span class="sxs-lookup"><span data-stu-id="1702c-158">Setting the **Allow cache on write** property to **True** increases the possibility of data loss in the event that the operating system experiences a failure.</span></span> <span data-ttu-id="1702c-159">在此狀況下，記憶體中檔案快取內儲存的任何資料都會流失。</span><span class="sxs-lookup"><span data-stu-id="1702c-159">In this scenario, any data that is stored in the in-memory file cache will be lost.</span></span>  
  
#### <a name="zero-byte-files-received-by-the-file-adapter-are-deleted"></a><span data-ttu-id="1702c-160">FILE 配接器接收的零位元組檔案已遭刪除</span><span class="sxs-lookup"><span data-stu-id="1702c-160">Zero byte files received by the File adapter are deleted</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="1702c-161">問題</span><span class="sxs-lookup"><span data-stu-id="1702c-161">Problem</span></span>  
 <span data-ttu-id="1702c-162">如果 FILE 接收配接器收取到空白 (零位元組) 檔案，便會刪除該檔案，並將類似以下的警告寫入 BizTalk Server 的應用程式記錄檔：</span><span class="sxs-lookup"><span data-stu-id="1702c-162">If an empty (zero byte) file is picked up by the File receive adapter, the file is deleted and a warning similar to the following is written to the application log of the BizTalk server:</span></span>  
  
```  
Event Type:Warning  
Event Source:BizTalk Server 2009  
Event Category:BizTalk Server 2009   
Event ID:7182  
Date:8/30/2006  
Time:1:32:32 PM  
User:N/A  
Computer:BIZTALKSERVER  
Description:  
The FILE receive adapter deleted the empty file "C:\filesource\emptyfile.xml.BTS-WIP" without performing any processing.  
```  
  
##### <a name="cause"></a><span data-ttu-id="1702c-163">原因</span><span class="sxs-lookup"><span data-stu-id="1702c-163">Cause</span></span>  
 <span data-ttu-id="1702c-164">FILE 接收配接器依設計會刪除零位元組檔案。</span><span class="sxs-lookup"><span data-stu-id="1702c-164">The File receive adapter deletes zero byte files by design.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="1702c-165">解決方案</span><span class="sxs-lookup"><span data-stu-id="1702c-165">Resolution</span></span>  
 <span data-ttu-id="1702c-166">不需動作，此行為是經過設計的。</span><span class="sxs-lookup"><span data-stu-id="1702c-166">No action is required, this behavior is by design.</span></span>