---
title: 執行大量載入以內容為基礎的路由範例 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7e981567-7c6c-4c13-bd5b-597efdd3fb50
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 36c5348563cc52c31b14dbceddf35bdb3d5d94cb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22294942"
---
# <a name="running-the-bulk-load-content-based-routing-sample"></a><span data-ttu-id="b18bf-102">執行大量載入內容架構路由範例</span><span class="sxs-lookup"><span data-stu-id="b18bf-102">Running the Bulk Load Content-Based Routing Sample</span></span>
<span data-ttu-id="b18bf-103">此範例的一部分示範大量載入的佇列訊息的 ESB 和 Microsoft BizTalk 會路由傳送至不同的目的地佇列，根據每個訊息中指定的佇列名稱。</span><span class="sxs-lookup"><span data-stu-id="b18bf-103">This part of the sample demonstrates bulk loading a queue with messages that the ESB and Microsoft BizTalk will route to different destination queues based on the queue name specified in each message.</span></span> <span data-ttu-id="b18bf-104">它先前的兩個部分中使用的功能，您所見的範例。</span><span class="sxs-lookup"><span data-stu-id="b18bf-104">It uses the features of the sample that you have seen in the previous two parts.</span></span>  
  
 <span data-ttu-id="b18bf-105">**若要執行大量載入內容為基礎的路由存取範例**</span><span class="sxs-lookup"><span data-stu-id="b18bf-105">**To run the Bulk Load Content-based Routing Access sample**</span></span>  
  
1.  <span data-ttu-id="b18bf-106">如果尚未執行 GlobalBank.ESB 應用程式，使用 BizTalk 管理主控台來啟動它。</span><span class="sxs-lookup"><span data-stu-id="b18bf-106">If the GlobalBank.ESB application is not already running, use the BizTalk Administration Console to start it.</span></span>  
  
2.  <span data-ttu-id="b18bf-107">執行 IBM RfhUtil 公用程式，然後選取 [佇列管理員名稱為 ESB。JMS。Sample.QueueManager 連接到此佇列管理員] 中，如這個範例的第 2 部分所示的第一個下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="b18bf-107">Run the IBM RfhUtil utility, and then select the queue manager named ESB.JMS.Sample.QueueManager in the first drop-down list to connect to this queue manager, as in Part 2 of this sample.</span></span>  
  
3.  <span data-ttu-id="b18bf-108">在第二個下拉式清單中，選取名為 ESB 目標輸出佇列。JMS。範例。SENDTOBIZTALK，如這個範例的第 2 部分所示。</span><span class="sxs-lookup"><span data-stu-id="b18bf-108">In the second drop-down list, select the target outbound queue named ESB.JMS.SAMPLE.SENDTOBIZTALK, as in Part 2 of this sample.</span></span>  
  
4.  <span data-ttu-id="b18bf-109">按一下**負載 Q**按鈕 RfhUtil 公用程式中，然後巡覽至名為測試 000128 測試訊息檔案。JMS 位於子資料夾名為 \Source\Samples\JMS\Test\Data\Load\\。</span><span class="sxs-lookup"><span data-stu-id="b18bf-109">Click the **Load Q** button in the RfhUtil utility, and then navigate to the test message file named TEST-000128.JMS located in the subfolder named \Source\Samples\JMS\Test\Data\Load\\.</span></span> <span data-ttu-id="b18bf-110">此檔案包含範例會將傳送至 ESB 128 測試訊息批的次。</span><span class="sxs-lookup"><span data-stu-id="b18bf-110">This file contains a batch of 128 test messages that the sample will send to the ESB.</span></span>  
  
5.  <span data-ttu-id="b18bf-111">在**負載**對話方塊中，保留所有的值設為其預設值。</span><span class="sxs-lookup"><span data-stu-id="b18bf-111">In the **Load** dialog box, leave all values set to their default values.</span></span>  
  
6.  <span data-ttu-id="b18bf-112">在**負載**對話方塊中，按一下 **確定**加入輸入佇列中的所有訊息。</span><span class="sxs-lookup"><span data-stu-id="b18bf-112">In the **Load** dialog box, click **OK** to add all the messages to the input queue.</span></span>  
  
7.  <span data-ttu-id="b18bf-113">在延遲之後應用程式執行，而 ESB 輸出訊息會出現在不同的目的地佇列，取決於其 JMS 標頭中的值。</span><span class="sxs-lookup"><span data-stu-id="b18bf-113">After a delay while the application executes, the ESB output messages appear in various destination queues, depending on the values in their JMS headers.</span></span> <span data-ttu-id="b18bf-114">不過，所有指定相同的收件者地佇列，因此所有回覆會都出現在 ESB。JMS。範例。回應佇列。</span><span class="sxs-lookup"><span data-stu-id="b18bf-114">However, all specify the same Reply To queue, so all the replies appear in the ESB.JMS.SAMPLE.REPLY queue.</span></span> <span data-ttu-id="b18bf-115">開啟 WebSphere 佇列總管並瀏覽佇列，確認這個項目。</span><span class="sxs-lookup"><span data-stu-id="b18bf-115">Open the WebSphere Queue Explorer and browse the queues to confirm this.</span></span>