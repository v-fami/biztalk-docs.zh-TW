---
title: "步驟 12： 設定協調流程圖形 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring, orchestration shapes
- orchestrations, shapes
- message enrichment tutorial, orchestrations
ms.assetid: 9388254b-2841-4489-838e-de913ceff151
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f7375912c49c431c67c7ff55025cd2821374b87b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-12-configure-orchestration-shapes"></a><span data-ttu-id="1a65a-102">步驟 12： 設定協調流程圖形</span><span class="sxs-lookup"><span data-stu-id="1a65a-102">Step 12: Configure Orchestration Shapes</span></span>
<span data-ttu-id="1a65a-103">在此步驟中，您可以完成協調流程圖形的組態以移除組態不完整智慧標籤。</span><span class="sxs-lookup"><span data-stu-id="1a65a-103">In this step, you complete the configuration of the orchestration shapes in order to remove the insufficient configuration smart tags.</span></span> <span data-ttu-id="1a65a-104">您指定**DoorbellOutputMessage**做為第一個轉換程序的輸出指定**DoorbellMap.btm**當做該程序中使用的對應。</span><span class="sxs-lookup"><span data-stu-id="1a65a-104">You designate **DoorbellOutputMessage** as the output of the first transform process, designating **DoorbellMap.btm** as the map used in that process.</span></span> <span data-ttu-id="1a65a-105">然後指定**DoorbellFinalMessage**做為第二個輸出轉換程序，並加入充實其他欄位資料訊息的運算式。</span><span class="sxs-lookup"><span data-stu-id="1a65a-105">You then designate **DoorbellFinalMessage** as the output of the second transform process, and add the expression that enriches the message with additional field data.</span></span>  
  
 <span data-ttu-id="1a65a-106">**必要條件：** [知識庫文章 941261](http://support.microsoft.com/kb/941261)必須套用之前設定協調流程設定。</span><span class="sxs-lookup"><span data-stu-id="1a65a-106">**Prerequisite:** [KB article 941261](http://support.microsoft.com/kb/941261) must be applied before setting up Orchestration Configuration.</span></span>  
  
### <a name="to-configure-orchestration-shapes"></a><span data-ttu-id="1a65a-107">若要設定協調流程圖形</span><span class="sxs-lookup"><span data-stu-id="1a65a-107">To configure orchestration shapes</span></span>  
  
1.  <span data-ttu-id="1a65a-108">協調流程設計檢視介面上[!INCLUDE[vs2012](../../includes/vs2012-md.md)]，按一下  **[constructmessage_1]**圖形。</span><span class="sxs-lookup"><span data-stu-id="1a65a-108">On the orchestration Design view surface of [!INCLUDE[vs2012](../../includes/vs2012-md.md)], click the **ConstructMessage_1** shape.</span></span>  
  
2.  <span data-ttu-id="1a65a-109">在**屬性**視窗中，按一下 **建構的訊息**屬性選取**DoorbellOutputMessage**從下拉式清單，然後按下**輸入**。</span><span class="sxs-lookup"><span data-stu-id="1a65a-109">In the **Properties** window, click the **Messages Constructed** property, select **DoorbellOutputMessage** from the drop-down list, and then press **Enter**.</span></span>  
  
3.  <span data-ttu-id="1a65a-110">協調流程設計檢視介面上，按一下  **DoorbellTransform**圖形內**constructmessage_1**圖形。</span><span class="sxs-lookup"><span data-stu-id="1a65a-110">On the orchestration Design view surface, click the **DoorbellTransform** shape inside of the **ConstructMessage_1** shape.</span></span> <span data-ttu-id="1a65a-111">在**屬性**視窗中，按一下 **對應名稱**，然後按一下 屬性欄位中的省略符號 （...） 按鈕。</span><span class="sxs-lookup"><span data-stu-id="1a65a-111">In the **Properties** window, click **Map Name**, and then click the ellipsis (…) button in the attribute field.</span></span>  
  
4.  <span data-ttu-id="1a65a-112">在 [轉換組態] 對話方塊中，選取**現有對應**。</span><span class="sxs-lookup"><span data-stu-id="1a65a-112">In the Transform Configuration dialog box, select **Existing Map**.</span></span> <span data-ttu-id="1a65a-113">在**完整格式對應名稱**下拉式清單中，按一下  **BTAHL7_Project.DoorbellMap**。</span><span class="sxs-lookup"><span data-stu-id="1a65a-113">In the **Fully Qualified Map Name** drop-down list, click **BTAHL7_Project.DoorbellMap**.</span></span>  
  
5.  <span data-ttu-id="1a65a-114">按一下**來源**的左窗格中。</span><span class="sxs-lookup"><span data-stu-id="1a65a-114">Click **Source** in the left pane.</span></span>  
  
6.  <span data-ttu-id="1a65a-115">按一下底下的空白方塊**變數名稱**按一下**DoorBellInputMessage**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="1a65a-115">Click the empty box under **Variable Name** and click **DoorBellInputMessage** from the drop-down list.</span></span>  
  
7.  <span data-ttu-id="1a65a-116">按一下**目的地**的左窗格中。</span><span class="sxs-lookup"><span data-stu-id="1a65a-116">Click **Destination** in the left pane.</span></span>  
  
8.  <span data-ttu-id="1a65a-117">按一下底下的空白方塊**變數名稱**按一下**DoorbellOutputMessage**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="1a65a-117">Click the empty box under **Variable Name** and click **DoorbellOutputMessage** from the drop-down list.</span></span>  
  
9. <span data-ttu-id="1a65a-118">按一下**確定**以儲存變更。</span><span class="sxs-lookup"><span data-stu-id="1a65a-118">Click **OK** to save changes.</span></span>  
  
10. <span data-ttu-id="1a65a-119">協調流程設計檢視介面上，按一下  **ConstructMessage_2**圖形。</span><span class="sxs-lookup"><span data-stu-id="1a65a-119">On the orchestration Design view surface, click the **ConstructMessage_2** shape.</span></span>  
  
11. <span data-ttu-id="1a65a-120">在**屬性**視窗中，按一下 **建構的訊息**，選取**DoorbellFinalMessage**從下拉式清單，然後按下**Enter**.</span><span class="sxs-lookup"><span data-stu-id="1a65a-120">In the **Properties** window, click **Messages Constructed**, select **DoorbellFinalMessage** from the drop-down list, and then press **Enter**.</span></span>  
  
12. <span data-ttu-id="1a65a-121">協調流程設計檢視介面上，按一下  **DoorbellFinalTransform**圖形內**ConstructMessage_2**圖形。</span><span class="sxs-lookup"><span data-stu-id="1a65a-121">On the orchestration Design view surface, click the **DoorbellFinalTransform** shape inside of the **ConstructMessage_2** shape.</span></span> <span data-ttu-id="1a65a-122">在**屬性**視窗中，按一下 **運算式**，然後按一下省略符號 （...） 按鈕，以開啟 BizTalk 運算式編輯器。</span><span class="sxs-lookup"><span data-stu-id="1a65a-122">In the **Properties** window, click **Expression**, and then click the ellipsis (…) button to open BizTalk Expression Editor.</span></span>  
  
13. <span data-ttu-id="1a65a-123">在 [BizTalk 運算式編輯器] 中，文字欄位中按一下，並貼上下列文字：</span><span class="sxs-lookup"><span data-stu-id="1a65a-123">In BizTalk Expression Editor, click in the text field and paste the following text:</span></span>  
  
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
  
14. <span data-ttu-id="1a65a-124">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="1a65a-124">Click **OK**.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="1a65a-125">在 「 HeaderInfo.LoadXml"運算式中，刪除歸位字元和運算式中的空格。</span><span class="sxs-lookup"><span data-stu-id="1a65a-125">In the "HeaderInfo.LoadXml" expression, delete the carriage returns and spaces within the expression.</span></span> <span data-ttu-id="1a65a-126">「 HeaderInfo.LoadXml"陳述式應該是在同一行。</span><span class="sxs-lookup"><span data-stu-id="1a65a-126">The "HeaderInfo.LoadXml" statement should be on one line.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1a65a-127">上述文字的第一個區塊是硬式編碼的 XML 標頭的範例。</span><span class="sxs-lookup"><span data-stu-id="1a65a-127">The first block of the preceding text is an example of a hard-coded XML header.</span></span> <span data-ttu-id="1a65a-128">[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]序列化程式需要的標頭區段。</span><span class="sxs-lookup"><span data-stu-id="1a65a-128">The [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] serializer requires a header segment.</span></span> <span data-ttu-id="1a65a-129">您可以自訂這些標頭值，根據您的環境的需求。</span><span class="sxs-lookup"><span data-stu-id="1a65a-129">You can customize these header values according to the needs of your environment.</span></span> <span data-ttu-id="1a65a-130">上述文字的第二個區塊定義所需要的多部分訊息的三個訊息部分。</span><span class="sxs-lookup"><span data-stu-id="1a65a-130">The second block of the preceding text defines the three message parts required in a multipart message.</span></span> <span data-ttu-id="1a65a-131">[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]序列化程式需要多部分訊息。</span><span class="sxs-lookup"><span data-stu-id="1a65a-131">The [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] serializer requires a multipart message.</span></span> <span data-ttu-id="1a65a-132">上述文字的第三個區塊包含的升級的屬性的[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]序列化程式會檢查序列化的 XML 訊息轉換為 HL7 一般檔案訊息。</span><span class="sxs-lookup"><span data-stu-id="1a65a-132">The third block of the preceding text contains the promoted properties that the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] serializer examines in order to serialize an XML message into an HL7 flat-file message.</span></span>  
  
 <span data-ttu-id="1a65a-133">若要繼續[步驟 13： 建立和設定連接埠](../../adapters-and-accelerators/accelerator-hl7/step-13-create-and-configure-ports.md)。</span><span class="sxs-lookup"><span data-stu-id="1a65a-133">Proceed to [Step 13: Create and Configure Ports](../../adapters-and-accelerators/accelerator-hl7/step-13-create-and-configure-ports.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a65a-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1a65a-134">See Also</span></span>  
 [<span data-ttu-id="1a65a-135">訊息擴充教學課程</span><span class="sxs-lookup"><span data-stu-id="1a65a-135">Message Enrichment Tutorial</span></span>](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)