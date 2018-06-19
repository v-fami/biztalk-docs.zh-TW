---
title: 找不到輸入內文路徑運算式內容 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ed294662-a94e-4fbb-b125-878a27107eab
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 879b846900441cfced9e4a875d7c2ad74310e701
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22286766"
---
# <a name="unable-to-find-content-for-inbound-body-path-expression"></a><span data-ttu-id="aeb7d-102">找不到輸入內文路徑運算式的內容</span><span class="sxs-lookup"><span data-stu-id="aeb7d-102">Unable to find content for inbound body path expression</span></span>
## <a name="details"></a><span data-ttu-id="aeb7d-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="aeb7d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="aeb7d-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="aeb7d-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="aeb7d-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="aeb7d-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="aeb7d-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="aeb7d-106">Event ID</span></span>|<span data-ttu-id="aeb7d-107">0</span><span class="sxs-lookup"><span data-stu-id="aeb7d-107">0</span></span>|  
|<span data-ttu-id="aeb7d-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="aeb7d-108">Event Source</span></span>|<span data-ttu-id="aeb7d-109">0</span><span class="sxs-lookup"><span data-stu-id="aeb7d-109">0</span></span>|  
|<span data-ttu-id="aeb7d-110">元件</span><span class="sxs-lookup"><span data-stu-id="aeb7d-110">Component</span></span>|<span data-ttu-id="aeb7d-111">0</span><span class="sxs-lookup"><span data-stu-id="aeb7d-111">0</span></span>|  
|<span data-ttu-id="aeb7d-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="aeb7d-112">Symbolic Name</span></span>|<span data-ttu-id="aeb7d-113">0</span><span class="sxs-lookup"><span data-stu-id="aeb7d-113">0</span></span>|  
|<span data-ttu-id="aeb7d-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="aeb7d-114">Message Text</span></span>|<span data-ttu-id="aeb7d-115">訊息中找不到輸入內文路徑運算式 "{0}" 的內容</span><span class="sxs-lookup"><span data-stu-id="aeb7d-115">Unable to find content for inbound body path expression "{0}" in message</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="aeb7d-116">說明</span><span class="sxs-lookup"><span data-stu-id="aeb7d-116">Explanation</span></span>  
 <span data-ttu-id="aeb7d-117">經由執行內文路徑運算式來從內送訊息中擷取的內容不含任何資料。</span><span class="sxs-lookup"><span data-stu-id="aeb7d-117">The content extracted from the incoming message by executing the body path expression does not contain any data.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="aeb7d-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="aeb7d-118">User Action</span></span>  
 <span data-ttu-id="aeb7d-119">請確定內文路徑運算式正確無誤，而且內送訊息具有正確的資料。</span><span class="sxs-lookup"><span data-stu-id="aeb7d-119">Make sure that body path expression is correct, and the incoming message has the correct data.</span></span>  
  
1.  <span data-ttu-id="aeb7d-120">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="aeb7d-120">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="aeb7d-121">在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="aeb7d-121">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3.  <span data-ttu-id="aeb7d-122">找出您的應用程式，然後再找出您的傳輸。</span><span class="sxs-lookup"><span data-stu-id="aeb7d-122">Locate your application and then locate your transport.</span></span>  
  
4.  <span data-ttu-id="aeb7d-123">以滑鼠右鍵按一下傳輸名稱。</span><span class="sxs-lookup"><span data-stu-id="aeb7d-123">Right-click the transport name.</span></span>  
  
5.  <span data-ttu-id="aeb7d-124">按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="aeb7d-124">Click **Properties**.</span></span>  
  
6.  <span data-ttu-id="aeb7d-125">在 連接埠**類型**清單中，選取正確的連接埠。</span><span class="sxs-lookup"><span data-stu-id="aeb7d-125">In the port **Type** list, select the correct port.</span></span>  
  
7.  <span data-ttu-id="aeb7d-126">按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="aeb7d-126">Click **Configure**.</span></span>  
  
8.  <span data-ttu-id="aeb7d-127">在 WCF **[***傳輸類型***] 傳輸屬性**對話方塊中，按一下 [**訊息**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="aeb7d-127">In the WCF **[***transport type***] Transport Properties** dialog box, click the **Messages** tab.</span></span>  
  
9. <span data-ttu-id="aeb7d-128">在**輸入 BizTalk 訊息內文**區段中，檢查的資訊**內文路徑運算式**。</span><span class="sxs-lookup"><span data-stu-id="aeb7d-128">In the **Inbound BizTalk message body** section, check the information for **Body path expression**.</span></span>