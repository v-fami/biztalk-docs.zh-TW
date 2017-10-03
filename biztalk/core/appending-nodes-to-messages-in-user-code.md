---
title: "將節點附加至使用者程式碼中的訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, nodes
- messages, cloning
ms.assetid: 636e0064-095e-49d1-850f-eaee0f0ffe77
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b0376094f31478c74a408eacab6c363ce22c9d2a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="appending-nodes-to-messages-in-user-code"></a><span data-ttu-id="596cc-102">將節點附加至使用者程式碼中的訊息</span><span class="sxs-lookup"><span data-stu-id="596cc-102">Appending Nodes to Messages in User Code</span></span>
<span data-ttu-id="596cc-103">因為 BizTalk Server 處理訊息的方式不同，您不能只在現有訊息中直接附加新節點。</span><span class="sxs-lookup"><span data-stu-id="596cc-103">Because of the way BizTalk Server handles messages, you cannot simply append a new node directly to an existing message.</span></span> <span data-ttu-id="596cc-104">相反地，您必須複製現有訊息，如下所示：</span><span class="sxs-lookup"><span data-stu-id="596cc-104">Instead, you must clone the existing message, as follows:</span></span>  
  
```  
myXMLDoc = myExistingMsg; // just holding a reference  
// use CloneNode to make a fresh copy of myModifiedMsg  
myXMLDoc = (XMLDocument)myXMLDoc.CloneNode;  
myXMLDoc.append myNode; // here is the node we want to append  
//update temp message   
myModifiedMsg = myXMLDoc;  
```  
  
 <span data-ttu-id="596cc-105">現在您可以使用包含新節點的 myModifiedMsg。</span><span class="sxs-lookup"><span data-stu-id="596cc-105">Now you can use myModifiedMsg, which includes the new node.</span></span> <span data-ttu-id="596cc-106">基於某些原因，若要重複使用 myExistingMsg，您可以建構新的 (空白) 複本，並將 myModifiedMsg 指定至該複本。</span><span class="sxs-lookup"><span data-stu-id="596cc-106">If for some reason you want to reuse myExistingMsg, you can construct a new (empty) copy and assign myModifiedMsg to it.</span></span>  
  
```  
myExistingMsg = myModifiedMsg;  
```  
  
## <a name="see-also"></a><span data-ttu-id="596cc-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="596cc-107">See Also</span></span>  
 <span data-ttu-id="596cc-108">[使用者程式碼中建構的訊息](../core/constructing-messages-in-user-code.md) </span><span class="sxs-lookup"><span data-stu-id="596cc-108">[Constructing Messages in User Code](../core/constructing-messages-in-user-code.md) </span></span>  
 [<span data-ttu-id="596cc-109">建構訊息</span><span class="sxs-lookup"><span data-stu-id="596cc-109">Constructing Messages</span></span>](../core/constructing-messages.md)