---
title: 步驟 3A： 新增 FILE 接收位置的互動即時案例 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e5579375-8c05-4583-bcaa-b483ac275d8a
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6c29b3eb291b1b36daab5d77aae74f6055a3c738
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22224558"
---
# <a name="step-3a-add-a-file-receive-location-for-the-interact-real-time-scenario"></a>步驟 3A： 新增 FILE 接收位置的互動即時案例
設定接收位置，可讓您輕鬆地卸除的驗證測試檔案。 您可以使用這個位置來測試案例。  
  
## <a name="add-a-file-receive-location"></a>新增 FILE 接收位置  
  
1.  啟動**BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，展開 [BizTalk 群組]，然後展開您要建立接收埠的 BizTalk 應用程式。  
  
3.  以滑鼠右鍵按一下**接收埠**，指向 **新增**，然後按一下 **單向接收埠。**  
  
4.  在**接收埠屬性**視窗中，接收埠， **Tutorial_IA_InputRequest_RealTime**。  
  
5.  在**接收埠屬性**視窗，請在**接收位置**索引標籤上，按一下 **新增**。  
  
6.  在**接收位置屬性**視窗，請在**一般**索引標籤上，從**傳輸類型**下拉式清單中，選取**檔案**，和然後按一下 **設定**。  
  
7.  在**FILE 傳輸屬性**對話方塊中，於**接收資料夾**方塊中，輸入**C:\SWIFTAdapterTutorial\Interact\InputRequest_RealTime**，然後按一下  **確定**。  
  
8.  在**接收位置屬性**視窗，請在**一般**索引標籤上，執行下列動作：  
  
    |**使用此選項**|**若要這樣做**|  
    |------------------|--------------------|  
    |**接收處理常式**|從下拉式清單選取**BizTalkServerApplication**。|  
    |**接收管線**|從下拉式清單選取**XMLReceive**。|  
  
9. 按一下 **[確定]**。  
  
## <a name="see-also"></a>另請參閱  
 [步驟 3： 建立傳送和接收埠互動即時案例](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-the-interact-real-time-scenario.md)   
 [步驟 3B： 加入互動接收位置互動即時案例](../../adapters-and-accelerators/fileact-interact/step-3b-add-an-interact-receive-location-for-the-interact-real-time-scenario.md)   
 [步驟 3c： 新增檔案傳送埠，以便擷取 Sw:HandleRequest 訊息互動即時案例](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlerequest-interact-real-time-scenario.md)   
 [步驟 3D： 新增檔案傳送埠，以便擷取 Sw:HandleResponse 訊息互動即時案例](../../adapters-and-accelerators/fileact-interact/step-3d-add-file-send-port-to-get-sw-handleresponse-message-for-interact.md)   
 [步驟 3E： 加入互動的傳送埠互動即時案例](../../adapters-and-accelerators/fileact-interact/step-3e-add-an-interact-send-port-for-the-interact-real-time-scenario.md)