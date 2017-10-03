---
title: "建立 TIBCO Rendezvous 傳送處理常式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: send handlers
ms.assetid: ad996c4f-e6ed-4582-a768-0cb1ad25b1d8
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 56b33210474275ffdf961add0b4eb3da0790d703
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="creating-tibco-rendezvous-send-handlers"></a><span data-ttu-id="07125-102">建立 TIBCO Rendezvous 傳送處理常式</span><span class="sxs-lookup"><span data-stu-id="07125-102">Creating TIBCO Rendezvous Send Handlers</span></span>
<span data-ttu-id="07125-103">本節說明如何建立結構描述，以在 BizTalk Server 協調流程中使用 TIBCO Rendezvous。</span><span class="sxs-lookup"><span data-stu-id="07125-103">This section explains how to create a schema to use TIBCO Rendezvous in a BizTalk Server orchestration.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="07125-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="07125-104">In This Section</span></span>  
  
-   [<span data-ttu-id="07125-105">管理</span><span class="sxs-lookup"><span data-stu-id="07125-105">Management</span></span>](../core/management.md)  
  
-   [<span data-ttu-id="07125-106">如何為 TIBCO Rendezvous 建立傳送埠</span><span class="sxs-lookup"><span data-stu-id="07125-106">How to Create Send Ports for TIBCO Rendezvous</span></span>](../core/how-to-create-send-ports-for-tibco-rendezvous.md)  
  
-   [<span data-ttu-id="07125-107">如何設定 TIBCO Rendezvous 傳輸屬性</span><span class="sxs-lookup"><span data-stu-id="07125-107">How to Set TIBCO Rendezvous Transport Properties</span></span>](../core/how-to-set-tibco-rendezvous-transport-properties.md)  
  
-   [<span data-ttu-id="07125-108">如何設定 TIBCO Rendezvous 的傳送管線</span><span class="sxs-lookup"><span data-stu-id="07125-108">How to Set Send Pipelines for TIBCO Rendezvous</span></span>](../core/how-to-set-send-pipelines-for-tibco-rendezvous.md)  
  
-   [<span data-ttu-id="07125-109">使用 TIBCO Rendezvous 傳送埠從 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="07125-109">Using TIBCO Rendezvous Send Ports from BizTalk Server</span></span>](../core/using-tibco-rendezvous-send-ports-from-biztalk-server.md)  
  
-   [<span data-ttu-id="07125-110">使用 BizTalk Server 從 TIBCO Rendezvous 傳送訊息</span><span class="sxs-lookup"><span data-stu-id="07125-110">Using BizTalk Server from TIBCO Rendezvous to Send Messages</span></span>](../core/using-biztalk-server-from-tibco-rendezvous-to-send-messages.md)  
  
-   [<span data-ttu-id="07125-111">TIBCO Rendezvous 中的傳送處理常式的資料類型對應</span><span class="sxs-lookup"><span data-stu-id="07125-111">Data Type Mapping for Send Handlers in TIBCO Rendezvous</span></span>](../core/data-type-mapping-for-send-handlers-in-tibco-rendezvous.md)  
  
-   [<span data-ttu-id="07125-112">BizTalk Server 訊息內容屬性 （傳送處理常式）</span><span class="sxs-lookup"><span data-stu-id="07125-112">BizTalk Server Message Context Properties (Send Handlers)</span></span>](../core/biztalk-server-message-context-properties-send-handlers.md)