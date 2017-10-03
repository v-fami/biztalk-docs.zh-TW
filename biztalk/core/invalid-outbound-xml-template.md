---
title: "無效的輸出 XML 範本 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f29bb60-8c04-4921-84bf-c629540a1c83
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f58d230b481e611879637ff1b6ae08c2eed0313f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-outbound-xml-template"></a><span data-ttu-id="ffd22-102">無效的輸出 XML 範本</span><span class="sxs-lookup"><span data-stu-id="ffd22-102">Invalid outbound XML template</span></span>
## <a name="details"></a><span data-ttu-id="ffd22-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="ffd22-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ffd22-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="ffd22-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="ffd22-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="ffd22-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="ffd22-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="ffd22-106">Event ID</span></span>|<span data-ttu-id="ffd22-107">0</span><span class="sxs-lookup"><span data-stu-id="ffd22-107">0</span></span>|  
|<span data-ttu-id="ffd22-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="ffd22-108">Event Source</span></span>|<span data-ttu-id="ffd22-109">0</span><span class="sxs-lookup"><span data-stu-id="ffd22-109">0</span></span>|  
|<span data-ttu-id="ffd22-110">元件</span><span class="sxs-lookup"><span data-stu-id="ffd22-110">Component</span></span>|<span data-ttu-id="ffd22-111">0</span><span class="sxs-lookup"><span data-stu-id="ffd22-111">0</span></span>|  
|<span data-ttu-id="ffd22-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="ffd22-112">Symbolic Name</span></span>|<span data-ttu-id="ffd22-113">0</span><span class="sxs-lookup"><span data-stu-id="ffd22-113">0</span></span>|  
|<span data-ttu-id="ffd22-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="ffd22-114">Message Text</span></span>|<span data-ttu-id="ffd22-115">無效的輸出 XML 範本</span><span class="sxs-lookup"><span data-stu-id="ffd22-115">Invalid outbound XML template</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ffd22-116">說明</span><span class="sxs-lookup"><span data-stu-id="ffd22-116">Explanation</span></span>  
 <span data-ttu-id="ffd22-117">可能有多個原因。</span><span class="sxs-lookup"><span data-stu-id="ffd22-117">There could be multiple reasons.</span></span> <span data-ttu-id="ffd22-118">輸出 WCF 訊息本文的範本可能不是有效的 XML。</span><span class="sxs-lookup"><span data-stu-id="ffd22-118">The outbound WCF message body template may not be valid XML.</span></span> <span data-ttu-id="ffd22-119">它可能包含無效的字元，以指定的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="ffd22-119">It may contain invalid characters in the given encoding.</span></span> <span data-ttu-id="ffd22-120">根項目可能已遺失。</span><span class="sxs-lookup"><span data-stu-id="ffd22-120">The root element may be missing.</span></span> <span data-ttu-id="ffd22-121">根層級的資料可能不正確。</span><span class="sxs-lookup"><span data-stu-id="ffd22-121">The data at the root level may be invalid.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ffd22-122">使用者動作</span><span class="sxs-lookup"><span data-stu-id="ffd22-122">User Action</span></span>  
 <span data-ttu-id="ffd22-123">請確認範本運算式具有有效的 XML 程式碼。</span><span class="sxs-lookup"><span data-stu-id="ffd22-123">Ensure that template expression has valid XML code.</span></span> <span data-ttu-id="ffd22-124">請確定它並未包含任何無效字元且有一個根項目。</span><span class="sxs-lookup"><span data-stu-id="ffd22-124">Ensure that It doesn’t contain any invalid characters and that there is only one root element.</span></span>  
  
1.  <span data-ttu-id="ffd22-125">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="ffd22-125">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="ffd22-126">在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="ffd22-126">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3.  <span data-ttu-id="ffd22-127">找出您的應用程式，然後再找出您的傳輸。</span><span class="sxs-lookup"><span data-stu-id="ffd22-127">Locate your application and then locate your transport.</span></span>  
  
4.  <span data-ttu-id="ffd22-128">以滑鼠右鍵按一下傳輸名稱。</span><span class="sxs-lookup"><span data-stu-id="ffd22-128">Right-click the transport name.</span></span>  
  
5.  <span data-ttu-id="ffd22-129">按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="ffd22-129">Click **Properties**.</span></span>  
  
6.  <span data-ttu-id="ffd22-130">在 連接埠**類型**清單中，選取正確的連接埠。</span><span class="sxs-lookup"><span data-stu-id="ffd22-130">In the port **Type** list, select the correct port.</span></span>  
  
7.  <span data-ttu-id="ffd22-131">按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="ffd22-131">Click **Configure**.</span></span>  
  
8.  <span data-ttu-id="ffd22-132">在**WCF [***傳輸類型***] 傳輸屬性**對話方塊中，按一下 [**訊息**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="ffd22-132">In the **WCF [***transport type***] Transport Properties** dialog box, click the **Messages** tab.</span></span>  
  
9. <span data-ttu-id="ffd22-133">在**輸出 WCF 訊息內文**區段中，選取**範本--由範本指定內容**。</span><span class="sxs-lookup"><span data-stu-id="ffd22-133">In the **Outbound WCF message body** section, select **Template--content specified by template**.</span></span>  
  
10. <span data-ttu-id="ffd22-134">在**XML**文字，請確認有效的 XML 程式碼。</span><span class="sxs-lookup"><span data-stu-id="ffd22-134">In the **XML** text box, ensure that the XML code is valid.</span></span>  
  
 <span data-ttu-id="ffd22-135">如需有關範本的詳細資訊，請參閱下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：</span><span class="sxs-lookup"><span data-stu-id="ffd22-135">For additional information on templates, see the following resources in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="ffd22-136">指定訊息本文為 WCF 配接器</span><span class="sxs-lookup"><span data-stu-id="ffd22-136">Specifying the Message Body for the WCF Adapters</span></span>](../core/specifying-the-message-body-for-the-wcf-adapters.md)