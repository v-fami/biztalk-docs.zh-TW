---
title: "開發和設定 BizTalk Server AS2 解決方案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 62aa76f2-b692-41d9-862a-3e0089635800
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b3cd1bfb6bba469f6096242f3e57fd199a4439e5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="developing-and-configuring-biztalk-server-as2-solutions"></a><span data-ttu-id="8b13b-102">開發和設定 BizTalk Server AS2 解決方案</span><span class="sxs-lookup"><span data-stu-id="8b13b-102">Developing and Configuring BizTalk Server AS2 Solutions</span></span>
## <a name="overview"></a><span data-ttu-id="8b13b-103">概觀</span><span class="sxs-lookup"><span data-stu-id="8b13b-103">Overview</span></span>
<span data-ttu-id="8b13b-104">開發人員建立 BizTalk AS2 解決方案的資訊。</span><span class="sxs-lookup"><span data-stu-id="8b13b-104">Information for developers to create BizTalk AS2 solutions.</span></span> <span data-ttu-id="8b13b-105">這些解決方案使用建立的 BizTalk 專案系統設計環境和[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="8b13b-105">These solutions are created using the BizTalk project system design environment and the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>
  
 <span data-ttu-id="8b13b-106">開發 BizTalk Server AS2 解決方案之前，請確定您已完整安裝並設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]以及 AS2 功能。</span><span class="sxs-lookup"><span data-stu-id="8b13b-106">Before developing a BizTalk Server AS2 solution, make sure that you have fully installed and configured [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] with the AS2 feature.</span></span> <span data-ttu-id="8b13b-107">請參閱[BizTalk Server 的新功能，安裝、 設定及升級](../install-and-config-guides/biztalk-server-what-s-new-installation-configuration-and-upgrade.md)。</span><span class="sxs-lookup"><span data-stu-id="8b13b-107">See [BizTalk Server - What's New, Installation, Configuration, and Upgrade](../install-and-config-guides/biztalk-server-what-s-new-installation-configuration-and-upgrade.md).</span></span> <span data-ttu-id="8b13b-108">其他 AS2 特定組態所需的開發 EDI 解決方案，請參閱[後設定步驟來最佳化您的環境](../install-and-config-guides/post-configuration-steps-to-optimize-your-environment.md)。</span><span class="sxs-lookup"><span data-stu-id="8b13b-108">For additional AS2-specific configuration that is required for developing an EDI solution, see [Post-configuration steps to optimize your environment](../install-and-config-guides/post-configuration-steps-to-optimize-your-environment.md).</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="8b13b-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="8b13b-109">In This Section</span></span>  
  
-   [<span data-ttu-id="8b13b-110">透過 FILE 傳送埠傳送 AS2 訊息</span><span class="sxs-lookup"><span data-stu-id="8b13b-110">Sending an AS2 Message over a FILE Send Port</span></span>](../core/sending-an-as2-message-over-a-file-send-port.md)  
  
-   [<span data-ttu-id="8b13b-111">設定 AS2 屬性</span><span class="sxs-lookup"><span data-stu-id="8b13b-111">Configuring AS2 Properties</span></span>](../core/configuring-as2-properties.md)  
  
-   [<span data-ttu-id="8b13b-112">設定 AS2 管線屬性</span><span class="sxs-lookup"><span data-stu-id="8b13b-112">Configuring AS2 Pipeline Properties</span></span>](../core/configuring-as2-pipeline-properties.md)  
  
-   [<span data-ttu-id="8b13b-113">設定 AS2 方案的連接埠</span><span class="sxs-lookup"><span data-stu-id="8b13b-113">Configuring Ports for an AS2 Solution</span></span>](../core/configuring-ports-for-an-as2-solution.md)  
  
-   [<span data-ttu-id="8b13b-114">AS2 安全性</span><span class="sxs-lookup"><span data-stu-id="8b13b-114">AS2 Security</span></span>](../core/as2-security.md)  
  
-   [<span data-ttu-id="8b13b-115">撰寫 AS2 內容屬性的輸出合作對象解析</span><span class="sxs-lookup"><span data-stu-id="8b13b-115">Writing AS2 Context Properties for Outbound Party Resolution</span></span>](../core/writing-as2-context-properties-for-outbound-party-resolution.md)  
  
-   [<span data-ttu-id="8b13b-116">AS2 內容屬性</span><span class="sxs-lookup"><span data-stu-id="8b13b-116">AS2 Context Properties</span></span>](../core/as2-context-properties.md)  
  
## <a name="see-also"></a><span data-ttu-id="8b13b-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8b13b-117">See Also</span></span>  
[<span data-ttu-id="8b13b-118">教學課程和逐步解說的 EDI、 AS2 和 EDIFACT</span><span class="sxs-lookup"><span data-stu-id="8b13b-118">Tutorials and walkthroughs for EDI, AS2, and EDIFACT</span></span>](../core/tutorials-and-walkthroughs-for-edi-as2-and-edifact.md)  
[<span data-ttu-id="8b13b-119">開發和設定 BizTalk Server EDI 解決方案</span><span class="sxs-lookup"><span data-stu-id="8b13b-119">Developing and Configuring BizTalk Server EDI Solutions</span></span>](../core/developing-and-configuring-biztalk-server-edi-solutions.md)