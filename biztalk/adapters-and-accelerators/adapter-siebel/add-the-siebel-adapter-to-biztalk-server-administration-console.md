---
title: Siebel 配接器加入 BizTalk Server 管理主控台 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b64d0bdc-ac83-46c9-b27d-625088a013d3
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1f8c30567849a0342432cb53e0c2de7959c175c8
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36967423"
---
# <a name="add-the-siebel-adapter-to-biztalk-server-administration-console"></a><span data-ttu-id="02a70-102">Siebel 配接器加入 BizTalk Server 管理主控台</span><span class="sxs-lookup"><span data-stu-id="02a70-102">Add the Siebel Adapter to BizTalk Server Administration Console</span></span>
<span data-ttu-id="02a70-103">[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]可用於 BizTalk 做為 WCF 自訂連接埠或 Wcf-siebel 連接埠。</span><span class="sxs-lookup"><span data-stu-id="02a70-103">The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] can be used in BizTalk either as a WCF-Custom port or a WCF-Siebel port.</span></span> <span data-ttu-id="02a70-104">如果您想要使用[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]透過 WCF 自訂連接埠，您不需要新增的 WCF 自訂連接埠[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台，因為 WCF 自訂連接埠新增至[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中的，預設值。</span><span class="sxs-lookup"><span data-stu-id="02a70-104">If you want to use the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] through a WCF-Custom port, you do not need to add the WCF-Custom port to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console because the WCF-Custom port is added to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console by default.</span></span> <span data-ttu-id="02a70-105">不過，如果您想要使用[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]透過 Wcf-siebel 連接埠，您必須先新增 Wcf-siebel 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="02a70-105">However, if you want to use the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] through a WCF-Siebel port, you must first add the WCF-Siebel adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
 <span data-ttu-id="02a70-106">本主題說明如何新增 Wcf-siebel 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="02a70-106">This topic provides instructions on how to add the WCF-Siebel adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="02a70-107">您不需要執行這些工作，如果您想要設定 WCF 自訂連接埠[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="02a70-107">You need not perform these tasks if you want to configure a WCF-Custom port for the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span></span>  
  
## <a name="add-the-siebel-adapter"></a><span data-ttu-id="02a70-108">新增 Siebel 配接器</span><span class="sxs-lookup"><span data-stu-id="02a70-108">Add the Siebel adapter</span></span>  
  
1. <span data-ttu-id="02a70-109">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="02a70-109">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2. <span data-ttu-id="02a70-110">在主控台樹狀目錄中，依序展開**BizTalk 群組**，展開**平台設定**，然後按一下**配接器**。</span><span class="sxs-lookup"><span data-stu-id="02a70-110">In the console tree, expand the **BizTalk Group**, expand **Platform Settings**, and then click **Adapters**.</span></span>  
  
3. <span data-ttu-id="02a70-111">以滑鼠右鍵按一下**配接器**，指向**新增**，然後按一下**配接器**。</span><span class="sxs-lookup"><span data-stu-id="02a70-111">Right-click **Adapters**, point to **New**, and click **Adapter**.</span></span>  
  
    <span data-ttu-id="02a70-112">![新增配接器](../../adapters-and-accelerators/media/c9610d42-8465-4099-b403-87df6dcd0d99.gif "c9610d42-8465-4099-b403-87df6dcd0d99")</span><span class="sxs-lookup"><span data-stu-id="02a70-112">![Add an adapter](../../adapters-and-accelerators/media/c9610d42-8465-4099-b403-87df6dcd0d99.gif "c9610d42-8465-4099-b403-87df6dcd0d99")</span></span>  
  
4. <span data-ttu-id="02a70-113">在 **配接器屬性**對話方塊方塊中，指定的名稱，配接器，並從**配接器**清單中，選取**Wcf-siebel**。</span><span class="sxs-lookup"><span data-stu-id="02a70-113">In the **Adapter Properties** dialog box, specify a name for the adapter and from the **Adapter** list, select **WCF-Siebel**.</span></span>  
  
    <span data-ttu-id="02a70-114">![新增 WCF&#45;Siebel 配接器至 BizTalk 主控台](../../adapters-and-accelerators/adapter-siebel/media/6d39b874-2233-452a-81ef-d93274b0784c.gif "6d39b874-2233-452a-81ef-d93274b0784c")</span><span class="sxs-lookup"><span data-stu-id="02a70-114">![Add WCF&#45;Siebel adapter to BizTalk console](../../adapters-and-accelerators/adapter-siebel/media/6d39b874-2233-452a-81ef-d93274b0784c.gif "6d39b874-2233-452a-81ef-d93274b0784c")</span></span>  
  
5. <span data-ttu-id="02a70-115">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="02a70-115">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02a70-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="02a70-116">See Also</span></span>  
[<span data-ttu-id="02a70-117">若要建立與 Siebel 配接器的 BizTalk 應用程式的建置組塊</span><span class="sxs-lookup"><span data-stu-id="02a70-117">Building blocks to create BizTalk applications with the Siebel adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/building-blocks-to-create-biztalk-applications-with-the-siebel-adapter.md)