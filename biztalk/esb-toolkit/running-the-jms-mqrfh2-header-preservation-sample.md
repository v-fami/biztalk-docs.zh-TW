---
title: "執行 JMS MQRFH2 標頭保留範例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 65982dca-77e1-4267-9528-26c59237e9b1
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ab840ed1d319f8fd50d3a386e0ffc9b349f61b9e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="running-the-jms-mqrfh2-header-preservation-sample"></a><span data-ttu-id="abc5c-102">執行 JMS MQRFH2 標頭保留範例</span><span class="sxs-lookup"><span data-stu-id="abc5c-102">Running the JMS MQRFH2 Header Preservation Sample</span></span>
<span data-ttu-id="abc5c-103">此範例的這個部分會將訊息插入 WebSphere 佇列。</span><span class="sxs-lookup"><span data-stu-id="abc5c-103">This part of this sample deposits a message into a WebSphere queue.</span></span> <span data-ttu-id="abc5c-104">ESB 拾取此訊息，並將輸出的 WebSphere 佇列。</span><span class="sxs-lookup"><span data-stu-id="abc5c-104">The ESB picks up this message and deposits it into an outbound WebSphere queue.</span></span> <span data-ttu-id="abc5c-105">這示範了 ESB 和 Microsoft BizTalk 保留失真 RFH2 標頭如下的訊息是透過 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="abc5c-105">This demonstrates that the ESB and Microsoft BizTalk preserve full-fidelity RFH2 headers as a message travels through BizTalk Server.</span></span>  
  
 <span data-ttu-id="abc5c-106">**若要執行保留標頭範例**</span><span class="sxs-lookup"><span data-stu-id="abc5c-106">**To run the Header Preservation sample**</span></span>  
  
1.  <span data-ttu-id="abc5c-107">如果尚未執行 GlobalBank.ESB 應用程式，使用 BizTalk 管理主控台來啟動它。</span><span class="sxs-lookup"><span data-stu-id="abc5c-107">If the GlobalBank.ESB application is not already running, use the BizTalk Administration Console to start it.</span></span>  
  
2.  <span data-ttu-id="abc5c-108">執行 IBM RfhUtil 公用程式，然後選取 佇列管理員名稱為 ESB。JMS。第一個下拉式清單來連線到此佇列管理員 Sample.QueueManager。</span><span class="sxs-lookup"><span data-stu-id="abc5c-108">Run the IBM RfhUtil utility, and then select the queue manager named ESB.JMS.Sample.QueueManager in the first drop-down list to connect to this queue manager.</span></span>  
  
3.  <span data-ttu-id="abc5c-109">在第二個下拉式清單中，選取名為 ESB 目標輸出佇列。JMS。範例。SENDTOBIZTALK，如圖 1 所示。</span><span class="sxs-lookup"><span data-stu-id="abc5c-109">In the second drop-down list, select the target outbound queue named ESB.JMS.SAMPLE.SENDTOBIZTALK, as shown in Figure 1.</span></span>  
  
     <span data-ttu-id="abc5c-110">![佇列管理員](../esb-toolkit/media/ch6-queuemanager.gif "第 6 章第 QueueManager")</span><span class="sxs-lookup"><span data-stu-id="abc5c-110">![Queue Manager](../esb-toolkit/media/ch6-queuemanager.gif "Ch6-QueueManager")</span></span>  
  
     <span data-ttu-id="abc5c-111">**圖 1**</span><span class="sxs-lookup"><span data-stu-id="abc5c-111">**Figure 1**</span></span>  
  
     <span data-ttu-id="abc5c-112">**連接到 「 佇列管理員和 RfhUtil 將傳出佇列**</span><span class="sxs-lookup"><span data-stu-id="abc5c-112">**Connecting to the queue manager and the outbound queue in RfhUtil**</span></span>  
  
4.  <span data-ttu-id="abc5c-113">如果下拉式清單不包含任何佇列，請確定佇列管理員正在執行檢查 WebSphere MQ 服務項目，如圖 2 所示。</span><span class="sxs-lookup"><span data-stu-id="abc5c-113">If the drop-down list does not contain any queues, make sure that the queue manager is running by checking the WebSphere MQ Services item, as shown in Figure 2.</span></span>  
  
     <span data-ttu-id="abc5c-114">![Web 球體](../esb-toolkit/media/ch6-websphere.gif "第 6 章第 WebSphere")</span><span class="sxs-lookup"><span data-stu-id="abc5c-114">![Web Sphere](../esb-toolkit/media/ch6-websphere.gif "Ch6-WebSphere")</span></span>  
  
     <span data-ttu-id="abc5c-115">**圖 2**</span><span class="sxs-lookup"><span data-stu-id="abc5c-115">**Figure 2**</span></span>  
  
     <span data-ttu-id="abc5c-116">**檢查佇列管理員正在執行中的 WebSphere 服務項目**</span><span class="sxs-lookup"><span data-stu-id="abc5c-116">**Checking that the queue manager is running in the WebSphere Services item**</span></span>  
  
5.  <span data-ttu-id="abc5c-117">按一下**ReadFile** RfhUtil 公用程式中的按鈕，巡覽至名為測試 000128 測試訊息檔案。JMS 位於子資料夾名為 \Source\Samples\JMS\Test\Data\Load\\。</span><span class="sxs-lookup"><span data-stu-id="abc5c-117">Click the **ReadFile** button in the RfhUtil utility and navigate to the test message file named TEST-000128.JMS located in the subfolder named \Source\Samples\JMS\Test\Data\Load\\.</span></span> <span data-ttu-id="abc5c-118">此檔案包含 128 測試訊息批次，但是此公用程式載入只有第一個。</span><span class="sxs-lookup"><span data-stu-id="abc5c-118">This file contains a batch of 128 test messages, but the utility loads only the first one.</span></span>  
  
6.  <span data-ttu-id="abc5c-119">按一下**RFH**索引標籤，然後確定只有**JMS**選取核取方塊。</span><span class="sxs-lookup"><span data-stu-id="abc5c-119">Click the **RFH** tab, and then make sure that only the **JMS** check box is selected.</span></span>  
  
7.  <span data-ttu-id="abc5c-120">按一下**jms**索引標籤，並請確定所選**回覆**佇列是 ESB。JMS。範例。DYNAMICQ1，所選**目的地佇列**是 ESB。JMS。範例。DYNAMICQ2。</span><span class="sxs-lookup"><span data-stu-id="abc5c-120">Click the **jms** tab, and then make sure that the selected **Reply To** queue is ESB.JMS.SAMPLE.DYNAMICQ1 and that the selected **Destination Queue** is ESB.JMS.SAMPLE.DYNAMICQ2.</span></span>  
  
8.  <span data-ttu-id="abc5c-121">按一下**Main**索引標籤，然後再按一下**寫入 Q**  按鈕，將訊息寫入佇列。</span><span class="sxs-lookup"><span data-stu-id="abc5c-121">Click the **Main** tab, and then click the **Write Q** button to write the message into the queue.</span></span>  
  
9. <span data-ttu-id="abc5c-122">在延遲之後應用程式執行，而 ESB 輸出訊息會出現在 ESB。JMS。範例。DYNAMICQ1 和 ESB。JMS。範例。DYNAMICQ1 佇列。</span><span class="sxs-lookup"><span data-stu-id="abc5c-122">After a delay while the application executes, the ESB output message appears in the ESB.JMS.SAMPLE.DYNAMICQ1 and ESB.JMS.SAMPLE.DYNAMICQ1 queues.</span></span> <span data-ttu-id="abc5c-123">開啟 WebSphere 佇列總管並瀏覽佇列，確認這個項目。</span><span class="sxs-lookup"><span data-stu-id="abc5c-123">Open the WebSphere Queue Explorer and browse the queues to confirm this.</span></span>  
  
10. <span data-ttu-id="abc5c-124">返回 RfhUtil 公用程式，並連接到看到的訊息佇列。</span><span class="sxs-lookup"><span data-stu-id="abc5c-124">Go back to the RfhUtil utility and connect to the queues to see the messages.</span></span> <span data-ttu-id="abc5c-125">按一下**MQMD、 RFH，**和**jms**驗證輸入和輸出值會變更該目的地佇列中的訊息，而且回覆佇列中的訊息是相同的索引標籤除外，而不是標準的 JMS 訊息，訊息會標示為 「 其他 」。</span><span class="sxs-lookup"><span data-stu-id="abc5c-125">Click the **MQMD, RFH,** and **jms** tabs to verify that the input and output values are unchanged for the message in the Destination Queue, and that the message in the Reply To queue is the same except that, instead of being a standard JMS message, the message is marked as "other".</span></span>