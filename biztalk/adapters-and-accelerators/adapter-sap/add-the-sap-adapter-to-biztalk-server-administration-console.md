---
title: 將 SAP 配接器新增至 BizTalk Server 管理主控台 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 95fc925d-0aac-4f0d-a19d-ad27469e4b3c
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6a8913e982a94a2b850bae1aab668f9672e86fe8
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36986623"
---
# <a name="add-the-sap-adapter-to-biztalk-server-administration-console"></a><span data-ttu-id="1709f-102">將 SAP 配接器新增至 BizTalk Server 管理主控台</span><span class="sxs-lookup"><span data-stu-id="1709f-102">Add the SAP Adapter to BizTalk Server Administration Console</span></span>
<span data-ttu-id="1709f-103">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]可用於 BizTalk 做為 WCF 自訂連接埠或 WCF SAP 連接埠。</span><span class="sxs-lookup"><span data-stu-id="1709f-103">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] can be used in BizTalk either as a WCF-Custom port or a WCF-SAP port.</span></span> <span data-ttu-id="1709f-104">如果您想要使用[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]透過 WCF 自訂連接埠，您不需要新增的 WCF 自訂連接埠[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台，因為 WCF 自訂連接埠新增至[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中的，預設值。</span><span class="sxs-lookup"><span data-stu-id="1709f-104">If you want to use the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] through a WCF-Custom port, you do not need to add the WCF-Custom port to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console because the WCF-Custom port is added to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console by default.</span></span> <span data-ttu-id="1709f-105">不過，如果您想要使用[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]透過 WCF SAP 連接埠，您必須先新增 WCF SAP 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="1709f-105">However, if you want to use the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] through a WCF-SAP port, you must first add the WCF-SAP adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
 <span data-ttu-id="1709f-106">本主題說明如何將 WCF SAP 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="1709f-106">This topic provides instructions on how to add the WCF-SAP adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1709f-107">您不需要執行這些工作，如果您想要設定 WCF 自訂連接埠[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="1709f-107">You need not perform these tasks if you want to configure a WCF-Custom port for the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
## <a name="add-the-sap-adapter"></a><span data-ttu-id="1709f-108">新增 SAP 配接器</span><span class="sxs-lookup"><span data-stu-id="1709f-108">Add the SAP Adapter</span></span>  
  
1. <span data-ttu-id="1709f-109">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="1709f-109">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2. <span data-ttu-id="1709f-110">在主控台樹狀目錄中，依序展開**BizTalk 群組**，展開**平台設定**，然後按一下**配接器**。</span><span class="sxs-lookup"><span data-stu-id="1709f-110">In the console tree, expand the **BizTalk Group**, expand **Platform Settings**, and then click **Adapters**.</span></span>  
  
3. <span data-ttu-id="1709f-111">以滑鼠右鍵按一下**配接器**，指向**新增**，然後按一下**配接器**。</span><span class="sxs-lookup"><span data-stu-id="1709f-111">Right-click **Adapters**, point to **New**, and click **Adapter**.</span></span>  
  
    <span data-ttu-id="1709f-112">![新增配接器](../../adapters-and-accelerators/media/c9610d42-8465-4099-b403-87df6dcd0d99.gif "c9610d42-8465-4099-b403-87df6dcd0d99")</span><span class="sxs-lookup"><span data-stu-id="1709f-112">![Add an adapter](../../adapters-and-accelerators/media/c9610d42-8465-4099-b403-87df6dcd0d99.gif "c9610d42-8465-4099-b403-87df6dcd0d99")</span></span>  
  
4. <span data-ttu-id="1709f-113">在 **配接器屬性**對話方塊方塊中，指定的名稱，配接器，並從**配接器**清單中，選取**WCF-SAP**。</span><span class="sxs-lookup"><span data-stu-id="1709f-113">In the **Adapter Properties** dialog box, specify a name for the adapter and from the **Adapter** list, select **WCF-SAP**.</span></span>  
  
    <span data-ttu-id="1709f-114">![新增 SAP 配接器至 BizTalk](../../adapters-and-accelerators/media/a1235b38-ab93-4233-924d-42710540b951.gif "a1235b38-ab93-4233-924d-42710540b951")</span><span class="sxs-lookup"><span data-stu-id="1709f-114">![Add SAP Adapter to BizTalk](../../adapters-and-accelerators/media/a1235b38-ab93-4233-924d-42710540b951.gif "a1235b38-ab93-4233-924d-42710540b951")</span></span>  
  
5. <span data-ttu-id="1709f-115">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="1709f-115">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1709f-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1709f-116">See Also</span></span>  
[<span data-ttu-id="1709f-117">建立 SAP 應用程式的建構元素</span><span class="sxs-lookup"><span data-stu-id="1709f-117">Building blocks to create SAP applications</span></span>](../../adapters-and-accelerators/adapter-sap/building-blocks-to-create-sap-applications.md)