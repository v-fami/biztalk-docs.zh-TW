---
title: 步驟 5： 建立傳送埠的訊息批次 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5db815df-5b76-4ba4-99ab-c7766b0c301a
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 24a71d788d0b12a3ffaef8f14ccd145ef61d673e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37002839"
---
# <a name="step-5-create-the-send-port-for-the-message-batch"></a>步驟 5： 建立訊息批次的傳送埠
在此步驟中，您可以建立傳送埠以將您所建立的訊息批次傳遞到目的合作對象。 這是靜態的單向連接埠與 FILE 配接器類型。 將檔案，其中會指定檔案資料夾的目的地 (\Tutorial_BatchMsgDrop)[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]會卸除的訊息批次檔。 您定義表示何種類型的訊息批次會傳送連接埠的連接埠的篩選條件。 篩選條件指定 Tutorial_BatchDest 和 OutboundBatch 的訊息類型的目的地。  

> [!NOTE]
>  當執行本教學課程的這個部分，您可以藉由停止傳送埠，在本教學課程第 2 部分中使用簡化結果： **Tutorial_BTAHL7Drop**傳送埠。  

### <a name="to-create-the-send-port-for-the-message-batch"></a>若要建立訊息批次的傳送埠  

1. 在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**傳送埠**，指向**新增**，然後按一下**靜態單向傳送埠**。  

2. 在 [傳送埠屬性] 對話方塊中，執行下列動作：  


   |   使用    |                              以進行此動作                               |
   |---------------|-----------------------------------------------------------------------|
   |   **名稱**    |                     型別**Tutorial_BatchDest**。                      |
   |   **型別**    |               選取 **檔案**從下拉式清單。                |
   | **設定** | 按一下 **設定**以開啟 FILE 傳輸屬性 對話方塊。 |


3. 在  **FILE 傳輸屬性**對話方塊方塊中，執行下列動作：  


   |        使用        |                                                                                                                                                                           以進行此動作                                                                                                                                                                            |
   |------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | **目的地資料夾** | 瀏覽至 **\<*磁碟機*:\>\Program Files\Microsoft BizTalk\<版本\>Accelerator for HL7\SDK\End 端對端 Tutorial\Tutorial_BatchMsgDrop**. 這是在檔案系統或公開共用的位置路徑[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]會寫入該檔案包含的訊息批次。 |
   |     **檔案名稱**      |                                                                                                                                         型別 **%MessageID%.txt** （取代副檔名為.txt 的副檔名為.xml）。                                                                                                                                          |
   |     **複製模式**      |                                                                                                                                                                     選取 **新建**。                                                                                                                                                                      |


4. 按一下 [確定] 。  

5. 在傳送埠屬性 對話方塊中，如**傳送管線**，選取**BTAHL72XPipelines.BTAHL72XSendPipeline**。  

6. 在主控台樹狀目錄中，按一下**篩選**，然後執行下列操作：  


   |   使用   |                                                              以進行此動作                                                              |
   |--------------|--------------------------------------------------------------------------------------------------------------------------------------|
   | **屬性** | 按一下下方的欄位**屬性**，然後選取**Microsoft.Solutions.BTAHL7.BatchOrchestration.Party**從下拉式清單。 |
   | **[運算子]** |                                                    離開**==** 做為運算子。                                                     |
   |  **ReplTest1**   |                                                     型別**Tutorial_BatchDest**。                                                     |
   | **群組依據** |                                               選取 **和**從下拉式清單。                                                |
   | **屬性** |                                             選取  **BTAHL7Schemas.BTAHL7MessageType**。                                              |
   | **[運算子]** |                                                    離開**==** 做為運算子。                                                     |
   |  **ReplTest1**   |                                                       型別**OutboundBatch**。                                                        |


7. 按 **Enter**鍵。 在對話方塊底部窗格中，確認您正確地輸入篩選運算式，然後按一下**確定**。  

8. 在 BizTalk 管理主控台中，選取**傳送埠**，以滑鼠右鍵按一下**Tutorial_BatchDest**，然後按一下**啟動**。  

### <a name="to-associate-the-send-port-with-the-destination-party"></a>目的合作對象相關聯的傳送埠  

1. 在 BizTalk Server 管理主控台中，展開**合作對象**，按一下**Tutorial_BatchDest**，然後以滑鼠右鍵按一下**屬性**。  

2. 在 [合作對象屬性] 對話方塊中，按一下**傳送埠**在主控台樹狀目錄中。  選取  **Tutorial_BatchDest**從下拉式清單中，然後按一下**確定**。  

   > [!NOTE]
   >  如果發生並行存取違規時**Tutorial_DestBatch**正在更新合作對象，按一下 **確定**並關閉對話方塊。 在管理主控台中，以滑鼠右鍵按一下**BizTalk 群組**，按一下**重新整理**，然後重複步驟 1 和 2。  

   請繼續進行[步驟 6： 建立通知批次的傳送埠](../../adapters-and-accelerators/accelerator-hl7/step-6-create-the-send-port-for-the-acknowledgment-batch.md)。