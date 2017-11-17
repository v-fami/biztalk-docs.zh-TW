---
title: "無效的服務憑證指紋 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 22e7d74e-40ec-4187-9246-bc8da2a9ce86
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a465d631e72bc27c6b24274deb31e396037aa182
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-service-certificate-thumbprint"></a><span data-ttu-id="b06fe-102">無效的服務憑證指紋</span><span class="sxs-lookup"><span data-stu-id="b06fe-102">Invalid service certificate thumbprint</span></span>
## <a name="details"></a><span data-ttu-id="b06fe-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="b06fe-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b06fe-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="b06fe-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="b06fe-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="b06fe-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="b06fe-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="b06fe-106">Event ID</span></span>|<span data-ttu-id="b06fe-107">0</span><span class="sxs-lookup"><span data-stu-id="b06fe-107">0</span></span>|  
|<span data-ttu-id="b06fe-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="b06fe-108">Event Source</span></span>|<span data-ttu-id="b06fe-109">0</span><span class="sxs-lookup"><span data-stu-id="b06fe-109">0</span></span>|  
|<span data-ttu-id="b06fe-110">元件</span><span class="sxs-lookup"><span data-stu-id="b06fe-110">Component</span></span>|<span data-ttu-id="b06fe-111">0</span><span class="sxs-lookup"><span data-stu-id="b06fe-111">0</span></span>|  
|<span data-ttu-id="b06fe-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="b06fe-112">Symbolic Name</span></span>|<span data-ttu-id="b06fe-113">0</span><span class="sxs-lookup"><span data-stu-id="b06fe-113">0</span></span>|  
|<span data-ttu-id="b06fe-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="b06fe-114">Message Text</span></span>|<span data-ttu-id="b06fe-115">無效的服務憑證指紋。必須是 40 個十六進位數字</span><span class="sxs-lookup"><span data-stu-id="b06fe-115">Invalid service certificate thumbprint; expected 40 hexadecimal digits</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="b06fe-116">說明</span><span class="sxs-lookup"><span data-stu-id="b06fe-116">Explanation</span></span>  
 <span data-ttu-id="b06fe-117">指定了無效的服務憑證指紋。</span><span class="sxs-lookup"><span data-stu-id="b06fe-117">An invalid service certificate thumbprint was specified.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b06fe-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="b06fe-118">User Action</span></span>  
 <span data-ttu-id="b06fe-119">在程式碼中設定 WCF 通訊埠，使用者介面的服務憑證屬性必須要有 40 位數的十六進位值。</span><span class="sxs-lookup"><span data-stu-id="b06fe-119">In the code configuring the WCF port, the service certificate property of the user interface expects a hexadecimal 40-digit value.</span></span> <span data-ttu-id="b06fe-120">範例： 798A68E7A3E6F2CCC6929FC4AF2A15A9EED66E39</span><span class="sxs-lookup"><span data-stu-id="b06fe-120">Example: 798A68E7A3E6F2CCC6929FC4AF2A15A9EED66E39</span></span>  
  
 <span data-ttu-id="b06fe-121">如需有關憑證的詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="b06fe-121">For additional information on certificates, see the following resource:</span></span>  
  
-   [<span data-ttu-id="b06fe-122">WCF 配接器安裝憑證</span><span class="sxs-lookup"><span data-stu-id="b06fe-122">Installing Certificates for the WCF Adapters</span></span>](../core/installing-certificates-for-the-wcf-adapters.md)