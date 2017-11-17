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
# <a name="policydispose-method"></a><span data-ttu-id="0cdc7-102">Policy.Dispose 方法</span><span class="sxs-lookup"><span data-stu-id="0cdc7-102">Policy.Dispose Method</span></span>
<span data-ttu-id="0cdc7-103">**Policy.Dispose**方法所使用的資源釋出**原則**類別，以及傳回**原則**快取的物件。</span><span class="sxs-lookup"><span data-stu-id="0cdc7-103">The **Policy.Dispose** method releases resources used by the **Policy** class, and also returns the **Policy** object to the cache.</span></span> <span data-ttu-id="0cdc7-104">當相同的原則會再次叫用、 快取**原則**使用物件，以節省建立新的所需的時間**原則**物件。</span><span class="sxs-lookup"><span data-stu-id="0cdc7-104">When the same policy is invoked again, the cached **Policy** object is used, which saves the time needed for creating a new **Policy** object.</span></span>  
  
 <span data-ttu-id="0cdc7-105">如果您沒有明確呼叫**Policy.Dispose**方法，則原則不會傳回至快取之前的.NET 執行階段記憶體回收集合程序期間釋放物件。</span><span class="sxs-lookup"><span data-stu-id="0cdc7-105">If you do not explicitly call the **Policy.Dispose** method, then the policy is not returned to the cache until the .NET runtime frees up the object during the garbage collection process.</span></span> <span data-ttu-id="0cdc7-106">因此，您應該呼叫**Policy.Dispose**您已完成**原則**物件。</span><span class="sxs-lookup"><span data-stu-id="0cdc7-106">Therefore, you should call **Policy.Dispose** when you are finished with the **Policy** object.</span></span>  
  
 <span data-ttu-id="0cdc7-107">使用的範例程式碼**Policy.Dispose**方法如下所示：</span><span class="sxs-lookup"><span data-stu-id="0cdc7-107">The sample code for using the **Policy.Dispose** method is as follows:</span></span>  
  
```  
xmlDocument = IncomingXMLMessage.XMLCase;  
typedXmlDocument = new Microsoft.RuleEngine.TypedXmlDocument("Microsoft.Samples.BizTalk.LoansProcessor.Case",xmlDocument);  
policy = new Microsoft.RuleEngine.Policy("LoanProcessing");  
policy.Execute(typedXmlDocument);  
OutgoingXMLMessage.XMLCase = xmlDocument;  
policy.Dispose();  
```