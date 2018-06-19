---
title: 開發接收配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cd2623c4-dc92-435f-83d4-1b6213f3cf59
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c8be86000a154da7b3087d34e92f61da964065ed
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22238462"
---
# <a name="developing-a-receive-adapter"></a><span data-ttu-id="42e25-102">開發接收配接器</span><span class="sxs-lookup"><span data-stu-id="42e25-102">Developing a Receive Adapter</span></span>
<span data-ttu-id="42e25-103">本節描述接收配接器內發生的物件互動。</span><span class="sxs-lookup"><span data-stu-id="42e25-103">This section describes the object interactions that occur within receive adapters.</span></span> <span data-ttu-id="42e25-104">您可以使用此項資訊，在建立接收配接器時引導自訂配接器開發，或了解原生配接器的運作方式。</span><span class="sxs-lookup"><span data-stu-id="42e25-104">You can use this information to guide custom adapter development when creating receive adapters, or to learn about how the native adapters work.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="42e25-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="42e25-105">In This Section</span></span>  
  
-   [<span data-ttu-id="42e25-106">交換模式的接收配接器</span><span class="sxs-lookup"><span data-stu-id="42e25-106">Exchange Patterns for Receive Adapters</span></span>](../core/exchange-patterns-for-receive-adapters.md)  
  
-   [<span data-ttu-id="42e25-107">具現化，並初始化接收配接器</span><span class="sxs-lookup"><span data-stu-id="42e25-107">Instantiating and Initializing a Receive Adapter</span></span>](../core/instantiating-and-initializing-a-receive-adapter.md)  
  
-   [<span data-ttu-id="42e25-108">接收配接器作業</span><span class="sxs-lookup"><span data-stu-id="42e25-108">Receive Adapter Operations</span></span>](../core/receive-adapter-operations.md)  
  
-   [<span data-ttu-id="42e25-109">批次處理接收訊息處理</span><span class="sxs-lookup"><span data-stu-id="42e25-109">Batching Messages for Receive Processing</span></span>](../core/batching-messages-for-receive-processing.md)  
  
-   [<span data-ttu-id="42e25-110">接收配接器介面。</span><span class="sxs-lookup"><span data-stu-id="42e25-110">Interfaces for Receive Adapters</span></span>](../core/interfaces-for-receive-adapters.md)  
  
-   [<span data-ttu-id="42e25-111">接收配接器的 SSO 支援</span><span class="sxs-lookup"><span data-stu-id="42e25-111">SSO Support for Receive Adapters</span></span>](../core/sso-support-for-receive-adapters.md)