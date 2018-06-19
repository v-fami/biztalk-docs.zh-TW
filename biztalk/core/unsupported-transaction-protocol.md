---
title: 不支援的交易通訊協定 |Microsoft 文件
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
ms.openlocfilehash: 3e000c706ca438494f8b07e8ce5dba24cb4f46bd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22286886"
---
# <a name="unsupported-transaction-protocol"></a><span data-ttu-id="f57d4-102">不支援的交易通訊協定</span><span class="sxs-lookup"><span data-stu-id="f57d4-102">Unsupported transaction protocol</span></span>
## <a name="details"></a><span data-ttu-id="f57d4-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f57d4-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f57d4-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="f57d4-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="f57d4-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="f57d4-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="f57d4-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="f57d4-106">Event ID</span></span>|<span data-ttu-id="f57d4-107">0</span><span class="sxs-lookup"><span data-stu-id="f57d4-107">0</span></span>|  
|<span data-ttu-id="f57d4-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="f57d4-108">Event Source</span></span>|<span data-ttu-id="f57d4-109">0</span><span class="sxs-lookup"><span data-stu-id="f57d4-109">0</span></span>|  
|<span data-ttu-id="f57d4-110">元件</span><span class="sxs-lookup"><span data-stu-id="f57d4-110">Component</span></span>|<span data-ttu-id="f57d4-111">0</span><span class="sxs-lookup"><span data-stu-id="f57d4-111">0</span></span>|  
|<span data-ttu-id="f57d4-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="f57d4-112">Symbolic Name</span></span>|<span data-ttu-id="f57d4-113">0</span><span class="sxs-lookup"><span data-stu-id="f57d4-113">0</span></span>|  
|<span data-ttu-id="f57d4-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="f57d4-114">Message Text</span></span>|<span data-ttu-id="f57d4-115">不支援的交易通訊協定： {0}</span><span class="sxs-lookup"><span data-stu-id="f57d4-115">Unsupported transaction protocol: {0}</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f57d4-116">說明</span><span class="sxs-lookup"><span data-stu-id="f57d4-116">Explanation</span></span>  
 <span data-ttu-id="f57d4-117">當接收位置或傳送埠的交易通訊協定屬性設定為無效值時，就會發生此錯誤。</span><span class="sxs-lookup"><span data-stu-id="f57d4-117">This error occurs when the transaction protocol property of a receive location or send port is set to an invalid value.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f57d4-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="f57d4-118">User Action</span></span>  
 <span data-ttu-id="f57d4-119">若要解決這個錯誤，請執行下列一個或多個動作：</span><span class="sxs-lookup"><span data-stu-id="f57d4-119">To resolve this error, do one or more of the following:</span></span>  
  
1.  <span data-ttu-id="f57d4-120">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="f57d4-120">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="f57d4-121">在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="f57d4-121">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3.  <span data-ttu-id="f57d4-122">找出您的應用程式，然後再找出您的傳輸。</span><span class="sxs-lookup"><span data-stu-id="f57d4-122">Locate your application and then locate your transport.</span></span>  
  
4.  <span data-ttu-id="f57d4-123">以滑鼠右鍵按一下傳輸名稱。</span><span class="sxs-lookup"><span data-stu-id="f57d4-123">Right-click the transport name.</span></span>  
  
5.  <span data-ttu-id="f57d4-124">按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="f57d4-124">Click **Properties**.</span></span>  
  
6.  <span data-ttu-id="f57d4-125">在 連接埠**類型**清單中，選取正確的連接埠。</span><span class="sxs-lookup"><span data-stu-id="f57d4-125">In the port **Type** list, select the correct port.</span></span>  
  
7.  <span data-ttu-id="f57d4-126">按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="f57d4-126">Click **Configure**.</span></span>  
  
8.  <span data-ttu-id="f57d4-127">在**WCF [***傳輸類型***] 傳輸屬性**對話方塊中，按一下 [**繫結**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="f57d4-127">In the **WCF [***transport type***] Transport Properties** dialog box, click the **Binding** tab.</span></span>  
  
9. <span data-ttu-id="f57d4-128">在**交易**區段中，選擇**啟用交易**選項。</span><span class="sxs-lookup"><span data-stu-id="f57d4-128">In the **Transactions** section, choose the **Enable transactions** option.</span></span>  
  
10. <span data-ttu-id="f57d4-129">在**交易通訊協定**下拉式清單中選擇  **OleTransactions**或**WSAtomicTransactions**。</span><span class="sxs-lookup"><span data-stu-id="f57d4-129">In the **Transactions protocol** drop-down list, choose either **OleTransactions** or **WSAtomicTransactions**.</span></span>  
  
 <span data-ttu-id="f57d4-130">這些步驟僅適用於下列傳輸類型：</span><span class="sxs-lookup"><span data-stu-id="f57d4-130">These steps only apply to the following transport types:</span></span>  
  
-   <span data-ttu-id="f57d4-131">Custom</span><span class="sxs-lookup"><span data-stu-id="f57d4-131">Custom</span></span>  
  
-   <span data-ttu-id="f57d4-132">CustomIsolated</span><span class="sxs-lookup"><span data-stu-id="f57d4-132">CustomIsolated</span></span>  
  
-   <span data-ttu-id="f57d4-133">NetNamedPipe</span><span class="sxs-lookup"><span data-stu-id="f57d4-133">NetNamedPipe</span></span>  
  
-   <span data-ttu-id="f57d4-134">NetTcp</span><span class="sxs-lookup"><span data-stu-id="f57d4-134">NetTcp</span></span>  
  
-   <span data-ttu-id="f57d4-135">WShttp</span><span class="sxs-lookup"><span data-stu-id="f57d4-135">WShttp</span></span>