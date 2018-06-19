---
title: 新增警示 頁面 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0023ee8d-a0d1-4257-95c6-38c95060bd62
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aa93a777481c905dbedfffe5e7675335c4aec40b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22290422"
---
# <a name="add-alert-page"></a><span data-ttu-id="1d60a-102">[新增警示] 頁面</span><span class="sxs-lookup"><span data-stu-id="1d60a-102">Add Alert Page</span></span>
<span data-ttu-id="1d60a-103">圖 1 顯示 新增警示頁面上，您可以在其中建立新的警示在入口網站將會引發當符合警示中指定的準則 （條件） 的錯誤訊息抵達入口網站。</span><span class="sxs-lookup"><span data-stu-id="1d60a-103">Figure 1 shows the Add Alert page, where you can create a new alert that the portal will raise when a fault message matching the criteria (conditions) specified in the alert arrives at the portal.</span></span>  
  
 <span data-ttu-id="1d60a-104">![新增警示 頁面](../esb-toolkit/media/ch8-addalertpage.gif "Ch8 AddAlertPage")</span><span class="sxs-lookup"><span data-stu-id="1d60a-104">![Add Alert Page](../esb-toolkit/media/ch8-addalertpage.gif "Ch8-AddAlertPage")</span></span>  
  
 <span data-ttu-id="1d60a-105">**圖 1**</span><span class="sxs-lookup"><span data-stu-id="1d60a-105">**Figure 1**</span></span>  
  
 <span data-ttu-id="1d60a-106">**ESB Management 入口網站新增警示 頁面**</span><span class="sxs-lookup"><span data-stu-id="1d60a-106">**The ESB Management Portal Add Alert page**</span></span>  
  
 <span data-ttu-id="1d60a-107">您可以在新增警示 頁面上，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="1d60a-107">On the Add Alert page, you can do the following:</span></span>  
  
-   <span data-ttu-id="1d60a-108">輸入新的警示中的名稱**輸入警示名稱**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="1d60a-108">Type a name for the new alert in the **Enter Alert Name** text box.</span></span>  
  
-   <span data-ttu-id="1d60a-109">指定警示將會符合的傳入例外狀況中的欄位值的方式**加入此警示的條件**本頁一節。</span><span class="sxs-lookup"><span data-stu-id="1d60a-109">Specify how the alert will match to values of the fields in incoming exceptions in the **Add conditions for this alert** section of this page.</span></span> <span data-ttu-id="1d60a-110">從例外狀況的結構描述中選取欄位 (例如**應用程式、 錯誤類型**或**錯誤嚴重性)** 中**準則**下拉式清單，選取比較型別 （例如與 =， **！ =、 > =、 < =、** 或**像**) 中**運算子**下拉式清單，並輸入或選取第三個清單中的值。</span><span class="sxs-lookup"><span data-stu-id="1d60a-110">Select a field from the exception schema (such as **Application, Error Type,** or **Fault Severity)** in the **Criteria** drop-down list; select a comparison type for the (such as =, **!=, >=, <=,** or **like**) in the **Operator** drop-down list; and type or select a value from the third list.</span></span> <span data-ttu-id="1d60a-111">當您選取的例外狀況欄位，**值**控制項變更為 [文字] 方塊或下拉式清單，以輸入或選取相符的值。</span><span class="sxs-lookup"><span data-stu-id="1d60a-111">When you select an exception field, the **Value** control changes to either a text box or a drop-down list for you to enter or select a matching value.</span></span>  
  
-   <span data-ttu-id="1d60a-112">選取或輸入準則值之後, 按**新增**連結加入到清單中的這種狀況**條件**的頁面上，重複上述步驟，加入任何您需要這項警示的更多條件區段.</span><span class="sxs-lookup"><span data-stu-id="1d60a-112">After selecting or entering the criteria values, click the **Add** link to add this condition to the list in the **Conditions** section of the page, and repeat to add any more conditions you require for this alert.</span></span>  
  
-   <span data-ttu-id="1d60a-113">按一下**儲存**按鈕以建立新的警示名稱與您指定的條件。</span><span class="sxs-lookup"><span data-stu-id="1d60a-113">Click the **Save** button to create the new alert with the name and conditions you specified.</span></span>