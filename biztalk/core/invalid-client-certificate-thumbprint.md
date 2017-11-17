---
title: "無效的用戶端憑證指紋 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f18fa0a2-b0d9-4190-aa96-12ab7007edd1
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 84401d28261b13c6f49a063f34e29054a4aba108
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-client-certificate-thumbprint"></a><span data-ttu-id="56a4c-102">無效的用戶端憑證指紋</span><span class="sxs-lookup"><span data-stu-id="56a4c-102">Invalid client certificate thumbprint</span></span>
## <a name="details"></a><span data-ttu-id="56a4c-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="56a4c-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="56a4c-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="56a4c-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="56a4c-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="56a4c-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="56a4c-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="56a4c-106">Event ID</span></span>|<span data-ttu-id="56a4c-107">0</span><span class="sxs-lookup"><span data-stu-id="56a4c-107">0</span></span>|  
|<span data-ttu-id="56a4c-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="56a4c-108">Event Source</span></span>|<span data-ttu-id="56a4c-109">0</span><span class="sxs-lookup"><span data-stu-id="56a4c-109">0</span></span>|  
|<span data-ttu-id="56a4c-110">元件</span><span class="sxs-lookup"><span data-stu-id="56a4c-110">Component</span></span>|<span data-ttu-id="56a4c-111">0</span><span class="sxs-lookup"><span data-stu-id="56a4c-111">0</span></span>|  
|<span data-ttu-id="56a4c-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="56a4c-112">Symbolic Name</span></span>|<span data-ttu-id="56a4c-113">0</span><span class="sxs-lookup"><span data-stu-id="56a4c-113">0</span></span>|  
|<span data-ttu-id="56a4c-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="56a4c-114">Message Text</span></span>|<span data-ttu-id="56a4c-115">無效的用戶端憑證指紋；應該是 40 位數的十六進位數字。</span><span class="sxs-lookup"><span data-stu-id="56a4c-115">Invalid client certificate thumbprint; expected 40 hexadecimal digits.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="56a4c-116">說明</span><span class="sxs-lookup"><span data-stu-id="56a4c-116">Explanation</span></span>  
 <span data-ttu-id="56a4c-117">指定的用戶端憑證指紋無效。</span><span class="sxs-lookup"><span data-stu-id="56a4c-117">An invalid client certificate thumbprint was specified.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="56a4c-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="56a4c-118">User Action</span></span>  
 <span data-ttu-id="56a4c-119">在程式碼中設定 WCF 傳送埠，用戶端憑證內容的使用者介面會預期 40 位數的十六進位值。</span><span class="sxs-lookup"><span data-stu-id="56a4c-119">In the code configuring the WCF send port, the client certificate property of the user interface expects a hexadecimal 40-digit value.</span></span> <span data-ttu-id="56a4c-120">範例： 798A68E7A3E6F2CCC6929FC4AF2A15A9EED66E39</span><span class="sxs-lookup"><span data-stu-id="56a4c-120">Example: 798A68E7A3E6F2CCC6929FC4AF2A15A9EED66E39</span></span>  
  
 <span data-ttu-id="56a4c-121">如需有關憑證的詳細資訊，請參閱下列各項：</span><span class="sxs-lookup"><span data-stu-id="56a4c-121">For additional information on certificates, see the following:</span></span>  
  
-   [<span data-ttu-id="56a4c-122">WCF 配接器安裝憑證</span><span class="sxs-lookup"><span data-stu-id="56a4c-122">Installing Certificates for the WCF Adapters</span></span>](../core/installing-certificates-for-the-wcf-adapters.md)