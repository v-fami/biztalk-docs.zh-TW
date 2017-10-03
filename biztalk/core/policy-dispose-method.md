---
title: "Policy.Dispose 方法 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: db37c6b9-acf0-42ee-9356-4d1567934862
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ba4713616edf55c149a215a6f7842cd5d0353dfe
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="policydispose-method"></a>Policy.Dispose 方法
**Policy.Dispose**方法所使用的資源釋出**原則**類別，以及傳回**原則**快取的物件。 當相同的原則會再次叫用、 快取**原則**使用物件，以節省建立新的所需的時間**原則**物件。  
  
 如果您沒有明確呼叫**Policy.Dispose**方法，則原則不會傳回至快取之前的.NET 執行階段記憶體回收集合程序期間釋放物件。 因此，您應該呼叫**Policy.Dispose**您已完成**原則**物件。  
  
 使用的範例程式碼**Policy.Dispose**方法如下所示：  
  
```  
xmlDocument = IncomingXMLMessage.XMLCase;  
typedXmlDocument = new Microsoft.RuleEngine.TypedXmlDocument("Microsoft.Samples.BizTalk.LoansProcessor.Case",xmlDocument);  
policy = new Microsoft.RuleEngine.Policy("LoanProcessing");  
policy.Execute(typedXmlDocument);  
OutgoingXMLMessage.XMLCase = xmlDocument;  
policy.Dispose();  
```