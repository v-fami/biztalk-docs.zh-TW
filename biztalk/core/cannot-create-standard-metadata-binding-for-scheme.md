---
title: "無法建立標準中繼資料繫結配置 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ce441c3e-0f6e-46ed-90cf-825dbf89d910
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3228da0dfee18581c5fa8105ce3dd480380cc034
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="cannot-create-standard-metadata-binding-for-scheme"></a><span data-ttu-id="9fc0c-102">無法為配置建立標準中繼資料繫結</span><span class="sxs-lookup"><span data-stu-id="9fc0c-102">Cannot create standard metadata binding for scheme</span></span>
## <a name="details"></a><span data-ttu-id="9fc0c-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="9fc0c-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9fc0c-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="9fc0c-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="9fc0c-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="9fc0c-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="9fc0c-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="9fc0c-106">Event ID</span></span>|<span data-ttu-id="9fc0c-107">0</span><span class="sxs-lookup"><span data-stu-id="9fc0c-107">0</span></span>|  
|<span data-ttu-id="9fc0c-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="9fc0c-108">Event Source</span></span>|<span data-ttu-id="9fc0c-109">0</span><span class="sxs-lookup"><span data-stu-id="9fc0c-109">0</span></span>|  
|<span data-ttu-id="9fc0c-110">元件</span><span class="sxs-lookup"><span data-stu-id="9fc0c-110">Component</span></span>|<span data-ttu-id="9fc0c-111">0</span><span class="sxs-lookup"><span data-stu-id="9fc0c-111">0</span></span>|  
|<span data-ttu-id="9fc0c-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="9fc0c-112">Symbolic Name</span></span>|<span data-ttu-id="9fc0c-113">0</span><span class="sxs-lookup"><span data-stu-id="9fc0c-113">0</span></span>|  
|<span data-ttu-id="9fc0c-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="9fc0c-114">Message Text</span></span>|<span data-ttu-id="9fc0c-115">無法為配置 "{0}" 建立標準中繼資料繫結。</span><span class="sxs-lookup"><span data-stu-id="9fc0c-115">Cannot create standard metadata binding for scheme "{0}".</span></span> <span data-ttu-id="9fc0c-116">支援的配置為 http、https、net.pipe 和 net.tcp</span><span class="sxs-lookup"><span data-stu-id="9fc0c-116">Supported schemes are http, https, net.pipe, and net.tcp</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="9fc0c-117">說明</span><span class="sxs-lookup"><span data-stu-id="9fc0c-117">Explanation</span></span>  
 <span data-ttu-id="9fc0c-118">此錯誤表示嘗試從中使用中繼資料的服務不是支援的結構描述。</span><span class="sxs-lookup"><span data-stu-id="9fc0c-118">This error indicates the service from which the metadata is trying to be consumed is not a supported scheme.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="9fc0c-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="9fc0c-119">User Action</span></span>  
 <span data-ttu-id="9fc0c-120">發行中繼資料，以有效的結構描述，然後再次執行精靈，對新的中繼資料位置。</span><span class="sxs-lookup"><span data-stu-id="9fc0c-120">Publish the metadata with a valid scheme and then run the wizard again, against the new metadata location.</span></span>  
  
 <span data-ttu-id="9fc0c-121">如需有關配接器和繫結的詳細資訊，請參閱下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：</span><span class="sxs-lookup"><span data-stu-id="9fc0c-121">For additional information on adapters and binding, see the following resources in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="9fc0c-122">WCF 配接器</span><span class="sxs-lookup"><span data-stu-id="9fc0c-122">WCF Adapters</span></span>](../core/wcf-adapters.md)