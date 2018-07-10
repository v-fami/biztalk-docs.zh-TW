---
title: 無法從 XML 設定建立端點行為組態項目 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 89d906a4-ea85-42d8-8e9e-0a3a7774bcd8
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0d1f014463bbbd12de856d20b37332c912b3ce22
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36987239"
---
# <a name="unable-to-create-endpoint-behavior-configuration-element-from-xml-configuration"></a><span data-ttu-id="57581-102">無法從 XML 設定建立端點行為組態項目</span><span class="sxs-lookup"><span data-stu-id="57581-102">Unable to create endpoint behavior configuration element from XML configuration</span></span>
## <a name="details"></a><span data-ttu-id="57581-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="57581-103">Details</span></span>  

|                 |                                                                                    |
|-----------------|------------------------------------------------------------------------------------|
|  <span data-ttu-id="57581-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="57581-104">Product Name</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| <span data-ttu-id="57581-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="57581-105">Product Version</span></span> |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    <span data-ttu-id="57581-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="57581-106">Event ID</span></span>     |                                         <span data-ttu-id="57581-107">0</span><span class="sxs-lookup"><span data-stu-id="57581-107">0</span></span>                                          |
|  <span data-ttu-id="57581-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="57581-108">Event Source</span></span>   |                                         <span data-ttu-id="57581-109">0</span><span class="sxs-lookup"><span data-stu-id="57581-109">0</span></span>                                          |
|    <span data-ttu-id="57581-110">元件</span><span class="sxs-lookup"><span data-stu-id="57581-110">Component</span></span>    |                                         <span data-ttu-id="57581-111">0</span><span class="sxs-lookup"><span data-stu-id="57581-111">0</span></span>                                          |
|  <span data-ttu-id="57581-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="57581-112">Symbolic Name</span></span>  |                                         <span data-ttu-id="57581-113">0</span><span class="sxs-lookup"><span data-stu-id="57581-113">0</span></span>                                          |
|  <span data-ttu-id="57581-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="57581-114">Message Text</span></span>   |  <span data-ttu-id="57581-115">無法從 XML 設定建立端點行為組態項目</span><span class="sxs-lookup"><span data-stu-id="57581-115">Unable to create endpoint behavior configuration element from XML configuration</span></span>   |

## <a name="explanation"></a><span data-ttu-id="57581-116">說明</span><span class="sxs-lookup"><span data-stu-id="57581-116">Explanation</span></span>  
 <span data-ttu-id="57581-117">此錯誤表示配接器未載入的端點行為組態。</span><span class="sxs-lookup"><span data-stu-id="57581-117">This error indicates the adapter did not load the endpoint behavior configuration.</span></span> <span data-ttu-id="57581-118">主要使用 Wcf-custom 和 Wcf-customisolated 配接器，就會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="57581-118">This situation occurs primarily with the WCF-Custom and WCF-CustomIsolated adapters.</span></span>  

## <a name="user-action"></a><span data-ttu-id="57581-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="57581-119">User Action</span></span>  
 <span data-ttu-id="57581-120">您可以使用下列程序來設定的端點行為。</span><span class="sxs-lookup"><span data-stu-id="57581-120">Use the following procedure to configure the endpoint behavior.</span></span>  

#### <a name="to-configure-the-endpoint-behavior"></a><span data-ttu-id="57581-121">若要設定的端點行為</span><span class="sxs-lookup"><span data-stu-id="57581-121">To configure the endpoint behavior</span></span>  

1. <span data-ttu-id="57581-122">按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理]**。</span><span class="sxs-lookup"><span data-stu-id="57581-122">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  

2. <span data-ttu-id="57581-123">在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="57581-123">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.</span></span>  

3. <span data-ttu-id="57581-124">找出您的應用程式，然後找出您的傳輸。</span><span class="sxs-lookup"><span data-stu-id="57581-124">Locate your application and then locate your transport.</span></span>  

4. <span data-ttu-id="57581-125">以滑鼠右鍵按一下傳輸名稱。</span><span class="sxs-lookup"><span data-stu-id="57581-125">Right-click the transport name.</span></span>  

5. <span data-ttu-id="57581-126">按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="57581-126">Click **Properties**.</span></span>  

6. <span data-ttu-id="57581-127">在 連接埠**型別**清單中，選取正確的連接埠。</span><span class="sxs-lookup"><span data-stu-id="57581-127">In the port **Type** list, select the correct port.</span></span>  

7. <span data-ttu-id="57581-128">按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="57581-128">Click **Configure**.</span></span>  

8. <span data-ttu-id="57581-129">在 [ **WCF [**<em>傳輸類型</em>**] 傳輸屬性**] 對話方塊中，按一下 [**行為**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="57581-129">In the **WCF [**<em>transport type</em>**] Transport Properties** dialog box, click the **Behavior** tab.</span></span>  

9. <span data-ttu-id="57581-130">在 **行為**區段中，按一下**endpointbehavior**組態。</span><span class="sxs-lookup"><span data-stu-id="57581-130">In the **Behavior** section, check the **EndpointBehavior** configuration.</span></span>
