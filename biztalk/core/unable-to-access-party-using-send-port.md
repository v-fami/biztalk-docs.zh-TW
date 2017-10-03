---
title: "無法存取合作對象使用傳送埠 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ffacba77-76e8-4f03-be26-134a9999d6c1
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2aa582319226b114720ef234b8e3f65e416a94d1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="unable-to-access-party-using-send-port"></a><span data-ttu-id="d1edc-102">無法存取合作對象使用傳送埠</span><span class="sxs-lookup"><span data-stu-id="d1edc-102">Unable to access party using send port</span></span>
## <a name="details"></a><span data-ttu-id="d1edc-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d1edc-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d1edc-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="d1edc-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="d1edc-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="d1edc-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="d1edc-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d1edc-106">Event ID</span></span>|-|  
|<span data-ttu-id="d1edc-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="d1edc-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="d1edc-108">EDI</span><span class="sxs-lookup"><span data-stu-id="d1edc-108"> EDI</span></span>|  
|<span data-ttu-id="d1edc-109">元件</span><span class="sxs-lookup"><span data-stu-id="d1edc-109">Component</span></span>|<span data-ttu-id="d1edc-110">AS2 引擎</span><span class="sxs-lookup"><span data-stu-id="d1edc-110">AS2 Engine</span></span>|  
|<span data-ttu-id="d1edc-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="d1edc-111">Symbolic Name</span></span>|<span data-ttu-id="d1edc-112">UnableToLocateAS2PartyBySendPortNameError</span><span class="sxs-lookup"><span data-stu-id="d1edc-112">UnableToLocateAS2PartyBySendPortNameError</span></span>|  
|<span data-ttu-id="d1edc-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="d1edc-113">Message Text</span></span>|<span data-ttu-id="d1edc-114">無法存取合作對象使用傳送埠： {0}</span><span class="sxs-lookup"><span data-stu-id="d1edc-114">Unable to access party using send port: {0}</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d1edc-115">說明</span><span class="sxs-lookup"><span data-stu-id="d1edc-115">Explanation</span></span>  
 <span data-ttu-id="d1edc-116">此錯誤表示傳送管線找不到指定相關聯的合作對象傳送外寄 AS2 訊息的連接埠。</span><span class="sxs-lookup"><span data-stu-id="d1edc-116">This error indicates the send pipeline could not find a party associated with the specified send port for the outgoing AS2 message.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d1edc-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="d1edc-117">User Action</span></span>  
 <span data-ttu-id="d1edc-118">若要解決這個錯誤，請將合作對象與指定的傳送埠產生關聯：</span><span class="sxs-lookup"><span data-stu-id="d1edc-118">To resolve this error, associate a party with the specified send port:</span></span>  
  
1.  <span data-ttu-id="d1edc-119">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="d1edc-119">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="d1edc-120">在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後按一下**合作對象**。</span><span class="sxs-lookup"><span data-stu-id="d1edc-120">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and click **Parties**.</span></span>  
  
3.  <span data-ttu-id="d1edc-121">以滑鼠右鍵按一下正確的合作對象。</span><span class="sxs-lookup"><span data-stu-id="d1edc-121">Right-click the correct party.</span></span>  
  
4.  <span data-ttu-id="d1edc-122">按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="d1edc-122">Click **Properties**.</span></span>  
  
5.  <span data-ttu-id="d1edc-123">在 [*合作對象名稱*]**合作對象屬性**] 對話方塊的左窗格中，按一下 [**傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="d1edc-123">In the [*party name*] **Party Properties** dialog box, in the left pane, click **Send Ports**.</span></span>  
  
6.  <span data-ttu-id="d1edc-124">輸入傳送埠名稱，在**傳送埠**清單。</span><span class="sxs-lookup"><span data-stu-id="d1edc-124">Enter the Send port name in the **Send Ports** list.</span></span>  
  
7.  <span data-ttu-id="d1edc-125">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="d1edc-125">Click **OK**.</span></span>