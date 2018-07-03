---
title: 入口網站警示頁面 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 131b4750-ce3d-445f-be0e-6bf499734c69
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 252da9de050c228a7b2d8a4f549d2d084e2a2f81
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36978703"
---
# <a name="portal-alerts-page"></a><span data-ttu-id="ca469-102">[入口網站警示] 頁面</span><span class="sxs-lookup"><span data-stu-id="ca469-102">Portal Alerts Page</span></span>
<span data-ttu-id="ca469-103">[圖 1] 顯示包含兩個區段的 [警示] 頁面：</span><span class="sxs-lookup"><span data-stu-id="ca469-103">Figure 1 shows the Alerts page, which contains two sections:</span></span>  

- <span data-ttu-id="ca469-104">主要的區段會顯示連結，以建立新的警示和現有的警示清單。</span><span class="sxs-lookup"><span data-stu-id="ca469-104">The main section displays a link to create a new alert and a list of existing alerts.</span></span> <span data-ttu-id="ca469-105">每個警示有對應的連結，可讓您訂閱警示。</span><span class="sxs-lookup"><span data-stu-id="ca469-105">Each alert has a corresponding link that allows you to subscribe to the alert.</span></span> <span data-ttu-id="ca469-106">您也可以按一下 檢視警示的詳細資料、 建立新的訂用帳戶的警示，以及刪除警示的 動作 欄中的圖示。</span><span class="sxs-lookup"><span data-stu-id="ca469-106">You can also click the icons in the Action column to view details of the alert, create a new subscription for the alert, and delete the alert.</span></span>  

- <span data-ttu-id="ca469-107">**我的訂用帳戶**區段會顯示您已在入口網站中定義的訂用帳戶的清單。</span><span class="sxs-lookup"><span data-stu-id="ca469-107">The **My Subscriptions** section displays a list of subscriptions you have defined within the portal.</span></span> <span data-ttu-id="ca469-108">您可以編輯，並取消訂閱您現有的訂用帳戶使用這份清單中的連結。</span><span class="sxs-lookup"><span data-stu-id="ca469-108">You can edit and unsubscribe your existing subscriptions using the links in this list.</span></span>  

  <span data-ttu-id="ca469-109">![入口網站警示頁面](../esb-toolkit/media/ch8-portalalertspage.gif "Ch8 PortalAlertsPage")</span><span class="sxs-lookup"><span data-stu-id="ca469-109">![Portal Alerts Page](../esb-toolkit/media/ch8-portalalertspage.gif "Ch8-PortalAlertsPage")</span></span>  

  <span data-ttu-id="ca469-110">**圖 1**</span><span class="sxs-lookup"><span data-stu-id="ca469-110">**Figure 1**</span></span>  

  <span data-ttu-id="ca469-111">**ESB 管理入口網站警示頁面**</span><span class="sxs-lookup"><span data-stu-id="ca469-111">**The ESB Management Portal Alerts page**</span></span>  

  <span data-ttu-id="ca469-112">ESB 警示服務會產生警示準則為根據您指定符合的例外狀況中的值在 ESB 管理入口網站所顯示的送達。</span><span class="sxs-lookup"><span data-stu-id="ca469-112">The ESB Alert Service generates alerts based on criteria you specify that match the values in exceptions as they arrive at the ESB Management Portal.</span></span> <span data-ttu-id="ca469-113">您可以比對，並比較各種精確地控制例外狀況的警示會比對每個可能的例外狀況類型的欄位。</span><span class="sxs-lookup"><span data-stu-id="ca469-113">You can match and compare a range of fields in an exception to control accurately which alerts will match each possible type of exception.</span></span> <span data-ttu-id="ca469-114">在入口網站也可讓您建立對應至您所定義的警示不同類型的訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="ca469-114">The portal also allows you to create subscriptions that map to the different types of alerts you define.</span></span> <span data-ttu-id="ca469-115">相符的警示發生時，這些訂用帳戶可以通知使用者。</span><span class="sxs-lookup"><span data-stu-id="ca469-115">These subscriptions can notify users when the matching alert occurs.</span></span>  

  <span data-ttu-id="ca469-116">下列清單說明如何使用 ESB 管理入口網站警示頁面的功能：</span><span class="sxs-lookup"><span data-stu-id="ca469-116">The following list explains how you can use the features of the ESB Management Portal Alerts page:</span></span>  

- <span data-ttu-id="ca469-117">若要建立新的警示，請按一下**建立警示**頁面，即可開啟 [新增警示] 頁面頂端的連結。</span><span class="sxs-lookup"><span data-stu-id="ca469-117">To create a new alert, click the **Create Alert** link at the top of the page to open the Add Alert page.</span></span>  

- <span data-ttu-id="ca469-118">若要檢視或編輯現有的警示，按一下 [警示] 頁面的主要區段中的 [動作] 欄中的放大鏡圖示。</span><span class="sxs-lookup"><span data-stu-id="ca469-118">To view or edit an existing alert, click the magnifying glass icon in the Action column for the alert in the main section of the page.</span></span> <span data-ttu-id="ca469-119">這會開啟[警示檢視器頁面](../esb-toolkit/alert-viewer-page.md)。</span><span class="sxs-lookup"><span data-stu-id="ca469-119">This opens the [Alert Viewer Page](../esb-toolkit/alert-viewer-page.md).</span></span>  

- <span data-ttu-id="ca469-120">若要訂閱現有的警示，按一下 新增訂用帳戶圖示以開啟警示旁邊的 [動作] 欄[新增警示訂閱和編輯訂閱頁面](../esb-toolkit/add-alert-subscription-and-edit-subscription-pages.md)。</span><span class="sxs-lookup"><span data-stu-id="ca469-120">To subscribe to an existing alert, click the new subscription icon the Action column next to the alert to open the [Add Alert Subscription and Edit Subscription Pages](../esb-toolkit/add-alert-subscription-and-edit-subscription-pages.md).</span></span>  

- <span data-ttu-id="ca469-121">如果您使用上的選項以系統管理員身分開啟此頁面**系統管理員**索引標籤功能表 (而不是從**警示** 索引標籤)，您可以按一下叉記號圖示旁邊的任何警示清單中的 動作 欄刪除警示和任何連結的訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="ca469-121">If you opened this page as an administrator using the options on the **Admin** tab menu (instead of from the **Alerts** tab), you can click the cross mark icon the Action column next to any of the alerts in the list to delete the alert and any linked subscriptions.</span></span>  

- <span data-ttu-id="ca469-122">若要編輯現有的訂用帳戶，請按一下**編輯**旁邊的清單中該訂用帳戶的連結**我的訂用帳戶**以開啟頁面的區段[新增警示的訂用帳戶並編輯訂用帳戶頁面](../esb-toolkit/add-alert-subscription-and-edit-subscription-pages.md)。</span><span class="sxs-lookup"><span data-stu-id="ca469-122">To edit an existing subscription, click the **Edit** link next to that subscription in the list in the **My Subscriptions** section of the page to open the [Add Alert Subscription and Edit Subscription Pages](../esb-toolkit/add-alert-subscription-and-edit-subscription-pages.md).</span></span>  

- <span data-ttu-id="ca469-123">若要移除現有的訂用帳戶，請按一下**Unsubscribe**旁邊的清單中該訂用帳戶的連結**我的訂用帳戶**頁面區段。</span><span class="sxs-lookup"><span data-stu-id="ca469-123">To remove an existing subscription, click the **Unsubscribe** link next to that subscription in the list in the **My Subscriptions** section of the page.</span></span>  

- <span data-ttu-id="ca469-124">若要將整個清單的警示匯出至 Microsoft Excel，按一下**匯出至 Excel**。</span><span class="sxs-lookup"><span data-stu-id="ca469-124">To export the entire list of alerts to Microsoft Excel, click **Export to Excel**.</span></span>
