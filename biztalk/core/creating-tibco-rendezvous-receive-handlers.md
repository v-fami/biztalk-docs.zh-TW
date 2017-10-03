---
title: "建立 TIBCO Rendezvous 接收處理常式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: receive handlers
ms.assetid: 2d617a97-c165-46bb-b5a7-b66f0c1ff9f2
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 29146e407a65c16ed8becabf19361532a76bc9b5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="creating-tibco-rendezvous-receive-handlers"></a><span data-ttu-id="72041-102">建立 TIBCO Rendezvous 接收處理常式</span><span class="sxs-lookup"><span data-stu-id="72041-102">Creating TIBCO Rendezvous Receive Handlers</span></span>
<span data-ttu-id="72041-103">建立通知或事件和在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中建立其他呼叫相似。</span><span class="sxs-lookup"><span data-stu-id="72041-103">Creating notifications or events is similar to creating other calls in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="72041-104">本節說明如何鍵列接收位置，以接聽 TIBCO Rendezvous 訊息。</span><span class="sxs-lookup"><span data-stu-id="72041-104">This section explains how to create a receive location to listen for TIBCO Rendezvous messages.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="72041-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="72041-105">In This Section</span></span>  
  
-   [<span data-ttu-id="72041-106">TIBCO Rendezvous 事件與接收位置</span><span class="sxs-lookup"><span data-stu-id="72041-106">TIBCO Rendezvous Events and Receive Locations</span></span>](../core/tibco-rendezvous-events-and-receive-locations.md)  
  
-   [<span data-ttu-id="72041-107">如何建立接收埠</span><span class="sxs-lookup"><span data-stu-id="72041-107">How to Create Receive Ports</span></span>](../core/how-to-create-receive-ports.md)  
  
-   [<span data-ttu-id="72041-108">設定 TIBCO Rendezvous 接收傳輸屬性</span><span class="sxs-lookup"><span data-stu-id="72041-108">Setting TIBCO Rendezvous Receive Transport Properties</span></span>](../core/setting-tibco-rendezvous-receive-transport-properties.md)  
  
-   [<span data-ttu-id="72041-109">如何設定 TIBCO rendezvous 接收管線</span><span class="sxs-lookup"><span data-stu-id="72041-109">How to Set Receive Pipelines for TIBCO Rendezvous</span></span>](../core/how-to-set-receive-pipelines-for-tibco-rendezvous.md)  
  
-   [<span data-ttu-id="72041-110">使用 TIBCO Rendezvous 接收埠從 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="72041-110">Using TIBCO Rendezvous Receive Ports from BizTalk Server</span></span>](../core/using-tibco-rendezvous-receive-ports-from-biztalk-server.md)  
  
-   [<span data-ttu-id="72041-111">使用 TIBCO Rendezvous 從 BizTalk Server 接收訊息</span><span class="sxs-lookup"><span data-stu-id="72041-111">Using BizTalk Server from TIBCO Rendezvous to Receive Messages</span></span>](../core/using-biztalk-server-from-tibco-rendezvous-to-receive-messages.md)  
  
-   [<span data-ttu-id="72041-112">TIBCO Rendezvous 中的訊息對應</span><span class="sxs-lookup"><span data-stu-id="72041-112">Message Mapping in TIBCO Rendezvous</span></span>](../core/message-mapping-in-tibco-rendezvous.md)  
  
-   [<span data-ttu-id="72041-113">資料類型對應在 TIBCO Rendezvous 接收處理常式</span><span class="sxs-lookup"><span data-stu-id="72041-113">Data Type Mapping for Receive Handlers in TIBCO Rendezvous</span></span>](../core/data-type-mapping-for-receive-handlers-in-tibco-rendezvous.md)  
  
-   [<span data-ttu-id="72041-114">BizTalk Server 訊息內容屬性 （接收處理常式）</span><span class="sxs-lookup"><span data-stu-id="72041-114">BizTalk Server Message Context Properties (Receive Handlers)</span></span>](../core/biztalk-server-message-context-properties-receive-handlers.md)