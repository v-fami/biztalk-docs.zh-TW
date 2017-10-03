---
title: "開發和設定 BizTalk Server EDI 解決方案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 65629eb1-8e08-4233-9331-c53ae0abaed4
caps.latest.revision: "29"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c6520b062ebc5c106e2f162cc92ff4c793a417b4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="developing-and-configuring-biztalk-server-edi-solutions"></a><span data-ttu-id="d661e-102">開發和設定 BizTalk Server EDI 解決方案</span><span class="sxs-lookup"><span data-stu-id="d661e-102">Developing and Configuring BizTalk Server EDI Solutions</span></span>
<span data-ttu-id="d661e-103">若要建立開發人員的資訊[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI 解決方案。</span><span class="sxs-lookup"><span data-stu-id="d661e-103">Information for developers to create [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI solutions.</span></span> <span data-ttu-id="d661e-104">這些解決方案使用建立的 BizTalk 專案系統設計環境和[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="d661e-104">These solutions are created using the BizTalk project system design environment and the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
 <span data-ttu-id="d661e-105">開發 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI 解決方案之前，請先確定您已完整安裝和設定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 以及 EDI 功能。</span><span class="sxs-lookup"><span data-stu-id="d661e-105">Before developing a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI solution, make sure that you have fully installed and configured [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] with the EDI feature.</span></span> <span data-ttu-id="d661e-106">請參閱[BizTalk Server 的新功能，安裝、 設定及升級](../install-and-config-guides/biztalk-server-what-s-new-installation-configuration-and-upgrade.md)。</span><span class="sxs-lookup"><span data-stu-id="d661e-106">See [BizTalk Server - What's New, Installation, Configuration, and Upgrade](../install-and-config-guides/biztalk-server-what-s-new-installation-configuration-and-upgrade.md).</span></span> <span data-ttu-id="d661e-107">開發 EDI 解決方案所需的其他 EDI 特定組態，請參閱[後設定步驟來最佳化您的環境](../install-and-config-guides/post-configuration-steps-to-optimize-your-environment.md)。</span><span class="sxs-lookup"><span data-stu-id="d661e-107">For additional EDI-specific configuration required for developing an EDI solution, see [Post-configuration steps to optimize your environment](../install-and-config-guides/post-configuration-steps-to-optimize-your-environment.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d661e-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="d661e-108">In This Section</span></span>  
  
-   [<span data-ttu-id="d661e-109">設定 EDI 屬性</span><span class="sxs-lookup"><span data-stu-id="d661e-109">Configuring EDI Properties</span></span>](../core/configuring-edi-properties.md)  
  
-   [<span data-ttu-id="d661e-110">設定全域或後援協議屬性</span><span class="sxs-lookup"><span data-stu-id="d661e-110">Configuring Global or Fallback Agreement Properties</span></span>](../core/configuring-global-or-fallback-agreement-properties.md)  
  
-   [<span data-ttu-id="d661e-111">設定 EDI 管線屬性</span><span class="sxs-lookup"><span data-stu-id="d661e-111">Configuring EDI Pipeline Properties</span></span>](../core/configuring-edi-pipeline-properties.md)  
  
-   [<span data-ttu-id="d661e-112">設定 EDI 解決方案的連接埠</span><span class="sxs-lookup"><span data-stu-id="d661e-112">Configuring Ports for an EDI Solution</span></span>](../core/configuring-ports-for-an-edi-solution.md)  
  
-   [<span data-ttu-id="d661e-113">設定 EDI 通知</span><span class="sxs-lookup"><span data-stu-id="d661e-113">Configuring EDI Acknowledgments</span></span>](../core/configuring-edi-acknowledgments.md)  
  
-   [<span data-ttu-id="d661e-114">設定 EDI 批次</span><span class="sxs-lookup"><span data-stu-id="d661e-114">Configuring EDI Batches</span></span>](../core/configuring-edi-batches.md)  
  
-   [<span data-ttu-id="d661e-115">開發 EDI 結構描述</span><span class="sxs-lookup"><span data-stu-id="d661e-115">Developing EDI Schemas</span></span>](../core/developing-edi-schemas.md)  
  
-   [<span data-ttu-id="d661e-116">使用設計階段 XML 工具</span><span class="sxs-lookup"><span data-stu-id="d661e-116">Using Design-Time XML Tools</span></span>](../core/using-design-time-xml-tools.md)  
  
-   [<span data-ttu-id="d661e-117">EDI 內容屬性</span><span class="sxs-lookup"><span data-stu-id="d661e-117">EDI Context Properties</span></span>](../core/edi-context-properties.md)  
  
-   [<span data-ttu-id="d661e-118">EDI 覆寫內容屬性</span><span class="sxs-lookup"><span data-stu-id="d661e-118">EDI Override Context Properties</span></span>](../core/edi-override-context-properties.md)  
  
## <a name="see-also"></a><span data-ttu-id="d661e-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d661e-119">See Also</span></span>  

[<span data-ttu-id="d661e-120">教學課程和逐步解說的 EDI、 AS2 和 EDIFACT</span><span class="sxs-lookup"><span data-stu-id="d661e-120">Tutorials and walkthroughs for EDI, AS2, and EDIFACT</span></span>](../core/tutorials-and-walkthroughs-for-edi-as2-and-edifact.md)  
[<span data-ttu-id="d661e-121">開發和設定 BizTalk Server AS2 解決方案</span><span class="sxs-lookup"><span data-stu-id="d661e-121">Developing and Configuring BizTalk Server AS2 Solutions</span></span>](../core/developing-and-configuring-biztalk-server-as2-solutions.md)