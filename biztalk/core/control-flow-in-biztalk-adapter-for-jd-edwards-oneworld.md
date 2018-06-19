---
title: 控制流程中 BizTalk Adapter for JD Edwards OneWorld |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- connection pooling
- control flows
- apartment threading
- apartment threading, business functions
ms.assetid: 1ec865d0-2257-453b-9230-1f3787ebac38
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0fc5a8be6516b61c4049242952967ce939513e9c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22237974"
---
# <a name="control-flow-in-biztalk-adapter-for-jd-edwards-oneworld"></a><span data-ttu-id="eee80-102">BizTalk Adapter for JD Edwards OneWorld 中的控制流程</span><span class="sxs-lookup"><span data-stu-id="eee80-102">Control Flow in BizTalk Adapter for JD Edwards OneWorld</span></span>
<span data-ttu-id="eee80-103">本主題將討論設計階段和執行階段控制流程，在 Microsoft BizTalk Adapter for JD Edwards OneWorld。</span><span class="sxs-lookup"><span data-stu-id="eee80-103">This topic discusses the design time and run-time control flows in Microsoft BizTalk Adapter for JD Edwards OneWorld.</span></span>  
  
## <a name="design-time-flow"></a><span data-ttu-id="eee80-104">設計階段流程</span><span class="sxs-lookup"><span data-stu-id="eee80-104">Design-Time Flow</span></span>  
 <span data-ttu-id="eee80-105">當配接器開啟時 (使用 [傳輸屬性] 對話方塊中的認證與系統資訊)，就會建立 JD Edwards OneWorld 的一或多個應用程式商務功能執行個體，並置入集區。</span><span class="sxs-lookup"><span data-stu-id="eee80-105">When the adapter opens (using the credentials and system information from the Transport Properties dialog box), one or more instances of the JD Edwards OneWorld application business function are created and pooled.</span></span> <span data-ttu-id="eee80-106">在配接器精靈中瀏覽命名空間時，就會出現商務功能清單。</span><span class="sxs-lookup"><span data-stu-id="eee80-106">When you browse the namespace in the Adapter Wizard, a list of business functions appear.</span></span> <span data-ttu-id="eee80-107">按一下商務功能，就會顯示其邏輯方法與方法簽章。</span><span class="sxs-lookup"><span data-stu-id="eee80-107">Clicking a business function displays its logical methods along with the methods signatures.</span></span>  
  
## <a name="run-time-flow"></a><span data-ttu-id="eee80-108">執行階段流程</span><span class="sxs-lookup"><span data-stu-id="eee80-108">Run-Time Flow</span></span>  
 <span data-ttu-id="eee80-109">對每個執行緒建立 JD Edwards OneWorld 商務功能執行個體，並置入集區。</span><span class="sxs-lookup"><span data-stu-id="eee80-109">Instances of the JD Edwards OneWorld business function are created and pooled for each thread.</span></span> <span data-ttu-id="eee80-110">將方法呼叫提交至商務服務時，就會使用 JD Edwards OneWorld 應用程式商務功能來讀取該方法的中繼資料；不過如果已快取該方法的中繼資料，商務功能就會使用快取的資訊，然後針對適當方法進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="eee80-110">When a method call is submitted to a business service, the metadata for the method is read using the JD Edwards OneWorld application business function; however, if the metadata for the method has already been cached, the business function uses the cached information and then makes a call to the appropriate method.</span></span> <span data-ttu-id="eee80-111">在執行階段，系統會動態地建構 JD Edwards OneWorld 介面層。</span><span class="sxs-lookup"><span data-stu-id="eee80-111">At run time, a JD Edwards OneWorld interface layer is dynamically constructed.</span></span> <span data-ttu-id="eee80-112">方法是透過 BizTalk Adapter for JD Edwards OneWorld 支援叫用和資料轉換的介面層。</span><span class="sxs-lookup"><span data-stu-id="eee80-112">It is through the interface layer that BizTalk Adapter for JD Edwards OneWorld supports invocation and data conversions.</span></span>  
  
 <span data-ttu-id="eee80-113">BizTalk Adapter for JD Edwards OneWorld 會對應 JD Edwards OneWorld 應用程式方法簽章的介面描述，允許 BizTalk Server 與這些介面描述互動。</span><span class="sxs-lookup"><span data-stu-id="eee80-113">BizTalk Adapter for JD Edwards OneWorld maps interface descriptions of the method signatures of the JD Edwards OneWorld application, allowing BizTalk Server to interact with these interface descriptions.</span></span>  
  
 <span data-ttu-id="eee80-114">配接器可採用下列一或多種形式來擴充應用程式中的功能，讓企業中的應用程式與 JD Edwards OneWorld 應用程式互動：</span><span class="sxs-lookup"><span data-stu-id="eee80-114">The adapter enables applications in the enterprise to interact with the JD Edwards OneWorld application by extending functionality from the application in the form of one or more of the following:</span></span>  
  
-   <span data-ttu-id="eee80-115">原生資料格式</span><span class="sxs-lookup"><span data-stu-id="eee80-115">Native data formats</span></span>  
  
-   <span data-ttu-id="eee80-116">程序</span><span class="sxs-lookup"><span data-stu-id="eee80-116">Procedures</span></span>  
  
-   <span data-ttu-id="eee80-117">方法</span><span class="sxs-lookup"><span data-stu-id="eee80-117">Methods</span></span>  
  
-   <span data-ttu-id="eee80-118">訊息</span><span class="sxs-lookup"><span data-stu-id="eee80-118">Messages</span></span>  
  
-   <span data-ttu-id="eee80-119">屬性</span><span class="sxs-lookup"><span data-stu-id="eee80-119">Properties</span></span>  
  
-   <span data-ttu-id="eee80-120">應用程式介面</span><span class="sxs-lookup"><span data-stu-id="eee80-120">Application interfaces</span></span>  
  
 <span data-ttu-id="eee80-121">在執行階段，BizTalk Adapter for JD Edwards OneWorld 可為與 JD Edwards OneWorld 互動的用戶端應用程式建置應用程式介面描述。</span><span class="sxs-lookup"><span data-stu-id="eee80-121">At run time, BizTalk Adapter for JD Edwards OneWorld builds a description of application interfaces for client applications that interact with JD Edwards OneWorld.</span></span> <span data-ttu-id="eee80-122">配接器可視需要建立、刪除以及叫用商務物件，在應用程式中執行運算以及直接叫用方法。</span><span class="sxs-lookup"><span data-stu-id="eee80-122">The adapter can create, delete, and invoke business objects as needed, to perform computations in the application and directly invoke methods.</span></span> <span data-ttu-id="eee80-123">針對 JD Edwards OneWorld 發出的所有呼叫，都是同步呼叫。</span><span class="sxs-lookup"><span data-stu-id="eee80-123">All calls into JD Edwards OneWorld are synchronous calls.</span></span> <span data-ttu-id="eee80-124">配接器會接收來自 BizTalk Server 的 XML 訊息，以 SOAP 信封括住訊息，然後將呼叫的資料從 SOAP 訊息轉換成 Java 類型。</span><span class="sxs-lookup"><span data-stu-id="eee80-124">The adapter receives the XML messages from BizTalk Server, encloses the messages in a SOAP envelope, and transforms the data for the call from SOAP messages into Java types.</span></span>  
  
 <span data-ttu-id="eee80-125">回覆會依照類似的程序送回：</span><span class="sxs-lookup"><span data-stu-id="eee80-125">The reply is sent back following a similar process:</span></span>  
  
1.  <span data-ttu-id="eee80-126">將 Java 類型轉換成 SOAP 訊息。</span><span class="sxs-lookup"><span data-stu-id="eee80-126">The Java types are transformed into SOAP messages.</span></span>  
  
2.  <span data-ttu-id="eee80-127">將 SOAP 訊息轉換成 XML 訊息。</span><span class="sxs-lookup"><span data-stu-id="eee80-127">The SOAP messages are converted into XML messages.</span></span>  
  
3.  <span data-ttu-id="eee80-128">將 XML 訊息提交至 BizTalk Server 以供進一步處理。</span><span class="sxs-lookup"><span data-stu-id="eee80-128">The XML messages are submitted to BizTalk Server for further processing.</span></span>  
  
### <a name="apartment-threading-of-business-functions"></a><span data-ttu-id="eee80-129">商務功能的 Apartment 執行緒</span><span class="sxs-lookup"><span data-stu-id="eee80-129">Apartment Threading of Business Functions</span></span>  
 <span data-ttu-id="eee80-130">JD Edwards OneWorld 商務功能與任何執行個體都只能在其建立或取得所在的執行緒上使用。</span><span class="sxs-lookup"><span data-stu-id="eee80-130">A JD Edwards OneWorld business function, and any instance, can only be used on the thread where it is created or obtained.</span></span> <span data-ttu-id="eee80-131">這稱為*apartment 執行緒*。</span><span class="sxs-lookup"><span data-stu-id="eee80-131">This is known as *apartment threading*.</span></span> <span data-ttu-id="eee80-132">BizTalk Adapter for JD Edwards OneWorld 的連線共用架構可管理可用連線的集區。</span><span class="sxs-lookup"><span data-stu-id="eee80-132">The connection pooling framework of BizTalk Adapter for JD Edwards OneWorld manages a pool of available connections.</span></span>  
  
### <a name="connection-pooling"></a><span data-ttu-id="eee80-133">連接共用</span><span class="sxs-lookup"><span data-stu-id="eee80-133">Connection Pooling</span></span>  
 <span data-ttu-id="eee80-134">連線共用可讓與伺服器系統的連線保持開啟，並予以重複使用，而不是在每個呼叫後關閉，透過此方法來改善呼叫效能。</span><span class="sxs-lookup"><span data-stu-id="eee80-134">Connection pooling improves the performance of calls by keeping connections to the server systems open and reusing them instead of closing them after each call.</span></span> <span data-ttu-id="eee80-135">BizTalk Adapter for JD Edwards OneWorld 可讓您共用特定登入識別碼內的連線，但仍保持控制所有集區的連線總數。</span><span class="sxs-lookup"><span data-stu-id="eee80-135">BizTalk Adapter for JD Edwards OneWorld enables you to pool connections within particular logon IDs, but still maintains critical control of the total number of connections across all pools.</span></span>  
  
 <span data-ttu-id="eee80-136">任何的新商務功能執行個體都會使用其建立所在的執行緒，並在完成每項作業之後摧毀該執行個體。</span><span class="sxs-lookup"><span data-stu-id="eee80-136">Any new business function instance uses the thread on which it is created, and the instance is destroyed after each operation.</span></span> <span data-ttu-id="eee80-137">商務功能的所有 JD Edwards OneWorld 呼叫都沒有狀態，不過在作業期間，配接器會確定是在正確的執行緒上使用該商務功能。</span><span class="sxs-lookup"><span data-stu-id="eee80-137">All JD Edwards OneWorld calls to business functions are stateless; however, during the operation, the adapter ensures that the business function is used on the correct thread.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eee80-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eee80-138">See Also</span></span>  
 <span data-ttu-id="eee80-139">[開發應用程式](../core/developing-applications3.md) </span><span class="sxs-lookup"><span data-stu-id="eee80-139">[Developing Applications](../core/developing-applications3.md) </span></span>  
 [<span data-ttu-id="eee80-140">規劃與架構</span><span class="sxs-lookup"><span data-stu-id="eee80-140">Planning and Architecture</span></span>](../core/planning-and-architecture17.md)