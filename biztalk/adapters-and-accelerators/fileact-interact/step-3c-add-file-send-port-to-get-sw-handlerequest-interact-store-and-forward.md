---
title: 步驟 3c： 新增 FILE 傳送埠，以取得 Sw:HandleRequest-互動存放與轉寄 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c872b4be-ef8b-4e42-b5ef-63dfd120793f
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b82c57f2f3a6e2fcfc199e56d34c44aa7667451d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22225574"
---
# <a name="step-3c-add-file-send-port-to-get-swhandlerequest-interact-store-and-forward"></a>步驟 3c： 新增 FILE 傳送埠，以取得 Sw:HandleRequest-互動儲存與轉送
在開始此步驟之前，必須先完成[步驟 3B： 新增的互動接收位置為互動存放與轉寄實例](../../adapters-and-accelerators/fileact-interact/step-3b-add-interact-receive-location-for-interact-store-and-forward-scenario.md)。  
  
### <a name="to-add-a-file-send-port-to-capture-the-swhandlerequest-message"></a>若要加入檔案傳送埠以擷取 Sw:HandleRequest 訊息  
  
1.  啟動**BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，展開 [BizTalk 群組]，然後展開您要建立傳送埠的 BizTalk 應用程式。  
  
3.  以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態單向傳送埠。**  
  
4.  在**傳送埠屬性**視窗中，傳送埠，Tutorial_IA_SendResponseToReceiver。  
  
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
    |**值**|型別**Tutorial_IA_InputRequest_SnF**。|  
    |**群組依據**|保留預設值。|  
  
9. 按一下 **[確定]**。  
  
## <a name="see-also"></a>另請參閱  
 [步驟 3： 建立傳送埠和接收埠以進行互動的存放區和轉寄的案例](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-interact-store-and-forward-scenario.md)   
 [步驟 3A： 新增 FILE 接收位置為互動存放區與正向的實例](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-interact-store-and-forward-scenario.md)   
 [步驟 3B： 加入互動接收位置的互動存放區和轉寄的案例](../../adapters-and-accelerators/fileact-interact/step-3b-add-interact-receive-location-for-interact-store-and-forward-scenario.md)   
 [步驟 3D: 互動存放區和轉寄的案例中加入互動的傳送埠](../../adapters-and-accelerators/fileact-interact/step-3d-add-an-interact-send-port-for-the-interact-store-and-forward-scenario.md)