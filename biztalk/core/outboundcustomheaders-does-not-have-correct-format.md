---
title: "沒有正確的格式 OutboundCustomHeaders。 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6097762b-01c9-48b8-8cee-ccd6b11d28d4
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b3b81a8c9c605f646a8ac0b6df2045af05eb58e5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="outboundcustomheaders-does-not-have-correct-format"></a><span data-ttu-id="40974-102">OutboundCustomHeaders 沒有正確的格式</span><span class="sxs-lookup"><span data-stu-id="40974-102">OutboundCustomHeaders does not have correct format</span></span>
## <a name="details"></a><span data-ttu-id="40974-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="40974-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="40974-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="40974-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="40974-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="40974-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="40974-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="40974-106">Event ID</span></span>|<span data-ttu-id="40974-107">0</span><span class="sxs-lookup"><span data-stu-id="40974-107">0</span></span>|  
|<span data-ttu-id="40974-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="40974-108">Event Source</span></span>|<span data-ttu-id="40974-109">0</span><span class="sxs-lookup"><span data-stu-id="40974-109">0</span></span>|  
|<span data-ttu-id="40974-110">元件</span><span class="sxs-lookup"><span data-stu-id="40974-110">Component</span></span>|<span data-ttu-id="40974-111">0</span><span class="sxs-lookup"><span data-stu-id="40974-111">0</span></span>|  
|<span data-ttu-id="40974-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="40974-112">Symbolic Name</span></span>|<span data-ttu-id="40974-113">0</span><span class="sxs-lookup"><span data-stu-id="40974-113">0</span></span>|  
|<span data-ttu-id="40974-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="40974-114">Message Text</span></span>|<span data-ttu-id="40974-115">OutboundCustomHeaders 沒有正確的格式</span><span class="sxs-lookup"><span data-stu-id="40974-115">OutboundCustomHeaders does not have a correct format</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="40974-116">說明</span><span class="sxs-lookup"><span data-stu-id="40974-116">Explanation</span></span>  
 <span data-ttu-id="40974-117">WCF 的值。InboundHeaders 或 WCF。OutboundCustomHeaders 不是以下列格式：\<標頭 >...\</headers >。</span><span class="sxs-lookup"><span data-stu-id="40974-117">The value of WCF.InboundHeaders or WCF.OutboundCustomHeaders  is not in the following format: \<headers>….\</headers>.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="40974-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="40974-118">User Action</span></span>  
 <span data-ttu-id="40974-119">自動換行的屬性值與\<標頭 > 項目。</span><span class="sxs-lookup"><span data-stu-id="40974-119">Wrap the property values with \<headers> element.</span></span>  
  
 <span data-ttu-id="40974-120">如需詳細資訊，請參閱下列資源中的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：</span><span class="sxs-lookup"><span data-stu-id="40974-120">For further information, see the following resource in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="40974-121">WCF 訊息的管線元件中使用 SOAP 標頭</span><span class="sxs-lookup"><span data-stu-id="40974-121">Using SOAP Headers in WCF Messages with Pipeline Components</span></span>](../core/using-soap-headers-in-wcf-messages-with-pipeline-components.md)