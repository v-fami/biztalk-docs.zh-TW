---
title: 步驟 3： 設定單向 FILE 傳送埠 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c52c6b6b-6f9c-48f2-8732-450fe3a15eae
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 67cc96dfccc7256681887290ef37261c4c7fecb9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36987919"
---
# <a name="step-3-configure-a-one-way-file-send-port"></a>步驟 3： 設定單向 FILE 傳送埠
在此步驟中，您會設定單向 FILE 傳送埠取用 REST 介面從收到的回應訊息，並將它複製到檔案位置。  

### <a name="to-configure-a-file-send-port"></a>若要設定 FILE 傳送埠  

1. BizTalk Server 管理主控台，從下**BizTalk Application 1**節點，以滑鼠右鍵按一下**傳送連接埠**，指向**新增**，然後按一下 **靜態單向傳送埠**。  

2. 在 [一般] 索引標籤上，執行下列動作：  

   |使用|以進行此動作|  
   |--------------|----------------|  
   |**名稱**|型別**SendPortOutAzureMarketPlaceData**。|  
   |**型別**|選取 **檔案**。|  
   |**傳送處理常式**|選取 **[BizTalkServerApplication]**。|  
   |**傳送管線**|選取  **PassThruTransmit**。|  

    按一下 **設定**。  

3. 從 [檔案傳輸屬性] 中，執行下列動作：  


   |      使用      |                                                              以進行此動作                                                               |
   |--------------------|---------------------------------------------------------------------------------------------------------------------------------------|
   | **接收資料夾** | 輸入的位置，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]複製回應訊息。 |
   |   **檔案名稱**    |                                                       保留 `%MessageID%.xml`                                                        |


4. 在 **篩選條件**索引標籤上，指定要取用所有的訊息寫入篩選器[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Messagebox 資料庫中建立的接收埠[步驟 2： 設定雙向 Wcf-webhttp 傳送埠](../core/step-2-configure-a-two-way-wcf-webhttp-send-port.md).  


   |              |                                       |
   |--------------|---------------------------------------|
   | **屬性** |         若要設定**BTS。SPName**         |
   | **[運算子]** |             若要設定 **==**             |
   |  **ReplTest1**   | 若要設定 `SendPortRESTAzureMarketPlace` |


5. 按一下 [確定] 。  

## <a name="see-also"></a>另請參閱  
 [教學課程 5： 叫用 REST 介面，使用 BizTalk Server](../core/tutorial-5-invoking-a-rest-interface-using-biztalk-server.md)