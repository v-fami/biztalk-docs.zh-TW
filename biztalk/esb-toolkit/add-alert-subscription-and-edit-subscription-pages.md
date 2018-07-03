---
title: 新增警示的訂用帳戶和編輯訂閱頁面 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ad5e99f1-714e-458b-b5f0-85ac69be5335
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1b843bde8905d8b6803dda56a6370f70c934a610
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37013447"
---
# <a name="add-alert-subscription-and-edit-subscription-pages"></a><span data-ttu-id="d96d5-102">新增警示的訂用帳戶和編輯訂閱頁面</span><span class="sxs-lookup"><span data-stu-id="d96d5-102">Add Alert Subscription and Edit Subscription Pages</span></span>
<span data-ttu-id="d96d5-103">新增警示的訂用帳戶 和 編輯訂用帳戶頁面很類似。</span><span class="sxs-lookup"><span data-stu-id="d96d5-103">The Add Alert Subscription and Edit Subscription pages are similar.</span></span> <span data-ttu-id="d96d5-104">它們的差異在於 [編輯訂用帳戶] 頁面顯示的訂閱者識別碼 （目前的入口網站使用者的 Microsoft Windows 帳戶），並有一組不同的按鈕。</span><span class="sxs-lookup"><span data-stu-id="d96d5-104">They differ in that the Edit Subscription page shows the subscriber ID (the Microsoft Windows account of the current portal user), and has a different set of buttons.</span></span> <span data-ttu-id="d96d5-105">圖 1 顯示 新增警示的訂用帳戶 和 編輯訂用帳戶頁面。</span><span class="sxs-lookup"><span data-stu-id="d96d5-105">Figure 1 shows the Add Alert Subscription and Edit Subscription pages.</span></span>  

 <span data-ttu-id="d96d5-106">![新增警示編輯訂閱](../esb-toolkit/media/ch8-addalerteditsubscription.gif "Ch8 AddAlertEditSubscription")</span><span class="sxs-lookup"><span data-stu-id="d96d5-106">![Add Alert Edit Subscription](../esb-toolkit/media/ch8-addalerteditsubscription.gif "Ch8-AddAlertEditSubscription")</span></span>  

 <span data-ttu-id="d96d5-107">**圖 1**</span><span class="sxs-lookup"><span data-stu-id="d96d5-107">**Figure 1**</span></span>  

 <span data-ttu-id="d96d5-108">**ESB 管理入口網站新增警示的訂用帳戶 和 編輯訂用帳戶頁面**</span><span class="sxs-lookup"><span data-stu-id="d96d5-108">**The ESB Management Portal Add Alert Subscription and Edit Subscription pages**</span></span>  

 <span data-ttu-id="d96d5-109">新增警示的訂用帳戶 和 編輯訂用帳戶頁面可讓您指定，並修改下列：</span><span class="sxs-lookup"><span data-stu-id="d96d5-109">The Add Alert Subscription and Edit Subscription pages allow you to specify and modify the following:</span></span>  

- <span data-ttu-id="d96d5-110">若要使用的訂用帳戶 （而不是您的 Microsoft Windows 帳戶電子郵件地址） 的自訂的電子郵件地址</span><span class="sxs-lookup"><span data-stu-id="d96d5-110">A custom e-mail address to use for the subscription (instead of your Microsoft Windows account e-mail address)</span></span>  

- <span data-ttu-id="d96d5-111">當您將會接受警示通知的時間週期</span><span class="sxs-lookup"><span data-stu-id="d96d5-111">The time period when you will accept alert notifications</span></span>  

- <span data-ttu-id="d96d5-112">事件，例如假期"黑色 out"期間</span><span class="sxs-lookup"><span data-stu-id="d96d5-112">A "black-out" period for events such as vacations</span></span>  

- <span data-ttu-id="d96d5-113">透過入口網站不會傳送重複的警示間隔</span><span class="sxs-lookup"><span data-stu-id="d96d5-113">The interval over which the portal will not send duplicate alerts</span></span>  

  <span data-ttu-id="d96d5-114">您可以在 新增警示的訂用帳戶 和 編輯訂用帳戶頁面上：</span><span class="sxs-lookup"><span data-stu-id="d96d5-114">You can do the following on the Add Alert Subscription and Edit Subscription pages:</span></span>  

- <span data-ttu-id="d96d5-115">選取此核取方塊旁**自訂的電子郵件**文字方塊，如果您想要用於您標準 Windows 帳戶的電子郵件地址，以不同的訂用帳戶的電子郵件地址，然後在文字方塊中輸入慣用的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="d96d5-115">Select the check box next to the **Custom Email** text box if you want to use an e-mail address for the subscription that is different to your standard Windows account e-mail address, and then type the preferred e-mail address in the text box.</span></span>  

- <span data-ttu-id="d96d5-116">選取頂端的核取方塊**排程**區段，如果您想要指定的期間，入口網站應該將警示傳送給您，並接著指定之期間的開始和結束時間時**開始時間**和**結束時間**下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="d96d5-116">Select the check box at the top of the **Schedule** section if you want to specify a period when the portal should send alerts to you, and then specify the start and end times for the period in the **Start Time** and **End Time** drop-down lists.</span></span> <span data-ttu-id="d96d5-117">這段期間外發生的警示已排入佇列，並傳遞指定的期間。</span><span class="sxs-lookup"><span data-stu-id="d96d5-117">Alerts occurring outside this period are queued and delivered during the specified period.</span></span>  

- <span data-ttu-id="d96d5-118">輸入開始日期和結束日期**瑪莉亞期間**是否的期間，當您將無法接收和處理警示。</span><span class="sxs-lookup"><span data-stu-id="d96d5-118">Type the start date and end date for a **Black-out Period** if there is a period when you will be unable to receive and act on alerts.</span></span> <span data-ttu-id="d96d5-119">使用兩個日期的格式為 mm/dd/yyyy。</span><span class="sxs-lookup"><span data-stu-id="d96d5-119">Use the format mm/dd/yyyy for the two dates.</span></span>  

- <span data-ttu-id="d96d5-120">選取 **間隔**中**分鐘**期間入口網站會比較引發的警示，並將只有一個傳送多個執行個體的相同警示發生時。</span><span class="sxs-lookup"><span data-stu-id="d96d5-120">Select an **Interval** in **Minutes** during which the portal will compare alerts raised and send only one when multiple instances of the same alert occur.</span></span> <span data-ttu-id="d96d5-121">這可防止建立大量的相同警示訊息快速出現的錯誤。</span><span class="sxs-lookup"><span data-stu-id="d96d5-121">This prevents a rapidly occurring fault from creating a large number of identical alert messages.</span></span>  

- <span data-ttu-id="d96d5-122">按一下 **儲存**按鈕來建立或更新訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="d96d5-122">Click the **Save** button to create or update the subscription.</span></span>  

- <span data-ttu-id="d96d5-123">按一下 **刪除**按鈕 （僅適用於 編輯訂用帳戶 頁面），以刪除選取的訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="d96d5-123">Click the **Delete** button (available only on the Edit Subscription page) to delete the selected subscription.</span></span>  

- <span data-ttu-id="d96d5-124">按一下 **取消**按鈕以返回[警示檢視器頁面](../esb-toolkit/alert-viewer-page.md)而不需要建立或修改訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="d96d5-124">Click the **Cancel** button to go back to the [Alert Viewer Page](../esb-toolkit/alert-viewer-page.md) without creating or modifying the subscription.</span></span>
