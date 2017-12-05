---
title: "如何加上標籤與註解的運算質 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.mapper.functiod.general
ms.assetid: 58ff3a07-cbb6-4817-b301-d2b434ed2ad9
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5720402e548992044eda26366c8b7b50bb95746a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-label-and-comment-a-functoid"></a>如何為運算質加上標籤與註解
標籤與註解有助於記錄對應中的運算質或連結用途。 您可以使用**標籤**屬性提供運算質的名稱。 **註解**屬性可讓您提供的運算質，它正在執行之作業的相關的一般相關資訊的其他資訊。  
  
 下圖顯示的標籤和註解的運算質。 運算質從來源結構描述新增兩個輸入 (Field1 與 Field3)，並將結果輸出到目標結構描述中的 Field4。 在此範例中，運算質標籤為「新增 Field1 與 Field3」，註解為「新增是 Field4 的輸出」。  
  
 ![插入運算質標籤及註解](../core/media/label.gif "Label_")  
  
 因為運算質可能是極複雜之對應的一部分，適當地加上標籤並提供相關註解是很重要的。 您可以為運算質和連結加上標籤。 如需如何標示連結資訊，請參閱[如何標示連結](../core/how-to-label-a-link.md)。  
  
 您可以下列方式為運算質加上標籤與註解：  
  
-   使用**設定\<運算質\>運算質** 對話方塊。  
  
-   使用**屬性**視窗。  
  
## <a name="prerequisites"></a>必要條件  
 這些指示需要執行中的 BizTalk 對應工具。  
  
### <a name="to-label-and-comment-a-functoid-from-configure-dialog-box"></a>從 [設定] 對話方塊為運算質加上標籤與註解  
  
1.  以滑鼠右鍵按一下您想要標籤和註解，然後再按一下運算質**設定運算質輸入**。  
  
2.  在**設定\<運算質\>運算質**對話方塊中，按一下 [**標籤與註解**] 索引標籤。  
  
3.  輸入下列資訊，然後再按一下**確定**。  
  
    -   **標籤 –**輸入新名稱。  
  
        > [!IMPORTANT]
        >  允許的字元數目上限是 256。 如果指定超過 256 個字元的字串，則接受前 256 個字元，其餘部分會被捨棄。  
  
    -   **註解 –**運算質輸入的註解。  
  
        > [!IMPORTANT]
        >  允許的字元數目上限為 1024年。 如果指定超過 1024 個字元的字串，則先 1024年個字元會接受，而且會捨棄其餘部分。  
  
### <a name="to-label-and-comment-a-functoid-from-properties-window"></a>從 [屬性] 視窗為運算質加上標籤與註解  
  
1.  選取您要加上標籤與註解的運算質。  
  
2.  在**屬性**視窗中，輸入下列資訊，然後再按一下**確定**。  
  
    -   **標籤 –**輸入新名稱。  
  
        > [!IMPORTANT]
        >  允許的字元數目上限是 256。 如果指定超過 256 個字元的字串，則接受前 256 個字元，其餘部分會被捨棄。  
  
    -   **註解 –**運算質輸入的註解。  
  
        > [!IMPORTANT]
        >  允許的字元數目上限為 1024年。 如果指定超過 1024 個字元的字串，則先 1024年個字元會接受，而且會捨棄其餘部分。  
  
## <a name="see-also"></a>請參閱  
 [編輯運算質屬性和輸入參數](../core/editing-functoid-properties-and-input-parameters.md)