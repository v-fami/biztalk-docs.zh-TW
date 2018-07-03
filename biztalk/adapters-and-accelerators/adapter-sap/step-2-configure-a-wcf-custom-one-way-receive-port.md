---
title: 步驟 2： 設定 Wcf-custom 單向接收埠 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF-Custom one-way receive port, configuring
- migration
ms.assetid: e2a8f074-64d5-4e6c-84d0-318fb606c0ba
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0d3320e7a2e6b948309087f2b33def57db9db0c9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36990295"
---
# <a name="step-2-configure-a-wcf-custom-one-way-receive-port"></a><span data-ttu-id="0ea6b-102">步驟 2： 設定 Wcf-custom 單向接收埠</span><span class="sxs-lookup"><span data-stu-id="0ea6b-102">Step 2: Configure a WCF-Custom One-way Receive Port</span></span>
<span data-ttu-id="0ea6b-103">![步驟 3 之 2](../../adapters-and-accelerators/adapter-oracle-database/media/step-2of3.gif "Step_2of3")</span><span class="sxs-lookup"><span data-stu-id="0ea6b-103">![Step 2 of 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-2of3.gif "Step_2of3")</span></span>  
  
 <span data-ttu-id="0ea6b-104">**若要完成的時間：** 10 分鐘</span><span class="sxs-lookup"><span data-stu-id="0ea6b-104">**Time to complete:** 10 minutes</span></span>  
  
 <span data-ttu-id="0ea6b-105">**目標：** 在此步驟中，您可以設定 WCF 自訂連接埠來接收一般檔案 IDOC 從 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="0ea6b-105">**Objective:** In this step, you configure a WCF-Custom port to receive a flat-file IDOC from an SAP system.</span></span> <span data-ttu-id="0ea6b-106">設定連接埠之後, 您可以設定 BizTalk 應用程式使用 WCF 自訂接收埠。</span><span class="sxs-lookup"><span data-stu-id="0ea6b-106">After configuring the port, you configure the BizTalk application to use the WCF-Custom receive port.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="0ea6b-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="0ea6b-107">Prerequisites</span></span>  
 <span data-ttu-id="0ea6b-108">您必須建置並部署 vPrev BizTalk 專案，若要從 SAP 系統接收 Idoc。</span><span class="sxs-lookup"><span data-stu-id="0ea6b-108">You must have built and deployed your vPrev BizTalk project to receive IDOCs from an SAP system.</span></span>  
  
### <a name="to-configure-a-wcf-custom-one-way-receive-port"></a><span data-ttu-id="0ea6b-109">若要設定 Wcf-custom 單向接收埠</span><span class="sxs-lookup"><span data-stu-id="0ea6b-109">To configure a WCF-Custom one-way receive port</span></span>  
  
1. <span data-ttu-id="0ea6b-110">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="0ea6b-110">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2. <span data-ttu-id="0ea6b-111">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="0ea6b-111">In the console tree, expand **BizTalk Group**, and then expand **Applications**.</span></span>  
  
3. <span data-ttu-id="0ea6b-112">展開您想要在其下建立接收埠的應用程式。</span><span class="sxs-lookup"><span data-stu-id="0ea6b-112">Expand the application under which you want create the receive port.</span></span>  
  
4. <span data-ttu-id="0ea6b-113">以滑鼠右鍵按一下**接收連接埠**，指向**新增**，然後按一下**單向接收埠**。</span><span class="sxs-lookup"><span data-stu-id="0ea6b-113">Right-click **Receive Ports**, point to **New**, and click **One-way Receive Port**.</span></span>  
  
5. <span data-ttu-id="0ea6b-114">在 **接收埠屬性**對話方塊的 **一般**索引標籤上，輸入接收埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="0ea6b-114">In the **Receive Port Properties** dialog box, on the **General** tab, type a name for the receive port.</span></span>  
  
6. <span data-ttu-id="0ea6b-115">在 **接收位置**索引標籤上，按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="0ea6b-115">On the **Receive Locations** tab, click **New**.</span></span> <span data-ttu-id="0ea6b-116">**接收位置屬性** 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="0ea6b-116">The **Receive Location Properties** dialog box appears.</span></span>  
  
7. <span data-ttu-id="0ea6b-117">在 **接收位置屬性**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="0ea6b-117">In the **Receive Location Properties** dialog box, do the following:</span></span>  
  
   1.  <span data-ttu-id="0ea6b-118">指定接收位置的名稱。</span><span class="sxs-lookup"><span data-stu-id="0ea6b-118">Specify a name for the receive location.</span></span>  
  
   2.  <span data-ttu-id="0ea6b-119">從**型別**下拉式清單中，選取**Wcf-custom**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="0ea6b-119">From the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.</span></span>  
  
8. <span data-ttu-id="0ea6b-120">在  **Wcf-custom 傳輸屬性**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="0ea6b-120">In the **WCF-Custom Transport Properties** dialog box, do the following:</span></span>  
  
   1. <span data-ttu-id="0ea6b-121">按一下 [**一般**] 索引標籤，然後在**位址 (URI)** 欄位中，指定連線 URI，從 SAP 系統接收訊息。</span><span class="sxs-lookup"><span data-stu-id="0ea6b-121">Click the **General** tab, and in the **Address (URI)** field, specify the connection URI to receive messages from the SAP system.</span></span> <span data-ttu-id="0ea6b-122">連接到 SAP 系統從接收訊息的 URI 必須以下列格式：</span><span class="sxs-lookup"><span data-stu-id="0ea6b-122">The connection URI to receive messages from the SAP system must be in the following format:</span></span>  
  
      ```  
      sap://Client=800;lang=EN@A/YourSAPHOST/00?ListenerGwHost=YourSAPHOST&ListenerGwServ=SAPGW00&ListenerProgramId=MyProgramId  
      ```  
  
       <span data-ttu-id="0ea6b-123">下圖顯示具有指定之 URI 的連接埠的 [內容] 對話方塊：</span><span class="sxs-lookup"><span data-stu-id="0ea6b-123">The following figure shows the port properties dialog box with the URI specified:</span></span>  
  
       <span data-ttu-id="0ea6b-124">![若要從 SAP 接收訊息的 URI 連接](../../adapters-and-accelerators/adapter-sap/media/91e12582-aea3-4f13-8cdc-af69a9a11a5c.gif "91e12582-aea3-4f13-8cdc-af69a9a11a5c")</span><span class="sxs-lookup"><span data-stu-id="0ea6b-124">![Connection URI to receive messages from SAP](../../adapters-and-accelerators/adapter-sap/media/91e12582-aea3-4f13-8cdc-af69a9a11a5c.gif "91e12582-aea3-4f13-8cdc-af69a9a11a5c")</span></span>  
  
       <span data-ttu-id="0ea6b-125">如需連線 URI 的詳細資訊，請參閱[建立 SAP 系統的連線](../../adapters-and-accelerators/adapter-sap/create-a-connection-to-the-sap-system.md)。</span><span class="sxs-lookup"><span data-stu-id="0ea6b-125">For more information about the connection URI, see [Create a  connection to the SAP system](../../adapters-and-accelerators/adapter-sap/create-a-connection-to-the-sap-system.md).</span></span>  
  
   2. <span data-ttu-id="0ea6b-126">按一下 **繫結**索引標籤上，以及從**繫結的型別**下拉式清單中，選取**sapBinding**。</span><span class="sxs-lookup"><span data-stu-id="0ea6b-126">Click the **Binding** tab, and from the **Binding Type** drop-down list, select **sapBinding**.</span></span> <span data-ttu-id="0ea6b-127">請確定指定接收埠的下列繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="0ea6b-127">Make sure you specify the following binding properties for the receive port.</span></span>  
  
      |<span data-ttu-id="0ea6b-128">繫結屬性</span><span class="sxs-lookup"><span data-stu-id="0ea6b-128">Binding property</span></span>|<span data-ttu-id="0ea6b-129">若要設定的值</span><span class="sxs-lookup"><span data-stu-id="0ea6b-129">Set value to</span></span>|  
      |----------------------|------------------|  
      |<span data-ttu-id="0ea6b-130">FlatFileSegmentIndicator</span><span class="sxs-lookup"><span data-stu-id="0ea6b-130">flatFileSegmentIndicator</span></span>|<span data-ttu-id="0ea6b-131">**SegmentType**。</span><span class="sxs-lookup"><span data-stu-id="0ea6b-131">**SegmentType**.</span></span> <span data-ttu-id="0ea6b-132">這表示一般的檔案應該包含在 IDOC 中的每個區段的區段類型。</span><span class="sxs-lookup"><span data-stu-id="0ea6b-132">This indicates that the flat files should contain the segment type for each segment in the IDOC.</span></span>|  
      |<span data-ttu-id="0ea6b-133">PadReceivedIdocWithSpaces</span><span class="sxs-lookup"><span data-stu-id="0ea6b-133">padReceivedIdocWithSpaces</span></span>|<span data-ttu-id="0ea6b-134">**True**。</span><span class="sxs-lookup"><span data-stu-id="0ea6b-134">**True**.</span></span> <span data-ttu-id="0ea6b-135">指定 IDOC 中的每一行是否填補空格到正確的長度。</span><span class="sxs-lookup"><span data-stu-id="0ea6b-135">Specifies whether each line in the IDOC is padded with spaces to the correct length.</span></span>|  
      |<span data-ttu-id="0ea6b-136">ReceiveIDocFormat</span><span class="sxs-lookup"><span data-stu-id="0ea6b-136">receiveIDocFormat</span></span>|<span data-ttu-id="0ea6b-137">**字串**。</span><span class="sxs-lookup"><span data-stu-id="0ea6b-137">**String**.</span></span> <span data-ttu-id="0ea6b-138">這會指定 IDOC 訊息應該以單一字串欄位。</span><span class="sxs-lookup"><span data-stu-id="0ea6b-138">This specifies that the IDOC message should be represented as a single string field.</span></span>|  
  
       <span data-ttu-id="0ea6b-139">如需有關繫結屬性的詳細資訊，請參閱 <<c0> [ 了解 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="0ea6b-139">For more information about binding properties, see [Read about BizTalk Adapter for mySAP Business Suite Binding Properties](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).</span></span>  
  
   3. <span data-ttu-id="0ea6b-140">按一下 **其他人**索引標籤，然後指定要連接到 SAP 系統的認證。</span><span class="sxs-lookup"><span data-stu-id="0ea6b-140">Click the **Others** tab, and specify the credentials to connect to an SAP system.</span></span>  
  
   4. <span data-ttu-id="0ea6b-141">按一下 [**訊息**] 索引標籤，然後在**輸入 BizTalk 訊息內文**區段中，選擇**路徑**選項。</span><span class="sxs-lookup"><span data-stu-id="0ea6b-141">Click the **Messages** tab, and in the **Inbound BizTalk message body** section, choose the **Path** option.</span></span>  
  
   5. <span data-ttu-id="0ea6b-142">在 **內文路徑運算式**文字方塊中，指定要擷取的 XML 訊息的一般檔案 IDOC 的 XPath 查詢。</span><span class="sxs-lookup"><span data-stu-id="0ea6b-142">In the **Body path expression** text box, specify the XPath query to extract the flat-file IDOC from the XML message.</span></span> <span data-ttu-id="0ea6b-143">如此一來，接收埠擷取 IDOC 中的資料與修剪是一部分的 XML 標記**ReceiveIdoc** WCF 為基礎的作業[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0ea6b-143">By doing so, the receive port extracts the data from the IDOC and trims the XML tag that is part of the **ReceiveIdoc** operation for the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span> <span data-ttu-id="0ea6b-144">如需有關的訊息結構描述**ReceiveIdoc**作業，請參閱[IDOC 作業的訊息結構描述](../../adapters-and-accelerators/adapter-sap/message-schemas-for-idoc-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="0ea6b-144">For more information about the message schema for the **ReceiveIdoc** operation, see [Message Schemas for IDOC Operations](../../adapters-and-accelerators/adapter-sap/message-schemas-for-idoc-operations.md).</span></span>  
  
       <span data-ttu-id="0ea6b-145">![用於擷取一般的 XPath 查詢&#45;檔案 IDOC](../../adapters-and-accelerators/adapter-sap/media/8b5b8165-a1e7-40ef-bcf7-de3149c6deb0.gif "8b5b8165-a1e7-40ef-bcf7-de3149c6deb0")</span><span class="sxs-lookup"><span data-stu-id="0ea6b-145">![XPath query to extract the flat&#45;file IDOC](../../adapters-and-accelerators/adapter-sap/media/8b5b8165-a1e7-40ef-bcf7-de3149c6deb0.gif "8b5b8165-a1e7-40ef-bcf7-de3149c6deb0")</span></span>  
  
       <span data-ttu-id="0ea6b-146">您必須指定下列的 XPath 查詢：</span><span class="sxs-lookup"><span data-stu-id="0ea6b-146">You must specify the following XPath query:</span></span>  
  
      ```  
      /*[local-name()='ReceiveIdoc']/*[local-name()='idocData']  
      ```  
  
   6. <span data-ttu-id="0ea6b-147">從**節點編碼**下拉式清單中，選取**字串**。</span><span class="sxs-lookup"><span data-stu-id="0ea6b-147">From the **Node encoding** drop-down list, select **String**.</span></span>  
  
   7. <span data-ttu-id="0ea6b-148">按一下 **套用**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="0ea6b-148">Click **Apply**, and then click **OK**.</span></span>  
  
9. <span data-ttu-id="0ea6b-149">在 [接收位置屬性] 對話方塊中，從**接收處理常式**下拉式清單中，選取**BizTalkServerApplication**。</span><span class="sxs-lookup"><span data-stu-id="0ea6b-149">In the Receive Location Properties dialog box, from the **Receive handler** drop-down list, select **BizTalkServerApplication**.</span></span>  
  
10. <span data-ttu-id="0ea6b-150">從**接收管線**下拉式清單中，選取**ConvertToXML**。</span><span class="sxs-lookup"><span data-stu-id="0ea6b-150">From the **Receive pipeline** drop-down list, select **ConvertToXML**.</span></span> <span data-ttu-id="0ea6b-151">這個一般檔案解譯器管線已經將一般檔案 IDOC 轉換成 XML IDOC vPrev BizTalk 專案的一部分。</span><span class="sxs-lookup"><span data-stu-id="0ea6b-151">This flat-file disassembler pipeline is already a part of the vPrev BizTalk project to convert a flat-file IDOC to an XML IDOC.</span></span>  
  
11. <span data-ttu-id="0ea6b-152">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="0ea6b-152">Click **OK**.</span></span>  
  
### <a name="to-configure-the-biztalk-application"></a><span data-ttu-id="0ea6b-153">若要設定的 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="0ea6b-153">To configure the BizTalk application</span></span>  
  
1. <span data-ttu-id="0ea6b-154">在 BizTalk Server 管理主控台中，依序展開**BizTalk 群組**，展開**應用程式**、 展開協調流程的部署位置的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="0ea6b-154">In the BizTalk Server Administration console, expand **BizTalk Group**, expand **Applications**, and expand the BizTalk Application where the orchestration is deployed.</span></span>  
  
2. <span data-ttu-id="0ea6b-155">以滑鼠右鍵按一下 BizTalk 應用程式，然後選取**設定**。</span><span class="sxs-lookup"><span data-stu-id="0ea6b-155">Right-click the BizTalk application, and then select **Configure**.</span></span>  
  
3. <span data-ttu-id="0ea6b-156">從左窗格中，按一下 協調流程設定。</span><span class="sxs-lookup"><span data-stu-id="0ea6b-156">From the left pane, click the orchestration to configure.</span></span> <span data-ttu-id="0ea6b-157">從右窗格中，從**主機**下拉式清單中，選取 BizTalk 主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="0ea6b-157">From the right pane, from the **Host** drop-down list, select a BizTalk host instance.</span></span>  
  
4. <span data-ttu-id="0ea6b-158">底下**繫結**方塊中，將 BizTalk 協調流程的邏輯連接埠對應至 BizTalk Server 管理主控台中的實體連接埠。</span><span class="sxs-lookup"><span data-stu-id="0ea6b-158">Under the **Bindings** box, map the logical ports of the BizTalk orchestration to the physical ports in the BizTalk Server Administration console.</span></span>  
  
   1. <span data-ttu-id="0ea6b-159">選取 「 WCF 自訂接收您稍早在本主題中建立的連接埠。</span><span class="sxs-lookup"><span data-stu-id="0ea6b-159">Select the WCF-Custom receive port you created earlier in this topic.</span></span>  
  
   2. <span data-ttu-id="0ea6b-160">選取您將在何處接收一般檔案 IDOC 的 file 連接埠。</span><span class="sxs-lookup"><span data-stu-id="0ea6b-160">Select a file port where you will receive the flat-file IDOC.</span></span>  
  
   3. <span data-ttu-id="0ea6b-161">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="0ea6b-161">Click **OK**.</span></span>  
  
      <span data-ttu-id="0ea6b-162">如需有關如何設定應用程式的詳細資訊，請參閱 < [ http://go.microsoft.com/fwlink/?LinkId=102360 ](http://go.microsoft.com/fwlink/?LinkId=102360)。</span><span class="sxs-lookup"><span data-stu-id="0ea6b-162">For more information about configuring an application, see [http://go.microsoft.com/fwlink/?LinkId=102360](http://go.microsoft.com/fwlink/?LinkId=102360).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="0ea6b-163">後續步驟</span><span class="sxs-lookup"><span data-stu-id="0ea6b-163">Next Steps</span></span>  
 <span data-ttu-id="0ea6b-164">您現在已完成移轉至 BizTalk 專案，從使用以 WCF 為基礎的 SAP 系統接收 Idoc vPrev BizTalk 專案的[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0ea6b-164">You have now completed migration of your vPrev BizTalk project to a BizTalk project that receives IDOCs from an SAP system using the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span> <span data-ttu-id="0ea6b-165">您必須現在測試已移轉的 BizTalk 應用程式接收一般檔案 IDOC，如中所述[步驟 3： 測試移轉的應用程式](../../adapters-and-accelerators/adapter-sap/step-3-test-the-migrated-application5.md)。</span><span class="sxs-lookup"><span data-stu-id="0ea6b-165">You must now test the migrated BizTalk application by receiving a flat-file IDOC, as described in [Step 3: Test the Migrated Application](../../adapters-and-accelerators/adapter-sap/step-3-test-the-migrated-application5.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ea6b-166">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0ea6b-166">See Also</span></span>  
 [<span data-ttu-id="0ea6b-167">教學課程 4：移轉 SAP 接收 IDOC BizTalk 專案</span><span class="sxs-lookup"><span data-stu-id="0ea6b-167">Tutorial 4: Migrating an SAP Receive IDOC BizTalk Project</span></span>](../../adapters-and-accelerators/adapter-sap/tutorial-4-migrating-an-sap-receive-idoc-biztalk-project.md)