---
title: 設定 EDI 和 AS2 狀態報告 |Microsoft 文件
description: 建立 EDI 或 AS2 狀態報告查詢運算式中，並選取您要在 BizTalk Server 中的報表中顯示的資料
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6490864d-f1e6-4932-aefb-c332a595aad7
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 833e3c6c26cdac57d7cc57d828b66a66b9eb37f5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22233678"
---
# <a name="configure-an-edi-and-as2-status-report"></a><span data-ttu-id="d16c0-103">設定 EDI 和 AS2 狀態報告</span><span class="sxs-lookup"><span data-stu-id="d16c0-103">Configure an EDI and AS2 Status Report</span></span>
<span data-ttu-id="d16c0-104">您已啟用 EDI 或 AS2 狀態報告，顯示狀態報告之後，您想從**EDI 狀態報告**或**EDIINT 狀態報告**區段**群組中樞**索引標籤**群組概觀**頁面[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="d16c0-104">After you have enabled EDI or AS2 status reports, you display the status report you want from the **EDI Status Reports** or **EDIINT Status Reports** section of the **Group Hub** tab of the **Group Overview** page in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console.</span></span> <span data-ttu-id="d16c0-105">當您顯示狀態報告時，您會看到預設的資料集。</span><span class="sxs-lookup"><span data-stu-id="d16c0-105">When you display a status report, you will see a default set of data.</span></span> <span data-ttu-id="d16c0-106">您可以設定狀態報告的下列各方面：</span><span class="sxs-lookup"><span data-stu-id="d16c0-106">You can configure the following aspects of the status reports:</span></span>  
  
-   <span data-ttu-id="d16c0-107">執行來決定狀態報告之資料範圍的查詢運算式，例如日期範圍、資料的方向 (接收或傳送) 或狀態值 (「已接受」、「已拒絕」、「全部」等)。</span><span class="sxs-lookup"><span data-stu-id="d16c0-107">The query expression that is run to determine the range of data that status is reported for, for example, the date range, the direction of the data (receive or send), or the status value (Accepted, Rejected, All, etc.)</span></span>  
  
-   <span data-ttu-id="d16c0-108">顯示在狀態報告窗格中的資料型別，這是由報告中的資料行所決定。</span><span class="sxs-lookup"><span data-stu-id="d16c0-108">The type of data displayed in the status report pane, as determined by the data columns in the report.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d16c0-109">一旦啟用狀態報告後，所有的狀態都會儲存在儲存區中。</span><span class="sxs-lookup"><span data-stu-id="d16c0-109">Whenever status reporting is enabled, all status will be saved in storage.</span></span> <span data-ttu-id="d16c0-110">透過自訂查詢運算式或狀態資料行，您就可以定義顯示的已儲存資料。</span><span class="sxs-lookup"><span data-stu-id="d16c0-110">By customizing the query expression or status columns, you are defining which saved data is displayed.</span></span>  
  
 <span data-ttu-id="d16c0-111">五個不同 EDI 和 AS2 狀態報告 (請參閱[類型的 EDI 和 AS2 狀態報告](../core/types-of-edi-and-as2-status-reports.md))。</span><span class="sxs-lookup"><span data-stu-id="d16c0-111">Five different EDI and AS2 status reports are available (see [Types of EDI and AS2 Status Reports](../core/types-of-edi-and-as2-status-reports.md)).</span></span> <span data-ttu-id="d16c0-112">雖然每種報告中的資料不同，但設定報告的方式都相同。</span><span class="sxs-lookup"><span data-stu-id="d16c0-112">The way that you configure each report is the same, even though the data for each report is different.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d16c0-113">必要條件</span><span class="sxs-lookup"><span data-stu-id="d16c0-113">Prerequisites</span></span>  
 <span data-ttu-id="d16c0-114">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分登入。</span><span class="sxs-lookup"><span data-stu-id="d16c0-114">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
## <a name="configure-the-status-report-query-expression"></a><span data-ttu-id="d16c0-115">設定狀態報告查詢運算式</span><span class="sxs-lookup"><span data-stu-id="d16c0-115">Configure the status report query expression</span></span>  
  
1.  <span data-ttu-id="d16c0-116">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，按一下  **BizTalk 群組**節點以查看**群組概觀**窗格。</span><span class="sxs-lookup"><span data-stu-id="d16c0-116">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, click the **BizTalk Group** node to see the **Group Overview** pane.</span></span>  
  
2.  <span data-ttu-id="d16c0-117">在底部**群組中樞**索引標籤中**群組概觀** 窗格中，按一下您想要這類設定的狀態報告**EDI 交換和相互關聯的 ACK 狀態**。</span><span class="sxs-lookup"><span data-stu-id="d16c0-117">At the bottom of the **Group Hub** tab in the **Group Overview** pane, click the status report that you want to configure, such as **EDI Interchange and Correlated ACK Status**.</span></span>  
  
3.  <span data-ttu-id="d16c0-118">在**查詢運算式**區域的狀態報告窗格中，確認其中列有您想要定義查詢的所有篩選準則。</span><span class="sxs-lookup"><span data-stu-id="d16c0-118">In the **Query Expression** area of the status report pane, verify that all filter criteria that you want to define for the query are present.</span></span> <span data-ttu-id="d16c0-119">如果沒有，請按一下中的空白資料列中的向下箭號**欄位名稱**底部查詢運算式中，然後選取您想要加入查詢運算式的準則的所有篩選的資料行。</span><span class="sxs-lookup"><span data-stu-id="d16c0-119">If not, click the down arrow in the empty row in the **Field Name** column at the bottom of the query expression, and select any filter criteria that you want to add to the query expression.</span></span> <span data-ttu-id="d16c0-120">您可以選取資料列並按一下刪除篩選準則列**刪除**鍵盤上的按鈕。</span><span class="sxs-lookup"><span data-stu-id="d16c0-120">You can delete a filter criteria row by selecting the row and clicking the **Delete** button on the keyboard.</span></span>  
  
4.  <span data-ttu-id="d16c0-121">確認篩選條件運算式的值是否是您需要的。</span><span class="sxs-lookup"><span data-stu-id="d16c0-121">Verify that the values for the filter expressions are as desired.</span></span> <span data-ttu-id="d16c0-122">如果沒有，請按一下向下的箭號**運算子**選取查詢作業，並輸入適當的值中的資料行**值**資料行。</span><span class="sxs-lookup"><span data-stu-id="d16c0-122">If not, click the down arrow for the **Operator** column to select a query operation, and enter the appropriate value in the **Value** column.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d16c0-123">中所述的運算子和值可用於查詢運算式中的篩選準則[類型的 EDI 和 AS2 狀態報告](../core/types-of-edi-and-as2-status-reports.md)和**EDI AS2 狀態報告 UI** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="d16c0-123">The operators and values available for filter criteria in the query expressions are described in [Types of EDI and AS2 Status Reports](../core/types-of-edi-and-as2-status-reports.md) and the **EDI-AS2 Status Reports UI** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>  
  
5.  <span data-ttu-id="d16c0-124">若要執行查詢，並顯示狀態報告，根據篩選準則，按一下**執行查詢**。</span><span class="sxs-lookup"><span data-stu-id="d16c0-124">To run the query, displaying the status report according to the filter criteria, click **Run Query**.</span></span>  
  
6.  <span data-ttu-id="d16c0-125">若要將查詢運算式儲存成.btq 檔案，按一下**存**、 指定的資料夾，並輸入的檔案名稱，然後按一下**儲存**。</span><span class="sxs-lookup"><span data-stu-id="d16c0-125">To save a query expression as a .btq file, click **Save As**, specify the folder and enter a filename, and then click **Save**.</span></span>  
  
7.  <span data-ttu-id="d16c0-126">若要開啟儲存的.btq 檔案，請按一下**開啟查詢**。</span><span class="sxs-lookup"><span data-stu-id="d16c0-126">To open a saved .btq file, click **Open Query**.</span></span>  
  
## <a name="configure-the-type-of-data-displayed-in-the-status-report-pane"></a><span data-ttu-id="d16c0-127">設定顯示在狀態報告窗格中的資料類型</span><span class="sxs-lookup"><span data-stu-id="d16c0-127">Configure the type of data displayed in the status report pane</span></span>  
  
1.  <span data-ttu-id="d16c0-128">以滑鼠右鍵按一下 [狀態報表] 窗格的狀態結果區域，然後按一下**新增/移除欄位**。</span><span class="sxs-lookup"><span data-stu-id="d16c0-128">Right-click the status results area of the status report pane, and then click **Add/Remove Columns**.</span></span>  
  
2.  <span data-ttu-id="d16c0-129">若要將狀態類別加入至顯示的資料行清單中，按一下 中的資料行**可用的資料行**清單，然後再按**新增**。</span><span class="sxs-lookup"><span data-stu-id="d16c0-129">To add a status category to the displayed columns list, click a column in the **Available columns** list, and then click **Add**.</span></span>  
  
3.  <span data-ttu-id="d16c0-130">若要移除狀態類別從顯示的資料行清單，請按一下中的資料行**顯示資料行**清單，然後再按**移除**。</span><span class="sxs-lookup"><span data-stu-id="d16c0-130">To remove a status category from the displayed columns list, click a column in the **Displayed columns** list, and then click **Remove**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d16c0-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d16c0-131">See Also</span></span>  
 <span data-ttu-id="d16c0-132">[監控 EDI 和 AS2 解決方案](../core/monitoring-edi-and-as2-solutions.md) </span><span class="sxs-lookup"><span data-stu-id="d16c0-132">[Monitoring EDI and AS2 Solutions](../core/monitoring-edi-and-as2-solutions.md) </span></span>  
 <span data-ttu-id="d16c0-133">[EDI 和 AS2 狀態報告](../core/edi-and-as2-status-reporting.md) </span><span class="sxs-lookup"><span data-stu-id="d16c0-133">[EDI and AS2 Status Reporting](../core/edi-and-as2-status-reporting.md) </span></span>  
 <span data-ttu-id="d16c0-134">[啟用 EDI 和 AS2 狀態報告](../core/enabling-edi-and-as2-status-reports.md) </span><span class="sxs-lookup"><span data-stu-id="d16c0-134">[Enabling EDI and AS2 Status Reports](../core/enabling-edi-and-as2-status-reports.md) </span></span>  
 [<span data-ttu-id="d16c0-135">顯示 EDI 或 AS2 狀態報告</span><span class="sxs-lookup"><span data-stu-id="d16c0-135">Displaying an EDI or AS2 Status Report</span></span>](../core/displaying-an-edi-or-as2-status-report.md)