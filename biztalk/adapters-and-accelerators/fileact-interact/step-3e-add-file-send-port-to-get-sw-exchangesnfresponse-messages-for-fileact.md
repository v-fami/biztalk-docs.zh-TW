---
title: "步驟 3E： 新增檔案傳送埠的 FileAct 存放與轉寄案例以擷取 Sw ExchangeSnFResponse 訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 04bad2ab-1ea4-4602-9dee-5b9af9be3b93
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 44cf320f22f5acc2511d6327c36c54cda8f0dd1c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-3e-add-a-file-send-port-for-the-fileact-store-and-forward-scenario-to-capture-sw-exchangesnfresponse-messages"></a>步驟 3E： 新增 FileAct 存放與轉寄案例以擷取 Sw ExchangeSnFResponse 訊息 FILE 傳送埠
在開始此步驟之前，必須先完成[步驟 3D： 新增 FILEACT 傳送埠為 FileAct 存放與轉寄實例](../../adapters-and-accelerators/fileact-interact/step-3d-add-a-fileact-send-port-for-the-fileact-store-and-forward-scenario.md)。  
  
### <a name="to-add-a-file-send-port-to-capture-status-events"></a>若要新增 FILE 傳送埠來擷取狀態事件：  
  
1.  啟動**BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，展開 [BizTalk 群組]，然後展開您要建立傳送埠的 BizTalk 應用程式。  
  
3.  以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態單向傳送埠**。  
  
4.  在**傳送埠屬性**視窗中，傳送埠，Tutorial_ GetStatusReports。  
  
5.  在**傳送埠屬性**視窗中，從**傳輸類型**下拉式清單中，選取**檔案**，然後按一下 **設定**。  
  
6.  在**FILE 傳輸屬性**對話方塊中，於**目的地資料夾**方塊、 輸入 C:\SWIFTAdapterTutorial\Fileact\ StatusEvents，然後按一下**確定**。  
  
7.  在**傳送埠屬性**視窗中，執行下列動作：  
  
    |**使用此選項**|**若要這樣做**|  
    |------------------|--------------------|  
    |**傳送處理常式**|從下拉式清單選取**BizTalkServerApplication**。|  
    |**傳送管線**|從下拉式清單選取**XMLTransmit**。|  
  
8.  在**傳送埠屬性**視窗，請在**篩選**索引標籤上，執行下列動作：  
  
    |**使用此選項**|**若要這樣做**|  
    |------------------|--------------------|  
    |**屬性**|選取 [BTS]。訊息類型|  
    |**運算子**|選取 = =|  
    |**值**|型別 Sw HandleFileEventRequest|  
    |**群組**|或|  
    |**屬性**|選取 [BTS]。 MessageType|  
    |**運算子**|選取 = =|  
    |**值**|型別 Sw ExchangeSnFResponse|