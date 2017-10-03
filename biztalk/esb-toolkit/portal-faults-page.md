---
title: "入口網站錯誤網頁 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b11e3492-da1a-43f3-acf8-3775b5cbc2c5
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 294ba24516cccbf6c15ada26d28f169a6eb45c98
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="portal-faults-page"></a><span data-ttu-id="009de-102">入口網站的錯誤頁面</span><span class="sxs-lookup"><span data-stu-id="009de-102">Portal Faults Page</span></span>
<span data-ttu-id="009de-103">圖 1 顯示錯誤頁面。</span><span class="sxs-lookup"><span data-stu-id="009de-103">Figure 1 shows the Faults page.</span></span> <span data-ttu-id="009de-104">此頁面會顯示每個錯誤的主要屬性，並提供排序和篩選的準則，例如錯誤類型和時間範圍內支援的錯誤詳細的分析的功能。</span><span class="sxs-lookup"><span data-stu-id="009de-104">This page displays the main properties of each fault, and it provides sorting and filtering capabilities that support detailed analysis of faults over a range of criteria, such as error type and time.</span></span> <span data-ttu-id="009de-105">每個錯誤的連結可讓您在錯誤訊息檢視器中檢視更多詳細資料。</span><span class="sxs-lookup"><span data-stu-id="009de-105">A link for each fault allows you to view more details in the Fault Message Viewer.</span></span>  
  
 <span data-ttu-id="009de-106">![FaultsPage](../esb-toolkit/media/faultspage.gif "FaultsPage")</span><span class="sxs-lookup"><span data-stu-id="009de-106">![FaultsPage](../esb-toolkit/media/faultspage.gif "FaultsPage")</span></span>  
  
 <span data-ttu-id="009de-107">**圖 1**</span><span class="sxs-lookup"><span data-stu-id="009de-107">**Figure 1**</span></span>  
  
 <span data-ttu-id="009de-108">**ESB 管理入口網站的 [錯誤] 頁面**</span><span class="sxs-lookup"><span data-stu-id="009de-108">**The Faults page of the ESB Management Portal**</span></span>  
  
 <span data-ttu-id="009de-109">下列清單說明如何使用 ESB Management 入口網站錯誤網頁的功能：</span><span class="sxs-lookup"><span data-stu-id="009de-109">The following list explains how you can use the features of the ESB Management Portal Faults page:</span></span>  
  
-   <span data-ttu-id="009de-110">若要篩選的頁面中所顯示的錯誤清單，請使用下拉式清單和清單上方的文字方塊中的錯誤。</span><span class="sxs-lookup"><span data-stu-id="009de-110">To filter the list of faults displayed in the page, use the drop-down lists and text boxes above the list of faults.</span></span> <span data-ttu-id="009de-111">您可以篩選以下列方式顯示的資料列：</span><span class="sxs-lookup"><span data-stu-id="009de-111">You can filter the rows displayed in the following ways:</span></span>  
  
    -   <span data-ttu-id="009de-112">選取已安裝的 BizTalk 應用程式中的任一**應用程式**下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="009de-112">Select any one of the installed BizTalk applications in the **Application** drop-down list.</span></span>  
  
    -   <span data-ttu-id="009de-113">指定在錯誤發生選取的週期**小時、 天、 週、 月、 季、 年、**或**所有**中**擷取內最後一個記錄**下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="009de-113">Specify the period within which the fault occurred by selecting **hour, day, week, month, quarter, year,** or **all** in the **Retrieve records within last** drop-down list.</span></span>  
  
    -   <span data-ttu-id="009de-114">指定您想要顯示在頁面上的資料列數目**記錄每頁**下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="009de-114">Specify how many rows you want to display on the page in the **Records Per Page** drop-down list.</span></span>  
  
    -   <span data-ttu-id="009de-115">錯誤的程式碼中輸入號碼**錯誤碼**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="009de-115">Type a fault code number in the **Fault Code** text box.</span></span>  
  
    -   <span data-ttu-id="009de-116">輸入全部或部分中的錯誤類別目錄名稱**錯誤類別目錄**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="009de-116">Type all or part of the fault category name in the **Fault Category** text box.</span></span>  
  
    -   <span data-ttu-id="009de-117">輸入全部或部分中的錯誤類型文字**錯誤類型**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="009de-117">Type all or part of the error type text in the **Error Type** text box.</span></span>  
  
    -   <span data-ttu-id="009de-118">輸入最小和/或最大錯誤嚴重性的值 (例如**警告、 錯誤、 嚴重，**或**重大**) 中**Min 錯誤嚴重性**和**最大錯誤嚴重性**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="009de-118">Type a value for the minimum and/or maximum fault severity (such as **Warning, Error, Severe,** or **Critical**) in the **Min Fault Severity** and **Max Fault Severity** text boxes.</span></span>  
  
-   <span data-ttu-id="009de-119">您可以指定值的一個或多個控制項之後，請按一下**套用篩選器**按鈕以套用指定的準則。</span><span class="sxs-lookup"><span data-stu-id="009de-119">After you specify the values for one or more of these controls, click the **Apply Filters** button to apply all the specified criteria.</span></span>  
  
-   <span data-ttu-id="009de-120">按一下資料行標題，顯示錯誤訊息的資料列順序該資料行的內容，並再按一次以反向順序顯示的清單。</span><span class="sxs-lookup"><span data-stu-id="009de-120">Click a column heading to display the fault message rows in the order of that column contents, and then click again to display the list in reverse order.</span></span>  
  
-   <span data-ttu-id="009de-121">若要顯示在清單中，顯示錯誤的更多詳細資料或編輯，再重新送出它包含的訊息，請按一下任何位置中將它開啟該錯誤的資料列中[入口網站錯誤訊息檢視器](../esb-toolkit/portal-fault-message-viewer.md)。</span><span class="sxs-lookup"><span data-stu-id="009de-121">To display more details of a fault shown in the list, or to edit and resubmit the message it contains, click anywhere in the row for that fault to open it in the [Portal Fault Message Viewer](../esb-toolkit/portal-fault-message-viewer.md).</span></span>