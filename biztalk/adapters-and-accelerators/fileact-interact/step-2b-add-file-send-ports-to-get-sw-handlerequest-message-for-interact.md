---
title: '步驟 2B： 新增 FILE 傳送埠以擷取 sw: handlerequest 訊息針對 InterAct 儲存和轉寄 （提取） 案例 |Microsoft Docs'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aa22d6e7-f1bd-43ad-9a0e-0b287057d20f
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 56cee834f5974d993dfeaa8fbfee8313eeb74064
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37004439"
---
# <a name="step-2b-add-file-send-ports-to-capture-the-swhandlerequest-message-for-the-interact-store-and-forward-pull-scenario"></a>步驟 2B： 新增 FILE 傳送埠以擷取 InterAct 儲存和轉寄 （提取） 案例的 sw: handlerequest 訊息
在開始此步驟之前，必須先完成[步驟 2A： 新增檔案接收位置針對 InterAct 儲存和轉寄 （提取） 案例](../../adapters-and-accelerators/fileact-interact/step-2a-add-file-receive-locations-for-interact-store-and-forward-scenario.md)。  

### <a name="to-add-a-file-send-port-to-capture-the-swhandlerequest-message"></a>若要新增 FILE 傳送埠以擷取 sw: handlerequest 訊息  

1. 開始**BizTalk Server 管理**。  

2. 在主控台樹狀目錄中，展開 BizTalk 群組，然後展開您要建立傳送埠的 BizTalk 應用程式。  

3. 以滑鼠右鍵按一下**傳送埠**，指向**新增**，然後按一下 **靜態單向傳送埠。**  

4. 在 **傳送埠屬性**視窗中，傳送埠，命名**Tutorial_IA_SendPullResponsetoReceiver**。  

5. 在 [**傳送埠屬性**] 視窗中，從**傳輸類型**下拉式清單中，選取**檔案**，然後按一下**設定**。  

6. 在  **FILE 傳輸屬性**對話方塊的 **目的地資料夾**方塊中，輸入**C:\SWIFTAdapterTutorial\Interact\PullResponse**，然後按一下  **確定**。  

7. 在 [**傳送埠屬性**] 視窗中，執行下列動作：  


   |   **使用此選項**    |                        **若要這樣做**                         |
   |-------------------|---------------------------------------------------------------|
   | **傳送處理常式**  | 從下拉式清單中，選取**BizTalkServerApplication**。 |
   | **傳送管線** |       從下拉式清單中，選取**XMLTransmit**。        |


8. 按一下 [確定] 。  

9. 重複步驟 1 和 2。  

10. 以滑鼠右鍵按一下**傳送埠**，指向**新增**，然後按一下**動態請求-回應傳送埠**。  

11. 在 **傳送埠屬性**視窗中，傳送埠命名<strong>，Tutorial_IA_DynamicSendPort</strong>。  

12. 在 [**傳送埠屬性**] 視窗中，執行下列動作：  


    |     **使用此選項**     |                  **若要這樣做**                  |
    |----------------------|--------------------------------------------------|
    |  **傳送管線**   | 從下拉式清單中，選取**XMLTransmit**。 |
    | **接收管線** | 從下拉式清單中，選取**XMLReceive**。  |


13. 按一下 [確定] 。  

## <a name="see-also"></a>另請參閱  
 [步驟 2A： 針對 InterAct 儲存和轉寄 （提取） 案例新增檔案接收位置](../../adapters-and-accelerators/fileact-interact/step-2a-add-file-receive-locations-for-interact-store-and-forward-scenario.md)   
 [步驟 2C：針對 InterAct 儲存和轉寄 (提取) 案例新增 INTERACT 傳送埠](../../adapters-and-accelerators/fileact-interact/step-2c-add-interact-send-port-for-interact-store-and-forward-pull-scenario.md)