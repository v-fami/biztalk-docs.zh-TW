---
title: "如何設定來源連結編譯器值 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4edd1d73-78d1-468d-806a-3f6f258ee375
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 61a7adf74d0b186f338220a383da6b6831013312
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-set-the-source-links-compiler-value"></a>如何設定來源連結編譯器值
您可以使用**來源連結**屬性指定值，如何從來源節點擷取並套用至目的地節點的連結。 本主題說明可用的選項以及如何在其中選擇。  
  
### <a name="to-set-the-source-links-link-property"></a>設定來源連結連結屬性  
  
1.  在「BizTalk 對應工具」的格線頁中，按一下連結以選取連結。  
  
     格線頁中所選連結的端點會反白顯示。  
  
2.  在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]屬性 視窗中，設定**來源連結**屬性設為其中包含下列選項：  
  
    -   **複製名稱。** 來源結構描述中的節點名稱作為目的結構描述中連結節點的值。  
  
    -   **複製文字值。** 對應至來源結構描述中節點的值 (項目資料或屬性值) 作為目的結構描述中連結節點的值。 此選項為預設。 例如，`<Node>Hello<Name>Chris</Name>Barry</Node>` 的結果為 "Hello"。  
  
    -   **複製文字與子內容值。** 將對應至來源結構描述中記錄節點、所有子節點的值，以及其子節點的值 (項目資料或屬性值) 結合起來，當做目的結構描述中連結之節點的值。 例如，`<Node>Hello<Name>Chris</Name>Barry</Node>` 的結果為 "Hello Chris Barry"。  
  
## <a name="see-also"></a>另請參閱  
 [使用連結指定記錄和欄位對應](../core/using-links-to-specify-record-and-field-mappings.md)   
 [編譯器指示詞和連結](../core/compiler-directives-and-links.md)