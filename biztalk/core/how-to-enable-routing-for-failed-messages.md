---
title: 如何啟用的路由失敗訊息 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d33beed4-1ae2-4282-95ac-5d68aab7fb5d
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8bfa76ba9378bc2177b31fac085b603971232840
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22254110"
---
# <a name="how-to-enable-routing-for-failed-messages"></a><span data-ttu-id="8bccc-102">如何啟用失敗訊息的路由</span><span class="sxs-lookup"><span data-stu-id="8bccc-102">How to Enable Routing for Failed Messages</span></span>
<span data-ttu-id="8bccc-103">失敗訊息路由是傳送埠和接收埠的屬性，啟用方式是在連接埠的屬性頁指定 [啟用失敗訊息的路由]。</span><span class="sxs-lookup"><span data-stu-id="8bccc-103">Failed message routing is a property of send and receive ports, and is enabled by indicating "Enable routing for failed messages" on the port's property page.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8bccc-104">接收埠的組態會套用到與該接收埠相關聯的所有接收位置。</span><span class="sxs-lookup"><span data-stu-id="8bccc-104">The configuration on a receive port applies to all receive locations associated with that receive port.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8bccc-105">傳送埠的組態會同時套用到主要傳輸和備份傳輸。</span><span class="sxs-lookup"><span data-stu-id="8bccc-105">The configuration on a send port applies to both the primary and backup transports.</span></span>  
  
### <a name="to-configure-failed-message-routing-for-a-receive-port-this-applies-to-both-one-way-and-request-response-receive-ports"></a><span data-ttu-id="8bccc-106">若要設定接收埠的失敗訊息路由 (此程序適用於單向及雙向要求-回應接收埠)</span><span class="sxs-lookup"><span data-stu-id="8bccc-106">To configure failed message routing for a receive port (this applies to both one-way and request-response receive ports)</span></span>  
  
1.  <span data-ttu-id="8bccc-107">開啟 BizTalk Server 管理主控台。</span><span class="sxs-lookup"><span data-stu-id="8bccc-107">Open the BizTalk Server Administration console.</span></span>  
  
2.  <span data-ttu-id="8bccc-108">展開[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]**管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，然後展開 傳送埠所屬的應用程式。</span><span class="sxs-lookup"><span data-stu-id="8bccc-108">Expand [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, expand **BizTalk Group**, expand **Applications**, and then expand the application to which the send port belongs.</span></span>  
  
3.  <span data-ttu-id="8bccc-109">按一下**接收埠**資料夾。</span><span class="sxs-lookup"><span data-stu-id="8bccc-109">Click the **Receive Ports** folder.</span></span>  
  
4.  <span data-ttu-id="8bccc-110">在右邊窗格中，按兩下您要設定的接收埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="8bccc-110">In the right pane, double-click the name of the receive port you want to configure.</span></span>  
  
5.  <span data-ttu-id="8bccc-111">在接收埠屬性 頁面上，在左窗格中，選取**一般**類別目錄。</span><span class="sxs-lookup"><span data-stu-id="8bccc-111">On the receive port's property page, in the left pane, select the **General** category.</span></span>  
  
6.  <span data-ttu-id="8bccc-112">在右窗格中，選取**啟用的路由失敗訊息**核取方塊，然後**套用**。</span><span class="sxs-lookup"><span data-stu-id="8bccc-112">In the right pane, select the **Enable routing for failed messages** check box, and then click **Apply**.</span></span>  
  
### <a name="to-configure-failed-message-routing-for-a-send-port-this-applies-only-to-static-one-way-and-static-solicit-response-send-ports"></a><span data-ttu-id="8bccc-113">若要設定傳送埠的失敗訊息路由 (此程序只適用於靜態單向及靜態雙向請求-回應傳送埠)</span><span class="sxs-lookup"><span data-stu-id="8bccc-113">To configure failed message routing for a send port (this applies only to static one-way and static solicit-response send ports)</span></span>  
  
1.  <span data-ttu-id="8bccc-114">開啟 BizTalk Server 管理主控台。</span><span class="sxs-lookup"><span data-stu-id="8bccc-114">Open the BizTalk Server Administration console.</span></span>  
  
2.  <span data-ttu-id="8bccc-115">展開[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]**管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，然後展開 傳送埠所屬的應用程式。</span><span class="sxs-lookup"><span data-stu-id="8bccc-115">Expand [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, expand **BizTalk Group**, expand **Applications**, and then expand the application to which the send port belongs.</span></span>  
  
3.  <span data-ttu-id="8bccc-116">按一下**傳送埠**資料夾。</span><span class="sxs-lookup"><span data-stu-id="8bccc-116">Click the **Send Ports** folder.</span></span>  
  
4.  <span data-ttu-id="8bccc-117">在右邊窗格中，按兩下您要設定的傳送埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="8bccc-117">In the right pane, double-click the name of the send port you want to configure.</span></span>  
  
5.  <span data-ttu-id="8bccc-118">在傳送埠屬性 頁面上，在左窗格中，選取**傳輸進階選項**類別目錄。</span><span class="sxs-lookup"><span data-stu-id="8bccc-118">On the send port's property page, in the left pane, select the **Transport Advanced Options** category.</span></span>  
  
6.  <span data-ttu-id="8bccc-119">在右窗格中，在**傳輸選項**群組方塊中，選取**啟用的路由失敗訊息**核取方塊，然後**套用**。</span><span class="sxs-lookup"><span data-stu-id="8bccc-119">In the right pane, in the **Transport Options** group box, select the **Enable routing for failed messages** check box, and then click **Apply**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bccc-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8bccc-120">See Also</span></span>  
 [<span data-ttu-id="8bccc-121">錯誤處理</span><span class="sxs-lookup"><span data-stu-id="8bccc-121">Error Handling</span></span>](../core/error-handling.md)