---
title: 訂閱和擷取訊息 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4e7fbc17-44d6-4cc5-a266-b54256e7b453
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 22d5a7f6065e8040e390947d44510bb7414e8e10
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22294718"
---
# <a name="subscribing-to-and-extracting-messages"></a><span data-ttu-id="8f717-102">訂閱和擷取訊息</span><span class="sxs-lookup"><span data-stu-id="8f717-102">Subscribing to and Extracting Messages</span></span>
<span data-ttu-id="8f717-103">協調流程可以包含訂閱，並從 ESB 錯誤訊息中擷取訊息的程式碼。</span><span class="sxs-lookup"><span data-stu-id="8f717-103">Orchestration can contain code to subscribe to and extract messages from an ESB fault message.</span></span> <span data-ttu-id="8f717-104">例如，下列程式碼會使用**GetMessage**和**GetException**方法來擷取兩個強型別訊息和**System.Exception** ESB 物件錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="8f717-104">For example, the following code uses the **GetMessage** and **GetException** methods to extract two strongly typed messages and the **System.Exception** object from an ESB fault message.</span></span>  
  
```csharp  
// Retrieve two messages from the fault message.  
requestMsg = Microsoft.Practices.ESB.ExceptionHandling.ExceptionMgmt.GetMessage(  
                                    faultMsg, "ApprovedRequest");  
deniedMsg = Microsoft.Practices.ESB.ExceptionHandling.ExceptionMgmt.GetMessage(  
                                    faultMsg, "DeniedRequest");  
  
// Retrieve the System.Exception object.  
newExc = Microsoft.Practices.ESB.ExceptionHandling.ExceptionMgmt.GetException(  
                                    faultMsg);  
```  
  
 <span data-ttu-id="8f717-105">要擷取訊息，請使用下列程式碼**GetMessages**方法來擷取所有訊息，然後逐一查看它們。</span><span class="sxs-lookup"><span data-stu-id="8f717-105">To extract type-less messages, the following code uses the **GetMessages** method to extract all the messages and then iterate through them.</span></span>  
  
```csharp  
Microsoft.Practices.ESB.ExceptionHandling.MessageCollection msgs;  
msgs = Microsoft.Practices.ESB.ExceptionHandling.ExceptionMgmt.GetMessages(faultMsg);  
System.Xml.XmlDocument tmpMsg;  
while (msgs.MoveNext())  
{  
  tmpMsg = msgs.Current;  
}  
```