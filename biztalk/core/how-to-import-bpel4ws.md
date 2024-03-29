---
title: 如何匯入 BPEL4WS |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3626fcb9-8e7d-4812-a0c9-bde6e7954ec8
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0043cca1305f0acf7f07878acd7e75b1390ffea5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36995967"
---
# <a name="import-bpel4ws-in-biztalk-server"></a>在 BizTalk Server 中匯入 BPEL4WS
您可以從現有的 BPEL4WS 匯入，以建立協調流程。  
  
> [!IMPORTANT]
>  這個版本的 BizTalk Server 支援 BPEL4WS 1.1。 您不能匯入或匯出 BPEL4WS 1.0。  
  
 如需如何匯入 BPEL4WS 的範例，請參閱 < [BPEL 匯入 （BizTalk Server 範例）](../core/bpel-import-biztalk-server-sample.md)。  
  
## <a name="import-bpel4ws-into-an-orchestration"></a>在符合 BPEL4WS 匯入到協調流程  
  
1. 建立新專案。  
  
2. 從 [BizTalk 專案] 類型，按兩下 [BizTalk Server BPEL 匯入專案]，或選取 [BizTalk Server BPEL 匯入專案] 並按 [確定]。  
  
3. 在精靈中，選取必須匯入的 BPEL、WSDL 和 XSD 檔案，以產生新 BizTalk 專案。 加入透過匯入與包含陳述式所參考的所有檔案。  
  
4. 選取叫用的 Web 服務之 WSDL 檔案。  
  
    您現在可以修改或部署新協調流程。  
  
   **匯入 BPEL4WS 的限制**  
  
-   匯入 BPEL 和 WSDL 時，請確定 WSDL 定義節點的 [名稱] 屬性和 BPEL 程序節點不相符。  
  
-   不要在您匯入的 BPEL4WS 中使用 XLANG/s 保留字。 如需完整清單，請參閱 < [XLANG/s 保留字](../core/xlang-s-reserved-words.md)。  
  
-   僅支援 XSD 預先定義的簡單類型。  
  
-   不支援 xsd: qname;它是以 System.String 匯入。 請改用 xsd: string。  
  
-   匯入 BPEL4WS 時請考慮使用標準的 XPath。  
  
     最好只匯入標準的 XPath，以達到最佳效能。 整個路徑從根節點到升級節點都必須使用 '/*[local-name()="someName" and namespace-uri()="someUri"]' 拼寫。  
  
     如果您匯入的非標準 XPath，您可以移除升級並 repromote 相同的欄位才會有結構描述編輯器建立正確的標準 XPath。  
  
     範例: (targetNamespace = http://BizTalk_Server_Project3.Schema1)  
  
    ```  
    <element name=Root type=complexType>  
                <sequence>  
                            <element name=promotedField/>  
                </sequence>  
    </element>  
    ```  
  
     `XPath - /*[local-name()='Root' and namespace-uri()='http://BizTalk_Server_Project3.Schema1']/\*[local-name()='promotedField' and namespace-uri()='']` 
  
    |標準 XPath|非標準 XPath|  
    |---------------------|--------------------------|  
    |BizTalk 編輯器會顯示特殊圖示 (![](../core/media/ebiz-orch-promotedprop.gif "ebiz_orch_promotedprop")) 來表示已升級的欄位。 使用標準 XPath 運算式升級欄位，以透過更有效的 XML 使用來改善效能|「BizTalk 編輯器」未顯示特殊圖示。 編譯器和升級對話方塊皆提出警告。 隨著訊息大小增加，對效能會產生線性且重要的影響。|  
  
## <a name="see-also"></a>另請參閱  
 [如何匯出 BPEL4WS](../core/how-to-export-bpel4ws.md)   
 [XLANG-s 至 BPEL4WS 類型轉換](../core/xlang-s-to-bpel4ws-type-conversions.md)
