---
title: "MSMQT 過時 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 007d65ce-d2a2-4602-80c8-55b26617f397
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f869dde7cb4c793e1e36beee6a20bc89d19272e8
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="msmqt-deprecation"></a><span data-ttu-id="de4cd-102">MSMQT 過時</span><span class="sxs-lookup"><span data-stu-id="de4cd-102">MSMQT Deprecation</span></span>
<span data-ttu-id="de4cd-103">MSMQT 功能已經自 BizTalk Server 移除。</span><span class="sxs-lookup"><span data-stu-id="de4cd-103">The MSMQT feature has been removed from BizTalk Server.</span></span> <span data-ttu-id="de4cd-104">在協調流程設計師中，MSMQT 傳輸選項仍然可在設計階段連接埠組態精靈中下當您選擇的映像中所示**現在指定**選項**連接埠繫結**.</span><span class="sxs-lookup"><span data-stu-id="de4cd-104">In Orchestration Designer, the MSMQT transport option remains available in the design-time Port Configuration Wizard as shown in the image below when you choose the **Specify now** option for **Port binding**.</span></span>  
  
 <span data-ttu-id="de4cd-105">**顯示 MSMQT 傳輸的連接埠組態精靈**</span><span class="sxs-lookup"><span data-stu-id="de4cd-105">**Port Configuration Wizard showing MSMQT transport**</span></span>  
  
 <span data-ttu-id="de4cd-106">![](../core/media/portconfigurationwizard-msmqt-transport.gif "PortConfigurationWizard_MSMQT_Transport")</span><span class="sxs-lookup"><span data-stu-id="de4cd-106">![](../core/media/portconfigurationwizard-msmqt-transport.gif "PortConfigurationWizard_MSMQT_Transport")</span></span>  
  
## <a name="biztalk-server-projects"></a><span data-ttu-id="de4cd-107">BizTalk Server 專案</span><span class="sxs-lookup"><span data-stu-id="de4cd-107">BizTalk Server Projects</span></span>  
 <span data-ttu-id="de4cd-108">新的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 專案不應該使用 MSMQT 傳輸選項。</span><span class="sxs-lookup"><span data-stu-id="de4cd-108">New [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] projects should not use the MSMQT transport option.</span></span> <span data-ttu-id="de4cd-109">應用程式部署至 BizTalk Server 將會失敗並出現錯誤**通訊協定類型"MSMQT"找不到**。</span><span class="sxs-lookup"><span data-stu-id="de4cd-109">Application deployment to BizTalk Server will fail with the error **Protocol type “MSMQT” not found**.</span></span>  
  
## <a name="migrated-biztalk-server-projects"></a><span data-ttu-id="de4cd-110">移轉的 BizTalk Server 專案</span><span class="sxs-lookup"><span data-stu-id="de4cd-110">Migrated BizTalk Server Projects</span></span>  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="de4cd-111">專案可以移轉至 BizTalk Server 使用[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]如中所述的轉換精靈[移轉 BizTalk Server 專案](../core/migrating-a-biztalk-server-project.md)。</span><span class="sxs-lookup"><span data-stu-id="de4cd-111"> projects can be migrated to BizTalk Server by using the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Conversion Wizard as documented in [Migrating a BizTalk Server Project](../core/migrating-a-biztalk-server-project.md).</span></span> <span data-ttu-id="de4cd-112">必須在部署至 BizTalk Server 之前手動重新設定包含通訊埠設定為使用 MSMQT 傳輸專案。</span><span class="sxs-lookup"><span data-stu-id="de4cd-112">Projects containing ports configured to use the MSMQT transport must be manually reconfigured before deployment to BizTalk Server.</span></span> <span data-ttu-id="de4cd-113">建議的重新設定是使用 MSMQ 配接器。</span><span class="sxs-lookup"><span data-stu-id="de4cd-113">The recommended reconfiguration is to use the MSMQ adapter.</span></span>  <span data-ttu-id="de4cd-114">如需 MSMQ 配接器的詳細資訊，請參閱[什麼是 MSMQ 配接器？](../core/what-is-the-msmq-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="de4cd-114">For more information about the MSMQ adapter see [What Is the MSMQ Adapter?](../core/what-is-the-msmq-adapter.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de4cd-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="de4cd-115">See Also</span></span>  
 [<span data-ttu-id="de4cd-116">從 MSMQT 配接器移轉至 MSMQ 配接器</span><span class="sxs-lookup"><span data-stu-id="de4cd-116">Migrating from the MSMQT Adapter to the MSMQ Adapter</span></span>](../core/migrating-from-the-msmqt-adapter-to-the-msmq-adapter.md)