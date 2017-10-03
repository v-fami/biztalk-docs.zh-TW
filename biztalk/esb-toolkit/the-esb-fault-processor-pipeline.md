---
title: "ESB 錯誤處理器管線 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a57752b1-8bca-4534-9e5b-7ce721a9490a
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ebd9a6cecf5353ab72cea0d67b06f3402fc1716a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="the-esb-fault-processor-pipeline"></a>ESB 錯誤處理器管線
[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]安裝名為所有的傳送埠。使用 ESBFaultProcessor 的例外狀況傳送管線。 圖 1 顯示所有的屬性。例外狀況傳送埠。  
  
 ![所有例外狀況傳送埠](../esb-toolkit/media/ch4-allexceptionssendport.gif "第 4 章第 AllExceptionsSendPort")  
  
 **圖 1**  
  
 **所有的組態。例外狀況傳送埠，包括其 ESBFaultProcessor 管線的使用情形**  
  
 ESBFaultProcessor 管線包含下列管線元件： ESB 例外狀況的編碼器、 ESB 商務活動監控 (BAM) 追蹤程式，並 ESB 轉換。  
  
 ALL。例外狀況傳送埠訂閱所有 ESB 錯誤訊息，並由 BizTalk 失敗訊息路由機制所產生的所有訊息。 圖 2 顯示篩選條件的所有屬性設定。例外狀況傳送埠。  
  
 ![篩選傳送埠](../esb-toolkit/media/ch4-filtersendport.gif "第 4 章第 FilterSendPort")  
  
 **圖 2**  
  
 **所有篩選條件屬性。例外狀況傳送連接埠定義的連接埠訂用帳戶**  
  
## <a name="the-fault-processor-pipeline-exception-encoder-component"></a>錯誤處理器管線例外狀況的編碼器元件  
 ESB 例外狀況的編碼器管線元件將正規化的 ESB 無法協調流程的例外狀況路由機制和 BizTalk 失敗訊息路由機制為標準的訊息，遵守 ESB 例外狀況報告中產生的錯誤訊息結構描述。  
  
 無法協調流程的例外狀況路由的例外狀況，元件加速功能，並且會序列化所有的錯誤訊息屬性、 XLANG 訊息、 內容屬性，以及**System.Exception**轉換為 XML 訊息的資訊。  
  
 失敗訊息路由傳送的例外狀況，元件加入應用程式名稱和其他環境的屬性，來充實資料，以及它適用於輸出 XML 訊息內容結構描述命名空間。  
  
 （選擇性） ESB 例外狀況的編碼器管線元件也可以套用 Microsoft InfoPath 處理指示到傳出訊息。 您可以藉由設定管線元件的屬性在設計檢視中修改 InfoPath 指示。 下列三個設計階段屬性會影響 ESB 例外狀況的編碼器管線元件的執行階段行為：  
  
-   **EscapeCDATA。** 此屬性會決定是否此元件將逸出任何**CDATA**區段中找到保存訊息，以便 InfoPath 可以正確顯示。  
  
-   **FaultDocumentNamespace。** 這個屬性具有預設值是**http://schemas.microsoft.biztalk.practices.esb.com/exceptionhandling**。 修改此設定會保存訊息使用自訂輸出的命名空間。  
  
-   **ProcessingInstruction。** 這個屬性可以包含任何符合 ESB 例外狀況報告錯誤結構描述的 InfoPath 處理指示。 [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]包括符合下列的處理指示的 InfoPath 範本。  
  
    ```  
    <?mso-infoPathSolution solutionVersion="1.0.0.346" productVersion="11.0.6565"  
    PIVersion="1.0.0.0"   
    href=file:///\\localhost\publish\Microsoft.Practices.ESB.ExceptionHandling.InfoPath.Reporting.xsn  
    name="urn:schemas-microsoft-com:office:infopath:  
    Microsoft-Practices-ESB-ExceptionHandling-InfoPath-Reporting:  
    http---schemas-microsoft-biztalk-practices-esb-com-exceptionhandling"  
    language="en-us" ?><?mso-application progid="InfoPath.Document"?>  
    ```  
  
## <a name="the-fault-processor-pipeline-bam-tracker-component"></a>錯誤處理器管線 BAM 追蹤器元件  
 ESB BAM 追蹤器管線元件 ESB 例外狀況的編碼器元件從接收訊息，並將所選的錯誤資料寫入 BAM 主要匯入資料表，在 ESB 例外狀況管理架構的安裝期間建立。  
  
 ESB BAM 追蹤器元件會使用**GetEventStream**管線內容，將下列欄位為活動記錄，到 BAM 主要匯入資料庫的方法：  
  
-   **應用程式**  
  
-   **說明**  
  
-   **FaultSeverity**  
  
-   **ServiceName**  
  
-   **ErrorType**  
  
-   **F**  
  
-   **MachineName**  
  
-   **MessageID**  
  
-   **DateTime**  
  
-   **FaultDescription**  
  
-   **範圍。**  
  
-   **FailureCategory**  
  
-   **FaultGenerator**  
  
-   **ServiceInstanceID**  
  
 ESB BAM 追蹤器元件使用的訊息識別項 ( **MessageID**屬性) 值的 ESB 錯誤訊息為 BAM 活動識別碼。 ESB BAM 追蹤器元件會公開兩個設計階段屬性，您可以變更其執行階段行為設定：  
  
-   **啟用。** 此屬性決定元件是否將處理訊息，並寫入 BAM 資料庫。 當設定為**False**，元件只會將訊息傳送管線中的下一個元件。  
  
-   **FaultDocumentNamespace。** 這個屬性具有預設值是**http://schemas.microsoft.biztalk.practices.esb.com/exceptionhandling**。  
  
## <a name="the-fault-processor-pipeline-transform-component"></a>錯誤處理器管線轉換元件  
 ESB 錯誤處理器管線會使用 ESB 轉換管線元件來執行轉譯格式符合結構描述，BizTalk SQL 配接器 (ExceptionSql.xsd) 編碼的 ESB 錯誤訊息的 BizTalk 對應。 然後，元件會將轉換的訊息傳遞給 SQL 配接器，ESB 管理入口網站資料庫中插入 ESB 錯誤訊息。  
  
 ESB 轉換管線元件會公開三個可以修改，以變更其執行階段行為的設計階段屬性：  
  
-   **啟用。** 這個屬性會啟用或停用元件。  
  
-   **驗證。** 此屬性會指定是否需要驗證訊息。  
  
-   **MapName。** 此屬性包含必須經過執行才能轉譯 ESB 管理入口網站資料庫中儲存的訊息對應的名稱。 以下是預設值。  
  
    ```  
    Microsoft.Practices.ESB.ExceptionHandling.Maps.FaultMessage_to_ExceptionSql,  
    Microsoft.Practices.ESB.ExceptionHandling.Maps,  
    Version=2.0.0.0,  
    Culture=neutral,  
    PublicKeyToken=c2c8b2b87f54180a  
    ```  
  
 所有的管線元件可讓您完成執行之後，BizTalk SQL Server 資料庫配接器會插入 ESB 管理入口網站資料庫的錯誤訊息。