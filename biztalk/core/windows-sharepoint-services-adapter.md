---
title: Windows SharePoint Services 配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Windows SharePoint Services adapters
ms.assetid: cbfc9bf3-912d-4849-ba8c-07a116888bbd
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5a6f1365b11ce93717223ec35e395165e8d0e551
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22289878"
---
# <a name="windows-sharepoint-services-adapter"></a><span data-ttu-id="f82c2-102">Windows SharePoint Services 配接器</span><span class="sxs-lookup"><span data-stu-id="f82c2-102">Windows SharePoint Services Adapter</span></span>
<span data-ttu-id="f82c2-103">Microsoft Windows SharePoint Services 的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 配接器為 BizTalk Server 與 Windows SharePoint Services 和 Microsoft Office 提供更緊密的整合。</span><span class="sxs-lookup"><span data-stu-id="f82c2-103">The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] adapter for Microsoft Windows SharePoint Services provides a tighter integration of BizTalk Server with Windows SharePoint Services and Microsoft Office.</span></span> <span data-ttu-id="f82c2-104">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 解決方案中使用 Windows SharePoint Services 配接器，可提供您下列功能：</span><span class="sxs-lookup"><span data-stu-id="f82c2-104">Using the Windows SharePoint Services adapter in your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solution provides you with the following capabilities:</span></span>  
  
-   <span data-ttu-id="f82c2-105">透過 Windows SharePoint Services 輕鬆存取輸入和輸出訊息。</span><span class="sxs-lookup"><span data-stu-id="f82c2-105">Easy access to input and output messages through Windows SharePoint Services.</span></span>  
  
-   <span data-ttu-id="f82c2-106">使用 Microsoft Office InfoPath 等 Office 應用程式來編輯 XML 訊息的功能。</span><span class="sxs-lookup"><span data-stu-id="f82c2-106">The ability to edit XML messages by using Office applications such as Microsoft Office InfoPath.</span></span>  
  
-   <span data-ttu-id="f82c2-107">在 XML 訊息與 InfoPath 間進行雙向轉換。</span><span class="sxs-lookup"><span data-stu-id="f82c2-107">Two-way transformations of XML messages to and from InfoPath.</span></span>  
  
 <span data-ttu-id="f82c2-108">[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] 配接器包含下列元件：</span><span class="sxs-lookup"><span data-stu-id="f82c2-108">The [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] adapter consists of the following components:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f82c2-109">CSOM[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)]配接器</span><span class="sxs-lookup"><span data-stu-id="f82c2-109">CSOM [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] Adapter</span></span>|<span data-ttu-id="f82c2-110">使用 [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] Client Side Object Model (CSOM)。</span><span class="sxs-lookup"><span data-stu-id="f82c2-110">Uses the [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] Client Side Object Model (CSOM).</span></span> <span data-ttu-id="f82c2-111">此配接器會在安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 時一併安裝。</span><span class="sxs-lookup"><span data-stu-id="f82c2-111">The adapter is installed when [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed.</span></span> <span data-ttu-id="f82c2-112">不需執行其他安裝步驟。</span><span class="sxs-lookup"><span data-stu-id="f82c2-112">There are no additional installation steps.</span></span><br /><br /> <span data-ttu-id="f82c2-113">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝***自動***安裝 SharePoint 用戶端物件模型可轉散發套件，這也是位於[http://go.microsoft.com/fwlink/p/?LinkId=263482](http://go.microsoft.com/fwlink/p/?LinkId=263482)。</span><span class="sxs-lookup"><span data-stu-id="f82c2-113">The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation ***automatically*** installs the SharePoint Client Object Model Redistributable, which is also available at [http://go.microsoft.com/fwlink/p/?LinkId=263482](http://go.microsoft.com/fwlink/p/?LinkId=263482).</span></span>|  
|<span data-ttu-id="f82c2-114">SSOM [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] Web 服務</span><span class="sxs-lookup"><span data-stu-id="f82c2-114">SSOM [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] Web Service</span></span>|<span data-ttu-id="f82c2-115">**已取代**。</span><span class="sxs-lookup"><span data-stu-id="f82c2-115">**Deprecated**.</span></span> <span data-ttu-id="f82c2-116">使用 [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] Service Side Object Model (SSOM)。</span><span class="sxs-lookup"><span data-stu-id="f82c2-116">Uses the [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] Service Side Object Model (SSOM).</span></span><br /><br /> <span data-ttu-id="f82c2-117">此 Web 服務安裝於 [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] 電腦上，可以在與 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 相同的電腦或個別電腦上。</span><span class="sxs-lookup"><span data-stu-id="f82c2-117">The web service is installed on the [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] computer, which can be on the same computer as [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] or a separate computer.</span></span><br /><br /> <span data-ttu-id="f82c2-118">若要安裝 web 服務，請執行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]上的安裝[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)]電腦並檢查**Windows SharePoint Services 配接器**。</span><span class="sxs-lookup"><span data-stu-id="f82c2-118">To install the web service, run the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation on the [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] computer and check **Windows SharePoint Services Adapter**.</span></span>|  
  
 <span data-ttu-id="f82c2-119">[附錄 b： 安裝 Microsoft SharePoint 配接器](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md)提供更多有關[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)]安裝。</span><span class="sxs-lookup"><span data-stu-id="f82c2-119">[Appendix B: Install the Microsoft SharePoint Adapter](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md) provides more information on the [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] installation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f82c2-120">目前不支援同盟驗證。</span><span class="sxs-lookup"><span data-stu-id="f82c2-120">Currently, federated authentication is not supported.</span></span> <span data-ttu-id="f82c2-121">只支援使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="f82c2-121">Only Username and Password are supported.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f82c2-122">本節內容</span><span class="sxs-lookup"><span data-stu-id="f82c2-122">In This Section</span></span>  
  
-   [<span data-ttu-id="f82c2-123">CSOM: SharePoint Services 配接器</span><span class="sxs-lookup"><span data-stu-id="f82c2-123">CSOM: SharePoint Services Adapter</span></span>](../core/csom-sharepoint-services-adapter.md)  
  
-   [<span data-ttu-id="f82c2-124">SSOM: SharePoint Services 配接器 Web 服務</span><span class="sxs-lookup"><span data-stu-id="f82c2-124">SSOM: SharePoint Services Adapter Web Service</span></span>](../core/ssom-sharepoint-services-adapter-web-service.md)  
  
## <a name="see-also"></a><span data-ttu-id="f82c2-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f82c2-125">See Also</span></span>  
 <span data-ttu-id="f82c2-126">[使用配接器](../core/using-adapters.md) </span><span class="sxs-lookup"><span data-stu-id="f82c2-126">[Using Adapters](../core/using-adapters.md) </span></span>  
 [<span data-ttu-id="f82c2-127">開發 BizTalk Server 應用程式</span><span class="sxs-lookup"><span data-stu-id="f82c2-127">Developing BizTalk Server Applications</span></span>](../core/developing-biztalk-server-applications.md)