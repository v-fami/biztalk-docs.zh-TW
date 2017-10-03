---
title: "File 配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: File adapters
ms.assetid: e4f6e94b-89b8-42ba-a4c2-a629f1107bb1
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ceb4f0728eb6fac66fb0fc5f84b117b37ba84121
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="file-adapter"></a>FILE 配接器
FILE 配接器負責 Microsoft BizTalk Server 的檔案傳輸。 File 配接器是由兩個配接器所組成 — 接收配接器和傳送配接器。  
  
 本節討論 FILE 接收配接器和 FILE 傳送配接器的工作流程與批次支援。  
 
## <a name="file-receive-adapter"></a>File 接收配接器  
  
使用檔案接收配接器從檔案讀取訊息，並將其發行到伺服器。 接收配接器會讀取檔案，並建立 BizTalk 訊息物件，因此，BizTalk Server 可以處理訊息。 讀取檔案時，配接器會鎖定檔案，以確保檔案內容不會遭到修改。  
  
> [!NOTE] 
> FILE 接收配接器不會拾取唯讀檔案或系統檔案。  
  
 FILE 接收配接器從本機檔案系統或網路共用上的檔案讀取訊息。 當網路共用上的指定位置由於網路問題而無法使用時，接收配接器會重試讀取作業 (重試次數可在 [BizTalk Server 管理] 主控台中設定)。 訊息已讀取並成功接受 「 BizTalk 傳訊引擎之後，接收配接器會從檔案系統或網路共用刪除的檔案。 若訊息已讀取但管線並未成功處理訊息，則配接器會將訊息放入擱置的佇列中，然後從檔案系統或網路共用刪除檔案。 若 FILE 接收配接器無法提交或擱置要給 MessageBox 資料庫的訊息，則不會從檔案系統或網路共用刪除原始檔案。  
  
 您也可以將 FILE 接收配接器設定為在處理檔案時將檔案重新命名。 您應該重新命名檔案，以確保在接收位置關閉後重新啟動時，接收配接器不會產生重複的訊息。 這是檔案接收位置的可設定選項。 依照預設，重新命名為停用。 啟用重新命名時，FILE 接收配接器會將副檔名 .BTS-WIP 附加至檔案。 然後，接收配接器會從接收位置中已重新命名的檔案讀取訊息，並將它提交至伺服器。 在接收配接器已成功提交檔案之後，接收配接器會從檔案系統或網路共用刪除已重新命名的檔案。 若訊息已經讀取但在管線中處理失敗，則接收配接器會將訊息放在 MessageBox 資料庫擱置佇列中，並從網路共用刪除已重新命名的檔案。  
  
> [!NOTE] 
> 重新命名的檔案不會影響效能。  
  
 如果 File 接收配接器成功讀取訊息，但是未成功將訊息儲存到 MessageBox 資料庫中，則重新命名的檔案會還原為原始名稱，而且副檔名不會是 .BTS-WIP。 請注意，若開啟重新命名選項，則接收配接器不會讀取副檔名為 .BTS-WIP 的檔案。  
  
#### <a name="using-file-change-notifications-and-polling"></a>使用檔案變更告知和輪詢
  
 File 接收配接器倚賴 Windows 檔案變更告知決定何時從指定的目錄或共用挑選檔案。 如果 File 接收配接器在檔案完全寫入指定的目錄或共用之前收到 Windows 檔案變更告知，則檔案將會遭到鎖定，而且 File 接收配接器將不會擷取檔案。 在此案例中，File 接收配接器會主動輪詢指定的目錄或共用**輪詢間隔 （毫秒）**上指定**進階設定**對話方塊可以設定時File 接收位置。 當 File 接收配接器輪詢目錄或共用時，會從共用擷取未鎖定的檔案，並且將檔案提交至 MessageBox 資料庫。  
  
> [!NOTE]
>  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] File 配接器僅在 NTFS 檔案系統上進行過測試，而且僅在該系統上支援。  
  
 下列 Windows 檔案變更告知將造成 File 接收配接器從指定的位置選取檔案：  
  
 `FILE_NOTIFY_CHANGE_ATTRIBUTES`
  
 監看目錄或樹狀子目錄中的任何屬性變更都會造成變更告知等待作業傳回。  
  
 `FILE_NOTIFY_CHANGE_FILE_NAME`  
  
 監看目錄或樹狀子目錄中的任何檔案名稱變更都會造成變更告知等待作業傳回。 變更包括重新命名、建立或刪除檔案名稱。  
  
 `FILE_NOTIFY_CHANGE_SIZE`  
  
 監看目錄或樹狀子目錄中的任何檔案大小變更都會造成變更告知等待作業傳回。 作業系統只會在檔案寫入磁碟時偵測檔案大小的變更。 如果是使用大量快取的作業系統，則只會在快取有效排清時進行偵測。  
  
 `FILE_NOTIFY_CHANGE_LAST_WRITE`  
  
 監看目錄或樹狀子目錄中檔案上次寫入時間的任何變更都會造成變更告知等待作業傳回。 作業系統只會在檔案寫入磁碟時偵測上次寫入時間的變更。 如果是使用大量快取的作業系統，則只會在快取有效排清時進行偵測。  
  
 如需有關**FindFirstChangeNotification**函式，請參閱[https://msdn.microsoft.com/library/windows/desktop/aa364417(v=vs.85).aspx](https://msdn.microsoft.com/library/windows/desktop/aa364417(v=vs.85).aspx).  
  
### <a name="file-receive-adapter-batching-support"></a>FILE 接收配接器批次支援
  
 FILE 接收配接器以批次方式提交訊息到伺服器。 首先，FILE 接收配接器透過收集接收位置中可用的所有可讀取檔案，在每個接收位置建置單一批次。 當已經收集到所有可用的檔案時，或收集的檔案數量超過批次大小上限時，接收配接器會將批次提交至 MessageBox 資料庫。  
  
 在批次中所有訊息已成功讀取並提交至 MessageBox 資料庫之後，FILE 接收配接器會從接收位置刪除對應的檔案。 若批次中的部分訊息無法處理，則 FILE 接收配接器會擱置它們，並從接收位置刪除對應的檔案。 若部分或全部訊息無法儲存在 MessageBox 資料庫中，則會回復整個批次作業，接收位置中所有對應的檔案皆維持不變。  
  
## <a name="file-send-adapter"></a>FILE 傳送配接器
  
 FILE 傳送配接器將訊息從 MessageBox 資料庫傳輸至指定的目的地址 (URL)。 您可以使用與訊息內容屬性相關的萬用字元來定義 URL，即檔案路徑與檔案名稱。 在將訊息寫入檔案之前，FILE 傳送配接器會將萬用字元解析為實際的檔案名稱。  
  
 正在將訊息寫入檔案時，FILE 傳送配接器會從 BizTalk 訊息物件的內文部分取得訊息內容。 FILE 傳送配接器會忽略 BizTalk 訊息物件中的其他訊息部分。 在 FILE 配接器將訊息寫入檔案之後，它會從 MessageBox 資料庫刪除訊息。 FILE 配接器直接或使用檔案系統快取將檔案寫入檔案系統，如此可改善效能，對大型檔案特別有用。  
  
### <a name="file-send-adapter-batching-support"></a>FILE 傳送配接器批次支援
  
 FILE 傳送配接器從 MessageBox 資料庫取得訊息批次並將它們寫入檔案系統或網路共用上目的地位置的檔案中。 檔案傳送配接器批次大小設定並不會預設為 20。 如果 BizTalk Server 無法將某些批次內的訊息寫入至檔案，系統會重新提交至 MessageBox 資料庫，重試處理這些訊息。 您可以使用 [BizTalk Server 管理] 主控台來設定重試間隔與重試計數。  
  
 
## <a name="in-this-section"></a>本節內容  
  
-   [設定 FILE 配接器](../core/configure-the-file-adapter.md) 
  
-   [設定 File 配接器時的限制](../core/restrictions-when-configuring-the-file-adapter.md)  
