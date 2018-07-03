---
title: 無效的服務憑證指紋 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 22e7d74e-40ec-4187-9246-bc8da2a9ce86
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5dcd37c3f3f2d56a9bdc2c576fee344a0eef7df4
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37005144"
---
# <a name="invalid-service-certificate-thumbprint"></a><span data-ttu-id="7f17b-102">無效的服務憑證指紋</span><span class="sxs-lookup"><span data-stu-id="7f17b-102">Invalid service certificate thumbprint</span></span>
## <a name="details"></a><span data-ttu-id="7f17b-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="7f17b-103">Details</span></span>  
  
|                 |                                                                                    |
|-----------------|------------------------------------------------------------------------------------|
|  <span data-ttu-id="7f17b-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="7f17b-104">Product Name</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| <span data-ttu-id="7f17b-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="7f17b-105">Product Version</span></span> |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    <span data-ttu-id="7f17b-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="7f17b-106">Event ID</span></span>     |                                         <span data-ttu-id="7f17b-107">0</span><span class="sxs-lookup"><span data-stu-id="7f17b-107">0</span></span>                                          |
|  <span data-ttu-id="7f17b-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="7f17b-108">Event Source</span></span>   |                                         <span data-ttu-id="7f17b-109">0</span><span class="sxs-lookup"><span data-stu-id="7f17b-109">0</span></span>                                          |
|    <span data-ttu-id="7f17b-110">元件</span><span class="sxs-lookup"><span data-stu-id="7f17b-110">Component</span></span>    |                                         <span data-ttu-id="7f17b-111">0</span><span class="sxs-lookup"><span data-stu-id="7f17b-111">0</span></span>                                          |
|  <span data-ttu-id="7f17b-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="7f17b-112">Symbolic Name</span></span>  |                                         <span data-ttu-id="7f17b-113">0</span><span class="sxs-lookup"><span data-stu-id="7f17b-113">0</span></span>                                          |
|  <span data-ttu-id="7f17b-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="7f17b-114">Message Text</span></span>   |       <span data-ttu-id="7f17b-115">無效的服務憑證指紋;必須是 40 位數的十六進位數字</span><span class="sxs-lookup"><span data-stu-id="7f17b-115">Invalid service certificate thumbprint; expected 40 hexadecimal digits</span></span>       |
  
## <a name="explanation"></a><span data-ttu-id="7f17b-116">說明</span><span class="sxs-lookup"><span data-stu-id="7f17b-116">Explanation</span></span>  
 <span data-ttu-id="7f17b-117">指定無效的服務憑證指紋。</span><span class="sxs-lookup"><span data-stu-id="7f17b-117">An invalid service certificate thumbprint was specified.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="7f17b-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="7f17b-118">User Action</span></span>  
 <span data-ttu-id="7f17b-119">在程式碼中設定 WCF 連接埠，使用者介面的服務憑證屬性應為十六進位的 40 位數值。</span><span class="sxs-lookup"><span data-stu-id="7f17b-119">In the code configuring the WCF port, the service certificate property of the user interface expects a hexadecimal 40-digit value.</span></span> <span data-ttu-id="7f17b-120">範例： 798A68E7A3E6F2CCC6929FC4AF2A15A9EED66E39</span><span class="sxs-lookup"><span data-stu-id="7f17b-120">Example: 798A68E7A3E6F2CCC6929FC4AF2A15A9EED66E39</span></span>  
  
 <span data-ttu-id="7f17b-121">如需有關憑證的詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="7f17b-121">For additional information on certificates, see the following resource:</span></span>  
  
-   [<span data-ttu-id="7f17b-122">安裝 WCF 配接器的憑證</span><span class="sxs-lookup"><span data-stu-id="7f17b-122">Installing Certificates for the WCF Adapters</span></span>](../core/installing-certificates-for-the-wcf-adapters.md)