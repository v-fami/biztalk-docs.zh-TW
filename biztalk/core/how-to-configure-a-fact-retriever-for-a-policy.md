---
title: 如何設定原則的事實擷取器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Business Rule Composer, policies
- Business Rule Composer, facts
- policies, facts
ms.assetid: a7bcf3e5-3f28-4f0e-b112-8c97dee072a1
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 18572af1323de817b3c934866af917d2601332f3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22247094"
---
# <a name="how-to-configure-a-fact-retriever-for-a-policy"></a>如何設定原則的事實擷取器
您可以儲存不會經常變更的事實，這樣就可以在主控件應用程式的第一次執行循環之前從儲存區中擷取事實，接著將這些呈現至規則引擎以供快取，如此便可以在多個執行循環中重複使用。  
  
 有兩種方法可以建立事實擷取器與原則的關聯。 您可以使用 「 商務規則編輯器 」 或以程式設計方式使用**RuleSetExecutionConfiguration**物件。  
  
> [!NOTE]
>  只有一個事實擷取器的實作能夠與原則版本建立關聯。  
  
### <a name="to-associate-a-fact-retriever-with-a-policy-in-the-business-rule-composer"></a>在「商務規則編輯器」中建立事實擷取器與原則的關聯  
  
1.  在 [原則總管] 視窗中按一下您想與事實擷取器建立關聯的原則版本。  
  
2.  在 [屬性] 視窗中，按一下**省略**按鈕 （...） 在**FactRetriever**瀏覽事實擷取器物件的全域組件快取中的屬性。  
  
    > [!IMPORTANT]
    >  **省略**按鈕 （...） 不會出現在您按一下之前**FactRetriever**屬性視窗中的資料列。  
  
## <a name="see-also"></a>另請參閱  
 [如何建立事實擷取器](../core/how-to-create-a-fact-retriever.md)