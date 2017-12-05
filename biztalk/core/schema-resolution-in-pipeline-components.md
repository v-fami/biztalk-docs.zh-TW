---
title: "管線元件中的結構描述解析 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipelines, schema resolution
- pipeline components, schema resolution
- schemas, pipeline components
ms.assetid: 35a79a6f-788b-4ca1-8483-36dcba5ae580
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 897c25ecb64a3038a6992b9c4caf927ba3e2d805
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="schema-resolution-in-pipeline-components"></a>管線元件中的結構描述解析
管線解譯器和組合器元件使用 XSD 結構描述來處理訊息。 此類結構描述包含如升級屬性清單、辨別欄位、一般檔案訊息的註解以及 XML 封套的註解等資訊。  
  
 標準解譯器和組合器元件使用結構描述類型名稱及訊息類型以支援擷取部署的結構描述。 部分元件使用結構描述類型名稱和訊息類型來擷取，而其他元件 (例如，一般檔案解譯器) 則僅使用結構描述類型來擷取。  
  
 接收 XML 訊息的管線元件以檢查訊息根項目和命名空間的方式來判斷訊息。 例如，下列 XML 的訊息類型為 "http://MyDocument.org#MyDocument"。  
  
```  
<ns0:MyDocument xmlns:ns0="http://MyDocument.org">  
  
</ns0:MyDocument>  
```  
  
 如果結構描述沒有為其定義的命名空間，訊息類型是"\<**rootNode**\>"。 例如，若先前的範例 XML 沒有命名空間，則訊息類型是 "MyDocument"。  
  
 標準管線元件使用訊息類型從資料庫擷取適當的結構描述。 預設 XML 接收和傳送管線永遠會使用在執行階段從訊息 XML 內容動態探索到的訊息類型，判斷要載入哪個結構描述 (除非管線元件設定為允許無法辨識的訊息)。 XML 解譯器透過使用此機制可移除訊息信封，不過，若 XML 組合器不知道要使用何種信封結構描述，則無法建立外寄訊息的信封。  
  
 您要在管線設計師內的 XML 組合器的組態屬性中指定信封結構描述。  
  
## <a name="how-schemas-are-resolved"></a>結構描述解析的方式  
 假設您未直接在 XmlDisassembler 中指定結構描述，結構描述會以下列方式進行解析：  
  
1.  首先，會使用根節點名稱和命名空間 (例如 http://MyNamespace#MyRoot) 在部署的結構描述上進行不合格的搜尋。 如果找到唯一的符合項目，則會解析該結構描述。 如果找到多個符合項目，這些項目只有版本號碼不同，且只有一個是作用中，則會使用該版本，並解析該結構描述。 如果相同的結構描述在多個應用程式中都是作用中，則會找到多個作用中的結構描述，搜尋就會繼續執行下列步驟 2。  
  
2.  如果步驟 1 的多個相符項目無法解決，搜尋會限定在管線正在執行中的組件。 如果相同的組件中找到唯一的結構描述在管線正在執行中，則會解析結構描述。  
  
3.  如果仍然沒有符合的項目，就會使用發行者來解析結構描述。 搜尋可使用根節點、命名空間和公開金鑰 Token 縮小範圍。 如果使用此搜尋找到唯一的結構描述，則會解析該結構描述。  
  
4.  無法解析結構描述。 傳回錯誤，指出找不到唯一的結構描述。  
  
 如需其他考量包括對結構描述解析的 SQL Server 定序和區分大小寫效果，請參閱[命名空間管理](../core/namespace-management.md)。  
  
 若要在 XML 組合器中建立信封或在一般檔案組合器中建立標頭和結尾，可執行下列其中一個動作：  
  
-   在 XML 組合器的組態屬性中建立自訂傳送管線以及指定信封的結構描述。 這要在管線設計師中完成。  
  
-   在 [BizTalk Server 管理] 主控台中，為傳送埠上的傳送管線屬性指定 XMLTransmit。 在 [EnvelopeDocSpecNames] 屬性中，按一下省略符號以設定管線屬性並指定信封的結構描述。  
  
 若相同結構描述的數個版本有意或無意地部署到資料庫中 (例如，並存部署或多個實例沒有唯一訊息類型)，則依訊息類型解析結構描述可能無法運作。 若依訊息類型解析結構描述失敗，則會在事件日誌中加入 "schema ambiguity" (結構描述模擬兩可) 錯誤。 若要確保依訊息類型解析結構描述成功，請執行下列其中一個動作：  
  
-   在與自訂管線相同的 BizTalk 專案中定義結構描述。  
  
-   使用與包含管線的組件相同的金鑰簽署具有結構描述的組件。  
  
-   明確指定管線元件中的結構描述 (訊息類型名稱在整個 BizTalk 管理資料庫上應為唯一)。  
  
> [!IMPORTANT]
>  當相同組件中的結構描述共用訊息類型時，不可在同一個管線元件組件中包含結構描述，因為模擬兩可解析有其限制，相反地，而是要參考管線元件組件外的結構描述。 即使在自訂管線的管線元件中已明確指定結構描述類型名稱，但是只要結構描述和管線元件在相同組件中，模擬兩可解析就不能運作。  
  
> [!NOTE]
>  使用的自訂管線元件**IPipelineContext**取得部署的結構描述應該取得結構描述的結構描述型別，只有當結構描述類型名稱未指定元件在執行階段，並取得訊息類型只能由結構描述如果在元件執行時，無法使用結構描述類型資訊。  
  
## <a name="see-also"></a>請參閱  
 [管線元件](../core/pipeline-components.md)