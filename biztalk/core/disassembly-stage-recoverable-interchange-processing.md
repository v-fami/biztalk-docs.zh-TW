---
title: 反組譯階段 （可復原交換處理） |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 552b1e90-f75d-4713-8c7b-155a52819308
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0ca8b90765b2b00803f5b8eb6a22c59ed6b43776
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36966111"
---
# <a name="disassembly-stage-recoverable-interchange-processing"></a>反組譯階段 (可復原交換處理)
在解譯階段可以使用兩種模式處理交換：  
  
-   **標準模式。** 當接收管線的解譯器元件設定為執行標準解譯時，包含在交換中的訊息會被擷取、由接收管線處理、對應並發佈為交易式工作單位。 也就是說，會完整地處理整個交換及其包含的訊息並發佈到 MessageBox 資料庫，或是將交換放置在已擱置佇列中。  
  
-   **可復原模式。** 當接收管線的解譯器元件設定為執行**可復原交換處理**，彼此擷取包含在交換訊息。 成功擷取的訊息會進一步傳播到接收管線。 在交換中已識別但未成功擷取的訊息，會放置在已擱置佇列中。  
  
## <a name="examples"></a>範例  
 下列範例說明交換處理實例。  
  
### <a name="example-1"></a>範例 1  
 在此範例中，下列虛擬交換在標準交換接收位置上提交。 也就是說，接收管線中的解譯器元件為標準交換處理所設定。  
  
```  
<Interchange>  
<Document1>...</Document1>  
<Document2 failure=”routing”>...</Document2>  
<Document3>...</Document3>  
<Document4 failure=”pipeline” recoverableError=”true”>...</Document4>  
<Document5>...</Document5>  
</Interchange>  
```  
  
 此交換包含五個訊息，解譯器可成功地從交換擷取所有這些訊息。 處理方式如下所示：  
  
- 第一個、第二個以及第三個訊息透過管線傳播並準備發佈。  
  
- 第四個訊息在管線的解譯階段處理失敗。 這造成所有已經處理的訊息回復，而且原始交換訊息被擱置為可繼續。  
  
  提交的結果為：  
  
- 沒有發佈任何訊息。 原始交換已擱置，因為在標準交換處理中，在交換處理期間或之後的任一點失敗的任何已擷取訊息，將導致所有已擷取訊息被捨棄，且原始交換以可繼續狀態放置在已擱置佇列中。  
  
### <a name="example-2"></a>範例 2  
 本範例使用與上一個範例相同的交換處理與傳播實例，除了解譯階段設定為執行可復原交換處理之外。  
  
 提交的結果是個別擷取的訊息已全部處理，並捨棄原始交換。 個別訊息的處理方式如下所示：  
  
-   第一個、第二個以及第三個訊息透過管線傳播並準備發佈。  
  
-   第四個訊息解譯處理失敗 (也就是說，在擷取此訊息之後發生錯誤)，並已準備將它擱置。  
  
-   第五個訊息透過管線傳播並準備發佈。  
  
-   從交換擷取所有訊息之後，就會將訊息 1、2、3 及 5 發佈到 MessageBox 資料庫，並將訊息 4 放置在已擱置佇列中。 訊息 2 由於沒有符合的訂閱者而造成路由失敗，也會重新導向至已擱置佇列。  
  
## <a name="configuring-recoverable-interchange-processing"></a>設定可復原交換處理  
 可復原交換處理是接收管線解譯器元件的屬性。 並非所有解譯器元件都可讓您指定可復原交換處理，例如，原生 BizTalk Framework 解譯器就不允許。 若解譯器支援可復原交換處理，則當您將解譯器元件新增至所設計管線的解譯階段時，就可以在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 的管線設計師中指定此行為。 您將選取的解譯器拖曳至管線的解譯階段之後，您會設定可復原交換處理屬性到該解譯器元件的`true`。  
  
### <a name="party-resolution"></a>合作對象解析  
 在可復原交換處理中成功擷取的訊息，則根據為父交換已到達之接收埠所設定的合作對象，來識別傳送合作對象。 若有任何從指定交換擷取的訊息之合作對象解析失敗，則整個交換的合作對象解析會被視為已失敗。  
  
### <a name="restrictions"></a>限制  
  
-   當交換在解譯器中失敗時，交換會被擱置為可繼續。 不過，若系統管理繼續此交換，它會再次失敗，因為造成解譯失敗的這些類型錯誤只是交換內容的結果，當交換繼續時，仍會維持相同結果。 必須修改這類失敗的交換並透過接收位置重新提交。  
  
-   若訊息已從交換成功擷取，之後在透過傳訊傳播時由於不相符的訂閱者而失敗，則會將訊息擱置為可繼續。 若已修正路由失敗的原因，則此訊息可由系統管理繼續。  
  
-   儘管在解譯器元件中發生下列錯誤，解譯器元件仍會繼續從交換擷取訊息：  
  
    -   找不到結構描述  
  
    -   結構描述模擬兩可未解析 (也就是說，相同訊息類型有一個以上的結構描述)  
  
    -   XML 驗證失敗  
  
    -   一般檔案剖析失敗  
  
-   解譯器元件**不**繼續從交換擷取訊息，如果解譯器元件中發生下列錯誤：  
  
    -   文件資料不是格式正確的 XML—任何會造成 System.Xml.XmlReader 失敗的文件屬性  
  
## <a name="see-also"></a>另請參閱  
 [如何設定 XML 解譯器管線元件](../core/how-to-configure-the-xml-disassembler-pipeline-component.md)   
 [如何設定一般檔案解譯器管線元件](../core/how-to-configure-the-flat-file-disassembler-pipeline-component.md)