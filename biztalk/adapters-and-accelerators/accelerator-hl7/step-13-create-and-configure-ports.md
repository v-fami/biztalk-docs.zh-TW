---
title: 步驟 13： 建立和設定連接埠 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ports, creating
- message enrichment tutorial, ports
- creating, ports
- configuring, ports
- ports, configuring
ms.assetid: cc0540d7-46fc-4d9f-bcf3-0b0e0179fd51
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4414795b1c214e8dbe15eb3117527c3cb5227cde
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36991935"
---
# <a name="step-13-create-and-configure-ports"></a>步驟 13： 建立和設定連接埠
在此步驟中，您可以使用連接埠組態精靈來建立及設定連接埠在協調流程設計師。 連接埠指定您的協調流程如何傳送和接收訊息，並從商務程序。 每個連接埠具有類型、 方向和繫結。 屬性一起決定通訊的通訊模式、 位置或從中方向[!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]傳送或接收訊息，以及通訊進行的方式。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 使用最小值較低層通訊協定 (MLLP) 配接器做為傳送埠。 MLLP 配接器會使用 TCP 通訊端通訊來與其他應用程式，例如實驗室應用程式、 保險的應用程式和舊版的特定業務應用程式的介面。 MLLP 傳送配接器表示[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]配接器：  

- 自訂。 配接器只隨附[!INCLUDE[HL7_CurrentVersion_abbrev](../../includes/hl7-currentversion-abbrev-md.md)]，而不是隨附於 BizTalk Server。  

- 通訊協定/傳輸。 配接器不是應用程式或資料配接器。  

- 靜態。 配接器組態不包括自訂使用者介面。  

- 非同步的。 配接器不會封鎖傳訊引擎執行緒，可讓所有介面卡的效能提升，[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]主機。  

- 非交易。 配接器不是交易性的接收或傳送[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]配接器。  

- 規則。 配接器不會在個別的應用程式處理序中執行。  

- 單向和雙向。 配接器支援單向和要求-回應/請求-回應模式的互動。  

  MLLP 配接器可以將個別訊息提交，或提交批次中的訊息。 MLLP 訊息的開頭標記以包裝函式字元十六進位 0x0b （也就是啟動區塊或 SB 字元），和十六進位的 0x1c 字元 （也稱為 End 區塊或 EB 字元） 的組合來標記訊息結尾緊接著 0x0d 字元 （歸位字元）。 BTAHL7 效能計數器只會計算傳送訊息的這些包裝函式的字元。 接收訊息時，BTAHL7 效能計數器不計算這些包裝函式的字元。  

> [!NOTE]
>  MLLP 通訊協定標準不訊息承載中允許下 0x20 的字元，因為它會干擾偵測的 SB 和 EB 字元的能力。 您可以設定 「 SB 」 和 「 EB 的字元值，因此請小心此問題的變更時。  

 在此步驟中，您可以設定的 MLLP 配接器和 SOAP 配接器。  

### <a name="to-create-and-configure-the-ports"></a>建立和設定連接埠  

1. 在協調流程設計師中，拖曳**連接埠**圖形從工具箱拖曳至連接埠介面左邊的 [設計] 檢視介面，然後將圖形，讓它與水平對齊**DoorbellReceive**圖形。  

2. 在 [**連接埠組態精靈**，按一下**下一步]**。  

3. 在上**連接埠屬性**頁面上，於**名稱**欄位中，輸入**SOAPReceivePort**，然後按一下**下一步**。  

4. 在上**選取 連接埠類型**頁面上，輸入下列資訊，然後按一下 **下一步**以繼續。  


   |         使用          |          以進行此動作           |
   |---------------------------|-------------------------------|
   |    **連接埠類型名稱**     | 型別**SOAPReceivePortType**。 |
   | **通訊模式** |      選取 **單向**。      |
   |  **存取限制**  | 選取 **公用-沒有限制**。 |


5. 在 [**連接埠繫結**頁面上，按一下**下一步]** 以接受預設值。  

6. 在 **完成連接埠精靈**頁面上，按一下**完成**。  

7. 拖曳**連接埠**圖形從工具箱拖曳至設計檢視介面時，右側連接埠介面，並將圖形放置，讓它與水平對齊**DoorbellSend**圖形。  

8. 使用**連接埠組態精靈**如同在步驟 2 到 7，建立額外的傳送埠，使用下列參數：  


   |              屬性               |                   參數                   |
   |-------------------------------------|-----------------------------------------------|
   |      **連接埠的屬性名稱**       |                 MLLPSendPort                  |
   |         **連接埠類型名稱**          |               MLLPSendPortType                |
   |      **通訊模式**      |                    單向                    |
   |       **存取限制**       |               公用 - 沒有限制               |
   |          **連接埠繫結**           |                 稍後指定                 |
   | **連接埠通訊方向** | 我將總是在此連接埠傳送訊息。 |


9. 在**協調流程檢視** 視窗中，使用**型別**，**連接埠類型**，和**SOAPReceivePortType**節點展開，展開**Operation_1**，然後按一下**要求**。  

10. 在 **屬性**視窗中的，下拉式清單中**訊息類型**，展開**結構描述**，然後按一下  **BTAHL7_Project.Doorbell**.  

11. 在 **協調流程檢視** 視窗中，展開**MLLPSendPortType**，展開**Operation_1**，然後按一下 **要求**。  

12. 在 **屬性**視窗中的，下拉式清單中**訊息類型**，展開**多部分訊息類型**，然後按一下  **BTAHL7_Project.DoorbellFinalMessageType**。  

13. 在 **名稱**欄位中，輸入**回應**，然後按**Enter**。  

14. 協調流程設計檢視介面上，按一下**DoorbellReceive**動作圖形。  

15. 在 **屬性**視窗中的，下拉式清單中**訊息**，選取**DoorbellInputMessage**。  

16. 協調流程設計檢視介面上，按一下**DoorbellSend**圖形。  

17. 在 **屬性**視窗中的，下拉式清單中**訊息**，選取**DoorbellFinalMessage**。  

18. 按一下中的綠色控**SOAPReceivePort**並將它拖曳至的綠色控點**DoorbellReceive**接收 」 圖形連接**SOAPReceivePort** 至**DoorbellReceive**接收圖形。  

19. 按一下中的綠色控**DoorbellSend**圖形，並將它拖曳至的綠色控點**MLLPSendPort**連接埠**DoorbellSend** 到傳送圖形**MLLPSendPort**連接埠。  

20. 按一下 **方案總管 中**下方協調流程檢視 索引標籤。  

21. 在 [方案總管] 中，以滑鼠右鍵按一下**BTAHL7V22Common**，然後按一下**建置**。 請確定在 [輸出] 視窗中出現的成功訊息。  

    > [!NOTE]
    >  如果沒有成功的訊息出現時，進行疑難排解的解決方案。  

22. 以滑鼠右鍵按一下**BTAHL7 專案**，然後按一下**部署**部署 BTAHL7 專案。  

    請繼續進行[步驟 14： 發佈為 Web 服務協調流程](../../adapters-and-accelerators/accelerator-hl7/step-14-publish-the-orchestration-as-a-web-service.md)。  

## <a name="see-also"></a>另請參閱  
 [訊息擴充教學課程](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)