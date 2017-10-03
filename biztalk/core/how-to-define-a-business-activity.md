---
title: "如何定義商務活動 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- business activities, creating [Excel add-in]
- monitoring business activities [BAM], creating business activities [Excel add-in]
- monitoring business activities [BAM], Excel add-in
ms.assetid: 305e3718-46b4-45df-bd52-f7ae36621576
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 74cb0bb6f2bd0a5f92f6029dda65d55d219bcc12
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-define-a-business-activity"></a><span data-ttu-id="77751-102">如何定義商務活動</span><span class="sxs-lookup"><span data-stu-id="77751-102">How to Define a Business Activity</span></span>
<span data-ttu-id="77751-103">若要指示您必須為報告收集的資料，則必須定義 BAM 活動。</span><span class="sxs-lookup"><span data-stu-id="77751-103">To indicate the data you need to collect for reports, you must define a BAM activity.</span></span> <span data-ttu-id="77751-104">這個定義包含您想要 BAM 追蹤的重要里程碑及資料項目的清單。請使用 BAM Excel 增益集來建立活動，如下列程序所示。</span><span class="sxs-lookup"><span data-stu-id="77751-104">This contains a list of the important milestones and data items you want BAM to track. Use the BAM Excel add-in to create an activity as shown in the following procedure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="77751-105">一旦部署活動之後，可在活動上採取的動作便會受到限制。</span><span class="sxs-lookup"><span data-stu-id="77751-105">Once an activity has been deployed, the actions you can take on an activity become restricted.</span></span> <span data-ttu-id="77751-106">特別是，您不可以從活動刪除項目，除非您準備請系統管理員解除部署整個 BAM 活動和檢視集，然後再重新部署。</span><span class="sxs-lookup"><span data-stu-id="77751-106">Specifically, you cannot delete items from an activity unless you are prepared to have your administrator undeploy the entire BAM activity and view sets and then redeploy them.</span></span> <span data-ttu-id="77751-107">這樣可能會造成暫時看不見資料或資料遺失，除非系統管理員執行資料備份與還原。</span><span class="sxs-lookup"><span data-stu-id="77751-107">This can cause an interruption of visibility and loss of data unless the administrator does a backup and restore of the data.</span></span>  
  
### <a name="to-create-a-business-activity"></a><span data-ttu-id="77751-108">建立商務活動</span><span class="sxs-lookup"><span data-stu-id="77751-108">To create a business activity</span></span>  
  
1.  <span data-ttu-id="77751-109">開啟 Microsoft Excel。</span><span class="sxs-lookup"><span data-stu-id="77751-109">Open Microsoft Excel.</span></span>  
  
2.  <span data-ttu-id="77751-110">在功能表的工具列上，按一下**BAM**功能表項目，然後按一下**BAM 活動**。</span><span class="sxs-lookup"><span data-stu-id="77751-110">On the menu tool bar, click the **BAM** menu item, and click **BAM Activity**.</span></span>  
  
     <span data-ttu-id="77751-111">**商務活動監控活動精靈**隨即出現。</span><span class="sxs-lookup"><span data-stu-id="77751-111">The **Business Activity Monitoring Activity Wizard** appears.</span></span>  
  
3.  <span data-ttu-id="77751-112">按一下**新活動**。</span><span class="sxs-lookup"><span data-stu-id="77751-112">Click **New Activity**.</span></span>  
  
     <span data-ttu-id="77751-113">**新活動** 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="77751-113">The **New Activity** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="77751-114">輸入之活動的描述性名稱**活動名稱**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="77751-114">Type a descriptive name for the activity in the **Activity Name** text box.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="77751-115">活動必須包含至少一個活動項目。</span><span class="sxs-lookup"><span data-stu-id="77751-115">An activity must contain at least one activity item.</span></span>  
  
#### <a name="to-create-a-new-item"></a><span data-ttu-id="77751-116">建立新項目</span><span class="sxs-lookup"><span data-stu-id="77751-116">To create a new item</span></span>  
  
1.  <span data-ttu-id="77751-117">按一下**新項目**。</span><span class="sxs-lookup"><span data-stu-id="77751-117">Click **New Item**.</span></span>  
  
2.  <span data-ttu-id="77751-118">在**新增活動項目**對話方塊中，於**新增活動項目**方塊中，輸入活動項目的描述性名稱。</span><span class="sxs-lookup"><span data-stu-id="77751-118">In the **New Activity Item** dialog box, in the **New Activity Item** box, type a descriptive name for the activity item.</span></span>  
  
3.  <span data-ttu-id="77751-119">從**項目類型**下拉式功能表，選取此項目的類型。</span><span class="sxs-lookup"><span data-stu-id="77751-119">From the **Item type** drop-down menu, select a type for this item.</span></span> <span data-ttu-id="77751-120">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="77751-120">Possible values include:</span></span>  
  
    |<span data-ttu-id="77751-121">項目類型</span><span class="sxs-lookup"><span data-stu-id="77751-121">Item type</span></span>|<span data-ttu-id="77751-122">Description</span><span class="sxs-lookup"><span data-stu-id="77751-122">Description</span></span>|  
    |---------------|-----------------|  
    |<span data-ttu-id="77751-123">商務里程碑</span><span class="sxs-lookup"><span data-stu-id="77751-123">Business Milestone</span></span>|<span data-ttu-id="77751-124">日期/時間值。</span><span class="sxs-lookup"><span data-stu-id="77751-124">A date/time value.</span></span> <span data-ttu-id="77751-125">例如，訂單的核准日期。</span><span class="sxs-lookup"><span data-stu-id="77751-125">For example, an approval date for a purchase order.</span></span>|  
    |<span data-ttu-id="77751-126">商務資料 – TEXT</span><span class="sxs-lookup"><span data-stu-id="77751-126">Business Data – Text</span></span>|<span data-ttu-id="77751-127">包含任何英數字元的字串。</span><span class="sxs-lookup"><span data-stu-id="77751-127">A string containing any alphanumeric characters.</span></span> <span data-ttu-id="77751-128">例如，送貨至： 城市、 縣/市和郵遞區號的程式碼。</span><span class="sxs-lookup"><span data-stu-id="77751-128">For example, Ship to: City, State/Province and Zip/Postal code.</span></span>|  
    |<span data-ttu-id="77751-129">商務資料 - INTEGER</span><span class="sxs-lookup"><span data-stu-id="77751-129">Business Data – Integer</span></span>|<span data-ttu-id="77751-130">整數值。</span><span class="sxs-lookup"><span data-stu-id="77751-130">A whole number value.</span></span> <span data-ttu-id="77751-131">例如，總訂購數。</span><span class="sxs-lookup"><span data-stu-id="77751-131">For example, the total number of purchases.</span></span>|  
    |<span data-ttu-id="77751-132">商務資料 – Decimal</span><span class="sxs-lookup"><span data-stu-id="77751-132">Business Data – Decimal</span></span>|<span data-ttu-id="77751-133">十進位值。</span><span class="sxs-lookup"><span data-stu-id="77751-133">A decimal value.</span></span> <span data-ttu-id="77751-134">例如 PO 的總金額。</span><span class="sxs-lookup"><span data-stu-id="77751-134">For example the total dollar amount of the PO.</span></span>|  
  
     <span data-ttu-id="77751-135">如果您選取的項目輸入 「 商務資料-Text，您必須為中的字串輸入的字元數上限**最大長度**方塊。</span><span class="sxs-lookup"><span data-stu-id="77751-135">If you select the item type "Business Data – Text", you must enter the maximum number of characters for the string in the **Maximum length** box.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="77751-136">如需有關建立這些項目的詳細資訊，請參閱 Microsoft BizTalk Server 教學課程中的＜夥伴管理與商務活動監控＞。</span><span class="sxs-lookup"><span data-stu-id="77751-136">For more information about creating these items, see "Partner Management and Business Activity Monitoring" in the Microsoft BizTalk Server tutorial.</span></span>  
  
4.  <span data-ttu-id="77751-137">重複步驟 1 至 3，視需要新增所需的項目至這個活動。</span><span class="sxs-lookup"><span data-stu-id="77751-137">Repeat steps 1 through 3 to add as many items as needed to this activity.</span></span>  
  
5.  <span data-ttu-id="77751-138">完成 [商務活動監控活動精靈] 之後，[商務活動監控檢視精靈] 便會自動啟動。</span><span class="sxs-lookup"><span data-stu-id="77751-138">After you complete the Business Activity Monitoring Activity Wizard, the Business Activity Monitoring View Wizard starts automatically.</span></span>  
  
 <span data-ttu-id="77751-139">如需有關使用此精靈的詳細資訊，請參閱[定義 BAM 檢視](../core/defining-a-bam-view.md)。</span><span class="sxs-lookup"><span data-stu-id="77751-139">For more information about using this wizard, see [Defining a BAM View](../core/defining-a-bam-view.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77751-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="77751-140">See Also</span></span>  
 <span data-ttu-id="77751-141">[定義 BAM 檢視](../core/defining-a-bam-view.md) </span><span class="sxs-lookup"><span data-stu-id="77751-141">[Defining a BAM View](../core/defining-a-bam-view.md) </span></span>  
 [<span data-ttu-id="77751-142">在 Excel 中定義商務活動和檢視</span><span class="sxs-lookup"><span data-stu-id="77751-142">Defining Business Activities and Views in Excel</span></span>](../core/defining-business-activities-and-views-in-excel.md)