---
title: 無效的位址 (絕對 uri) |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5db292ad-9105-492d-a6c5-a7108159901a
caps.latest.revision: 20
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 933897545d47e2a68c1911474a3549931edd4512
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37001247"
---
# <a name="invalid-address-absolute-uri"></a><span data-ttu-id="533b3-102">無效的位址 (絕對 uri)</span><span class="sxs-lookup"><span data-stu-id="533b3-102">Invalid address (absolute uri)</span></span>
## <a name="details"></a><span data-ttu-id="533b3-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="533b3-103">Details</span></span>  

|                 |                                                                                    |
|-----------------|------------------------------------------------------------------------------------|
|  <span data-ttu-id="533b3-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="533b3-104">Product Name</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| <span data-ttu-id="533b3-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="533b3-105">Product Version</span></span> |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    <span data-ttu-id="533b3-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="533b3-106">Event ID</span></span>     |                                         <span data-ttu-id="533b3-107">0</span><span class="sxs-lookup"><span data-stu-id="533b3-107">0</span></span>                                          |
|  <span data-ttu-id="533b3-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="533b3-108">Event Source</span></span>   |                                         <span data-ttu-id="533b3-109">0</span><span class="sxs-lookup"><span data-stu-id="533b3-109">0</span></span>                                          |
|    <span data-ttu-id="533b3-110">元件</span><span class="sxs-lookup"><span data-stu-id="533b3-110">Component</span></span>    |                                         <span data-ttu-id="533b3-111">0</span><span class="sxs-lookup"><span data-stu-id="533b3-111">0</span></span>                                          |
|  <span data-ttu-id="533b3-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="533b3-112">Symbolic Name</span></span>  |                                         <span data-ttu-id="533b3-113">0</span><span class="sxs-lookup"><span data-stu-id="533b3-113">0</span></span>                                          |
|  <span data-ttu-id="533b3-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="533b3-114">Message Text</span></span>   |              <span data-ttu-id="533b3-115">無效的位址;「{0}"不是語式正確的絕對 uri</span><span class="sxs-lookup"><span data-stu-id="533b3-115">Invalid address; "{0}" is not a well-formed absolute uri</span></span>              |

## <a name="explanation"></a><span data-ttu-id="533b3-116">說明</span><span class="sxs-lookup"><span data-stu-id="533b3-116">Explanation</span></span>  
 <span data-ttu-id="533b3-117">這個錯誤事件表示您未提供的內含式 WCF 傳輸語式正確的絕對位址。</span><span class="sxs-lookup"><span data-stu-id="533b3-117">This error event indicates that you did not provide an in-process WCF transport with a well-formed absolute address.</span></span> <span data-ttu-id="533b3-118">比方說，您無法設定內含式 WCF 傳輸的位址屬性，為相對位址，例如 /path/service.svc。</span><span class="sxs-lookup"><span data-stu-id="533b3-118">For example, you cannot set the Address property of the in-process WCF transport to a relative address, such as /path/service.svc.</span></span>  

## <a name="user-action"></a><span data-ttu-id="533b3-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="533b3-119">User Action</span></span>  
 <span data-ttu-id="533b3-120">內含式 WCF 傳輸位址變更為語式正確的絕對位址。</span><span class="sxs-lookup"><span data-stu-id="533b3-120">Change the address of the in-process WCF transport to a well-formed absolute address.</span></span>  

1. <span data-ttu-id="533b3-121">按一下 **開始**，按一下**所有程式**，按一下  **Microsoft [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]** ，然後按一下**BizTalk Server 管理]**。</span><span class="sxs-lookup"><span data-stu-id="533b3-121">Click **Start**, click **All Programs**, click **Microsoft [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]**, and click **BizTalk Server Administration**.</span></span>  

2. <span data-ttu-id="533b3-122">在 [主控台根目錄中，展開**BizTalk Server 管理]**，展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="533b3-122">In the Console Root, expand  **BizTalk Server Administration**, expand **BizTalk Group**, and expand  **Applications**.</span></span>  

3. <span data-ttu-id="533b3-123">找出您的應用程式，然後找出您的傳輸。</span><span class="sxs-lookup"><span data-stu-id="533b3-123">Locate your application and then locate your transport.</span></span>  

4. <span data-ttu-id="533b3-124">以滑鼠右鍵按一下傳輸名稱。</span><span class="sxs-lookup"><span data-stu-id="533b3-124">Right-click the transport name.</span></span>  

5. <span data-ttu-id="533b3-125">按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="533b3-125">Click **Properties**.</span></span>  

6. <span data-ttu-id="533b3-126">在 連接埠**型別**清單中，選取正確的連接埠。</span><span class="sxs-lookup"><span data-stu-id="533b3-126">In the port **Type** list, select the correct port.</span></span>  

7. <span data-ttu-id="533b3-127">按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="533b3-127">Click **Configure**.</span></span>  

8. <span data-ttu-id="533b3-128">在 [ **WCF [**<em>傳輸類型</em>**] 傳輸屬性**] 對話方塊中，按一下 [**一般**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="533b3-128">In the **WCF [**<em>transport type</em>**] Transport Properties** dialog box, click the **General** tab.</span></span>  

9. <span data-ttu-id="533b3-129">在 **位址 (URI)** 文字方塊。</span><span class="sxs-lookup"><span data-stu-id="533b3-129">In the **Address (URI)** text box.</span></span> <span data-ttu-id="533b3-130">變更地址。</span><span class="sxs-lookup"><span data-stu-id="533b3-130">change the address.</span></span> <span data-ttu-id="533b3-131">語式正確的絕對位址的範例 http://localhost/path/service.svc</span><span class="sxs-lookup"><span data-stu-id="533b3-131">An example of a well-formed absolute address is http://localhost/path/service.svc</span></span>
