---
title: "步驟 4B： 啟動傳送埠和接收埠為 FileAct 存放與轉寄 （提取） 實例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ea2215c5-fb43-4c7e-a42d-5d131a6dee38
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ad4c6b9d17ab1ea55c1f8378f1cb481a07b09e34
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-4b-start-the-send-ports-and-receive-ports-for-the-fileact-store-and-forward-pull-scenario"></a>步驟 4B： 啟動傳送埠和接收埠為 FileAct 存放與轉寄 （提取） 實例
在開始此步驟之前，必須先完成[步驟 4A： 啟動 FileAct 存放與轉寄 （提取） 案例 SWIFTNet 服務](../../adapters-and-accelerators/fileact-interact/step-4a-start-swiftnet-service-for-fileact-store-and-forward-pull-scenario.md)。  
  
### <a name="to-start-the-send-ports-and-receive-ports"></a>啟動傳送埠和接收埠  
  
1.  啟動**BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，展開 [BizTalk 群組]，然後展開您用來建立傳送埠的 BizTalk 應用程式。  
  
3.  針對下列每個傳送埠，傳送埠，以滑鼠右鍵按一下，然後按一下**啟動**:  
  
    -   **Tutorial_ FA_SendPullResponseToReceiver**  
  
    -   **Tutorial_ FA_SendRequest_SnF**  
  
    -   **Tutorial_ FA_DynamicSendPort**  
  
4.  在主控台樹狀目錄中，展開 [BizTalk 群組]，然後展開您在其中建立接收位置的 BizTalk 應用程式。  
  
5.  針對每個下列的接收位置，以滑鼠右鍵按一下接收位置，然後**啟用**:  
  
    -   **Tutorial_ FA_InputRequest_SnF**  
  
    -   **Tutorial_ FA_InputRequest_PullMode**  
  
## <a name="see-also"></a>另請參閱  
 [步驟 4A： 啟動 SWIFTNet 服務為 FileAct 存放與轉寄 （提取） 實例](../../adapters-and-accelerators/fileact-interact/step-4a-start-swiftnet-service-for-fileact-store-and-forward-pull-scenario.md)   
 [步驟 4c： 建立 FileAct 存放與轉寄 （提取） 案例的測試執行個體](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-fileact-store-and-forward-pull-scenario.md)   
 [步驟 4d： 測試 FileAct 存放與轉寄 （提取） 案例的有效執行個體](../../adapters-and-accelerators/fileact-interact/step-4d-test-a-valid-instance-for-fileact-store-and-forward-pull-scenario.md)