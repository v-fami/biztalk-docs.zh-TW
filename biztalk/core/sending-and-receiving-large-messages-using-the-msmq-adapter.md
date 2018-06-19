---
title: 傳送和接收大型訊息使用 MSMQ 配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- messages, large messages
- configuring [MSMQ adapters], large messages
- MSMQ adapters, large messages
ms.assetid: 208efbed-7b58-4da5-ba27-65a315c2713b
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8a23265be84f2767849e4d61c2e9a95bfc9ed4ce
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22269526"
---
# <a name="sending-and-receiving-large-messages-using-the-msmq-adapter"></a><span data-ttu-id="d61b0-102">使用 MSMQ 配接器傳送和接收大型訊息</span><span class="sxs-lookup"><span data-stu-id="d61b0-102">Sending and Receiving Large Messages Using the MSMQ Adapter</span></span>
<span data-ttu-id="d61b0-103">MSMQ 配接器預設訊息處理部分與訊息大小相關。</span><span class="sxs-lookup"><span data-stu-id="d61b0-103">The MSMQ adapter default message handling depends, in part, on the size of the message.</span></span> <span data-ttu-id="d61b0-104">當訊息小於 4 MB 時，MSMQ 配接器使用 .NET Framework 類別庫。</span><span class="sxs-lookup"><span data-stu-id="d61b0-104">When a message is less than four megabytes (4 MB), the MSMQ adapter uses the .NET Framework Class Library.</span></span> <span data-ttu-id="d61b0-105">否則，它會使用 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中的大型訊息延伸模組。</span><span class="sxs-lookup"><span data-stu-id="d61b0-105">Otherwise, it uses the large message extensions in Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
 <span data-ttu-id="d61b0-106">若您的應用程式一貫接收或傳送大型訊息，則可能必須控制配接器使用的記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="d61b0-106">If your application consistently receives or sends large messages, you may have to control the amount of memory that the adapter uses.</span></span> <span data-ttu-id="d61b0-107">如需有關節省記憶體的詳細資訊，請參閱[最佳化 MSMQ 配接器效能](../core/optimizing-performance-of-the-msmq-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="d61b0-107">For more information about conserving memory, see [Optimizing Performance of the MSMQ Adapter](../core/optimizing-performance-of-the-msmq-adapter.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d61b0-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d61b0-108">See Also</span></span>  
 <span data-ttu-id="d61b0-109">[最佳化 MSMQ 配接器效能](../core/optimizing-performance-of-the-msmq-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="d61b0-109">[Optimizing Performance of the MSMQ Adapter](../core/optimizing-performance-of-the-msmq-adapter.md) </span></span>  
 [<span data-ttu-id="d61b0-110">設定 MSMQ 配接器</span><span class="sxs-lookup"><span data-stu-id="d61b0-110">Configuring the MSMQ Adapter</span></span>](../core/configuring-the-msmq-adapter.md)