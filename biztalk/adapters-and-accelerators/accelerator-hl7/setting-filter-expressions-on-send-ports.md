---
title: 設定傳送埠篩選條件運算式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- send ports, context properties
- filtering, send ports
- send ports, filtering
- context properties, send ports
- context properties, filtering
- filtering, context properties
ms.assetid: 48c7c83b-9464-4ed9-bd8d-cf5b75e16702
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b94497f4e1412f81c36df3195994aafa32ecc451
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22206078"
---
# <a name="setting-filter-expressions-on-send-ports"></a>設定傳送埠的篩選條件運算式
您設定篩選條件運算式中的內容屬性來控制連接埠所傳送的內容傳送埠上。 您可以設定篩選條件運算式，以提供您在篩選屬性的方式彈性的運算子的數字 (相等或不等，存在，大於、 大於或等於、 小於且小於或等於)。  
  
### <a name="to-set-the-filter-expression-on-a-send-port"></a>若要設定傳送埠上的篩選條件運算式  
  
1.  在 BizTalk Server 管理主控台中，展開**BizTalk Server 管理**， **BizTalk 群組**，**應用程式**，和**BizTalk 應用程式1** （或另一個應用程式）。 按一下**傳送埠**。  
  
2.  以滑鼠右鍵按一下您想要設定的篩選運算式，然後按一下 傳送埠**屬性**。  
  
3.  在 傳送埠屬性 對話方塊的主控台樹狀目錄中，按一下 **篩選**。  
  
4.  按一下文字方塊中的**屬性**資料行，然後選取 [內容] 屬性從**屬性**下拉式清單。  
  
5.  按一下**運算子**方塊中的資料列的屬性，並從下拉式清單中選取屬性的運算子。  
  
6.  按一下**值**方塊中的資料列的屬性和輸入的值運算式。  
  
7.  如果您要加入另一個子句的篩選條件運算式，請按一下**Group By**方塊中的資料列的屬性，然後選取**和**或**或**判斷的關聯性子句。  
  
8.  重複步驟 4 到 6 來新增另一個篩選子句。  
  
9. 確認篩選條件運算式是正確的底部窗格**篩選**窗格。  
  
10. 當您加入所有篩選子句時，按一下**確定**。  
  
## <a name="see-also"></a>另請參閱  
 [處理 HL7 訊息](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md)   
 [使用內容屬性](../../adapters-and-accelerators/accelerator-hl7/using-context-properties.md)