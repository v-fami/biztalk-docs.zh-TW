---
title: "如何執行原則 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Business Rules Framework, policies
- Business Rules Framework, code samples
- Business Rules Framework, programming
ms.assetid: 90d28d9d-0204-47de-a927-26e284c886e4
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8b0aa834150f0d5c84ebb4c757769a2be38f3942
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-execute-policies"></a>如何執行原則
下列範例程式碼示範如何叫用規則引擎來執行原則以程式設計方式使用**原則**類別**Microsoft.RuleEngine**組件。  
  
```  
xmlDocument = IncomingXMLMessage.XMLCase;  
typedXmlDocument = new Microsoft.RuleEngine.TypedXmlDocument("Microsoft.Samples.BizTalk.LoansProcessor.Case",xmlDocument);  
policy = new Microsoft.RuleEngine.Policy("LoanProcessing");  
policy.Execute(typedXmlDocument);  
OutgoingXMLMessage.XMLCase = xmlDocument;  
policy.Dispose();  
```  
  
## <a name="important-methods-of-the-policy-class"></a>Policy 類別的重要方法  
 以下是 Policy 類別的重要方法以及其描述。  
  
|Policy 類別中的方法|Description|  
|--------------------------------|-----------------|  
|Execute|將指定的短期事實新增至規則引擎的工作記憶體中，然後使用 Match-Conflict Resolution-Action 演算法來執行此原則。 如需 Match-conflict Resolution-action 演算法的詳細資訊，請參閱[條件評估與動作執行](../core/condition-evaluation-and-action-execution.md)。|  
|處置|釋放規則引擎用來執行原則所使用的資源。|  
|Clear|清除或重設工作記憶體，以及為了執行原則所建立之規則引擎執行個體的議程。|  
  
## <a name="see-also"></a>另請參閱  
 [Policy.Dispose 方法](../core/policy-dispose-method.md)