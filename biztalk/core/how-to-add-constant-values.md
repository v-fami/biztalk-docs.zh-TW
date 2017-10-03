---
title: "如何新增常數值 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f46bf66e-caf2-4352-930f-c3c43a5717c3
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 398e2f4d176fdfab866cc8c87ce19aaf523a1b03
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-constant-values"></a>如何新增常數值
在測試對應時，您有時候需要設定用於測試期間的常數值。  
  
## <a name="set-constant-values-for-nodes-in-the-source-or-destination-schema-trees"></a>設定在來源或目的結構描述樹狀結構節點的常數值  
  
1.  在來源或目的結構描述樹狀結構中選取記錄或欄位。  
  
2.  在 [屬性] 視窗中**一般**類別中，使用**值**輸入選取的記錄或欄位值的屬性。  
  
    > [!NOTE]
    >  您可以只關聯值的記錄其**內容**屬性設定為**純文字**或**混合**。  
  
 來源結構描述，如果您將設定中的節點**值**屬性**\<空白 >**，產生的執行個體訊息的來源結構描述包含在對應的節點為空值。  
  
 有時，您不會使用目標結構描述中的所有欄位，也就是說，目標結構描述中有些欄位會沒有任何連入連結。 在這種情況下，「 測試對應 」 作業會擲回錯誤，但前提是**驗證 TestMap 輸入**或**驗證 TestMap 輸出**屬性會設為**True**。 若要避免在此情況下測試對應 」 錯誤，請設定**值**節點為常數值的屬性或**\<空白 >**。 使用**\<空白 >**如果您不想設定未使用的目標結構描述欄位的任意資料。  
  
## <a name="see-also"></a>另請參閱  
[驗證和測試您的對應](../core/how-to-configure-map-validation-and-test-parameters.md)