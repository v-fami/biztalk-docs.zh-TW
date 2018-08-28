---
title: 步驟 5： 建立傳送埠，以便將通知傳送到 ADT 系統，請使用 File 配接器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- end-to-end tutorial, send ports
- send ports, acknowledgements
- creating, send ports
- acknowledgements, send ports
- send ports, creating
ms.assetid: 565a2adf-fd86-46e3-8035-7e4748aefffc
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1421b39ed4bbd15fb82cb16ed55b23e5781eead6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37002095"
---
# <a name="step-5-create-a-send-port-to-deliver-acknowledgments-to-the-adt-system-using-the-file-adapter"></a>步驟 5： 建立傳送埠，以便將通知傳送到 ADT 系統，請使用 File 配接器
在此步驟中，您可以建立傳送埠，以產生使用 File 配接器的通知。  

### <a name="to-create-the-tutorialsendackadt-send-port"></a>若要建立 Tutorial_sendAck_ADT 傳送埠  

1. 使用[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]總管 中，建立\<*磁碟機*:\>\Program Files\Microsoft BizTalk\<版本\>Accelerator for HL7\SDK\End 端對端 Tutorial\Tutorial_sendAck_ADT 資料夾中。  

2. 在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**傳送埠**，指向**新增**，然後按一下**靜態單向傳送埠**。  

3. 在 [傳送埠屬性] 對話方塊中，執行下列動作：  


   |      使用      |                                以進行此動作                                 |
   |--------------------|---------------------------------------------------------------------------|
   |      **名稱**      |                      型別**Tutorial_sendAck_ADT**。                       |
   | **傳輸類型** |                 選取 **檔案**從下拉式清單。                  |
   |   **設定**    | 按一下 [**設定**來開啟**File 傳輸屬性**] 對話方塊。 |


4. 在檔案傳輸屬性 對話方塊中，執行下列動作，然後按一下**確定**。  


   |        使用        |                                                                     以進行此動作                                                                      |
   |------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------|
   | **目的地資料夾** | 瀏覽至**\<**<em>磁碟機</em>**:\>\Program Files\Microsoft BizTalk\<版本\>Accelerator for HL7\SDK\End 端對端Tutorial\Tutorial_sendAck_ADT**。 |
   |     **檔案名稱**      |                                   型別 **%MessageID%.txt** （取代副檔名為.txt 的副檔名為.xml）。                                    |


5. 在傳送埠屬性 對話方塊中，如**傳送管線**，選取**BTAHL72XPipelines.BTAHL72XSendPipeline**。  

6. 在左窗格中，按一下**篩選**，然後執行下列操作：  

   > [!NOTE]
   >  第一個篩選條件，表示您要訂閱的通知訊息。 第二個篩選條件，表示您的目的地的 「 發行者 」 端 Tutorial_ADTSystem 通知訂閱。  

    按一下 **確定**時準備好繼續進行。  


   |          使用          |                                            以進行此動作                                            |
   |----------------------------|--------------------------------------------------------------------------------------------------|
   |        **屬性**        | 按一下下方的欄位**屬性**，然後選取  **BTS。MessageType**從下拉式清單。 |
   |        **[運算子]**        |                              選取  **==** 從下拉式清單。                              |
   |         **ReplTest1**          |                型別**<http://microsoft.com/HealthCare/HL7/2X#ACK_24_GLO_DEF>**。                 |
   |        **群組依據**        |                              選取 **或**從下拉式清單。                              |
   | **屬性 （第二行）** | 按一下下方的欄位**屬性**，然後選取  **BTS。MessageType**從下拉式清單。 |
   |        **[運算子]**        |                              選取  **==** 從下拉式清單。                              |
   |         **ReplTest1**          |                型別 **<http://microsoft.com/HealthCare/HL7/2X#ACK_25_GLO_DEF>。**                 |
   |        **群組依據**        |                             選取  **AND**從下拉式清單。                              |
   |        **屬性**        |     在第一個屬性中，按一下空白的方塊，，然後按**BTAHL7Schemas.MSH5_1**。     |
   |        **[運算子]**        |                              選取  **==** 從下拉式清單。                              |
   |         **ReplTest1**          |                                   型別**Tutorial_ADTSystem**。                                   |

   > [!NOTE]
   >  Tutorial_sendAck_ADT 傳送埠，BTAHL7 會卸除通知在檔案放置位置\<*磁碟機*\>: Program Filessystem BizTalk <version> Accelerator for HL7SDKEnd 端對端TutorialTutorial_sendAck_ADT。  

7. 按一下 **套用**，然後按一下  **確定。**  

8. 在管理主控台中，按一下**傳送埠**，以滑鼠右鍵按一下**Tutorial_sendAck_ADT**，然後按一下**啟動**。  

   請繼續進行[步驟 6： 建立傳送埠以傳遞 ^ 給 RX 系統使用 File 配接器將 adt^a03 訊息](../../adapters-and-accelerators/accelerator-hl7/step-6-create-send-port-to-deliver-adt^a03-message-to-rx-system-using-file.md)。