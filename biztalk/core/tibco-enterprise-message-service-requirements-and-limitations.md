---
title: "TIBCO Enterprise Message Service 的需求和限制 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- encryption
- messages, compression
- EMS limitations
- message compression
- API, adding to GAC
- global assembly cache, adding API
- GAC, adding TIBCO EMS API
- system requirements
- TIBCO.EMS.dll
- EMS requirements
- messages, encryption
ms.assetid: 6e4c022c-e6a8-4ac5-b998-b0465002a31e
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 81e49f4a74cce4414fd9d0b069a382d9facb03d0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="tibco-enterprise-message-service-requirements-and-limitations"></a><span data-ttu-id="de8d7-102">TIBCO Enterprise Message Service 的需求和限制</span><span class="sxs-lookup"><span data-stu-id="de8d7-102">TIBCO Enterprise Message Service Requirements and Limitations</span></span>
## <a name="system-requirements"></a><span data-ttu-id="de8d7-103">系統需求</span><span class="sxs-lookup"><span data-stu-id="de8d7-103">System Requirements</span></span>  
 <span data-ttu-id="de8d7-104">Microsoft BizTalk Adapter for TIBCO Enterprise Message Service 支援 TIBCO Enterprise Message Service (EMS) 4.2 版。</span><span class="sxs-lookup"><span data-stu-id="de8d7-104">Microsoft BizTalk Adapter for TIBCO Enterprise Message Service supports TIBCO Enterprise Message Service (EMS) version 4.2.</span></span> <span data-ttu-id="de8d7-105">包含與 TIBCO EMS 4.2 版是用戶端 SDK （使用 TIBCO EMS C# API）。</span><span class="sxs-lookup"><span data-stu-id="de8d7-105">Included with TIBCO EMS version 4.2 is a client SDK (using the TIBCO EMS C# API).</span></span> <span data-ttu-id="de8d7-106">BizTalk Adapter for TIBCO EMS 會使用此 API 來與 TIBCO EMS 進行通訊。</span><span class="sxs-lookup"><span data-stu-id="de8d7-106">BizTalk Adapter for TIBCO EMS uses this API to communicate with TIBCO EMS.</span></span>  
  
## <a name="adding-the-api-to-the-gac"></a><span data-ttu-id="de8d7-107">將 API 加入 GAC</span><span class="sxs-lookup"><span data-stu-id="de8d7-107">Adding the API to the GAC</span></span>  
 <span data-ttu-id="de8d7-108">BizTalk Adapter for TIBCO EMS 需要 TIBCO EMS C# API，TIBCO。EMS.dll，要加入至全域組件快取 (GAC)。</span><span class="sxs-lookup"><span data-stu-id="de8d7-108">BizTalk Adapter for TIBCO EMS requires the TIBCO EMS C# API, TIBCO.EMS.dll, to be added to the global assembly cache (GAC).</span></span> <span data-ttu-id="de8d7-109">配接器會觸發例外狀況，並記錄適當的訊息，如果未安裝這個組件。</span><span class="sxs-lookup"><span data-stu-id="de8d7-109">The adapter triggers an exception and logs an appropriate message if this assembly is not installed.</span></span>  
  
#### <a name="to-add-the-tibco-ems-c-api-to-the-gac"></a><span data-ttu-id="de8d7-110">若要將 TIBCO EMS C# API 加入 GAC</span><span class="sxs-lookup"><span data-stu-id="de8d7-110">To add the TIBCO EMS C# API to the GAC</span></span>  
  
1.  <span data-ttu-id="de8d7-111">複製至 TIBCO EMS C #API 您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦。</span><span class="sxs-lookup"><span data-stu-id="de8d7-111">Copy the TIBCO EMS C#API to your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer.</span></span>  
  
2.  <span data-ttu-id="de8d7-112">將目錄變更為 C# API 檔案，TIBCO 的位置。EMS。DLL。</span><span class="sxs-lookup"><span data-stu-id="de8d7-112">Change directories to the location of the C# API file, TIBCO.EMS.DLL.</span></span>  
  
     <span data-ttu-id="de8d7-113">在預設安裝中，這個 dll 的路徑會是 c:\tibco\ems\clients\cs\TIBCO。EMS。DLL。</span><span class="sxs-lookup"><span data-stu-id="de8d7-113">In the default installation, the path to this DLL is c:\tibco\ems\clients\cs\TIBCO.EMS.DLL.</span></span>  
  
3.  <span data-ttu-id="de8d7-114">在命令提示字元中，輸入：</span><span class="sxs-lookup"><span data-stu-id="de8d7-114">In a command prompt, type:</span></span>  
  
     `C:\bin> gacutil /i TIBCO.EMS.dll`  
  
     <span data-ttu-id="de8d7-115">TIBCO。EMS.dll 現在會顯示 GAC。</span><span class="sxs-lookup"><span data-stu-id="de8d7-115">The TIBCO.EMS.dll now shows the GAC.</span></span>  
  
     <span data-ttu-id="de8d7-116">若要檢視 GAC 清單中，控制台] 中，開啟**系統管理工具**，開啟**Microsoft.NET Framework X.XConfiguration**，然後按一下 [**組件快取**。</span><span class="sxs-lookup"><span data-stu-id="de8d7-116">To view the GAC list, in Control Panel, open **Administrative Tools**, open **Microsoft .NET Framework X.XConfiguration**, and then click **Assembly Cache**.</span></span>  
  
## <a name="limitations"></a><span data-ttu-id="de8d7-117">限制</span><span class="sxs-lookup"><span data-stu-id="de8d7-117">Limitations</span></span>  
 <span data-ttu-id="de8d7-118">BizTalk Adapter for TIBCO Enterprise Message Service 會使用 TIBCO。EMS.dll 與 TIBCO Enterprise Message Service 進行通訊。</span><span class="sxs-lookup"><span data-stu-id="de8d7-118">BizTalk Adapter for TIBCO Enterprise Message Service uses TIBCO.EMS.dll to communicate with TIBCO Enterprise Message Service.</span></span> <span data-ttu-id="de8d7-119">當您使用 TIBCO EMS C# API 時，您應該考慮下列限制：</span><span class="sxs-lookup"><span data-stu-id="de8d7-119">You should consider the following limitations when you use the TIBCO EMS C# API:</span></span>  
  
-   <span data-ttu-id="de8d7-120">訊息壓縮功能，可讓 TIBCO EMS 用戶端是以壓縮格式的訊息傳送給 EMS，都無法使用 C# API。</span><span class="sxs-lookup"><span data-stu-id="de8d7-120">Message compression, which enables the TIBCO EMS client to send messages in a compressed form to EMS, is not available with the C# API.</span></span>  
  
-   <span data-ttu-id="de8d7-121">找不到適用於 C# API 的配接器和伺服器之間的訊息加密。</span><span class="sxs-lookup"><span data-stu-id="de8d7-121">Encryption of messages between the adapter and the server is not available with the C# API.</span></span> <span data-ttu-id="de8d7-122">C# API 不允許使用 OpenSSL 程式庫的 SSL 加密。</span><span class="sxs-lookup"><span data-stu-id="de8d7-122">The C# API does not allow for SSL encryption using the OpenSSL libraries.</span></span>  
  
-   <span data-ttu-id="de8d7-123">C# API 不支援適用於 EMS 的系統管理 API。</span><span class="sxs-lookup"><span data-stu-id="de8d7-123">The C# API does not support the Administration API for EMS.</span></span>  
  
-   <span data-ttu-id="de8d7-124">無法傳送或接收使用 BizTalk TIBCO EMS 配接器的訊息大於 50 MB 的大小。</span><span class="sxs-lookup"><span data-stu-id="de8d7-124">Messages greater than 50MB in size cannot be sent or received using the BizTalk TIBCO EMS adapter.</span></span> <span data-ttu-id="de8d7-125">超過此大小，在環境發生 System.OutOfMemoryException 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="de8d7-125">Beyond this size, the environment experiences System.OutOfMemoryException exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de8d7-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="de8d7-126">See Also</span></span>  
 [<span data-ttu-id="de8d7-127">規劃與架構</span><span class="sxs-lookup"><span data-stu-id="de8d7-127">Planning and Architecture</span></span>](../core/planning-and-architecture16.md)