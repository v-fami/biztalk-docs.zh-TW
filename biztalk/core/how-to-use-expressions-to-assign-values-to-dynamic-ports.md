---
title: 如何使用運算式來將值指派給動態連接埠 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- dynamic send ports, variables
- send ports, dynamic
ms.assetid: 6bdb937c-8702-43ff-914a-a02adc88658b
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 59c2d11b5da44e94beee914704f46ac6b0346e85
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22256582"
---
# <a name="use-expressions-to-assign-values-to-dynamic-ports"></a><span data-ttu-id="0cffa-102">使用運算式來將值指派給動態連接埠</span><span class="sxs-lookup"><span data-stu-id="0cffa-102">Use Expressions to Assign Values to Dynamic Ports</span></span>

## <a name="assign-values"></a><span data-ttu-id="0cffa-103">指派值</span><span class="sxs-lookup"><span data-stu-id="0cffa-103">Assign values</span></span>
<span data-ttu-id="0cffa-104">如果傳送埠標示為動態，您可以將某個字串類型的變數值，包含要使用於 [運算式] 圖形的連接埠 URI 指派給它。</span><span class="sxs-lookup"><span data-stu-id="0cffa-104">If a send port is marked as dynamic, you can assign to it the value of some variable of type string that contains the URI of the port you want to use in the Expression shape.</span></span> <span data-ttu-id="0cffa-105">例如，</span><span class="sxs-lookup"><span data-stu-id="0cffa-105">For example,</span></span>  
  
```  
DynamicSendPort(Microsoft.XLANGs.BaseTypes.Address)="mailto:johnd@contoso.com";  
DynamicSendPort(Microsoft.XLANGs.BaseTypes.Address)=@"file://C:\MyLocation\%SourceFileName%.xml";  
DynamicSendPort(Microsoft.XLANGs.BaseTypes.Address)=@"msmq://.\private$\MyQueue";  
DynamicSendPort(Microsoft.XLANGs.BaseTypes.Address)="http://MyOrder.contoso.com";  
DynamicSendPort(Microsoft.XLANGs.BaseTypes.Address)="ftp://MyServer/MyDirectory/%MessageID%.xml";  
```  
  
 <span data-ttu-id="0cffa-106">接著，您可以進一步指派屬性給輸出訊息。</span><span class="sxs-lookup"><span data-stu-id="0cffa-106">Then you can further assign the properties to the outgoing messages.</span></span> <span data-ttu-id="0cffa-107">例如，</span><span class="sxs-lookup"><span data-stu-id="0cffa-107">For example,</span></span>  
  
```  
MyOutgoingMessage(SMTP.Subject)="Purcahse Order Received";  
MyOutgoingMessage(FILE.ReceivedFileName)="MyFileName.xml";  
MyOutgoingMessage(FTP.UserName)="MyUserName";  
MyOutgoingMessage(FTP.Password)="MyPassword";  
MyOutgoingMessage((MSMQ.Transactional)=true;  
```  
  
## <a name="see-also"></a><span data-ttu-id="0cffa-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0cffa-108">See Also</span></span>  
[<span data-ttu-id="0cffa-109">設定 File 配接器時的限制</span><span class="sxs-lookup"><span data-stu-id="0cffa-109">Restrictions when configuring the File adapter</span></span>](restrictions-when-configuring-the-file-adapter.md)