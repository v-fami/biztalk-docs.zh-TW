---
title: "如何複製 XPath |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 404599d4-0fb3-4c7c-91e6-1295d9d0965e
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bb282c5c32d8da62a9da6d7a9c900c798e44eee7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-copy-xpath"></a>如何複製 XPath
XML 結構描述定義 (XSD) 語言提供在 BizTalk Server 中定義之訊息結構描述的基礎語法。 雖然 BizTalk 對應工具中的樹狀檢視會使用記錄和欄位節點 (在其他類型節點之間) 之 BizTalk 特定的圖形階層，但其各自的屬性集 (如階層) 均是以 XSD 建構與保存。  
  
 在分佈於多個格線頁的複雜對應案例中，尋找結構描述節點的父節點並不容易。 在此情況下可以使用 XSD 路徑。 您可以使用 XSD 路徑來取得結構描述節點深度的相關資訊。 此外，您也可以在其他格線頁重複使用此路徑以識別關係。  
  
## <a name="prerequisites"></a>必要條件  
 這些指示需要執行中的 BizTalk 對應工具。  
  
### <a name="to-copy-the-xsd-path-xpath"></a>複製 XSD 路徑 (XPath)  
  
1.  以滑鼠右鍵按一下結構描述 節點，您想要的 XSD 路徑，然後按一下**複製 XPath**。  
  
2.  開啟文字編輯器。 在 [編輯] 功能表上，按一下 [貼上]。 您現在可以看到 XSD 路徑。  
  
    > [!NOTE]
    >  或者，您可以按下 CTRL+V 以在文字編輯器中貼上路徑。  
  
     下面的程式碼顯示所選取結構描述節點的 XSD 路徑。  
  
    ```  
    /*[local-name()='<Schema>']/*[local-name()='Shipment']/*[local-name()='DataCollection']  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [使用 BizTalk 對應工具中的增強的功能](../core/using-enhanced-features-in-biztalk-mapper.md)   
 [如何取代結構描述](../core/how-to-replace-schemas.md)   
 [如何展開和摺疊結構描述樹狀結構](https://msdn.microsoft.com/library/ee253802(v=bts.10).aspx)