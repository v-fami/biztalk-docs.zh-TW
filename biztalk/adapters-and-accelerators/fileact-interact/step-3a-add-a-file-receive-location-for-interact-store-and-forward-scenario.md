---
title: "步驟 3A： 新增 FILE 接收位置為互動存放區與正向實例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5f4bae51-6869-4334-a3a1-ef7e662197ca
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7d2027878771249ceb2dcb45683a71b4475a75cd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-3a-add-a-file-receive-location-for-the-interact-store-and-forward-scenario"></a>步驟 3A： 新增 FILE 接收位置為互動存放區與正向的實例
完成[步驟 2： 新增 SWIFTNet 組態為互動存放與轉寄實例 Paramfile](../../adapters-and-accelerators/fileact-interact/step-2-add-swiftnet-configuration-to-paramfile-for-interact-store-and-forward.md)開始此步驟之前。
  
## <a name="add-a-file-receive-location"></a>新增 FILE 接收位置  
  
1.  啟動**BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，展開 [BizTalk 群組]，然後展開您要建立接收埠的 BizTalk 應用程式。  
  
3.  以滑鼠右鍵按一下**接收埠**，指向 **新增**，然後按一下 **單向接收埠。**  
  
4.  在**接收埠屬性**視窗中，接收埠，Tutorial_IA_InputRequest_SnF。  
  
5.  在**接收埠屬性**視窗，請在**接收位置**索引標籤上，按一下 **新增**。  
  
6.  在**接收位置屬性**視窗，請在**一般**索引標籤上，從**傳輸類型**下拉式清單中，選取**檔案**，和然後按一下 **設定**。  
  
7.  在**FILE 傳輸屬性**對話方塊中，輸入 C:\SWIFTAdapterTutorial\Interact\InputRequest_SnF，，然後按一下**確定**。  
  
8.  在**接收位置屬性**視窗，請在**一般**索引標籤上，執行下列動作：  
  
    |**使用此選項**|**若要這樣做**|  
    |------------------|--------------------|  
    |**接收處理常式**|從下拉式清單選取**BizTalkServerApplication**。|  
    |**接收管線**|從下拉式清單選取**XMLReceive**。|  
  
9. 按一下 **[確定]**。  
  
## <a name="complete-steps"></a>完成步驟
 [步驟 3： 建立傳送埠和接收埠以進行互動的存放區和轉寄的案例](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-interact-store-and-forward-scenario.md)   
 [步驟 3B： 加入互動接收位置的互動存放區和轉寄的案例](../../adapters-and-accelerators/fileact-interact/step-3b-add-interact-receive-location-for-interact-store-and-forward-scenario.md)   
 [步驟 3c： 新增檔案傳送埠，以便擷取 Sw:HandleRequest 訊息互動存放區和轉寄的案例](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlerequest-interact-store-and-forward.md)  
 [步驟 3D: 互動存放區和轉寄的案例中加入互動的傳送埠](../../adapters-and-accelerators/fileact-interact/step-3d-add-an-interact-send-port-for-the-interact-store-and-forward-scenario.md)