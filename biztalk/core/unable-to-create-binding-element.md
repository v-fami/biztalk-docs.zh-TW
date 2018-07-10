---
title: 無法建立繫結項目 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5b036833-12ba-463c-8df6-9d5e1ac26b6d
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 117ad9a604f0b0d61cd494da52d84b8aabd4a9eb
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36987895"
---
# <a name="unable-to-create-binding-element"></a><span data-ttu-id="50c8e-102">無法建立繫結項目</span><span class="sxs-lookup"><span data-stu-id="50c8e-102">Unable to create binding element</span></span>
## <a name="details"></a><span data-ttu-id="50c8e-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="50c8e-103">Details</span></span>  

|                 |                                                                                    |
|-----------------|------------------------------------------------------------------------------------|
|  <span data-ttu-id="50c8e-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="50c8e-104">Product Name</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| <span data-ttu-id="50c8e-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="50c8e-105">Product Version</span></span> |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    <span data-ttu-id="50c8e-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="50c8e-106">Event ID</span></span>     |                                         <span data-ttu-id="50c8e-107">0</span><span class="sxs-lookup"><span data-stu-id="50c8e-107">0</span></span>                                          |
|  <span data-ttu-id="50c8e-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="50c8e-108">Event Source</span></span>   |                                         <span data-ttu-id="50c8e-109">0</span><span class="sxs-lookup"><span data-stu-id="50c8e-109">0</span></span>                                          |
|    <span data-ttu-id="50c8e-110">元件</span><span class="sxs-lookup"><span data-stu-id="50c8e-110">Component</span></span>    |                                         <span data-ttu-id="50c8e-111">0</span><span class="sxs-lookup"><span data-stu-id="50c8e-111">0</span></span>                                          |
|  <span data-ttu-id="50c8e-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="50c8e-112">Symbolic Name</span></span>  |                                         <span data-ttu-id="50c8e-113">0</span><span class="sxs-lookup"><span data-stu-id="50c8e-113">0</span></span>                                          |
|  <span data-ttu-id="50c8e-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="50c8e-114">Message Text</span></span>   |                 <span data-ttu-id="50c8e-115">無法建立繫結的繫結項目 」{0}</span><span class="sxs-lookup"><span data-stu-id="50c8e-115">Unable to create binding element for binding "{0}</span></span>                  |

## <a name="explanation"></a><span data-ttu-id="50c8e-116">說明</span><span class="sxs-lookup"><span data-stu-id="50c8e-116">Explanation</span></span>  
 <span data-ttu-id="50c8e-117">此錯誤表示配接器無法建立在執行階段組態中指定的繫結。</span><span class="sxs-lookup"><span data-stu-id="50c8e-117">This error indicates the adapter cannot create the binding specified in the configuration at runtime.</span></span> <span data-ttu-id="50c8e-118">主要使用 Wcf-custom 和 Wcf-customisolated 配接器，就會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="50c8e-118">This situation occurs primarily with the WCF-Custom and WCF-CustomIsolated adapters.</span></span>  

## <a name="user-action"></a><span data-ttu-id="50c8e-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="50c8e-119">User Action</span></span>  
 <span data-ttu-id="50c8e-120">您可以使用下列程序來驗證繫結項目有效。</span><span class="sxs-lookup"><span data-stu-id="50c8e-120">Use the following procedure to verify binding elements are valid.</span></span>  

#### <a name="to-verify-binding-elements"></a><span data-ttu-id="50c8e-121">若要確認繫結項目</span><span class="sxs-lookup"><span data-stu-id="50c8e-121">To verify binding elements</span></span>  

1. <span data-ttu-id="50c8e-122">按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理]**。</span><span class="sxs-lookup"><span data-stu-id="50c8e-122">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  

2. <span data-ttu-id="50c8e-123">在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="50c8e-123">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.</span></span>  

3. <span data-ttu-id="50c8e-124">找出您的應用程式，然後找出您的傳輸。</span><span class="sxs-lookup"><span data-stu-id="50c8e-124">Locate your application and then locate your transport.</span></span>  

4. <span data-ttu-id="50c8e-125">以滑鼠右鍵按一下傳輸名稱。</span><span class="sxs-lookup"><span data-stu-id="50c8e-125">Right-click the transport name.</span></span>  

5. <span data-ttu-id="50c8e-126">按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="50c8e-126">Click **Properties**.</span></span>  

6. <span data-ttu-id="50c8e-127">在 連接埠**型別**清單中，選取正確的連接埠。</span><span class="sxs-lookup"><span data-stu-id="50c8e-127">In the port **Type** list, select the correct port.</span></span>  

7. <span data-ttu-id="50c8e-128">按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="50c8e-128">Click **Configure**.</span></span>  

8. <span data-ttu-id="50c8e-129">在 [ **WCF [**<em>傳輸類型</em>**] 傳輸屬性**] 對話方塊中，按一下 [**繫結**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="50c8e-129">In the **WCF [**<em>transport type</em>**] Transport Properties** dialog box, click the **Binding** tab.</span></span>  

9. <span data-ttu-id="50c8e-130">請確定組態中指定的繫結項目有效。</span><span class="sxs-lookup"><span data-stu-id="50c8e-130">Ensure that the binding elements specified in the configuration are valid.</span></span>
