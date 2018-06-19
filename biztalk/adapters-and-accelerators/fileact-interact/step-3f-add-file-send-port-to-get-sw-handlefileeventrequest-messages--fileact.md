---
title: 步驟 3F： 新增檔案傳送埠 FileAct 即時案例以擷取 Sw HandleFileEventRequest 訊息 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0b7594b0-0443-41b7-ae04-55b2cc8bf90e
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b1d70c338696f1c4455161a88c8d2988e0ea0ccb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22225526"
---
# <a name="step-3f-add-a-file-send-port-for-the-fileact-real-time-scenario-to-capture-sw-handlefileeventrequest-messages"></a>步驟 3F： 新增 FileAct 即時案例以擷取 Sw HandleFileEventRequest 訊息的 FILE 傳送埠
在開始此步驟之前，必須先完成[步驟 3E: FileAct 即時案例中，將檔案傳送埠新增至擷取 Sw:ExchangeFileResponse 訊息](../../adapters-and-accelerators/fileact-interact/step-3e-add-file-send-port-to-get-sw-exchangefileresponse-message-for-fileact.md)  
  
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
    |**屬性**|選取 [BTS]。 MessageType|  
    |**運算子**|選取 = =|  
    |**值**|型別 Sw HandleFileEventRequest|  
    |**群組**|或|  
    |**屬性**|選取 [BTS]。 MessageType|  
    |**運算子**|選取 = =|  
    |**值**|型別 Sw ExchangeSnFResponse|