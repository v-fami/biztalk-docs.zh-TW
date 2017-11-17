---
title: "訂閱警示 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cfa46b63-c1c7-47cd-86b0-557fd322dc8f
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 02ef5f136002f5afca6e062362b92d25a20baa99
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="subscribing-to-alerts"></a><span data-ttu-id="72c6b-102">訂閱警示</span><span class="sxs-lookup"><span data-stu-id="72c6b-102">Subscribing to Alerts</span></span>
### <a name="to-subscribe-to-an-alert"></a><span data-ttu-id="72c6b-103">若要訂閱警示</span><span class="sxs-lookup"><span data-stu-id="72c6b-103">To subscribe to an alert</span></span>  
  
1.  <span data-ttu-id="72c6b-104">開啟[入口網站 [警示] 頁面](../esb-toolkit/portal-alerts-page.md)查看現有警示的清單，這些警示您目前訂閱。</span><span class="sxs-lookup"><span data-stu-id="72c6b-104">Open the [Portal Alerts Page](../esb-toolkit/portal-alerts-page.md) to see a list of existing alerts and your current subscriptions to these alerts.</span></span>  
  
2.  <span data-ttu-id="72c6b-105">在 [動作] 欄中，按一下**AddSubscriber**現有警示的圖示。</span><span class="sxs-lookup"><span data-stu-id="72c6b-105">In the Action column, click the **AddSubscriber** icon for an existing alert.</span></span> <span data-ttu-id="72c6b-106">這會開啟[新增警示訂閱和編輯訂閱頁面](../esb-toolkit/add-alert-subscription-and-edit-subscription-pages.md)。</span><span class="sxs-lookup"><span data-stu-id="72c6b-106">This opens the [Add Alert Subscription and Edit Subscription Pages](../esb-toolkit/add-alert-subscription-and-edit-subscription-pages.md).</span></span>  
  
3.  <span data-ttu-id="72c6b-107">在入口網站會傳送警示通知給您用來存取入口網站的帳戶相關聯的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="72c6b-107">The portal sends alert notifications to the e-mail address associated with the account you use to access the portal.</span></span> <span data-ttu-id="72c6b-108">如果您想要使用不同的電子郵件地址，選取核取方塊旁的 **自訂電子郵件**文字方塊中，然後輸入慣用的電子郵件地址，在文字方塊中。</span><span class="sxs-lookup"><span data-stu-id="72c6b-108">If you want to use a different e-mail address, select the check box next to the **Custom Email** text box, and then type the preferred e-mail address in the text box.</span></span>  
  
4.  <span data-ttu-id="72c6b-109">選取核取方塊，在**排程**區段，如果您想要指定當入口網站應該會將警示傳送給您，，然後指定 之期間的開始和結束時間週期**開始時間**和**EndTime**下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="72c6b-109">Select the check box in the **Schedule** section if you want to specify a period when the portal should send alerts to you, and then specify the start and end times for the period in the **Start Time** and **EndTime** drop-down lists.</span></span>  
  
5.  <span data-ttu-id="72c6b-110">如果有週期，當您將無法接收和處理警示，請輸入中的開始和結束日期**黑色逾時**方塊。</span><span class="sxs-lookup"><span data-stu-id="72c6b-110">If there is a period when you will be unable to receive and act upon alerts, type the start and end dates in the **Black-out Period** boxes.</span></span>  
  
6.  <span data-ttu-id="72c6b-111">選取**間隔**中**分鐘**期間的入口網站會比較產生的警示，並傳送一個多個執行個體的相同警示發生時。</span><span class="sxs-lookup"><span data-stu-id="72c6b-111">Select an **Interval** in **Minutes** during which the portal will compare alerts raised and send only one when multiple instances of the same alert occur.</span></span> <span data-ttu-id="72c6b-112">這樣可避免建立大量的相同警示訊息快速所發生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="72c6b-112">This prevents a rapidly occurring fault from creating a large number of identical alert messages.</span></span>  
  
7.  <span data-ttu-id="72c6b-113">按一下**儲存**按鈕以建立新的訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="72c6b-113">Click the **Save** button to create the new subscription.</span></span>  
  
### <a name="to-edit-an-existing-alert-subscription"></a><span data-ttu-id="72c6b-114">若要編輯現有的警示訂閱</span><span class="sxs-lookup"><span data-stu-id="72c6b-114">To edit an existing alert subscription</span></span>  
  
1.  <span data-ttu-id="72c6b-115">開啟[入口網站 [警示] 頁面](../esb-toolkit/portal-alerts-page.md)查看現有警示的清單，這些警示您目前訂閱。</span><span class="sxs-lookup"><span data-stu-id="72c6b-115">Open the [Portal Alerts Page](../esb-toolkit/portal-alerts-page.md) to see a list of existing alerts and your current subscriptions to these alerts.</span></span>  
  
2.  <span data-ttu-id="72c6b-116">按一下**編輯**您想要修改的清單中的訂用帳戶旁的連結**我的訂閱**開啟頁面區段[新增警示訂閱和編輯訂閱頁面](../esb-toolkit/add-alert-subscription-and-edit-subscription-pages.md).</span><span class="sxs-lookup"><span data-stu-id="72c6b-116">Click the **Edit** link next to the subscription you want to modify in the list in the **My Subscriptions** section of the page to open the [Add Alert Subscription and Edit Subscription Pages](../esb-toolkit/add-alert-subscription-and-edit-subscription-pages.md).</span></span>  
  
3.  <span data-ttu-id="72c6b-117">在入口網站會傳送警示通知給您用來存取入口網站的帳戶相關聯的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="72c6b-117">The portal sends alert notifications to the e-mail address associated with the account you use to access the portal.</span></span> <span data-ttu-id="72c6b-118">如果您想要使用不同的電子郵件地址，選取核取方塊旁的 **自訂電子郵件**文字方塊中，然後輸入慣用的電子郵件地址，在文字方塊中。</span><span class="sxs-lookup"><span data-stu-id="72c6b-118">If you want to use a different e-mail address, select the check box next to the **Custom Email** text box, and then type the preferred e-mail address in the text box.</span></span>  
  
4.  <span data-ttu-id="72c6b-119">選取核取方塊，在**排程**區段，如果您想要指定當入口網站應該會將警示傳送給您，，然後指定 之期間的開始和結束時間週期**開始時間**和**EndTime**下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="72c6b-119">Select the check box in the **Schedule** section if you want to specify a period when the portal should send alerts to you, and then specify the start and end times for the period in the **Start Time** and **EndTime** drop-down lists.</span></span>  
  
5.  <span data-ttu-id="72c6b-120">輸入的開始和結束日期**黑色逾時**是否有的週期，當您將無法接收和處理警示。</span><span class="sxs-lookup"><span data-stu-id="72c6b-120">Type the start and end dates for a **Black-out Period** if there is a period when you will be unable to receive and act upon alerts.</span></span>  
  
6.  <span data-ttu-id="72c6b-121">選取**間隔**中**分鐘**期間的入口網站會比較產生的警示，並將只有一個發生時，傳送多個執行個體的相同警示。</span><span class="sxs-lookup"><span data-stu-id="72c6b-121">Select an **Interval** in **Minutes** during which the portal will compare alerts raised and will send only one when multiple instances of the same alert occur.</span></span> <span data-ttu-id="72c6b-122">這樣可避免建立大量的相同警示訊息快速所發生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="72c6b-122">This prevents a rapidly occurring fault from creating a large number of identical alert messages.</span></span>  
  
7.  <span data-ttu-id="72c6b-123">按一下**儲存**更新訂用帳戶 按鈕。</span><span class="sxs-lookup"><span data-stu-id="72c6b-123">Click the **Save** button to update the subscription.</span></span>  
  
### <a name="to-delete-an-existing-alert-subscription"></a><span data-ttu-id="72c6b-124">若要刪除現有的警示訂閱</span><span class="sxs-lookup"><span data-stu-id="72c6b-124">To delete an existing alert subscription</span></span>  
  
1.  <span data-ttu-id="72c6b-125">開啟[入口網站 [警示] 頁面](../esb-toolkit/portal-alerts-page.md)查看現有警示的清單，這些警示您目前訂閱。</span><span class="sxs-lookup"><span data-stu-id="72c6b-125">Open the [Portal Alerts Page](../esb-toolkit/portal-alerts-page.md) to see a list of existing alerts and your current subscriptions to these alerts.</span></span>  
  
2.  <span data-ttu-id="72c6b-126">按一下**刪除**您想要刪除的清單中的訂用帳戶旁的連結**我的訂閱**頁面區段。</span><span class="sxs-lookup"><span data-stu-id="72c6b-126">Click the **Delete** link next to the subscription you want to delete in the list in the **My Subscriptions** section of the page.</span></span>