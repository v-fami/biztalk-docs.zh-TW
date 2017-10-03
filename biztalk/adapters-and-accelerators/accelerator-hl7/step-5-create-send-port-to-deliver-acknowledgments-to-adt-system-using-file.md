---
title: "步驟 5： 建立傳送埠，以便將通知傳送到使用 File 配接器 ADT 系統 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- end-to-end tutorial, send ports
- send ports, acknowledgements
- creating, send ports
- acknowledgements, send ports
- send ports, creating
ms.assetid: 565a2adf-fd86-46e3-8035-7e4748aefffc
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 926a13d443e7002a71e2b9f6509c3a377f0af0be
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-5-create-a-send-port-to-deliver-acknowledgments-to-the-adt-system-using-the-file-adapter"></a>步驟 5： 建立傳送埠，以便將通知傳送到使用 File 配接器 ADT 系統
在此步驟中，您可以建立傳送埠，以產生使用 File 配接器的通知。  
  
### <a name="to-create-the-tutorialsendackadt-send-port"></a>若要建立 Tutorial_sendAck_ADT 傳送埠  
  
1.  使用[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]總管 中，建立\<*磁碟機*: > \Program Files\Microsoft BizTalk\<版本 > Accelerator for HL7\SDK\End 端對端 Tutorial\Tutorial_sendAck_ADT 資料夾。  
  
2.  在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態單向傳送埠**。  
  
3.  在 [傳送埠屬性] 對話方塊中，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**名稱**|型別**Tutorial_sendAck_ADT**。|  
    |**傳輸類型**|選取**檔案**從下拉式清單。|  
    |**設定**|按一下**設定**開啟**File 傳輸屬性** 對話方塊。|  
  
4.  在 FILE 傳輸屬性 對話方塊中，執行下列動作，然後按一下 **確定**。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**目的地資料夾**|瀏覽至 **\<** *磁碟機***: > \Program Files\Microsoft BizTalk\<版本 > Accelerator for HL7\SDK\End 端對端 Tutorial\Tutorial_sendAck_ADT**.|  
    |**檔案名稱**|型別**%MessageID%.txt** （副檔名為.txt 取代.xml 副檔名）。|  
  
5.  在 [傳送埠屬性] 對話方塊的**傳送管線**，選取**BTAHL72XPipelines.BTAHL72XSendPipeline**。  
  
6.  在左窗格中，按一下 **篩選**，然後執行下列步驟：  
  
    > [!NOTE]
    >  第一個篩選條件，表示您要訂閱的通知訊息。 第二個篩選表示您要訂閱通知，並且用於 Tutorial_ADTSystem 「 發行者 」。  
  
     按一下**確定**當您準備好繼續進行。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**屬性**|按一下下方的欄位**屬性**，然後選取**BTS。MessageType**從下拉式清單。|  
    |**運算子**|選取 **==** 從下拉式清單。|  
    |**值**|型別**http://microsoft.com/HealthCare/HL7/2X#ACK_24_GLO_DEF**。|  
    |**Group By**|選取**或**從下拉式清單。|  
    |**屬性 （第二行）**|按一下下方的欄位**屬性**，然後選取**BTS。MessageType**從下拉式清單。|  
    |**運算子**|選取 **==** 從下拉式清單。|  
    |**值**|型別**http://microsoft.com/HealthCare/HL7/2X#ACK_25_GLO_DEF。**|  
    |**Group By**|選取**AND**從下拉式清單。|  
    |**屬性**|在第一個屬性中，按一下空白的方塊，，然後選取**BTAHL7Schemas.MSH5_1**。|  
    |**運算子**|選取 **==** 從下拉式清單。|  
    |**值**|型別**Tutorial_ADTSystem**。|  
  
    > [!NOTE]
    >  Tutorial_sendAck_ADT 傳送埠，BTAHL7 會卸除的通知在檔案放置位置\<*磁碟機*>: Program FilesMicrosoft BizTalk <version> Accelerator for HL7SDKEnd 端對端 TutorialTutorial_sendAck_ADT。  
  
7.  按一下**套用**，然後按一下  **確定。**  
  
8.  在 管理主控台中，按一下 **傳送埠**，以滑鼠右鍵按一下**Tutorial_sendAck_ADT**，然後按一下 **啟動**。  
  
 若要繼續[步驟 6： 建立傳送埠以傳送 ADT ^ A03 訊息使用 File 配接器之接收系統](../../adapters-and-accelerators/accelerator-hl7/step-6-create-send-port-to-deliver-adt^a03-message-to-rx-system-using-file.md)。