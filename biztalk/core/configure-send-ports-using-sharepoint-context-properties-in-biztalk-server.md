---
title: 如何設定傳送埠使用 Windows Sharepoint Services 內容屬性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Windows SharePoint Services adapters, InfoPath forms
- configuring [Windows SharePoint Services adapters], InfoPath forms
- Windows SharePoint Services adapters, Windows SharePoint Services
- InfoPath forms, Windows SharePoint Services adapters
- configuring [Windows SharePoint Services adapters], Windows SharePoint Services
- Windows SharePoint Services adapters, send ports
- configuring [Windows SharePoint Services adapters], send ports
- send ports, Windows SharePoint Services adapters
- Windows SharePoint Services, Windows SharePoint Services adapters
ms.assetid: 1ff50fb8-7ba0-47b8-9476-d57413989346
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e766272f33bf23166ba412a76498e4240ab3343b
ms.sourcegitcommit: 36350889f318e1f7e0ac9506dc8df794d475bda6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="how-to-configure-send-ports-using-windows-sharepoint-services-context-properties"></a>如何使用 Windows Sharepoint Services 內容屬性設定傳送埠
本主題說明如何在執行階段從 BizTalk 協調流程使用 Windows Sharepoint Services 內容屬性設定 Windows SharePoint Services 傳送埠。 相同的機制可以用來設定 Windows SharePoint Services 動態和晚期繫結傳送埠。 動態傳送埠的組態屬性需於執行階段時在協調流程中設定。 配接器屬性中公開的 **Windows SharePoint Services 傳輸屬性** 對話方塊也可以套用至動態或晚期繫結的傳送埠。 若要使用 Windows Sharepoint Services 配接器內容屬性設定動態或晚期繫結傳送埠的組態屬性，請依照下列步驟執行：  
  
### <a name="to-set-configuration-properties-for-a-send-port-using-windows-sharepoint-services-adapter-context-properties"></a>若要使用 Windows Sharepoint Services 配接器內容屬性設定傳送埠的組態屬性  
  
1.  針對動態傳送埠，若要建立動態單向傳送埠，請依照下列主題中的步驟[如何建立傳送埠](../core/how-to-create-a-send-port2.md)。  
  
2.  使用 **訊息指派** 圖形內 **建構訊息** 協調流程設定外寄訊息的組態屬性。 如需如何設定輸出訊息的組態屬性的範例，請參閱[逐步解說： 模組 3-從協調流程存取 SharePoint 屬性](../core/walkthrough-module-3-accessing-sharepoint-properties-from-an-orchestration.md)。 **建構新訊息** 本主題的章節將說明如何設定傳出訊息的組態屬性。 可以在中設定之屬性相互關聯的配接器內容屬性 **Windows SharePoint Services 傳輸屬性**  對話方塊會列在下表中︰  
  
    |傳輸屬性|配接器內容屬性|資料類型|註解|  
    |------------------------|------------------------------|---------------|--------------|  
    |配接器 Web 服務連接埠|WSS.ConfigAdapterWSPort|整數|有效值從 1 到 65535 之間<br /><br /> 預設值為 80|  
    |逾時|WSS.ConfigTimeout|整數|有效值介於 1000年到 2147483647<br /><br /> 預設值為 100000<br /><br /> 指定 0 值表示無限的逾時。|  
    |目的資料夾 URL|NA|NA|動態通訊埠，這個設定是間接設定 **Microsoft.XLANGs.BaseTypes.Address** 動態連接埠與協調流程中的 「 運算式 」 圖形的屬性。 晚期繫結連接埠的這個屬性不能在執行階段設定，因為實體傳送埠的值一定會覆寫它。|  
    |檔名|WSS.Filename|字串|除了傳輸屬性中支援所有可用的檔名巨集使用 **%filename%** 和 **%extension%** 巨集。|  
    |命名空間別名|WSS.ConfigNamespaceAliases|字串|如果執行階段中為訊息設定的命名空間別名與訊息傳送目標的傳送埠設定的命名空間別名完全相符，則會合併命名空間，而且會發生傳送錯誤。 為了避免發生這個問題，請務必指定不同的命名空間別名。 例如，如果在協調流程中使用下列運算式設定訊息的命名空間別名：<br /><br /> `Message_Task(WSS.ConfigNamespaceAliases)= "orchns='http://OrderProcess.PurchaseOrder'";`<br /><br /> 如果此訊息路由至傳送埠，指定下列值 **命名空間別名** 屬性︰<br /><br /> orchns ='http://OrderProcess.PurchaseOrder'<br /><br /> 則當 BizTalk Server 嘗試將訊息傳送到這個傳送埠時，就會發生錯誤。 若要解決此問題，您可以指定下列值 **命名空間別名** 的傳送埠屬性︰<br /><br /> **orchns2**='http://OrderProcess.PurchaseOrder'|  
    |Overwrite|WSS.ConfigOverwrite|字串|有效值為：<br /><br /> -[是]。<br /><br /> -[否]<br /><br /> -[重新命名]|  
    |SharePoint 網站 URL|WSS.InListUrl|字串|動態通訊埠，這個設定是間接設定 **Microsoft.XLANGs.BaseTypes.Address** 動態連接埠與協調流程中的 「 運算式 」 圖形的屬性。 晚期繫結連接埠的這個屬性不能在執行階段設定，因為實體傳送埠的值一定會覆寫它。|  
    |Microsoft Office 整合|WSS.ConfigOfficeIntegration|字串|有效值為：<br /><br /> -[是]。<br /><br /> -[否]<br /><br /> -「 yesformlibrary 」<br /><br /> -"optional"|  
    |範本文件庫|WSS.ConfigTemplatesDocLib|字串|無|  
    |範本後援文件庫|WSS.ConfigCustomTemplatesDocLib|字串|無|  
    |範本後援命名空間資料行|WSS.ConfigCustomTemplatesNamespaceCol|字串|無|  
    |範本命名空間資料行|WSS.ConfigTemplatesNamespaceCol|字串|無|  
    |資料行 `n`|WSS.ConfigPropertiesXml<br /><br /> 設定資料行名稱\<PropertyName*x*\>*columnname*\</ PropertyName*x* \>欄位。|字串|無|  
    |資料行 `n` 值|WSS.ConfigPropertiesXml<br /><br /> 資料行值是否以設定\<PropertySource*x*\>*columnvalue*\</ PropertySource*x* \>欄位。|字串|除了傳輸屬性中支援所有可用的檔名巨集使用 **%filename%** 和 **%extension%** 巨集。|  
  
    > [!NOTE]
    >  提供給內容屬性的值需區分大小寫。 使用內容屬性設定動態連接埠的值時，請務必您使用適當的大小寫，否則當 BizTalk 嘗試將文件傳送到指定的傳送埠時，將會發生錯誤。  
  
3.  使用 「 運算式 」 圖形的協調流程中設定 **Microsoft.XLANGs.BaseTypes.Address** 屬性動態傳送埠。 這個屬性可用來指定動態傳送埠傳送訊息的目標 URI。 如需如何設定的範例**Microsoft.XLANGs.BaseTypes.Address**動態傳送埠屬性查看**建立運算式**主題的章節[逐步解說： 模組 3-從協調流程存取 SharePoint 屬性](../core/walkthrough-module-3-accessing-sharepoint-properties-from-an-orchestration.md)。 如需 Windows Sharepoint Services 配接器內容屬性的詳細資訊，請參閱[Windows SharePoint Services 配接器屬性參考](../core/windows-sharepoint-services-adapter-properties-reference.md)。  
  
     您也可以在協調流程中動態設定晚期繫結 Windows Sharepoint Services 傳送埠的某些屬性。 如果完成這項設定，Windows SharePoint Services 連接埠會設定兩次，一次是透過 Windows SharePoint Services 內容屬性，另一次則是透過 [Windows SharePoint Services 傳輸屬性] 對話方塊設定。 根據預設，在 [Windows SharePoint Services 傳輸屬性] 對話方塊中指定之組態的優先順序高於內容屬性中指定的組態屬性。 為了使用內容屬性中指定的組態，請依照下列步驟執行：  
  
    1.  若要建立靜態單向傳送埠，請遵循本主題中的步驟[如何建立傳送埠](../core/how-to-create-a-send-port2.md)。  
  
    2.  設定傳送埠屬性時，請輸入適當的值定義之傳送埠的 URI **Sharepoint 網站 URL** 和 **目的資料夾 URL** 屬性。  
  
    3.  設定的值 **覆寫** 屬性 **協調流程** 想要使用的內容屬性所定義的值 **WSS。ConfigOverwrite** 協調流程中。  
  
    4.  設定 **Microsoft Office 整合** 屬性 **協調流程** 想要使用的內容屬性所定義的值 **WSS。ConfigOfficeIntegration** 協調流程中。  
  
    5.  輸入值為 **-1** 的任何傳送埠屬性使用整數資料類型，如果您想要在協調流程中設定這些內容屬性的值。  
  
    6.  如果您要使用協調流程中的內容屬性來設定使用字串資料型別之任何傳送埠屬性的值，請將這些屬性保留空白。 這不適用於 **Sharepoint 網站 URL** 和 **目的資料夾 URL** 屬性。 這些屬性必須指定 **Windows Sharepoint Services 傳輸屬性** 對話方塊。  
  
    7.  使用 **訊息指派** 圖形內 **建構訊息** 協調流程設定外寄訊息的組態屬性。 如需如何設定輸出訊息的組態屬性的範例，請參閱[逐步解說： 模組 3-從協調流程存取 SharePoint 屬性](../core/walkthrough-module-3-accessing-sharepoint-properties-from-an-orchestration.md)。 **建構新訊息** 本主題的章節將說明如何設定傳出訊息的組態屬性。  
  
    8.  設定值為 -1 (使用整數資料型別的屬性)、[協調流程] (下拉式列舉型別屬性) 或保留空白 (使用字串資料型別的屬性) 的任何傳送埠屬性都將在執行階段由協調流程中指定的內容屬性進行設定。  
  
 如果您使用 Windows SharePoint Services 配接器來接收具有內嵌附件的 InfoPath 表單，然後再將 InfoPath 表單傳送到 SharePoint 文件庫，請完成下列步驟，以保留表單中的任何 InfoPath 處理指示：  
  
### <a name="to-preserve-infopath-processing-instructions-for-infopath-forms-with-embedded-attachments-processed-by-biztalk-server"></a>若要為具有 BizTalk Server 所處理之內嵌附件的 InfoPath 表單保留 InfoPath 處理指示  
  
1.  如果您使用協調流程中的對應，對應至另一個 InfoPath 表單的 InfoPath 表單資料，請確定您已設定 **複製處理指示 (Pi)** 屬性對應至 **是**。 此參數設定下 **自訂標頭** 區段 **格線屬性** 對應的頁面。  
  
2.  如果您不要使用協調流程中的對應，請使用訊息指派圖形中的下列運算式來更新輸出訊息：  
  
    ```  
    NewMessage(XMLNORM.ProcessingInstructionOption) = 1;  
    NewMessage(XMLNORM.ProcessingInstruction) = "<?mso-infoPath-file-attachment-present?>"  
    ```  
  
     上述運算式中 *NewMessage* 是您要新增處理指示的輸出訊息。  
  
## <a name="see-also"></a>另請參閱  
 [如何建立傳送埠](../core/how-to-create-a-send-port2.md)