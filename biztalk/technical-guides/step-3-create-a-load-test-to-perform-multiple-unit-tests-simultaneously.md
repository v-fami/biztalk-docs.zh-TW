---
title: 步驟 3： 建立負載測試，以便同時執行多個單元測試 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b5dd7e31-7188-4edf-9513-ea2725950b47
caps.latest.revision: 19
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d946c48c1bcaca420347771e73089e5535ab1229
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37002703"
---
# <a name="step-3-create-a-load-test-to-perform-multiple-unit-tests-simultaneously"></a><span data-ttu-id="abab9-102">步驟 3： 建立負載測試，以便同時執行多個單元測試</span><span class="sxs-lookup"><span data-stu-id="abab9-102">Step 3: Create a Load Test to Perform Multiple Unit Tests Simultaneously</span></span>
<span data-ttu-id="abab9-103">負載測試執行多個執行個體的其中一個或多個單元測試，以便您可以測量您的應用程式效能和處理負載的能力。</span><span class="sxs-lookup"><span data-stu-id="abab9-103">Load tests run multiple instances of one or more unit tests so that you can measure your application's performance and ability to handle load.</span></span> <span data-ttu-id="abab9-104">Visual Studio 2010 負載測試的主要元件包括：</span><span class="sxs-lookup"><span data-stu-id="abab9-104">The primary components of a Visual Studio 2010 load test include:</span></span>  
  
- <span data-ttu-id="abab9-105">**案例**– 讓您設定測試的負載模式、 測試混合模型、 測試混合、 網路混合和 Web 瀏覽器混合負載測試的區段。</span><span class="sxs-lookup"><span data-stu-id="abab9-105">**Scenarios** – The section of a load test where you configure the test load pattern, test mix model, test mix, network mix and Web browser mix.</span></span> <span data-ttu-id="abab9-106">案例容納模擬複雜的真實世界工作負載設定檔的複雜度。</span><span class="sxs-lookup"><span data-stu-id="abab9-106">Scenarios accommodate the complexity of simulating complex real world work load profiles.</span></span> <span data-ttu-id="abab9-107">如需完整的清單，所有的負載測試情節屬性，請參閱[負載測試情節屬性](http://go.microsoft.com/fwlink/?LinkId=208327)(http://go.microsoft.com/fwlink/?LinkId=208327)。</span><span class="sxs-lookup"><span data-stu-id="abab9-107">For a comprehensive listing of all load test scenario properties see [Load Test Scenario Properties](http://go.microsoft.com/fwlink/?LinkId=208327) (http://go.microsoft.com/fwlink/?LinkId=208327).</span></span>  
  
- <span data-ttu-id="abab9-108">**計數器集合**– 讓您建立的特定群組或 「 集 」 效能計數器的負載測試執行時，要收集的負載測試的區段。</span><span class="sxs-lookup"><span data-stu-id="abab9-108">**Counter Sets** – The section of a load test where you create particular groupings or “Sets” of performance counters to be collected while the load test is running.</span></span> <span data-ttu-id="abab9-109">預設會提供數個預先定義的計數器集合，而且可以加入自訂計數器集合。</span><span class="sxs-lookup"><span data-stu-id="abab9-109">Several predefined counter sets are provided by default and custom counter sets can be added.</span></span> <span data-ttu-id="abab9-110">例如若要評估的網路效能，您可以建立自訂的計數器設定、 新增相關的網路效能計數器，以及將它儲存到可用的計數器集合的清單。</span><span class="sxs-lookup"><span data-stu-id="abab9-110">For example to evaluate Network performance you can create a custom counter set, add the relevant Network performance counters and save it to the list of available counter sets.</span></span> <span data-ttu-id="abab9-111">如需建立及儲存的負載測試計數器集合的詳細資訊，請參閱[指定在負載測試中的 電腦的計數器集合](http://go.microsoft.com/fwlink/?LinkId=208328)(http://go.microsoft.com/fwlink/?LinkId=208328)。</span><span class="sxs-lookup"><span data-stu-id="abab9-111">For more information about creating and saving counter sets for load tests see [Specifying the Counter Sets for Computers in a Load Test](http://go.microsoft.com/fwlink/?LinkId=208328) (http://go.microsoft.com/fwlink/?LinkId=208328).</span></span>  
  
- <span data-ttu-id="abab9-112">**回合設定**– 回合設定定義多個面向的負載測試、 測試持續期間，在負載測試期間，會與不同的電腦相關聯的計數器集合包括各種測試驗證選項，並測試結果的儲存體選項。</span><span class="sxs-lookup"><span data-stu-id="abab9-112">**Run Settings** – Run settings define multiple aspects of a load test, including the test duration, the counter sets that are associated with various computers during the load test, various test validation options, and test results storage options.</span></span> <span data-ttu-id="abab9-113">您可以建立並儲存每個負載測試中，多個執行的設定，然後選取 執行測試時要使用特定的設定。</span><span class="sxs-lookup"><span data-stu-id="abab9-113">You can create and store multiple run settings for each load test, and then select a particular setting to use when you run the test.</span></span> <span data-ttu-id="abab9-114">使用新增負載測試精靈建立負載測試時，會將初始回合設定加入至負載測試。</span><span class="sxs-lookup"><span data-stu-id="abab9-114">An initial run setting is added to your load test when you create your load test with the New Load Test Wizard.</span></span> <span data-ttu-id="abab9-115">如需完整的所有負載測試回合設定屬性清單，請參閱[負載測試回合設定屬性](http://go.microsoft.com/fwlink/?LinkId=208329)(http://go.microsoft.com/fwlink/?LinkId=208329)。</span><span class="sxs-lookup"><span data-stu-id="abab9-115">For a comprehensive listing of all load test run setting properties see [Load Test Run Setting Properties](http://go.microsoft.com/fwlink/?LinkId=208329) (http://go.microsoft.com/fwlink/?LinkId=208329).</span></span>  
  
  <span data-ttu-id="abab9-116">建立使用新增負載測試精靈]，編輯使用負載測試編輯器中，並在 [負載測試分析器分析負載測試。</span><span class="sxs-lookup"><span data-stu-id="abab9-116">Load tests are created using the New Load Test Wizard, edited with the Load Test Editor, and analyzed in the Load Test Analyzer.</span></span> <span data-ttu-id="abab9-117">所有這些工具包含在 Microsoft Visual Studio Ultimate 版本中。</span><span class="sxs-lookup"><span data-stu-id="abab9-117">All these tools are included in Microsoft Visual Studio Ultimate edition.</span></span> <span data-ttu-id="abab9-118">如需建立和編輯 Visual Studio 2010 Ultimate edition 中的負載測試的詳細資訊，請參閱[建立和編輯負載測試](http://go.microsoft.com/fwlink/?LinkId=208308)(http://go.microsoft.com/fwlink/?LinkId=208308)。</span><span class="sxs-lookup"><span data-stu-id="abab9-118">For more information about creating and editing load tests in Visual Studio 2010 Ultimate edition see [Creating and Editing Load Tests](http://go.microsoft.com/fwlink/?LinkId=208308) (http://go.microsoft.com/fwlink/?LinkId=208308).</span></span>  
  
  <span data-ttu-id="abab9-119">在測試專案中所述的步驟，在下列各節來新增負載測試的後續[步驟 1： 建立單元測試，以提交至 BizTalk Server 的文件](../technical-guides/step-1-create-a-unit-test-to-submit-documents-to-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="abab9-119">Follow the steps in the sections below to add a load test to the test project described in [Step 1: Create a Unit Test to Submit Documents to BizTalk Server](../technical-guides/step-1-create-a-unit-test-to-submit-documents-to-biztalk-server.md).</span></span> <span data-ttu-id="abab9-120">這些步驟也會說明如何設定**案例**，**計數器集合**，並**回合設定**負載測試。</span><span class="sxs-lookup"><span data-stu-id="abab9-120">These steps also describe how to configure the **Scenarios**, **Counter Sets**, and **Run Settings** for a load test.</span></span>  
  
##  <a name="BKMK_StepLoadTest"></a> <span data-ttu-id="abab9-121">將負載測試加入負載測試情節、 計數器集合，並設定回合設定</span><span class="sxs-lookup"><span data-stu-id="abab9-121">Add a Load Test and Configure the Load Test Scenario, Counter Sets, and Run Settings</span></span>  
 <span data-ttu-id="abab9-122">本主題描述如何使用**新增負載測試精靈**新增負載測試專案的測試，以及如何設定負載測試以符合特定需求。</span><span class="sxs-lookup"><span data-stu-id="abab9-122">This topic describes how to use the **New Load Test Wizard** to add a load test to a test project and how to configure the load test to meet specific needs.</span></span>  
  
### <a name="use-the-new-load-test-wizard-to-add-a-load-test-to-the-test-project"></a><span data-ttu-id="abab9-123">使用新增負載測試精靈 將負載測試新增至測試專案</span><span class="sxs-lookup"><span data-stu-id="abab9-123">Use the New Load Test Wizard to Add a Load Test to the Test Project</span></span>  
 <span data-ttu-id="abab9-124">請遵循下列步驟來新增負載測試來使用新增負載測試精靈 的測試專案。</span><span class="sxs-lookup"><span data-stu-id="abab9-124">Follow these steps to add a load test to a test project using the New Load Test Wizard.</span></span>  
  
1.  <span data-ttu-id="abab9-125">開啟**負載測試**如果它尚未開啟的 Visual Studio 2010 中的方案。</span><span class="sxs-lookup"><span data-stu-id="abab9-125">Open the **Load Test** solution in Visual Studio 2010 if it is not already open.</span></span>  
  
2.  <span data-ttu-id="abab9-126">將資料夾加入 BTSLoad 專案;這個資料夾將包含此專案的過程中建立任何負載測試。</span><span class="sxs-lookup"><span data-stu-id="abab9-126">Add a folder to the BTSLoad project; this folder will contain any load tests that are created as part of this project.</span></span> <span data-ttu-id="abab9-127">在 [方案總管] 中，以滑鼠右鍵按一下 BTSLoad 專案，指向**新增**，然後按一下**新資料夾**。</span><span class="sxs-lookup"><span data-stu-id="abab9-127">In Solution Explorer, right-click the BTSLoad project, point to **Add**, and click **New Folder**.</span></span> <span data-ttu-id="abab9-128">反白顯示文字的資料夾圖示**NewFolder1** BTSLoad 專案中，型別將會出現**LoadTests**變更醒目提示的文字，並按 Enter 鍵以完成建立資料夾 C:\Projects\LoadTest\BTSLoad\LoadTests。</span><span class="sxs-lookup"><span data-stu-id="abab9-128">A folder icon with the highlighted text **NewFolder1** will appear under the BTSLoad project, type **LoadTests** to change the highlighted text and press the Enter key to complete creation of the folder C:\Projects\LoadTest\BTSLoad\LoadTests.</span></span>  
  
3.  <span data-ttu-id="abab9-129">在 [方案總管] 中，以滑鼠右鍵按一下**BTSLoad**專案，指向**新增**，然後按一下**負載測試**啟動**新增負載測試精靈**.</span><span class="sxs-lookup"><span data-stu-id="abab9-129">In Solution Explorer, right-click on the **BTSLoad** project, point to **Add**, and then click **Load Test** to start the **New Load Test Wizard**.</span></span>  
  
4.  <span data-ttu-id="abab9-130">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="abab9-130">Click **Next**.</span></span>  
  
5.  <span data-ttu-id="abab9-131">上**編輯負載測試情節的設定**下方的頁面上**輸入負載測試情節的名稱：** 類型**BTS_Messaging_Step**。</span><span class="sxs-lookup"><span data-stu-id="abab9-131">On the **Edit Settings for a Load Test Scenario** page under **Enter a name for the load test scenario:** type **BTS_Messaging_Step**.</span></span> <span data-ttu-id="abab9-132">底下**考慮時間特性**選取**不使用考慮時間**，然後按一下 [**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="abab9-132">Under **Think time profile** select **Do not use think times** and then click **Next**.</span></span>  
  
6.  <span data-ttu-id="abab9-133">在 [**編輯負載模式設定為負載測試情節**頁面上，選取**逐步執行負載**，輸入下列值，然後按一下**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="abab9-133">On the **Edit load pattern settings for a load test scenario** page select **Step load**, enter the values below and then click **Next**.</span></span>  
  
    -   <span data-ttu-id="abab9-134">**啟動使用者計數：** 30 位使用者</span><span class="sxs-lookup"><span data-stu-id="abab9-134">**Start user count:** 30 users</span></span>  
  
    -   <span data-ttu-id="abab9-135">**逐步執行持續期間：** 60 秒</span><span class="sxs-lookup"><span data-stu-id="abab9-135">**Step duration:** 60 seconds</span></span>  
  
    -   <span data-ttu-id="abab9-136">**逐步執行使用者計數：** 10 位使用者</span><span class="sxs-lookup"><span data-stu-id="abab9-136">**Step user count:** 10 users</span></span>  
  
    -   <span data-ttu-id="abab9-137">**最大使用者計數**80 的使用者</span><span class="sxs-lookup"><span data-stu-id="abab9-137">**Maximum user count** 80 users</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="abab9-138">套用的步驟負載模式的設定時，您應該計算所需的所有步驟會增加完成的時間量。</span><span class="sxs-lookup"><span data-stu-id="abab9-138">When applying settings for a step load pattern you should calculate the amount of time required for all step increments to complete.</span></span> <span data-ttu-id="abab9-139">比方說，使用上述的負載測試指定的負載模式設定將需要 5 分鐘才能完成所有的 60 秒遞增時跳緩慢增加從 30 80 的使用者。</span><span class="sxs-lookup"><span data-stu-id="abab9-139">For example, using the load pattern settings specified above the load test will need 5 minutes to complete all of the 60 second step increments when ramping up from 30 to 80 users.</span></span> <span data-ttu-id="abab9-140">新增負載測試精靈 選項來指定負載測試的長度會看到您的最後一頁，其中將會**負載測試的持續時間**。</span><span class="sxs-lookup"><span data-stu-id="abab9-140">On the last page of the New Load Test Wizard you will be presented with options for specifying the length of the load test, one of which will be **Load Test Duration**.</span></span> <span data-ttu-id="abab9-141">如果您已經有針對計算所需的所有步驟完成簡單的工作，以輸入值 （在此情況下的 5 分鐘） 後，就遞增的時間**負載測試持續期間**。</span><span class="sxs-lookup"><span data-stu-id="abab9-141">If you have already calculated the time required for all step increments to complete then it is a straightforward task to enter the value (5 minutes in this case) for **Load Test Duration**.</span></span>  
  
7.  <span data-ttu-id="abab9-142">在上**選取負載測試的測試混合模型**頁面上，選取**依據虛擬使用者數目**，然後按一下 [**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="abab9-142">On the **Select a test mix model for the load test** page select **Based on the number of virtual users** and then click **Next**.</span></span>  
  
8.  <span data-ttu-id="abab9-143">在 [**將測試加入至負載測試情節，並且編輯測試混合**頁面上，按一下**新增**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="abab9-143">On the **Add tests to the load test scenario and edit the test mix** page click the **Add** button.</span></span>  
  
9. <span data-ttu-id="abab9-144">底下**可用的測試**按兩下**BTSMessaging**並**BTSMessaging2**若要將這些單元測試新增到清單**選取的測試**。</span><span class="sxs-lookup"><span data-stu-id="abab9-144">Under **Available tests** double-click **BTSMessaging** and **BTSMessaging2** to add these unit tests to the list of **Selected tests**.</span></span> <span data-ttu-id="abab9-145">按一下 [ **[確定]** ，然後按一下**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="abab9-145">Click **OK** and then click **Next**.</span></span>  
  
10. <span data-ttu-id="abab9-146">在上**將網路類型加入至負載測試情節，並且編輯網路混合**頁面上確認**網路類型**設定為**LAN**與**發佈**的**100%** ，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="abab9-146">On the **Add network types to a load test scenario and edit the network mix** page verify that **Network Type** is set to **LAN** with a **Distribution** of **100%** and then click **Next**.</span></span>  
  
11. <span data-ttu-id="abab9-147">在 [**指定在負載測試回合期間以計數器集合監視的電腦**頁面上，按一下**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="abab9-147">On the **Specify computers to monitor with counter sets during load test run** page click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="abab9-148">不要將電腦新增至目前的負載測試。</span><span class="sxs-lookup"><span data-stu-id="abab9-148">Do not add computers to the load test at this time.</span></span> <span data-ttu-id="abab9-149">新增負載測試精靈只允許您將建立電腦關聯以預先定義的計數器集合，而且此負載測試需要預先定義的兩個使用並*自訂*計數器集合。</span><span class="sxs-lookup"><span data-stu-id="abab9-149">The New Load Test Wizard will only allow you to associate computers with predefined counter sets, and this load test requires the use of both predefined and *custom* counter sets.</span></span> <span data-ttu-id="abab9-150">精靈完成為止，並儲存在負載測試之後，您就可以編輯負載測試，以便加入自訂計數器集合，並設定要監視使用這兩個預先定義的電腦的負載測試*和*自訂計數器集合。</span><span class="sxs-lookup"><span data-stu-id="abab9-150">After the wizard is complete and the load test is saved you can edit the load test to add custom counter sets and configure the load test to monitor computers using both predefined *and* custom counter sets.</span></span>  
  
     <span data-ttu-id="abab9-151">在 **檢閱並編輯執行負載測試設定**頁面上，輸入下列值：</span><span class="sxs-lookup"><span data-stu-id="abab9-151">On the **Review and edit run settings for a load test** page enter the following values:</span></span>  
  
    1.  <span data-ttu-id="abab9-152">選取 **負載測試持續期間**。</span><span class="sxs-lookup"><span data-stu-id="abab9-152">Select **Load test duration**.</span></span>  
  
    2.  <span data-ttu-id="abab9-153">**準備持續期間 （時分秒）** 30 秒</span><span class="sxs-lookup"><span data-stu-id="abab9-153">**Warm-up duration (hh mm ss)** 30 seconds</span></span>  
  
    3.  <span data-ttu-id="abab9-154">**執行持續期間 （時分秒）** 5 分鐘</span><span class="sxs-lookup"><span data-stu-id="abab9-154">**Run duration (hh mm ss)** 5 minutes</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="abab9-155">配置的時間**回合持續期限**應該等於需要的所有步驟以完成上述，步驟 5 或 5 分鐘，此範例中所述的遞增的時間量。</span><span class="sxs-lookup"><span data-stu-id="abab9-155">The time allocated for **Run duration** should equal the amount of time required for all step increments to complete as described in step 5 above, or 5 minutes for this example.</span></span>  
  
    4.  <span data-ttu-id="abab9-156">**取樣率**5 秒</span><span class="sxs-lookup"><span data-stu-id="abab9-156">**Sampling rate** 5 seconds</span></span>  
  
    5.  <span data-ttu-id="abab9-157">**描述**（選擇性），輸入負載測試的描述。</span><span class="sxs-lookup"><span data-stu-id="abab9-157">**Description** (optional), Enter a description for the load test here.</span></span>  
  
    6.  <span data-ttu-id="abab9-158">**測試失敗時儲存記錄檔**，則為 True</span><span class="sxs-lookup"><span data-stu-id="abab9-158">**Save Log on Test Failure** True</span></span>  
  
    7.  <span data-ttu-id="abab9-159">**驗證層級**低-叫用標記為 「 低的驗證規則</span><span class="sxs-lookup"><span data-stu-id="abab9-159">**Validation level** Low – invoke validation rules marked low</span></span>  
  
12. <span data-ttu-id="abab9-160">按一下 **完成**以關閉 新增負載測試精靈。</span><span class="sxs-lookup"><span data-stu-id="abab9-160">Click **Finish** to close the New Load Test Wizard.</span></span>  
  
13. <span data-ttu-id="abab9-161">按一下 **檔案**功能表，然後選取**儲存\<負載測試名稱\>.loadtest 為**。</span><span class="sxs-lookup"><span data-stu-id="abab9-161">Click the **File** menu and select **Save \<Load Test Name\>.loadtest As**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="abab9-162">在此範例中，<Load Test Name>將是由 Visual Studio 2010 中，通常 loadtestx.loadtest 指派至負載測試檔案的名稱，除非檔案的名稱已被手動變更。</span><span class="sxs-lookup"><span data-stu-id="abab9-162">In this example, <Load Test Name> will be the name assigned to the load test file by Visual Studio 2010, typically loadtestx.loadtest, unless the name of the file has already been manually changed.</span></span>  
  
14. <span data-ttu-id="abab9-163">將檔案儲存至稍早建立的 C:\Projects\LoadTest\BTSLoad\LoadTests 目錄。</span><span class="sxs-lookup"><span data-stu-id="abab9-163">Save the file to the C:\Projects\LoadTest\BTSLoad\LoadTests directory created earlier.</span></span> <span data-ttu-id="abab9-164">它可能會很有用的案例中，所使用的名稱儲存檔案在此範例中的情節名稱會是 BTS_Messaging_Step，因此 loadtest 檔案會儲存為 C:\Projects\LoadTest\BTSLoad\LoadTests\BTS_Messaging_Step.loadtest。</span><span class="sxs-lookup"><span data-stu-id="abab9-164">It may be useful to save the file with the name used for the scenario; in this example the scenario name is BTS_Messaging_Step so the loadtest file would be saved as C:\Projects\LoadTest\BTSLoad\LoadTests\BTS_Messaging_Step.loadtest.</span></span>  
  
###  <a name="BKMK_BTSCounters"></a> <span data-ttu-id="abab9-165">新增自訂計數器集合加入至量值的 BizTalk Server 關鍵效能指標 (KPI)</span><span class="sxs-lookup"><span data-stu-id="abab9-165">Add a Custom Counter Set to Measure BizTalk Server Key Performance Indicators (KPI)</span></span>  
 <span data-ttu-id="abab9-166">請遵循下列步驟來新增計數器，與量值來判斷最大持續輸送量 (MST) 的 BizTalk Server 應用程式所需的 BizTalk Server KPI 的效能計數器集合：</span><span class="sxs-lookup"><span data-stu-id="abab9-166">Follow these steps to add a counter set with performance counters that measure BizTalk Server KPI required for determining Maximum Sustainable Throughput (MST) of the BizTalk Server application:</span></span>  
  
1. <span data-ttu-id="abab9-167">在方案總管 中按兩下在負載測試您在上一節，在負載測試編輯器中檢視負載測試中建立。</span><span class="sxs-lookup"><span data-stu-id="abab9-167">In Solution Explorer double-click the load test that you created in the previous section to view the load test in Load Test editor.</span></span>  
  
2. <span data-ttu-id="abab9-168">在負載測試編輯器 中，按一下以展開**計數器集合**。</span><span class="sxs-lookup"><span data-stu-id="abab9-168">In Load Test editor, click to expand **Counter Sets**.</span></span> <span data-ttu-id="abab9-169">請注意，沒有預先定義的計數器集合，以便讓 BizTalk Server，因此必須加入 「 BizTalk Server 」 計數器集合的計數器清單的自訂設定。</span><span class="sxs-lookup"><span data-stu-id="abab9-169">Notice that there is no predefined counter set for BizTalk Server, therefore a custom “BizTalk Server” counter set must be added to the list of counter sets.</span></span>  
  
3. <span data-ttu-id="abab9-170">以滑鼠右鍵按一下**計數器集合**，然後選取**加入自訂計數器集合**。</span><span class="sxs-lookup"><span data-stu-id="abab9-170">Right-click **Counter Sets** and select **Add Custom Counter Set**.</span></span> <span data-ttu-id="abab9-171">根據預設，此動作會建立自訂計數器集合名稱**Custom1**。</span><span class="sxs-lookup"><span data-stu-id="abab9-171">By default this action will create a custom counter set with the name **Custom1**.</span></span>  
  
4. <span data-ttu-id="abab9-172">以滑鼠右鍵按一下**Custom1**計數器設定，然後選取**屬性**若要將焦點設定為**屬性**Custom1 計數器集合 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="abab9-172">Right-click the **Custom1** counter set and select **Properties** to set focus to the **Properties** dialog for the Custom1 counter set.</span></span>  
  
5. <span data-ttu-id="abab9-173">按兩下名稱**Custom1**中**屬性**對話方塊中，輸入**BizTalk**然後按 ENTER 鍵來重新命名自訂計數器集合加入至**BizTalk**.</span><span class="sxs-lookup"><span data-stu-id="abab9-173">Double-click the name **Custom1** in the **Properties** dialog, type **BizTalk** and then press the ENTER key to rename the custom counter set to **BizTalk**.</span></span>  
  
6. <span data-ttu-id="abab9-174">在 [負載測試編輯器] 中，以滑鼠右鍵按一下**BizTalk**計數器設定，然後選取**新增計數器**。</span><span class="sxs-lookup"><span data-stu-id="abab9-174">In Load Test Editor, right-click the **BizTalk** counter set and select **Add Counters**.</span></span>  
  
7. <span data-ttu-id="abab9-175">底下**電腦**，輸入 BizTalk Server 群組，以顯示包含 BizTalk Server 效能計數器的效能監視器類別中的其中一個 BizTalk Server 電腦的名稱。</span><span class="sxs-lookup"><span data-stu-id="abab9-175">Under **Computer**, type the name of one of the BizTalk Server computers in the BizTalk Server group to display performance monitor categories that include BizTalk Server performance counters.</span></span>  
  
   > [!IMPORTANT]
   >  <span data-ttu-id="abab9-176">若要確保列出所有的 BizTalk Server 效能類別和效能計數器，您可能需要輸入完整的網域名稱 （或 IP 位址） 中的 BizTalk Server 群組中，您可能也需要啟動下列主控件執行個體上BizTalk Server 電腦。</span><span class="sxs-lookup"><span data-stu-id="abab9-176">To ensure that all BizTalk Server performance categories and performance counters are listed, you may need to type in the fully qualified domain name (or IP Address) of a BizTalk Server in the group and you may also need to start the instances of the following hosts on the BizTalk Server computer.</span></span>  
   > 
   > - <span data-ttu-id="abab9-177">繫結至協調流程會在負載測試期間執行的 BizTalk 主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="abab9-177">Instances of BizTalk hosts which are bound to orchestrations that will run during the load test.</span></span>  
   >   -   <span data-ttu-id="abab9-178">設定為傳送或接收處理常式會在負載測試期間執行的配接器的 BizTalk 主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="abab9-178">Instances of BizTalk hosts configured as send or receive handlers for adapters that will run during the load test.</span></span>  
  
8. <span data-ttu-id="abab9-179">步驟 24、 選取選項至預設主機中執行，選取主機類型的預設，然後在32 或 64 位元處理序中執行測試，選取的選項64 位元電腦上，在 64 位元處理序中執行測試。</span><span class="sxs-lookup"><span data-stu-id="abab9-179">BizTalk Server provides quite an extensive set of performance counters.</span></span> <span data-ttu-id="abab9-180">針對步驟 25，選取**將個別測試標示為失敗，如果執行時間超過**並保留預設值為選取的 30 分鐘。</span><span class="sxs-lookup"><span data-stu-id="abab9-180">For purposes of determining the Maximum Sustainable Performance (MST) of a BizTalk Server application you only need to add the following BizTalk Server performance counters to the **BizTalk** custom counter set:</span></span>  
  
   |<span data-ttu-id="abab9-181">27b 步驟中，選取核取方塊test 目錄中的組件使用載入內容，然後按一下另存新檔。</span><span class="sxs-lookup"><span data-stu-id="abab9-181">Performance Category</span></span>|<span data-ttu-id="abab9-182">效能計數器</span><span class="sxs-lookup"><span data-stu-id="abab9-182">Performance Counter</span></span>|  
   |--------------------------|-------------------------|  
   |<span data-ttu-id="abab9-183">處理器</span><span class="sxs-lookup"><span data-stu-id="abab9-183">Processor</span></span>|<span data-ttu-id="abab9-184">在另存新檔對話方塊方塊中，確認名稱BizTalkLoadTest旁輸入檔名，然後按一下儲存。</span><span class="sxs-lookup"><span data-stu-id="abab9-184">% Processor Time for the _Total counter instance.</span></span>|  
   |<span data-ttu-id="abab9-185">您現在已加入至方案的測試設定檔。</span><span class="sxs-lookup"><span data-stu-id="abab9-185">BizTalk:Message Box: General Counters</span></span>|<span data-ttu-id="abab9-186">多工緩衝處理大小 *\<BizTalk MessageBox 資料庫名稱\>*:*\<SQL Server 執行個體名稱\>* 計數器執行個體。</span><span class="sxs-lookup"><span data-stu-id="abab9-186">Spool Size for the *\<BizTalk MessageBox database name\>*:*\<SQL Server instance name\>* counter instance.</span></span> <span data-ttu-id="abab9-187">**注意︰***\<BizTalk MessageBox 資料庫名稱\>* 並 *\<SQL Server 執行個體名稱\>* 只是預留位置BizTalk MessageBox 資料庫和裝載 BizTalk MessageBox 資料庫的 SQL Server 執行個體的實際名稱。</span><span class="sxs-lookup"><span data-stu-id="abab9-187">**Note:**  *\<BizTalk MessageBox database name\>* and *\<SQL Server instance name\>* are just placeholders for the actual names of the BizTalk MessageBox database and the SQL Server instance that houses the BizTalk MessageBox database.</span></span> <span data-ttu-id="abab9-188">應與 BizTalk MessageBox 資料庫和相關聯的 SQL Server 執行個體的實際名稱取代這些預留位置。</span><span class="sxs-lookup"><span data-stu-id="abab9-188">These placeholders should be replaced with the actual names of the BizTalk MessageBox database and associated SQL Server instance.</span></span>|  
   |<span data-ttu-id="abab9-189">BizTalk:傳訊</span><span class="sxs-lookup"><span data-stu-id="abab9-189">BizTalk:Messaging</span></span>|<span data-ttu-id="abab9-190">文件數/秒的接收主控件計數器執行個體。</span><span class="sxs-lookup"><span data-stu-id="abab9-190">Documents received/Sec for the receive host counter instance.</span></span><br /><br /> <span data-ttu-id="abab9-191">文件處理每秒傳輸主控件計數器執行個體。</span><span class="sxs-lookup"><span data-stu-id="abab9-191">Documents processed/Sec for the transmit host counter instance.</span></span>|  
   |<span data-ttu-id="abab9-192">BizTalk：訊息代理程式</span><span class="sxs-lookup"><span data-stu-id="abab9-192">BizTalk:Message Agent</span></span>|<span data-ttu-id="abab9-193">文件的訊息傳遞內送速率接收主控件。</span><span class="sxs-lookup"><span data-stu-id="abab9-193">Message delivery incoming rate for the document receive host.</span></span>|  
   |<span data-ttu-id="abab9-194">BizTalk：訊息代理程式</span><span class="sxs-lookup"><span data-stu-id="abab9-194">BizTalk:Message Agent</span></span>|<span data-ttu-id="abab9-195">文件傳輸主控件的訊息發佈外寄速率。</span><span class="sxs-lookup"><span data-stu-id="abab9-195">Message publishing outgoing rate for the document transmit host.</span></span>|  
   |<span data-ttu-id="abab9-196">XLANG/s 協調流程</span><span class="sxs-lookup"><span data-stu-id="abab9-196">XLANG/s Orchestrations</span></span>|<span data-ttu-id="abab9-197">協調流程每秒完成的協調流程處理主控件。</span><span class="sxs-lookup"><span data-stu-id="abab9-197">Orchestrations completed/sec for the Orchestration processing host.</span></span>|  
  
### <a name="modify-run-settings-to-map-counter-sets-to-appropriate-computers"></a><span data-ttu-id="abab9-198">修改執行的設定，以將計數器集合對應至適當的電腦</span><span class="sxs-lookup"><span data-stu-id="abab9-198">Modify Run Settings to Map Counter Sets to Appropriate Computers</span></span>  
 <span data-ttu-id="abab9-199">請遵循下列步驟來將負載測試的適當的電腦與適當的計數器集合對應：</span><span class="sxs-lookup"><span data-stu-id="abab9-199">Follow these steps to map the appropriate counter sets with the appropriate computers for the load test:</span></span>  
  
1.  <span data-ttu-id="abab9-200">在 **負載測試編輯器**，以滑鼠右鍵按一下**回合設定**，然後選取**管理計數器集合**。</span><span class="sxs-lookup"><span data-stu-id="abab9-200">In **Load Test Editor**, right-click **Run Settings** and select **Manage Counter Sets**.</span></span>  
  
2.  <span data-ttu-id="abab9-201">按一下 **新增電腦**將新電腦新增到清單。</span><span class="sxs-lookup"><span data-stu-id="abab9-201">Click **Add Computer** to add a new computer to the list.</span></span> <span data-ttu-id="abab9-202">反白顯示的文字與圖示**新的電腦**下方會出現**要監視的電腦和計數器集合**。</span><span class="sxs-lookup"><span data-stu-id="abab9-202">An icon with the highlighted text **New Computer** will appear under **Computers and counter sets to monitor**.</span></span> <span data-ttu-id="abab9-203">輸入您想要新增至清單的電腦名稱取代醒目提示的文字。</span><span class="sxs-lookup"><span data-stu-id="abab9-203">Replace the highlighted text by typing the name of the computer you would like to add to the list.</span></span>  
  
3.  <span data-ttu-id="abab9-204">之後將電腦新增至清單中，按一下以展開 可用的計數器集合的清單，然後按一下以選取一或多個可用的計數器設定與電腦建立關聯的計數器集。</span><span class="sxs-lookup"><span data-stu-id="abab9-204">After adding the computer to the list, click to expand the list of available counter sets and then click to select one or more of the available counter sets to associate the counter set(s) with the computer.</span></span>  
  
4.  <span data-ttu-id="abab9-205">重複步驟 2 和 3，直到您有與您要收集效能資料的所有電腦相關聯計數器集合。</span><span class="sxs-lookup"><span data-stu-id="abab9-205">Repeat steps 2 and 3 until you have associated counter sets with all computers for which you would like to collect performance data.</span></span>  
  
###  <a name="BKMK_TestSettings"></a> <span data-ttu-id="abab9-206">將測試設定檔新增至解決方案來執行測試並且從遠端收集資料</span><span class="sxs-lookup"><span data-stu-id="abab9-206">Add a Test Settings File to the Solution to Run Tests and Collect Data Remotely</span></span>  
 <span data-ttu-id="abab9-207">若要設定要使用您在中建立的測試控制器和測試代理程式電腦的負載測試[步驟 2： 設定負載測試控制器和代理程式電腦](../technical-guides/step-2-configure-load-test-controller-and-agent-computers.md)，請依照下列中的步驟[新增遠端執行的測試設定或您的方案的資料收集](http://go.microsoft.com/fwlink/?LinkId=209182)(http://go.microsoft.com/fwlink/?LinkId=209182)如下所示：</span><span class="sxs-lookup"><span data-stu-id="abab9-207">To configure the Load test to use the Test Controller and Test Agent computers that you created in [Step 2: Configure Load Test Controller and Agent Computers](../technical-guides/step-2-configure-load-test-controller-and-agent-computers.md), follow the steps in [Add a test settings for remote execution or data collection to your solution](http://go.microsoft.com/fwlink/?LinkId=209182)(http://go.microsoft.com/fwlink/?LinkId=209182) as noted below:</span></span>  
  
1.  <span data-ttu-id="abab9-208">步驟 3 中，輸入名稱**BizTalkLoadTest**</span><span class="sxs-lookup"><span data-stu-id="abab9-208">For Step 3, enter the name **BizTalkLoadTest**</span></span>  
  
2.  <span data-ttu-id="abab9-209">略過步驟 6，因為您已在步驟 3 輸入的名稱。</span><span class="sxs-lookup"><span data-stu-id="abab9-209">Ignore Step 6 because you have already entered a name in Step 3.</span></span>  
  
3.  <span data-ttu-id="abab9-210">步驟 7 中，輸入 「 這些遠端測試回合的預設測試設定 」 底下**描述**。</span><span class="sxs-lookup"><span data-stu-id="abab9-210">For Step 7, enter “These are default test settings for a remote test run” under **Description**.</span></span>  
  
4.  <span data-ttu-id="abab9-211">步驟 8 中，選取 預設命名配置。</span><span class="sxs-lookup"><span data-stu-id="abab9-211">For Step 8, select the default naming scheme.</span></span>  
  
5.  <span data-ttu-id="abab9-212">針對步驟 9，底下**測試執行方法**選取**遠端執行**下方**控制器**選取測試控制器電腦，並保留其餘的屬性上**角色**頁面的預設設定。</span><span class="sxs-lookup"><span data-stu-id="abab9-212">For Step 9, under **Test execution method** select **Remote execution**, under **Controller** select the test controller computer and leave the remaining properties on the **Roles** page at their default settings.</span></span>  
  
6.  <span data-ttu-id="abab9-213">步驟 24、 選取選項**至預設主機中執行**，選取**主機類型**的**預設**，然後在**32 或 64 位元處理序中執行測試**，選取的選項**64 位元電腦上，在 64 位元處理序中執行測試**。</span><span class="sxs-lookup"><span data-stu-id="abab9-213">For Step 24, select the option **to Run in default host**, select a **Host type** of **Default**, and under **Run tests in 32 or 64 bit process**, select the option to **Run tests in 64 bit process on 64 bit machine**.</span></span>  
  
7.  <span data-ttu-id="abab9-214">針對步驟 25，選取**將個別測試標示為失敗，如果執行時間超過**並保留預設值為選取的 30 分鐘。</span><span class="sxs-lookup"><span data-stu-id="abab9-214">For Step 25, select **Mark an individual test as failed if its execution time exceeds** and leave the default value of 30 minutes selected.</span></span>  
  
8.  <span data-ttu-id="abab9-215">27b 步驟中，選取核取方塊**test 目錄中的組件使用載入內容**，然後按一下**另存新檔**。</span><span class="sxs-lookup"><span data-stu-id="abab9-215">For Step 27b, select the check box for **Use the Load Context for assemblies in the test directory**, and then click **Save As**.</span></span>  
  
9. <span data-ttu-id="abab9-216">在**另存新檔**對話方塊方塊中，確認名稱**BizTalkLoadTest**旁輸入**檔名**，然後按一下**儲存**。</span><span class="sxs-lookup"><span data-stu-id="abab9-216">In the **Save As** dialog box, verify that the name **BizTalkLoadTest** is entered next to **File name**, and click **Save**.</span></span> <span data-ttu-id="abab9-217">您現在已加入至方案的測試設定檔。</span><span class="sxs-lookup"><span data-stu-id="abab9-217">You have now added a test settings file to your solution.</span></span>