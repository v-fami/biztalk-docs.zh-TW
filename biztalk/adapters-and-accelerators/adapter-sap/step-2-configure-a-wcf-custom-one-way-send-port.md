---
title: 步驟 2： 設定 Wcf-custom 單向傳送埠 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF-Custom one-way send port, configuring
- migration
ms.assetid: ae13222e-42e7-45a7-9b2a-0a6779b21736
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8aab14799076d3f774130b357ab90c5ed5335f4a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25962788"
---
# <a name="step-2-configure-a-wcf-custom-one-way-send-port"></a><span data-ttu-id="90b91-102">步驟 2： 設定 Wcf-custom 單向傳送埠</span><span class="sxs-lookup"><span data-stu-id="90b91-102">Step 2: Configure a WCF-Custom One-way Send Port</span></span>
<span data-ttu-id="90b91-103">![步驟 3 之 2](../../adapters-and-accelerators/adapter-oracle-database/media/step-2of3.gif "Step_2of3")</span><span class="sxs-lookup"><span data-stu-id="90b91-103">![Step 2 of 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-2of3.gif "Step_2of3")</span></span>  
  
 <span data-ttu-id="90b91-104">**若要完成的時間：** 10 分鐘</span><span class="sxs-lookup"><span data-stu-id="90b91-104">**Time to complete:** 10 minutes</span></span>  
  
 <span data-ttu-id="90b91-105">**目標：** 在此步驟中，您可以設定 WCF 自訂連接埠來傳送一般檔案 IDOC 到 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="90b91-105">**Objective:** In this step, you configure a WCF-Custom port to send the flat-file IDOC to an SAP system.</span></span> <span data-ttu-id="90b91-106">設定連接埠之後, 您可以設定使用 Wcf-custom 傳送埠的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="90b91-106">After configuring the port, you configure the BizTalk application to use the WCF-Custom send port.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="90b91-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="90b91-107">Prerequisites</span></span>  
 <span data-ttu-id="90b91-108">您必須建立和部署 vPrev BizTalk 專案，以傳送 Idoc 至 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="90b91-108">You must have built and deployed your vPrev BizTalk project to send IDOCs to an SAP system.</span></span>  
  
### <a name="to-configure-a-wcf-custom-one-way-send-port"></a><span data-ttu-id="90b91-109">若要設定 Wcf-custom 單向傳送埠</span><span class="sxs-lookup"><span data-stu-id="90b91-109">To configure a WCF-Custom one-way send port</span></span>  
  
1.  <span data-ttu-id="90b91-110">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="90b91-110">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="90b91-111">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="90b91-111">In the console tree, expand **BizTalk Group**, and then expand **Applications**.</span></span>  
  
3.  <span data-ttu-id="90b91-112">展開您要在其下建立傳送埠的應用程式。</span><span class="sxs-lookup"><span data-stu-id="90b91-112">Expand the application under which you want to create the send port.</span></span>  
  
4.  <span data-ttu-id="90b91-113">以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下**靜態單向傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="90b91-113">Right-click **Send Ports**, point to **New**, and click **Static One-way Send Port**.</span></span>  
  
5.  <span data-ttu-id="90b91-114">在**傳送埠屬性**對話方塊**一般**索引標籤上，輸入傳送埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="90b91-114">In the **Send Port Properties** dialog box, on the **General** tab, type a name for the send port.</span></span>  
  
6.  <span data-ttu-id="90b91-115">從**類型**下拉式清單中，選取**Wcf-custom**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="90b91-115">From the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.</span></span>  
  
7.  <span data-ttu-id="90b91-116">在**Wcf-custom 傳輸屬性**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="90b91-116">In the **WCF-Custom Transport Properties** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="90b91-117">按一下**一般** 索引標籤，然後在**位址 (URI)** 欄位中，指定連線將訊息傳送至 SAP 系統的 URI。</span><span class="sxs-lookup"><span data-stu-id="90b91-117">Click the **General** tab, and in the **Address (URI)** field, specify the connection URI to send messages to the SAP system.</span></span> <span data-ttu-id="90b91-118">如需連線 URI 的詳細資訊，請參閱[建立 SAP 系統連接 URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md)。</span><span class="sxs-lookup"><span data-stu-id="90b91-118">For more information about the connection URI, see [Create the SAP System Connection URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md).</span></span>  
  
         <span data-ttu-id="90b91-119">![指定傳送埠中的連線 URI](../../adapters-and-accelerators/adapter-sap/media/53ae71e1-89ec-49c5-8096-ff04a2c94c0a.gif "53ae71e1-89ec-49c5-8096-ff04a2c94c0a")</span><span class="sxs-lookup"><span data-stu-id="90b91-119">![Connection URI specified in the send port](../../adapters-and-accelerators/adapter-sap/media/53ae71e1-89ec-49c5-8096-ff04a2c94c0a.gif "53ae71e1-89ec-49c5-8096-ff04a2c94c0a")</span></span>  
  
    2.  <span data-ttu-id="90b91-120">在**一般**索引標籤的**動作**文字方塊中，輸入作業的動作。</span><span class="sxs-lookup"><span data-stu-id="90b91-120">On the **General** tab, in the **Action** text box, type the action for the operation.</span></span> <span data-ttu-id="90b91-121">若要傳送一般檔案 IDOC，您必須使用**SendIdoc**作業由 WCF 基礎[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="90b91-121">To send a flat-file IDOC, you must use the **SendIdoc** operation exposed by the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span> <span data-ttu-id="90b91-122">**SendIdoc**作業可讓配接器用戶端傳送 Idoc 具有弱式型別的結構描述。</span><span class="sxs-lookup"><span data-stu-id="90b91-122">**SendIdoc** operation enables adapter clients to send IDOCs having a weakly-typed schema.</span></span> <span data-ttu-id="90b91-123">如需詳細資訊，請參閱[sap Idoc 的作業](../../adapters-and-accelerators/adapter-sap/operations-on-idocs-in-sap.md)。</span><span class="sxs-lookup"><span data-stu-id="90b91-123">For more information, see [Operations on IDOCs in SAP](../../adapters-and-accelerators/adapter-sap/operations-on-idocs-in-sap.md).</span></span> <span data-ttu-id="90b91-124">下圖顯示**動作**文字方塊的動作與**SendIdoc**作業。</span><span class="sxs-lookup"><span data-stu-id="90b91-124">The following figure shows the **Action** text box with the action for the **SendIdoc** operation.</span></span>  
  
         <span data-ttu-id="90b91-125">![在 傳送埠中指定動作](../../adapters-and-accelerators/adapter-sap/media/94dd1505-5529-43cf-a27b-2588a022dfb9.gif "94dd1505-5529-43cf-a27b-2588a022dfb9")</span><span class="sxs-lookup"><span data-stu-id="90b91-125">![Specify action in the send port](../../adapters-and-accelerators/adapter-sap/media/94dd1505-5529-43cf-a27b-2588a022dfb9.gif "94dd1505-5529-43cf-a27b-2588a022dfb9")</span></span>  
  
    3.  <span data-ttu-id="90b91-126">按一下**繫結** 索引標籤，並從**繫結的型別**下拉式清單中，選取**sapBinding**。</span><span class="sxs-lookup"><span data-stu-id="90b91-126">Click the **Binding** tab, and from the **Binding Type** drop-down list, select **sapBinding**.</span></span>  
  
    4.  <span data-ttu-id="90b91-127">按一下**認證**索引標籤並指定要連接到 SAP 系統的認證。</span><span class="sxs-lookup"><span data-stu-id="90b91-127">Click the **Credentials** tab and specify the credentials to connect to an SAP system.</span></span>  
  
    5.  <span data-ttu-id="90b91-128">按一下**訊息** 索引標籤，然後在**輸出 WCF 訊息內文**區段中，選擇**範本**選項。</span><span class="sxs-lookup"><span data-stu-id="90b91-128">Click the **Messages** tab, and in the **Outbound WCF message body** section, choose the **Template** option.</span></span>  
  
    6.  <span data-ttu-id="90b91-129">在**XML**文字方塊中，指定將用來建構 WCF 訊息的範本。</span><span class="sxs-lookup"><span data-stu-id="90b91-129">In the **XML** text box, specify the template that will be used to construct the WCF message.</span></span> <span data-ttu-id="90b91-130">如此一來，您會建立符合訊息**SendIdoc** WCF 為基礎的作業[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="90b91-130">By doing so, you create a message that conforms to the **SendIdoc** operation for the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span> <span data-ttu-id="90b91-131">如需有關的訊息結構**SendIdoc**作業，請參閱[IDOC 作業的訊息結構描述](../../adapters-and-accelerators/adapter-sap/message-schemas-for-idoc-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="90b91-131">For more information about the message structure for the **SendIdoc** operation, see [Message Schemas for IDOC Operations](../../adapters-and-accelerators/adapter-sap/message-schemas-for-idoc-operations.md).</span></span>  
  
         <span data-ttu-id="90b91-132">![指定輸出 WCF 訊息的範本](../../adapters-and-accelerators/adapter-sap/media/909835c3-a941-49dc-87f0-858fe0e1fc63.gif "909835c3-a941-49dc-87f0-858fe0e1fc63")</span><span class="sxs-lookup"><span data-stu-id="90b91-132">![Specify template for outbound WCF message](../../adapters-and-accelerators/adapter-sap/media/909835c3-a941-49dc-87f0-858fe0e1fc63.gif "909835c3-a941-49dc-87f0-858fe0e1fc63")</span></span>  
  
         <span data-ttu-id="90b91-133">SendIdoc 作業中，您必須指定下列範本：</span><span class="sxs-lookup"><span data-stu-id="90b91-133">For the SendIdoc operation, you must specify the following template:</span></span>  
  
        ```  
        <SendIdoc xmlns="http://Microsoft.LobServices.Sap/2007/03/Idoc/">  
        <idocData><bts-msg-body xmlns="http://www.microsoft.com/schemas/bts2007" encoding="string"/></idocData>  
        </SendIdoc>  
        ```  
  
         <span data-ttu-id="90b91-134">在上述範本中，`bts-msg-body`是 XML IDOC 建立使用一般檔案解譯器與檔案相關聯的接收埠。</span><span class="sxs-lookup"><span data-stu-id="90b91-134">In the preceding template, the `bts-msg-body` is XML IDOC that is created using the flat-file disassembler associated with the file receive port.</span></span> <span data-ttu-id="90b91-135">XML IDOC 被封裝在 SendIdoc 訊息。</span><span class="sxs-lookup"><span data-stu-id="90b91-135">The XML IDOC is encapsulated in the SendIdoc message.</span></span>  
  
    7.  <span data-ttu-id="90b91-136">按一下**套用**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="90b91-136">Click **Apply**, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="90b91-137">在**傳送埠屬性**對話方塊中，從**傳送處理常式**下拉式清單中，選取**BizTalkServerApplication**。</span><span class="sxs-lookup"><span data-stu-id="90b91-137">In the **Send Port Properties** dialog box, from the **Send handler** drop-down list, select **BizTalkServerApplication**.</span></span>  
  
9. <span data-ttu-id="90b91-138">從**傳送管線**下拉式清單中，選取**ConvertToFlatFile**。</span><span class="sxs-lookup"><span data-stu-id="90b91-138">From the **Send pipeline** drop-down list, select **ConvertToFlatFile**.</span></span> <span data-ttu-id="90b91-139">這個一般檔案組合器管線已 vPrev BizTalk 專案的一部分，用來將 XML IDOC 轉換成一般檔案 IDOC。</span><span class="sxs-lookup"><span data-stu-id="90b91-139">This flat-file assembler pipeline is already a part of the vPrev BizTalk project and is used to convert an XML IDOC to a flat-file IDOC.</span></span>  
  
10. <span data-ttu-id="90b91-140">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="90b91-140">Click **OK**.</span></span>  
  
### <a name="to-configure-the-biztalk-application"></a><span data-ttu-id="90b91-141">若要設定 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="90b91-141">To configure the BizTalk application</span></span>  
  
1.  <span data-ttu-id="90b91-142">在 BizTalk Server 管理主控台中，展開  **BizTalk 群組**，依序展開**應用程式**、 展開協調流程部署所在的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="90b91-142">In the BizTalk Server Administration console, expand **BizTalk Group**, expand **Applications**, and expand the BizTalk Application where the orchestration is deployed.</span></span>  
  
2.  <span data-ttu-id="90b91-143">以滑鼠右鍵按一下 BizTalk 應用程式，然後選取**設定**。</span><span class="sxs-lookup"><span data-stu-id="90b91-143">Right-click the BizTalk application, and then select **Configure**.</span></span>  
  
3.  <span data-ttu-id="90b91-144">從左窗格中，按一下 協調流程設定。</span><span class="sxs-lookup"><span data-stu-id="90b91-144">From the left pane, click the orchestration to configure.</span></span> <span data-ttu-id="90b91-145">從右窗格中，從**主機**下拉式清單中，選取 BizTalk 主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="90b91-145">From the right pane, from the **Host** drop-down list, select a BizTalk host instance.</span></span>  
  
4.  <span data-ttu-id="90b91-146">在下**繫結**方塊中，將 BizTalk 協調流程的邏輯連接埠對應到 BizTalk Server 管理主控台中的實體連接埠。</span><span class="sxs-lookup"><span data-stu-id="90b91-146">Under the **Bindings** box, map the logical ports of the BizTalk orchestration to the physical ports in the BizTalk Server Administration console.</span></span>  
  
    1.  <span data-ttu-id="90b91-147">選取您將在此置放一般檔案 IDOC 的檔案連接埠。</span><span class="sxs-lookup"><span data-stu-id="90b91-147">Select the file port where you will drop the flat-file IDOC.</span></span>  
  
    2.  <span data-ttu-id="90b91-148">選取您稍早在本主題中所建立的 WCF 自訂傳送連接埠。</span><span class="sxs-lookup"><span data-stu-id="90b91-148">Select the WCF-Custom send port you created earlier in this topic.</span></span>  
  
    3.  <span data-ttu-id="90b91-149">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="90b91-149">Click **OK**.</span></span>  
  
     <span data-ttu-id="90b91-150">如需有關如何設定應用程式的詳細資訊，請參閱 「 如何設定應用程式 」 在[http://go.microsoft.com/fwlink/?LinkId=102360](http://go.microsoft.com/fwlink/?LinkId=102360)。</span><span class="sxs-lookup"><span data-stu-id="90b91-150">For more information about configuring an application, see "How to Configure an Application" at [http://go.microsoft.com/fwlink/?LinkId=102360](http://go.microsoft.com/fwlink/?LinkId=102360).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="90b91-151">後續步驟</span><span class="sxs-lookup"><span data-stu-id="90b91-151">Next Steps</span></span>  
 <span data-ttu-id="90b91-152">您現在已完成的 vPrev BizTalk 專案，以傳送 Idoc 到 SAP 系統使用 WCF 為基礎的 BizTalk 專案移轉[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="90b91-152">You have now completed migration of your vPrev BizTalk project to a BizTalk project that sends IDOCs to an SAP system using the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span> <span data-ttu-id="90b91-153">您必須現在測試已移轉的 BizTalk 應用程式傳送一般檔案 IDOC 中, 所述[步驟 3： 測試移轉應用程式](../../adapters-and-accelerators/adapter-sap/step-3-test-the-migrated-application2.md)。</span><span class="sxs-lookup"><span data-stu-id="90b91-153">You must now test the migrated BizTalk application by sending a flat-file IDOC, as described in [Step 3: Test the Migrated Application](../../adapters-and-accelerators/adapter-sap/step-3-test-the-migrated-application2.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90b91-154">請參閱</span><span class="sxs-lookup"><span data-stu-id="90b91-154">See Also</span></span>  
 [<span data-ttu-id="90b91-155">教學課程 3：移轉 SAP 傳送 IDOC BizTalk 專案</span><span class="sxs-lookup"><span data-stu-id="90b91-155">Tutorial 3: Migrating an SAP Send IDOC BizTalk Project</span></span>](../../adapters-and-accelerators/adapter-sap/tutorial-3-migrating-an-sap-send-idoc-biztalk-project.md)