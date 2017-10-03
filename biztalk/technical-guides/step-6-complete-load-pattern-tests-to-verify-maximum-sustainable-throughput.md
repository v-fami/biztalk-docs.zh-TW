---
title: "步驟 6： 執行常數負載模式測試，以確認最大持續輸送量 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dd790354-be9f-4278-bd15-493eac8970c9
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b6bfc0b9670366ab2f38046fcdc5497234b51ba5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-6-perform-constant-load-pattern-tests-to-verify-maximum-sustainable-throughput"></a><span data-ttu-id="5314e-102">步驟 6： 執行常數負載模式測試，以確認最大持續輸送量</span><span class="sxs-lookup"><span data-stu-id="5314e-102">Step 6: Perform Constant Load Pattern Tests to Verify Maximum Sustainable Throughput</span></span>
<span data-ttu-id="5314e-103">負載測試使用 Visual Studio 2010 的 BizTalk Server 方案時，應該執行的常數負載模式測試，一旦中所述，決定大約最大持續輸送量 (MST) 解決方案的[步驟 5： 執行步驟載入模式測試，以判斷最大持續輸送量](../technical-guides/step-5-complete-step-load-tests-to-determine-maximum-sustainable-throughput.md)。</span><span class="sxs-lookup"><span data-stu-id="5314e-103">When load testing a BizTalk Server solution using Visual Studio 2010, a constant load pattern test should be performed once the approximate Maximum Sustainable Throughput (MST) of the solution is determined as described in [Step 5: Perform Step Load Pattern Tests to Determine Maximum Sustainable Throughput](../technical-guides/step-5-complete-step-load-tests-to-determine-maximum-sustainable-throughput.md).</span></span> <span data-ttu-id="5314e-104">這應該確認 MST 事實上持續一段時間，以建立基準負載測試向前移到評估的任何效能調整套用至 BizTalk Server 應用程式或環境。</span><span class="sxs-lookup"><span data-stu-id="5314e-104">This should be done to confirm that the MST is in fact sustainable over time and also so as to create a baseline load test moving forward to evaluate the effects of any performance tuning applied to the BizTalk Server application or environment.</span></span>  
  
## <a name="create-and-run-a-constant-load-pattern-test"></a><span data-ttu-id="5314e-105">建立和執行常數負載模式測試</span><span class="sxs-lookup"><span data-stu-id="5314e-105">Create and run a Constant Load Pattern Test</span></span>  
 <span data-ttu-id="5314e-106">最簡單的方式來建立使用相同的測試混合、 計數器集合和使用步驟負載模式測試的計數器集合對應的常數負載模式測試僅儲存步驟負載模式測試 」 BTS_Messaging_Step.loadtest"為"BTS_Messaging_Constant.loadtest"，然後讓某些變更為"BTS_Messaging_Constant.loadtest"。</span><span class="sxs-lookup"><span data-stu-id="5314e-106">The easiest way to create a Constant Load Pattern test that uses the same Test Mix, Counter Sets, and Counter Set Mappings used by the Step Load Pattern test is to simply save the Step Load Pattern test “BTS_Messaging_Step.loadtest” as “BTS_Messaging_Constant.loadtest” and then make some changes to “BTS_Messaging_Constant.loadtest”.</span></span> <span data-ttu-id="5314e-107">遵循下列步驟來建立以常數負載模式也就是測試根據現有的步驟負載模式測試：</span><span class="sxs-lookup"><span data-stu-id="5314e-107">Follow these steps to create a Constant Load Pattern test that is based upon the existing Step Load Pattern test:</span></span>  
  
1.  <span data-ttu-id="5314e-108">如果不是已開啟，請開啟 BTS_Messaging_Step.loadtest。</span><span class="sxs-lookup"><span data-stu-id="5314e-108">Open BTS_Messaging_Step.loadtest if it is not already open.</span></span>  
  
2.  <span data-ttu-id="5314e-109">按一下**檔案**選取**存 LoadTests\BTS_Messaging_Step.loadtest**。</span><span class="sxs-lookup"><span data-stu-id="5314e-109">Click **File** and select **Save LoadTests\BTS_Messaging_Step.loadtest As**.</span></span>  
  
3.  <span data-ttu-id="5314e-110">在**另存新檔**對話方塊中，旁邊**檔案名稱**，輸入 C:\Projects\LoadTest\BTSLoad\LoadTests\BTS_Messaging_Constant.loadtest，然後按一下**儲存**。</span><span class="sxs-lookup"><span data-stu-id="5314e-110">In the **Save File As** dialog box, next to **File name**, enter C:\Projects\LoadTest\BTSLoad\LoadTests\BTS_Messaging_Constant.loadtest and then click **Save**.</span></span>  
  
4.  <span data-ttu-id="5314e-111">在負載測試編輯器，重新命名情節**BTS_Messaging_Step**至**BTS_Messaging_Constant**。</span><span class="sxs-lookup"><span data-stu-id="5314e-111">In the Load Test Editor, rename the scenario **BTS_Messaging_Step** to **BTS_Messaging_Constant**.</span></span> <span data-ttu-id="5314e-112">情節名稱會顯示正下方**案例**資料夾。</span><span class="sxs-lookup"><span data-stu-id="5314e-112">The scenario name is displayed directly under the **Scenarios** folder.</span></span>  
  
5.  <span data-ttu-id="5314e-113">保留的值**測試混合**和**網路混合**保持不變，但是按一下以選取**步驟負載模式**。</span><span class="sxs-lookup"><span data-stu-id="5314e-113">Leave the values for **Test Mix** and **Network Mix** unchanged but click to select **Step Load Pattern**.</span></span>  
  
6.  <span data-ttu-id="5314e-114">以滑鼠右鍵按一下**步驟負載模式**選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="5314e-114">Right-click **Step Load Pattern** and select **Properties**.</span></span>  
  
7.  <span data-ttu-id="5314e-115">在**屬性**下**負載模式**旁按一下下拉式清單**模式**和變更的模式**步驟**至**常數**。</span><span class="sxs-lookup"><span data-stu-id="5314e-115">In the **Properties** section, under **Load Pattern** click the dropdown list next to **Pattern** and change the Pattern from **Step** to **Constant**.</span></span>  
  
8.  <span data-ttu-id="5314e-116">在**屬性**下**參數**，變更的值**常數使用者計數**稍微小於的使用者數目的值至步驟負載模式測試已成為現象 (也就是值**BizTalk:Messaging\Documents 每秒接收到**持續超過的值開始**BizTalk:Messaging\Documents processed/Sec**和值**biztalk: Message Box: General Counters\Spool Size**開始增加 unbounded)。</span><span class="sxs-lookup"><span data-stu-id="5314e-116">In the **Properties** section, under **Parameters**, change the value for **Constant User Count** to a value slightly less than the number of users at which the Step Load Pattern test was becoming unsustainable (i.e. the value for the **BizTalk:Messaging\Documents received per/Sec** began to consistently exceed the value for **BizTalk:Messaging\Documents processed/Sec** and the value of the **BizTalk:Message Box:General Counters\Spool Size** began to increase unbounded).</span></span>  
  
9. <span data-ttu-id="5314e-117">在下**回合設定**資料夾中，以滑鼠右鍵按一下**執行 Setting1 [Active]**選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="5314e-117">Under the **Run Settings** folder, right-click **Run Setting1 [Active]** and select **Properties**.</span></span>  
  
10. <span data-ttu-id="5314e-118">向下的捲動清單屬性，以**計時**區段，並輸入的值**執行持續期間**至少 10 分鐘 (00: 10:00)，並驗證的值**取樣率**已設定為 5 秒 (00: 00:05)。</span><span class="sxs-lookup"><span data-stu-id="5314e-118">Scroll down the list of properties to the **Timing** section and enter a value for **Run Duration** of at least 10 minutes (00:10:00) and verify that the value for **Sample Rate** is still set to 5 seconds (00:00:05).</span></span>  
  
11. <span data-ttu-id="5314e-119">啟動負載測試的測試名稱 (例如 BTS_Messaging_Constant) 上按一下滑鼠右鍵，然後按一下**執行測試**功能表選項。</span><span class="sxs-lookup"><span data-stu-id="5314e-119">Start the load test by right-clicking the test name (e.g. BTS_Messaging_Constant) and then click the **Run Test** menu option.</span></span>