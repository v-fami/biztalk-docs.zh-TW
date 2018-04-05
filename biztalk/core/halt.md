---
title: 暫止 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Halt function [Business Rules Engine]
ms.assetid: 468ba6dd-2bb2-4787-a824-1f5455508efd
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 07ca8091d4ff4405704314d72939758c7600a71a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="halt"></a>終止
您可以使用**暫止**暫止目前的規則引擎執行的函式。 **暫止**函數會採用一個參數的型別`Boolean`。 如果您將此參數的值指定為 `true`，規則引擎也會清除包含擱置候選規則的議程。  
  
 **Policy.Execute**方法基本上是周圍的包裝函式**RuleEngine.Execute**方法。 該方法的程式碼與下列程式碼類似：  
  
```  
RuleEngine.Assert(facts);   
RuleEngine.Execute();   
RuleEngine.Retract(facts);  
```  
  
 如果您使用**Policy.Execute**方法來執行原則，規則引擎會將控制傳回**Policy.Execute**方法時**暫止**函式執行。 **Policy.Execute**方法會撤回事實並將控制權傳回給呼叫者。 因此，終止的原則執行不能在此情況下繼續。 當您使用時，會發生相同的作業**呼叫規則**圖形來叫用原則。  
  
 不過，如果您使用**RuleEngine.Execute**方法來執行此原則，您可以繼續終止的原則執行一個擱置規則引發，只需呼叫直接**RuleEngine.Execute**一次 （前提是您沒有撤回在兩個呼叫之間所需的任何物件）。 以下是繼續執行已終止原則的範例程式碼：  
  
```  
//assert facts into working memory of the rule engine instance  
RuleEngine.Assert(facts);   
//execute the policy  
RuleEngine.Execute();   
//policy invokes the Halt method when executing actions.   
//control is returned to here when the Halt method is invoked  
  
//when engine is halted do the following  
//Add your code here  
  
//To resume the halted rule engine execution  
RuleEngine.Execute();  
//retract or remove facts frm the working memory of the rule engine  
RuleEngine.Retract(facts);  
```  
  
 請注意， **Policy.Execute**方法會快取規則引擎執行個體，以提升效能。 當您使用**RuleEngine.Execute**直接的方法時，規則引擎執行個體不會快取。  
  
## <a name="see-also"></a>另請參閱  
 [引擎控制函式](../core/engine-control-functions.md)