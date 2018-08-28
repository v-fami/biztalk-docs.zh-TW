---
title: 步驟 6： 建立通知批次的傳送埠 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2a0f1ee-e060-4fb9-923e-ebe8168777d9
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3f38b8c7f8e2f486e4de6feca12bf69551221428
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37004999"
---
# <a name="step-6-create-the-send-port-for-the-acknowledgment-batch"></a>步驟 6： 建立通知批次的傳送埠
在此步驟中，您可以建立要將您建立通知批次傳送到來源合作對象的傳送埠。 這是靜態的單向連接埠與 FILE 配接器類型。 您指定檔案資料夾的來源 (\Tutorial_BatchACKDrop)，其中[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]會卸除的通知批次檔。 您定義表示何種類型的通知批次會傳送連接埠的連接埠的篩選條件。 篩選會指定來源 Tutorial_BatchSource 和 OutboundBatch 的訊息類型。  

### <a name="to-create-the-send-port-for-the-acknowledgment-batch"></a>若要建立通知批次的傳送埠  

1. 在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**傳送埠**，指向**新增**，然後按一下**靜態單向傳送埠**。  

2. 在 [傳送埠屬性] 對話方塊中，執行下列動作：  


   |   使用    |                              以進行此動作                               |
   |---------------|-----------------------------------------------------------------------|
   |   **名稱**    |                    型別**Tutorial_BatchSource**。                     |
   |   **型別**    |               選取 **檔案**從下拉式清單。                |
   | **設定** | 按一下 **設定**以開啟 FILE 傳輸屬性 對話方塊。 |


3. 在 [FILE 傳輸屬性] 對話方塊中，執行下列作業：  


   |        使用        |                                                                                                                                                                              以進行此動作                                                                                                                                                                               |
   |------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | **目的地資料夾** | 瀏覽至 **\<*磁碟機*:\>\Program Files\Microsoft BizTalk\<版本\>Accelerator for HL7\SDK\End 端對端 Tutorial\Tutorial_BatchACKDrop**. 這是在檔案系統或公開共用的位置路徑[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]會寫入包含通知批次的檔案。 |
   |     **檔案名稱**      |                                                                                                                                            型別 **%MessageID%.txt** （取代副檔名為.txt 的副檔名為.xml）。                                                                                                                                             |
   |     **複製模式**      |                                                                                                                                                                        選取 **新建**。                                                                                                                                                                         |


4. 按一下 [確定] 。  

5. 在傳送埠屬性 對話方塊中，如**傳送管線**，選取**BTAHL72XPipelines.BTAHL72XSendPipeline**。  

6. 在主控台樹狀目錄中，按一下**篩選**，然後執行下列操作：  


   |   使用   |                                                              以進行此動作                                                              |
   |--------------|--------------------------------------------------------------------------------------------------------------------------------------|
   | **屬性** | 按一下下方的欄位**屬性**，然後選取**Microsoft.Solutions.BTAHL7.BatchOrchestration.Party**從下拉式清單。 |
   | **[運算子]** |                                                    離開**==** 做為運算子。                                                     |
   |  **ReplTest1**   |                                                    型別**Tutorial_BatchSource**。                                                    |
   | **群組依據** |                                               選取 **和**從下拉式清單。                                                |
   | **屬性** |                                             選取  **BTAHL7Schemas.BTAHL7MessageType**。                                              |
   | **[運算子]** |                                                    離開**==** 做為運算子。                                                     |
   |  **ReplTest1**   |                                                       型別**OutboundBatch**。                                                        |


7. 按 **Enter**鍵。 在對話方塊底部窗格中，確認您正確地輸入篩選運算式，然後按一下**確定**。  

8. 在 BizTalk 管理主控台中，選取**傳送埠**，以滑鼠右鍵按一下**Tutorial_BatchSource**，然後按一下**啟動**。  

### <a name="to-associate-the-send-port-with-the-source-party"></a>將關聯的來源合作對象的傳送埠  

1. 在 BizTalk 管理主控台中，按一下**合作對象**。 以滑鼠右鍵按一下**Tutorial_BatchSource**，然後按一下**屬性**。  

2. 在 [合作對象屬性] 對話方塊中，按一下**傳送埠**在主控台樹狀目錄中。 針對**傳送埠**，選取**Tutorial_BatchSource**從下拉式清單中，然後按一下**確定**。  

   請繼續進行[步驟 7： 啟動協調流程，然後重新啟動 BizTalk Server](../../adapters-and-accelerators/accelerator-hl7/step-7-start-the-orchestration-and-restart-biztalk-server.md)。