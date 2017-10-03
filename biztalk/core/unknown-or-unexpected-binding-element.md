---
title: "不明或非預期的繫結項目 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 56021ff3-5abf-46ab-90bb-4531ccc9abd0
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 43c59c20968ea1329a6d689c7976aeba48650fc2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="unknown-or-unexpected-binding-element"></a><span data-ttu-id="1bd1b-102">不明或非預期的繫結項目</span><span class="sxs-lookup"><span data-stu-id="1bd1b-102">Unknown or unexpected binding element</span></span>
## <a name="details"></a><span data-ttu-id="1bd1b-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="1bd1b-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1bd1b-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="1bd1b-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="1bd1b-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="1bd1b-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="1bd1b-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="1bd1b-106">Event ID</span></span>|<span data-ttu-id="1bd1b-107">0</span><span class="sxs-lookup"><span data-stu-id="1bd1b-107">0</span></span>|  
|<span data-ttu-id="1bd1b-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="1bd1b-108">Event Source</span></span>|<span data-ttu-id="1bd1b-109">0</span><span class="sxs-lookup"><span data-stu-id="1bd1b-109">0</span></span>|  
|<span data-ttu-id="1bd1b-110">元件</span><span class="sxs-lookup"><span data-stu-id="1bd1b-110">Component</span></span>|<span data-ttu-id="1bd1b-111">0</span><span class="sxs-lookup"><span data-stu-id="1bd1b-111">0</span></span>|  
|<span data-ttu-id="1bd1b-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="1bd1b-112">Symbolic Name</span></span>|<span data-ttu-id="1bd1b-113">0</span><span class="sxs-lookup"><span data-stu-id="1bd1b-113">0</span></span>|  
|<span data-ttu-id="1bd1b-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="1bd1b-114">Message Text</span></span>|<span data-ttu-id="1bd1b-115">不明或非預期的繫結項目</span><span class="sxs-lookup"><span data-stu-id="1bd1b-115">Unknown or unexpected binding element</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="1bd1b-116">說明</span><span class="sxs-lookup"><span data-stu-id="1bd1b-116">Explanation</span></span>  
 <span data-ttu-id="1bd1b-117">此錯誤表示配接器找不到指定的繫結中的使用者定義繫結項目。</span><span class="sxs-lookup"><span data-stu-id="1bd1b-117">This error indicates the adapter cannot find the user defined binding element specified in the binding.</span></span> <span data-ttu-id="1bd1b-118">主要是搭配 Wcf-custom 和 Wcf-customisolated 配接器，就會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="1bd1b-118">This situation occurs primarily with the WCF-Custom and WCF-CustomIsolated adapters.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="1bd1b-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="1bd1b-119">User Action</span></span>  
 <span data-ttu-id="1bd1b-120">使用下列程序以確認繫結項目有效。</span><span class="sxs-lookup"><span data-stu-id="1bd1b-120">Use the following procedure to verify binding elements are valid.</span></span>  
  
#### <a name="to-verify-binding-elements-are-valid"></a><span data-ttu-id="1bd1b-121">若要驗證繫結項目有效</span><span class="sxs-lookup"><span data-stu-id="1bd1b-121">To verify binding elements are valid</span></span>  
  
1.  <span data-ttu-id="1bd1b-122">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="1bd1b-122">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="1bd1b-123">在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="1bd1b-123">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3.  <span data-ttu-id="1bd1b-124">找出您的應用程式，然後再找出您的傳輸。</span><span class="sxs-lookup"><span data-stu-id="1bd1b-124">Locate your application and then locate your transport.</span></span>  
  
4.  <span data-ttu-id="1bd1b-125">以滑鼠右鍵按一下傳輸名稱。</span><span class="sxs-lookup"><span data-stu-id="1bd1b-125">Right-click the transport name.</span></span>  
  
5.  <span data-ttu-id="1bd1b-126">按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="1bd1b-126">Click **Properties**.</span></span>  
  
6.  <span data-ttu-id="1bd1b-127">在 連接埠**類型**清單中，選取正確的連接埠。</span><span class="sxs-lookup"><span data-stu-id="1bd1b-127">In the port **Type** list, select the correct port.</span></span>  
  
7.  <span data-ttu-id="1bd1b-128">按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="1bd1b-128">Click **Configure**.</span></span>  
  
8.  <span data-ttu-id="1bd1b-129">在 WCF **[***傳輸類型***] 傳輸屬性**對話方塊中，按一下 [**繫結**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="1bd1b-129">In the WCF **[***transport type***] Transport Properties** dialog box, click the **Binding** tab.</span></span>  
  
9. <span data-ttu-id="1bd1b-130">請確定組態中指定的繫結項目有效。</span><span class="sxs-lookup"><span data-stu-id="1bd1b-130">Ensure that the binding elements specified in the configuration are valid.</span></span>