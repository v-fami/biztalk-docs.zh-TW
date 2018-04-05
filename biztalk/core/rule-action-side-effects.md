---
title: 規則動作的副作用 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Business Rules Engine, side effects
ms.assetid: 1ef65014-9c0a-40d3-b941-2a67c20b54d3
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d2ed890ca8efca6fdd1403c4ec89f4c0c5d32eaa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="rule-action-side-effects"></a>規則動作的副作用
若執行動作會影響到物件的狀態或條件中使用的詞彙，那麼該動作即視為對物件有副作用。  
  
 假設我們有下列規則。  
  
## <a name="rule-1"></a>規則 1  
  
```  
IF OrderForm.ItemCount > 100   
THEN OrderForm.Status = "important"  
```  
  
## <a name="rule-2"></a>規則 2  
  
```  
IF OrderList.IsFromMember = true   
THEN OrderForm.UpdateStatus("important")  
```  
  
 在此情況下， **OrderForm.UpdateStatus**即所謂具有副作用**OrderForm.Status**。 這並不表示**OrderForm.UpdateStatus**有副作用; 相反地， **OrderForm.Status**可能會受到一或多個動作。  
  
 根據預設， **SideEffects** .NET 類別成員的屬性是**true**，它可防止規則引擎快取具有副作用的成員。 在本例中，規則引擎並不會快取**OrderForm.Status**工作記憶體中改為取得最新值的**OrderForm.Status**每次評估規則 1。 如果**SideEffects**屬性設定為**false**，規則引擎快取的值評估的第一次**OrderForm.Status**，但 （在稍後的評估正向鏈結實例），它會使用快取的值。  
  
 目前商務規則編輯器 」 不提供方法，讓使用者修改**SideEffects**，不過，您只能設定**SideEffects**屬性以程式設計方式透過 「 商務規則架構. 您設定可以在繫結，請使用[ClassMemberBinding](https://msdn.microsoft.com/library/microsoft.ruleengine.classmemberbinding.aspx)類別，以指定物件的方法、 屬性和規則條件和動作中使用的欄位。 **ClassMemberBinding**具有內容， [SideEffects](https://msdn.microsoft.com/library/microsoft.ruleengine.classmemberbinding.sideeffects.aspx#P:Microsoft.RuleEngine.ClassMemberBinding.SideEffects)，其中包含布林值，指出是否存取成員變更其值。  
  
## <a name="see-also"></a>另請參閱  
 [規則引擎](../core/rule-engine.md)