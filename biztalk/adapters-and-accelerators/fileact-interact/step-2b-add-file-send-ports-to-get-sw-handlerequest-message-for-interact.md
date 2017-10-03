---
title: "步驟 2B： 將檔案傳送埠，以擷取 Sw:HandleRequest 訊息互動存放區和轉送 （提取） 案例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aa22d6e7-f1bd-43ad-9a0e-0b287057d20f
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 24200d21ef4a2047b94f9d818864a0a9da2ceb3b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-2b-add-file-send-ports-to-capture-the-swhandlerequest-message-for-the-interact-store-and-forward-pull-scenario"></a>步驟 2B： 將檔案傳送埠，以擷取 Sw:HandleRequest 訊息互動存放區和轉送 （提取） 案例
在開始此步驟之前，必須先完成[步驟 2A： 新增檔案接收位置互動存放區和轉送 （提取） 案例](../../adapters-and-accelerators/fileact-interact/step-2a-add-file-receive-locations-for-interact-store-and-forward-scenario.md)。  
  
### <a name="to-add-a-file-send-port-to-capture-the-swhandlerequest-message"></a>若要加入檔案傳送埠以擷取 Sw:HandleRequest 訊息  
  
1.  啟動**BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，展開 [BizTalk 群組]，然後展開您要建立傳送埠的 BizTalk 應用程式。  
  
3.  以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態單向傳送埠。**  
  
4.  在**傳送埠屬性**視窗中，傳送埠， **Tutorial_IA_SendPullResponsetoReceiver**。  
  
5.  在**傳送埠屬性**視窗中，從**傳輸類型**下拉式清單中，選取**檔案**，然後按一下 **設定**。  
  
6.  在**FILE 傳輸屬性**對話方塊中，於**目的地資料夾**方塊中，輸入**C:\SWIFTAdapterTutorial\Interact\PullResponse**，然後按一下  **確定**。  
  
7.  在**傳送埠屬性**視窗中，執行下列動作：  
  
    |**使用此選項**|**若要這樣做**|  
    |------------------|--------------------|  
    |**傳送處理常式**|從下拉式清單選取**BizTalkServerApplication**。|  
    |**傳送管線**|從下拉式清單選取**XMLTransmit**。|  
  
8.  按一下 **[確定]**。  
  
9. 重複步驟 1 和 2。  
  
10. 以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **動態請求-回應傳送埠**。  
  
11. 在**傳送埠屬性**視窗中，傳送埠**，Tutorial_IA_DynamicSendPort**。  
  
12. 在**傳送埠屬性**視窗中，執行下列動作：  
  
    |**使用此選項**|**若要這樣做**|  
    |------------------|--------------------|  
    |**傳送管線**|從下拉式清單選取**XMLTransmit**。|  
    |**接收管線**|從下拉式清單選取**XMLReceive**。|  
  
13. 按一下 **[確定]**。  
  
## <a name="see-also"></a>另請參閱  
 [步驟 2A： 新增檔案接收位置的互動存放區和轉送 （提取） 案例](../../adapters-and-accelerators/fileact-interact/step-2a-add-file-receive-locations-for-interact-store-and-forward-scenario.md)   
 [步驟 2c: 互動存放區和轉送 （提取） 案例中加入互動的傳送埠](../../adapters-and-accelerators/fileact-interact/step-2c-add-interact-send-port-for-interact-store-and-forward-pull-scenario.md)