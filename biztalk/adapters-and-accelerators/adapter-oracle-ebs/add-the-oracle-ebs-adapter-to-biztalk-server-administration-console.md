---
title: 將 Oracle E-business Suite 配接器新增至 BizTalk Server 管理主控台 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 24b126aa-2a05-49fa-80e1-f1d5c21ad60f
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 77d7bbc13857f51a9bc4072c2f8a02407a5da2ec
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36977255"
---
# <a name="add-the-oracle-e-business-suite-adapter-to-biztalk-server-administration-console"></a><span data-ttu-id="5f044-102">將 Oracle E-business Suite 配接器新增至 BizTalk Server 管理主控台</span><span class="sxs-lookup"><span data-stu-id="5f044-102">Add the Oracle E-Business Suite adapter to BizTalk Server Administration console</span></span>
<span data-ttu-id="5f044-103">[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]可用於 BizTalk Server 可做為 WCF 自訂連接埠或 Wcf-oracleebs 連接埠。</span><span class="sxs-lookup"><span data-stu-id="5f044-103">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] can be used in BizTalk Server either as a WCF-Custom port or a WCF-OracleEBS port.</span></span> <span data-ttu-id="5f044-104">如果您想要使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]透過 WCF 自訂連接埠，您不需要新增的 WCF 自訂連接埠[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台，因為 WCF 自訂連接埠新增至[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中的，預設值。</span><span class="sxs-lookup"><span data-stu-id="5f044-104">If you want to use the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] through a WCF-Custom port, you do not need to add the WCF-Custom port to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console because the WCF-Custom port is added to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console by default.</span></span> <span data-ttu-id="5f044-105">不過，如果您想要使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]透過 Wcf-oracleebs 連接埠，您必須先新增 Wcf-oracleebs 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="5f044-105">However, if you want to use the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] through a WCF-OracleEBS port, you must first add the WCF-OracleEBS adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
 <span data-ttu-id="5f044-106">本主題說明如何新增 Wcf-oracleebs 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="5f044-106">This topic provides instructions on how to add the WCF-OracleEBS adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5f044-107">如果您想要設定 WCF 自訂連接埠[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，您不需要執行此程序。</span><span class="sxs-lookup"><span data-stu-id="5f044-107">If you want to configure a WCF-Custom port for the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], you need not perform this procedure.</span></span>  
  
### <a name="to-add-the-oracle-e-business-suite-adapter"></a><span data-ttu-id="5f044-108">若要新增 Oracle E-business Suite 配接器</span><span class="sxs-lookup"><span data-stu-id="5f044-108">To add the Oracle E-Business Suite Adapter</span></span>  
  
1. <span data-ttu-id="5f044-109">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="5f044-109">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2. <span data-ttu-id="5f044-110">在主控台樹狀目錄中，依序展開**BizTalk 群組**，展開**平台設定**，然後按一下**配接器**。</span><span class="sxs-lookup"><span data-stu-id="5f044-110">In the console tree, expand the **BizTalk Group**, expand **Platform Settings**, and then click **Adapters**.</span></span>  
  
3. <span data-ttu-id="5f044-111">以滑鼠右鍵按一下**配接器**，指向**新增**，然後按一下**配接器**。</span><span class="sxs-lookup"><span data-stu-id="5f044-111">Right-click **Adapters**, point to **New**, and click **Adapter**.</span></span>  
  
    <span data-ttu-id="5f044-112">![新增配接器](../../adapters-and-accelerators/media/c9610d42-8465-4099-b403-87df6dcd0d99.gif "c9610d42-8465-4099-b403-87df6dcd0d99")</span><span class="sxs-lookup"><span data-stu-id="5f044-112">![Add an adapter](../../adapters-and-accelerators/media/c9610d42-8465-4099-b403-87df6dcd0d99.gif "c9610d42-8465-4099-b403-87df6dcd0d99")</span></span>  
  
4. <span data-ttu-id="5f044-113">在 **配接器屬性**對話方塊方塊中，指定的名稱，配接器，並從**配接器**清單中，選取**Wcf-oracleebs**。</span><span class="sxs-lookup"><span data-stu-id="5f044-113">In the **Adapter Properties** dialog box, specify a name for the adapter and from the **Adapter** list, select **WCF-OracleEBS**.</span></span>  
  
    <span data-ttu-id="5f044-114">![新增 WCF&#45;OracleEBS 配接器至 BizTalk](../../adapters-and-accelerators/adapter-oracle-ebs/media/3e2cde5a-9f32-489c-a931-0dd509451e62.gif "3e2cde5a-9f32-489c-a931-0dd509451e62")</span><span class="sxs-lookup"><span data-stu-id="5f044-114">![Add WCF&#45;OracleEBS adapter to BizTalk](../../adapters-and-accelerators/adapter-oracle-ebs/media/3e2cde5a-9f32-489c-a931-0dd509451e62.gif "3e2cde5a-9f32-489c-a931-0dd509451e62")</span></span>  
  
5. <span data-ttu-id="5f044-115">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="5f044-115">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f044-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f044-116">See Also</span></span>  
 [<span data-ttu-id="5f044-117">若要建立 Oracle E-business Suite 應用程式的建置組塊</span><span class="sxs-lookup"><span data-stu-id="5f044-117">Building blocks to create Oracle E-Business Suite applications</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/building-blocks-to-create-oracle-e-business-suite-applications.md)