---
title: 步驟 3A： 建立協調流程互動的存放區和轉送 （提取） 案例的動態傳送埠 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d5bbfed-f2cb-4caa-91e2-58f0bdb3b3c5
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 486133586a3db8669a58aae59c3ec67a4f561999
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22225278"
---
# <a name="step-3a-create-an-orchestration-for-dynamic-send-port-for-interact-store-and-forward-pull-scenario"></a><span data-ttu-id="c2e91-102">步驟 3A： 建立協調流程互動的存放區和轉送 （提取） 案例的動態傳送埠</span><span class="sxs-lookup"><span data-stu-id="c2e91-102">Step 3A: Create an orchestration for dynamic send port for InterAct Store and Forward (Pull) Scenario</span></span>
<span data-ttu-id="c2e91-103">開始本節中的步驟之前，您必須完成的步驟[步驟 2c： 加入互動的傳送埠的互動存放區和轉送 （提取） 案例](../../adapters-and-accelerators/fileact-interact/step-2c-add-interact-send-port-for-interact-store-and-forward-pull-scenario.md)> 一節。</span><span class="sxs-lookup"><span data-stu-id="c2e91-103">Before you begin the steps in this section, you must complete the steps in the [Step 2C: Add an INTERACT Send Port for the InterAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-2c-add-interact-send-port-for-interact-store-and-forward-pull-scenario.md) section.</span></span>  
  
### <a name="to-create-an-orchestration"></a><span data-ttu-id="c2e91-104">若要建立協調流程</span><span class="sxs-lookup"><span data-stu-id="c2e91-104">To Create an Orchestration</span></span>  
  
1.  <span data-ttu-id="c2e91-105">建立訂閱的所有訊息的訊息類型 Sw ExchangeSnFRequest 「 接收 」 圖形。</span><span class="sxs-lookup"><span data-stu-id="c2e91-105">Create the Receive shape that subscribes to all of the messages of message type Sw-ExchangeSnFRequest.</span></span>  
  
2.  <span data-ttu-id="c2e91-106">新增 「 運算式 」 圖形，從 ExchangeRequestSnF 訊息中取得所有必要的值。</span><span class="sxs-lookup"><span data-stu-id="c2e91-106">Add an Expression shape to get all of the required values from the ExchangeRequestSnF message.</span></span> <span data-ttu-id="c2e91-107">請參閱下面的 「 運算式 」 圖形的範例：</span><span class="sxs-lookup"><span data-stu-id="c2e91-107">Refer to the following Expression Shape sample:</span></span>  
  
    ```  
    ExchangeSnFRequestDoc=ExchangeSnFRequest;  
    AcquireQueuePath="/Sw-ExchangeSnFRequest/Sw-SnFRequest/Sw-SnFOpRequest/Sw-AcquireSnFRequest/";  
  
    QueueNameNode=ExchangeSnFRequestDoc.SelectSingleNode(AcquireQueuePath + "SwInt-Queue");  
    SessionModeNode=ExchangeSnFRequestDoc.SelectSingleNode(AcquireQueuePath+ "Sw-SessionMode");  
    ForceAcquireNode=ExchangeSnFRequestDoc.SelectSingleNode(AcquireQueuePath+ "Sw-ForceAcquire");  
    OrderByNode=ExchangeSnFRequestDoc.SelectSingleNode(AcquireQueuePath+ "Sw-OrderBy");  
    RecoveryModeNode=ExchangeSnFRequestDoc.SelectSingleNode(AcquireQueuePath+ "Sw-RecoveryMode");  
  
    QueueName=QueueNameNode.InnerText;  
    SessionMode=SessionModeNode.InnerText;  
    ForceAcquire=ForceAcquireNode.InnerText;  
    OrderBy=OrderByNode.InnerText;  
    RecoveryMode=RecoveryModeNode.InnerText;  
  
    MessageFormat="InteractMessage";  
    IsPull=true;  
    ```  
  
3.  <span data-ttu-id="c2e91-108">建構動態傳送的訊息類型 PullSnFRequest 和 URL。</span><span class="sxs-lookup"><span data-stu-id="c2e91-108">Construct a message of type PullSnFRequest and the URL for Dynamic Send.</span></span> <span data-ttu-id="c2e91-109">請參閱 「 建構訊息指派圖形的範例：</span><span class="sxs-lookup"><span data-stu-id="c2e91-109">Refer to the Assignment Shape of Construct Message sample:</span></span>  
  
    ```  
    PullMessage = new System.Xml.XmlDocument();  
    PullMessage.LoadXml(@"<Sw-PullSnFRequest/>");  
    PullRequest = PullMessage;  
  
    DynamicPull(Microsoft.XLANGs.BaseTypes.Address) = "INTERACT://<machine  
     name>/" + QueueName + "/" + SessionMode + "/" + ForceAcquire + "/" +   
    OrderBy + "/" + RecoveryMode + "/" + MessageFormat;  
    ```  
  
4.  <span data-ttu-id="c2e91-110">在此範例中，PullMessage 是 Sw PullSnFRequest 類型的訊息。</span><span class="sxs-lookup"><span data-stu-id="c2e91-110">In this sample, PullMessage is a message of type Sw-PullSnFRequest.</span></span>  
  
5.  <span data-ttu-id="c2e91-111">新增傳送圖形傳送 PullMessage （提取要求）。</span><span class="sxs-lookup"><span data-stu-id="c2e91-111">Add a Send shape to send the PullMessage (pull request).</span></span>  
  
6.  <span data-ttu-id="c2e91-112">新增要求-回應連接埠傳送提取訊息，以及接收 pull 回應與動態繫結。</span><span class="sxs-lookup"><span data-stu-id="c2e91-112">Add a request-response port for sending the pull message and for receiving the pull response with the dynamic binding.</span></span>  
  
7.  <span data-ttu-id="c2e91-113">連接 「 傳送 」 圖形與上一個步驟中建立的連接埠。</span><span class="sxs-lookup"><span data-stu-id="c2e91-113">Connect the Send shape with the port created in the previous step.</span></span>  
  
8.  <span data-ttu-id="c2e91-114">新增接收 PullResponse （PullSnFResponse 類型的訊息），然後連線與先前建立的連接埠的 「 接收 」 圖形的 「 接收 」 圖形。</span><span class="sxs-lookup"><span data-stu-id="c2e91-114">Add a Receive shape to receive the PullResponse (message of type PullSnFResponse) and then connect the Receive shape with the port previously created.</span></span>  
  
9. <span data-ttu-id="c2e91-115">傳送回應至使用 「 傳送 」 圖形的個別資料夾。</span><span class="sxs-lookup"><span data-stu-id="c2e91-115">Send the response to the respective folder using a Send shape.</span></span>  
  
10. <span data-ttu-id="c2e91-116">加入所有的這些活動 （傳送提取要求和接收回應） 在迴圈中如果您想要提取的所有訊息。</span><span class="sxs-lookup"><span data-stu-id="c2e91-116">Add all of these activities (sending a pull request and receiving the response) in a loop if you want to pull all of the messages.</span></span>  
  
11. <span data-ttu-id="c2e91-117">新增 「 運算式 」 圖形 CheckQueueEmpty 以保存提取直到時間佇列是空的。</span><span class="sxs-lookup"><span data-stu-id="c2e91-117">Add an Expression shape CheckQueueEmpty to keep pulling until the time queue is empty.</span></span> <span data-ttu-id="c2e91-118">下列運算式 」 圖形的範例，請參閱：</span><span class="sxs-lookup"><span data-stu-id="c2e91-118">Refer the following Expression Shape sample:</span></span>  
  
    ```  
    PullResponseDoc=PullResponse;  
    PullResponseNode=PullResponseDoc.SelectSingleNode("/SwPullSnFResponse/  
    SwGbl-Status/SwGbl-StatusAttributes/SwGbl-Code");  
    if(PullResponseNode !=null && PullResponseNode.InnerText=="Sw.SnF.QueueEmpty")  
    {  
        IsPull=false;  
    }  
    ```  
  
12. <span data-ttu-id="c2e91-119">這會將 IsPull = false，一旦佇列是空的。</span><span class="sxs-lookup"><span data-stu-id="c2e91-119">This will set the IsPull = false, once the queue is empty.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2e91-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c2e91-120">See Also</span></span>  
 [<span data-ttu-id="c2e91-121">步驟 3B： 互動存放區和轉送 （提取） 案例的動態傳送埠與協調流程繫結</span><span class="sxs-lookup"><span data-stu-id="c2e91-121">Step 3B: Bind the orchestration with dynamic send port for InterAct Store and Forward (Pull) Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-3b-bind-orchestration-with-dynamic-send-port-for-interact-scenario.md)