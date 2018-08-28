---
title: 步驟 6： 建立傳送埠以傳遞通知 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 739b3e60-db56-46e9-a6b1-0acbe0c08f55
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 47e30db70d67cb70ba87cf661e46ca325de1f3cc
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37003615"
---
# <a name="step-6-create-a-send-port-to-deliver-acknowledgments"></a>步驟 6： 建立傳送埠以傳遞通知
在此步驟中，您可以建立連接埠來傳送通知回批次的來源。  

 您建立此連接埠是靜態，如此就只能是 MLLP 配接器相關聯，而且它只會傳送到特定的目的地 （批次的來源）。 在本教學課程中，來源是合作對象 Tutorial_BatchSource 相關聯。 此來源合作對象都包含在個別的訊息和 FHS3 MSH3 和 BHS3 原始批次。  

 您可以建立連接埠具有限制的連接埠來傳送通知，不是資料訊息的篩選。 這些篩選器指定一種 ACK_024_GLO_DEF] 和 [目的地為 Tutorial_BatchSource 之間的訊息。  

 您設定這個傳送埠以接收通知的目的地，與名為的接收埠產生關聯的傳送埠**TwoWayAckReceivePort**。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 安裝程式建立此連接埠，以及隨附的接收位置**TwoWayAckReceiveLocation**。 您設定傳送埠來設定使用此連接埠**請求回應啟用**來**否**並設定**提交接收位置 URI**來**127.0.0.1:65535** （接受通知所需的設定）。 如需詳細資訊，請參閱 <<c0> [ 設定向上傳送連接埠接收 Ack](../../adapters-and-accelerators/accelerator-hl7/setting-up-a-send-port-for-receiving-acks.md)。  

### <a name="to-create-a-send-port-to-deliver-acknowledgments"></a>若要建立傳送埠以傳遞通知  

1. 在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**傳送埠**，指向**新增**，然後按一下**靜態單向傳送埠**。  

2. 在 [傳送埠屬性] 對話方塊中，執行下列動作：  


   |      使用      |                                以進行此動作                                 |
   |--------------------|---------------------------------------------------------------------------|
   |      **名稱**      |                        型別**Tutorial_2wayAck**。                         |
   | **傳輸類型** |                 選取  **MLLP**從下拉式清單。                  |
   |   **設定**    | 按一下 [**設定**來開啟**MLLP 傳輸屬性**] 對話方塊。 |


3. 在 [MLLP 傳輸屬性] 對話方塊中，執行下列動作：  


   |                 使用                  |        以進行此動作         |
   |-------------------------------------------|---------------------------|
   |            **連接名稱**            |     型別**2wayAck**。     |
   |                 **主控件**                  |    型別**localhost**。    |
   |                 **通訊埠**                  |      型別**41002**。      |
   |       **請求回應已啟用**        | 保留做為欄位**No**。 |
   | **提交接收通知的位置 (URI)** | 型別**127.0.0.1:65535**  |


4. 按一下 [確定] 。  

5. 在傳送埠屬性 對話方塊中，如**傳送管線**，選取**BTAHL72XPipelines.BTAHL72XSendPipeline**。  

6. 在主控台樹狀目錄中，按一下**篩選**，然後執行下列操作：  

   > [!NOTE]
   >  請確定您完全依照顯示輸入下列資料。 這項資料會區分大小寫。  

   |          使用          |                                            以進行此動作                                            |
   |----------------------------|--------------------------------------------------------------------------------------------------|
   | **屬性**（第一次換行）  |   按一下下方的欄位**屬性**，然後選取**BTS。MessageType**從下拉式清單。   |
   |        **[運算子]**        |                              選取  **==** 從下拉式清單。                              |
   |         **ReplTest1**          |                型別**<http://microsoft.com/HealthCare/HL7/2X#ACK_24_GLO_DEF>**。                 |
   |        **群組依據**        |                              選取 **或**從下拉式清單。                              |
   | **屬性**（第二行） | 按一下下方的欄位**屬性**，然後選取  **BTS。MessageType**從下拉式清單。 |
   |        **[運算子]**        |                              選取  **==** 從下拉式清單。                              |
   |         **ReplTest1**          |                型別 **<http://microsoft.com/HealthCare/HL7/2X#ACK_25_GLO_DEF>。**                 |
   |        **群組依據**        |                             選取 **和**從下拉式清單。                              |
   | **屬性**（第三行）  |   按一下底下的第二列的欄位**屬性**，然後選取**BTAHL7Schemas.MSH5_1**。   |
   |        **[運算子]**        |                              選取  **==** 從下拉式清單。                              |
   |         **ReplTest1**          |                                  型別**Tutorial_BatchSource**。                                  |

   > [!NOTE]
   >  第一個篩選條件，表示您訂閱的通知訊息。 第二個篩選條件，表示您想要聲明這具有的 「 發行者 」，目的地**Tutorial_BatchSource**。  

7. 按一下 **[輸入]**。 在對話方塊底部窗格中，確認您正確地輸入篩選運算式，然後按一下**確定**。  

8. 在 管理主控台中，按一下**傳送埠**，以滑鼠右鍵按一下**Tutorial_2wayAck**，然後選取**啟動**。  

   > [!NOTE]
   >  Tutorial_2wayAck 傳送埠才能正常，您必須啟用 TwoWayAckReceivePort 接收位置。  

9. 按一下 **接收位置**。 確認已啟用 TwoWayAckReceiveLocation 的狀態。 如果沒有，請以滑鼠右鍵按一下**TwoWayAckReceiveLocation**，然後按一下**啟用**。  

   請繼續進行[步驟 7： 建立和設定來源合作對象](../../adapters-and-accelerators/accelerator-hl7/step-7-create-and-configure-a-source-party.md)。