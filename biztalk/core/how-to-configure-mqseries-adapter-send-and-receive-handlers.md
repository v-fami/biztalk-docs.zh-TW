---
title: 如何設定 MQSeries 配接器傳送和接收處理常式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- receive handlers, MQSeries adapters
- configuring [MQSeries adapters], receive handlers
- MQSeries adapters, send handlers
- MQSeries adapters, receive handlers
- send handlers, MQSeries adapters
- configuring [MQSeries adapters], send handlers
ms.assetid: e1cfc415-50d2-440b-9301-ad69da28ad3e
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 88c97b109146dadd1a5cc90710f00c9c8f6620f8
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36988895"
---
# <a name="how-to-configure-mqseries-adapter-send-and-receive-handlers"></a><span data-ttu-id="1d29a-102">如何設定 MQSeries 配接器傳送和接收處理常式</span><span class="sxs-lookup"><span data-stu-id="1d29a-102">How to Configure MQSeries Adapter Send and Receive Handlers</span></span>
<span data-ttu-id="1d29a-103">您可以透過 [BizTalk Server 管理] 主控台，為 MQSeries 配接器的傳送與接收處理常式設定一些屬性。</span><span class="sxs-lookup"><span data-stu-id="1d29a-103">You can configure some properties for the send and receive handlers for the MQSeries adapter through the BizTalk Server Administration console.</span></span> <span data-ttu-id="1d29a-104">此程序中所述[如何設定 MQSeries 配接器接收位置和傳送埠](../core/how-to-configure-mqseries-adapter-receive-locations-and-send-ports.md)建立大多數傳送處理常式屬性的值。</span><span class="sxs-lookup"><span data-stu-id="1d29a-104">The process described in [How to Configure MQSeries Adapter Receive Locations and Send Ports](../core/how-to-configure-mqseries-adapter-receive-locations-and-send-ports.md) establishes the values for the majority of send handler properties.</span></span>  

## <a name="to-configure-the-send-and-receive-handlers"></a><span data-ttu-id="1d29a-105">設定傳送與接收處理常式</span><span class="sxs-lookup"><span data-stu-id="1d29a-105">To configure the send and receive handlers</span></span>  
 <span data-ttu-id="1d29a-106">請依照下列步驟執行，設定 MSQeries 配接器的傳送和接收處理常式：</span><span class="sxs-lookup"><span data-stu-id="1d29a-106">Follow these steps to configure send and receive handlers for the MSQeries adapter:</span></span>  

1. <span data-ttu-id="1d29a-107">按一下 **開始**，指向**程式**，指向[!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="1d29a-107">Click **Start**, point to **Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  

2. <span data-ttu-id="1d29a-108">在 BizTalk Server 管理主控台中，依序展開**BizTalk Server 管理]**，展開**BizTalk 群組**，按一下以展開**平台設定**，然後按一下 [以依序展開**配接器**。</span><span class="sxs-lookup"><span data-stu-id="1d29a-108">In the BizTalk Server Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, click to expand **Platform Settings**, and then click to expand **Adapters**.</span></span>  

3. <span data-ttu-id="1d29a-109">在展開的配接器清單中，選取**MQSeries**。</span><span class="sxs-lookup"><span data-stu-id="1d29a-109">In the expanded adapter list, select **MQSeries**.</span></span> <span data-ttu-id="1d29a-110">繫結至 MQSeries 配接器的傳送與接收處理常式清單會顯示在右窗格中。</span><span class="sxs-lookup"><span data-stu-id="1d29a-110">The list of send and receive handlers that are bound to the MQSeries adapter appear in the right pane.</span></span>  

4. <span data-ttu-id="1d29a-111">在右窗格中，按兩下傳送或接收處理常式。</span><span class="sxs-lookup"><span data-stu-id="1d29a-111">In the right pane, double-click a send or receive handler in the right pane.</span></span>  

5. <span data-ttu-id="1d29a-112">在 [**配接器處理常式屬性**] 對話方塊中，按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="1d29a-112">In the **Adapter Handler Properties** dialog box, click **Properties**.</span></span>  

6. <span data-ttu-id="1d29a-113">在  **MQSeries 傳輸屬性**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="1d29a-113">In the **MQSeries Transport Properties** dialog box, do the following:</span></span>  


   |           <span data-ttu-id="1d29a-114">使用</span><span class="sxs-lookup"><span data-stu-id="1d29a-114">Use this</span></span>            |                                    <span data-ttu-id="1d29a-115">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="1d29a-115">To do this</span></span>                                    |
   |-------------------------------|----------------------------------------------------------------------------------|
   | <span data-ttu-id="1d29a-116">**批次中的訊息上限**</span><span class="sxs-lookup"><span data-stu-id="1d29a-116">**Maximum Messages in Batch**</span></span> | <span data-ttu-id="1d29a-117">設定批次中的訊息數目上限。</span><span class="sxs-lookup"><span data-stu-id="1d29a-117">Set the maximum number of messages in a batch.</span></span> <span data-ttu-id="1d29a-118">只適用於傳送處理常式。</span><span class="sxs-lookup"><span data-stu-id="1d29a-118">Applies only to the send handler.</span></span> |
   |          <span data-ttu-id="1d29a-119">**Server**</span><span class="sxs-lookup"><span data-stu-id="1d29a-119">**Server**</span></span>           |      <span data-ttu-id="1d29a-120">執行 MQSeries Server for Windows 的電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="1d29a-120">The name of the computer that is running MQSeries Server for Windows.</span></span>       |


7. <span data-ttu-id="1d29a-121">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="1d29a-121">Click **OK**.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="1d29a-122">[接收位置] 與 [傳送埠] 屬性會覆寫 [接收處理常式] 與 [傳送處理常式] 值。</span><span class="sxs-lookup"><span data-stu-id="1d29a-122">The Receive Location and Send Port properties override the Receive Handler and Send Handler values.</span></span> <span data-ttu-id="1d29a-123">若 [接收位置] 或 [傳送埠] 屬性沒有值，配接器會分別使用 [接收處理常式] 與 [傳送處理常式] 值。</span><span class="sxs-lookup"><span data-stu-id="1d29a-123">If there is no value for the Receive Location or Send Port properties, the adapter uses the Receive Handler and Send Handler values respectively.</span></span>  

8. <span data-ttu-id="1d29a-124">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="1d29a-124">Click **OK**.</span></span>  

## <a name="see-also"></a><span data-ttu-id="1d29a-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1d29a-125">See Also</span></span>  
 <span data-ttu-id="1d29a-126">[如何設定 MQSeries 配接器接收位置和傳送埠](../core/how-to-configure-mqseries-adapter-receive-locations-and-send-ports.md) </span><span class="sxs-lookup"><span data-stu-id="1d29a-126">[How to Configure MQSeries Adapter Receive Locations and Send Ports](../core/how-to-configure-mqseries-adapter-receive-locations-and-send-ports.md) </span></span>  
 [<span data-ttu-id="1d29a-127">設定 MQSeries 配接器</span><span class="sxs-lookup"><span data-stu-id="1d29a-127">Configuring the MQSeries Adapter</span></span>](../core/configuring-the-mqseries-adapter.md)