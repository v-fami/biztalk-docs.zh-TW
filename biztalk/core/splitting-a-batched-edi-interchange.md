---
title: "分割批次的 EDI 交換 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 29c79b06-cc88-4cc8-aa99-40f24a1bdcde
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 441eafe79de57963dc1df5ac19334542f41a23d1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="splitting-a-batched-edi-interchange"></a>分割批次 EDI 交換
> [!NOTE]
>  本主題中提及的所有使用者介面選項都可用於**本機主機設定**頁面 (**接收者的設定**區段) 中的單向協議索引標籤**協議屬性** 對話方塊。  
  
 EDI 接收管線會分割內送的 EDI 交換批次如果您已將**輸入批次處理選項**協議屬性設**將交換分割為交易集**。  
  
 當 EDI 接收管線分割內送批次 EDI 交換時，會為每個 EDI 交易集/訊息建立一個 XML 檔。 管線會將整個交易和群組標頭升級至每個從交換分割出的交易集內容中。 此外還會升級特定交換和群組標頭，例如 ISA6、GS1 和 GS2，如此就能使用這些欄位進行路由。 您可以藉由選取遮罩標頭中的安全性資訊**遮罩安全性/授權/密碼資訊**屬性。  
  
 當 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 嘗試將交換分割成交易集時，特定 ISA (ISA1 到 ISA13) 或 UNB 標頭欄位中的任何錯誤都將導致交換遭拒。 如果協議或後援協議屬性中啟用了檢查重複的交換控制編號，則交換控制編號重複時也會發生同樣的情況。 其他交換標頭欄位 (X12 交換的 ISA1 到 ISA13 以外) 或群組標頭欄位中的錯誤，可能不會造成交換程序失敗。  
  
 如果**將交換分割為交易集-發生錯誤時暫停交易集**協議屬性中選取[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會暫停交易集發生錯誤。 如果**將交換分割為交易集-發生錯誤時暫停交換**選取時，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會擱置交換。  
  
 每個 XML 批次元素都會路由至 MessageBox，並且由訂閱批次元素的傳送埠或協調流程處理。 交換中的交易集在處理為分割訊息之後，可能不會保留其排序。 在接收端，訊息將依在交換中出現的順序處理，並且依同樣的順序放入 MessageBox，但是您必須使用群組或循序傳遞傳送埠在傳送端維持該排序。  
  
 如果分割自批次的元素將納入外寄批次中，則 BatchMarker 管線元件會升級所需的屬性。 如需詳細資訊，請參閱[批次處理外寄 EDI 訊息](../core/batching-outgoing-edi-messages.md)。  
  
## <a name="see-also"></a>另請參閱  
 [處理內送的批次](../core/processing-incoming-batches.md)   
 [批次處理外寄 EDI 訊息](../core/batching-outgoing-edi-messages.md)