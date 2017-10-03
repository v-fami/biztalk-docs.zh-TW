---
title: "步驟 3c： 新增 FILE 傳送埠，以取得 Sw:HandleRequest-互動即時案例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 31e9c942-ba74-4ae2-b6e1-5266d0fbcb14
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4ddc38913b8bf9ea5c9450334e58dfaeb5ff4ad3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-3c-add-file-send-port-to-get-swhandlerequest-interact-real-time-scenario"></a>步驟 3c： 新增 FILE 傳送埠，以取得 Sw:HandleRequest-互動即時案例
當您傳送訊息給夥伴時，SWIFT 轉換訊息標頭，並將訊息轉寄給您的夥伴為 Sw:HandleRequest 訊息。 在開始此步驟之前，必須先完成[步驟 3B： 互動即時案例中加入互動的接收位置](../../adapters-and-accelerators/fileact-interact/step-3b-add-an-interact-receive-location-for-the-interact-real-time-scenario.md)。  
  
### <a name="to-add-a-file-send-port-to-capture-swhandlerequest-message"></a>若要加入檔案傳送埠以擷取 Sw:HandleRequest 訊息  
  
1.  啟動**BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，展開 [BizTalk 群組]，然後展開您要建立傳送埠的 BizTalk 應用程式。  
  
3.  以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態單向傳送埠。**  
  
4.  在**傳送埠屬性**視窗中，傳送埠**Tutorial_IA_SendResponseToReceiver**。  
  
5.  在**傳送埠屬性**視窗中，從**傳輸類型**下拉式清單中，選取**檔案**，然後按一下 **設定**。  
  
6.  中**FILE 傳輸屬性**對話方塊中，於**目的地資料夾**方塊、 輸入 C:\SWIFTAdapterTutorial\Interact\HandleRequest，，然後按一下**確定**。  
  
7.  在**傳送埠屬性**視窗中，執行下列動作：  
  
    |**使用此選項**|**若要這樣做**|  
    |------------------|--------------------|  
    |**傳送處理常式**|從下拉式清單選取**BizTalkServerApplication**。|  
    |**傳送管線**|從下拉式清單選取**XMLTransmit**。|  
  
8.  在**傳送埠屬性**視窗，請在**篩選**索引標籤上，執行下列動作：  
  
    |**使用此選項**|**若要這樣做**|  
    |------------------|--------------------|  
    |**屬性**|從下拉式清單選取**BTS。ReceivePortName**。|  
    |**運算子**|從下拉式清單選取 **==** 。|  
    |**值**|型別**Tutorial_IA_HandleRequestOneWay_RealTime。**|  
    |**群組依據**|保留預設值。|  
  
9. 按一下 **[確定]**。  
  
## <a name="see-also"></a>另請參閱  
 [步驟 3： 建立傳送和接收埠互動即時案例](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-the-interact-real-time-scenario.md)   
 [步驟 3A： 新增 FILE 接收位置的互動即時案例](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-the-interact-real-time-scenario.md)   
 [步驟 3B： 加入互動接收位置互動即時案例](../../adapters-and-accelerators/fileact-interact/step-3b-add-an-interact-receive-location-for-the-interact-real-time-scenario.md)   
 [步驟 3D： 新增檔案傳送埠，以便擷取 Sw:HandleResponse 訊息互動即時案例](../../adapters-and-accelerators/fileact-interact/step-3d-add-file-send-port-to-get-sw-handleresponse-message-for-interact.md)   
 [步驟 3E： 加入互動的傳送埠互動即時案例](../../adapters-and-accelerators/fileact-interact/step-3e-add-an-interact-send-port-for-the-interact-real-time-scenario.md)