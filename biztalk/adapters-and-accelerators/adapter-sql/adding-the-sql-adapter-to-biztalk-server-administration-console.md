---
title: 將 SQL 配接器新增至 BizTalk Server 管理主控台 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd974f28-c9cb-46de-95be-83716231ebcd
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ff3eb1aa8870316ec506a61658c34db6acc7f62c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37005727"
---
# <a name="adding-the-sql-adapter-to-biztalk-server-administration-console"></a><span data-ttu-id="c0568-102">將 SQL 配接器新增至 BizTalk Server 管理主控台</span><span class="sxs-lookup"><span data-stu-id="c0568-102">Adding the SQL Adapter to BizTalk Server Administration Console</span></span>
<span data-ttu-id="c0568-103">[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]可用於 BizTalk 做為 WCF 自訂連接埠或 WCF SQL 連接埠。</span><span class="sxs-lookup"><span data-stu-id="c0568-103">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] can be used in BizTalk either as a WCF-Custom port or a WCF-SQL port.</span></span> <span data-ttu-id="c0568-104">如果您想要使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]透過 WCF 自訂連接埠，您不需要新增的 WCF 自訂連接埠[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台，因為 WCF 自訂連接埠新增至[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中的，預設值。</span><span class="sxs-lookup"><span data-stu-id="c0568-104">If you want to use the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] through a WCF-Custom port, you do not need to add the WCF-Custom port to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console because the WCF-Custom port is added to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console by default.</span></span> <span data-ttu-id="c0568-105">不過，如果您想要使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]透過 WCF SQL 連接埠，您必須先新增 WCF-SQL 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="c0568-105">However, if you want to use the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] through a WCF-SQL port, you must first add the WCF-SQL adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
 <span data-ttu-id="c0568-106">本主題說明如何新增 WCF-SQL 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="c0568-106">This topic shows you how to add the WCF-SQL adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c0568-107">您不需要請遵循下列步驟，如果您想要設定 WCF 自訂連接埠[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c0568-107">You do not need to follow these steps if you want to configure a WCF-Custom port for the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
## <a name="add-the-sql-adapter"></a><span data-ttu-id="c0568-108">新增 SQL 配接器</span><span class="sxs-lookup"><span data-stu-id="c0568-108">Add the SQL Adapter</span></span>  
  
1. <span data-ttu-id="c0568-109">開啟[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="c0568-109">Open the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2. <span data-ttu-id="c0568-110">依序展開**BizTalk 群組**，展開**平台設定**，然後選取**配接器**。</span><span class="sxs-lookup"><span data-stu-id="c0568-110">Expand the **BizTalk Group**, expand **Platform Settings**, and then select **Adapters**.</span></span>  
  
3. <span data-ttu-id="c0568-111">以滑鼠右鍵按一下**配接器**，指向**新增**，然後選取**配接器**。</span><span class="sxs-lookup"><span data-stu-id="c0568-111">Right-click **Adapters**, point to **New**, and select **Adapter**.</span></span>  
  
    <span data-ttu-id="c0568-112">![新增配接器](../../adapters-and-accelerators/media/c9610d42-8465-4099-b403-87df6dcd0d99.gif "c9610d42-8465-4099-b403-87df6dcd0d99")</span><span class="sxs-lookup"><span data-stu-id="c0568-112">![Add an adapter](../../adapters-and-accelerators/media/c9610d42-8465-4099-b403-87df6dcd0d99.gif "c9610d42-8465-4099-b403-87df6dcd0d99")</span></span>  
  
4. <span data-ttu-id="c0568-113">在 **配接器屬性**對話方塊中，輸入名稱，該介面卡，然後從**配接器**清單中，選取**WCF-SQL**。</span><span class="sxs-lookup"><span data-stu-id="c0568-113">In the **Adapter Properties** dialog box, enter a name for the adapter, and from the **Adapter** list, select **WCF-SQL**.</span></span>  
  
    <span data-ttu-id="c0568-114">![新增 WCF&#45;SQL 配接器至 BizTalk](../../adapters-and-accelerators/adapter-sql/media/4c6e2650-5d3a-4de8-a60a-a136d93a6fcf.gif "4c6e2650-5d3a-4de8-a60a-a136d93a6fcf")</span><span class="sxs-lookup"><span data-stu-id="c0568-114">![Add WCF&#45;SQL adapter to BizTalk](../../adapters-and-accelerators/adapter-sql/media/4c6e2650-5d3a-4de8-a60a-a136d93a6fcf.gif "4c6e2650-5d3a-4de8-a60a-a136d93a6fcf")</span></span>  
  
5. <span data-ttu-id="c0568-115">選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="c0568-115">Select **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0568-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0568-116">See Also</span></span>  
 [<span data-ttu-id="c0568-117">若要開發使用 SQL 配接器的 BizTalk 應用程式的建置組塊</span><span class="sxs-lookup"><span data-stu-id="c0568-117">Building blocks to develop BizTalk applications with the SQL adapter</span></span>](../../adapters-and-accelerators/adapter-sql/building-blocks-to-develop-biztalk-applications-with-the-sql-adapter.md)