---
title: OutboundCustomHeaders 未包含正確的格式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6097762b-01c9-48b8-8cee-ccd6b11d28d4
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6d9cb9311015bfa7d88169944a206a8882b11cfe
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37008919"
---
# <a name="outboundcustomheaders-does-not-have-correct-format"></a><span data-ttu-id="e8765-102">OutboundCustomHeaders 未包含正確的格式</span><span class="sxs-lookup"><span data-stu-id="e8765-102">OutboundCustomHeaders does not have correct format</span></span>
## <a name="details"></a><span data-ttu-id="e8765-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="e8765-103">Details</span></span>  
  
|                 |                                                                                    |
|-----------------|------------------------------------------------------------------------------------|
|  <span data-ttu-id="e8765-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="e8765-104">Product Name</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| <span data-ttu-id="e8765-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="e8765-105">Product Version</span></span> |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    <span data-ttu-id="e8765-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="e8765-106">Event ID</span></span>     |                                         <span data-ttu-id="e8765-107">0</span><span class="sxs-lookup"><span data-stu-id="e8765-107">0</span></span>                                          |
|  <span data-ttu-id="e8765-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="e8765-108">Event Source</span></span>   |                                         <span data-ttu-id="e8765-109">0</span><span class="sxs-lookup"><span data-stu-id="e8765-109">0</span></span>                                          |
|    <span data-ttu-id="e8765-110">元件</span><span class="sxs-lookup"><span data-stu-id="e8765-110">Component</span></span>    |                                         <span data-ttu-id="e8765-111">0</span><span class="sxs-lookup"><span data-stu-id="e8765-111">0</span></span>                                          |
|  <span data-ttu-id="e8765-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="e8765-112">Symbolic Name</span></span>  |                                         <span data-ttu-id="e8765-113">0</span><span class="sxs-lookup"><span data-stu-id="e8765-113">0</span></span>                                          |
|  <span data-ttu-id="e8765-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="e8765-114">Message Text</span></span>   |                <span data-ttu-id="e8765-115">OutboundCustomHeaders 未包含正確的格式</span><span class="sxs-lookup"><span data-stu-id="e8765-115">OutboundCustomHeaders does not have a correct format</span></span>                |
  
## <a name="explanation"></a><span data-ttu-id="e8765-116">說明</span><span class="sxs-lookup"><span data-stu-id="e8765-116">Explanation</span></span>  
 <span data-ttu-id="e8765-117">WCF 的值。InboundHeaders 或 WCF。OutboundCustomHeaders 未以下列格式：\<標頭\>...\</headers\>。</span><span class="sxs-lookup"><span data-stu-id="e8765-117">The value of WCF.InboundHeaders or WCF.OutboundCustomHeaders  is not in the following format: \<headers\>….\</headers\>.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e8765-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="e8765-118">User Action</span></span>  
 <span data-ttu-id="e8765-119">換行的屬性值\<標頭\>項目。</span><span class="sxs-lookup"><span data-stu-id="e8765-119">Wrap the property values with \<headers\> element.</span></span>  
  
 <span data-ttu-id="e8765-120">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：</span><span class="sxs-lookup"><span data-stu-id="e8765-120">For further information, see the following resource in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="e8765-121">搭配使用 WCF 訊息中的 SOAP 標頭與管線元件</span><span class="sxs-lookup"><span data-stu-id="e8765-121">Using SOAP Headers in WCF Messages with Pipeline Components</span></span>](../core/using-soap-headers-in-wcf-messages-with-pipeline-components.md)