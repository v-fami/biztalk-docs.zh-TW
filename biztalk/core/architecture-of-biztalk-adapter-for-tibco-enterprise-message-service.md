---
title: BizTalk Adapter for TIBCO Enterprise Message Service 的架構 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- transmit adapter
- one-way receive operations
- architecture
- one-way send operations
- receive adapter
ms.assetid: 304c7236-aacd-4761-8c33-e876b53e84ff
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 88c7bc6420efb67085e4f3a05f6daf0c5dbd2feb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22230278"
---
# <a name="architecture-of-biztalk-adapter-for-tibco-enterprise-message-service"></a><span data-ttu-id="06dbe-102">BizTalk Adapter for TIBCO Enterprise Message Service 的架構</span><span class="sxs-lookup"><span data-stu-id="06dbe-102">Architecture of BizTalk Adapter for TIBCO Enterprise Message Service</span></span>
<span data-ttu-id="06dbe-103">Microsoft BizTalk Adapter for TIBCO Enterprise Message Service (EMS) 提供在 TIBCO EMS 系統與 BizTalk Server 之間交換即時商務資料的方法。</span><span class="sxs-lookup"><span data-stu-id="06dbe-103">Microsoft BizTalk Adapter for TIBCO Enterprise Message Service (EMS) provides a means to exchange real-time business data between TIBCO EMS systems and BizTalk Server.</span></span> <span data-ttu-id="06dbe-104">此配接器可讓 XML 應用程式與 TIBCO EMS 互動。</span><span class="sxs-lookup"><span data-stu-id="06dbe-104">The adapter enables interaction between an XML application and TIBCO EMS.</span></span>  
  
 <span data-ttu-id="06dbe-105">此配接器接受 XML 訊息，可讓 BizTalk 應用程式使用下列其中一種方式和 TIBCO EMS 進行通訊：</span><span class="sxs-lookup"><span data-stu-id="06dbe-105">The adapter accepts XML messages that enable BizTalk applications to communicate with TIBCO EMS using one of the following:</span></span>  
  
-   <span data-ttu-id="06dbe-106">**傳輸配接器**： 使用靜態單向傳送埠將訊息傳送至 TIBCO EMS。</span><span class="sxs-lookup"><span data-stu-id="06dbe-106">**Transmit Adapter**: Uses a static one-way send port to send a message to TIBCO EMS.</span></span>  
  
-   <span data-ttu-id="06dbe-107">**接收配接器**： 使用靜態的單向接收埠以接收來自 TIBCO EMS 的訊息。</span><span class="sxs-lookup"><span data-stu-id="06dbe-107">**Receive Adapter**: Uses a static one-way receive port to receive messages from TIBCO EMS.</span></span>  
  
## <a name="one-way-send-operation"></a><span data-ttu-id="06dbe-108">單向傳送作業</span><span class="sxs-lookup"><span data-stu-id="06dbe-108">One-Way Send Operation</span></span>  
 <span data-ttu-id="06dbe-109">下圖顯示使用 BizTalk Adapter for TIBCO EMS 之單向傳送作業的架構。</span><span class="sxs-lookup"><span data-stu-id="06dbe-109">The following figure shows the architecture of a one-way send operation using BizTalk Adapter for TIBCO EMS.</span></span>  
  
 ![](../core/media/tibcoems-architecture-send.gif "TIBCOEMS_architecture_send")  
  
## <a name="one-way-receive-operation"></a><span data-ttu-id="06dbe-110">單向接收作業</span><span class="sxs-lookup"><span data-stu-id="06dbe-110">One-Way Receive Operation</span></span>  
 <span data-ttu-id="06dbe-111">下圖顯示使用 BizTalk Adapter for TIBCO EMS 之單向接收作業的架構。</span><span class="sxs-lookup"><span data-stu-id="06dbe-111">The following figure shows the architecture for a one-way receive operation using BizTalk Adapter for TIBCO EMS.</span></span>  
  
 ![](../core/media/tibcoems-architecture-receive.gif "TIBCOEMS_architecture_receive")  
  
## <a name="see-also"></a><span data-ttu-id="06dbe-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="06dbe-112">See Also</span></span>  
 <span data-ttu-id="06dbe-113">[配接器功能](../core/adapter-features.md) </span><span class="sxs-lookup"><span data-stu-id="06dbe-113">[Adapter Features](../core/adapter-features.md) </span></span>  
 [<span data-ttu-id="06dbe-114">規劃與架構</span><span class="sxs-lookup"><span data-stu-id="06dbe-114">Planning and Architecture</span></span>](../core/planning-and-architecture16.md)