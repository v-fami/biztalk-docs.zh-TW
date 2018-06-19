---
title: 接收器介面 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c7ab77d4-705a-4b39-8c33-a7532ae6484c
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 77b42530d721a6dcee52e082fe46deae9ae06405
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22268326"
---
# <a name="receiver-interfaces"></a><span data-ttu-id="c24fa-102">接收器介面</span><span class="sxs-lookup"><span data-stu-id="c24fa-102">Receiver Interfaces</span></span>
<span data-ttu-id="c24fa-103">除了標準的配接器介面，接收配接器必須實作**IBTTransportConfig**。</span><span class="sxs-lookup"><span data-stu-id="c24fa-103">In addition to the standard adapter interfaces, receive adapters need to implement **IBTTransportConfig**.</span></span> <span data-ttu-id="c24fa-104">這是 BizTalk 傳訊引擎將接收位置傳遞到配接器時所使用的介面。</span><span class="sxs-lookup"><span data-stu-id="c24fa-104">This is the interface on which the BizTalk Messaging Engine delivers receive location configuration to the adapter.</span></span>  
  
## <a name="request-response-adapters"></a><span data-ttu-id="c24fa-105">要求-回應配接器</span><span class="sxs-lookup"><span data-stu-id="c24fa-105">Request-Response Adapters</span></span>  
 <span data-ttu-id="c24fa-106">某些情況下，接收配接器可能也需要處理傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="c24fa-106">Receive adapters may also need to handle send messages in some cases.</span></span> <span data-ttu-id="c24fa-107">執行此操作的配接器通常稱為雙向配接器或「要求-回應」配接器。</span><span class="sxs-lookup"><span data-stu-id="c24fa-107">Adapters that do this are usually referred to as two-way, or Request-Response adapters.</span></span> <span data-ttu-id="c24fa-108">若要能夠傳送訊息，接收配接器必須實作**IBTTransmitter**。</span><span class="sxs-lookup"><span data-stu-id="c24fa-108">To be able to send messages, a receive adapter needs to implement **IBTTransmitter**.</span></span>  
  
 <span data-ttu-id="c24fa-109">下圖顯示接收配接器實作的介面。</span><span class="sxs-lookup"><span data-stu-id="c24fa-109">The following figure shows the interfaces implemented by receive adapters.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c24fa-110">**IBTBatchTransmitter**介面不支援要求-回應配接器。</span><span class="sxs-lookup"><span data-stu-id="c24fa-110">The **IBTBatchTransmitter** interface is not supported for Request-Response adapters.</span></span>  
  
 ![](../core/media/requestresponseadapters.gif "RequestResponseAdapters")