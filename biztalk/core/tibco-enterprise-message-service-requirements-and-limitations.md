---
title: TIBCO Enterprise Message Service 需求和限制 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6e4c022c-e6a8-4ac5-b998-b0465002a31e
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 453edabdadbd50b320a0bc078a638991ab7a3a5c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36995983"
---
# <a name="tibco-enterprise-message-service-requirements-and-limitations"></a><span data-ttu-id="2f821-102">TIBCO Enterprise Message Service 的需求和限制</span><span class="sxs-lookup"><span data-stu-id="2f821-102">TIBCO Enterprise Message Service Requirements and Limitations</span></span>

## <a name="system-requirements"></a><span data-ttu-id="2f821-103">系統需求</span><span class="sxs-lookup"><span data-stu-id="2f821-103">System Requirements</span></span>  
<span data-ttu-id="2f821-104">隨附 TIBCO Enterprise Message Service 包含的用戶端 SDK （使用 TIBCO EMS C# API）。</span><span class="sxs-lookup"><span data-stu-id="2f821-104">Included with TIBCO Enterprise Message Service includes a client SDK (using the TIBCO EMS C# API).</span></span> <span data-ttu-id="2f821-105">BizTalk Adapter for TIBCO EMS 會使用此 API 來與 TIBCO EMS 進行通訊。</span><span class="sxs-lookup"><span data-stu-id="2f821-105">BizTalk Adapter for TIBCO EMS uses this API to communicate with TIBCO EMS.</span></span>  
  
## <a name="add-the-api-to-the-gac"></a><span data-ttu-id="2f821-106">將 API 加入 GAC</span><span class="sxs-lookup"><span data-stu-id="2f821-106">Add the API to the GAC</span></span>  
 <span data-ttu-id="2f821-107">BizTalk Adapter for TIBCO EMS 需要 TIBCO EMS C# API，TIBCO。EMS.dll，可以加入至全域組件快取 (GAC)。</span><span class="sxs-lookup"><span data-stu-id="2f821-107">BizTalk Adapter for TIBCO EMS requires the TIBCO EMS C# API, TIBCO.EMS.dll, to be added to the global assembly cache (GAC).</span></span> <span data-ttu-id="2f821-108">配接器會觸發例外狀況，並記錄適當的訊息，如果未安裝此組件。</span><span class="sxs-lookup"><span data-stu-id="2f821-108">The adapter triggers an exception and logs an appropriate message if this assembly is not installed.</span></span>  
  
1. <span data-ttu-id="2f821-109">複製至 TIBCO EMS C #API 您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦。</span><span class="sxs-lookup"><span data-stu-id="2f821-109">Copy the TIBCO EMS C#API to your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer.</span></span>  
  
2. <span data-ttu-id="2f821-110">將目錄變更至 TIBCO 的 C# API 檔案的位置。EMS。DLL。</span><span class="sxs-lookup"><span data-stu-id="2f821-110">Change directories to the location of the C# API file, TIBCO.EMS.DLL.</span></span>  
  
    <span data-ttu-id="2f821-111">在預設安裝中，此 DLL 的路徑會是 c:\tibco\ems\clients\cs\TIBCO。EMS。DLL。</span><span class="sxs-lookup"><span data-stu-id="2f821-111">In the default installation, the path to this DLL is c:\tibco\ems\clients\cs\TIBCO.EMS.DLL.</span></span>  
  
3. <span data-ttu-id="2f821-112">在命令提示字元中，輸入：</span><span class="sxs-lookup"><span data-stu-id="2f821-112">In a command prompt, type:</span></span>  
  
    `C:\bin> gacutil /i TIBCO.EMS.dll`  
  
    <span data-ttu-id="2f821-113">TIBCO。EMS.dll 現在會顯示 GAC。</span><span class="sxs-lookup"><span data-stu-id="2f821-113">The TIBCO.EMS.dll now shows the GAC.</span></span>  
  
    <span data-ttu-id="2f821-114">若要檢視 GAC 清單中，在控制台中，開啟**系統管理工具**，開啟**Microsoft.NET Framework X.XConfiguration**，然後按一下**組件快取**。</span><span class="sxs-lookup"><span data-stu-id="2f821-114">To view the GAC list, in Control Panel, open **Administrative Tools**, open **Microsoft .NET Framework X.XConfiguration**, and then click **Assembly Cache**.</span></span>  
  
## <a name="limitations"></a><span data-ttu-id="2f821-115">限制</span><span class="sxs-lookup"><span data-stu-id="2f821-115">Limitations</span></span>  
 <span data-ttu-id="2f821-116">BizTalk Adapter for TIBCO Enterprise Message Service 會使用 TIBCO。EMS.dll 與 TIBCO Enterprise Message Service 進行通訊。</span><span class="sxs-lookup"><span data-stu-id="2f821-116">BizTalk Adapter for TIBCO Enterprise Message Service uses TIBCO.EMS.dll to communicate with TIBCO Enterprise Message Service.</span></span> <span data-ttu-id="2f821-117">當您使用 TIBCO EMS C# API 時，您應該考慮下列限制：</span><span class="sxs-lookup"><span data-stu-id="2f821-117">You should consider the following limitations when you use the TIBCO EMS C# API:</span></span>  
  
-   <span data-ttu-id="2f821-118">訊息壓縮功能，可讓 TIBCO EMS 用戶端，以壓縮格式的訊息傳送給 EMS，不適用於 C# API。</span><span class="sxs-lookup"><span data-stu-id="2f821-118">Message compression, which enables the TIBCO EMS client to send messages in a compressed form to EMS, is not available with the C# API.</span></span>  
  
-   <span data-ttu-id="2f821-119">配接器和伺服器之間的訊息加密不提供使用 C# API。</span><span class="sxs-lookup"><span data-stu-id="2f821-119">Encryption of messages between the adapter and the server is not available with the C# API.</span></span> <span data-ttu-id="2f821-120">C# API 不允許進行 SSL 加密，使用 OpenSSL 程式庫。</span><span class="sxs-lookup"><span data-stu-id="2f821-120">The C# API does not allow for SSL encryption using the OpenSSL libraries.</span></span>  
  
-   <span data-ttu-id="2f821-121">C# API 不支援適用於 EMS 的系統管理 API。</span><span class="sxs-lookup"><span data-stu-id="2f821-121">The C# API does not support the Administration API for EMS.</span></span>  
  
-   <span data-ttu-id="2f821-122">無法傳送訊息大於 50 MB 的大小，或使用 BizTalk TIBCO EMS 配接器接收。</span><span class="sxs-lookup"><span data-stu-id="2f821-122">Messages greater than 50MB in size cannot be sent or received using the BizTalk TIBCO EMS adapter.</span></span> <span data-ttu-id="2f821-123">超過此大小，環境會體驗 System.OutOfMemoryException 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="2f821-123">Beyond this size, the environment experiences System.OutOfMemoryException exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f821-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2f821-124">See Also</span></span>  
 [<span data-ttu-id="2f821-125">規劃和架構</span><span class="sxs-lookup"><span data-stu-id="2f821-125">Planning and Architecture</span></span>](../core/planning-and-architecture16.md)