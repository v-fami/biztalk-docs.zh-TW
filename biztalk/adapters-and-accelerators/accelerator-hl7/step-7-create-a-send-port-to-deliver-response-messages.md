---
title: 步驟 7： 建立傳送埠以傳送回應訊息 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- interrogative tutorial, send ports
ms.assetid: 5edaefb6-72f2-4317-9477-f3a0d0027e0c
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1260772f3b3df5f0dea96b0aa66023e107b9aa6c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22207078"
---
# <a name="step-7-create-a-send-port-to-deliver-response-messages"></a>步驟 7： 建立傳送埠以傳送回應訊息
在此步驟中，您建立傳送埠傳送查詢回應，回到許可、 放電和傳輸 (ADT) 系統。  
  
### <a name="to-create-the-adtsend-send-port"></a>若要建立 ADT_Send 傳送埠  
  
1.  在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後選取**靜態單向傳送埠**。  
  
2.  在 [傳送埠屬性] 對話方塊中，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**名稱**|型別**ADT_Send**。|  
    |**傳輸類型**|選取**MLLP**。|  
    |**設定**|按一下**設定**按鈕右邊的**類型**。|  
  
3.  在 MLLP 傳輸屬性 對話方塊中，輸入下列資訊，然後再按一下**確定**。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**連接名稱**|型別**ADT_SendMLLP**。|  
    |**Host**|型別**localhost**。|  
    |**[通訊埠]**|型別**25000**。|  
  
4.  在 [傳送埠屬性] 對話方塊的**傳送管線**，選取**BTAHL72XPipelines.BTAHL72XSendPipeline**。  
  
5.  在主控台樹狀目錄中，按一下**篩選**，然後執行下列步驟：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**屬性**|選取**BTS。MessageType**。|  
    |**運算子**|選取 **==** 從下拉式清單。|  
    |**值**|型別**http://microsoft.com/HealthCare/HL7/2X#DSR_Q01_24_GLO_DEF**。|  
    |**Group By**|選取**AND**從下拉式清單。|  
    |**屬性**|在第一個屬性中，按一下空白的方塊，，然後選取**BTAHL7Schemas.MSH5_1**。|  
    |**運算子**|選取 **==** 從下拉式清單。|  
    |**值**|型別**ADT**。|  
  
    > [!NOTE]
    >  第一個篩選條件可讓您指定傳送埠只選取符合 DSR 訊息 ^ Q01 步驟 3A 中建立的結構描述。 第二個篩選指定的目的[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]介面引擎會傳送這些訊息。  
  
6.  按一下 **[確定]**。  
  
7.  在 管理主控台中，按一下 **傳送埠**，以滑鼠右鍵按一下**ADT_Send**，然後按一下 **啟動**。  
  
 若要繼續[步驟 8： 設定合作對象資訊](../../adapters-and-accelerators/accelerator-hl7/step-8-configure-party-information-hl7-main.md)。