---
title: ESB 錯誤處理器管線 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a57752b1-8bca-4534-9e5b-7ce721a9490a
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1eb33c091c064c8a94939a8b9f2f0ee37f75881b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37015426"
---
# <a name="the-esb-fault-processor-pipeline"></a>ESB 錯誤處理器管線
[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]會安裝名為所有的傳送埠。使用 ESBFaultProcessor 的例外狀況傳送管線。 [圖 1] 顯示所有的屬性。例外狀況傳送埠。  
  
 ![所有的例外狀況傳送連接埠](../esb-toolkit/media/ch4-allexceptionssendport.gif "第 4 章第 AllExceptionsSendPort")  
  
 **圖 1**  
  
 **所有的組態。例外狀況傳送埠，包括其使用情況 ESBFaultProcessor 管線**  
  
 ESBFaultProcessor 管線包含下列管線元件： ESB 例外狀況的編碼器、 ESB 商務活動監控 (BAM) 追蹤器，並 ESB 轉換。  
  
 ALL。例外狀況傳送埠訂閱所有 ESB 錯誤訊息，並由 BizTalk 失敗訊息路由機制所產生的所有訊息。 圖 2 顯示篩選條件的所有屬性設定。例外狀況傳送埠。  
  
 ![篩選傳送埠](../esb-toolkit/media/ch4-filtersendport.gif "第 4 章第 FilterSendPort")  
  
 **圖 2**  
  
 **所有篩選條件屬性。例外狀況傳送連接埠定義的連接埠訂用帳戶**  
  
## <a name="the-fault-processor-pipeline-exception-encoder-component"></a>錯誤處理器管線例外狀況的編碼器元件  
 ESB 例外狀況的編碼器管線元件將正規化的 ESB 失敗的協調流程例外狀況路由機制和 BizTalk 失敗訊息路由機制，為標準的訊息，遵守 ESB 例外狀況報告中產生的錯誤訊息結構描述。  
  
 針對失敗的協調流程例外狀況路由的例外狀況，元件來擴充，並且會序列化所有的錯誤訊息屬性、 XLANG 訊息、 內容屬性，並**System.Exception**轉換為 XML 訊息的資訊。  
  
 針對失敗訊息路由的例外狀況，元件來新增應用程式名稱和其他環境的屬性，來充實資料，並套用到輸出 XML 訊息內容結構描述命名空間。  
  
 （選擇性） ESB 例外狀況的編碼器管線元件也可以套用 Microsoft InfoPath 處理指示到傳出訊息。 您可以在設計檢視中設定管線元件的屬性來修改 InfoPath 指示。 下列三個設計階段屬性會影響執行階段行為的 ESB 例外狀況的編碼器管線元件：  
  
- **EscapeCDATA。** 此屬性會決定是否該元件會逸出任何**CDATA**各節中找到保存訊息，以便 InfoPath 可以正確顯示。  
  
- **FaultDocumentNamespace。** 這個屬性具有預設值是**http://schemas.microsoft.biztalk.practices.esb.com/exceptionhandling**。 這可以修改為使用自訂的輸出命名空間之保存的訊息。  
  
- **ProcessingInstruction。** 這個屬性可以包含使用 ESB 例外狀況報告的錯誤結構描述符合任何 InfoPath 處理指示。 [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]包含符合下列的處理指示的 InfoPath 範本。  
  
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
 ESB BAM 追蹤器管線元件的 ESB 例外狀況的編碼器元件從接收訊息，並將所選的錯誤資料寫入 ESB 例外狀況管理架構安裝期間建立的 BAM 主要匯入資料表。  
  
 ESB BAM 追蹤器元件會使用**GetEventStream**管線內容，將下列欄位與活動記錄新增至 BAM 主要匯入資料庫的方法：  
  
- **應用程式**  
  
- **說明**  
  
- **FaultSeverity**  
  
- **ServiceName**  
  
- **錯誤類型**  
  
- **D**  
  
- **MachineName**  
  
- **MessageID**  
  
- **DateTime**  
  
- **FaultDescription**  
  
- **範圍。**  
  
- **FailureCategory**  
  
- **FaultGenerator**  
  
- **ServiceInstanceID**  
  
  ESB BAM 追蹤器元件會使用的訊息識別項 ( **MessageID**屬性) 值的 ESB 錯誤訊息，做為 BAM 活動識別碼。 ESB BAM 追蹤器元件會公開兩個您可以設定來變更其執行階段行為的設計階段屬性：  
  
- **已啟用。** 此屬性決定元件是否會處理訊息，寫入 BAM 資料庫。 當設定為**False**，元件只會將訊息傳送至管線中的下一個元件。  
  
- **FaultDocumentNamespace。** 這個屬性具有預設值是**http://schemas.microsoft.biztalk.practices.esb.com/exceptionhandling**。  
  
## <a name="the-fault-processor-pipeline-transform-component"></a>錯誤處理器管線轉換元件  
 ESB 錯誤處理器管線會使用 ESB 轉換管線元件來執行轉譯的結構描述相符 BizTalk SQL 配接器 (ExceptionSql.xsd) 格式的編碼的 ESB 錯誤訊息的 BizTalk 對應。 然後，元件會將轉換的訊息傳遞給 SQL 配接器，插入 ESB 管理入口網站資料庫中的 ESB 錯誤訊息。  
  
 ESB 轉換管線元件會公開三個可以修改以變更其執行階段行為的設計階段屬性：  
  
- **已啟用。** 這個屬性會啟用或停用元件。  
  
- **驗證。** 此屬性會指定訊息是否需要驗證。  
  
- **MapName。** 此屬性包含必須經過執行才能轉譯 ESB 管理入口網站資料庫中的儲存體的訊息對應的名稱。 以下是預設值。  
  
  ```  
  Microsoft.Practices.ESB.ExceptionHandling.Maps.FaultMessage_to_ExceptionSql,  
  Microsoft.Practices.ESB.ExceptionHandling.Maps,  
  Version=2.0.0.0,  
  Culture=neutral,  
  PublicKeyToken=c2c8b2b87f54180a  
  ```  
  
  所有管線元件可讓您都完成執行之後，BizTalk SQL Server 資料庫配接器會將錯誤訊息插入 ESB 管理入口網站資料庫中。