---
title: 在 Excel 中定義商務活動和檢視 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Excel add-in [BAM], creating business activities
- monitoring business activities [BAM], creating business activities
ms.assetid: 000532f0-cb9a-40ac-a6c5-a8bd4e49f8d0
caps.latest.revision: 19
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 61e9302d2f3178e457a5ed57353e77eac0909d32
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37014135"
---
# <a name="defining-business-activities-and-views-in-excel"></a><span data-ttu-id="7eaad-102">在 Excel 中定義商務活動和檢視</span><span class="sxs-lookup"><span data-stu-id="7eaad-102">Defining Business Activities and Views in Excel</span></span>
<span data-ttu-id="7eaad-103">建立任何 BAM 解決方案時的第一個步驟是，找出您有興趣的資料，並釐清解譯此項資料所應採用的方式。</span><span class="sxs-lookup"><span data-stu-id="7eaad-103">Your first step in creating any BAM solution is to identify what data you're interested in and how that data should be interpreted.</span></span> <span data-ttu-id="7eaad-104">若要這樣做，您可以使用 Excel 的 BAM 增益集。</span><span class="sxs-lookup"><span data-stu-id="7eaad-104">To do this, you use the BAM Add-in for Excel.</span></span> <span data-ttu-id="7eaad-105">此增益集可讓您藉由定義商務活動來定義您希望的「感興趣資料」清單。</span><span class="sxs-lookup"><span data-stu-id="7eaad-105">The add-in allows you to define a wish-list of the data of interest by defining a business activity.</span></span> <span data-ttu-id="7eaad-106">您也可以定義解譯資料以及向不同類別的商務使用者顯示資料的方式。</span><span class="sxs-lookup"><span data-stu-id="7eaad-106">You can also define the way the data should be interpreted and shown to different categories of business users.</span></span>  
  
 <span data-ttu-id="7eaad-107">此 BAM 增益集還可以用來定義彙總。</span><span class="sxs-lookup"><span data-stu-id="7eaad-107">The BAM Add-in also enables you to define aggregations.</span></span>  
  
 <span data-ttu-id="7eaad-108">您也可以重新命名活動項目；例如，某些使用者熟悉的詞彙可能不符合活動中對應資料項目的名稱。</span><span class="sxs-lookup"><span data-stu-id="7eaad-108">You can also rename activity items, for example, where the terminology some users are familiar with does not match the names of the corresponding data items in the activity.</span></span> <span data-ttu-id="7eaad-109">因此，如果檢視使用不同的語言，便可以構成重新命名的理由。</span><span class="sxs-lookup"><span data-stu-id="7eaad-109">One explanation for this is where the view is in a different language.</span></span>  
  
 <span data-ttu-id="7eaad-110">完成活動定義之後，Excel 會產生隨機的預覽資料，以便您用來定義需要的圖表和其他的簡報方法。</span><span class="sxs-lookup"><span data-stu-id="7eaad-110">After you complete the activity definition, Excel generates random preview data that you can use to define the desired charts and other means of presentation.</span></span> <span data-ttu-id="7eaad-111">如需預覽資料的詳細資訊，請參閱[如何使用樞紐分析表](../core/how-to-use-the-pivottable.md)。</span><span class="sxs-lookup"><span data-stu-id="7eaad-111">For more information about preview data, see [How to Use the PivotTable](../core/how-to-use-the-pivottable.md).</span></span>  
  
 <span data-ttu-id="7eaad-112">完成的活動定義會定義執行商務程序時必須收集的資料點和事件。</span><span class="sxs-lookup"><span data-stu-id="7eaad-112">The completed activity definition defines the data points and events that you need collected when a business process is run.</span></span> <span data-ttu-id="7eaad-113">您可以從各種來源取得該 BAM 增益集。</span><span class="sxs-lookup"><span data-stu-id="7eaad-113">You can get the BAM Add-in from a variety of sources.</span></span>  
  
 <span data-ttu-id="7eaad-114">您可以安裝 BAM 增益集 XLA 期間[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝。</span><span class="sxs-lookup"><span data-stu-id="7eaad-114">You can install the BAM Add-in XLA during the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation.</span></span> <span data-ttu-id="7eaad-115">如需詳細資訊，請參閱[BizTalk Server 2013 和 2013 R2 的安裝概觀](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5)</span><span class="sxs-lookup"><span data-stu-id="7eaad-115">For more information, see [Installation Overview for BizTalk Server 2013 and 2013 R2](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5)</span></span>  
  
 <span data-ttu-id="7eaad-116">BAM。XLA 檔案會安裝在下列位置：</span><span class="sxs-lookup"><span data-stu-id="7eaad-116">The BAM.XLA file is installed in one of the following locations:</span></span>  
  
- <span data-ttu-id="7eaad-117">如果未安裝 Microsoft Office 的電腦上，則 BAM.xla 會安裝至 BizTalk Server 20 \Program Files\Microsoft*xx*\ExcelDir\ 資料夾。</span><span class="sxs-lookup"><span data-stu-id="7eaad-117">If Microsoft Office is not installed on the computer, then the BAM.xla is installed to the \Program Files\Microsoft BizTalk Server 20*xx*\ExcelDir\ folder.</span></span>  
  
- <span data-ttu-id="7eaad-118">如果已安裝 Microsoft Office，則 BAM.xla 會安裝 \Program Files\Microsoft Office\OFFICE*xx*\Library\ 資料夾。</span><span class="sxs-lookup"><span data-stu-id="7eaad-118">If Microsoft Office is installed, the BAM.xla is installed in the \Program Files\Microsoft Office\OFFICE*xx*\Library\ folder.</span></span>  
  
  <span data-ttu-id="7eaad-119">您也可以將 BAM.xla 從另一台電腦上的共用資料夾複製至您的電腦。</span><span class="sxs-lookup"><span data-stu-id="7eaad-119">You can also copy the BAM.xla to your computer from a shared folder on another computer.</span></span> <span data-ttu-id="7eaad-120">然後從 XLA 複製到的位置加以選取，以註冊 XLA。</span><span class="sxs-lookup"><span data-stu-id="7eaad-120">You can then register the XLA by selecting it from the location to which you copied it.</span></span>  
  
  <span data-ttu-id="7eaad-121">若要啟用 BAM 增益集在 Excel 功能表工具列上，按一下**檔案**功能表，然後按一下**選項**，然後按一下**增益集**。選取 **商務活動監控**，然後按一下**移**，在 增益 視窗中，選取核取方塊旁**商務活動監控**，然後按一下  **確定**。</span><span class="sxs-lookup"><span data-stu-id="7eaad-121">To enable the BAM Add-in on the Excel menu toolbar, click the **File** menu, then click **Options**, and then click **Add-Ins**. Select **Business Activity Monitoring**, then click **GO**, In the Ad-ins window, select the check box next to **Business Activity Monitoring**, and then click **OK**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7eaad-122">使用 BAM 增益集可以避免 Excel 在兩個執行個體載入至相同處理程序的情況下執行。</span><span class="sxs-lookup"><span data-stu-id="7eaad-122">Using the BAM Add-in precludes running Excel with two instances loaded into the same process.</span></span>  <span data-ttu-id="7eaad-123">使用增益集時，相同處理程序中出現多個執行個體的情形可能會在下列狀況中發生：</span><span class="sxs-lookup"><span data-stu-id="7eaad-123">When using the add-in, multiple instances in the same process can occur in the following situations:</span></span>  
>   
>  <span data-ttu-id="7eaad-124">開啟 Excel 試算表並啟用 BAM 增益集後，再按兩下其他的 Excel 試算表時，Excel 會嘗試將試算表載入目前執行中的執行個體。</span><span class="sxs-lookup"><span data-stu-id="7eaad-124">When you have an Excel spreadsheet open with the BAM Add-in enabled, and you double-click a different Excel spreadsheet, Excel attempts to load the spreadsheet into the currently running instance.</span></span>  
>   
>  <span data-ttu-id="7eaad-125">開啟 Excel 試算表並啟用 BAM 增益集後，再使用 [檔案/開啟舊檔] 功能表選項載入另一份 Excel 試算表。</span><span class="sxs-lookup"><span data-stu-id="7eaad-125">When you have an Excel spreadsheet open, with the BAM Add-in enabled, and you use the File/Open menu option to load another Excel spreadsheet.</span></span>  
  
 <span data-ttu-id="7eaad-126">在這種情況下，您就無法正確使用增益集。</span><span class="sxs-lookup"><span data-stu-id="7eaad-126">You cannot use the add-in properly in such situations.</span></span> <span data-ttu-id="7eaad-127">若要在 BAM 增益集啟用時開啟多份 Excel 試算表，您必須另外開啟新的 Excel 複本，然後再將試算表載入至這個 Excel 執行個體。</span><span class="sxs-lookup"><span data-stu-id="7eaad-127">To open multiple Excel spreadsheets when you have the BAM Add-in enabled, you must open a new copy of Excel and load the spreadsheet into that instance of Excel.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7eaad-128">當您在 Excel 中使用 BAM.xla 時，您可能會收到錯誤 「 此活頁簿已經遺失的 VBA 專案、 ActiveX 控制項以及其他可程式性相關的功能 」。</span><span class="sxs-lookup"><span data-stu-id="7eaad-128">When you use BAM.xla in Excel, you may get the error “This workbook has lost its VBA project, ActiveX controls and any other programmability-related features.”</span></span> <span data-ttu-id="7eaad-129">如需錯誤的詳細資訊，請參閱[疑難排解 BAM](../core/troubleshooting-bam.md)。</span><span class="sxs-lookup"><span data-stu-id="7eaad-129">For more information about the error, see [Troubleshooting BAM](../core/troubleshooting-bam.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7eaad-130">本節內容</span><span class="sxs-lookup"><span data-stu-id="7eaad-130">In This Section</span></span>  
  
-   [<span data-ttu-id="7eaad-131">如何定義商務活動</span><span class="sxs-lookup"><span data-stu-id="7eaad-131">How to Define a Business Activity</span></span>](../core/how-to-define-a-business-activity.md)  
  
-   [<span data-ttu-id="7eaad-132">定義 BAM 檢視</span><span class="sxs-lookup"><span data-stu-id="7eaad-132">Defining a BAM View</span></span>](../core/defining-a-bam-view.md)  
  
## <a name="see-also"></a><span data-ttu-id="7eaad-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7eaad-133">See Also</span></span>  
 [<span data-ttu-id="7eaad-134">使用 BAM 來監控商務活動</span><span class="sxs-lookup"><span data-stu-id="7eaad-134">Monitoring Business Activities with BAM</span></span>](../core/monitoring-business-activities-with-bam.md)