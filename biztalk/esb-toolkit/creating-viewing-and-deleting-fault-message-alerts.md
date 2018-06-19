---
title: 建立、 檢視和刪除錯誤訊息通知 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 59df2b40-b42c-4167-873c-0819839919da
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 55894eca1baa8ca6616c67f623a87e8015a2f32f
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25974444"
---
# <a name="creating-viewing-and-deleting-fault-message-alerts"></a><span data-ttu-id="b8e41-102">建立、 檢視和刪除錯誤訊息的警示</span><span class="sxs-lookup"><span data-stu-id="b8e41-102">Creating, Viewing, and Deleting Fault Message Alerts</span></span>
<span data-ttu-id="b8e41-103">ESB 管理入口網站可以產生警示，當錯誤訊息抵達入口網站中，指定警示的準則為基礎的訊息中的值的比較。</span><span class="sxs-lookup"><span data-stu-id="b8e41-103">The ESB Management Portal can generate alerts when fault messages arrive at the portal, based on a comparison of values in the message with criteria specified for the alert.</span></span> <span data-ttu-id="b8e41-104">在入口網站也可以維護一份通知連結到個別警示的使用者，並主動便會產生警示時，它會通知這些使用者。</span><span class="sxs-lookup"><span data-stu-id="b8e41-104">The portal can also maintain a list of notifications linked to individual alerts and users, and it will notify these users when it proactively raises alerts.</span></span>  
  
### <a name="to-create-and-configure-a-new-alert"></a><span data-ttu-id="b8e41-105">若要建立及設定新的警示</span><span class="sxs-lookup"><span data-stu-id="b8e41-105">To create and configure a new alert</span></span>  
  
1.  <span data-ttu-id="b8e41-106">開啟[入口網站 [警示] 頁面](../esb-toolkit/portal-alerts-page.md)查看現有警示的清單，這些警示您目前訂閱。</span><span class="sxs-lookup"><span data-stu-id="b8e41-106">Open the [Portal Alerts Page](../esb-toolkit/portal-alerts-page.md) to see a list of existing alerts and your current subscriptions to these alerts.</span></span>  
  
2.  <span data-ttu-id="b8e41-107">按一下**建立警示**連結可開啟[新增警示 頁面](../esb-toolkit/add-alert-page.md)。</span><span class="sxs-lookup"><span data-stu-id="b8e41-107">Click the **Create Alert** link to open the [Add Alert Page](../esb-toolkit/add-alert-page.md).</span></span>  
  
3.  <span data-ttu-id="b8e41-108">在**輸入警示名稱** 文字方塊中，輸入新警示的名稱。</span><span class="sxs-lookup"><span data-stu-id="b8e41-108">In the **Enter Alert Name** text box, type a name for the new alert.</span></span>  
  
4.  <span data-ttu-id="b8e41-109">在**條件**區段的 新增警示 頁面上，選取一個欄位 (例如**應用程式**，**錯誤類型**，或**錯誤嚴重性**) 中**準則**下拉式清單; 請選取 比較類型 (例如 +、 =、 ！ =、 > =、 < =、 或**像**) 中**運算子**下拉式清單，並輸入或選取從清單或文字的第三個方塊的值 (名為**值**)。</span><span class="sxs-lookup"><span data-stu-id="b8e41-109">In the **Conditions** section of the Add Alert page, select a field (such as **Application**, **Error Type**, or **Fault Severity**) in the **Criteria** drop-down list; select a comparison type (such as +, =, !=, >=, <=, or **like**) in the **Operator** drop-down list; and type or select a value from the third list or text box (named **Value**).</span></span> <span data-ttu-id="b8e41-110">當您選取**準則**值相符的值的下拉式清單或文字方塊中顯示的頁面上變更。</span><span class="sxs-lookup"><span data-stu-id="b8e41-110">As you select a **Criteria** value, the page changes to display either a text box or a drop-down list for the matching value.</span></span> <span data-ttu-id="b8e41-111">所有的條件會組合使用**AND**運算子。</span><span class="sxs-lookup"><span data-stu-id="b8e41-111">All conditions are combined using the **AND** operator.</span></span>  
  
5.  <span data-ttu-id="b8e41-112">按一下**新增**連結新增至清單中，這種狀況，然後重複上述步驟，視需要新增更多條件。</span><span class="sxs-lookup"><span data-stu-id="b8e41-112">Click the **Add** link to add this condition to the list, and then repeat the previous step to add more conditions if required.</span></span>  
  
6.  <span data-ttu-id="b8e41-113">按一下**儲存**按鈕以建立新的警示，具有指定的名稱和條件。</span><span class="sxs-lookup"><span data-stu-id="b8e41-113">Click the **Save** button to create a new alert with the specified name and conditions.</span></span>  
  
### <a name="to-view-details-of-an-existing-alert-or-delete-an-existing-alert"></a><span data-ttu-id="b8e41-114">若要檢視現有警示的詳細資料，或刪除現有的警示</span><span class="sxs-lookup"><span data-stu-id="b8e41-114">To view details of an existing alert or delete an existing alert</span></span>  
  
1.  <span data-ttu-id="b8e41-115">開啟[入口網站 [警示] 頁面](../esb-toolkit/portal-alerts-page.md)。</span><span class="sxs-lookup"><span data-stu-id="b8e41-115">Open the [Portal Alerts Page](../esb-toolkit/portal-alerts-page.md).</span></span>  
  
2.  <span data-ttu-id="b8e41-116">若要刪除警示，請按一下**刪除警示**現有警示的 [動作] 欄中的圖示。</span><span class="sxs-lookup"><span data-stu-id="b8e41-116">To delete an alert, click the **Delete Alert** icon in the Action column of an existing alert.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b8e41-117">非系統管理使用者可以刪除只有警示他們是擁有者，以及其目前沒有任何訂閱者。</span><span class="sxs-lookup"><span data-stu-id="b8e41-117">Non-administrative users can delete only alerts for which they are an owner, and for which there are currently no subscribers.</span></span> <span data-ttu-id="b8e41-118">您必須刪除其他警示系統管理員身分來登入入口網站。</span><span class="sxs-lookup"><span data-stu-id="b8e41-118">You must log on to the portal as an administrator to delete other alerts.</span></span>  
  
3.  <span data-ttu-id="b8e41-119">若要檢視警示的詳細資訊，請按一下**檢視**現有警示的 [動作] 欄中的圖示。</span><span class="sxs-lookup"><span data-stu-id="b8e41-119">To view details of an alert, click the **View** icon in the Action column of an existing alert.</span></span> <span data-ttu-id="b8e41-120">這會開啟 [警示檢視器] 頁面。</span><span class="sxs-lookup"><span data-stu-id="b8e41-120">This opens the Alert Viewer page.</span></span>  
  
4.  <span data-ttu-id="b8e41-121">按一下**匯出至 Excel**下載的格式，您可以在 Microsoft Excel 中檢視警示的完整清單。</span><span class="sxs-lookup"><span data-stu-id="b8e41-121">Click **Export To Excel** to download the complete list of alerts in a format that you can view in Microsoft Excel.</span></span>