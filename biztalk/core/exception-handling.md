---
title: 例外狀況處理 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 00a9125c-7c7c-4d2a-ae04-c923cd89683c
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 520f4eb47fb98bf497753a8348031f7c2ab93d29
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22245926"
---
# <a name="exception-handling"></a>例外狀況處理
**RuleEngine**類別具有屬性**CompensationHandlerInfo**，其中又包含兩個屬性： **CompensationHandler**和**UserData**. **CompensationHandler**屬性屬於型別**RuleEngineCompensationHandler**，而**UserData**屬性屬於型別**物件**. 定義**RuleEngineCompensationHandler**如下所示：  
  
```  
public delegate bool RuleEngineCompensationHandler(  
   Exception ex,  
   object userData  
);  
```  
  
 規則引擎取用者指定處理常式，規則引擎之使用者資料使用**CompensationHandlerInfo**屬性**RuleEngine**類別。 處理常式必須具有相同的簽章**RuleEngineCompensationHandler**委派。 如果發生執行階段例外狀況，引擎便會呼叫處理常式，並傳遞例外狀況及預先定義的使用者資料做為處理常式的參數。 如果處理常式傳回 `true`，則規則引擎會繼續進行處理。 否則，規則引擎會中止處理，並將原本的例外狀況傳回至使用者。 如您所見，只有當您使用叫用原則，您可以使用這個例外狀況處理機制**RuleEngine.Execute**方法。  
  
 如果您使用**Policy.Execute**方法來執行原則，您必須使用 try catch 區塊來攔截規則引擎執行原則時產生任何例外狀況。  
  
 如果您使用**呼叫規則**圖形以執行原則，請使用**Catch 例外狀況**封鎖**範圍**攔截規則引擎執行時引發的例外狀況的圖形原則。  
  
## <a name="see-also"></a>另請參閱  
 [如何新增 Catch 例外狀況區塊](../core/how-to-add-a-catch-exception-block3.md)