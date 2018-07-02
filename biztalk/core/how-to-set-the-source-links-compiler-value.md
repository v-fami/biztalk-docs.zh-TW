---
title: 如何設定來源連結編譯器值 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4edd1d73-78d1-468d-806a-3f6f258ee375
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6ad777bc5b4df2717d20fd95aa60fdf5d59d1f6f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36975167"
---
# <a name="how-to-set-the-source-links-compiler-value"></a>如何設定來源連結編譯器值
您可以使用**來源連結**來指定從來源節點擷取及套用到目的地節點值的方式連結的屬性。 本主題說明可用的選項以及如何在其中選擇。  
  
### <a name="to-set-the-source-links-link-property"></a>設定來源連結連結屬性  
  
1. 在「BizTalk 對應工具」的格線頁中，按一下連結以選取連結。  
  
    格線頁中所選連結的端點會反白顯示。  
  
2. 在 [[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]屬性] 視窗中，設定**來源連結**屬性設為其中包含下列選項：  
  
   -   **複製名稱。** 來源結構描述中的節點名稱作為目的結構描述中連結節點的值。  
  
   -   **複製文字值。** 對應至來源結構描述中節點的值 (項目資料或屬性值) 作為目的結構描述中連結節點的值。 此選項為預設。 例如，`<Node>Hello<Name>Chris</Name>Barry</Node>` 的結果為 "Hello"。  
  
   -   **複製文字與子內容值。** 將對應至來源結構描述中記錄節點、所有子節點的值，以及其子節點的值 (項目資料或屬性值) 結合起來，當做目的結構描述中連結之節點的值。 例如，`<Node>Hello<Name>Chris</Name>Barry</Node>` 的結果為 "Hello Chris Barry"。  
  
## <a name="see-also"></a>另請參閱  
 [使用連結指定記錄和欄位對應](../core/using-links-to-specify-record-and-field-mappings.md)   
 [編譯器指示詞和連結](../core/compiler-directives-and-links.md)