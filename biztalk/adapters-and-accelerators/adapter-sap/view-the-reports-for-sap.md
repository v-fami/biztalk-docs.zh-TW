---
title: 檢視適用於 SAP 的報告 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0932ffc5-cde0-4d14-822f-713b760c3f12
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8643ef37e3fe4aec77cd9d218a171d37c2c24852
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36974607"
---
# <a name="view-the-reports-for-sap"></a><span data-ttu-id="06509-102">適用於 SAP 的檢視報表</span><span class="sxs-lookup"><span data-stu-id="06509-102">View the Reports for SAP</span></span>
<span data-ttu-id="06509-103">您已建立報表之後，您可以檢視使用 Visual Studio，或透過網路將它裝載在 Internet Information Services (IIS) 與存取報表伺服器上。</span><span class="sxs-lookup"><span data-stu-id="06509-103">After you have created the report, you can view it either using Visual Studio or host it on the Report Server on Internet Information Services (IIS) and access over the network.</span></span> <span data-ttu-id="06509-104">本主題提供有關如何檢視報表，在 Visual Studio，並使用 IIS 的指示。</span><span class="sxs-lookup"><span data-stu-id="06509-104">This topic provides instructions on how to view reports both in Visual Studio and using IIS.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="06509-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="06509-105">Prerequisites</span></span>  
 <span data-ttu-id="06509-106">然後再執行本主題所提供的程序，您必須產生報表中所述[使用 Data Provider for SAP 建立報表伺服器專案](../../adapters-and-accelerators/adapter-sap/use-the-data-provider-for-sap-to-create-a-report-server-project.md)。</span><span class="sxs-lookup"><span data-stu-id="06509-106">Before performing the procedures provided in this topic, you must have generated a report as described in [Use the Data Provider for SAP to Create a Report Server Project](../../adapters-and-accelerators/adapter-sap/use-the-data-provider-for-sap-to-create-a-report-server-project.md).</span></span>  
  
### <a name="to-view-the-reports-in-visual-studio"></a><span data-ttu-id="06509-107">在 Visual Studio 中檢視報表</span><span class="sxs-lookup"><span data-stu-id="06509-107">To view the reports in Visual Studio</span></span>  
  
1. <span data-ttu-id="06509-108">在  [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，以滑鼠右鍵按一下 [方案總管] 中的專案名稱，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="06509-108">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], right-click the project name in the Solution Explorer, and then click **Properties**.</span></span>  
  
2. <span data-ttu-id="06509-109">在 [報表屬性頁] 對話方塊中，按一下**Configuration Manager**，並清除底下的核取方塊**部署**資料行。</span><span class="sxs-lookup"><span data-stu-id="06509-109">In the report property pages dialog box, click **Configuration Manager**, and clear the check box under the **Deploy** column.</span></span> <span data-ttu-id="06509-110">按一下 [ **關閉**]。</span><span class="sxs-lookup"><span data-stu-id="06509-110">Click **Close**.</span></span>  
  
3. <span data-ttu-id="06509-111">在 [報表屬性頁] 對話方塊中，如**StartItem**屬性中，選取報表的名稱，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="06509-111">In the report property pages dialog box, for the **StartItem** property, select the name of the report, and then click **OK**.</span></span>  
  
    <span data-ttu-id="06509-112">![指定報表伺服器專案的屬性](../../adapters-and-accelerators/adapter-sap/media/b3c500f7-840d-461f-945c-66db239d81b9.gif "b3c500f7-840d-461f-945c-66db239d81b9")</span><span class="sxs-lookup"><span data-stu-id="06509-112">![Specify properties for the Report Server project](../../adapters-and-accelerators/adapter-sap/media/b3c500f7-840d-461f-945c-66db239d81b9.gif "b3c500f7-840d-461f-945c-66db239d81b9")</span></span>  
  
4. <span data-ttu-id="06509-113">以滑鼠右鍵按一下 [方案總管] 中的專案名稱，然後按一下**建置**。</span><span class="sxs-lookup"><span data-stu-id="06509-113">Right-click the project name in the Solution Explorer, and then click **Build**.</span></span>  
  
5. <span data-ttu-id="06509-114">按下`F5`執行此專案以產生報表。</span><span class="sxs-lookup"><span data-stu-id="06509-114">Press `F5` to run the project to generate the report.</span></span>  
  
   > [!IMPORTANT]
   >  <span data-ttu-id="06509-115">在[!INCLUDE[btsVStudio2008](../../includes/btsvstudio2008-md.md)]，您可以按一下來查看報表**預覽** 索引標籤。在此情況下，後續的對話方塊會開啟 [預覽] 索引標籤中。</span><span class="sxs-lookup"><span data-stu-id="06509-115">In [!INCLUDE[btsVStudio2008](../../includes/btsvstudio2008-md.md)], you can see the report by clicking the **Preview** tab. In such a case, the subsequent dialog boxes will open within the preview tab.</span></span>  
  
6. <span data-ttu-id="06509-116">具有相同名稱與您針對報表指定的對話方塊會開啟。</span><span class="sxs-lookup"><span data-stu-id="06509-116">A dialog box with the same name as you specified for the report opens up.</span></span> <span data-ttu-id="06509-117">建立資料來源時，如果您選擇**提示認證**選項，為 SAP 系統中，輸入使用者名稱和密碼，然後按一下**檢視報表**。</span><span class="sxs-lookup"><span data-stu-id="06509-117">While creating the data source, if you chose the **Prompt for credentials** option, enter the user name and password for the SAP system, and then click **View Report**.</span></span>  
  
    <span data-ttu-id="06509-118">![指定要產生報告的 SAP 認證](../../adapters-and-accelerators/adapter-sap/media/fa831aae-b2d1-4ba2-a23f-f7beeb8f898e.gif "fa831aae-b2d1-4ba2-a23f-f7beeb8f898e")</span><span class="sxs-lookup"><span data-stu-id="06509-118">![Specify SAP credentials to generate a report](../../adapters-and-accelerators/adapter-sap/media/fa831aae-b2d1-4ba2-a23f-f7beeb8f898e.gif "fa831aae-b2d1-4ba2-a23f-f7beeb8f898e")</span></span>  
  
7. <span data-ttu-id="06509-119">如果您指定查詢時建立報表伺服器專案需要參數，您必須輸入參數的值。</span><span class="sxs-lookup"><span data-stu-id="06509-119">If the query you specified while creating the Report Server project requires a parameter, you must enter the value of the parameter.</span></span> <span data-ttu-id="06509-120">例如，查詢中指定[使用 Data Provider for SAP 建立報表伺服器專案](../../adapters-and-accelerators/adapter-sap/use-the-data-provider-for-sap-to-create-a-report-server-project.md)主題，會要求您指定的參數，參數的值。</span><span class="sxs-lookup"><span data-stu-id="06509-120">For example, for the query you specified in the [Use the Data Provider for SAP to Create a Report Server Project](../../adapters-and-accelerators/adapter-sap/use-the-data-provider-for-sap-to-create-a-report-server-project.md) topic, requires you to specify a value for the parameter, PARAM.</span></span>  
  
    <span data-ttu-id="06509-121">如有需要，指定參數的值，然後按一下 **檢視報表**。</span><span class="sxs-lookup"><span data-stu-id="06509-121">Specify the value of the parameter, if required, and click **View Report**.</span></span>  
  
    <span data-ttu-id="06509-122">![指定要產生報表的參數](../../adapters-and-accelerators/adapter-sap/media/5deec152-771b-46b4-84da-dd176193d7f3.gif "5deec152-771b-46b4-84da-dd176193d7f3")</span><span class="sxs-lookup"><span data-stu-id="06509-122">![Specify parameters to generate a report](../../adapters-and-accelerators/adapter-sap/media/5deec152-771b-46b4-84da-dd176193d7f3.gif "5deec152-771b-46b4-84da-dd176193d7f3")</span></span>  
  
### <a name="to-host-the-reports-on-report-server"></a><span data-ttu-id="06509-123">若要裝載報表伺服器上的報表</span><span class="sxs-lookup"><span data-stu-id="06509-123">To host the reports on Report Server</span></span>  
  
1. <span data-ttu-id="06509-124">在  [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，以滑鼠右鍵按一下 [方案總管] 中的專案名稱，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="06509-124">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], right-click the project name in the Solution Explorer, and then click **Properties**.</span></span>  
  
2. <span data-ttu-id="06509-125">在 [報表屬性頁] 對話方塊中，按一下**Configuration Manager**，然後選取底下的核取方塊**部署**資料行。</span><span class="sxs-lookup"><span data-stu-id="06509-125">In the report property pages dialog box, click **Configuration Manager**, and select the check box under the **Deploy** column.</span></span> <span data-ttu-id="06509-126">按一下 [ **關閉**]。</span><span class="sxs-lookup"><span data-stu-id="06509-126">Click **Close**.</span></span>  
  
3. <span data-ttu-id="06509-127">在 [報表屬性頁] 對話方塊中，如**StartItem**屬性中，選取報表的名稱。</span><span class="sxs-lookup"><span data-stu-id="06509-127">In the report property pages dialog box, for the **StartItem** property, select the name of the report.</span></span>  
  
4. <span data-ttu-id="06509-128">在 [報表屬性頁] 對話方塊中，如**TargetServerURL**屬性，指定報表伺服器的 URL，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="06509-128">In the report property pages dialog box, for the **TargetServerURL** property, specify a URL for the Report Server, and then click **OK**.</span></span> <span data-ttu-id="06509-129">例如：</span><span class="sxs-lookup"><span data-stu-id="06509-129">For example:</span></span>  
  
   ```  
   http://localhost/reportserver  
   ```  
  
    <span data-ttu-id="06509-130">![指定的報表伺服器 URL](../../adapters-and-accelerators/adapter-sap/media/397ddfd6-f3d2-4327-9bc3-1efa22dc2249.gif "397ddfd6-f3d2-4327-9bc3-1efa22dc2249")</span><span class="sxs-lookup"><span data-stu-id="06509-130">![Specify URL for the Report Server](../../adapters-and-accelerators/adapter-sap/media/397ddfd6-f3d2-4327-9bc3-1efa22dc2249.gif "397ddfd6-f3d2-4327-9bc3-1efa22dc2249")</span></span>  
  
5. <span data-ttu-id="06509-131">以滑鼠右鍵按一下 [方案總管] 中的專案名稱，然後按一下**建置**。</span><span class="sxs-lookup"><span data-stu-id="06509-131">Right-click the project name in the Solution Explorer, and then click **Build**.</span></span>  
  
6. <span data-ttu-id="06509-132">以滑鼠右鍵按一下 [方案總管] 中的專案名稱，然後按一下**部署**。</span><span class="sxs-lookup"><span data-stu-id="06509-132">Right-click the project name in the Solution Explorer, and then click **Deploy**.</span></span>  
  
7. <span data-ttu-id="06509-133">啟動 IIS。</span><span class="sxs-lookup"><span data-stu-id="06509-133">Start IIS.</span></span> <span data-ttu-id="06509-134">按一下 **開始**，按一下**執行**，型別`inetmgr`，然後按`Enter`。</span><span class="sxs-lookup"><span data-stu-id="06509-134">Click **Start**, click **Run**, type `inetmgr`, and press `Enter`.</span></span>  
  
8. <span data-ttu-id="06509-135">在  **Internet Information Services (IIS) 管理員**嵌入式管理單元中，展開電腦名稱，展開**網站**，展開**Default Web Site**，以滑鼠右鍵按一下**ReportServer**，然後按一下**瀏覽**。</span><span class="sxs-lookup"><span data-stu-id="06509-135">In the **Internet Information Services (IIS) Manager** snap-in, expand the computer name, expand **Web Sites**, expand **Default Web Site**, right-click **ReportServer**, and then click **Browse**.</span></span>  
  
9. <span data-ttu-id="06509-136">在右窗格中，按一下專案名稱，然後按一下報表名稱。</span><span class="sxs-lookup"><span data-stu-id="06509-136">In the right pane, click the name of the project, and then click on the name of the report.</span></span>  
  
10. <span data-ttu-id="06509-137">建立資料來源時，如果您選擇**提示認證**選項，輸入 SAP 系統的使用者名稱和密碼，然後按一下**檢視報表**。</span><span class="sxs-lookup"><span data-stu-id="06509-137">While creating the data source, if you chose the **Prompt for credentials** option, enter the user name and password for the SAP system and click **View Report**.</span></span>  
  
11. <span data-ttu-id="06509-138">如果您指定查詢時建立報表伺服器專案需要參數，您必須輸入參數的值。</span><span class="sxs-lookup"><span data-stu-id="06509-138">If the query you specified while creating the Report Server project requires a parameter, you must enter the value of the parameter.</span></span> <span data-ttu-id="06509-139">例如，查詢中指定[使用 Data Provider for SAP 建立報表伺服器專案](../../adapters-and-accelerators/adapter-sap/use-the-data-provider-for-sap-to-create-a-report-server-project.md)主題，會要求您指定的參數，參數的值。</span><span class="sxs-lookup"><span data-stu-id="06509-139">For example, for the query you specified in the [Use the Data Provider for SAP to Create a Report Server Project](../../adapters-and-accelerators/adapter-sap/use-the-data-provider-for-sap-to-create-a-report-server-project.md) topic, requires you to specify a value for the parameter, PARAM.</span></span>  
  
     <span data-ttu-id="06509-140">如有需要，指定參數的值，然後按一下 **檢視報表**。</span><span class="sxs-lookup"><span data-stu-id="06509-140">Specify the value of the parameter, if required, and click **View Report**.</span></span>  
  
     <span data-ttu-id="06509-141">![指定要產生報表的參數](../../adapters-and-accelerators/adapter-sap/media/221c8c12-4e4f-47f5-9289-9e9212cf6e25.gif "221c8c12-4e4f-47f5-9289-9e9212cf6e25")</span><span class="sxs-lookup"><span data-stu-id="06509-141">![Specify parameters to generate a report](../../adapters-and-accelerators/adapter-sap/media/221c8c12-4e4f-47f5-9289-9e9212cf6e25.gif "221c8c12-4e4f-47f5-9289-9e9212cf6e25")</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="06509-142">您也可以直接從網頁瀏覽器檢視，讓報表的 URL。</span><span class="sxs-lookup"><span data-stu-id="06509-142">You can also view directly from the web browser by giving the URL for the report.</span></span> <span data-ttu-id="06509-143">報表的一般 URL `is http://localhohost/reportserver/<report_name>`。</span><span class="sxs-lookup"><span data-stu-id="06509-143">A typical URL for the report `is http://localhohost/reportserver/<report_name>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06509-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="06509-144">See Also</span></span>  
 [<span data-ttu-id="06509-145">搭配使用 Data Provider for SAP 與 SSRS</span><span class="sxs-lookup"><span data-stu-id="06509-145">Use the Data Provider for SAP with SSRS</span></span>](../../adapters-and-accelerators/adapter-sap/use-the-data-provider-for-sap-with-ssis.md)