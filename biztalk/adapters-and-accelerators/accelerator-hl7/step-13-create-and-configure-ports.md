---
title: "步驟 13： 建立和設定連接埠 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ports, creating
- message enrichment tutorial, ports
- creating, ports
- configuring, ports
- ports, configuring
ms.assetid: cc0540d7-46fc-4d9f-bcf3-0b0e0179fd51
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 256b1618313605f0847d9328abfd003f41ac61cd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-13-create-and-configure-ports"></a>步驟 13： 建立和設定連接埠
在此步驟中，您可以使用連接埠組態精靈來建立及設定協調流程設計師中的連接埠。 連接埠指定您的協調流程傳送和接收訊息，並從商務程序的方式。 每個連接埠都有類型、 方向和繫結。 屬性可同時決定通訊的通訊模式、 位置或從中方向[!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]傳送或接收訊息，以及如何的通訊會發生。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]使用最小值較低層通訊協定 (MLLP) 配接器做為傳送埠。 MLLP 配接器介面與其他應用程式，例如實驗室儀器應用程式、 保險的應用程式和繼承的特定業務應用程式使用 TCP 通訊端通訊。 代表 MLLP 傳送配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]配接器：  
  
-   自訂。 配接器只隨附[!INCLUDE[HL7_CurrentVersion_abbrev](../../includes/hl7-currentversion-abbrev-md.md)]，隨附於與[!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]。  
  
-   通訊協定/傳輸。 配接器不是應用程式或資料配接器。  
  
-   靜態。 配接器組態不包括自訂使用者介面。  
  
-   非同步的。 配接器不會封鎖傳訊引擎執行緒，可讓所有介面卡的提升的效能，[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]主機。  
  
-   非交易。 配接器不是交易性的接收或傳送[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]配接器。  
  
-   規則。 配接器不會在個別的應用程式處理序中執行。  
  
-   單向和雙向。 配接器支援單向和要求-回應/請求-回應模式的互動。  
  
 MLLP 配接器可以將個別訊息提交或提交批次中的訊息。 MLLP 訊息的開頭是以包裝函式的字元、 十六進位 0x0b （也就是啟動區塊或 SB 字元），而且訊息結尾是十六進位 0x1c 字元 （也稱為 End 區塊或 EB 字元） 的組合緊接著 0x0d 字元 （歸位字元）。 BTAHL7 效能計數器只會計算傳送訊息的這些包裝函式的字元。 接收訊息時，BTAHL7 效能計數器不計算這些包裝函式的字元。  
  
> [!NOTE]
>  MLLP 通訊協定標準不訊息內容中允許 0x20 下的字元，因為它會干擾偵測 SB 和 EB 字元的功能。 您可以設定 SB 和 EB 字元值，所以要小心此問題進行變更時。  
  
 在此步驟中，您可以設定 MLLP 配接器與 SOAP 配接器。  
  
### <a name="to-create-and-configure-the-ports"></a>建立和設定連接埠  
  
1.  在協調流程設計師 」 中，拖曳**連接埠**圖形從工具箱拖曳至設計檢視介面中，左側連接埠介面，然後將圖形放，讓它與水平對齊**DoorbellReceive**圖形。  
  
2.  在**連接埠組態精靈**，按一下 **下一步**。  
  
3.  在**連接埠內容**頁面上，於**名稱**欄位中，輸入**SOAPReceivePort**，然後按一下 **下一步**。  
  
4.  在**選取連接埠類型**頁面上，輸入下列資訊，然後按**下一步**才能繼續。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**連接埠類型名稱**|型別**SOAPReceivePortType**。|  
    |**通訊模式**|選取**單向**。|  
    |**存取限制**|選取**公用-沒有限制**。|  
  
5.  在**連接埠繫結**頁面上，按一下**下一步**接受預設值。  
  
6.  在**完成連接埠精靈**頁面上，按一下**完成**。  
  
7.  拖曳**連接埠**圖形從工具箱拖曳至 [設計] 檢視介面，右邊的連接埠介面，然後將圖形放，讓它與水平對齊**DoorbellSend**圖形。  
  
8.  使用**連接埠組態精靈**如同在步驟 2 到 7，建立額外的傳送埠，使用下列參數：  
  
    |屬性|參數|  
    |--------------|---------------|  
    |**連接埠的屬性名稱**|MLLPSendPort|  
    |**連接埠類型名稱**|MLLPSendPortType|  
    |**通訊模式**|單向|  
    |**存取限制**|公用 - 沒有限制|  
    |**連接埠繫結**|稍後指定|  
    |**連接埠通訊方向**|我將總是在此連接埠傳送訊息。|  
  
9. 在**協調流程檢視**視窗中，與**類型**，**連接埠類型**，和**SOAPReceivePortType**節點展開，展開  **Operation_1**，然後按一下 **要求**。  
  
10. 在**屬性**視窗中的，在下拉式清單中**訊息類型**，依序展開**結構描述**，然後按一下  **BTAHL7_Project.Doorbell**.  
  
11. 在**協調流程檢視**視窗中，展開  **MLLPSendPortType**，依序展開**Operation_1**，然後按一下**要求**。  
  
12. 在**屬性**視窗中的，在下拉式清單中**訊息類型**，依序展開**多部分訊息類型**，然後按一下  **BTAHL7_Project.DoorbellFinalMessageType**。  
  
13. 在**名稱**欄位中，輸入**回應**，然後按下**Enter**。  
  
14. 協調流程設計檢視介面上，按一下  **DoorbellReceive**動作圖形。  
  
15. 在**屬性**視窗中的，在下拉式清單中**訊息**，選取**DoorbellInputMessage**。  
  
16. 協調流程設計檢視介面上，按一下  **DoorbellSend**圖形。  
  
17. 在**屬性**視窗中的，在下拉式清單中**訊息**，選取**DoorbellFinalMessage**。  
  
18. 按一下中的綠色控點**SOAPReceivePort**並將它拖曳至的綠色控點**DoorbellReceive**接收圖形連接**SOAPReceivePort** 至**DoorbellReceive**接收圖形。  
  
19. 按一下中的綠色控點**DoorbellSend**圖形，並將它拖曳至的綠色控點**MLLPSendPort**連接的連接埠**DoorbellSend** 到傳送圖形**MLLPSendPort**連接埠。  
  
20. 按一下**方案總管 中**在協調流程檢視 索引標籤。  
  
21. 在 方案總管 中，以滑鼠右鍵按一下**BTAHL7V22Common**，然後按一下 **建置**。 請在 [輸出] 視窗中出現的成功訊息。  
  
    > [!NOTE]
    >  如果不成功的訊息出現，請對方案進行疑難排解。  
  
22. 以滑鼠右鍵按一下**BTAHL7 專案**，然後按一下**部署**部署 BTAHL7 專案。  
  
 若要繼續[步驟 14： 發佈為 Web 服務協調流程](../../adapters-and-accelerators/accelerator-hl7/step-14-publish-the-orchestration-as-a-web-service.md)。  
  
## <a name="see-also"></a>另請參閱  
 [訊息擴充教學課程](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)