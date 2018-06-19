---
title: 步驟 2B： 將檔案傳送埠，以擷取 Sw:HandleFileRequest 和 Sw:HandleSnFRequest FileAct 存放與轉寄的訊息 （提取） 案例 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 21d055e9-ff7c-4af1-983b-d03e8d4a94f6
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3c2eb55cd6aca9b26b8a8ac47ab6dbe192f174d8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22224358"
---
# <a name="step-2b-add-file-send-ports-to-capture-the-swhandlefilerequest-and-swhandlesnfrequest-messages-for-the-fileact-store-and-forward-pull-scenario"></a>步驟 2B： 將檔案傳送埠，以擷取 Sw:HandleFileRequest 和 Sw:HandleSnFRequest FileAct 存放與轉寄的訊息 （提取） 案例
在開始此步驟之前，必須先完成[步驟 2A： 新增檔案接收位置 FileAct 存放與轉寄 （提取） 案例](../../adapters-and-accelerators/fileact-interact/step-2a-add-file-receive-locations-for-fileact-store-and-forward-scenario.md)> 一節。  
  
### <a name="to-add-a-file-send-port-to-capture-the-sw-handlefilerequest-message"></a>若要加入檔案傳送埠以擷取 Sw: HandleFileRequest 訊息  
  
1.  啟動**BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，展開 [BizTalk 群組]，然後展開您要建立傳送埠的 BizTalk 應用程式。  
  
3.  以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態單向傳送埠。**  
  
4.  在**傳送埠屬性**視窗中，傳送埠， **Tutorial_FA_SendPullResponsetoReceiver**。  
  
5.  在**傳送埠屬性**視窗中，從**傳輸類型**下拉式清單中，選取**檔案**，然後按一下 **設定**。  
  
6.  在**FILE 傳輸屬性**對話方塊中，於**目的地資料夾**方塊中，輸入**C:\SWIFTAdapterTutorial\FileAct\PullResponse**，然後按一下  **確定**。  
  
7.  在**傳送埠屬性**視窗中，執行下列動作：  
  
    |**使用此選項**|**若要這樣做**|  
    |------------------|--------------------|  
    |**傳送處理常式**|從下拉式清單選取**BizTalkServerApplication**。|  
    |**傳送管線**|從下拉式清單選取**XMLTransmit**。|  
  
8.  按一下 **[確定]**。  
  
9. 重複步驟 1 和 2。  
  
10. 以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **動態請求-回應傳送埠**。  
  
11. 在**傳送埠屬性**視窗中，傳送埠 **，Tutorial_IA_DynamicSendPort**。  
  
12. 在**傳送埠屬性**視窗中，執行下列動作：  
  
    |**使用此選項**|**若要這樣做**|  
    |------------------|--------------------|  
    |**傳送管線**|從下拉式清單選取**XMLTransmit**。|  
    |**接收管線**|從下拉式清單選取**XMLReceive**。|  
  
13. 按一下 **[確定]**。  
  
## <a name="see-also"></a>另請參閱  
 [步驟 2A： 新增檔案接收位置的 FileAct 存放與轉寄 （提取） 案例](../../adapters-and-accelerators/fileact-interact/step-2a-add-file-receive-locations-for-fileact-store-and-forward-scenario.md)   
 [步驟 2c： 新增為 FileAct 存放與轉寄 （提取） 實例 FILEACT 傳送埠](../../adapters-and-accelerators/fileact-interact/step-2c-add-a-fileact-send-port-for-fileact-store-and-forward-pull-scenario.md)