---
title: 步驟 12： 設定協調流程圖形 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- configuring, orchestration shapes
- orchestrations, shapes
- message enrichment tutorial, orchestrations
ms.assetid: 9388254b-2841-4489-838e-de913ceff151
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d269fa177e7c0da857fb903cef5013f434554d17
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36991471"
---
# <a name="step-12-configure-orchestration-shapes"></a>步驟 12： 設定協調流程圖形
在此步驟中中,，您可以完成協調流程圖形的組態以移除組態不完整智慧標籤。 您指定**DoorbellOutputMessage**做為輸出的第一個轉換處理序中，指定**DoorbellMap.btm**當做該程序中使用的對應。 然後指定**DoorbellFinalMessage**做為第二個輸出轉換程序，並新增額外的欄位資料將訊息擴充的運算式。  
  
 **必要條件：** [知識庫文章 941261](http://support.microsoft.com/kb/941261)必須協調流程組態設定之前套用。  
  
### <a name="to-configure-orchestration-shapes"></a>若要設定協調流程圖形  
  
1. 在 Visual Studio 的協調流程設計檢視介面，按一下  **constructmessage_1**圖形。  
  
2. 在 [**屬性**] 視窗中，按一下**建構的訊息**屬性中，選取**DoorbellOutputMessage**從下拉式清單中，然後按下**輸入**。  
  
3. 協調流程設計檢視介面上，按一下**DoorbellTransform**圖形內 **[constructmessage_1]** 圖形。 在 [**屬性**] 視窗中，按一下**對應名稱**，，然後按一下省略符號 （...） 按鈕，在 [屬性] 欄位。  
  
4. 在 [轉換組態] 對話方塊中，選取**現有的對應**。 在 **完整格式對應名稱**下拉式清單中，按一下**BTAHL7_Project.DoorbellMap**。  
  
5. 按一下 **來源**的左窗格中。  
  
6. 按一下下方的空白方塊**變數名稱**然後按一下**DoorBellInputMessage**從下拉式清單。  
  
7. 按一下 **目的地**的左窗格中。  
  
8. 按一下下方的空白方塊**變數名稱**然後按一下**DoorbellOutputMessage**從下拉式清單。  
  
9. 按一下 **確定**以儲存變更。  
  
10. 協調流程設計檢視介面上，按一下**ConstructMessage_2**圖形。  
  
11. 在 [**屬性**] 視窗中，按一下**建構的訊息**，選取**DoorbellFinalMessage**從下拉式清單中，然後按下**Enter**.  
  
12. 協調流程設計檢視介面上，按一下**DoorbellFinalTransform**圖形內**ConstructMessage_2**圖形。 在 **屬性** 視窗中，按一下**運算式**，然後按一下省略符號 （...） 按鈕，以開啟 BizTalk 運算式編輯器。  
  
13. 在 BizTalk 運算式編輯器 中，按一下 文字欄位中，並貼上下列文字：  
  
    ```  
    HeaderInfo = new System.Xml.XmlDocument();   
    HeaderInfo.LoadXml("<ns0:MSH_25_GLO_DEF xmlns:ns0=\"http://microsoft.com/HealthCare/HL7/2X\">  
        <MSH><MSH.2_EncodingCharacters>^~\\&</MSH.2_EncodingCharacters><MSH.3_SendingApplication>  
        <HD.0_NamespaceId>SrcApp</HD.0_NamespaceId><HD.1_UniversalId>SrcAppUid</HD.1_UniversalId>  
        </MSH.3_SendingApplication><MSH.4_SendingFacility><HD.0_NamespaceId>srcFac</HD.0_NamespaceId>  
        <HD.1_UniversalId>srcFacUid</HD.1_UniversalId></MSH.4_SendingFacility><MSH.5_ReceivingApplication>  
        <HD.0_NamespaceId>dstApp</HD.0_NamespaceId><HD.1_UniversalId>dstAppUid</HD.1_UniversalId>  
        </MSH.5_ReceivingApplication><MSH.6_ReceivingFacility><HD.0_NamespaceId>dstFac</HD.0_NamespaceId>  
        <HD.1_UniversalId>dstFacUid</HD.1_UniversalId></MSH.6_ReceivingFacility><MSH.7_DateTimeOfMessage>  
        <TS.1>200307092343</TS.1></MSH.7_DateTimeOfMessage><MSH.8_Security>sec</MSH.8_Security>  
        <MSH.9_MessageType><CM_MSG.0_MessageType>ADT</CM_MSG.0_MessageType>  
        <CM_MSG.1_TriggerEvent>A04</CM_MSG.1_TriggerEvent></MSH.9_MessageType>  
        <MSH.10_MessageControlId>msgid2134</MSH.10_MessageControlId><MSH.11_ProcessingId>  
        <PT.0_ProcessingId>P</PT.0_ProcessingId></MSH.11_ProcessingId><MSH.12_VersionId>  
       <VID_0_VersionId>2.2</VID_0_VersionId></MSH.12_VersionId></MSH></ns0:MSH_25_GLO_DEF>");  
  
    DoorbellFinalMessage.MSHSegment = HeaderInfo;  
    DoorbellFinalMessage.BodySegments = DoorbellOutputMessage;  
    DoorbellFinalMessage.ZSegments = "";  
  
    DoorbellFinalMessage(BTAHL7Schemas.MSH1) = 124;   
    DoorbellFinalMessage(BTAHL7Schemas.MessageEncoding) = 65001;  
    DoorbellFinalMessage(BTAHL7Schemas.MSH2) = "^~\\&";  
    DoorbellFinalMessage(BTAHL7Schemas.ParseError) = false;   
    DoorbellFinalMessage(BTAHL7Schemas.ZPartPresent) = false;  
    DoorbellFinalMessage(BTAHL7Schemas.SegmentDelimiter2Char) = true;  
  
    ```  
  
14. 按一下 [確定] 。  
  
    > [!IMPORTANT]
    >  在 「 HeaderInfo.LoadXml"運算式中，刪除在運算式內的空格與換行字元。 「 HeaderInfo.LoadXml"陳述式應該是在同一行。  
    > 
    > [!NOTE]
    >  上述文字的第一個區塊是硬式編碼的 XML 標頭的範例。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]序列化程式需要的標頭區段。 您可以自訂這些標頭值，根據您的環境的需求。 上述文字的第二個區塊會定義所需要的多部分訊息的三個訊息部分。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]序列化程式需要多部分訊息。 上述文字的第三個區塊包含的升級的屬性，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]才能序列化為 XML 訊息轉換為 HL7 一般檔案訊息的序列化程式會檢查。  
  
    請繼續進行[步驟 13： 建立和設定連接埠](../../adapters-and-accelerators/accelerator-hl7/step-13-create-and-configure-ports.md)。  
  
## <a name="see-also"></a>另請參閱  
 [訊息擴充教學課程](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)