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
# <a name="appending-nodes-to-messages-in-user-code"></a>將節點附加至使用者程式碼中的訊息
因為 BizTalk Server 處理訊息的方式不同，您不能只在現有訊息中直接附加新節點。 相反地，您必須複製現有訊息，如下所示：  
  
```  
myXMLDoc = myExistingMsg; // just holding a reference  
// use CloneNode to make a fresh copy of myModifiedMsg  
myXMLDoc = (XMLDocument)myXMLDoc.CloneNode;  
myXMLDoc.append myNode; // here is the node we want to append  
//update temp message   
myModifiedMsg = myXMLDoc;  
```  
  
 現在您可以使用包含新節點的 myModifiedMsg。 基於某些原因，若要重複使用 myExistingMsg，您可以建構新的 (空白) 複本，並將 myModifiedMsg 指定至該複本。  
  
```  
myExistingMsg = myModifiedMsg;  
```  
  
## <a name="see-also"></a>另請參閱  
 [使用者程式碼中建構的訊息](../core/constructing-messages-in-user-code.md)   
 [建構訊息](../core/constructing-messages.md)