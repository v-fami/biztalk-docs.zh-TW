---
title: "步驟 6： 建立傳送埠認可批次 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2a0f1ee-e060-4fb9-923e-ebe8168777d9
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 958746634776e9b01c32ff2425122312bc7a841c
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="step-6-create-the-send-port-for-the-acknowledgment-batch"></a>步驟 6： 建立通知批次的傳送埠
在此步驟中，您可以建立傳送埠以將您建立的認可批次傳送到來源合作對象。 這是靜態單向連接埠與 FILE 配接器類型。 您指定檔案資料夾的來源 (\Tutorial_BatchACKDrop)，其中[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]將卸除認可批次檔。 您定義指出哪種類型的通知批次傳送連接埠的連接埠的篩選。 篩選器會指定來源 Tutorial_BatchSource 和 OutboundBatch 的訊息類型。  
  
### <a name="to-create-the-send-port-for-the-acknowledgment-batch"></a>若要建立通知批次的傳送埠  
  
1.  在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態單向傳送埠**。  
  
2.  在 [傳送埠屬性] 對話方塊中，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**名稱**|型別**Tutorial_BatchSource**。|  
    |**型別**|選取**檔案**從下拉式清單。|  
    |**設定**|按一下**設定**以開啟 [FILE 傳輸屬性] 對話方塊。|  
  
3.  在 [FILE 傳輸屬性] 對話方塊中，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**目的地資料夾**|瀏覽至 **\<*磁碟機*:\>\Program Files\Microsoft BizTalk\<版本\>Accelerator for HL7\SDK\End 端對端 Tutorial\Tutorial_BatchACKDrop**. 這是在檔案系統或公用共用的位置路徑[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]將撰寫包含認可批次的檔案。|  
    |**檔案名稱**|型別**%MessageID%.txt** （副檔名為.txt 取代.xml 副檔名）。|  
    |**複製模式**|選取**建立新**。|  
  
4.  按一下 **[確定]**。  
  
5.  在 [傳送埠屬性] 對話方塊的**傳送管線**，選取**BTAHL72XPipelines.BTAHL72XSendPipeline**。  
  
6.  在主控台樹狀目錄中，按一下  **篩選**, ，然後執行下列一項︰  
  
    |使用|動作|  
    |--------------|----------------|  
    |**屬性**|按一下下方的欄位**屬性**，然後選取**Microsoft.Solutions.BTAHL7.BatchOrchestration.Party**從下拉式清單。|  
    |**運算子**|保留 **==** 做為運算子。|  
    |**值**|型別**Tutorial_BatchSource**。|  
    |**分組方式**|選取**和**從下拉式清單。|  
    |**屬性**|選取**BTAHL7Schemas.BTAHL7MessageType**。|  
    |**運算子**|保留 **==** 做為運算子。|  
    |**值**|型別**OutboundBatch**。|  
  
7.  按 **Enter**鍵。 在對話方塊底部窗格中，確認正確地輸入篩選運算式，然後按一下**確定**。  
  
8.  在 BizTalk 管理主控台中，選取**傳送埠**，以滑鼠右鍵按一下**Tutorial_BatchSource**，然後按一下 **啟動**。  
  
### <a name="to-associate-the-send-port-with-the-source-party"></a>要與來源合作對象產生關聯的傳送埠  
  
1.  在 BizTalk 管理主控台中，按一下 **合作對象**。 以滑鼠右鍵按一下**Tutorial_BatchSource**，然後按一下 **屬性**。  
  
2.  在 [合作對象屬性] 對話方塊中，按一下**傳送埠**在主控台樹狀目錄中。 如**傳送埠**，選取**Tutorial_BatchSource**從下拉式清單，然後按一下**確定**。  
  
 若要繼續[步驟 7： 啟動協調流程，然後重新啟動 BizTalk Server](../../adapters-and-accelerators/accelerator-hl7/step-7-start-the-orchestration-and-restart-biztalk-server.md)。