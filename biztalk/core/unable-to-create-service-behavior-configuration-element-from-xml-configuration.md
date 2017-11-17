---
title: "無法從 XML 組態建立服務行為組態項目 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6732e5d2-bb4b-48ec-af59-467eede80f36
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 830391eca955c3a3381cb780df0c01e114ceda2f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="unable-to-create-service-behavior-configuration-element-from-xml-configuration"></a><span data-ttu-id="cf7b5-102">無法從 XML 組態建立服務行為組態項目</span><span class="sxs-lookup"><span data-stu-id="cf7b5-102">Unable to create service behavior configuration element from XML configuration</span></span>
## <a name="details"></a><span data-ttu-id="cf7b5-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="cf7b5-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cf7b5-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="cf7b5-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="cf7b5-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="cf7b5-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="cf7b5-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="cf7b5-106">Event ID</span></span>|<span data-ttu-id="cf7b5-107">0</span><span class="sxs-lookup"><span data-stu-id="cf7b5-107">0</span></span>|  
|<span data-ttu-id="cf7b5-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="cf7b5-108">Event Source</span></span>|<span data-ttu-id="cf7b5-109">0</span><span class="sxs-lookup"><span data-stu-id="cf7b5-109">0</span></span>|  
|<span data-ttu-id="cf7b5-110">元件</span><span class="sxs-lookup"><span data-stu-id="cf7b5-110">Component</span></span>|<span data-ttu-id="cf7b5-111">0</span><span class="sxs-lookup"><span data-stu-id="cf7b5-111">0</span></span>|  
|<span data-ttu-id="cf7b5-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="cf7b5-112">Symbolic Name</span></span>|<span data-ttu-id="cf7b5-113">0</span><span class="sxs-lookup"><span data-stu-id="cf7b5-113">0</span></span>|  
|<span data-ttu-id="cf7b5-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="cf7b5-114">Message Text</span></span>|<span data-ttu-id="cf7b5-115">無法從 XML 組態建立服務行為組態項目。</span><span class="sxs-lookup"><span data-stu-id="cf7b5-115">Unable to create service behavior configuration element from XML configuration.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="cf7b5-116">說明</span><span class="sxs-lookup"><span data-stu-id="cf7b5-116">Explanation</span></span>  
 <span data-ttu-id="cf7b5-117">此錯誤表示配接器未載入服務行為組態。</span><span class="sxs-lookup"><span data-stu-id="cf7b5-117">This error indicates the adapter did not load the service behavior configuration.</span></span> <span data-ttu-id="cf7b5-118">主要是搭配 Wcf-custom 和 Wcf-customisolated 配接器，就會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="cf7b5-118">This situation occurs primarily with the WCF-Custom and WCF-CustomIsolated adapters.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="cf7b5-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="cf7b5-119">User Action</span></span>  
 <span data-ttu-id="cf7b5-120">您可以使用下列程序來設定服務行為。</span><span class="sxs-lookup"><span data-stu-id="cf7b5-120">Use the following procedure to configure the service behavior.</span></span>  
  
#### <a name="to-configure-the-service-behavior"></a><span data-ttu-id="cf7b5-121">若要設定服務行為</span><span class="sxs-lookup"><span data-stu-id="cf7b5-121">To configure the service behavior</span></span>  
  
1.  <span data-ttu-id="cf7b5-122">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="cf7b5-122">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="cf7b5-123">在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="cf7b5-123">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3.  <span data-ttu-id="cf7b5-124">找出您的應用程式，然後再找出您的傳輸。</span><span class="sxs-lookup"><span data-stu-id="cf7b5-124">Locate your application and then locate your transport.</span></span>  
  
4.  <span data-ttu-id="cf7b5-125">以滑鼠右鍵按一下傳輸名稱。</span><span class="sxs-lookup"><span data-stu-id="cf7b5-125">Right-click the transport name.</span></span>  
  
5.  <span data-ttu-id="cf7b5-126">按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="cf7b5-126">Click **Properties**.</span></span>  
  
6.  <span data-ttu-id="cf7b5-127">在 連接埠**類型**清單中，選取正確的連接埠。</span><span class="sxs-lookup"><span data-stu-id="cf7b5-127">In the port **Type** list, select the correct port.</span></span>  
  
7.  <span data-ttu-id="cf7b5-128">按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="cf7b5-128">Click **Configure**.</span></span>  
  
8.  <span data-ttu-id="cf7b5-129">在**WCF [***傳輸類型***] 傳輸屬性**對話方塊中，按一下 [**行為**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="cf7b5-129">In the **WCF [***transport type***] Transport Properties** dialog box, click the **Behavior** tab.</span></span>  
  
9. <span data-ttu-id="cf7b5-130">在**行為**區段中，按一下**ServiceBehavior**組態。</span><span class="sxs-lookup"><span data-stu-id="cf7b5-130">In the **Behavior** section, check the **ServiceBehavior** configuration.</span></span>