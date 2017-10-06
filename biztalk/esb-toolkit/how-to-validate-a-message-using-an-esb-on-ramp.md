---
title: "如何： 驗證訊息，使用 ESB 上手 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 43dfc791-7cb6-45a4-898f-f53def199c08
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 63a6a79a12949148f77363d7e4cffd2b2c321d00
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-validate-a-message-using-an-esb-on-ramp"></a><span data-ttu-id="426ff-102">如何： 驗證訊息，使用 ESB 上手</span><span class="sxs-lookup"><span data-stu-id="426ff-102">How to: Validate a Message Using an ESB On-Ramp</span></span>
## <a name="goal"></a><span data-ttu-id="426ff-103">目標</span><span class="sxs-lookup"><span data-stu-id="426ff-103">Goal</span></span>  
 <span data-ttu-id="426ff-104">本節示範如何設定 ESB 發送器解譯管線元件來執行訊息驗證的 XML 訊息提交給 ESB 上手。</span><span class="sxs-lookup"><span data-stu-id="426ff-104">This section demonstrates how to configure the ESB Dispatcher Disassemble pipeline component to perform message validation for XML messages submitted to an ESB on-ramp.</span></span>  
  
 <span data-ttu-id="426ff-105">在此 「 如何 」 主題，您將完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="426ff-105">In this How-to topic, you will complete the following steps:</span></span>  
  
-   <span data-ttu-id="426ff-106">建立 ESB 上手使用**ItinerarySelectReceiveXml**管線。</span><span class="sxs-lookup"><span data-stu-id="426ff-106">Create an ESB on-ramp that uses the **ItinerarySelectReceiveXml** pipeline.</span></span>  
  
-   <span data-ttu-id="426ff-107">設定 ESB 發送器解譯管線元件以驗證訊息內容。</span><span class="sxs-lookup"><span data-stu-id="426ff-107">Configure the ESB Dispatcher Disassemble pipeline component to validate message content.</span></span>  
  
-   <span data-ttu-id="426ff-108">若要解決適當路線路線選取器管線元件設定。</span><span class="sxs-lookup"><span data-stu-id="426ff-108">Configure the Itinerary Selector pipeline component to resolve the appropriate itinerary.</span></span>  
  
-   <span data-ttu-id="426ff-109">測試訊息驗證使用有效的訊息和一個無效的訊息。</span><span class="sxs-lookup"><span data-stu-id="426ff-109">Test message validation using a valid message and an invalid message.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="426ff-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="426ff-110">Prerequisites</span></span>  
 <span data-ttu-id="426ff-111">在此 「 如何 」 主題中的程序需要完成[開發活動的必要條件](../esb-toolkit/prerequisites-for-the-development-activities.md)。</span><span class="sxs-lookup"><span data-stu-id="426ff-111">The procedures in this How-to topic require the completion of the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md).</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="426ff-112">開始之前</span><span class="sxs-lookup"><span data-stu-id="426ff-112">Before You Begin</span></span>  
 <span data-ttu-id="426ff-113">在執行本使用說明主題中稍後的步驟之前，請完成下列工作：</span><span class="sxs-lookup"><span data-stu-id="426ff-113">Complete the following tasks before you perform the steps later in this How-to topic:</span></span>  
  
-   <span data-ttu-id="426ff-114">建立無效的測試訊息。</span><span class="sxs-lookup"><span data-stu-id="426ff-114">Create an invalid test message.</span></span>  
  
-   <span data-ttu-id="426ff-115">建立 ESB 路線網域特定領域語言 (DSL) 模型。</span><span class="sxs-lookup"><span data-stu-id="426ff-115">Create an ESB itinerary domain-specific language (DSL) model.</span></span>  
  
-   <span data-ttu-id="426ff-116">設定屬性的路線。</span><span class="sxs-lookup"><span data-stu-id="426ff-116">Configure the properties of the itinerary.</span></span>  
  
-   <span data-ttu-id="426ff-117">定義結構的路線。</span><span class="sxs-lookup"><span data-stu-id="426ff-117">Define the structure of the itinerary.</span></span>  
  
-   <span data-ttu-id="426ff-118">將模型匯出至路線資料庫。</span><span class="sxs-lookup"><span data-stu-id="426ff-118">Export the model to the Itinerary database.</span></span>  
  
 <span data-ttu-id="426ff-119">下列程序說明如何執行每一種。</span><span class="sxs-lookup"><span data-stu-id="426ff-119">The following procedures describe how to do each of these.</span></span>  
  
#### <a name="to-create-an-invalid-test-message"></a><span data-ttu-id="426ff-120">若要建立無效的測試訊息</span><span class="sxs-lookup"><span data-stu-id="426ff-120">To create an invalid test message</span></span>  
  
1.  <span data-ttu-id="426ff-121">在 Windows 檔案總管，瀏覽至 C:\HowTos。</span><span class="sxs-lookup"><span data-stu-id="426ff-121">In Windows Explorer, browse to C:\HowTos.</span></span>  
  
2.  <span data-ttu-id="426ff-122">建立一份 NAOrderDoc.xml，，然後重新命名複製 Invalid.xml。</span><span class="sxs-lookup"><span data-stu-id="426ff-122">Create a copy of NAOrderDoc.xml, and then rename the copy Invalid.xml.</span></span>  
  
3.  <span data-ttu-id="426ff-123">在 [記事本] 開啟 Invalid.xml。</span><span class="sxs-lookup"><span data-stu-id="426ff-123">In Notepad, open Invalid.xml.</span></span>  
  
4.  <span data-ttu-id="426ff-124">變更 **\<ns0:requestType > 10\</ns0:requestType > 至\<ns0:requestType > 十個\</ns0:requestType >**。</span><span class="sxs-lookup"><span data-stu-id="426ff-124">Change **\<ns0:requestType>10\</ns0:requestType> to \<ns0:requestType>TEN\</ns0:requestType>**.</span></span>  
  
5.  <span data-ttu-id="426ff-125">儲存 Invalid.xml 為 utf-8，，然後關閉 [記事本]。</span><span class="sxs-lookup"><span data-stu-id="426ff-125">Save Invalid.xml as UTF-8, and then close Notepad.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="426ff-126">藉由變更這個項目的數值成文字，訊息將不再有效根據結構描述。</span><span class="sxs-lookup"><span data-stu-id="426ff-126">By changing the numerical value of this element to text, the message will no longer be valid according to the schema.</span></span>  
  
#### <a name="to-create-an-esb-itinerary-dsl-model"></a><span data-ttu-id="426ff-127">若要建立 ESB 路線 DSL 模型</span><span class="sxs-lookup"><span data-stu-id="426ff-127">To create an ESB itinerary DSL model</span></span>  
  
1.  <span data-ttu-id="426ff-128">在[!INCLUDE[vs2010](../includes/vs2010-md.md)]，開啟 C:\HowTos\Patterns\Patterns.sln。</span><span class="sxs-lookup"><span data-stu-id="426ff-128">In [!INCLUDE[vs2010](../includes/vs2010-md.md)], open C:\HowTos\Patterns\Patterns.sln.</span></span>  
  
2.  <span data-ttu-id="426ff-129">在 方案總管 中，以滑鼠右鍵按一下**ItineraryLibrary**，指向 **新增**，然後按一下**新的行程**。</span><span class="sxs-lookup"><span data-stu-id="426ff-129">In Solution Explorer, right-click **ItineraryLibrary**, point to **Add**, and then click **New Itinerary**.</span></span>  
  
3.  <span data-ttu-id="426ff-130">在**加入新項目** 對話方塊中，輸入**驗證**中**名稱**方塊，然後再按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="426ff-130">In the **Add New Item** dialog box, type **Validation** in the **Name** box, and then click **Add**.</span></span>  
  
#### <a name="to-configure-the-properties-of-the-itinerary"></a><span data-ttu-id="426ff-131">若要設定的路線屬性</span><span class="sxs-lookup"><span data-stu-id="426ff-131">To configure the properties of the itinerary</span></span>  
  
1.  <span data-ttu-id="426ff-132">在 Visual Studio 中，按一下設計介面的**Validation.itinerary**。</span><span class="sxs-lookup"><span data-stu-id="426ff-132">In Visual Studio, click the design surface of **Validation.itinerary**.</span></span> <span data-ttu-id="426ff-133">在**驗證**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="426ff-133">In the **Validation** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="426ff-134">在**模型匯出工具**下拉式清單中，按一下 **資料庫路線匯出工具**。</span><span class="sxs-lookup"><span data-stu-id="426ff-134">In the **Model Exporter** drop-down list, click **Database Itinerary Exporter**.</span></span>  
  
    2.  <span data-ttu-id="426ff-135">按一下旁邊的省略符號按鈕 （...）**路線資料庫**屬性。</span><span class="sxs-lookup"><span data-stu-id="426ff-135">Click the ellipsis button (...) next to the **Itinerary Database** property.</span></span>  
  
    3.  <span data-ttu-id="426ff-136">在**連接屬性**對話方塊中，選擇裝載路線的儲存機制資料庫，SQL Server，，然後指定資料庫的名稱 (預設名稱是**EsbItineraryDb**)。</span><span class="sxs-lookup"><span data-stu-id="426ff-136">In the **Connection Properties** dialog box, choose the SQL Server that hosts the itinerary repository database, and then specify the name of the database (the default name is **EsbItineraryDb**).</span></span>  
  
2.  <span data-ttu-id="426ff-137">在**路線狀態**下拉式清單中，按一下 **部署**。</span><span class="sxs-lookup"><span data-stu-id="426ff-137">In the **Itinerary Status** drop-down list, click **Deployed**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="426ff-138">這個步驟可讓您匯出至中央儲存機制; 路線可以選取和接收訊息時就會從這個儲存機制附加行程。</span><span class="sxs-lookup"><span data-stu-id="426ff-138">This step enables you to export the itinerary to a central repository; itineraries can be selected and attached from this repository when the message is received.</span></span> <span data-ttu-id="426ff-139">您稍後將設定路線選取器管線元件從這個儲存機制中選取適當的行程中使用靜態的解析程式。</span><span class="sxs-lookup"><span data-stu-id="426ff-139">You will later configure the Itinerary Selector pipeline component to use a static resolver to select the appropriate itinerary from this repository.</span></span>  
  
#### <a name="to-define-the-structure-of-the-itinerary"></a><span data-ttu-id="426ff-140">若要定義路線結構</span><span class="sxs-lookup"><span data-stu-id="426ff-140">To define the structure of the itinerary</span></span>  
  
1.  <span data-ttu-id="426ff-141">從 [工具箱] 拖曳**上手**至設計介面的模型項目。</span><span class="sxs-lookup"><span data-stu-id="426ff-141">From the Toolbox, drag an **On-Ramp** model element to the design surface.</span></span> <span data-ttu-id="426ff-142">在**OnRamp1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="426ff-142">In the **OnRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="426ff-143">按一下**名稱**屬性，，然後輸入**ReceiveNAOrder**。</span><span class="sxs-lookup"><span data-stu-id="426ff-143">Click the **Name** property, and then type **ReceiveNAOrder**.</span></span>  
  
    2.  <span data-ttu-id="426ff-144">在**Extender**下拉式清單中，按一下 **上手 ESB Extender**。</span><span class="sxs-lookup"><span data-stu-id="426ff-144">In the **Extender** drop-down list, click **On-Ramp ESB Extender**.</span></span>  
  
    3.  <span data-ttu-id="426ff-145">在**BizTalk 應用程式**下拉式清單中，按一下  **Microsoft.Practices.ESB**。</span><span class="sxs-lookup"><span data-stu-id="426ff-145">In the **BizTalk Application** drop-down list, click **Microsoft.Practices.ESB**.</span></span>  
  
    4.  <span data-ttu-id="426ff-146">在**接收埠**下拉式清單中，按一下  **OnRamp.Itinerary**。</span><span class="sxs-lookup"><span data-stu-id="426ff-146">In the **Receive Port** drop-down list, click **OnRamp.Itinerary**.</span></span>  
  
2.  <span data-ttu-id="426ff-147">從 [工具箱] 拖曳**匝道**模型項目至設計介面，並將其放置到現有的模型項目的右。</span><span class="sxs-lookup"><span data-stu-id="426ff-147">From the Toolbox, drag an **Off-Ramp** model element to the design surface, and then place it to the right of the existing model element.</span></span> <span data-ttu-id="426ff-148">在**OffRamp1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="426ff-148">In the **OffRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="426ff-149">按一下**名稱**屬性，，然後輸入**SendNAOrder**。</span><span class="sxs-lookup"><span data-stu-id="426ff-149">Click the **Name** property, and then type **SendNAOrder**.</span></span>  
  
    2.  <span data-ttu-id="426ff-150">在**Extender**下拉式清單中，按一下 **匝道 ESB Extender**。</span><span class="sxs-lookup"><span data-stu-id="426ff-150">In the **Extender** drop-down list, click **Off-Ramp ESB Extender**.</span></span>  
  
    3.  <span data-ttu-id="426ff-151">在**BizTalk 應用程式**下拉式清單中，按一下  **GlobalBank.ESB**。</span><span class="sxs-lookup"><span data-stu-id="426ff-151">In the **BizTalk Application** drop-down list, click **GlobalBank.ESB**.</span></span>  
  
    4.  <span data-ttu-id="426ff-152">在**傳送埠**下拉式清單中，按一下  **DynamicResolutionOneWay**。</span><span class="sxs-lookup"><span data-stu-id="426ff-152">In the **Send Port** drop-down list, click **DynamicResolutionOneWay**.</span></span>  
  
3.  <span data-ttu-id="426ff-153">從 [工具箱] 拖曳**路線服務**模型項目至設計介面，並將其之間放置**ReceiveNAOrder**模型項目和**SendNAOrder**模型項目。</span><span class="sxs-lookup"><span data-stu-id="426ff-153">From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it between the **ReceiveNAOrder** model element and the **SendNAOrder** model element.</span></span> <span data-ttu-id="426ff-154">在**ItineraryService1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="426ff-154">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="426ff-155">按一下**名稱**屬性，，然後輸入**SendPortFilter**。</span><span class="sxs-lookup"><span data-stu-id="426ff-155">Click the **Name** property, and then type **SendPortFilter**.</span></span>  
  
    2.  <span data-ttu-id="426ff-156">在**路線服務的擴充項**下拉式清單中，按一下 **匝道 Extender**。</span><span class="sxs-lookup"><span data-stu-id="426ff-156">In the **Itinerary Service Extender** drop-down list, click **Off-Ramp Extender**.</span></span>  
  
    3.  <span data-ttu-id="426ff-157">在**匝道**下拉式清單中，展開**SendNAOrder**，然後按一下**傳送處理常式**。</span><span class="sxs-lookup"><span data-stu-id="426ff-157">In the **Off-Ramp** drop-down list, expand **SendNAOrder**, and then click **Send Handlers**.</span></span>  
  
4.  <span data-ttu-id="426ff-158">以滑鼠右鍵按一下**解析程式**集合**SendPortFilter**項目，然後再按一下**加入新的解析程式**。</span><span class="sxs-lookup"><span data-stu-id="426ff-158">Right-click the **Resolver** collection of the **SendPortFilter** element, and then click **Add new Resolver**.</span></span> <span data-ttu-id="426ff-159">在**Resolver1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="426ff-159">In the **Resolver1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="426ff-160">按一下**名稱**屬性，，然後輸入**ConfigureOffRamp**。</span><span class="sxs-lookup"><span data-stu-id="426ff-160">Click the **Name** property, and then type **ConfigureOffRamp**.</span></span>  
  
    2.  <span data-ttu-id="426ff-161">在**解析程式實作**下拉式清單中，按一下 **靜態解析程式擴充功能**。</span><span class="sxs-lookup"><span data-stu-id="426ff-161">In the **Resolver Implementation** drop-down list, click **Static Resolver Extension**.</span></span>  
  
    3.  <span data-ttu-id="426ff-162">在**傳輸名稱**下拉式清單中，按一下 **檔案**。</span><span class="sxs-lookup"><span data-stu-id="426ff-162">In the **Transport Name** drop-down list, click **FILE**.</span></span>  
  
    4.  <span data-ttu-id="426ff-163">按一下**傳輸位置**屬性，，然後輸入**C:\HowTos\Out\Validated%MessageID%.xml**。</span><span class="sxs-lookup"><span data-stu-id="426ff-163">Click the **Transport Location** property, and then type **C:\HowTos\Out\Validated%MessageID%.xml**.</span></span>  
  
5.  <span data-ttu-id="426ff-164">在工具箱中，按一下 **連接器**。</span><span class="sxs-lookup"><span data-stu-id="426ff-164">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="426ff-165">拖曳連接**ReceiveNAOrder**模型項目的**SendPortFilter**模型項目。</span><span class="sxs-lookup"><span data-stu-id="426ff-165">Drag a connection from the **ReceiveNAOrder** model element to the **SendPortFilter** model element.</span></span>  
  
6.  <span data-ttu-id="426ff-166">在工具箱中，按一下 **連接器**。</span><span class="sxs-lookup"><span data-stu-id="426ff-166">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="426ff-167">拖曳連接**SendPortFilter**模型項目的**SendNAOrder**模型項目。</span><span class="sxs-lookup"><span data-stu-id="426ff-167">Drag a connection from the **SendPortFilter** model element to the **SendNAOrder** model element.</span></span>  
  
#### <a name="to-export-the-model-to-the-itinerary-database"></a><span data-ttu-id="426ff-168">將模型匯出至路線資料庫</span><span class="sxs-lookup"><span data-stu-id="426ff-168">To export the model to the itinerary database</span></span>  
  
1.  <span data-ttu-id="426ff-169">在 Visual Studio 中，以滑鼠右鍵按一下設計介面的**驗證**路線，然後再按一下**匯出模型**。</span><span class="sxs-lookup"><span data-stu-id="426ff-169">In Visual Studio, right-click the design surface of the **Validation** itinerary, and then click **Export Model**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="426ff-170">路線已經匯出成路線的資料庫，現在可供路線選取器管線元件。</span><span class="sxs-lookup"><span data-stu-id="426ff-170">The itinerary has been exported to the itinerary database and can now be used by the Itinerary Selector pipeline component.</span></span>  
  
2.  <span data-ttu-id="426ff-171">儲存專案的所有成品。</span><span class="sxs-lookup"><span data-stu-id="426ff-171">Save all project artifacts.</span></span>  
  
## <a name="steps"></a><span data-ttu-id="426ff-172">步驟</span><span class="sxs-lookup"><span data-stu-id="426ff-172">Steps</span></span>  
  
#### <a name="to-create-and-configure-an-esb-on-ramp"></a><span data-ttu-id="426ff-173">若要建立及設定 ESB 上手</span><span class="sxs-lookup"><span data-stu-id="426ff-173">To create and configure an ESB on-ramp</span></span>  
  
1.  <span data-ttu-id="426ff-174">按一下**啟動**在工作列上，指向**所有程式**，指向   **[!INCLUDE[prague](../includes/prague-md.md)]** ，然後按一下 **BizTalk Server 管理**.</span><span class="sxs-lookup"><span data-stu-id="426ff-174">Click **Start** on the taskbar, point to **All Programs**, point to **[!INCLUDE[prague](../includes/prague-md.md)]**, and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="426ff-175">在[!INCLUDE[prague](../includes/prague-md.md)]管理主控台中，展開  **BizTalk 群組**，依序展開**應用程式**，然後展開**Microsoft.Practices.ESB**。</span><span class="sxs-lookup"><span data-stu-id="426ff-175">In the [!INCLUDE[prague](../includes/prague-md.md)] Administration Console, expand **BizTalk Group**, expand **Applications**, and then expand **Microsoft.Practices.ESB**.</span></span>  
  
3.  <span data-ttu-id="426ff-176">以滑鼠右鍵按一下**接收位置**，指向 **新增**，然後按一下**單向接收位置**。</span><span class="sxs-lookup"><span data-stu-id="426ff-176">Right-click **Receive Locations**, point to **New**, and then click **One-way Receive Location**.</span></span>  
  
4.  <span data-ttu-id="426ff-177">在**選取接收埠**對話方塊中，按一下  **OnRamp.Itinerary**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="426ff-177">In the **Select a Receive Port** dialog box, click **OnRamp.Itinerary**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="426ff-178">在**接收位置屬性** 對話方塊中，輸入**OnRamp.Itinerary.HowTo**中**名稱**方塊。</span><span class="sxs-lookup"><span data-stu-id="426ff-178">In the **Receive Location Properties** dialog box, type **OnRamp.Itinerary.HowTo** in the **Name** box.</span></span>  
  
6.  <span data-ttu-id="426ff-179">在**類型**下拉式清單中，按一下 **檔案**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="426ff-179">In the **Type** drop-down list, click **FILE**, and then click **Configure**.</span></span>  
  
7.  <span data-ttu-id="426ff-180">在**FILE 傳輸屬性** 對話方塊中，輸入**C:\HowTos\DropFolder**中**接收資料夾**方塊，然後再按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="426ff-180">In the **FILE Transport Properties** dialog box, type **C:\HowTos\DropFolder** in the **Receive folder** box, and then click **OK**.</span></span>  
  
#### <a name="to-configure-the-on-ramp-to-perform-message-validation"></a><span data-ttu-id="426ff-181">若要設定上手執行訊息驗證</span><span class="sxs-lookup"><span data-stu-id="426ff-181">To configure the on-ramp to perform message validation</span></span>  
  
1.  <span data-ttu-id="426ff-182">在**接收位置屬性**對話方塊中，於**接收管線**下拉式清單中，按一下  **ItinerarySelectReceiveXml**，然後按一下省略符號按鈕 （...).</span><span class="sxs-lookup"><span data-stu-id="426ff-182">In the **Receive Location Properties** dialog box, in the **Receive pipeline** drop-down list, click **ItinerarySelectReceiveXml**, and then click the ellipsis button (...).</span></span>  
  
2.  <span data-ttu-id="426ff-183">使用**設定管線**對話方塊來設定下列**XML 解譯器**元件屬性：</span><span class="sxs-lookup"><span data-stu-id="426ff-183">Use the **Configure Pipeline** dialog box to configure the following **XML disassembler** component properties:</span></span>  
  
    1.  <span data-ttu-id="426ff-184">展開 GlobalBank.Esb 應用程式，然後按一下**結構描述**。</span><span class="sxs-lookup"><span data-stu-id="426ff-184">Expand the GlobalBank.Esb application, and then click **Schemas**.</span></span> <span data-ttu-id="426ff-185">以滑鼠右鍵按一下**GlobalBank.ESB.DynamicResolution.Schemas.NAOrderDoc**，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="426ff-185">Right-click **GlobalBank.ESB.DynamicResolution.Schemas.NAOrderDoc**, and then click **Properties**.</span></span> <span data-ttu-id="426ff-186">複製**名稱**和**組件**屬性並將它們貼至文字檔案。</span><span class="sxs-lookup"><span data-stu-id="426ff-186">Copy the **Name** and **Assembly** properties and paste them into a text file.</span></span>  
  
    2.  <span data-ttu-id="426ff-187">在**解譯**元件，請按一下**True**中**ValidateDocument**下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="426ff-187">In the **Disassemble** component, click **True** in the **ValidateDocument** drop-down list.</span></span>  
  
    3.  <span data-ttu-id="426ff-188">按一下**DocumentSpecNames**屬性，然後輸入完整名稱的結構描述。</span><span class="sxs-lookup"><span data-stu-id="426ff-188">Click the **DocumentSpecNames** property, and then type the fully qualified name of the schema.</span></span> <span data-ttu-id="426ff-189">名稱為開頭的完整限定的名稱，且後面逗號和擷取步驟中的組件資訊。</span><span class="sxs-lookup"><span data-stu-id="426ff-189">The fully qualified name starts with the name and is followed by a comma and the assembly information extracted in step a.</span></span> <span data-ttu-id="426ff-190">以下是一個範例：</span><span class="sxs-lookup"><span data-stu-id="426ff-190">The following is an example:</span></span>  
  
         <span data-ttu-id="426ff-191">GlobalBank.ESB.DynamicResolution.Schemas.NAOrderDoc，GlobalBank.ESB.DynamicResolution.Schemas，版本 = 2.0.0.0，Culture = neutral，PublicKeyToken = c2c8b2b87f54180a</span><span class="sxs-lookup"><span data-stu-id="426ff-191">GlobalBank.ESB.DynamicResolution.Schemas.NAOrderDoc, GlobalBank.ESB.DynamicResolution.Schemas, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c2c8b2b87f54180a</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="426ff-192">這是要驗證之結構描述的完整格式的名稱它包含的結構描述名稱和四個組件屬性： 組件名稱、 版本、 文化特性和公開金鑰語彙基元。</span><span class="sxs-lookup"><span data-stu-id="426ff-192">This is the fully qualified name of the schema to be validated; it is comprised of the schema name and four assembly properties: assembly name, version, culture, and public key token.</span></span> <span data-ttu-id="426ff-193">允許多個值。使用管道 (&#124;) 分隔多個結構描述的符號。</span><span class="sxs-lookup"><span data-stu-id="426ff-193">Multiple values are allowed; separate multiple schemas with a pipe (&#124;) symbol.</span></span>  
  
#### <a name="to-configure-the-itinerary-selector-pipeline-component"></a><span data-ttu-id="426ff-194">若要設定路線選取器管線元件</span><span class="sxs-lookup"><span data-stu-id="426ff-194">To configure the Itinerary Selector Pipeline component</span></span>  
  
1.  <span data-ttu-id="426ff-195">在**設定管線**對話方塊方塊中，設定下列各項**路線選取器**元件屬性：</span><span class="sxs-lookup"><span data-stu-id="426ff-195">In the **Configure Pipeline** dialog box, configure the following **Itinerary Selector** component properties:</span></span>  
  
    1.  <span data-ttu-id="426ff-196">按一下**ItineraryFactKey**屬性，，然後輸入**Resolver.Itinerary**。</span><span class="sxs-lookup"><span data-stu-id="426ff-196">Click the **ItineraryFactKey** property, and then type **Resolver.Itinerary**.</span></span>  
  
    2.  <span data-ttu-id="426ff-197">按一下**ResolverConnectionString**屬性，，然後輸入**路線：\\\name=Validation;**。</span><span class="sxs-lookup"><span data-stu-id="426ff-197">Click the **ResolverConnectionString** property, and then type **ITINERARY:\\\name=Validation;**.</span></span>  
  
    3.  <span data-ttu-id="426ff-198">按一下**確定**關閉**設定管線** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="426ff-198">Click **OK** to close the **Configure Pipeline** dialog box.</span></span>  
  
2.  <span data-ttu-id="426ff-199">按一下**確定**關閉**接收位置屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="426ff-199">Click **OK** to close the **Receive Location Properties** dialog box.</span></span>  
  
3.  <span data-ttu-id="426ff-200">在[!INCLUDE[prague](../includes/prague-md.md)]管理主控台中，以滑鼠右鍵按一下**OnRamp.Itinerary.HowTo**接收位置，然後按一下**啟用**。</span><span class="sxs-lookup"><span data-stu-id="426ff-200">In the [!INCLUDE[prague](../includes/prague-md.md)] Administration Console, right-click the **OnRamp.Itinerary.HowTo** receive location, and then click **Enable**.</span></span>  
  
#### <a name="to-test-the-message-validation-and-itinerary-selection"></a><span data-ttu-id="426ff-201">若要測試訊息驗證和行程選取項目</span><span class="sxs-lookup"><span data-stu-id="426ff-201">To test the message validation and itinerary selection</span></span>  
  
1.  <span data-ttu-id="426ff-202">在 Windows 檔案總管，瀏覽至 C:\HowTos。</span><span class="sxs-lookup"><span data-stu-id="426ff-202">In Windows Explorer, browse to C:\HowTos.</span></span>  
  
2.  <span data-ttu-id="426ff-203">複製 （不會移動） NAOrderDoc.xml DropFolder 資料夾。</span><span class="sxs-lookup"><span data-stu-id="426ff-203">Copy (do not move) NAOrderDoc.xml to the DropFolder folder.</span></span>  
  
3.  <span data-ttu-id="426ff-204">瀏覽至 C:\HowTos\Out。請確認 Validated%MessageID%.xml 已寫入至目錄。</span><span class="sxs-lookup"><span data-stu-id="426ff-204">Browse to C:\HowTos\Out. Verify that Validated%MessageID%.xml has been written to the directory.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="426ff-205">有效的訊息其行程為基礎的路由，依照預期方式完成。</span><span class="sxs-lookup"><span data-stu-id="426ff-205">The valid message completed its itinerary-based routing, as expected.</span></span>  
  
4.  <span data-ttu-id="426ff-206">Validated%MessageID%.xml 刪除 Out 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="426ff-206">Delete Validated%MessageID%.xml from the Out folder.</span></span>  
  
5.  <span data-ttu-id="426ff-207">在 Windows 檔案總管，瀏覽至 C:\HowTos。</span><span class="sxs-lookup"><span data-stu-id="426ff-207">In Windows Explorer, browse to C:\HowTos.</span></span>  
  
6.  <span data-ttu-id="426ff-208">複製 （不會移動） Invalid.xml DropFolder 資料夾。</span><span class="sxs-lookup"><span data-stu-id="426ff-208">Copy (do not move) Invalid.xml to the DropFolder folder.</span></span>  
  
7.  <span data-ttu-id="426ff-209">瀏覽至 C:\HowTos\Out。請確認已傳送任何新訊息。</span><span class="sxs-lookup"><span data-stu-id="426ff-209">Browse to C:\HowTos\Out. Verify that no new message has been delivered.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="426ff-210">無法驗證訊息。因此，行程為基礎的路由無法完成。</span><span class="sxs-lookup"><span data-stu-id="426ff-210">The message could not be validated; therefore, itinerary-based routing could not be completed.</span></span>  
  
8.  <span data-ttu-id="426ff-211">按一下**啟動**在工作列上，指向**系統管理工具**，然後按一下**事件檢視器**。</span><span class="sxs-lookup"><span data-stu-id="426ff-211">Click **Start** on the taskbar, point to **Administrative Tools**, and then click **Event Viewer**.</span></span>  
  
9. <span data-ttu-id="426ff-212">在 事件檢視器中，展開**Windows 記錄檔**，然後按一下**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="426ff-212">In Event Viewer, expand **Windows Logs**, and then click **Application**.</span></span>  
  
10. <span data-ttu-id="426ff-213">找出最近的事件位置**來源**是 **[!INCLUDE[prague](../includes/prague-md.md)]** ，而**事件識別碼**是**5719**。</span><span class="sxs-lookup"><span data-stu-id="426ff-213">Locate a recent event where the **Source** is **[!INCLUDE[prague](../includes/prague-md.md)]**, and the **Event ID** is **5719**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="426ff-214">提交和失敗的無效訊息應用程式事件記錄檔產生的例外狀況的項目。</span><span class="sxs-lookup"><span data-stu-id="426ff-214">The submission and failure of the invalid message resulted in an exception entry to the application event log.</span></span>  
  
11. <span data-ttu-id="426ff-215">在[!INCLUDE[prague](../includes/prague-md.md)]管理主控台中，以滑鼠右鍵按一下**OnRamp.Itinerary.HowTo**接收位置，然後按一下**停用**。</span><span class="sxs-lookup"><span data-stu-id="426ff-215">In the [!INCLUDE[prague](../includes/prague-md.md)] Administration Console, right-click the **OnRamp.Itinerary.HowTo** receive location, and then click **Disable**.</span></span>  
  
12. <span data-ttu-id="426ff-216">之後**OnRamp.Itinerary.HowTo**接收位置已停用，以滑鼠右鍵按一下，，然後按一下**刪除**。</span><span class="sxs-lookup"><span data-stu-id="426ff-216">After the **OnRamp.Itinerary.HowTo** receive location is disabled, right-click it, and then click **Delete**.</span></span> <span data-ttu-id="426ff-217">在**確認刪除接收位置**對話方塊中，按一下 **是**。</span><span class="sxs-lookup"><span data-stu-id="426ff-217">In the **Confirm delete receive location** dialog box, click **Yes**.</span></span>  
  
## <a name="additional-resources"></a><span data-ttu-id="426ff-218">其他資源</span><span class="sxs-lookup"><span data-stu-id="426ff-218">Additional Resources</span></span>  
 <span data-ttu-id="426ff-219">如需詳細資訊，請參閱下列相關主題：</span><span class="sxs-lookup"><span data-stu-id="426ff-219">For more information, see the following related topics:</span></span>  
  
-   [<span data-ttu-id="426ff-220">如何： 選取 使用商務規則原則路線</span><span class="sxs-lookup"><span data-stu-id="426ff-220">How to: Select an Itinerary Using a Business Rules Policy</span></span>](../esb-toolkit/how-to-select-an-itinerary-using-a-business-rules-policy.md)  
  
-   [<span data-ttu-id="426ff-221">開發活動</span><span class="sxs-lookup"><span data-stu-id="426ff-221">Development Activities</span></span>](../esb-toolkit/development-activities.md)  
  
-   [<span data-ttu-id="426ff-222">安裝及執行動態解析範例</span><span class="sxs-lookup"><span data-stu-id="426ff-222">Installing and Running the Dynamic Resolution Sample</span></span>](../esb-toolkit/installing-and-running-the-dynamic-resolution-sample.md)