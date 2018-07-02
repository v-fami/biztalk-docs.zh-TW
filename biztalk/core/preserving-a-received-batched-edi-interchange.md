---
title: 保留收到的批次處理 EDI 交換 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10d21b9b-9684-422a-8948-8bd71a4d5a10
caps.latest.revision: 20
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4883f6c6df9042d40b82138a4d3a871797a5fa1f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36985775"
---
# <a name="preserving-a-received-batched-edi-interchange"></a>保留收到的批次處理 EDI 交換
> [!NOTE]
>  本主題中提及的所有使用者介面選項都可用於**本機主機設定**網頁 (**接收者的設定**一節) 中之雙向協議索引標籤**協議屬性** 對話方塊。  

 當 EDI 接收管線保留輸入的批次處理 EDI 交換時，就不會執行將每個交易集/訊息剖析成個別中繼 XML 檔案的一般作業。 EDI 接收管線會以單一文件的方式處理該次交換，而不會分割交易集/訊息。 發生這種情況時**輸入批次處理選項**屬性設定為**保留交換-發生錯誤時暫停交換**或**保留交換-發生時暫停交易集錯誤**。  

 **結構描述驗證**  

 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會使用批次結構描述和服務結構描述來驗證保留批次的信封。 批次結構描述可用來驗證保留訊息的根節點，而服務結構描述則用於驗證交換、群組，以及交易集標頭和結尾。 如需有關批次結構描述的詳細資訊，請參閱 < [EDI 批次結構描述](../core/edi-batch-schemas.md)。 如需有關服務結構描述的詳細資訊，請參閱 < [EDI 服務和控制結構描述](../core/edi-service-and-control-schemas.md)。  

 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會使用專案中的文件結構描述來驗證批次交換中的文件。  

 **接收端處理**  

 EDI 解譯器處理保留批次的方式如下：  

- 當 EDI 解譯器處理要保留的批次時，它會將一般檔案格式轉換成 XML，並加入 X12InterchangeXML 或 EdifactInterchangeXML 做為 XML 根節點。 這個步驟讓傳送管線知道它應該保留批次交換，也表示系統應該使用 Edifact_BatchSchema 結構描述或 X12_BatchSchema 結構描述來驗證根節點。  

- 解譯器會將 DelimiterSetSerializedData 屬性 (Attribute) 加入至批次 XML 訊息的根節點，以指定傳送管線在從 XML 訊息產生批次 EDI 交換時所要使用的分隔符號。 若 XML 訊息是保留的批次，接收管線就會從內送訊息中使用的分隔符號填入這個屬性。 在批次協調流程產生批次 XML 時，則會根據協議屬性 (Property) 中指定的值填入此屬性 (Attribute)。  

- 在建立 XML 編碼的保留交換時，解譯器會使用下列其中一個命名空間：`http://schemas.microsoft.com/BizTalk/EDI/EDIFACT/2006/InterchangeXML` or `http://schemas.microsoft.com/BizTalk/EDI/X12/2006/InterchangeXML`。  

- 解譯器會升級內容屬性 `EDI.ReuseEnvelope == True`，以識別保留的交換。 這可讓您建立傳送埠，以訂閱保留的所有批次交換。  

  > [!NOTE]
  >  HIPAA 文件才不會分割成子文件**輸入批次處理選項**設為**保留交換**。 即使 HIPAA 結構描述內的子文件建立分頁註解設定為 "Yes" 也一樣。  

  **錯誤處理**  

  如果您已選取**保留交換-發生錯誤時暫停交換**for**輸入批次處理選項**，將會暫停整個交換，因為任何錯誤。 如果 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 擱置了整個保留的交換，交換結構以及交換內交易集的順序都會保留。 發生錯誤時，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會在事件日誌中公佈一個合併的錯誤項目。 這個項目將包括交換、功能群組與交易集等層級中的所有錯誤。  

  如果您已選取**保留交換-發生錯誤時暫停交易集**輸入批次處理選項，則 EDI 接收管線會將任何無效的交易集從交換中捨棄，然後再繼續建立交換 XML。 產生的交換 XML 必須重複使用現有的控制區段信封 (適用於 X12 編碼交換的 ISA、GS、GE 和 IEA，或適用於 EDIFACT 編碼交換的 UNA、UNB、UNG、UNE 和 UNZ)。 系統會將這個交換視為已成功處理完成的文件；不過，事件檢視器中將會報告錯誤，而且如果已經產生功能通知，通知中也會報告錯誤。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 將事件記錄檔中的每個交易集發生錯誤，建立個別的項目。 如果[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]捨棄錯誤交易集從交換，交換結構和順序可能不會保留。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 將更新交換中交易集的數目。  

  下列特殊案例適用於發生錯誤時擱置交易集的情況：  

- 如果群組中所有的交易集全都無效，則會個別擱置每個交易集；不過，群組控制區段 (沒有交易集，因為已經捨棄) 將會包含在產生的交換 XML 中。  

- 如果交換中所有的交易集全都無效，則會個別擱置每個交易集；不過，交換控制區段 (沒有交易集，因為已經捨棄) 將會包含在產生的交換 XML 中。  

- 如果群組控制區段無效，將會個別擱置群組中的所有交易集。  

- 如果交換控制區段無效，將會個別擱置交換中的所有交易集，而且不會產生交換 XML。 事件檢視器中將會建立已拒絕之交換的記錄檔。
