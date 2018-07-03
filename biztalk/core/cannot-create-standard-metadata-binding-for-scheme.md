---
title: 無法建立標準中繼資料繫結配置 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ce441c3e-0f6e-46ed-90cf-825dbf89d910
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4fd4a91535c7872bb5be7328755808eb91758db6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36989311"
---
# <a name="cannot-create-standard-metadata-binding-for-scheme"></a><span data-ttu-id="7e313-102">無法為配置建立標準中繼資料繫結</span><span class="sxs-lookup"><span data-stu-id="7e313-102">Cannot create standard metadata binding for scheme</span></span>
## <a name="details"></a><span data-ttu-id="7e313-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="7e313-103">Details</span></span>  
  
|                 |                                                                                                                    |
|-----------------|--------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="7e313-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="7e313-104">Product Name</span></span>   |                 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                 |
| <span data-ttu-id="7e313-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="7e313-105">Product Version</span></span> |                             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                             |
|    <span data-ttu-id="7e313-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="7e313-106">Event ID</span></span>     |                                                         <span data-ttu-id="7e313-107">0</span><span class="sxs-lookup"><span data-stu-id="7e313-107">0</span></span>                                                          |
|  <span data-ttu-id="7e313-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="7e313-108">Event Source</span></span>   |                                                         <span data-ttu-id="7e313-109">0</span><span class="sxs-lookup"><span data-stu-id="7e313-109">0</span></span>                                                          |
|    <span data-ttu-id="7e313-110">元件</span><span class="sxs-lookup"><span data-stu-id="7e313-110">Component</span></span>    |                                                         <span data-ttu-id="7e313-111">0</span><span class="sxs-lookup"><span data-stu-id="7e313-111">0</span></span>                                                          |
|  <span data-ttu-id="7e313-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="7e313-112">Symbolic Name</span></span>  |                                                         <span data-ttu-id="7e313-113">0</span><span class="sxs-lookup"><span data-stu-id="7e313-113">0</span></span>                                                          |
|  <span data-ttu-id="7e313-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="7e313-114">Message Text</span></span>   | <span data-ttu-id="7e313-115">無法建立標準中繼資料繫結配置 」{0}"。</span><span class="sxs-lookup"><span data-stu-id="7e313-115">Cannot create standard metadata binding for scheme "{0}".</span></span> <span data-ttu-id="7e313-116">支援的配置為 http、https、net.pipe 和 net.tcp</span><span class="sxs-lookup"><span data-stu-id="7e313-116">Supported schemes are http, https, net.pipe, and net.tcp</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="7e313-117">說明</span><span class="sxs-lookup"><span data-stu-id="7e313-117">Explanation</span></span>  
 <span data-ttu-id="7e313-118">此錯誤表示嘗試從中使用中繼資料的服務不是支援的結構描述。</span><span class="sxs-lookup"><span data-stu-id="7e313-118">This error indicates the service from which the metadata is trying to be consumed is not a supported scheme.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="7e313-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="7e313-119">User Action</span></span>  
 <span data-ttu-id="7e313-120">發行具有有效的配置的中繼資料，然後再次執行精靈，對新的中繼資料位置。</span><span class="sxs-lookup"><span data-stu-id="7e313-120">Publish the metadata with a valid scheme and then run the wizard again, against the new metadata location.</span></span>  
  
 <span data-ttu-id="7e313-121">如需其他有關配接器和繫結的詳細資訊，請參閱下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：</span><span class="sxs-lookup"><span data-stu-id="7e313-121">For additional information on adapters and binding, see the following resources in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="7e313-122">WCF 配接器</span><span class="sxs-lookup"><span data-stu-id="7e313-122">WCF Adapters</span></span>](../core/wcf-adapters.md)