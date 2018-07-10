---
title: 無效的開啟逾時 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0047cf43-fcc3-40b4-abeb-bf1b6e7a422b
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b32e06d5f26eafe5d5184a995adc7103e659a739
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37023612"
---
# <a name="invalid-open-timeout"></a><span data-ttu-id="bf408-102">無效的開啟逾時</span><span class="sxs-lookup"><span data-stu-id="bf408-102">Invalid open timeout</span></span>
## <a name="details"></a><span data-ttu-id="bf408-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="bf408-103">Details</span></span>  

|                 |                                                                                         |
|-----------------|-----------------------------------------------------------------------------------------|
|  <span data-ttu-id="bf408-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="bf408-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]    |
| <span data-ttu-id="bf408-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="bf408-105">Product Version</span></span> |               [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                |
|    <span data-ttu-id="bf408-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="bf408-106">Event ID</span></span>     |                                            <span data-ttu-id="bf408-107">0</span><span class="sxs-lookup"><span data-stu-id="bf408-107">0</span></span>                                            |
|  <span data-ttu-id="bf408-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="bf408-108">Event Source</span></span>   |                                            <span data-ttu-id="bf408-109">0</span><span class="sxs-lookup"><span data-stu-id="bf408-109">0</span></span>                                            |
|    <span data-ttu-id="bf408-110">元件</span><span class="sxs-lookup"><span data-stu-id="bf408-110">Component</span></span>    |                                            <span data-ttu-id="bf408-111">0</span><span class="sxs-lookup"><span data-stu-id="bf408-111">0</span></span>                                            |
|  <span data-ttu-id="bf408-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="bf408-112">Symbolic Name</span></span>  |                                            <span data-ttu-id="bf408-113">0</span><span class="sxs-lookup"><span data-stu-id="bf408-113">0</span></span>                                            |
|  <span data-ttu-id="bf408-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="bf408-114">Message Text</span></span>   | <span data-ttu-id="bf408-115">無效的開啟逾時。</span><span class="sxs-lookup"><span data-stu-id="bf408-115">Invalid open timeout.</span></span> <span data-ttu-id="bf408-116">有效範圍： 0 到 23 小時，0 到 59 分，以及 0 到 59 秒。</span><span class="sxs-lookup"><span data-stu-id="bf408-116">Valid range: 0 to 23 hours, 0 to 59 minutes, and 0 to 59 seconds.</span></span> |

## <a name="explanation"></a><span data-ttu-id="bf408-117">說明</span><span class="sxs-lookup"><span data-stu-id="bf408-117">Explanation</span></span>  

## <a name="user-action"></a><span data-ttu-id="bf408-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="bf408-118">User Action</span></span>  
 <span data-ttu-id="bf408-119">您可以使用下列程序來設定逾時時間範圍。</span><span class="sxs-lookup"><span data-stu-id="bf408-119">Use the following procedure to configure the timeout range.</span></span>  

#### <a name="to-configure-the-timeout-range"></a><span data-ttu-id="bf408-120">若要設定逾時時間範圍</span><span class="sxs-lookup"><span data-stu-id="bf408-120">To configure the timeout range</span></span>  

1. <span data-ttu-id="bf408-121">按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理]**。</span><span class="sxs-lookup"><span data-stu-id="bf408-121">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  

2. <span data-ttu-id="bf408-122">在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="bf408-122">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.</span></span>  

3. <span data-ttu-id="bf408-123">找出您的應用程式，然後找出您的傳輸。</span><span class="sxs-lookup"><span data-stu-id="bf408-123">Locate your application and then locate your transport.</span></span>  

4. <span data-ttu-id="bf408-124">以滑鼠右鍵按一下傳輸名稱。</span><span class="sxs-lookup"><span data-stu-id="bf408-124">Right-click the transport name.</span></span>  

5. <span data-ttu-id="bf408-125">按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="bf408-125">Click **Properties**.</span></span>  

6. <span data-ttu-id="bf408-126">在 連接埠**型別**清單中，選取正確的連接埠。</span><span class="sxs-lookup"><span data-stu-id="bf408-126">In the port **Type** list, select the correct port.</span></span>  

7. <span data-ttu-id="bf408-127">按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="bf408-127">Click **Configure**.</span></span>  

8. <span data-ttu-id="bf408-128">在 [ **WCF [**<em>傳輸類型</em>**] 傳輸屬性**] 對話方塊中，按一下 [**繫結**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="bf408-128">In the **WCF [**<em>transport type</em>**] Transport Properties** dialog box, click the **Binding** tab.</span></span>  

9. <span data-ttu-id="bf408-129">確定逾時範圍有效。</span><span class="sxs-lookup"><span data-stu-id="bf408-129">Ensure the timeout range is valid.</span></span> <span data-ttu-id="bf408-130">可接受的值為 0 到 23 小時，0 到 59 分，以及 0 到 59 秒。</span><span class="sxs-lookup"><span data-stu-id="bf408-130">Acceptable values are 0 to 23 hours, 0 to 59 minutes, and 0 to 59 seconds.</span></span>
