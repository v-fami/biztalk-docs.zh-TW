---
title: 建立 PeopleSoft HTTP 主控件和連接埠 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- HTTP port
- HTTP host
ms.assetid: 3e1ce5fd-32ee-409f-b4c8-f2bc68470f17
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e673b2a2acdcd5248391f245ab990d424aefd298
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22238110"
---
# <a name="creating-a-peoplesoft-http-host-and-port"></a><span data-ttu-id="4ed7d-102">建立 PeopleSoft HTTP 主控件和連接埠</span><span class="sxs-lookup"><span data-stu-id="4ed7d-102">Creating a PeopleSoft HTTP Host and Port</span></span>
<span data-ttu-id="4ed7d-103">PeopleSoft 中的訊息發佈架構稱為 Integration Broker。</span><span class="sxs-lookup"><span data-stu-id="4ed7d-103">The Message publication architecture in PeopleSoft is known as Integration Broker.</span></span> <span data-ttu-id="4ed7d-104">Integration Broker 的主要元件包括：</span><span class="sxs-lookup"><span data-stu-id="4ed7d-104">The main components of Integration Broker are as follows:</span></span>  
  
-   <span data-ttu-id="4ed7d-105">閘道</span><span class="sxs-lookup"><span data-stu-id="4ed7d-105">Gateway</span></span>  
  
-   <span data-ttu-id="4ed7d-106">發佈節點</span><span class="sxs-lookup"><span data-stu-id="4ed7d-106">Publishing node</span></span>  
  
-   <span data-ttu-id="4ed7d-107">訂閱者節點</span><span class="sxs-lookup"><span data-stu-id="4ed7d-107">Subscriber node</span></span>  
  
 <span data-ttu-id="4ed7d-108">這三種元件一起使用便可發佈訊息到 HTTP 接聽程式的 URL。</span><span class="sxs-lookup"><span data-stu-id="4ed7d-108">All three work together to publish a message to a URL for an HTTP listener.</span></span> <span data-ttu-id="4ed7d-109">您必須設定發佈節點。</span><span class="sxs-lookup"><span data-stu-id="4ed7d-109">You must set the Publishing node.</span></span> <span data-ttu-id="4ed7d-110">PeopleSoft 有預設發行節點，也稱為本機訊息節點。</span><span class="sxs-lookup"><span data-stu-id="4ed7d-110">PeopleSoft has a default publishing node, also known as local message node.</span></span> <span data-ttu-id="4ed7d-111">您必須啟用節點，並為發佈節點啟用交易。</span><span class="sxs-lookup"><span data-stu-id="4ed7d-111">You must activate the node and the transactions for the publishing node.</span></span> <span data-ttu-id="4ed7d-112">您必須將訂閱節點設定為外部節點類型，然後啟用節點與交易。</span><span class="sxs-lookup"><span data-stu-id="4ed7d-112">You must set the Subscription node with the type as external node, and then activate the node and the transactions.</span></span> <span data-ttu-id="4ed7d-113">對於此節點，您也必須將類型設定為 HTTP，並設定連線資訊。</span><span class="sxs-lookup"><span data-stu-id="4ed7d-113">For this node, you also set the type to be HTTP and set the connection information.</span></span>  
  
 <span data-ttu-id="4ed7d-114">您可以使用 PeopleSoft Integration Broker 建立 PeopleSoft HTTP 主控件和連接埠，讓 PeopleSoft 傳送事件。</span><span class="sxs-lookup"><span data-stu-id="4ed7d-114">You use PeopleSoft Integration Broker to create a PeopleSoft HTTP Host and Port where PeopleSoft sends events.</span></span> <span data-ttu-id="4ed7d-115">您確定訊息使用中的程序使用中和路由是[如何驗證訊息的活動狀態](../core/how-to-verify-activity-status-of-a-message.md)。</span><span class="sxs-lookup"><span data-stu-id="4ed7d-115">You make sure that the message is active and routed by using the procedure in [How to Verify Activity Status of a Message](../core/how-to-verify-activity-status-of-a-message.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4ed7d-116">本節內容</span><span class="sxs-lookup"><span data-stu-id="4ed7d-116">In This Section</span></span>  
  
-   [<span data-ttu-id="4ed7d-117">如何驗證訊息的活動狀態</span><span class="sxs-lookup"><span data-stu-id="4ed7d-117">How to Verify Activity Status of a Message</span></span>](../core/how-to-verify-activity-status-of-a-message.md)  
  
-   [<span data-ttu-id="4ed7d-118">如何設定整合閘道和 HTTP 輸出連接器</span><span class="sxs-lookup"><span data-stu-id="4ed7d-118">How to Configure the Integration Gateway and HTTP Output Connector</span></span>](../core/how-to-configure-the-integration-gateway-and-http-output-connector.md)  
  
-   [<span data-ttu-id="4ed7d-119">如何建立新的 Gateway 節點</span><span class="sxs-lookup"><span data-stu-id="4ed7d-119">How to Create a New Gateway Node</span></span>](../core/how-to-create-a-new-gateway-node.md)  
  
-   [<span data-ttu-id="4ed7d-120">如何新增交易</span><span class="sxs-lookup"><span data-stu-id="4ed7d-120">How to Add a Transaction</span></span>](../core/how-to-add-a-transaction.md)  
  
-   [<span data-ttu-id="4ed7d-121">如何測試 HTTP 節點</span><span class="sxs-lookup"><span data-stu-id="4ed7d-121">How to Test the HTTP Node</span></span>](../core/how-to-test-the-http-node.md)