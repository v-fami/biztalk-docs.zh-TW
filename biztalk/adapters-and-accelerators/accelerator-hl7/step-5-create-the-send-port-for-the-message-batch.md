---
title: "步驟 5： 建立傳送埠的訊息批次 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5db815df-5b76-4ba4-99ab-c7766b0c301a
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a5749166c8a9b34d5e5a04849c4179ac4427201c
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="step-5-create-the-send-port-for-the-message-batch"></a>步驟 5： 建立傳送埠的訊息批次
在此步驟中，您可以建立傳送埠以將您建立的訊息批次傳遞至目的合作對象。 這是靜態單向連接埠與 FILE 配接器類型。 您指定的目的地 (\Tutorial_BatchMsgDrop) 的檔案資料夾位置[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]將卸除的訊息批次檔。 您定義指出哪種類型的訊息批次傳送連接埠的連接埠的篩選。 篩選器會指定 Tutorial_BatchDest 和 OutboundBatch 的訊息類型的目的地。  
  
> [!NOTE]
>  當執行本教學課程的這個部分，您可以簡化結果停止傳送埠用於本教學課程的第 2 部分： **Tutorial_BTAHL7Drop**傳送埠。  
  
### <a name="to-create-the-send-port-for-the-message-batch"></a>若要建立的訊息批次的傳送埠  
  
1.  在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態單向傳送埠**。  
  
2.  在 [傳送埠屬性] 對話方塊中，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**名稱**|型別**Tutorial_BatchDest**。|  
    |**型別**|選取**檔案**從下拉式清單。|  
    |**設定**|按一下**設定**以開啟 [FILE 傳輸屬性] 對話方塊。|  
  
3.  在**FILE 傳輸屬性**對話方塊方塊中，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**目的地資料夾**|瀏覽至  **\<*磁碟機*:\>\Program Files\Microsoft BizTalk\<版本\>Accelerator for HL7\SDK\End 端對端 Tutorial\Tutorial_BatchMsgDrop * *。 這是在檔案系統或公用共用的位置路徑[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]會寫入含有訊息批次的檔案。|  
    |**檔案名稱**|型別**%MessageID%.txt** （副檔名為.txt 取代.xml 副檔名）。|  
    |**複製模式**|選取**建立新**。|  
  
4.  按一下 **[確定]**。  
  
5.  在 [傳送埠屬性] 對話方塊的**傳送管線**，選取**BTAHL72XPipelines.BTAHL72XSendPipeline**。  
  
6.  在主控台樹狀目錄中，按一下**篩選**，然後執行下列步驟：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**屬性**|按一下下方的欄位**屬性**，然後選取**Microsoft.Solutions.BTAHL7.BatchOrchestration.Party**從下拉式清單。|  
    |**運算子**|保留 **==** 做為運算子。|  
    |**值**|型別**Tutorial_BatchDest**。|  
    |**Group By**|選取**和**從下拉式清單。|  
    |**屬性**|選取**BTAHL7Schemas.BTAHL7MessageType**。|  
    |**運算子**|保留 **==** 做為運算子。|  
    |**值**|型別**OutboundBatch**。|  
  
7.  按 **Enter**鍵。 在對話方塊底部窗格中，確認正確地輸入篩選運算式，然後按一下**確定**。  
  
8.  在 BizTalk 管理主控台中，選取**傳送埠**，以滑鼠右鍵按一下**Tutorial_BatchDest**，然後按一下 **啟動**。  
  
### <a name="to-associate-the-send-port-with-the-destination-party"></a>若要將傳送埠與目的合作對象產生關聯  
  
1.  在 BizTalk Server 管理主控台中，展開**合作對象**，按一下  **Tutorial_BatchDest**，然後以滑鼠右鍵按一下**屬性**。  
  
2.  在 [合作對象屬性] 對話方塊中，按一下**傳送埠**在主控台樹狀目錄中。  選取**Tutorial_BatchDest**從下拉式清單，然後按一下**確定**。  
  
    > [!NOTE]
    >  如果並行存取違規，就會發生時**Tutorial_DestBatch**更新合作對象，按一下**確定**並關閉對話方塊。 在管理主控台中，以滑鼠右鍵按一下**BizTalk 群組**，按一下 **重新整理**，然後重複步驟 1 和 2。  
  
 若要繼續[步驟 6： 建立通知批次的傳送埠](../../adapters-and-accelerators/accelerator-hl7/step-6-create-the-send-port-for-the-acknowledgment-batch.md)。