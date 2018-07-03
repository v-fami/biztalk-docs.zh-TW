---
title: 無效的用戶端憑證指紋 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f18fa0a2-b0d9-4190-aa96-12ab7007edd1
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 74551ac825f9e517bec1d07edc7f288db732b348
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37018880"
---
# <a name="invalid-client-certificate-thumbprint"></a><span data-ttu-id="79ae4-102">無效的用戶端憑證指紋</span><span class="sxs-lookup"><span data-stu-id="79ae4-102">Invalid client certificate thumbprint</span></span>
## <a name="details"></a><span data-ttu-id="79ae4-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="79ae4-103">Details</span></span>  
  
|                 |                                                                                    |
|-----------------|------------------------------------------------------------------------------------|
|  <span data-ttu-id="79ae4-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="79ae4-104">Product Name</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| <span data-ttu-id="79ae4-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="79ae4-105">Product Version</span></span> |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    <span data-ttu-id="79ae4-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="79ae4-106">Event ID</span></span>     |                                         <span data-ttu-id="79ae4-107">0</span><span class="sxs-lookup"><span data-stu-id="79ae4-107">0</span></span>                                          |
|  <span data-ttu-id="79ae4-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="79ae4-108">Event Source</span></span>   |                                         <span data-ttu-id="79ae4-109">0</span><span class="sxs-lookup"><span data-stu-id="79ae4-109">0</span></span>                                          |
|    <span data-ttu-id="79ae4-110">元件</span><span class="sxs-lookup"><span data-stu-id="79ae4-110">Component</span></span>    |                                         <span data-ttu-id="79ae4-111">0</span><span class="sxs-lookup"><span data-stu-id="79ae4-111">0</span></span>                                          |
|  <span data-ttu-id="79ae4-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="79ae4-112">Symbolic Name</span></span>  |                                         <span data-ttu-id="79ae4-113">0</span><span class="sxs-lookup"><span data-stu-id="79ae4-113">0</span></span>                                          |
|  <span data-ttu-id="79ae4-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="79ae4-114">Message Text</span></span>   |       <span data-ttu-id="79ae4-115">無效的用戶端憑證指紋；應該是 40 位數的十六進位數字。</span><span class="sxs-lookup"><span data-stu-id="79ae4-115">Invalid client certificate thumbprint; expected 40 hexadecimal digits.</span></span>       |
  
## <a name="explanation"></a><span data-ttu-id="79ae4-116">說明</span><span class="sxs-lookup"><span data-stu-id="79ae4-116">Explanation</span></span>  
 <span data-ttu-id="79ae4-117">指定的用戶端憑證指紋無效。</span><span class="sxs-lookup"><span data-stu-id="79ae4-117">An invalid client certificate thumbprint was specified.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="79ae4-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="79ae4-118">User Action</span></span>  
 <span data-ttu-id="79ae4-119">在程式碼中設定 WCF 傳送埠，使用者介面的用戶端憑證屬性應為十六進位的 40 位數值。</span><span class="sxs-lookup"><span data-stu-id="79ae4-119">In the code configuring the WCF send port, the client certificate property of the user interface expects a hexadecimal 40-digit value.</span></span> <span data-ttu-id="79ae4-120">範例： 798A68E7A3E6F2CCC6929FC4AF2A15A9EED66E39</span><span class="sxs-lookup"><span data-stu-id="79ae4-120">Example: 798A68E7A3E6F2CCC6929FC4AF2A15A9EED66E39</span></span>  
  
 <span data-ttu-id="79ae4-121">如需有關憑證的詳細資訊，請參閱下列各項：</span><span class="sxs-lookup"><span data-stu-id="79ae4-121">For additional information on certificates, see the following:</span></span>  
  
-   [<span data-ttu-id="79ae4-122">安裝 WCF 配接器的憑證</span><span class="sxs-lookup"><span data-stu-id="79ae4-122">Installing Certificates for the WCF Adapters</span></span>](../core/installing-certificates-for-the-wcf-adapters.md)