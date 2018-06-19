---
title: 步驟 6： 建立傳送埠以傳送 ADT ^ A03 訊息使用 File 配接器之接收系統 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- end-to-end tutorial, send ports
- creating, send ports
- send ports, creating
ms.assetid: 66c4b524-c8ff-43b5-9c44-6d7bc759ae2c
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 62581310d4260ecb5b1162df1f52b0170d791d57
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26005503"
---
# <a name="step-6-create-a-send-port-to-deliver-the-adta03-message-to-the-rx-system-using-the-file-adapter"></a>步驟 6： 建立傳送埠以傳送 ADT ^ A03 RX 系統使用 File 配接器的訊息
在此步驟中，您建立傳送埠的藥局系統 (RX) 使用 File 配接器。  
  
### <a name="to-create-the-tutorialsendmsgrx-send-port"></a>若要建立 Tutorial_sendMsg_RX 傳送埠  
  
1.  在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態單向傳送埠**。  
  
2.  在**傳送埠屬性**對話方塊方塊中，執行下列動作，然後按一下**確定**。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**名稱**|型別**Tutorial_sendMsg_RX**。|  
    |**傳輸類型**|選取**檔案**從下拉式清單。|  
    |**設定**|按一下**設定**開啟**File 傳輸屬性** 對話方塊。|  
  
3.  在 [FILE 傳輸屬性] 對話方塊中，執行下列動作，然後按一下**確定**。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**目的地資料夾**|瀏覽至 **\<** *磁碟機***:\>\Program Files\Microsoft BizTalk\<版本\>Accelerator for HL7\SDK\End 端對端Tutorial\Tutorial_sendMsg_RX**。|  
    |**檔案名稱**|型別 **%MessageID%.txt** （副檔名為.txt 取代.xml 副檔名）。|  
  
4.  在**傳送埠屬性**對話方塊中，針對**傳送管線**，選取**BTAHL72XPipelines.BTAHL72XSendPipeline**。  
  
5.  在左窗格中，選取**篩選**，然後執行下列動作。 按一下 **[確定]** 繼續進行。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**屬性**（第一次換行）|選取**BTS。MessageType**從下拉式清單。|  
    |**運算子**|選取 **！ =** 從下拉式清單。|  
    |**值**|型別**http://microsoft.com/HealthCare/HL7/2X#ACK_24_GLO_DEF**。|  
    |**Group By**|選取**或**從下拉式清單。|  
    |**屬性**（第二行）|按一下下方的欄位**屬性**，然後選取**BTS。MessageType**從下拉式清單。|  
    |**運算子**|選取 **！ =** 從下拉式清單。|  
    |**值**|型別**http://microsoft.com/HealthCare/HL7/2X#ACK_25_GLO_DEF。**|  
    |**Group By**|選取**AND**從下拉式清單。|  
    |**屬性**（第三個行）|選取**BTAHL7Schemas.MSH3_1**。|  
    |**運算子**|選取 **==** 從下拉式清單。|  
    |**值**|型別**Tutorial_ADTSystem**。|  
  
    > [!NOTE]
    >  第一個篩選條件會表示醫院資訊系統 (HIS) 訊息時，不會通知訂閱。 第二個篩選表示他其來源是許可放電和傳輸 (ADT) 系統的訊息來進行訂閱。  
  
    > [!NOTE]
    >  BTAHL7 會捨棄訊息，在檔案放置位置\<*磁碟機*\>： 程式 FilesMicrosoft BizTalk<version>的端對端 HL7SDKEnd TutorialTutorial_sendMsg_RX 加速器。  
  
6.  按一下**套用**，然後按一下  **確定。**  
  
7.  在 管理主控台中，按一下 **傳送埠**，以滑鼠右鍵按一下**Tutorial_sendMsg_RX**，然後按一下 **啟動**。  
  
 若要繼續[步驟 7： 建立傳送埠以傳送 ADT ^ A03 他使用 MLLP 配接器的訊息](../../adapters-and-accelerators/accelerator-hl7/step-7-create-send-port-to-deliver-adt^a03-message-to-his-using-mllp-adapter.md)。