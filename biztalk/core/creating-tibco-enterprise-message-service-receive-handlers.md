---
title: "建立 TIBCO Enterprise Message Service 接收處理常式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: receive handlers
ms.assetid: e1307e3c-0237-4f19-a642-58e694fe95d0
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 83163701f897b782d577351cd08b3f2650ae6fb0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="creating-tibco-enterprise-message-service-receive-handlers"></a><span data-ttu-id="fa1a8-102">建立 TIBCO Enterprise Message Service 接收處理常式</span><span class="sxs-lookup"><span data-stu-id="fa1a8-102">Creating TIBCO Enterprise Message Service Receive Handlers</span></span>
<span data-ttu-id="fa1a8-103">TIBCO Enterprise Message Service 接收器是一項待命程式服務，能夠註冊特定的佇列或主題，然後接收相關的訊息。</span><span class="sxs-lookup"><span data-stu-id="fa1a8-103">TIBCO Enterprise Message Service receiver is a listener service that registers a particular Queue or Topic and receives the relative messages.</span></span> <span data-ttu-id="fa1a8-104">BizTalk Adapter for TIBCO Enterprise Message Service 會先開啟新的工作階段以向 TIBCO Enterprise Message Service 註冊，然後才繼續輪詢以接收訊息。</span><span class="sxs-lookup"><span data-stu-id="fa1a8-104">BizTalk Adapter for TIBCO Enterprise Message Service first registers with TIBCO Enterprise Message Service by opening a new session, and then it continues polling to receive messages..</span></span> <span data-ttu-id="fa1a8-105">本節將說明如何設定傳送埠以連線至 TIBCO Enterprise Message Service，以及如何在協調流程中納入 XML 以在執行階段與 TIBCO EMS 互動。</span><span class="sxs-lookup"><span data-stu-id="fa1a8-105">This section explains how to set the receive port to connect to TIBCO Enterprise Message Service and how to include XML in your orchestration to interact with TIBCO EMS at run time.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fa1a8-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="fa1a8-106">In This Section</span></span>  
  
-   [<span data-ttu-id="fa1a8-107">如何建立 TIBCO Enterprise Message Service 中的接收埠</span><span class="sxs-lookup"><span data-stu-id="fa1a8-107">How to Create Receive Ports in TIBCO Enterprise Message Service</span></span>](../core/how-to-create-receive-ports-in-tibco-enterprise-message-service.md)  
  
-   [<span data-ttu-id="fa1a8-108">設定 TIBCO 企業訊息服務傳輸屬性的接收埠</span><span class="sxs-lookup"><span data-stu-id="fa1a8-108">Setting TIBCO Enterprise Message Service Transport Properties for the Receive Port</span></span>](../core/set-tibco-enterprise-message-service-transport-properties-for-the-receive-port.md)  
  
-   [<span data-ttu-id="fa1a8-109">如何設定 TIBCO Enterprise Message Service 的接收管線</span><span class="sxs-lookup"><span data-stu-id="fa1a8-109">How to Set Receive Pipelines for TIBCO Enterprise Message Service</span></span>](../core/how-to-set-receive-pipelines-for-tibco-enterprise-message-service.md)