---
title: 步驟 4B： 啟動傳送埠和接收埠以進行互動的存放區和情況 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c7b0ecd4-ea08-4567-80bd-14f465ba4867
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f5d92b70a1c98a2ff21443980be57d969281fbd3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22224422"
---
# <a name="step-4b-start-the-send-ports-and-receive-ports-for-the-interact-store-and-forward-scenario"></a>步驟 4B： 啟動傳送埠和接收埠以進行互動的存放區和轉寄的案例
在開始此步驟之前，必須先完成[步驟 4A： 啟動 SWIFTNet 服務為互動存放與轉寄實例](../../adapters-and-accelerators/fileact-interact/step-4a-start-the-swiftnet-service-for-the-interact-store-and-forward-scenario.md)。  
  
### <a name="to-start-the-send-ports-and-receive-ports"></a>啟動傳送埠和接收埠  
  
1.  啟動**BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，展開 [BizTalk 群組]，然後展開您用來建立傳送埠的 BizTalk 應用程式。  
  
3.  針對下列每個傳送埠，傳送埠，以滑鼠右鍵按一下，然後按一下**啟動**:  
  
    -   **Tutorial_IA_SendResponseToReceiver**  
  
    -   **Tutorial_IA_SendResponseToSender**  
  
    -   **Tutorial_IA_SendRequest_SnF**  
  
4.  在主控台樹狀目錄中，展開 [BizTalk 群組]，然後展開您在其中建立接收位置的 BizTalk 應用程式。  
  
5.  針對每個下列的接收位置，以滑鼠右鍵按一下接收位置，然後**啟用**:  
  
    -   **Tutorial_IA_InputRequest_SnF**  
  
    -   **Tutorial_IA_HandleRequestOneWay_SnF**  
  
## <a name="see-also"></a>另請參閱  
 [步驟 4： 測試互動存放區和轉寄的端對端案例](../../adapters-and-accelerators/fileact-interact/step-4-test-the-interact-store-and-forward-end-to-end-scenario.md)   
 [步驟 4A： 啟動 SWIFTNet 服務互動的存放區和轉寄的案例](../../adapters-and-accelerators/fileact-interact/step-4a-start-the-swiftnet-service-for-the-interact-store-and-forward-scenario.md)   
 [步驟 4c： 建立測試執行個體互動的存放區和轉寄的案例](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-the-interact-store-and-forward-scenario.md)   
 [步驟 4d： 測試有效的執行個體互動的存放區和轉寄的案例](../../adapters-and-accelerators/fileact-interact/step-4d-test-a-valid-instance-for-the-interact-store-and-forward-scenario.md)