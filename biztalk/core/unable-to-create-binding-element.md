---
title: "無法建立繫結項目 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5b036833-12ba-463c-8df6-9d5e1ac26b6d
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d9b93bfd8ca7f87904f32fefa60837603677bc23
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="unable-to-create-binding-element"></a><span data-ttu-id="cbc24-102">無法建立繫結項目</span><span class="sxs-lookup"><span data-stu-id="cbc24-102">Unable to create binding element</span></span>
## <a name="details"></a><span data-ttu-id="cbc24-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="cbc24-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cbc24-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="cbc24-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="cbc24-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="cbc24-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="cbc24-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="cbc24-106">Event ID</span></span>|<span data-ttu-id="cbc24-107">0</span><span class="sxs-lookup"><span data-stu-id="cbc24-107">0</span></span>|  
|<span data-ttu-id="cbc24-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="cbc24-108">Event Source</span></span>|<span data-ttu-id="cbc24-109">0</span><span class="sxs-lookup"><span data-stu-id="cbc24-109">0</span></span>|  
|<span data-ttu-id="cbc24-110">元件</span><span class="sxs-lookup"><span data-stu-id="cbc24-110">Component</span></span>|<span data-ttu-id="cbc24-111">0</span><span class="sxs-lookup"><span data-stu-id="cbc24-111">0</span></span>|  
|<span data-ttu-id="cbc24-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="cbc24-112">Symbolic Name</span></span>|<span data-ttu-id="cbc24-113">0</span><span class="sxs-lookup"><span data-stu-id="cbc24-113">0</span></span>|  
|<span data-ttu-id="cbc24-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="cbc24-114">Message Text</span></span>|<span data-ttu-id="cbc24-115">無法建立繫結項目繫結"{0}</span><span class="sxs-lookup"><span data-stu-id="cbc24-115">Unable to create binding element for binding "{0}</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="cbc24-116">說明</span><span class="sxs-lookup"><span data-stu-id="cbc24-116">Explanation</span></span>  
 <span data-ttu-id="cbc24-117">此錯誤表示配接器無法建立在執行階段組態中指定的繫結。</span><span class="sxs-lookup"><span data-stu-id="cbc24-117">This error indicates the adapter cannot create the binding specified in the configuration at runtime.</span></span> <span data-ttu-id="cbc24-118">主要是搭配 Wcf-custom 和 Wcf-customisolated 配接器，就會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="cbc24-118">This situation occurs primarily with the WCF-Custom and WCF-CustomIsolated adapters.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="cbc24-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="cbc24-119">User Action</span></span>  
 <span data-ttu-id="cbc24-120">使用下列程序以確認繫結項目有效。</span><span class="sxs-lookup"><span data-stu-id="cbc24-120">Use the following procedure to verify binding elements are valid.</span></span>  
  
#### <a name="to-verify-binding-elements"></a><span data-ttu-id="cbc24-121">若要確認繫結項目</span><span class="sxs-lookup"><span data-stu-id="cbc24-121">To verify binding elements</span></span>  
  
1.  <span data-ttu-id="cbc24-122">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="cbc24-122">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="cbc24-123">在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="cbc24-123">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3.  <span data-ttu-id="cbc24-124">找出您的應用程式，然後再找出您的傳輸。</span><span class="sxs-lookup"><span data-stu-id="cbc24-124">Locate your application and then locate your transport.</span></span>  
  
4.  <span data-ttu-id="cbc24-125">以滑鼠右鍵按一下傳輸名稱。</span><span class="sxs-lookup"><span data-stu-id="cbc24-125">Right-click the transport name.</span></span>  
  
5.  <span data-ttu-id="cbc24-126">按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="cbc24-126">Click **Properties**.</span></span>  
  
6.  <span data-ttu-id="cbc24-127">在 連接埠**類型**清單中，選取正確的連接埠。</span><span class="sxs-lookup"><span data-stu-id="cbc24-127">In the port **Type** list, select the correct port.</span></span>  
  
7.  <span data-ttu-id="cbc24-128">按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="cbc24-128">Click **Configure**.</span></span>  
  
8.  <span data-ttu-id="cbc24-129">在**WCF [***傳輸類型***] 傳輸屬性**對話方塊中，按一下 [**繫結**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="cbc24-129">In the **WCF [***transport type***] Transport Properties** dialog box, click the **Binding** tab.</span></span>  
  
9. <span data-ttu-id="cbc24-130">請確定組態中指定的繫結項目有效。</span><span class="sxs-lookup"><span data-stu-id="cbc24-130">Ensure that the binding elements specified in the configuration are valid.</span></span>