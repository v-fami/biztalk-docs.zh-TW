---
title: 步驟 2A： 新增檔案接收位置的互動存放區和轉送 （提取） 案例 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: acdc30e1-d80c-40bf-864d-bf136c77a2b8
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 195480b616437eea7b1cfafa703d4ec5d0bd2b54
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22225270"
---
# <a name="step-2a-add-file-receive-locations-for-the-interact-store-and-forward-pull-scenario"></a>步驟 2A： 新增檔案接收位置的互動存放區和轉送 （提取） 案例
在開始此步驟之前，必須先完成[步驟 2： 新增 SWIFTNet 組態為互動存放與轉寄實例 Paramfile](../../adapters-and-accelerators/fileact-interact/step-2-add-swiftnet-configuration-to-paramfile-for-interact-store-and-forward.md)。  
  
### <a name="to-add-a-file-receive-location"></a>若要新增 FILE 接收位置  
  
1.  啟動**BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，展開 [BizTalk 群組]，然後展開您要建立接收埠的 BizTalk 應用程式。  
  
3.  以滑鼠右鍵按一下**接收埠**，指向 **新增**，然後按一下 **單向接收埠。**  
  
4.  在**接收埠屬性**視窗中，接收埠， **Tutorial_IA_InputRequest_SnF**。  
  
5.  在**接收埠屬性**視窗，請在**接收位置**索引標籤上，按一下 **新增**。  
  
6.  在**接收位置屬性**視窗，請在**一般**索引標籤上，從**傳輸類型**下拉式清單中，選取**檔案**，和然後按一下 **設定**。  
  
7.  在**FILE 傳輸屬性**] 對話方塊中，輸入**C:\SWIFTAdapterTutorial\Interact\InputRequest_SnF**，然後按一下 [**確定**。  
  
8.  在**接收位置屬性**視窗，請在**一般**索引標籤上，執行下列動作：  
  
    |**使用此選項**|**若要這樣做**|  
    |------------------|--------------------|  
    |**接收處理常式**|從下拉式清單選取**BizTalkServerApplication**。|  
    |**接收管線**|從下拉式清單選取**XMLReceive**。|  
  
9. 按一下 **[確定]**。  
  
10. 重複步驟 1 和 2。  
  
11. 以滑鼠右鍵按一下**接收埠**，指向 **新增**，然後按一下 **單向接收埠。**  
  
12. 在**接收埠屬性**視窗中，接收埠， **Tutorial_IA_InputRequest_PullMode**。  
  
13. 在**接收埠屬性**視窗，請在**接收位置**索引標籤上，按一下 **新增**。  
  
14. 在**接收位置屬性**視窗，請在**一般**索引標籤上，從**傳輸類型**下拉式清單中，選取**檔案**，和然後按一下 **設定**。  
  
15. 在**FILE 傳輸屬性**] 對話方塊中，輸入**C:\SWIFTAdapterTutorial\Interact\PullRequest**，然後按一下 [**確定**。  
  
16. 在**接收位置屬性**視窗，請在**一般**索引標籤上，執行下列動作：  
  
    |**使用此選項**|**若要這樣做**|  
    |------------------|--------------------|  
    |**接收處理常式**|從下拉式清單選取**BizTalkServerApplication**。|  
    |**接收管線**|從下拉式清單選取**XMLReceive**。|  
  
17. 按一下 **[確定]**。  
  
## <a name="see-also"></a>另請參閱  
 [步驟 2B： 將檔案傳送埠，以擷取 Sw:HandleRequest 訊息互動存放區和轉送 （提取） 案例](../../adapters-and-accelerators/fileact-interact/step-2b-add-file-send-ports-to-get-sw-handlerequest-message-for-interact.md)   
 [步驟 2c: 互動存放區和轉送 （提取） 案例中加入互動的傳送埠](../../adapters-and-accelerators/fileact-interact/step-2c-add-interact-send-port-for-interact-store-and-forward-pull-scenario.md)