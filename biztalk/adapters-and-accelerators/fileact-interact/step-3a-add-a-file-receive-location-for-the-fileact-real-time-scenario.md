---
title: "步驟 3A： 新增 FILE 接收位置 FileAct 即時案例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 73b044b4-6611-493f-969c-02b52cb56ba7
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 266b29281ea7518cffee1461da2a3eaac66d9429
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-3a-add-a-file-receive-location-for-the-fileact-real-time-scenario"></a>步驟 3A： 新增 FILE 接收位置 FileAct 即時案例
在開始此步驟之前，必須先完成[步驟 2： 新增 SWIFTNet 設定 FileAct 即時案例 Paramfile](../../adapters-and-accelerators/fileact-interact/step-2-add-swiftnet-configuration-to-paramfile-for-fileact-real-time-scenario.md)。  
  
### <a name="to-add-a-file-receive-location"></a>若要新增 FILE 接收位置  
  
1.  啟動**BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，展開 [BizTalk 群組]，然後展開您要建立接收埠的 BizTalk 應用程式。  
  
3.  以滑鼠右鍵按一下**接收埠**，指向 **新增**，然後按一下 **單向接收埠。**  
  
4.  在**接收埠屬性**視窗中，接收埠，Tutorial_FA_InputRequest_RealTime。  
  
5.  在**接收埠屬性**視窗，請在**接收位置**索引標籤上，按一下 **新增**。  
  
6.  在**接收位置屬性**視窗，請在**一般**索引標籤上，從**傳輸類型**下拉式清單中，選取**檔案**，和然後按一下 **設定**。  
  
7.  在**FILE 傳輸屬性**對話方塊中，於**接收資料夾**方塊、 輸入 C:\SWIFTAdapterTutorial\Fileact\FileRequestDropRealTime，，然後按一下**確定**。  
  
8.  在**接收位置屬性**視窗，請在**一般**索引標籤上，執行下列動作：  
  
    |**使用此選項**|**若要這樣做**|  
    |------------------|--------------------|  
    |**接收處理常式**|從下拉式清單選取**BizTalkServerApplication**。|  
    |**接收管線**|從下拉式清單選取**XMLReceive**。|  
  
9. 按一下 **[確定]**。  
  
## <a name="see-also"></a>另請參閱  
 [步驟 3： 建立傳送埠和接收埠以進行 FileAct 即時案例](../../adapters-and-accelerators/fileact-interact/step-3-create-the-send-ports-and-receive-ports-for-fileact-real-time-scenario.md)   
 [步驟 3B： 新增 FILEACT 接收位置 FileAct 即時案例](../../adapters-and-accelerators/fileact-interact/step-3b-add-a-fileact-receive-location-for-the-fileact-real-time-scenario.md)   
 [步驟 3c： 加入擷取 FileAct 即時案例 Sw:HandleRequest 訊息的 FILE 傳送埠](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlerequest-message-for-fileact.md)   
 [步驟 3D: FileAct 即時案例新增 FILEACT 傳送埠](../../adapters-and-accelerators/fileact-interact/step-3d-add-a-fileact-send-port-for-the-fileact-real-time-scenario.md)   
 [步驟 3E： 加入擷取 FileAct 即時案例 Sw:ExchangeFileResponse 訊息的 FILE 傳送埠](../../adapters-and-accelerators/fileact-interact/step-3e-add-file-send-port-to-get-sw-exchangefileresponse-message-for-fileact.md)