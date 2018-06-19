---
title: 無效的傳送逾時 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 01c63cd8-e978-4dd6-ba12-d0c0ad07b8c7
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d790471f23e0eafd0110e1fff3484836f4e1c653
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22257590"
---
# <a name="invalid-send-timeout"></a><span data-ttu-id="e5faa-102">無效的傳送等候逾時</span><span class="sxs-lookup"><span data-stu-id="e5faa-102">Invalid send timeout</span></span>
## <a name="details"></a><span data-ttu-id="e5faa-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="e5faa-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e5faa-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="e5faa-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="e5faa-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="e5faa-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="e5faa-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="e5faa-106">Event ID</span></span>|<span data-ttu-id="e5faa-107">0</span><span class="sxs-lookup"><span data-stu-id="e5faa-107">0</span></span>|  
|<span data-ttu-id="e5faa-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="e5faa-108">Event Source</span></span>|<span data-ttu-id="e5faa-109">0</span><span class="sxs-lookup"><span data-stu-id="e5faa-109">0</span></span>|  
|<span data-ttu-id="e5faa-110">元件</span><span class="sxs-lookup"><span data-stu-id="e5faa-110">Component</span></span>|<span data-ttu-id="e5faa-111">0</span><span class="sxs-lookup"><span data-stu-id="e5faa-111">0</span></span>|  
|<span data-ttu-id="e5faa-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="e5faa-112">Symbolic Name</span></span>|<span data-ttu-id="e5faa-113">0</span><span class="sxs-lookup"><span data-stu-id="e5faa-113">0</span></span>|  
|<span data-ttu-id="e5faa-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="e5faa-114">Message Text</span></span>|<span data-ttu-id="e5faa-115">無效的傳送等候逾時。</span><span class="sxs-lookup"><span data-stu-id="e5faa-115">Invalid send timeout.</span></span> <span data-ttu-id="e5faa-116">有效範圍： 0 到 23 小時，0 到 59 分鐘的時間，以及 0 到 59 秒。</span><span class="sxs-lookup"><span data-stu-id="e5faa-116">Valid range: 0 to 23 hours, 0 to 59 minutes, and 0 to 59 seconds.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="e5faa-117">說明</span><span class="sxs-lookup"><span data-stu-id="e5faa-117">Explanation</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e5faa-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="e5faa-118">User Action</span></span>  
 <span data-ttu-id="e5faa-119">您可以使用下列程序來設定逾時時間範圍。</span><span class="sxs-lookup"><span data-stu-id="e5faa-119">Use the following procedure to configure the timeout range.</span></span>  
  
#### <a name="to-configure-the-timeout-range"></a><span data-ttu-id="e5faa-120">若要設定的逾時範圍</span><span class="sxs-lookup"><span data-stu-id="e5faa-120">To configure the timeout range</span></span>  
  
1.  <span data-ttu-id="e5faa-121">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="e5faa-121">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="e5faa-122">在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="e5faa-122">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3.  <span data-ttu-id="e5faa-123">找出您的應用程式，然後再找出您的傳輸。</span><span class="sxs-lookup"><span data-stu-id="e5faa-123">Locate your application and then locate your transport.</span></span>  
  
4.  <span data-ttu-id="e5faa-124">以滑鼠右鍵按一下傳輸名稱。</span><span class="sxs-lookup"><span data-stu-id="e5faa-124">Right-click the transport name.</span></span>  
  
5.  <span data-ttu-id="e5faa-125">按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="e5faa-125">Click **Properties**.</span></span>  
  
6.  <span data-ttu-id="e5faa-126">在 連接埠**類型**清單中，選取正確的連接埠。</span><span class="sxs-lookup"><span data-stu-id="e5faa-126">In the port **Type** list, select the correct port.</span></span>  
  
7.  <span data-ttu-id="e5faa-127">按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="e5faa-127">Click **Configure**.</span></span>  
  
8.  <span data-ttu-id="e5faa-128">在**WCF [***傳輸類型***] 傳輸屬性**對話方塊中，按一下 [**繫結**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="e5faa-128">In the **WCF [***transport type***] Transport Properties** dialog box, click the **Binding** tab.</span></span>  
  
9. <span data-ttu-id="e5faa-129">確定逾時範圍有效。</span><span class="sxs-lookup"><span data-stu-id="e5faa-129">Ensure the timeout range is valid.</span></span> <span data-ttu-id="e5faa-130">可接受的值為 0 到 23 小時，0 到 59 分鐘的時間，以及 0 到 59 秒數。</span><span class="sxs-lookup"><span data-stu-id="e5faa-130">Acceptable values are 0 to 23 hours, 0 to 59 minutes, and 0 to 59 seconds.</span></span>