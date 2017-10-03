---
title: "步驟 3D： 新增檔案傳送埠，以便擷取 Sw:HandleResponse 訊息互動即時案例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e05e4d20-4cf2-402f-aaea-66987cb6515a
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5a0c8c8721d9f7de7b1cd1e57537aa02d2ed8fd5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-3d-add-a-file-send-port-to-capture-the-swhandleresponse-message-for-the-interact-real-time-scenario"></a>步驟 3D： 新增檔案傳送埠，以便擷取 Sw:HandleResponse 訊息互動即時案例
完成[步驟 3c： 新增檔案傳送埠，以便擷取 Sw:HandleRequest 訊息互動即時案例](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlerequest-interact-real-time-scenario.md)開始此步驟之前。
  
## <a name="add-a-file-send-port-to-capture-swhandleresponse-message"></a>將檔案傳送埠以擷取 Sw:HandleResponse 訊息  
  
1.  啟動**BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，展開 [BizTalk 群組]，然後展開您要建立傳送埠的 BizTalk 應用程式。  
  
3.  以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態單向傳送埠。**  
  
4.  在**傳送埠屬性**視窗中，傳送埠**Tutorial_IA_SendResponseToSender**。  
  
5.  在**傳送埠屬性**視窗中，從**Transporttype**下拉式清單中，選取**檔案**，然後按一下 **設定**。  
  
6.  在**FILE 傳輸屬性**對話方塊中，於**目的地資料夾**方塊中，輸入**C:\SWIFTAdapterTutorial\Interact\Response**，然後按一下  **確定**。  
  
7.  在**傳送埠屬性**視窗中，執行下列動作：  
  
    |**使用此選項**|**若要這樣做**|  
    |------------------|--------------------|  
    |**傳送處理常式**|從下拉式清單選取**BizTalkServerApplication**。|  
    |**傳送管線**|從下拉式清單選取**XMLTransmit**。|  
  
8.  在**傳送埠屬性**視窗，請在**篩選**索引標籤上，執行下列動作：  
  
    |**使用此選項**|**若要這樣做**|  
    |------------------|--------------------|  
    |第一次資料列：**屬性**|從下拉式清單選取**BTS。SPName**。|  
    |第一次資料列：**運算子**|從下拉式清單選取 **==** 。|  
    |第一次資料列：**值**|型別**Tutorial_IA_HandleRequest_RealTime**。|  
    |第一次資料列：**分組**|從下拉式清單選取**或**。|  
    |第二個資料列：**屬性**|從下拉式清單選取**BTS。MessageType**。|  
    |第二個資料列：**運算子**|從下拉式清單選取 **==** 。|  
    |第二個資料列：**值**|型別**SwInt ExchangeResponse**。|  
    |第二個資料列：**分組**|保留預設值。|  
  
9. 按一下 **[確定]**。  
  
## <a name="see-also"></a>另請參閱  
 [步驟 3： 建立傳送和接收埠互動即時案例](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-the-interact-real-time-scenario.md)   
 [步驟 3A： 新增 FILE 接收位置的互動即時案例](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-the-interact-real-time-scenario.md)   
 [步驟 3B： 加入互動接收位置互動即時案例](../../adapters-and-accelerators/fileact-interact/step-3b-add-an-interact-receive-location-for-the-interact-real-time-scenario.md)   
 [步驟 3c： 新增檔案傳送埠，以便擷取 Sw:HandleRequest 訊息互動即時案例](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlerequest-interact-real-time-scenario.md)   
 [步驟 3E： 加入互動的傳送埠互動即時案例](../../adapters-and-accelerators/fileact-interact/step-3e-add-an-interact-send-port-for-the-interact-real-time-scenario.md)