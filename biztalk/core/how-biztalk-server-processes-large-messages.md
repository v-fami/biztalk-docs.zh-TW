---
title: BizTalk Server 如何處理大型訊息 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 62c070be-dff5-4349-9e36-dd3a7caf1752
caps.latest.revision: 33
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f17509983e7eab7b8743c8036c429c886b0b9265
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37016525"
---
# <a name="how-biztalk-server-processes-large-messages"></a>BizTalk Server 如何處理大型訊息
## <a name="what-is-a-large-message"></a>何謂大型訊息？  
 可惜這個問題的答案並不直接受限於特定訊息大小，反而取決於 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統中的特定瓶頸而定。 與大型訊息相關的問題可分為下列類別：  
  
-   **記憶體不足錯誤**特定類型的訊息處理，例如對應、 驗證和屬性升級-會將整個訊息載入記憶體。 若記憶體中的訊息大小超過可用資源，則會發生記憶體不足錯誤。 屬於此類型的訊息之大小閾值遠低於未載入記憶體的訊息之大小閾值。 例如，一個 10 MB 的一般檔案剖析為 XML 並對應後，可能會成長 10 倍或更多，而耗用超過 100 MB 的記憶體，但是一個未剖析或對應的 100 MB 的 XML 文件事實上可能僅耗用 1 MB 的記憶體，因為它會串流至 MessageBox 資料庫。  
  
-   **未載入記憶體的訊息的效能問題**不一定要載入到記憶體的訊息串流至 MessageBox 資料庫，使用.NET XmlReader 介面。 雖然它們未受到必須載入記憶體的訊息之大小限制，但是有一些重要因素會影響 BizTalk Server 處理串流至 MessageBox 資料庫之資料的方式。  
  
## <a name="factors-that-affect-the-processing-of-large-messages"></a>影響大型訊息處理的因素  
 原始訊息大小、訊息格式以及訊息處理類型都會影響 BizTalk Server 處理大型訊息的方式。  
  
- **原始訊息大小**BizTalk Server 所接收之訊息的大小是最明顯的大訊息時，會由 BizTalk Server 處理指示。 在整個訊息均載入記憶體時，訊息的原始大小對效能的影響遠大於在訊息串流至 MessageBox 資料庫時其對效能的影響。  
  
- **訊息格式**到 BizTalk Server 中有兩種主要格式接收訊息： XML 檔或一般檔案。  
  
  -   **XML 檔案**為了讓 BizTalk Server 可以執行任何處理不透過路由傳遞訊息，訊息必須是 XML 檔案格式。 若要處理的檔案以 XML 格式接收，則大部分會保留原始大小。  
  
  -   **一般檔案**一般檔案必須先剖析為 XML 格式，BizTalk Server 才能執行處理而不透過路由傳遞。 將一般檔案剖析為 XML 檔案會大幅增加檔案大小。 一般檔案不包含 XML 標記及其資料的描述性資訊。 XML 檔案，相反地，可包裝其所有資料具描述性的 XML 標記。 在部分實例中，剖析會使一般檔案的大小增加 10 倍或更多，視該檔案的 XML 標記中包含的描述性資料多寡而定。  
  
  -   **一般檔案文件包裝在 XML 文件中單一 CDATA 區段節點**這種類型的文件是 XML 和一般檔案的組合，可能會造成問題，因為 BizTalk Server 必須將整個包裝的一般檔案文件載入前的記憶體正在處理它。  
  
- **訊息處理的類型**在 BizTalk Server 中，有兩種訊息處理類型： 僅路由以及對應。 繫結至執行的訊息處理類型之效能變數是訊息大小以及訊息是否載入記憶體。  
  
  - **僅路由**若 BizTalk Server 僅用於升級的訊息屬性為基礎的路由傳送訊息，然後將訊息串流至 Messagebox 資料庫，使用.NET XmlReader 介面，而且訊息部分不個別載入記憶體。 在此案例中，記憶體不足錯誤將不是問題，而主要的考量是將非常大型的訊息 (超過 100 MB) 寫入 MessageBox 資料庫所需的時間量。 BizTalk Server 開發團隊已成功測試，在僅執行路由時處理高達 1 GB 大小的訊息。  
  
     決定在此案例中的效能的主要因素是**大型訊息分割大小**用來分割資料至資料庫。 **大型訊息分割大小**可設定的選項位於**BizTalk 群組屬性**組態 頁面上，預設值為 102400 位元組 (100 KB)。 增加此值會降低將訊息串流至 MessageBox 資料庫所需的往返次數。  
  
  - **對應**轉換對應文件可以是需要大量記憶體的作業。 當文件以對應轉換時，BizTalk Server 會將訊息傳遞至.Net XSLCompileTransform 類別，它會載入 XSL 樣式表。 Load 方法順利完成之後，轉換方法可以是從多個執行緒同時呼叫。 [XslCompiledTransform 類別](http://go.microsoft.com/fwlink/p/?LinkID=282683)XSLCompiledTransform 類別提供的詳細資訊。  
  
     [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 藉由實作可設定的訊息大小閾值，供轉換期間將文件載入記憶體，以大幅改善大型文件的記憶體管理。 大小低於此閾值的任何訊息都會在記憶體中處理，而大小大於此閾值的任何訊息則會緩衝至檔案系統，以降低記憶體需求。 預設訊息大小閾值是 1 MB。  
  
## <a name="guidelines-for-processing-large-messages"></a>處理大型訊息的指導方針  
 請遵循這些指導方針，以改善在 BizTalk Server 中處理大型訊息的效能：  
  
1. 調整訊息大小閾值，若在對應期間超過此閾值，則將文件緩衝至檔案系統。 若要修改大小閾值，建立名為 DWORD 值**TransformThreshold**在 BizTalk Server 登錄的下列位置：  
  
   ```  
   HKLM\Software\Microsoft\BizTalk Server\3.0\Administration\TransformThreshold  
   ```  
  
    建立此值之後，輸入十進位值的位元組數目，以設定新的閾值。 例如，輸入十進位值 2097152，以增加訊息大小閾值至 2 MB (從預設的 1 MB)。 以大量可用的記憶體增加系統上的此值來改善輸送量。 將文件緩衝至磁碟機，以耗用整體輸送量成本的方式來節省記憶體。  
  
   > [!NOTE]
   >  根據預設，對應期間緩衝至檔案系統的文件會寫入 *%temp%* BizTalk Server 電腦的目錄。 變更的設定 *%temp%* 非系統磁碟機，以改善效能，對應期間緩衝至檔案系統的大型訊息的環境變數。  
  
2. 讓協調流程中使用的對應最小化：  
  
   -   若您在協調流程中使用對應擷取或設定與商務邏輯搭配使用的屬性，請改以辨別欄位或升級屬性取代。 使用對應擷取或設定值時，文件會載入記憶體。 使用辨別欄位或升級屬性時，協調流程引擎會存取訊息內文而不會將文件載入記憶體。  
  
   -   若您使用對應將數個欄位彙總成一個欄位，請使用辨別欄位或升級屬性搭配協調流程變數，以累計結果集。  
  
   -   請勿將協調流程設定為含有多個轉換圖形輸入。 含有多個轉換圖形輸入的協調流程在對應時不會串流至檔案系統。 如果文件大小超過指定的 TransformThreshold 登錄值，這項限制將導致要對應的整份文件均載入記憶體。 這個問題可行的解決方法之一就是在接收埠層級套用轉換，如此一來，協調流程將永不接受一個以上的轉換圖形輸入。  
  
3. 調整**大型訊息分割大小**屬性上公開**BizTalk 群組屬性**組態 頁面上：  
  
    如果接收的訊息之記憶體中大小超過指定的位元組數目**大型訊息分割大小**則訊息會分割成片段，指定的大小和片段會寫入至下 MessageBoxMicrosoft Distributed Transaction Coordinator (MSDTC) 交易，如下所示的內容：  
  
   1.  若內送訊息正在現有 MSDTC 交易的環境下發佈，則會在將訊息分割寫入 MessageBox 時，使用此交易。 例如，若內送訊息由設定為必要交易的交易配接器發佈，則在將訊息分割寫入 MessageBox 時，會使用現有的交易。  
  
   2.  若內送訊息不在現有 MSDTC 交易的環境下發佈，則會建立新的 MSDTC 交易以寫入訊息分割。  
  
   -   增加的值**大型訊息分割大小**以減少與大型訊息會分割並降低建立關聯的 MSDTC 交易的發生率的頻率。 您應該執行此動作，因為從效能觀點來看，過度使用 MSDTC 交易的代價很高。 請注意，增加此值也可能增加使用的可用記憶體量。  
  
   -   若將訊息寫入 MessageBox 所花費的時間超過 MSDTC 交易逾時允許的上限 (60 分鐘)，則交易會逾時、導致錯誤，且寫入訊息的嘗試會失敗並回復。 **大型訊息分割大小**值應該增加足夠處理非常大型的訊息時避免發生這個問題。 視可用的記憶體而定，此值最多可增加到 1000000 個位元組的值。  
  
   -   訊息中的每個訊息分割都會對 MessageBox 資料庫建立一或多個 SQL Server 資料庫鎖定。 當鎖定數目超過數十萬時，SQL Server 可能會開始產生「鎖定不足」錯誤。 如果發生此問題，請增加**大型訊息分割大小**以降低對 MessageBox 資料庫的 SQL Server 資料庫鎖定數目。  
  
4. 若發生「鎖定不足」錯誤，請考慮將您的 MessageBox 資料庫儲存在 64 位元版本的 SQL Server 上。 在 64 位元版本的 SQL Server 上，可用的鎖定數目大幅提高。  
  
5. 調整**大型訊息閾值**屬性上公開**BizTalk 群組屬性**組態 頁面上：  
  
    為訊息批次處理時，如果記憶體中大小的訊息批次達到指定的位元組數目**大型訊息閾值**然後已處理的訊息批次部分寫入 MessageBox 之前處理訊息批次的其餘部分。 此動作是在 MSDTC 交易環境下執行，如下所示：  
  
   1. 若訊息批次正在現有 MSDTC 交易的環境下發佈，則會在將處理的訊息批次部分寫入 MessageBox 時，使用此交易。 例如，若內送訊息批次由設定為必要交易的交易配接器發佈，則在將處理的訊息批次部分寫入 MessageBox 時，會使用現有的交易。  
  
   2. 若訊息批次不在現有 MSDTC 交易的環境下發佈，則必須建立新的 MSDTC 交易，以將訊息批次部分寫入 MessageBox。 使用 MSDTC 交易可確保指定的訊息批次之所有部分均成功寫入 MessageBox 資料庫。  
  
      **大型訊息閾值**設定可直接套用至訊息的批次，但訊息批次可以設定為值為 1，因為**大型訊息閾值**設定也可以間接適用於個別訊息。 例如當一個訊息的訊息批次超過指定時才**大型訊息閾值**參數則**大型訊息閾值**實際上只適用於批次中的單一訊息。  
  
   -   **大型訊息閾值**應該調整參數，以減少用來分配訊息批次至 MessageBox 的 MSDTC 交易的建立。 您應該執行此動作，因為從效能觀點來看，過度使用 MSDTC 交易的代價很高。 使用下列計算來判斷哪些的最小值**大型訊息閾值**設定應該避免建立不必要的 MSDTC 交易：  
  
       ```  
       Batch Size * Average size (in bytes) of each message in the batch after being processed by the receive pipeline < Large message threshold  
       ```  
  
        只要以位元組為單位的訊息批次的總大小超過指定的值，如**大型訊息閾值**則不需要初始化 MSDTC 交易的 BizTalk 來分配訊息批次至 MessageBox資料庫。