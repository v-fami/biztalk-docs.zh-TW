---
title: 交換包含格式不正確的 ISA，或無法使用服務結構描述 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 78d285f6-26fb-4a3b-a959-a17623321b20
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cce469b25a2ba15c3038ea9079c3f22fc4f8c0c2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010711"
---
# <a name="the-interchange-contained-a-malformed-isa-or-the-service-schema-was-not-available"></a><span data-ttu-id="162d0-102">交換包含格式不正確的 ISA，或服務結構描述無法使用</span><span class="sxs-lookup"><span data-stu-id="162d0-102">The interchange contained a malformed ISA or the Service schema was not available</span></span>
## <a name="details"></a><span data-ttu-id="162d0-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="162d0-103">Details</span></span>  
  
|                 |                                                                                                                    |
|-----------------|--------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="162d0-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="162d0-104">Product Name</span></span>   |                 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                 |
| <span data-ttu-id="162d0-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="162d0-105">Product Version</span></span> |                             [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                             |
|    <span data-ttu-id="162d0-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="162d0-106">Event ID</span></span>     |                                                         -                                                          |
|  <span data-ttu-id="162d0-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="162d0-107">Event Source</span></span>   |               [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="162d0-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="162d0-108"> EDI</span></span>               |
|    <span data-ttu-id="162d0-109">元件</span><span class="sxs-lookup"><span data-stu-id="162d0-109">Component</span></span>    |                                                     <span data-ttu-id="162d0-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="162d0-110">EDI Engine</span></span>                                                     |
|  <span data-ttu-id="162d0-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="162d0-111">Symbolic Name</span></span>  |                                                 <span data-ttu-id="162d0-112">MalformedIsaError</span><span class="sxs-lookup"><span data-stu-id="162d0-112">MalformedIsaError</span></span>                                                  |
|  <span data-ttu-id="162d0-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="162d0-113">Message Text</span></span>   | <span data-ttu-id="162d0-114">交換包含格式不正確的 ISA 或服務結構描述無法使用，它完全拒絕</span><span class="sxs-lookup"><span data-stu-id="162d0-114">The interchange contained a malformed ISA or the Service schema was not available, it is being rejected completely</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="162d0-115">說明</span><span class="sxs-lookup"><span data-stu-id="162d0-115">Explanation</span></span>  
 <span data-ttu-id="162d0-116">這個錯誤/警告/資訊事件表示，接收管線無法處理內送的交換，因為 X12ServiceSchema，不符合交換中的 ISA 或 IEA 區段，或 （在 BaseArtifacts.dll) X12ServiceSchema未部署。</span><span class="sxs-lookup"><span data-stu-id="162d0-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange, because the ISA or IEA segments in the interchange did not conform to the X12ServiceSchema, or the X12ServiceSchema (in BaseArtifacts.dll) was not deployed.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="162d0-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="162d0-117">User Action</span></span>  
 <span data-ttu-id="162d0-118">若要解決這個錯誤，請執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="162d0-118">To resolve this error, do one of the following:</span></span>  
  
-   <span data-ttu-id="162d0-119">有的寄件者的交換變更 ISA 和 IEA 區段，使它們符合 X12ServiceSchema。</span><span class="sxs-lookup"><span data-stu-id="162d0-119">Have the sender of the interchange change the ISA and IEA segments so that they conform to the X12ServiceSchema.</span></span>  
  
-   <span data-ttu-id="162d0-120">請確定 BaseArtifacts.dll 包含 X12ServiceSchema 和部署。</span><span class="sxs-lookup"><span data-stu-id="162d0-120">Ensure that BaseArtifacts.dll includes the X12ServiceSchema and is deployed.</span></span> <span data-ttu-id="162d0-121">您可以藉由開啟 BizTalk Server 管理主控台，開啟 BizTalk EDI 應用程式 節點，然後 結構描述 節點中，確認已列出 X12ServiceSchema 來這麼做。</span><span class="sxs-lookup"><span data-stu-id="162d0-121">You can do so by opening the BizTalk Server Administration Console, opening the BizTalk EDI Application node and then the Schemas node, and verifying that X12ServiceSchema is listed.</span></span>