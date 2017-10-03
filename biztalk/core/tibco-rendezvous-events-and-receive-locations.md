---
title: "TIBCO Rendezvous 事件與接收位置 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: receive locations, life cycle
ms.assetid: 3576af82-4723-4efc-961e-40b1150cf13d
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e9278687ff212fc2368eca138780417d7c052824
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="tibco-rendezvous-events-and-receive-locations"></a><span data-ttu-id="6af44-102">TIBCO Rendezvous 事件與接收位置</span><span class="sxs-lookup"><span data-stu-id="6af44-102">TIBCO Rendezvous Events and Receive Locations</span></span>
<span data-ttu-id="6af44-103">所有 TIBCO Rendezvous 系統均可傳送訊息給它們選擇的主體名稱。</span><span class="sxs-lookup"><span data-stu-id="6af44-103">Any TIBCO Rendezvous system can send messages to their subject name of choice.</span></span> <span data-ttu-id="6af44-104">概念*事件*是訊息的其他 TIBCO Rendezvous 程式產生。</span><span class="sxs-lookup"><span data-stu-id="6af44-104">The concept of *event* is the generation of messages by other TIBCO Rendezvous programs.</span></span>  
  
 <span data-ttu-id="6af44-105">下列步驟說明接收位置的生命週期：</span><span class="sxs-lookup"><span data-stu-id="6af44-105">The following steps describe the life cycle of a receive location:</span></span>  
  
1.  <span data-ttu-id="6af44-106">接收位置已建立。</span><span class="sxs-lookup"><span data-stu-id="6af44-106">Receive location is created.</span></span>  
  
2.  <span data-ttu-id="6af44-107">接收位置已和主控件建立關聯。</span><span class="sxs-lookup"><span data-stu-id="6af44-107">Receive location is associated with a host.</span></span>  
  
3.  <span data-ttu-id="6af44-108">接收位置已繫結到協調流程。</span><span class="sxs-lookup"><span data-stu-id="6af44-108">Receive location is bound to an orchestration.</span></span>  
  
4.  <span data-ttu-id="6af44-109">接收位置已啟用。</span><span class="sxs-lookup"><span data-stu-id="6af44-109">Receive location is enabled.</span></span>  
  
5.  <span data-ttu-id="6af44-110">接收位置收到訊息。</span><span class="sxs-lookup"><span data-stu-id="6af44-110">Receive location receives messages.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6af44-111">每個接收位置都必須有一個唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="6af44-111">Each receive location must have a unique name.</span></span> <span data-ttu-id="6af44-112">在同一個 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 部署中，不能有兩個相同名稱的接收位置。</span><span class="sxs-lookup"><span data-stu-id="6af44-112">Two receive locations cannot have the same name in the same [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] deployment.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6af44-113">建議您在接收位置的放置位置中設定強式存取控制清單 (ACL)。</span><span class="sxs-lookup"><span data-stu-id="6af44-113">It is recommended that you set strong access control lists (ACL) in the receive locations drop locations.</span></span> <span data-ttu-id="6af44-114">例如，您必須在檔案接收位置拾取訊息的目錄中設定強式 ACL，讓只有經過授權的使用者可以在此位置放置訊息。</span><span class="sxs-lookup"><span data-stu-id="6af44-114">For example, you must set strong ACLs for the directory where the file receive location picks up messages, so that only authorized users can drop messages in this location.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6af44-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6af44-115">See Also</span></span>  
 [<span data-ttu-id="6af44-116">建立 TIBCO Rendezvous 接收處理常式</span><span class="sxs-lookup"><span data-stu-id="6af44-116">Creating TIBCO Rendezvous Receive Handlers</span></span>](../core/creating-tibco-rendezvous-receive-handlers.md)