---
title: "步驟 5： 建立傳送埠將訊息傳遞 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f56ad7a7-5c77-4191-a001-691e5e0652a1
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e85033256f7a49ed506fea00a7b48db67b0da1b9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-5-create-a-send-port-to-deliver-messages"></a>步驟 5： 建立傳送埠將訊息傳遞
在此步驟中，您可以建立和設定傳送接收之批次中包含的個別訊息的連接埠。 稍後在教學課程中，將原始的合作對象 (Tutorial_BatchSource) 片段中啟用[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管。 如此一來，BizTalk 整合引擎時，會為個別的訊息片段批次和[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]會透過您在此步驟中建立的傳送埠傳送這些訊息。  
  
 您建立此連接埠是靜態，如此才會與 MLLP 配接器相關聯，它只會傳送到特定的目的地 （目的地的特定業務應用程式）。 在本教學課程中，該目的地會是包含在個別訊息 MSH5 MESA_IS。 您可以建立連接埠限制連接埠傳送訊息，而非通知來篩選掉符合 ACK_024_GLO_DEF 結構描述或任何靜態通知 (ACK) 訊息的篩選器。  
  
 您設定這個傳送埠來接收通知的目的地，與名為接收埠產生關聯的傳送埠**TwoWayAckReceivePort**。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]安裝程式會建立此連接埠，以及隨附的接收位置的**TwoWayAckReceiveLocation**。 您設定傳送埠設定來使用此連接埠**請求回應啟用**至**是**和設定**提交接收位置 URI**至**127.0.0.1:65535** （接受認可所需的設定）。 如需詳細資訊，請參閱[設定向上傳送埠的接收認可](../../adapters-and-accelerators/accelerator-hl7/setting-up-a-send-port-for-receiving-acks.md)。  
  
### <a name="to-create-a-send-port-to-deliver-messages"></a>若要建立傳送埠將訊息傳遞  
  
1.  在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態單向傳送埠**。  
  
2.  在 [傳送埠屬性] 對話方塊中，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**名稱**|型別**Tutorial_2wayMsg**。|  
    |**傳輸類型**|選取**MLLP**從下拉式清單。|  
    |**設定**|按一下**設定**開啟 MLLP 傳輸屬性 對話方塊。|  
  
3.  在 MLLP 傳輸屬性 對話方塊中，執行下列作業：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**連接名稱**|型別**2wayMsg**。|  
    |**Host**|型別**localhost**。|  
    |**[通訊埠]**|型別**41000**。|  
    |**請求回應已啟用**|按一下右邊的欄位**請求回應啟用**，然後選取**是**從下拉式清單。|  
    |**送出接收位置 (URI) 的通知**|型別**127.0.0.1:65535**|  
  
4.  按一下 **[確定]**。  
  
5.  在 [傳送埠屬性] 對話方塊的**傳送管線**，選取**BTAHL72XPipelines.BTAHL72XSendPipeline**。  
  
6.  在主控台樹狀目錄中，按一下**篩選**，然後執行下列步驟：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**屬性**（第一次換行）|按一下下方的欄位**屬性**，然後選取**BTS。MessageType**從下拉式清單。|  
    |**運算子**|選取**！ =**從下拉式清單。|  
    |**值**|型別**http://microsoft.com/HealthCare/HL7/2X#ACK_24_GLO_DEF**。|  
    |**Group By**|選取**AND**從下拉式清單。|  
    |**屬性**（第二行）|按一下下方的欄位**屬性**，然後選取**BTS。MessageType**從下拉式清單。|  
    |**運算子**|選取**！ =**從下拉式清單。|  
    |**值**|型別**http://microsoft.com/HealthCare/HL7/2X#ACK_25_GLO_DEF。**|  
    |**Group By**|選取**和**從下拉式清單。|  
    |**屬性**（第三個行）|按一下底下的第二列的欄位**屬性**，然後選取**BTS。MessageType**從下拉式清單。|  
    |**運算子**|選取**！ =**從下拉式清單。|  
    |**值**|型別**StaticAck**。|  
  
7.  按一下 **[輸入]**。 在對話方塊底部窗格中，確認正確地輸入篩選運算式，然後按一下**確定**。  
  
8.  在 管理主控台中，按一下 **傳送埠**，以滑鼠右鍵按一下**Tutorial_2wayMsg**，然後按一下 **啟動**。  
  
 若要繼續[步驟 6： 建立要傳遞通知的傳送埠](../../adapters-and-accelerators/accelerator-hl7/step-6-create-a-send-port-to-deliver-acknowledgments.md)。