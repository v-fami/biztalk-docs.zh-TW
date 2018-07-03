---
title: 將 Oracle 資料庫配接器新增至 BizTalk Server 管理主控台 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8d71e161-addc-47d4-9103-3655f3fb0b0d
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 95ef6f3c4f33ddfdb6dbaca3e1823149ede66abf
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36997871"
---
# <a name="adding-the-oracle-database-adapter-to-biztalk-server-administration-console"></a><span data-ttu-id="bab96-102">將 Oracle 資料庫配接器新增至 BizTalk Server 管理主控台</span><span class="sxs-lookup"><span data-stu-id="bab96-102">Adding the Oracle Database Adapter to BizTalk Server Administration Console</span></span>
<span data-ttu-id="bab96-103">本主題說明如何新增 Wcf-oracledb 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="bab96-103">This topic provides instructions on how to add the WCF-OracleDB adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="bab96-104">您不需要執行這些工作，如果您想要設定 WCF 自訂連接埠[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="bab96-104">You need not perform these tasks if you want to configure a WCF-Custom port for the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span>  
  
## <a name="add-the-oracle-database-adapter"></a><span data-ttu-id="bab96-105">將 Oracle 資料庫配接器</span><span class="sxs-lookup"><span data-stu-id="bab96-105">Add the Oracle Database Adapter</span></span>  
  
1. <span data-ttu-id="bab96-106">開啟[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="bab96-106">Open the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2. <span data-ttu-id="bab96-107">依序展開**BizTalk 群組**，展開**平台設定**，然後選取**配接器**。</span><span class="sxs-lookup"><span data-stu-id="bab96-107">Expand the **BizTalk Group**, expand **Platform Settings**, and then select **Adapters**.</span></span>  
  
3. <span data-ttu-id="bab96-108">以滑鼠右鍵按一下**配接器**，選取**新增**，然後選取**配接器**。</span><span class="sxs-lookup"><span data-stu-id="bab96-108">Right-click **Adapters**, select **New**, and select **Adapter**.</span></span>  
  
    <span data-ttu-id="bab96-109">![新增配接器](../../adapters-and-accelerators/media/c9610d42-8465-4099-b403-87df6dcd0d99.gif "c9610d42-8465-4099-b403-87df6dcd0d99")</span><span class="sxs-lookup"><span data-stu-id="bab96-109">![Add an adapter](../../adapters-and-accelerators/media/c9610d42-8465-4099-b403-87df6dcd0d99.gif "c9610d42-8465-4099-b403-87df6dcd0d99")</span></span>  
  
4. <span data-ttu-id="bab96-110">在 **配接器屬性**對話方塊方塊中，輸入名稱，配接器，並從**配接器**清單中，選取**Wcf-oracledb**。</span><span class="sxs-lookup"><span data-stu-id="bab96-110">In the **Adapter Properties** dialog box, enter a name for the adapter and from the **Adapter** list, select **WCF-OracleDB**.</span></span>  
  
    <span data-ttu-id="bab96-111">![新增 WCF&#45;OracleDB 配接器至 BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/media/wcf-oracledb.gif "WCF_OracleDB")</span><span class="sxs-lookup"><span data-stu-id="bab96-111">![Adding WCF&#45;OracleDB adapter to BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/media/wcf-oracledb.gif "WCF_OracleDB")</span></span>  
  
5. <span data-ttu-id="bab96-112">選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="bab96-112">Select **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bab96-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bab96-113">See Also</span></span>  
[<span data-ttu-id="bab96-114">若要開發與 Oracle 資料庫的 BizTalk 應用程式的建置組塊</span><span class="sxs-lookup"><span data-stu-id="bab96-114">Building Blocks to develop BizTalk Applications with Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md)