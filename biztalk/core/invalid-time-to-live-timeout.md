---
title: 即時逾時的時間無效 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c2ddb6de-8c3b-4dee-a984-980e1caea95e
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9171fd311a07317c0480e6e4d1ef35742e0e8bcd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22262094"
---
# <a name="invalid-time-to-live-timeout"></a><span data-ttu-id="a3195-102">無效的存留時間等候逾時</span><span class="sxs-lookup"><span data-stu-id="a3195-102">Invalid time to live timeout</span></span>
## <a name="details"></a><span data-ttu-id="a3195-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="a3195-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a3195-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="a3195-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="a3195-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="a3195-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="a3195-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="a3195-106">Event ID</span></span>|<span data-ttu-id="a3195-107">0</span><span class="sxs-lookup"><span data-stu-id="a3195-107">0</span></span>|  
|<span data-ttu-id="a3195-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="a3195-108">Event Source</span></span>|<span data-ttu-id="a3195-109">0</span><span class="sxs-lookup"><span data-stu-id="a3195-109">0</span></span>|  
|<span data-ttu-id="a3195-110">元件</span><span class="sxs-lookup"><span data-stu-id="a3195-110">Component</span></span>|<span data-ttu-id="a3195-111">0</span><span class="sxs-lookup"><span data-stu-id="a3195-111">0</span></span>|  
|<span data-ttu-id="a3195-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="a3195-112">Symbolic Name</span></span>|<span data-ttu-id="a3195-113">0</span><span class="sxs-lookup"><span data-stu-id="a3195-113">0</span></span>|  
|<span data-ttu-id="a3195-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="a3195-114">Message Text</span></span>|<span data-ttu-id="a3195-115">即時逾時的時間無效。</span><span class="sxs-lookup"><span data-stu-id="a3195-115">Invalid time to live timeout.</span></span> <span data-ttu-id="a3195-116">有效範圍： 0 到 23 小時，0 到 59 分鐘的時間，以及 0 到 59 秒</span><span class="sxs-lookup"><span data-stu-id="a3195-116">Valid range: 0 to 23 hours, 0 to 59 minutes, and 0 to 59 seconds</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a3195-117">說明</span><span class="sxs-lookup"><span data-stu-id="a3195-117">Explanation</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a3195-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="a3195-118">User Action</span></span>  
 <span data-ttu-id="a3195-119">您可以使用下列程序來設定逾時時間範圍。</span><span class="sxs-lookup"><span data-stu-id="a3195-119">Use the following procedure to configure the timeout range.</span></span>  
  
#### <a name="to-configure-the-timeout-range"></a><span data-ttu-id="a3195-120">若要設定的逾時範圍</span><span class="sxs-lookup"><span data-stu-id="a3195-120">To configure the timeout range</span></span>  
  
1.  <span data-ttu-id="a3195-121">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="a3195-121">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="a3195-122">在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="a3195-122">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3.  <span data-ttu-id="a3195-123">找出您的應用程式，然後再找出您的傳輸。</span><span class="sxs-lookup"><span data-stu-id="a3195-123">Locate your application and then locate your transport.</span></span>  
  
4.  <span data-ttu-id="a3195-124">以滑鼠右鍵按一下傳輸名稱。</span><span class="sxs-lookup"><span data-stu-id="a3195-124">Right-click the transport name.</span></span>  
  
5.  <span data-ttu-id="a3195-125">按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="a3195-125">Click **Properties**.</span></span>  
  
6.  <span data-ttu-id="a3195-126">在 連接埠**類型**清單中，選取**Wcf-netmsmq**。</span><span class="sxs-lookup"><span data-stu-id="a3195-126">In the port **Type** list, select **WCF-NetMsmq**.</span></span>  
  
7.  <span data-ttu-id="a3195-127">按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="a3195-127">Click **Configure**.</span></span>  
  
8.  <span data-ttu-id="a3195-128">在**Wcf-netmsmq 傳輸屬性**對話方塊中，按一下 [**繫結**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="a3195-128">In the **WCF-NetMsmq Transport Properties** dialog box, click the **Binding** tab.</span></span>  
  
9. <span data-ttu-id="a3195-129">在**佇列設定**區段中，確定**訊息即時 (dd:hh:mm:ss) 的時間**範圍是否有效。</span><span class="sxs-lookup"><span data-stu-id="a3195-129">In the **Queue Settings** section, ensure the **Message time to live (dd:hh:mm:ss)** range is valid.</span></span> <span data-ttu-id="a3195-130">可接受的值為 0 到 23 小時，0 到 59 分鐘的時間，以及 0 到 59 秒數。</span><span class="sxs-lookup"><span data-stu-id="a3195-130">Acceptable values are 0 to 23 hours, 0 to 59 minutes, and 0 to 59 seconds.</span></span>