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
# <a name="known-issues-with-the-file-adapter"></a>FILE 配接器的已知問題
本節包含可幫助您避免錯誤的資訊。  
  
## <a name="known-issues"></a>已知問題  
  
#### <a name="a-file-receive-location-is-disabled"></a>FILE 接收位置已停用  
  
##### <a name="problem"></a>問題  
 FILE 接收位置變成停用。  
  
##### <a name="cause"></a>原因  
 發生下列任一情況時，FILE 接收配接器會停用接收位置：  
  
-   由於指定的路徑不存在，FILE 接收配接器無法存取檔案系統或網路共用上的接收位置。 存取網路共用時，若已耗盡所有的重試嘗試次數，FILE 接收配接器便會停用接收位置。  
  
-   由於相關主控件執行個體所使用的帳戶對特定位置沒有讀寫權限，因此 FILE 接收配接器無法存取檔案系統或網路共用上的接收位置。 存取網路共用時，若已耗盡所有的重試嘗試次數，FILE 接收配接器便會停用接收位置。  
  
-   接收位置上的檔案其名稱超過 256 個字元。  
  
##### <a name="resolution"></a>解決方案  
  
-   確定指定的路徑或共用存在。  
  
-   請確認帳戶做為**登入：**帳戶為 File 接收處理常式主控件執行個體具有讀取和寫入權限指定接收位置。  
  
-   確定寫入至 FILE 接收配接器監控之資料夾的檔案未超過 256 個字元的檔案名稱限制。  
  
#### <a name="files-are-not-being-read-from-the-specified-receive-location"></a>無法從指定的接收位置讀取檔案  
  
##### <a name="problem"></a>問題  
 FILE 接收配接器無法從指定的接收位置讀取檔案。 FILE 接收配接器若遇到上述類型的檔案，便會在事件日誌中記錄錯誤，並將檔案留在接收位置上。  
  
##### <a name="cause"></a>原因  
 發生下列任一情況時，FILE 接收配接器不會從接收位置讀取檔案：  
  
-   檔案是唯讀的。  
  
-   檔案設有系統屬性。  
  
-   FILE 接收配接器沒有讀寫檔案的權限。  
  
-   接收位置上的檔案其名稱超過 256 個字元。  
  
##### <a name="resolution"></a>解決方案  
  
-   確定指定接收位置上的檔案未標示為「唯讀」。  
  
-   確定指定接收位置上的檔案未標示有系統屬性。  
  
-   請確認帳戶做為**登入：**帳戶為 File 接收處理常式主控件執行個體具有讀取和寫入權限指定接收位置。  
  
-   確定寫入至 FILE 接收配接器監控之資料夾的檔案未超過 256 個字元的檔案名稱限制。  
  
#### <a name="messages-are-not-being-sent-by-the-file-send-adapter"></a>FILE 傳送配接器並未送出訊息  
  
##### <a name="problem"></a>問題  
 FILE 傳送配接器無法傳送訊息至指定的目錄或檔案共用。  
  
 如果訊息無法寫入指定的目錄或檔案共用，便會在 BizTalk Server 電腦的事件日誌中記錄錯誤，並且會依照下列順序發生事件：  
  
1.  FILE 傳送配接器會重試寫入作業。  
  
2.  FILE 配接器會使用備份傳輸 (如果已設定)，嘗試傳遞檔案。  
  
3.  訊息會寫入到擱置佇列。  
  
##### <a name="cause"></a>原因  
  
-   由於指定的路徑不存在，FILE 傳送配接器無法存取檔案系統或網路共用上的檔案傳送來源所在目錄。  
  
-   由於相關主控件執行個體對特定檔案或位置沒有寫入權限，因此 FILE 傳送配接器無法寫入檔案系統或網路共用上位於目的地位置的檔案。  
  
-   File 傳送配接器無法寫入檔案中指定，因為它是唯讀或標示為**系統**檔案屬性。  
  
##### <a name="resolution"></a>解決方案  
  
-   確定指定的路徑或共用存在。  
  
-   請確認帳戶做為**登入：**檔案傳送處理常式的主控件執行個體的帳戶具有讀取和寫入指定的目錄或檔案共用權限。  
  
-   確定指定目錄或檔案共用上的現有檔案未標示有系統屬性。  
  
#### <a name="sending-a-file-using-the-file-adapter-is-very-slow"></a>使用 FILE 配接器傳送檔案的速度非常慢  
  
##### <a name="problem"></a>問題  
 File 傳送配接器的效能會變慢時**允許寫入時快取**屬性設定為**False**。 **允許寫入時快取**屬性設定為**False**預設。  
  
##### <a name="cause"></a>原因  
 設定**允許寫入時快取**屬性**False**可以降低效能，因為這項設定不允許使用記憶體中快取檔案的作業系統。  
  
##### <a name="resolution"></a>解決方案  
 若要增加效能的檔案傳送配接器變更**允許寫入時快取**屬性**True** （核取方塊）。 如需有關**允許寫入時快取**屬性，請參閱[如何設定 File 傳送埠](http://msdn.microsoft.com/library/d801c5b7-da0a-4228-af0c-c2d450c251a9)。  
  
> [!NOTE]
>  設定**允許寫入時快取**屬性**True**作業系統發生失敗時增加資料遺失的可能性。 在此狀況下，記憶體中檔案快取內儲存的任何資料都會流失。  
  
#### <a name="zero-byte-files-received-by-the-file-adapter-are-deleted"></a>FILE 配接器接收的零位元組檔案已遭刪除  
  
##### <a name="problem"></a>問題  
 如果 FILE 接收配接器收取到空白 (零位元組) 檔案，便會刪除該檔案，並將類似以下的警告寫入 BizTalk Server 的應用程式記錄檔：  
  
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
  
##### <a name="cause"></a>原因  
 FILE 接收配接器依設計會刪除零位元組檔案。  
  
##### <a name="resolution"></a>解決方案  
 不需動作，此行為是經過設計的。