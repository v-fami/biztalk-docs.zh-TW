---
title: 設定 EDI 管線屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.edir2.edi.pipeline.properties
ms.assetid: 1b6229b6-a8b0-4824-86bd-39021844c5a8
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e15d0c57454e8b6ba13e0d2636662f18081ee67e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37003783"
---
# <a name="configuring-edi-pipeline-properties"></a>設定 EDI 管線屬性
管線屬性用來處理內送或外寄 EDI 交換時[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]無法判斷內送或外寄交換解析成的協議。 在某些情況下，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會使用管線屬性來處理交換; 其他情況[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]使用後援協議。 如需詳細資訊，請參閱 <<c0> [ 如何驗證 EDI 交換已](../core/how-validation-of-an-edi-interchange-is-configured.md)。  
  
 有少數的例外狀況，這項規則：  
  
- 對於 X12，在執行階段設定使用的字元取決於 [管線] 屬性中，即使已經確定協議。 設定協議中所述的字元僅用於驗證協議屬性設定。  
  
- 對於 EDIFACT，如果內送交換沒有 UNA 區段中，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會使用 EfactDelimiters 管線屬性中指定的分隔符號[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]不會使用訊息會解析為協議或後援中定義的屬性協議。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  
  
## <a name="edi-pipeline-properties"></a>EDI 管線屬性  
 您可以在 EDI 管線中設定下列屬性：  
  
|屬性|使用|值|管線-階段|  
|--------------|---------|------------|-----------------------|  
|AllowTrailingDelimiters|在接收的交換上產生尾端分隔符號。|False (預設值)<br /><br /> True|EdiReceive-反組譯<br /><br /> AS2EdiReceive-反組譯<br /><br /> EdiSend-組合<br /><br /> AS2EdiSend-組合|  
|CharacterSet|指定進行外寄 EDI 交換執行階段驗證時所要使用的字元集。<br /><br /> 這個屬性只適用於 X12 處理，不適用於 EDIFACT。|UTF8 (預設值)<br /><br /> [基本]<br /><br /> 擴充|EdiReceive-反組譯<br /><br /> AS2EdiReceive-反組譯<br /><br /> EdiSend-組合<br /><br /> AS2EdiSend-組合|  
|ConvertToImpliedDecimal|針對內送交換，將以 Nn 格式指定的 EDI 數字轉換為 BizTalk Server 中繼 XML 中的 10 進制數值。<br /><br /> 這個屬性只適用於 X12 處理，不適用於 EDIFACT。|False (預設值)<br /><br /> True|EdiReceive-反組譯<br /><br /> AS2EdiReceive-反組譯|  
|CreateXMLTagForTrailingSeparators|針對每一個尾端分隔符號建立空的 XML 標記 (如果您已將**AllowTrailingDelimiters**設為 true)。|False (預設值)<br /><br /> True|EdiReceive-反組譯<br /><br /> AS2EdiReceive-反組譯|  
|DetectMID|啟用 EDI 解譯器以剖析單一訊息中的多個交換。|True (預設值)<br /><br /> False|EdiReceive-反組譯<br /><br /> AS2EdiReceive-反組譯|  
|EdiDataValidation|啟用外寄 EDI 交換的 EDI 類型 (資料元素) 驗證，這除了 EDI 資料元素驗證外，也包括欄位長度、選擇性和重複計數的驗證。|True (預設值)<br /><br /> False|EdiReceive-反組譯<br /><br /> AS2EdiReceive-反組譯<br /><br /> EdiSend-組合<br /><br /> AS2EdiSend-組合|  
|EfactDelimiters|指定處理內送訊息時所要使用的分隔符號。 在內送交換沒有 UNA 區段時使用。<br /><br /> 分隔符號包括下列各項：<br /><br /> -UNA1 （元件資料元素分隔符號）<br />-UNA2 （資料元素分隔符號）<br />-UNA3 （小數點標記）<br />-UNA4 （釋放指示符號）<br />-UNA5 （重複分隔符號）<br />-UNA6 （區段結束字元）**附註：** 這個屬性用於 EDIFACT 處理，不適用於 X12。|0x3A、 0x2B，0x2C、 0x3F，0x20，0x27 （預設值）|EdiReceive-反組譯<br /><br /> AS2EdiReceive-反組譯|  
IgnoreMessageEncoding|指定 BatchMarker 元件將不會設定 EDI。EncodingType 內容屬性\<X12\>或是\<EDIFACT\>。 這適用於處理非 EDI 訊息時的自訂管線。|False (預設值)<br /><br /> True|EdiReceive - 解析合作對象<br /><br /> AS2EdiReceive-解析合作對象|  
|MaskSecurityInformation|遮罩內送 EDI 交換之內容屬性中的授權/密碼安全性資訊，以避免資訊洩漏。 適用於 X12 交換的 ISA1、ISA2、ISA3 和 ISA4 等欄位，以及 EDIFACT 交換的 UNB6 欄位。|True (預設值)<br /><br /> False|EdiReceive-反組譯<br /><br /> AS2EdiReceive-反組譯|  
|PreserveInterchange|指定將接收的批次當做單一單位處理。|False (預設值)<br /><br /> True|EdiReceive-反組譯<br /><br /> AS2EdiReceive-反組譯|  
|RouteAckOn2WayPort|透過雙向要求-回應接收埠的開啟連線來傳回 EDI 通知。|True (預設值)<br /><br /> False|EdiReceive-反組譯<br /><br /> AS2EdiReceive-反組譯|  
|UseDotAsDecimalSeperator|設為 True 時，EDI 接收管線會使用的小數點標記"。" 而不是內送文件的小數點標記。|False (預設值)<br /><br /> True|EdiReceive-反組譯<br /><br /> AS2EdiReceive-反組譯|  
|UseIsa11AsRepetitionSeparator|指定使用 ISA11 做為重複分隔符號，而非標準識別項。 **注意：** 這個屬性用於 X12 處理，不適用於 EDIFACT。|False (預設值)<br /><br /> True|EdiReceive-反組譯<br /><br /> AS2EdiReceive-反組譯|  
|XmlSchemaValidation|啟用外寄 EDI 交換的擴充 (BTS-XSD) 驗證。 這只適用於已經使用資料型別不是 EDI 資料型別之元素自訂結構描述的情況。 這些加入的元素不會由 EDI 驗證方法予以驗證，所以都會接受擴充驗證。|False (預設值)<br /><br /> True|EdiReceive-反組譯<br /><br /> AS2EdiReceive-反組譯<br /><br /> EdiSend-組合<br /><br /> AS2EdiSend-組合|  
  
### <a name="to-set-a-pipeline-property"></a>若要設定管線屬性  
  
1. 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下接收位置或傳送埠使用您要設定屬性，然後按一下 管線**屬性**。  
  
2. 按一下要設定屬性之管線旁邊的省略符號按鈕 (?。  
  
3. 在 [**設定管線**] 對話方塊中，輸入屬性的值，，然後按一下**確定**。  
  
## <a name="see-also"></a>另請參閱  
 [如何設定驗證 EDI 交換](../core/how-validation-of-an-edi-interchange-is-configured.md)