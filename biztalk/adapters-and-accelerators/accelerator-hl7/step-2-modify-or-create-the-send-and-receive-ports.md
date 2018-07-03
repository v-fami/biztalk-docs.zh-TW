---
title: 步驟 2： 修改或建立傳送和接收埠 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8d96d02c-b75d-4d18-a127-37002c5ff138
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 42c40652d334fd2c7dec2475edca81b9fc9b1b14
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36996519"
---
# <a name="step-2-modify-or-create-the-send-and-receive-ports"></a>步驟 2： 修改或建立傳送和接收埠
FILE 傳送和接收埠以進行批次，您需要在 / 批次出教學課程。 如果您按下**啟動的教學課程**結尾的安裝 Enterprise Edition 的按鈕[!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]為您建立這些連接埠： 名為 Tutorial_BTAHL7Drop，傳送埠和接收埠命名為 Tutorial_BTAHL7PickUp。 如果您有這些連接埠，您仍然需要修改傳送埠 Tutorial_BTAHL7Drop。  

 如果[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]安裝程式建立傳送和接收埠以進行您，請參閱本主題中，「 建立 BIBOTutorialPickup 接收連接埠 」 程序，且然後請參閱 「 建立 BIBOTutorialDrop 傳送連接埠 」 也是本主題中的程序。  

### <a name="to-modify-the-tutorialbtahl7drop-send-port"></a>若要修改 Tutorial_BTAHL7Drop 傳送埠  

1. 按一下 **開始**，指向**所有程式**，指向**Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)]，然後按一下**BizTalk Server 管理**。  

2. 在管理主控台中，依序展開[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**，展開**BizTalk 群組**，依序展開**應用程式**，然後展開**BizTalk 應用程式 1**。  

3. 按一下 **傳送埠**，以滑鼠右鍵按一下**Tutorial_BTAHL7Drop**，然後按一下**屬性**。  

4. 在主控台樹狀目錄中，按一下**篩選器**。  

5. 在 **篩選器**窗格中的，第二個資料列中，選取**BTAHL7Schemas.MessageClass**的**屬性**，選取**==** 的**運算子**，然後輸入**MessageClass2X** for**值**。 按一下 **[輸入]**。  

6. 設定**分組**上**BTS。ReceivePortName**列**或是**，然後按一下**確定**。  

7. 在 Microsoft[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]系統管理 視窗中，展開**平台設定**，然後展開**主控件執行個體**。 以滑鼠右鍵按一下**BizTalkServerApplication**，然後按一下**重新啟動**。  

   > [!NOTE]
   >  只能使用下列程序，如果您已安裝 Standard Edition [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]，或如果您沒有按一下**啟動的教學課程**按鈕，當您設定[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]。  

### <a name="to-create-the-tutorialbtahl7pickup-receive-port-and-location"></a>若要建立 Tutorial_BTAHL7Pickup 接收埠和位置  

1. 按一下 **開始**，指向**所有程式**，指向**Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)]，然後按一下**BizTalk Server 管理**。  

2. 在管理主控台中，依序展開[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**，展開**BizTalk 群組**，依序展開**應用程式**，然後展開**BizTalk 應用程式 1**。  

3. 以滑鼠右鍵按一下**接收連接埠**，指向**新增**，然後按一下**單向接收埠**。  

4. 在接收埠屬性 對話方塊中，在**名稱**方塊中，輸入**Tutorial_BTAHL7PickUp**。  

5. 按一下 **套用**要繫結連接埠，然後按一下**確定**。  

6. 以滑鼠右鍵按一下**接收位置**，指向**新增**，然後按一下**單向接收位置**。  

7. 在 [選取接收埠] 對話方塊中，按一下**Tutorial_BTAHL7PickUp**，然後按一下**確定**。  

8. 在 [接收位置屬性] 對話方塊中，在**名稱**方塊中，輸入**Tutorial_FileReceiveLoc**。  

9. 在**傳輸**區段中，如**型別**文字方塊中，按一下下拉式清單中，然後按**檔案**。  

10. 按一下 **設定**按鈕右邊的 類型 下拉式清單。  

11. 在 [FILE 傳輸屬性] 對話方塊中，執行下列作業：  


    |      使用      |                                                                                                                                                                         以進行此動作                                                                                                                                                                          |
    |--------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | **接收資料夾** | 瀏覽至**\<**<em>磁碟機</em>**\>: \Program Files\Microsoft BizTalk\<版本\>Accelerator for HL7\SDK\End 端對端Tutorial\Tutorial_BTAHL7PickUp**。 **注意︰** 這是在檔案系統或公用的共用位置的路徑從何處[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]會收取檔案。 |
    |   **檔案遮罩**    |                                                                                                                                                                      型別 **\*.txt**。                                                                                                                                                                       |


12. 按一下 [確定] 。  

13. 在 [接收位置屬性] 對話方塊中，執行下列動作：  


    |       使用       |                      以進行此動作                       |
    |----------------------|-------------------------------------------------------|
    | **接收處理常式**  |    保持**BizTalkServerApplication**為選取狀態。     |
    | **接收管線** | 選取  **BTAHL72XPipelines.BTAHL72XReceivePipeline**。 |


14. 按一下 [確定] 。  

15. 在 [BizTalk 總管] 中，以滑鼠右鍵按一下**Tutorial_FileReceiveLoc**，然後按一下**啟用**。  

### <a name="to-create-the-tutorialbtahl7drop-send-port"></a>若要建立 Tutorial_BTAHL7Drop 傳送埠  

1. 在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**傳送埠**，指向**新增**，然後按一下**靜態單向傳送埠**。  

2. 在 [傳送埠屬性] 對話方塊中，執行下列動作：  


   |   使用    |                                以進行此動作                                 |
   |---------------|---------------------------------------------------------------------------|
   |   **名稱**    |                       型別**Tutorial_BTAHL7Drop**。                       |
   |   **型別**    |                 選取 **檔案**從下拉式清單。                  |
   | **設定** | 按一下 [**設定**來開啟**FILE 傳輸屬性**] 對話方塊。 |


3. 在 [FILE 傳輸屬性] 對話方塊中，執行下列作業：  


   |        使用        |                                                                                                                                                                      以進行此動作                                                                                                                                                                       |
   |------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | **目的地資料夾** | 瀏覽至**\<**<em>磁碟機</em>**:\>\Program Files\Microsoft BizTalk\<版本\>Accelerator for HL7\SDK\End 端對端Tutorial\Tutorial_BTAHL7Drop**。 **注意︰** 這是在檔案系統或公開共用的位置路徑[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]會寫入檔案。 |
   |     **檔案名稱**      |                                                                                                                                          型別 **%MessageID%.txt** （請注意，副檔名為 txt，不是 xml）。                                                                                                                                          |


4. 按一下 [確定] 。  

5. 在傳送埠屬性 對話方塊中，如**傳送管線**，選取**BTAHL72XPipelines.BTAHL72XSendPipeline**從下拉式清單。  

6. 在主控台樹狀目錄中，按一下**篩選**，然後執行下列操作：  


   |   使用   |                       以進行此動作                        |
   |--------------|---------------------------------------------------------|
   | **屬性** | 選取**BTS。ReceivePortName**從下拉式清單。 |
   | **[運算子]** |              離開**==** 做為運算子。              |
   |  **ReplTest1**   |             型別**Tutorial_BTAHL7PickUp**。             |
   | **群組依據** |         選取 **或**從下拉式清單。          |
   | **屬性** |         選取  **BTAHL7Schemas.MessageClass**。          |
   | **[運算子]** |              離開**==** 做為運算子。              |
   |  **ReplTest1**   |                型別**MessageClass2X**。                 |


7. 按一下 **[輸入]**。 確認在對話方塊底部窗格中的篩選條件運算式正確。  

8. 按一下 [確定] 。  

9. 在管理主控台中，按一下**傳送埠**，以滑鼠右鍵按一下**Tutorial_BTAHL7Drop**，然後按一下**啟動**。  

10. 依序展開**平台設定**，然後按一下**主控件執行個體**。 以滑鼠右鍵按一下**BizTalkServerApplication**，然後按一下**重新啟動**。  

    請繼續進行[步驟 3： 測試中的批次 / 批次出案例](../../adapters-and-accelerators/accelerator-hl7/step-3-test-the-batch-in-batch-out-scenario.md)。