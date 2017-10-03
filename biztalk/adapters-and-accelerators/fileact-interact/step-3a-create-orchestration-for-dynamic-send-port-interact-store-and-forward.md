---
title: "步驟 3A： 建立協調流程互動的存放區和轉送 （提取） 案例的動態傳送埠 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6d5bbfed-f2cb-4caa-91e2-58f0bdb3b3c5
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 486133586a3db8669a58aae59c3ec67a4f561999
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-3a-create-an-orchestration-for-dynamic-send-port-for-interact-store-and-forward-pull-scenario"></a>步驟 3A： 建立協調流程互動的存放區和轉送 （提取） 案例的動態傳送埠
開始本節中的步驟之前，您必須完成的步驟[步驟 2c： 加入互動的傳送埠的互動存放區和轉送 （提取） 案例](../../adapters-and-accelerators/fileact-interact/step-2c-add-interact-send-port-for-interact-store-and-forward-pull-scenario.md)> 一節。  
  
### <a name="to-create-an-orchestration"></a>若要建立協調流程  
  
1.  建立訂閱的所有訊息的訊息類型 Sw ExchangeSnFRequest 「 接收 」 圖形。  
  
2.  新增 「 運算式 」 圖形，從 ExchangeRequestSnF 訊息中取得所有必要的值。 請參閱下面的 「 運算式 」 圖形的範例：  
  
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
  
3.  建構動態傳送的訊息類型 PullSnFRequest 和 URL。 請參閱 「 建構訊息指派圖形的範例：  
  
    ```  
    PullMessage = new System.Xml.XmlDocument();  
    PullMessage.LoadXml(@"<Sw-PullSnFRequest/>");  
    PullRequest = PullMessage;  
  
    DynamicPull(Microsoft.XLANGs.BaseTypes.Address) = "INTERACT://<machine  
     name>/" + QueueName + "/" + SessionMode + "/" + ForceAcquire + "/" +   
    OrderBy + "/" + RecoveryMode + "/" + MessageFormat;  
    ```  
  
4.  在此範例中，PullMessage 是 Sw PullSnFRequest 類型的訊息。  
  
5.  新增傳送圖形傳送 PullMessage （提取要求）。  
  
6.  新增要求-回應連接埠傳送提取訊息，以及接收 pull 回應與動態繫結。  
  
7.  連接 「 傳送 」 圖形與上一個步驟中建立的連接埠。  
  
8.  新增接收 PullResponse （PullSnFResponse 類型的訊息），然後連線與先前建立的連接埠的 「 接收 」 圖形的 「 接收 」 圖形。  
  
9. 傳送回應至使用 「 傳送 」 圖形的個別資料夾。  
  
10. 加入所有的這些活動 （傳送提取要求和接收回應） 在迴圈中如果您想要提取的所有訊息。  
  
11. 新增 「 運算式 」 圖形 CheckQueueEmpty 以保存提取直到時間佇列是空的。 下列運算式 」 圖形的範例，請參閱：  
  
    ```  
    PullResponseDoc=PullResponse;  
    PullResponseNode=PullResponseDoc.SelectSingleNode("/SwPullSnFResponse/  
    SwGbl-Status/SwGbl-StatusAttributes/SwGbl-Code");  
    if(PullResponseNode !=null && PullResponseNode.InnerText=="Sw.SnF.QueueEmpty")  
    {  
        IsPull=false;  
    }  
    ```  
  
12. 這會將 IsPull = false，一旦佇列是空的。  
  
## <a name="see-also"></a>另請參閱  
 [步驟 3B： 互動存放區和轉送 （提取） 案例的動態傳送埠與協調流程繫結](../../adapters-and-accelerators/fileact-interact/step-3b-bind-orchestration-with-dynamic-send-port-for-interact-scenario.md)