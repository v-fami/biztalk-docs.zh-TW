---
title: "BizTalk Server EDI 功能 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9fd91569-f246-40dc-acb1-4f9296479296
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 10a037349cb967fab3d9c0d79bdf47c2f0f8a194
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="biztalk-server-edi-functionality"></a><span data-ttu-id="92895-102">BizTalk Server EDI 功能</span><span class="sxs-lookup"><span data-stu-id="92895-102">BizTalk Server EDI Functionality</span></span>
<span data-ttu-id="92895-103">BizTalk Server 處理 EDI 訊息使用的核心組合[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]功能和 EDI 特有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]功能。</span><span class="sxs-lookup"><span data-stu-id="92895-103">BizTalk Server processes EDI messages using a combination of core [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] features and EDI-specific [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] features.</span></span> <span data-ttu-id="92895-104">這讓 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 可以執行 EDI 傳訊特有的處理，同時利用其核心傳訊功能。</span><span class="sxs-lookup"><span data-stu-id="92895-104">This enables [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to perform the processing that is unique to EDI messaging, while leveraging its core messaging functionality.</span></span>  
  
 <span data-ttu-id="92895-105">本節說明基本 EDI 傳訊的運作方式，以及 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 如何加以實作。</span><span class="sxs-lookup"><span data-stu-id="92895-105">This section describes how basic EDI messaging works and how [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] implements it.</span></span> <span data-ttu-id="92895-106">此外，還說明如何將 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中的交易夥伴協議定義用於 EDI 傳訊、接收端 EDI 處理及傳送端 EDI 處理。</span><span class="sxs-lookup"><span data-stu-id="92895-106">It also describes how a trading partner agreement definition in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] can be leveraged for EDI messaging, receive-side EDI processing, and send-side EDI processing.</span></span>  
  
 <span data-ttu-id="92895-107">如需說明如何在 BizTalk Server 和其他版本中支援 EDI 處理的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，以及 EDI 標準支援和 EDI 文件結構描述支援的說明，請參閱[EDI 支援問題](../core/edi-support-issues.md)。</span><span class="sxs-lookup"><span data-stu-id="92895-107">For a description of how EDI processing is supported in BizTalk Server and other versions of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], and for a description of EDI standards support and EDI document schema support, see [EDI Support Issues](../core/edi-support-issues.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="92895-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="92895-108">In This Section</span></span>  
  
-   [<span data-ttu-id="92895-109">BizTalk Server 中的 EDI 支援</span><span class="sxs-lookup"><span data-stu-id="92895-109">EDI Support in BizTalk Server</span></span>](../core/edi-support-in-biztalk-server1.md)  
  
-   [<span data-ttu-id="92895-110">BizTalk Server 中的 HIPAA 支援</span><span class="sxs-lookup"><span data-stu-id="92895-110">HIPAA Support in BizTalk Server</span></span>](../core/hipaa-support-in-biztalk-server.md)  
  
-   [<span data-ttu-id="92895-111">BizTalk Server 中的 EDI 處理</span><span class="sxs-lookup"><span data-stu-id="92895-111">EDI Processing in BizTalk Server</span></span>](../core/edi-processing-in-biztalk-server.md)  
  
-   [<span data-ttu-id="92895-112">EDI 支援問題</span><span class="sxs-lookup"><span data-stu-id="92895-112">EDI Support Issues</span></span>](../core/edi-support-issues.md)  
  
## <a name="see-also"></a><span data-ttu-id="92895-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="92895-113">See Also</span></span>  
 <span data-ttu-id="92895-114">[BizTalk Server AS2 功能](../core/biztalk-server-as2-functionality.md) </span><span class="sxs-lookup"><span data-stu-id="92895-114">[BizTalk Server AS2 Functionality](../core/biztalk-server-as2-functionality.md) </span></span>  
 <span data-ttu-id="92895-115">[EDI 解決方案架構](../core/edi-solution-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="92895-115">[EDI Solution Architecture](../core/edi-solution-architecture.md) </span></span>  
 [<span data-ttu-id="92895-116">開發和設定 BizTalk Server EDI 解決方案</span><span class="sxs-lookup"><span data-stu-id="92895-116">Developing and Configuring BizTalk Server EDI Solutions</span></span>](../core/developing-and-configuring-biztalk-server-edi-solutions.md)