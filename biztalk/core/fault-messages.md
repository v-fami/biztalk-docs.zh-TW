---
title: 錯誤訊息 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- error messages
- ports, error messages
- Catch Exception block [Orchestration Designer], error messages
- error messages, receiving
- messages, errors
- error messages, sending
ms.assetid: 33d62260-b5e0-4d14-b2d2-996733d588e7
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e4127fd5718ee910cb298436c0d0f7058ccba55b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22245894"
---
# <a name="fault-messages"></a><span data-ttu-id="9892d-102">錯誤訊息</span><span class="sxs-lookup"><span data-stu-id="9892d-102">Fault Messages</span></span>
<span data-ttu-id="9892d-103">要求回應連接埠可能具有與其關聯的錯誤訊息，因此如果在傳送要求後出現錯誤，回應的服務即可對要求者通訊錯誤，以便代替回應。</span><span class="sxs-lookup"><span data-stu-id="9892d-103">Request-response ports can have fault messages associated with them, so that if something goes wrong after a request is sent, the responding service can communicate the error to the requester, in lieu of the response.</span></span>  
  
 <span data-ttu-id="9892d-104">要求回應連接埠的每項作業都可以處理任意數目的不同錯誤。</span><span class="sxs-lookup"><span data-stu-id="9892d-104">Each operation of a request-response port can handle an arbitrary number of different faults.</span></span> <span data-ttu-id="9892d-105">錯誤訊息可以具有任何訊息類型，不過訊息類型對作業必須是唯一的，而且不能是在該連接埠作業中回應所使用的類型。</span><span class="sxs-lookup"><span data-stu-id="9892d-105">A fault message can have any message type, but the message type must be unique for the operation, and it must not be the type used by the response in that port operation.</span></span>  
  
## <a name="receiving-fault-messages"></a><span data-ttu-id="9892d-106">接收錯誤訊息</span><span class="sxs-lookup"><span data-stu-id="9892d-106">Receiving fault messages</span></span>  
 <span data-ttu-id="9892d-107">如果您的連接埠先傳送要求，然後再接收回應，您就可以使用該作業來接收一個或多個不同的錯誤訊息類型。</span><span class="sxs-lookup"><span data-stu-id="9892d-107">If your port operation sends a request, then receives a response, you can use it to receive one or more different fault message types.</span></span>  
  
 <span data-ttu-id="9892d-108">您可以設定**Catch 例外狀況**區塊來處理傳入的錯誤訊息從做為其例外狀況物件類型的要求-回應連接埠作業選取適當的錯誤。</span><span class="sxs-lookup"><span data-stu-id="9892d-108">You can configure a **Catch Exception** block to handle an incoming fault message by selecting the appropriate fault from the request-response port operation as its Exception Object Type.</span></span>  
  
## <a name="sending-fault-messages"></a><span data-ttu-id="9892d-109">傳送錯誤訊息</span><span class="sxs-lookup"><span data-stu-id="9892d-109">Sending fault messages</span></span>  
 <span data-ttu-id="9892d-110">如果您的連接埠先接收回應，然後再傳送要求，您就可以使用該作業來傳送一個或多個不同的錯誤訊息類型。</span><span class="sxs-lookup"><span data-stu-id="9892d-110">If your port operation receives a response, then sends a request, you can use it to send one or more different fault message types.</span></span>  
  
 <span data-ttu-id="9892d-111">例如如果您的協調流程碰到錯誤狀況而擲回例外狀況，您可以傳送錯誤訊息從**Catch 例外狀況**區塊處理例外狀況。</span><span class="sxs-lookup"><span data-stu-id="9892d-111">If for example your orchestration encounters an error condition and throws an exception, you can send a fault message from within the **Catch Exception** block that handles the exception.</span></span> <span data-ttu-id="9892d-112">您可以建構具有適當類型的錯誤訊息，以便將情況傳達給參與的服務，並在將於連接埠作業中使用對應錯誤的「傳送」圖形上指定錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="9892d-112">You construct a fault message of an appropriate type to convey the situation to the participating service, and specify that fault message on a Send shape that will use the corresponding fault in the port operation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9892d-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9892d-113">See Also</span></span>  
 [<span data-ttu-id="9892d-114">例外狀況</span><span class="sxs-lookup"><span data-stu-id="9892d-114">Exceptions</span></span>](../core/exceptions.md)