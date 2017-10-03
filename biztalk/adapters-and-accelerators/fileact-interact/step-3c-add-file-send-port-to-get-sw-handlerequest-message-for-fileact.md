---
title: "步驟 3c： 新增檔案傳送埠，以便擷取 Sw:HandleRequest 訊息 FileAct 即時案例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc0a9173-20df-4c73-80ee-755987d639d2
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3705f0b649e7f8d1c85898677ddc0301851dd302
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-3c-add-a-file-send-port-to-capture-swhandlerequest-message-for-the-fileact-real-time-scenario"></a>步驟 3c： 加入擷取 FileAct 即時案例 Sw:HandleRequest 訊息的 FILE 傳送埠
在開始此步驟之前，必須先完成[步驟 3B： 將 FILEACT 接收位置新增 FileAct 即時案例](../../adapters-and-accelerators/fileact-interact/step-3b-add-a-fileact-receive-location-for-the-fileact-real-time-scenario.md)。  
  
### <a name="to-add-a-file-send-port-to-capture-swhandlefilerequest-message"></a>若要加入檔案傳送埠以擷取 Sw:HandleFileRequest 訊息  
  
1.  啟動**BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，展開 [BizTalk 群組]，然後展開您要建立傳送埠的 BizTalk 應用程式。  
  
3.  以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態單向傳送埠。**  
  
4.  在**傳送埠屬性**視窗中，傳送埠，Tutorial_FA_SendResponseToReceiver。  
  
5.  在**傳送埠屬性**視窗中，從**傳輸類型**下拉式清單中，選取**檔案**，然後按一下 **設定**。  
  
6.  中**FILE 傳輸屬性**對話方塊中，於**目的地資料夾**方塊、 輸入 C:\SWIFTAdapterTutorial\Fileact\ResponseServer，，然後按一下**確定**。  
  
7.  在**傳送埠屬性**視窗中，執行下列動作：  
  
    |**使用此選項**|**若要這樣做**|  
    |------------------|--------------------|  
    |**傳送處理常式**|從下拉式清單選取**BizTalkServerApplication**。|  
    |**傳送管線**|從下拉式清單選取**XMLTransmit**。|  
  
8.  在**傳送埠屬性**視窗，請在**篩選**索引標籤上，執行下列動作：  
  
    |**使用此選項**|**若要這樣做**|  
    |------------------|--------------------|  
    |**屬性**|從下拉式清單選取**BTS。MessageType**。|  
    |**運算子**|從下拉式清單選取 **==** 。|  
    |**值**|型別**Sw HandleFileRequest**。|  
    |**群組依據**|保留預設值|  
  
9. 按一下 **[確定]**。  
  
## <a name="see-also"></a>另請參閱  
 [步驟 3： 建立傳送埠和接收埠以進行 FileAct 即時案例](../../adapters-and-accelerators/fileact-interact/step-3-create-the-send-ports-and-receive-ports-for-fileact-real-time-scenario.md)   
 [步驟 3A： 新增 FILE 接收位置 FileAct 即時案例](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-the-fileact-real-time-scenario.md)   
 [步驟 3B： 新增 FILEACT 接收位置 FileAct 即時案例](../../adapters-and-accelerators/fileact-interact/step-3b-add-a-fileact-receive-location-for-the-fileact-real-time-scenario.md)   
 [步驟 3D: FileAct 即時案例新增 FILEACT 傳送埠](../../adapters-and-accelerators/fileact-interact/step-3d-add-a-fileact-send-port-for-the-fileact-real-time-scenario.md)   
 [步驟 3E： 加入擷取 FileAct 即時案例 Sw:ExchangeFileResponse 訊息的 FILE 傳送埠](../../adapters-and-accelerators/fileact-interact/step-3e-add-file-send-port-to-get-sw-exchangefileresponse-message-for-fileact.md)