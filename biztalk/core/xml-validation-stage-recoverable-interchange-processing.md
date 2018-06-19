---
title: XML 驗證階段 （可復原交換處理） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1ed00971-d85b-4adb-86c4-c56de7ba7c67
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: de8f0225e100053fe6dced8165b7fc800c5e4804
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22289950"
---
# <a name="xml-validation-stage-recoverable-interchange-processing"></a>XML 驗證階段 (可復原交換處理)
**XML 驗證器**管線元件會處理交換，在兩種模式：  
  
-   **標準模式**。 當**XML 驗證器**元件設定為執行標準驗證、 交易式工作單位來驗證交換中包含的訊息。 特別是如果驗證交換中的訊息失敗，就會將整個交換 (包含所有訊息) 放入擱置佇列。  
  
-   **可復原模式**。 當**XML 驗證器**元件設定執行可復原交換處理時，如果訊息的驗證失敗，訊息放入擱置佇列和**XML 驗證器**元件會繼續驗證交換中的其餘訊息。  
  
### <a name="to-configure-recoverable-interchange-processing"></a>設定可復原交換處理  
  
1.  在 Visual Studio 中使用管線設計師來開啟接收管線。  
  
2.  拖曳**XML 驗證器**元件從**工具箱**至**驗證**接收管線階段。  
  
3.  在 [屬性] 視窗中設定的值**可復原交換處理**屬性**True**如果您想**XML 驗證器**元件至處理程序交換在可復原模式中，或將屬性設定為**False**如果您想要處理交換在標準模式的元件。 這個屬性的預設值是`False`。  
  
 **XMLValidator**類別中物件模型中，對應至**XML 驗證器**管線元件，有一個名為的公用屬性**RecoverableInterchangeProcessing**可用來以程式設計方式取得或設定模式。 請參閱文件[Microsoft.BizTalk.Component.XmlValidator](http://msdn.microsoft.com/library/microsoft.biztalk.component.xmlvalidator.aspx)類別，如需詳細資訊。  
  
 已順利驗證的訊息會根據父交換抵達的接收連接埠所設定的合作對象，來識別其傳送合作對象。 對於任何從交換擷取的訊息，若合作對象解析失敗，則整個交換的合作對象解析就會被視為已失敗。  
  
## <a name="see-also"></a>另請參閱  
 [如何設定 XML 驗證器管線元件](../core/how-to-configure-the-xml-validator-pipeline-component.md)