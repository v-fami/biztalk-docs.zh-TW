---
title: 不支援交易通訊協定 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 11fb2497-9971-4e85-b21a-161734f071e0
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5dde6df3360a7b4581964f26e395448d15f3de73
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37022356"
---
# <a name="unsupported-transaction-protocol"></a><span data-ttu-id="f150c-102">不支援的交易通訊協定</span><span class="sxs-lookup"><span data-stu-id="f150c-102">Unsupported transaction protocol</span></span>
## <a name="details"></a><span data-ttu-id="f150c-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f150c-103">Details</span></span>  
  
|                 |                                                                                    |
|-----------------|------------------------------------------------------------------------------------|
|  <span data-ttu-id="f150c-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="f150c-104">Product Name</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| <span data-ttu-id="f150c-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="f150c-105">Product Version</span></span> |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    <span data-ttu-id="f150c-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="f150c-106">Event ID</span></span>     |                                         <span data-ttu-id="f150c-107">0</span><span class="sxs-lookup"><span data-stu-id="f150c-107">0</span></span>                                          |
|  <span data-ttu-id="f150c-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="f150c-108">Event Source</span></span>   |                                         <span data-ttu-id="f150c-109">0</span><span class="sxs-lookup"><span data-stu-id="f150c-109">0</span></span>                                          |
|    <span data-ttu-id="f150c-110">元件</span><span class="sxs-lookup"><span data-stu-id="f150c-110">Component</span></span>    |                                         <span data-ttu-id="f150c-111">0</span><span class="sxs-lookup"><span data-stu-id="f150c-111">0</span></span>                                          |
|  <span data-ttu-id="f150c-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="f150c-112">Symbolic Name</span></span>  |                                         <span data-ttu-id="f150c-113">0</span><span class="sxs-lookup"><span data-stu-id="f150c-113">0</span></span>                                          |
|  <span data-ttu-id="f150c-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="f150c-114">Message Text</span></span>   |                       <span data-ttu-id="f150c-115">不支援的交易通訊協定： {0}</span><span class="sxs-lookup"><span data-stu-id="f150c-115">Unsupported transaction protocol: {0}</span></span>                        |
  
## <a name="explanation"></a><span data-ttu-id="f150c-116">說明</span><span class="sxs-lookup"><span data-stu-id="f150c-116">Explanation</span></span>  
 <span data-ttu-id="f150c-117">當接收位置或傳送埠的交易通訊協定屬性設定為無效值時，就會發生此錯誤。</span><span class="sxs-lookup"><span data-stu-id="f150c-117">This error occurs when the transaction protocol property of a receive location or send port is set to an invalid value.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f150c-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="f150c-118">User Action</span></span>  
 <span data-ttu-id="f150c-119">若要解決這個錯誤，請執行下列一個或多個動作：</span><span class="sxs-lookup"><span data-stu-id="f150c-119">To resolve this error, do one or more of the following:</span></span>  
  
1. <span data-ttu-id="f150c-120">按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理]**。</span><span class="sxs-lookup"><span data-stu-id="f150c-120">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  
  
2. <span data-ttu-id="f150c-121">在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="f150c-121">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3. <span data-ttu-id="f150c-122">找出您的應用程式，然後找出您的傳輸。</span><span class="sxs-lookup"><span data-stu-id="f150c-122">Locate your application and then locate your transport.</span></span>  
  
4. <span data-ttu-id="f150c-123">以滑鼠右鍵按一下傳輸名稱。</span><span class="sxs-lookup"><span data-stu-id="f150c-123">Right-click the transport name.</span></span>  
  
5. <span data-ttu-id="f150c-124">按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="f150c-124">Click **Properties**.</span></span>  
  
6. <span data-ttu-id="f150c-125">在 連接埠**型別**清單中，選取正確的連接埠。</span><span class="sxs-lookup"><span data-stu-id="f150c-125">In the port **Type** list, select the correct port.</span></span>  
  
7. <span data-ttu-id="f150c-126">按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="f150c-126">Click **Configure**.</span></span>  
  
8. <span data-ttu-id="f150c-127">在 [ **WCF [**<em>傳輸類型</em>**] 傳輸屬性**] 對話方塊中，按一下 [**繫結**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="f150c-127">In the **WCF [**<em>transport type</em>**] Transport Properties** dialog box, click the **Binding** tab.</span></span>  
  
9. <span data-ttu-id="f150c-128">在 **交易**區段中，選擇**啟用交易**選項。</span><span class="sxs-lookup"><span data-stu-id="f150c-128">In the **Transactions** section, choose the **Enable transactions** option.</span></span>  
  
10. <span data-ttu-id="f150c-129">在 **交易通訊協定**下拉式清單中，選擇**OleTransactions**或是**WSAtomicTransactions**。</span><span class="sxs-lookup"><span data-stu-id="f150c-129">In the **Transactions protocol** drop-down list, choose either **OleTransactions** or **WSAtomicTransactions**.</span></span>  
  
    <span data-ttu-id="f150c-130">這些步驟只適用於下列傳輸類型：</span><span class="sxs-lookup"><span data-stu-id="f150c-130">These steps only apply to the following transport types:</span></span>  
  
-   <span data-ttu-id="f150c-131">Custom</span><span class="sxs-lookup"><span data-stu-id="f150c-131">Custom</span></span>  
  
-   <span data-ttu-id="f150c-132">CustomIsolated</span><span class="sxs-lookup"><span data-stu-id="f150c-132">CustomIsolated</span></span>  
  
-   <span data-ttu-id="f150c-133">NetNamedPipe</span><span class="sxs-lookup"><span data-stu-id="f150c-133">NetNamedPipe</span></span>  
  
-   <span data-ttu-id="f150c-134">NetTcp</span><span class="sxs-lookup"><span data-stu-id="f150c-134">NetTcp</span></span>  
  
-   <span data-ttu-id="f150c-135">WShttp</span><span class="sxs-lookup"><span data-stu-id="f150c-135">WShttp</span></span>