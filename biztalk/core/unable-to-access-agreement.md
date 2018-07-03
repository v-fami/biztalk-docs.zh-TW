---
title: 無法存取協議 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 72890ee9-54c9-48ed-8c6e-8b329d79c68b
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4b9c8d8126a7b38d95adfce1e813dd2a86ccde24
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37024532"
---
# <a name="unable-to-access-agreement"></a><span data-ttu-id="14264-102">無法存取協議</span><span class="sxs-lookup"><span data-stu-id="14264-102">Unable to access agreement</span></span>
## <a name="details"></a><span data-ttu-id="14264-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="14264-103">Details</span></span>  

|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="14264-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="14264-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="14264-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="14264-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="14264-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="14264-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="14264-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="14264-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="14264-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="14264-108"> EDI</span></span> |
|    <span data-ttu-id="14264-109">元件</span><span class="sxs-lookup"><span data-stu-id="14264-109">Component</span></span>    |                                       <span data-ttu-id="14264-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="14264-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="14264-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="14264-111">Symbolic Name</span></span>  |                              <span data-ttu-id="14264-112">UnableToLocateAS2PartyError</span><span class="sxs-lookup"><span data-stu-id="14264-112">UnableToLocateAS2PartyError</span></span>                               |
|  <span data-ttu-id="14264-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="14264-113">Message Text</span></span>   |            <span data-ttu-id="14264-114">無法存取協議。</span><span class="sxs-lookup"><span data-stu-id="14264-114">Unable to access agreement.</span></span> <span data-ttu-id="14264-115">AS2From: {0} AS2To: {1}。</span><span class="sxs-lookup"><span data-stu-id="14264-115">AS2From: {0} AS2To: {1}.</span></span> <span data-ttu-id="14264-116">錯誤： {2}</span><span class="sxs-lookup"><span data-stu-id="14264-116">Error: {2}</span></span>             |

## <a name="explanation"></a><span data-ttu-id="14264-117">說明</span><span class="sxs-lookup"><span data-stu-id="14264-117">Explanation</span></span>  
 <span data-ttu-id="14264-118">此錯誤表示 BizTalk Server 找不到指定的辨識符號和值的合作對象。</span><span class="sxs-lookup"><span data-stu-id="14264-118">This error indicates BizTalk Server could not find a party for the given qualifier and value.</span></span>  

## <a name="user-action"></a><span data-ttu-id="14264-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="14264-119">User Action</span></span>  
 <span data-ttu-id="14264-120">若要解決這個錯誤，建立以給定限定詞的合作對象別名：</span><span class="sxs-lookup"><span data-stu-id="14264-120">To resolve this error, create a party alias for the given qualifier:</span></span>  

1. <span data-ttu-id="14264-121">按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="14264-121">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  

2. <span data-ttu-id="14264-122">在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後按一下**合作對象**。</span><span class="sxs-lookup"><span data-stu-id="14264-122">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and click **Parties**.</span></span>  

3. <span data-ttu-id="14264-123">以滑鼠右鍵按一下正確的合作對象。</span><span class="sxs-lookup"><span data-stu-id="14264-123">Right-click the correct party.</span></span>  

4. <span data-ttu-id="14264-124">按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="14264-124">Click **Properties**.</span></span>  

5. <span data-ttu-id="14264-125">在 [*合作對象名稱*]**合作對象屬性**對話方塊中，輸入**EDIINT-AS2 From 值**中**名稱**資料行。</span><span class="sxs-lookup"><span data-stu-id="14264-125">In the [*party name*] **Party Properties** dialog box, enter **EDIINT-AS2 From Value** in the **Name** column.</span></span>  

6. <span data-ttu-id="14264-126">輸入中的合作對象名稱**值**資料行。</span><span class="sxs-lookup"><span data-stu-id="14264-126">Enter the party name in the **Value** column.</span></span>  

7. <span data-ttu-id="14264-127">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="14264-127">Click **OK**.</span></span>
