---
title: MQSeries 配接器批次和交易處理 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IBM WebSphere MQ queues
- transactions, MQSeries adapters
- MQSeries adapters, transactions
- MQSeries adapters, IBM WebSphere MQ queues
- MQSeries adapters, batching
- batching, MQSeries adapters
ms.assetid: 2e43fca9-acbd-4fd3-8df3-5f7398553830
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ffcdec02c464b9398acbece35657e0c3d1dc4432
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22262982"
---
# <a name="mqseries-adapter-batching-and-transaction-handling"></a><span data-ttu-id="3fe3f-102">MQSeries 配接器批次和交易處理</span><span class="sxs-lookup"><span data-stu-id="3fe3f-102">MQSeries Adapter Batching and Transaction Handling</span></span>
<span data-ttu-id="3fe3f-103">MQSeries 配接器只有在未接收到所有資料時才會停止交易。</span><span class="sxs-lookup"><span data-stu-id="3fe3f-103">The MQSeries adapter stops a transaction only if it does not receive all the data.</span></span> <span data-ttu-id="3fe3f-104">配接器交易的界限是配接器結束點 (MQSeries Server 上的 MQSeries 佇列) 和 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="3fe3f-104">The boundaries of a transaction for the adapter are the adapter endpoint (MQSeries queue on the MQSeries Server) and the MessageBox database.</span></span>  
  
 <span data-ttu-id="3fe3f-105">若 BizTalk 應用程式使訊息無效，則配接器會將訊息移動到訊息擱置佇列。</span><span class="sxs-lookup"><span data-stu-id="3fe3f-105">If the BizTalk application invalidates a message, the adapter moves the message to the suspended queue.</span></span> <span data-ttu-id="3fe3f-106">但是，因為從配接器的觀點來看，它仍是有效的交易 (配接器已接收到所有資料)，因此配接器會認可交易。</span><span class="sxs-lookup"><span data-stu-id="3fe3f-106">However, because it is still a valid transaction from the point of view of the adapter (the adapter received all the data), the adapter commits the transaction.</span></span>  
  
 <span data-ttu-id="3fe3f-107">您可以在設定配接器時設定屬性，來控制批次和交易處理。</span><span class="sxs-lookup"><span data-stu-id="3fe3f-107">You can control batching and transaction handling by setting properties when configuring the adapter.</span></span> <span data-ttu-id="3fe3f-108">如需詳細資訊，請參閱[設定 MQSeries 配接器](../core/configuring-the-mqseries-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="3fe3f-108">For more information, see [Configuring the MQSeries Adapter](../core/configuring-the-mqseries-adapter.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fe3f-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3fe3f-109">See Also</span></span>  
 [<span data-ttu-id="3fe3f-110">MQSeries 配接器屬性</span><span class="sxs-lookup"><span data-stu-id="3fe3f-110">MQSeries Adapter Properties</span></span>](../core/mqseries-adapter-properties.md)