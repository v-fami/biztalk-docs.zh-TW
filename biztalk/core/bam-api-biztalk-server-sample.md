---
title: BAM API 範例 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 32a925f2-c7f4-4111-9c59-8865f15c6a89
caps.latest.revision: 20
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 899b28a95b6f07d7aec20868ea6b71138acfe60f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36987375"
---
# <a name="bam-api-biztalk-server-sample"></a>BAM API (BizTalk Server 範例)
BAM API 範例示範如何將對 BAM API 的呼叫整合到應用程式，以儲存可供您監控的關鍵資訊。  
  
## <a name="what-this-sample-does"></a>此範例的用途  
 此範例實作簡單的採購實例。 它會產生訂單、處理每筆訂單、建立出貨、建立和處理發票。 隨著範例執行，它會建立與更新 BAM 活動，以反映訂單與發票的明細和處理狀況。  
  
## <a name="how-this-sample-was-designed-and-why"></a>此範例的設計方式和原因  
 此範例旨在示範如何使用 BAM 來儲存來自非 BizTalk 協調流程之應用程式的資訊。 雖然應用程式是簡易的應用程式，卻示範了在實際執行應用程式中可能會用到的 BAM 的數個層面。 這些選項包括：  
  
- 構成單一活動的多個執行緒  
  
- 建立兩個活動之間的關係  
  
- 使用接續以允許使用不同的 ID 存取相同的活動  
  
  BAM API 範例包含三個主要類別： 一個用來處理採購訂單、 一個處理出貨、，以處理發票的另一個。 每個類別都**RunOnce**從佇列擷取訊息，然後再處理訊息的方法。 每個類別也有**執行**不斷呼叫的方法**RunOnce**方法。  
  
  **RunOnce**方法**PoApplication**類別會進行下列作業：  
  
1. 建立代表訂單的 XML 訊息。  
  
2. 開始 BAMApiPo 活動，並將訂單和訂單收到時間相關資訊新增到活動。  
  
3. 核准或拒絕訂單。  
  
4. 更新 BAMApiPo 活動以記錄訂單狀態 (已接受或已拒絕)。  
  
5. 如果已接受訂單**RunOnce**方法也會進行下列作業：  
  
   1.  建立代表要出貨之包裝的 XML 訊息，並將該訊息新增到出貨佇列。  
  
   2.  將代表訂單的 XML 訊息新增到訂單佇列，以包含在發票中。  
  
   3.  為 BAMApiPo 活動啟用接續。  
  
   4.  結束 BAMApiPo 活動。  
  
   **RunOnce**方法**ShipmentApplication**類別會進行下列作業：  
  
6. 從其佇列中擷取代表要出貨之包裝的 XML 訊息。  
  
7. 更新 BAMApiPo 活動以記錄包裝出貨的時間。  
  
8. 結束 BAMApiPo 活動。  
  
   **RunOnce**方法**InvoiceApplication**類別會進行下列作業：  
  
9. 從其佇列中擷取代表要開發票之訂單的 XML 訊息。  
  
10. 開始 BAMApiInvoice 活動。  
  
11. 為正在開發票的訂單建立 BAMApiInvoice 活動與 BAMApiPo 活動間的 BAM 關係。  
  
12. 將發票和發票建立時間相關資訊新增到 BAMApiPo 活動資訊。  
  
13. 在模擬等候支付發票款項的一段延遲時間後，將支付發票款項的時間新增到 BAMApiInvoice 活動。  
  
14. 結束 BAMApiInvoice 活動。  
  
    **Main**方法**MainApp**類別初始化應用程式。 它會執行下列工作：  
  
15. 會建立**DirectEventStream**物件。  
  
16. 啟動數個執行緒，並呼叫**執行**方法**POApplication**中每個執行緒的物件。  
  
17. 啟動數個執行緒，並呼叫**執行**方法**ShipmentApplication**中每個執行緒的物件。  
  
18. 啟動數個執行緒，並呼叫**執行**方法**InvoiceApplication**中每個執行緒的物件。  
  
    **Global**類別會定義常數所使用的範例應用程式，例如要建立的執行緒數目和拒絕訂單的百分比。  
  
    除了 Visual Studio 方案中，此範例也會包含定義活動的 Microsoft Excel 檔案。  
  
## <a name="where-to-find-this-sample"></a>可在何處找到此範例  
 您可以找到在此範例*\<範例路徑\>* \BAM\BamApiSample。  
  
 下表顯示此範例中的檔案，並描述其用途。  
  
|檔案|描述|  
|----------|-----------------|  
|BamApiSample.cs|檢測的應用程式。|  
|BamApiSample.csproj|檢測的應用程式專案。|  
|BamApiSample.sln|檢測的應用程式方案。|  
|BamApiSample.xls|BAM 定義樣式表。|  
|Cleanup.bat|移除所部署範例檔的批次檔。|  
|Input.txt|範例攔截器組態輸入。|  
|InterceptorConfig.cs|API 範例的攔截器組態程式碼。|  
|InterceptorConfig.csproj|攔截器組態專案。|  
|Invoice_config.xml|發票攔截器組態。|  
|Invoice_interceptor.bin|序列化發票攔截器。|  
|PurchaseOrder_config.xml|訂單攔截器組態。|  
|PurchaseOrder_interceptor.bin|序列化訂單攔截器。|  
|Setup.bat|用來部署和登錄範例檔的批次檔。|  
|Shipment_config.xml|出貨攔截器組態。|  
|Shipment_interceptor.bin|已序列化的出貨攔截器。|  
  
## <a name="run-the-bam-api-sample"></a>執行 BAM API 範例  
  
1.  開啟命令提示字元，以系統管理員身分，然後執行*\<範例路徑\>* \BAM\ BamApiSample\setup.bat。  
  
2.  系統管理員身分啟動 Visual Studio，然後開啟*\<範例路徑\>* BAMAPISAMPLE\BAMAPISAMPLE.SLN 方案。 
  
    > [!IMPORTANT]
    >  必須在 BamApiSample.cs 檔案的 `//#define Interceptor` 該行前加上註解符號。請勿移除此行中的 “//”。 BAM API 範例僅使用不在 `#if Interceptor` 前置處理器指示詞內的程式碼。  
  
3.  建置方案。  
  
4.  執行*\<範例路徑\>* \BAM\BamApiSample\bin\debug\BamApiSample.exe。  
  
     輸出看起來會向下面這樣：  
  
    ```  
    ...  
    New Purchase Order #17 Received  
    8 was shipped as pkg#87  
    New Purchase Order #18 Received.  
    Shipping package pkg#87 via DHL  
    13 was Approved.  
    18 was Rejected.  
    17 was Rejected.  
    11 was shipped as pkg#114  
    16 wsas Rejected.  
    Shipping package pkg#114 via DHL  
    Invoice #5 send for {2 5 1 9 4 8 11 }  
    Package pkg#49 was delivered  
    New Purchase Order #19 Received.  
    ...  
    ```  
  
5.  約 1 分鐘後，按下 CTRL+C 或關閉命令提示字元視窗以停止 BamApiSample 程式。  
  
## <a name="view-the-results"></a>檢視結果
  
1.  開啟 SQL Server Management Studio。  
  
2.  在 SQL Server Management Studio 中，展開伺服器，展開**資料庫**，展開**BAMPrimaryImport**，然後展開**資料表**。  
  
3.  以滑鼠右鍵按一下 **[dbo.bam_bamapiinvoice_active]** ，然後按一下**開啟資料表**。 如果您使用 SQL Server，請按一下**選取前 1000 個資料列**。  
  
     bam_BAMApiInvoice_Active 資料表的內容會顯示於右窗格。 資料表中的每個資料列各代表一個已啟動但尚未完成的 BAMApiInvoice 活動。  
  
4.  以滑鼠右鍵按一下 **[dbo.bam_bamapipo_completed]** ，然後按一下**開啟資料表**。 如果您使用 SQL Server，請按一下**選取前 1000 個資料列**。  
  
     bam_BAMApiPo_Completed 資料表的內容會顯示於右窗格。 資料表中的每個資料列各代表一個已完成的 BAMApiPo 活動。