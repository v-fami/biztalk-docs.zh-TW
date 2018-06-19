---
title: 如何比對對應中的結構描述節點 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 584f85d2-6198-4ef3-90d9-a322f1457d9a
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c1e2ce880489ca49b0b55d2e6f45b9e887d719a8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22253934"
---
# <a name="how-to-match-schema-nodes-in-a-map"></a>如何比對對應中的結構描述節點
當來源或目的地結構描述均很複雜時，對應項目會是很困難的工作。 BizTalk 對應工具引進**指示符合**功能，可讓您透過建議最佳對應對應複雜的結構描述項目。 本主題提供如何執行此作業的相關資訊。  
  
> [!NOTE]
>  BizTalk 對應工具會為結構描述節點建議可能的對應。 此功能目前只支援英文名稱。  
  
## <a name="prerequisites"></a>必要條件  
 這些指示需要執行中的 BizTalk 對應工具。  
  
### <a name="to-match-relevant-schema-nodes"></a>對應相關的結構描述節點  
  
1.  選取並以滑鼠右鍵按一下您要知道最符合項目，然後按一下 結構描述項目**表示符合**。 BizTalk 對應工具會反白顯示最符合項目 （限制為七個），以選取最適合的對應。  
  
     或者，您可以選取**指出相符項目**從 [BizTalk] 功能表中或按下 SHIFT + 空格鍵。  
  
     下圖顯示選取之節點的暗示性符合目的結構描述中。  
  
     ![暗示性對應](../core/media/suggestive-mapping.gif "Suggestive_Mapping")  
  
    > [!NOTE]
    >  按住 SHIFT 鍵可來回瀏覽建議的對應。  
  
2.  您可以進行下列動作：  
  
    -   按下 ENTER 以確認反白顯示最佳 （可能的話） 比對。  
  
    -   使用向上 / 向下鍵，循環的喜好順序反白顯示相符項目。  
  
        > [!NOTE]
        >  按向下鍵來周遊至下一個最符合項目，並向上鍵反白顯示的前一個最符合項目。  
  
    -   按 HOME 鍵以返回最上方的對應。  
  
## <a name="see-also"></a>另請參閱  
 [使用 BizTalk 對應工具中的增強的功能](../core/using-enhanced-features-in-biztalk-mapper.md)