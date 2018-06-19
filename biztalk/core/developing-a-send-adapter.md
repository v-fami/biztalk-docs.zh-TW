---
title: 開發傳送配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 11b430da-ddba-4827-b9a1-c61338b9c647
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a186aa40ea97c1139521ecf16b4aedac30e57da9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22239366"
---
# <a name="developing-a-send-adapter"></a><span data-ttu-id="60d94-102">開發傳送配接器</span><span class="sxs-lookup"><span data-stu-id="60d94-102">Developing a Send Adapter</span></span>
<span data-ttu-id="60d94-103">本節描述傳送配接器內發生的物件互動。</span><span class="sxs-lookup"><span data-stu-id="60d94-103">This section describes the object interactions that occur within send adapters.</span></span> <span data-ttu-id="60d94-104">您可以使用此項資訊，當做開發自訂配接器時的指南，或用來瞭解原生配接器的運作方式。</span><span class="sxs-lookup"><span data-stu-id="60d94-104">You can use this information to guide custom adapter development when creating send adapters, or to learn about how the native adapters work.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="60d94-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="60d94-105">In This Section</span></span>  
  
-   [<span data-ttu-id="60d94-106">傳送配接器的交換模式</span><span class="sxs-lookup"><span data-stu-id="60d94-106">Exchange Patterns for Send Adapters</span></span>](../core/exchange-patterns-for-send-adapters.md)  
  
-   [<span data-ttu-id="60d94-107">具現化，並初始化傳送配接器</span><span class="sxs-lookup"><span data-stu-id="60d94-107">Instantiating and Initializing a Send Adapter</span></span>](../core/instantiating-and-initializing-a-send-adapter.md)  
  
-   [<span data-ttu-id="60d94-108">傳送配接器作業</span><span class="sxs-lookup"><span data-stu-id="60d94-108">Send Adapter Operations</span></span>](../core/send-adapter-operations.md)  
  
-   [<span data-ttu-id="60d94-109">傳送處理的批次訊息</span><span class="sxs-lookup"><span data-stu-id="60d94-109">Batching Messages for Send Processing</span></span>](../core/batching-messages-for-send-processing.md)  
  
-   [<span data-ttu-id="60d94-110">傳送配接器介面</span><span class="sxs-lookup"><span data-stu-id="60d94-110">Interfaces for Send Adapters</span></span>](../core/interfaces-for-send-adapters.md)  
  
-   [<span data-ttu-id="60d94-111">傳送配接器的 SSO 支援</span><span class="sxs-lookup"><span data-stu-id="60d94-111">SSO Support for Send Adapters</span></span>](../core/sso-support-for-send-adapters.md)