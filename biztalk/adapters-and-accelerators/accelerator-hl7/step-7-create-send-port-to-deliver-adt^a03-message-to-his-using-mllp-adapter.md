---
title: "步驟 7： 建立傳送埠以傳送 ADT ^ A03 他使用 MLLP 配接器的訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- end-to-end tutorial, send ports
- creating, send ports
- send ports, creating
ms.assetid: d9e7f281-3d25-4675-a13e-0e2057f5e69a
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fc122ab37ee0d618c3bd75792a5b88571dd49162
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-7-create-a-send-port-to-deliver-the-adta03-message-to-his-using-the-mllp-adapter"></a>步驟 7： 建立傳送埠以傳送 ADT ^ A03 他使用 MLLP 配接器的訊息
在此步驟中，您可以建立要傳送訊息至醫院資訊系統 (HIS) 使用 MLLP 配接器的傳送埠。  
  
### <a name="to-create-the-tutorialmllpsend-send-port"></a>若要建立 Tutorial_MllpSend 傳送埠  
  
1.  在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態單向傳送埠**。  
  
2.  在 [傳送埠屬性] 對話方塊中，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**名稱**|型別**Tutorial_MllpSend**。|  
    |**傳輸類型**|選取**MLLP**從下拉式清單。|  
    |**設定**|按一下**設定**開啟**MLLP 傳輸屬性** 對話方塊。|  
  
3.  在 MLLP 傳輸屬性 對話方塊中，執行下列動作，然後按一下**確定**。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**連接名稱**|型別**1WaySend**。|  
    |**Host**|型別**localhost**。|  
    |**[通訊埠]**|型別**14000**。|  
  
4.  在 [傳送埠屬性] 對話方塊的**傳送管線**，選取**BTAHL72XPipelines.BTAHL72XSendPipeline**。  
  
5.  在左窗格中，選取**篩選**，然後執行下列步驟：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**屬性**|選取**BTS。ReceivePortName**從下拉式清單。|  
    |**運算子**|選取 **==** 從下拉式清單。|  
    |**值**|型別**Tutorial_1WayReceive**。|  
  
    > [!NOTE]
    >  1WayReceive 有任何訊息中指定的連接埠會接聽連接埠。  
  
6.  按一下**套用**，然後按一下  **確定。**  
  
7.  在 管理主控台中，按一下 **傳送埠**，以滑鼠右鍵按一下**Tutorial_MllpSend**，然後按一下 **啟動**。  
  
 若要繼續[步驟 8： 設定合作對象資訊](../../adapters-and-accelerators/accelerator-hl7/step-8-configure-party-information.md)。