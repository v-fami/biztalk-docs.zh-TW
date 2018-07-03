---
title: BPEL 匯入 （BizTalk Server 範例） |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BPEL, orchestrations
- examples, orchestrations
- examples, BPEL Import Wizard
- BPEL, examples
- BPEL Import Wizard, examples
- BPEL Import Wizard, orchestrations
ms.assetid: 3fc70608-ccd9-4249-b238-c09fc6551db1
caps.latest.revision: 31
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 62eb5603ffca6f22e0e22f185886d0cfefb17746
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37012551"
---
# <a name="bpel-import-biztalk-server-sample"></a><span data-ttu-id="86a9c-102">BPEL 匯入 （BizTalk Server 範例）</span><span class="sxs-lookup"><span data-stu-id="86a9c-102">BPEL Import (BizTalk Server Sample)</span></span>
<span data-ttu-id="86a9c-103">BPEL 匯入範例示範如何從商務程序執行語言 (Business Process Execution Language, BPEL) 程序描述及其相關成品建立協調流程。</span><span class="sxs-lookup"><span data-stu-id="86a9c-103">The BPEL Import sample demonstrates how to create an orchestration from a Business Process Execution Language (BPEL) process description and its related artifacts.</span></span>  

## <a name="what-this-sample-does"></a><span data-ttu-id="86a9c-104">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="86a9c-104">What This Sample Does</span></span>  
 <span data-ttu-id="86a9c-105">Wide World Importers 是一個為零售商提供自動化出貨服務的託運公司。</span><span class="sxs-lookup"><span data-stu-id="86a9c-105">Wide World Importers is a shipping company that provides automated shipping services to retailers.</span></span> <span data-ttu-id="86a9c-106">具體來說，Wide World Importers 可讓零售商可以：</span><span class="sxs-lookup"><span data-stu-id="86a9c-106">Specifically, Wide World Importers enables retailers to:</span></span>  

- <span data-ttu-id="86a9c-107">要求訂單出貨</span><span class="sxs-lookup"><span data-stu-id="86a9c-107">Request order shipments</span></span>  

- <span data-ttu-id="86a9c-108">追蹤出貨</span><span class="sxs-lookup"><span data-stu-id="86a9c-108">Track shipments</span></span>  

- <span data-ttu-id="86a9c-109">確認出貨</span><span class="sxs-lookup"><span data-stu-id="86a9c-109">Confirm shipments</span></span>  

- <span data-ttu-id="86a9c-110">確認出貨的發票開立和付款</span><span class="sxs-lookup"><span data-stu-id="86a9c-110">Confirm invoicing and payment for shipments</span></span>  

  <span data-ttu-id="86a9c-111">雖然這些服務的可用性可透過 Web 服務描述語言 (WSDL) 文件來說明，但 BPEL 文件描述了產品公司應該如何呼叫服務以及應該如何從 Wide World Importers 取得回應的典型方式。</span><span class="sxs-lookup"><span data-stu-id="86a9c-111">While the availability of these services can be represented by using a Web Services Description Language (WSDL) document, a BPEL document describes the typical way in which the product companies are expected to call the services and how to expect responses from Wide World Importers.</span></span>  

  <span data-ttu-id="86a9c-112">當 Northwind Traders 雇用 Wide World Importers 來處理其出貨時，他們會收到一個 BPEL 檔案，以及一些描述整個互動的相關成品。</span><span class="sxs-lookup"><span data-stu-id="86a9c-112">When Northwind Traders hires Wide World Importers to handle their shipping, they are provided a BPEL file and some related artifacts that describe the entire interaction.</span></span> <span data-ttu-id="86a9c-113">Northwind Traders 可使用該 BPEL 檔案建立 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 應用程式 (BPELShipping)，以透過 Wide World Importers 自動處理訂單。</span><span class="sxs-lookup"><span data-stu-id="86a9c-113">Using the BPEL file, Northwind Traders creates a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application (BPELShipping) to automatically process orders through Wide World Importers.</span></span>  

  <span data-ttu-id="86a9c-114">此範例為您逐步解說此案例，其中 BPELShipping 應用程式會：</span><span class="sxs-lookup"><span data-stu-id="86a9c-114">This sample walks you through this scenario in which the BPELShipping application:</span></span>  

1. <span data-ttu-id="86a9c-115">從 Northwind Traders 客戶訂單系統接收訂單。</span><span class="sxs-lookup"><span data-stu-id="86a9c-115">Receives an order from the Northwind Traders customer order system.</span></span>  

2. <span data-ttu-id="86a9c-116">將出貨要求傳送到 Wide World Importers 並要求確認。</span><span class="sxs-lookup"><span data-stu-id="86a9c-116">Sends a shipping request to Wide World Importers and requests confirmation.</span></span>  

3. <span data-ttu-id="86a9c-117">從 Wide World Importers 接收出貨要求確認。</span><span class="sxs-lookup"><span data-stu-id="86a9c-117">Receives shipment request confirmation from Wide World Importers.</span></span>  

4. <span data-ttu-id="86a9c-118">從 Wide World Importers 接收取件通知。</span><span class="sxs-lookup"><span data-stu-id="86a9c-118">Receives pickup notification from Wide World Importers.</span></span>  

5. <span data-ttu-id="86a9c-119">接收客戶收到貨品之前 (時) 的出貨狀態訊息。</span><span class="sxs-lookup"><span data-stu-id="86a9c-119">Receives shipment status messages up to and including when the shipment has been received by the customer.</span></span>  

6. <span data-ttu-id="86a9c-120">從 Wide World Importers 接收發票。</span><span class="sxs-lookup"><span data-stu-id="86a9c-120">Receives an invoice from Wide World Importers.</span></span>  

7. <span data-ttu-id="86a9c-121">使用發票通知回應 Wide World Importers。</span><span class="sxs-lookup"><span data-stu-id="86a9c-121">Responds to Wide World Importers with an invoice acknowledgment.</span></span>  

8. <span data-ttu-id="86a9c-122">從 Wide World Importers 接收付款確認。</span><span class="sxs-lookup"><span data-stu-id="86a9c-122">Receives a payment confirmation from Wide World Importers.</span></span>  

9. <span data-ttu-id="86a9c-123">將最後出貨確認傳送到訂單系統。</span><span class="sxs-lookup"><span data-stu-id="86a9c-123">Sends a final shipping confirmation to the ordering system.</span></span>  

   <span data-ttu-id="86a9c-124">此範例使用個別的 BizTalk 應用程式 (ShipperProcess) 來模擬 Wide World Importers。</span><span class="sxs-lookup"><span data-stu-id="86a9c-124">A separate BizTalk application (ShipperProcess) is used to simulate Wide World Importers for this sample.</span></span> <span data-ttu-id="86a9c-125">BPELShipping 應用程式使用 FILE 傳輸 (此傳輸使用常用檔案系統位置進行通訊) 與 ShipperProcess 通訊。</span><span class="sxs-lookup"><span data-stu-id="86a9c-125">The BPELShipping application communicates with ShipperProcess by using the FILE transport, which uses common file system locations for the communication.</span></span>  

## <a name="how-this-sample-is-designed-and-why"></a><span data-ttu-id="86a9c-126">此範例的設計方式和原因</span><span class="sxs-lookup"><span data-stu-id="86a9c-126">How This Sample is Designed and Why</span></span>  
 <span data-ttu-id="86a9c-127">供 Web 服務使用的 BPEL 是一種 XML 語言，可描述商務程序，以便讓想要使用 Web 服務進行業務往來的不同公司可以輕鬆共用此商務程序。</span><span class="sxs-lookup"><span data-stu-id="86a9c-127">BPEL for Web services is an XML-based language to describe the business process so that it can be easily shared across different companies who want to do business with each other using Web services.</span></span> <span data-ttu-id="86a9c-128">BPEL 描述如何在商務通訊協定層級處理商務程序，但未描述公司的內部程序，例如公司從合作對象收到訂單之後要如何處理訂單的步驟。</span><span class="sxs-lookup"><span data-stu-id="86a9c-128">BPEL describes how to handle the business process at the business protocol level, but it does not describe the internal process in a company, such as the steps a company would take to process a purchase order after receiving it from a partner.</span></span> <span data-ttu-id="86a9c-129">此範例依其設計可說明如何匯入 BPEL 和對應的 WSDL 檔案，並將它們轉換為協調流程，然後開始執行與合作對象之間的商務程序。</span><span class="sxs-lookup"><span data-stu-id="86a9c-129">This sample is designed to show you how to import BPEL and corresponding WSDL files, convert them into an orchestration, and then start to run the business process with the partner.</span></span>  

 <span data-ttu-id="86a9c-130">以下是逐步程序，顯示如何匯入 BPEL 和 WSDL 檔案，以及如何將它們轉換為協調流程，以和預先建置的 BizTalk 應用程式 (ShipperProcess) 進行互動。</span><span class="sxs-lookup"><span data-stu-id="86a9c-130">The following is the step-by-step procedure showing how to import the BPEL and WSDL files and convert them into an orchestration to interact with a prebuilt BizTalk application (ShipperProcess).</span></span> <span data-ttu-id="86a9c-131">如果您完成下列步驟，就不需要執行＜建置和初始化 BPELShipping 應用程式＞中的步驟。</span><span class="sxs-lookup"><span data-stu-id="86a9c-131">If you complete the following steps, you do not need to perform the steps described in "To build and initialize the BPELShipping application".</span></span>  

#### <a name="to-import-from-bpel-and-build-a-working-solution"></a><span data-ttu-id="86a9c-132">從 BPEL 匯入並建置有效的方案</span><span class="sxs-lookup"><span data-stu-id="86a9c-132">To import from BPEL and build a working solution</span></span>  

1. <span data-ttu-id="86a9c-133">在 Microsoft[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]上**檔案**功能表上，按一下 **新增**，然後按一下**專案**。</span><span class="sxs-lookup"><span data-stu-id="86a9c-133">In Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], on the **File** menu, click **New**, and then click **Project**.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="86a9c-134">完成此程序之前，您必須先設定 ShipperProcess 應用程式，以建立支援的程序和結構描述專案。</span><span class="sxs-lookup"><span data-stu-id="86a9c-134">Before completing this procedure, you must set up the ShipperProcess application to create the supporting processes and schema projects.</span></span>  

2. <span data-ttu-id="86a9c-135">在 **新的專案**對話方塊中，專案類型窗格中，選取**BizTalk （專案）**。</span><span class="sxs-lookup"><span data-stu-id="86a9c-135">In the **New Project** dialog box, in the Project Types pane, select **BizTalk (Projects)**.</span></span> <span data-ttu-id="86a9c-136">在 [範本] 窗格中，選取**BizTalk (Server) BPEL 匯入專案**。</span><span class="sxs-lookup"><span data-stu-id="86a9c-136">In the Templates pane, select **BizTalk (Server) BPEL Import Project**.</span></span>  

3. <span data-ttu-id="86a9c-137">在 **名稱**方塊中，輸入**BPELShipping**。</span><span class="sxs-lookup"><span data-stu-id="86a9c-137">In the **Name** box, enter **BPELShipping**.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="86a9c-138">如果您使用不同的名稱，可能會在進行最後一個繫結步驟時發生問題。</span><span class="sxs-lookup"><span data-stu-id="86a9c-138">If you use a different name, you may experience problems with the final binding step.</span></span>  

4. <span data-ttu-id="86a9c-139">選取專案的位置，然後按一下**確定**啟動 「 BPEL 匯入精靈 」。</span><span class="sxs-lookup"><span data-stu-id="86a9c-139">Select a location for the project, and then click **OK** to start the BPEL Import Wizard.</span></span>  

5. <span data-ttu-id="86a9c-140">在 [**歡迎**頁面上，按一下**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="86a9c-140">On the **Welcome** page, click **Next**.</span></span>  

6. <span data-ttu-id="86a9c-141">在 **選取 BPEL、 WSDL 與 XSD 檔案**頁面上，按一下**瀏覽**。</span><span class="sxs-lookup"><span data-stu-id="86a9c-141">On the **Select BPEL, WSDL, and XSD Files** page, click **Browse**.</span></span>  

7. <span data-ttu-id="86a9c-142">選取的所有檔案\<*範例路徑*\>\Orchestrations\BPELImport\BPELSource 資料夾中，按一下 **開啟**，然後按一下 **下一步**.</span><span class="sxs-lookup"><span data-stu-id="86a9c-142">Select all the files from the \<*Samples Path*\>\Orchestrations\BPELImport\BPELSource folder, click **Open**, and then click **Next**.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="86a9c-143">在此步驟中，您會選取 BPEL 和 WSDL 檔案，描述商務程序和 XSD 檔案來表示商務文件結構描述。</span><span class="sxs-lookup"><span data-stu-id="86a9c-143">In this step, you select the BPEL and WSDL files to describe the business process and the XSD files to represent the business document schemas.</span></span>  

8. <span data-ttu-id="86a9c-144">在 **選取用於叫用 Webservice 的 WSDL 檔案**頁面上，按一下**完成**。</span><span class="sxs-lookup"><span data-stu-id="86a9c-144">On the **Select WSDL Files for Invoked WebServices** page, click **Finish**.</span></span>  

9. <span data-ttu-id="86a9c-145">在「BPEL 匯入精靈」報告成功匯入後，關閉該精靈。</span><span class="sxs-lookup"><span data-stu-id="86a9c-145">After the BPEL Import Wizard reports a successful import, close the wizard.</span></span> <span data-ttu-id="86a9c-146">專案現已建立。</span><span class="sxs-lookup"><span data-stu-id="86a9c-146">The project is now created.</span></span>  

10. <span data-ttu-id="86a9c-147">在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]命令提示字元，變更目錄 (**cd**) 至專案位置。</span><span class="sxs-lookup"><span data-stu-id="86a9c-147">At the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] command prompt, change directory (**cd**) to the project location.</span></span>  

11. <span data-ttu-id="86a9c-148">執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="86a9c-148">Run the following command:</span></span>  

     <span data-ttu-id="86a9c-149">**sn – k BPELShipping.snk**</span><span class="sxs-lookup"><span data-stu-id="86a9c-149">**sn –k BPELShipping.snk**</span></span>  

12. <span data-ttu-id="86a9c-150">在 [方案總管] 中，以滑鼠右鍵按一下**BPELShipping**專案，然後再按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="86a9c-150">In Solution Explorer, right-click the **BPELShipping** project, and then click **Properties**.</span></span>  

13. <span data-ttu-id="86a9c-151">底下**Common Properties\Assembly**，選取組件金鑰檔案**BPELShipping.snk**步驟 11 中建立，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="86a9c-151">Under **Common Properties\Assembly**, select the assembly key file **BPELShipping.snk** created in step 11, and then click **OK**.</span></span>  

14. <span data-ttu-id="86a9c-152">在 [方案總管] 中選取所有的 .xsd 檔案，然後將其刪除。</span><span class="sxs-lookup"><span data-stu-id="86a9c-152">In Solution Explorer, select all the .xsd files and delete them.</span></span>  

15. <span data-ttu-id="86a9c-153">在 方案總管 中，選取**加入參考**，然後在**專案**索引標籤上，按一下 **瀏覽**。</span><span class="sxs-lookup"><span data-stu-id="86a9c-153">In Solution Explorer, select **Add Reference**, and on the **Projects** tab, click **Browse**.</span></span>  

16. <span data-ttu-id="86a9c-154">選取  **ShippingSchemas.dll**從位置\<*範例路徑*\>\Orchestrations\BPELImport\Solution\ShipperProcess\ShippingSchemas\bin\Development，及然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="86a9c-154">Select **ShippingSchemas.dll** from the location \<*Samples Path*\>\Orchestrations\BPELImport\Solution\ShipperProcess\ShippingSchemas\bin\Development, and then click **OK**.</span></span>  

    > [!NOTE]
    >  <span data-ttu-id="86a9c-155">＜建置和初始化 ShipperProcess 應用程式＞一節中包含如何建置此檔案的指示。</span><span class="sxs-lookup"><span data-stu-id="86a9c-155">The section "To build and initialize the ShipperProcess application" has instructions on how to build this.</span></span>  

17. <span data-ttu-id="86a9c-156">在 [方案總管] 中，按兩下 **[ordershippingprocess.bpel.odx]**。</span><span class="sxs-lookup"><span data-stu-id="86a9c-156">In Solution Explorer, double-click **OrderShippingProcess.bpel.odx**.</span></span>  

18. <span data-ttu-id="86a9c-157">在 **檢視**功能表上，選取**其他的 Windows/協調流程檢視**。</span><span class="sxs-lookup"><span data-stu-id="86a9c-157">On the **View** menu, select **Other Windows/Orchestration View**.</span></span>  

19. <span data-ttu-id="86a9c-158">在 協調流程檢視 視窗中，以滑鼠右鍵按一下**協調流程屬性**，然後按一下**屬性 視窗**。</span><span class="sxs-lookup"><span data-stu-id="86a9c-158">In the Orchestration View window, right-click **Orchestration Properties** and then click **Properties Window**.</span></span>  

20. <span data-ttu-id="86a9c-159">在 [屬性] 視窗中，設定**協調流程可匯出**屬性設**False**。</span><span class="sxs-lookup"><span data-stu-id="86a9c-159">In the Properties window, set the **Orchestration Exportable** property to **False**.</span></span>  

21. <span data-ttu-id="86a9c-160">在 [方案總管] 中，按兩下 **[ordershipping.wsdl.odx]**。</span><span class="sxs-lookup"><span data-stu-id="86a9c-160">In Solution Explorer, double-click **OrderShipping.wsdl.odx**.</span></span>  

22. <span data-ttu-id="86a9c-161">在 [協調流程檢視] 視窗中，依序展開**型別/多部分訊息類型**。</span><span class="sxs-lookup"><span data-stu-id="86a9c-161">In the Orchestration View window, expand **Types/Multipart Message Types**.</span></span>  

23. <span data-ttu-id="86a9c-162">依序展開 **[invoiceackmessagetype]** ，然後按一下 **[invoiceackmessagepart]**。</span><span class="sxs-lookup"><span data-stu-id="86a9c-162">Expand **InvoiceAckMessageType** and then click **InvoiceAckMessagePart**.</span></span>  

24. <span data-ttu-id="86a9c-163">在 [屬性] 視窗中，依序展開**型別**欄位，然後選取**從參考的組件的結構描述/選取**。</span><span class="sxs-lookup"><span data-stu-id="86a9c-163">In the Properties window, expand the **Type** field, and select **Schemas/Select from referenced Assembly**.</span></span>  

25. <span data-ttu-id="86a9c-164">在 **選取成品類型** 對話方塊中，按一下**ShippingSchemas**，選取**Imported_InvoiceAckMessage**輸入，然後再按一下**確定**.</span><span class="sxs-lookup"><span data-stu-id="86a9c-164">In the **Select Artifact Type** dialog box, click **ShippingSchemas**, select the **Imported_InvoiceAckMessage** type, and then click **OK**.</span></span>  

    > [!NOTE]
    >  <span data-ttu-id="86a9c-165">在步驟 23 到 25 中，您會將參與 BPEL 程序的服務訊息類型取代成 ShippingSchemas 中的對應訊息類型。</span><span class="sxs-lookup"><span data-stu-id="86a9c-165">In steps 23 through 25, you replace the message type of the services that participate in the BPEL process to the corresponding message types described in the ShippingSchemas.</span></span>  

26. <span data-ttu-id="86a9c-166">使用下列值對每個訊息類型重複步驟 23 到 25。</span><span class="sxs-lookup"><span data-stu-id="86a9c-166">Repeat steps 23 through 25 for each message type using the following values.</span></span>  


    |          <span data-ttu-id="86a9c-167">訊息部分</span><span class="sxs-lookup"><span data-stu-id="86a9c-167">Message part</span></span>          |                    <span data-ttu-id="86a9c-168">訊息類型</span><span class="sxs-lookup"><span data-stu-id="86a9c-168">Message type</span></span>                     |
    |--------------------------------|-----------------------------------------------------|
    |       <span data-ttu-id="86a9c-169">InvoiceMessagePart</span><span class="sxs-lookup"><span data-stu-id="86a9c-169">InvoiceMessagePart</span></span>       |       <span data-ttu-id="86a9c-170">ShippingSchemas.Imported_InvoiceMessage</span><span class="sxs-lookup"><span data-stu-id="86a9c-170">ShippingSchemas.Imported_InvoiceMessage</span></span>       |
    |      <span data-ttu-id="86a9c-171">OrderAckMessagePart</span><span class="sxs-lookup"><span data-stu-id="86a9c-171">OrderAckMessagePart</span></span>       |      <span data-ttu-id="86a9c-172">ShippingSchemas.Imported_OrderAckMessage</span><span class="sxs-lookup"><span data-stu-id="86a9c-172">ShippingSchemas.Imported_OrderAckMessage</span></span>       |
    |        <span data-ttu-id="86a9c-173">OrderMessagePart</span><span class="sxs-lookup"><span data-stu-id="86a9c-173">OrderMessagePart</span></span>        |        <span data-ttu-id="86a9c-174">ShippingSchemas.Imported_OrderMessage</span><span class="sxs-lookup"><span data-stu-id="86a9c-174">ShippingSchemas.Imported_OrderMessage</span></span>        |
    | <span data-ttu-id="86a9c-175">PaymentConfirmationMessagePart</span><span class="sxs-lookup"><span data-stu-id="86a9c-175">PaymentConfirmationMessagePart</span></span> | <span data-ttu-id="86a9c-176">ShippingSchemas.Imported_PaymentConfirmationMessage</span><span class="sxs-lookup"><span data-stu-id="86a9c-176">ShippingSchemas.Imported_PaymentConfirmationMessage</span></span> |
    | <span data-ttu-id="86a9c-177">PickupNotificationMessagePart</span><span class="sxs-lookup"><span data-stu-id="86a9c-177">PickupNotificationMessagePart</span></span>  | <span data-ttu-id="86a9c-178">ShippingSchemas.Imported_PickupNotificationMessage</span><span class="sxs-lookup"><span data-stu-id="86a9c-178">ShippingSchemas.Imported_PickupNotificationMessage</span></span>  |
    |  <span data-ttu-id="86a9c-179">ShipConfirmationMessagePart</span><span class="sxs-lookup"><span data-stu-id="86a9c-179">ShipConfirmationMessagePart</span></span>   |  <span data-ttu-id="86a9c-180">ShippingSchemas.Imported_ShipConfirmationMessage</span><span class="sxs-lookup"><span data-stu-id="86a9c-180">ShippingSchemas.Imported_ShipConfirmationMessage</span></span>   |
    |      <span data-ttu-id="86a9c-181">ShippingHistoryPart</span><span class="sxs-lookup"><span data-stu-id="86a9c-181">ShippingHistoryPart</span></span>       |      <span data-ttu-id="86a9c-182">ShippingSchemas.Imported_ShippingHistory</span><span class="sxs-lookup"><span data-stu-id="86a9c-182">ShippingSchemas.Imported_ShippingHistory</span></span>       |
    |   <span data-ttu-id="86a9c-183">ShipRequestAckMessagePart</span><span class="sxs-lookup"><span data-stu-id="86a9c-183">ShipRequestAckMessagePart</span></span>    |   <span data-ttu-id="86a9c-184">ShippingSchemas.Imported_ShipRequestAckMessage</span><span class="sxs-lookup"><span data-stu-id="86a9c-184">ShippingSchemas.Imported_ShipRequestAckMessage</span></span>    |
    |     <span data-ttu-id="86a9c-185">ShipRequestMessagePart</span><span class="sxs-lookup"><span data-stu-id="86a9c-185">ShipRequestMessagePart</span></span>     |     <span data-ttu-id="86a9c-186">ShippingSchemas.Imported_ShipRequestMessage</span><span class="sxs-lookup"><span data-stu-id="86a9c-186">ShippingSchemas.Imported_ShipRequestMessage</span></span>     |
    |     <span data-ttu-id="86a9c-187">ShipStatusMessagePart</span><span class="sxs-lookup"><span data-stu-id="86a9c-187">ShipStatusMessagePart</span></span>      |     <span data-ttu-id="86a9c-188">ShippingSchemas.Imported_ShipStatusMessage</span><span class="sxs-lookup"><span data-stu-id="86a9c-188">ShippingSchemas.Imported_ShipStatusMessage</span></span>      |


27. <span data-ttu-id="86a9c-189">在 [方案總管] 中，以滑鼠右鍵按一下**BPELShipping**專案，指向**新增**，然後按一下**現有項目**。</span><span class="sxs-lookup"><span data-stu-id="86a9c-189">In Solution Explorer, right-click the **BPELShipping** project, point to **Add**, and then click **Existing Item**.</span></span>  

28. <span data-ttu-id="86a9c-190">選取所有的.btm 檔案從位置\<*範例路徑*\>\Orchestrations\BPELImport\Solution\BPELShipping\BPELShipping。</span><span class="sxs-lookup"><span data-stu-id="86a9c-190">Select all the .btm files from the location \<*Samples Path*\>\Orchestrations\BPELImport\Solution\BPELShipping\BPELShipping.</span></span>  

29. <span data-ttu-id="86a9c-191">在 [協調流程檢視] 視窗中，找出**訊息指派**圖形為的 MessageAssignment_1 在 ConstructMessage1 中，並將它刪除。</span><span class="sxs-lookup"><span data-stu-id="86a9c-191">In the Orchestration View window, locate the **Message Assignment** shape named MessageAssignment_1 in ConstructMessage1 and delete it.</span></span>  

30. <span data-ttu-id="86a9c-192">從 [工具箱] 拖曳**轉換**圖形到 ConstructMessage1 圖形。</span><span class="sxs-lookup"><span data-stu-id="86a9c-192">From the Toolbox, drag a **Transform** shape into the ConstructMessage1 shape.</span></span>  

31. <span data-ttu-id="86a9c-193">在 [屬性] 視窗中，按一下 [省略符號按鈕 (**...**)，然後開啟**轉換組態**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="86a9c-193">In the Properties window, click the ellipsis button (**…**) and open the **Transform Configuration** dialog box.</span></span>  

32. <span data-ttu-id="86a9c-194">選取 **現有的對應**。</span><span class="sxs-lookup"><span data-stu-id="86a9c-194">Select **Existing Map**.</span></span>  

33. <span data-ttu-id="86a9c-195">選取 完整格式的對應名稱為**BPELShipping.Order2ShipRequest**。</span><span class="sxs-lookup"><span data-stu-id="86a9c-195">Select the fully qualified map name as **BPELShipping.Order2ShipRequest**.</span></span>  

34. <span data-ttu-id="86a9c-196">選取做為來源**順序。OrderMessagePart**。</span><span class="sxs-lookup"><span data-stu-id="86a9c-196">Select the source as **order.OrderMessagePart**.</span></span>  

35. <span data-ttu-id="86a9c-197">選取做為目的地**ship_request。ShipRequestMessagePart** ，按一下  **確定**。</span><span class="sxs-lookup"><span data-stu-id="86a9c-197">Select the destination as **ship_request.ShipRequestMessagePart** and click **OK**.</span></span>  

36. <span data-ttu-id="86a9c-198">針對每個重複步驟 29 到 35**訊息指派**圖形，並將其取代為**轉換**根據下表的圖形。</span><span class="sxs-lookup"><span data-stu-id="86a9c-198">Repeat steps 29 through 35 for each of the **Message Assignment** shapes and replace them with **Transform** shapes according to the following table.</span></span>  


    |  <span data-ttu-id="86a9c-199">要取代的圖形</span><span class="sxs-lookup"><span data-stu-id="86a9c-199">Shape to replace</span></span>   |              <span data-ttu-id="86a9c-200">要使用的對應</span><span class="sxs-lookup"><span data-stu-id="86a9c-200">Map to use</span></span>              |      <span data-ttu-id="86a9c-201">來源文件</span><span class="sxs-lookup"><span data-stu-id="86a9c-201">Source document</span></span>       |       <span data-ttu-id="86a9c-202">目的文件</span><span class="sxs-lookup"><span data-stu-id="86a9c-202">Destination document</span></span>        |
    |---------------------|--------------------------------------|----------------------------|-----------------------------------|
    | <span data-ttu-id="86a9c-203">MessageAssignment_2</span><span class="sxs-lookup"><span data-stu-id="86a9c-203">MessageAssignment_2</span></span> |     <span data-ttu-id="86a9c-204">BPELShipping.Order2OrderAck</span><span class="sxs-lookup"><span data-stu-id="86a9c-204">BPELShipping.Order2OrderAck</span></span>      |   <span data-ttu-id="86a9c-205">order.OrderMessagePart</span><span class="sxs-lookup"><span data-stu-id="86a9c-205">order.OrderMessagePart</span></span>   |   <span data-ttu-id="86a9c-206">order_ack.OrderAckMessagePart</span><span class="sxs-lookup"><span data-stu-id="86a9c-206">order_ack.OrderAckMessagePart</span></span>   |
    | <span data-ttu-id="86a9c-207">MessageAssignment_3</span><span class="sxs-lookup"><span data-stu-id="86a9c-207">MessageAssignment_3</span></span> |     <span data-ttu-id="86a9c-208">BPELShipping.Order2OrderNAck</span><span class="sxs-lookup"><span data-stu-id="86a9c-208">BPELShipping.Order2OrderNAck</span></span>     |   <span data-ttu-id="86a9c-209">order.OrderMessagePart</span><span class="sxs-lookup"><span data-stu-id="86a9c-209">order.OrderMessagePart</span></span>   |   <span data-ttu-id="86a9c-210">order_ack.OrderAckMessagePart</span><span class="sxs-lookup"><span data-stu-id="86a9c-210">order_ack.OrderAckMessagePart</span></span>   |
    | <span data-ttu-id="86a9c-211">MessageAssignment_4</span><span class="sxs-lookup"><span data-stu-id="86a9c-211">MessageAssignment_4</span></span> |    <span data-ttu-id="86a9c-212">BPELShipping.Order2ShipHistory</span><span class="sxs-lookup"><span data-stu-id="86a9c-212">BPELShipping.Order2ShipHistory</span></span>    |   <span data-ttu-id="86a9c-213">order.OrderMessagePart</span><span class="sxs-lookup"><span data-stu-id="86a9c-213">order.OrderMessagePart</span></span>   | <span data-ttu-id="86a9c-214">ship_history.ShippingHistoryPart</span><span class="sxs-lookup"><span data-stu-id="86a9c-214">ship_history.ShippingHistoryPart</span></span>  |
    | <span data-ttu-id="86a9c-215">MessageAssignment_5</span><span class="sxs-lookup"><span data-stu-id="86a9c-215">MessageAssignment_5</span></span> |  <span data-ttu-id="86a9c-216">BPELShipping.ShipHistory2Completed</span><span class="sxs-lookup"><span data-stu-id="86a9c-216">BPELShipping.ShipHistory2Completed</span></span>  |   <span data-ttu-id="86a9c-217">order.OrderMessagePart</span><span class="sxs-lookup"><span data-stu-id="86a9c-217">order.OrderMessagePart</span></span>   | <span data-ttu-id="86a9c-218">ship_history.ShippingHistoryPart</span><span class="sxs-lookup"><span data-stu-id="86a9c-218">ship_history.ShippingHistoryPart</span></span>  |
    | <span data-ttu-id="86a9c-219">MessageAssignment_6</span><span class="sxs-lookup"><span data-stu-id="86a9c-219">MessageAssignment_6</span></span> |       <span data-ttu-id="86a9c-220">BPELShipping.Invoice2Ack</span><span class="sxs-lookup"><span data-stu-id="86a9c-220">BPELShipping.Invoice2Ack</span></span>       | <span data-ttu-id="86a9c-221">invoice.InvoiceMessagePart</span><span class="sxs-lookup"><span data-stu-id="86a9c-221">invoice.InvoiceMessagePart</span></span> | <span data-ttu-id="86a9c-222">invoice_ack.InvoiceAckMessagePart</span><span class="sxs-lookup"><span data-stu-id="86a9c-222">invoice_ack.InvoiceAckMessagePart</span></span> |
    | <span data-ttu-id="86a9c-223">MessageAssignment_7</span><span class="sxs-lookup"><span data-stu-id="86a9c-223">MessageAssignment_7</span></span> | <span data-ttu-id="86a9c-224">BPELShipping.Order2FinalConfirmation</span><span class="sxs-lookup"><span data-stu-id="86a9c-224">BPELShipping.Order2FinalConfirmation</span></span> |   <span data-ttu-id="86a9c-225">order.OrderMessagePart</span><span class="sxs-lookup"><span data-stu-id="86a9c-225">order.OrderMessagePart</span></span>   | <span data-ttu-id="86a9c-226">order_shipped.OrderAckMessagePart</span><span class="sxs-lookup"><span data-stu-id="86a9c-226">order_shipped.OrderAckMessagePart</span></span> |


37. <span data-ttu-id="86a9c-227">儲存此協調流程。</span><span class="sxs-lookup"><span data-stu-id="86a9c-227">Save the orchestration.</span></span>  

38. <span data-ttu-id="86a9c-228">按兩下**Rule_1**中**決定**圖形**Decision_1**。</span><span class="sxs-lookup"><span data-stu-id="86a9c-228">Double-click **Rule_1** in the **Decide** shape **Decision_1**.</span></span>  

39. <span data-ttu-id="86a9c-229">在 [BizTalk 運算式編輯器] 中，將</span><span class="sxs-lookup"><span data-stu-id="86a9c-229">In BizTalk Expression Editor, replace</span></span>  

     <span data-ttu-id="86a9c-230">ship_request_ack(BPELShipping.Ship_Acknowledged) == true</span><span class="sxs-lookup"><span data-stu-id="86a9c-230">ship_request_ack(BPELShipping.Ship_Acknowledged) == true</span></span>  

     <span data-ttu-id="86a9c-231">取代為</span><span class="sxs-lookup"><span data-stu-id="86a9c-231">with</span></span>  

     <span data-ttu-id="86a9c-232">ship_request_ack(ShippingSchemas.Ship_Acknowledged) == true</span><span class="sxs-lookup"><span data-stu-id="86a9c-232">ship_request_ack(ShippingSchemas.Ship_Acknowledged) == true</span></span>  

40. <span data-ttu-id="86a9c-233">按兩下**迴圈**設為圖案**Loop_1**。</span><span class="sxs-lookup"><span data-stu-id="86a9c-233">Double-click the **Loop** shape named **Loop_1**.</span></span>  

41. <span data-ttu-id="86a9c-234">在 [BizTalk 運算式編輯器] 中，將</span><span class="sxs-lookup"><span data-stu-id="86a9c-234">In BizTalk Expression Editor, replace</span></span>  

     <span data-ttu-id="86a9c-235">ship_history(BPELShipping.Ship_Completed) == true</span><span class="sxs-lookup"><span data-stu-id="86a9c-235">ship_history(BPELShipping.Ship_Completed) == true</span></span>  

     <span data-ttu-id="86a9c-236">取代為</span><span class="sxs-lookup"><span data-stu-id="86a9c-236">with</span></span>  

     <span data-ttu-id="86a9c-237">ship_history(ShippingSchemas.Ship_Completed) == true</span><span class="sxs-lookup"><span data-stu-id="86a9c-237">ship_history(ShippingSchemas.Ship_Completed) == true</span></span>  

42. <span data-ttu-id="86a9c-238">按兩下**Rule_2**中**決定**圖形**rule_2**。</span><span class="sxs-lookup"><span data-stu-id="86a9c-238">Double-click **Rule_2** in the **Decide** shape **Decision_2**.</span></span>  

43. <span data-ttu-id="86a9c-239">在 [BizTalk 運算式編輯器] 中，將</span><span class="sxs-lookup"><span data-stu-id="86a9c-239">In BizTalk Expression Editor, replace</span></span>  

     <span data-ttu-id="86a9c-240">ship_status(BPELShipping.ShipStatus) == "DONE"</span><span class="sxs-lookup"><span data-stu-id="86a9c-240">ship_status(BPELShipping.ShipStatus) == "DONE"</span></span>  

     <span data-ttu-id="86a9c-241">取代為</span><span class="sxs-lookup"><span data-stu-id="86a9c-241">with</span></span>  

     <span data-ttu-id="86a9c-242">ship_status(ShippingSchemas.ShipStatus) == "DONE"</span><span class="sxs-lookup"><span data-stu-id="86a9c-242">ship_status(ShippingSchemas.ShipStatus) == "DONE"</span></span>  

44. <span data-ttu-id="86a9c-243">在 [協調流程] 檢視中，依序展開**類型/相互關聯類型**然後按一下***OrderCorrelationSet_Type\\***。</span><span class="sxs-lookup"><span data-stu-id="86a9c-243">In the Orchestration View, expand **Types/Correlation Types** and click ***OrderCorrelationSet_Type\\***.</span></span>  

45. <span data-ttu-id="86a9c-244">在 屬性 視窗中，按一下 省略符號按鈕 (**...**) 上**相互關聯屬性**。</span><span class="sxs-lookup"><span data-stu-id="86a9c-244">In the Properties window, click the ellipsis button (**…**) on **Correlation Properties**.</span></span>  

46. <span data-ttu-id="86a9c-245">在屬性窗格上相互關聯中，按一下 **[bpelshipping.orderid]**，然後按一下**移除**。</span><span class="sxs-lookup"><span data-stu-id="86a9c-245">In the Properties to correlate on pane, click **BPELShipping.OrderID**, and then click **Remove**.</span></span>  

47. <span data-ttu-id="86a9c-246">在 [可用的屬性] 窗格中，依序展開**出貨結構描述**，選取**訂單識別碼**，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="86a9c-246">In the Available Properties pane, expand **Shipping Schemas**, select **Order ID**, and then click **Add**.</span></span>  

48. <span data-ttu-id="86a9c-247">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="86a9c-247">Click **OK**.</span></span>  

49. <span data-ttu-id="86a9c-248">儲存所有檔案，然後建置方案。</span><span class="sxs-lookup"><span data-stu-id="86a9c-248">Save all the files and build the solution.</span></span>  

50. <span data-ttu-id="86a9c-249">部署該方案。</span><span class="sxs-lookup"><span data-stu-id="86a9c-249">Deploy the solution.</span></span>  

51. <span data-ttu-id="86a9c-250">瀏覽至位置\<*範例路徑*\>\Orchestrations\BPELImport\Solution\BPELShipping，然後按兩下**BindAndStartOnly.bat**繫結並啟動協調流程。</span><span class="sxs-lookup"><span data-stu-id="86a9c-250">Browse to the location \<*Samples Path*\>\Orchestrations\BPELImport\Solution\BPELShipping and double-click **BindAndStartOnly.bat** to bind and start the orchestration.</span></span>  

## <a name="where-to-find-this-sample"></a><span data-ttu-id="86a9c-251">可在何處找到此範例</span><span class="sxs-lookup"><span data-stu-id="86a9c-251">Where to Find This Sample</span></span>  
 <span data-ttu-id="86a9c-252">*\<範例路徑\>* \Orchestrations\BPELImport</span><span class="sxs-lookup"><span data-stu-id="86a9c-252">*\<Samples Path\>* \Orchestrations\BPELImport</span></span>  

 <span data-ttu-id="86a9c-253">下表顯示此範例中的檔案，並描述其用途。</span><span class="sxs-lookup"><span data-stu-id="86a9c-253">The following table shows the files in this sample and describes their purpose.</span></span>  

|<span data-ttu-id="86a9c-254">檔案</span><span class="sxs-lookup"><span data-stu-id="86a9c-254">File(s)</span></span>|<span data-ttu-id="86a9c-255">描述</span><span class="sxs-lookup"><span data-stu-id="86a9c-255">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="86a9c-256">BPELSource\InvoiceAckMessage.xsd</span><span class="sxs-lookup"><span data-stu-id="86a9c-256">BPELSource\InvoiceAckMessage.xsd</span></span>|<span data-ttu-id="86a9c-257">Invoice acknowledgment schema.</span><span class="sxs-lookup"><span data-stu-id="86a9c-257">Invoice acknowledgment schema.</span></span>|  
|<span data-ttu-id="86a9c-258">BPELSource\InvoiceMessage.xsd</span><span class="sxs-lookup"><span data-stu-id="86a9c-258">BPELSource\InvoiceMessage.xsd</span></span>|<span data-ttu-id="86a9c-259">發票結構描述。</span><span class="sxs-lookup"><span data-stu-id="86a9c-259">Invoice schema.</span></span>|  
|<span data-ttu-id="86a9c-260">BPELSource\OrderAckMessage.xsd</span><span class="sxs-lookup"><span data-stu-id="86a9c-260">BPELSource\OrderAckMessage.xsd</span></span>|<span data-ttu-id="86a9c-261">Order acknowledgment schema.</span><span class="sxs-lookup"><span data-stu-id="86a9c-261">Order acknowledgment schema.</span></span>|  
|<span data-ttu-id="86a9c-262">BPELSource\OrderHeader.xsd</span><span class="sxs-lookup"><span data-stu-id="86a9c-262">BPELSource\OrderHeader.xsd</span></span>|<span data-ttu-id="86a9c-263">訂單標頭結構描述。</span><span class="sxs-lookup"><span data-stu-id="86a9c-263">Order header schema.</span></span>|  
|<span data-ttu-id="86a9c-264">BPELSource\OrderMessage.xsd</span><span class="sxs-lookup"><span data-stu-id="86a9c-264">BPELSource\OrderMessage.xsd</span></span>|<span data-ttu-id="86a9c-265">訂單訊息結構描述。</span><span class="sxs-lookup"><span data-stu-id="86a9c-265">Order message schema.</span></span>|  
|<span data-ttu-id="86a9c-266">BPELSource\OrderShipping.wsdl</span><span class="sxs-lookup"><span data-stu-id="86a9c-266">BPELSource\OrderShipping.wsdl</span></span>|<span data-ttu-id="86a9c-267">BPEL 參考的 WSDL 檔案。</span><span class="sxs-lookup"><span data-stu-id="86a9c-267">WSDL file referred to by BPEL.</span></span>|  
|<span data-ttu-id="86a9c-268">BPELSource\OrderShippingProcess.bpel</span><span class="sxs-lookup"><span data-stu-id="86a9c-268">BPELSource\OrderShippingProcess.bpel</span></span>|<span data-ttu-id="86a9c-269">BPEL 程序流程。</span><span class="sxs-lookup"><span data-stu-id="86a9c-269">BPEL process flow.</span></span>|  
|<span data-ttu-id="86a9c-270">BPELSource\PaymentConfirmationMessage.xsd</span><span class="sxs-lookup"><span data-stu-id="86a9c-270">BPELSource\PaymentConfirmationMessage.xsd</span></span>|<span data-ttu-id="86a9c-271">付款確認訊息。</span><span class="sxs-lookup"><span data-stu-id="86a9c-271">Payment confirmation message.</span></span>|  
|<span data-ttu-id="86a9c-272">BPELSource\PickupNotificationMessage.xsd</span><span class="sxs-lookup"><span data-stu-id="86a9c-272">BPELSource\PickupNotificationMessage.xsd</span></span>|<span data-ttu-id="86a9c-273">取件通知訊息。</span><span class="sxs-lookup"><span data-stu-id="86a9c-273">Pickup notification message.</span></span>|  
|<span data-ttu-id="86a9c-274">BPELSource\ShipConfirmationMessage.xsd</span><span class="sxs-lookup"><span data-stu-id="86a9c-274">BPELSource\ShipConfirmationMessage.xsd</span></span>|<span data-ttu-id="86a9c-275">出貨確認訊息。</span><span class="sxs-lookup"><span data-stu-id="86a9c-275">Shipment confirmation message.</span></span>|  
|<span data-ttu-id="86a9c-276">BPELSource\ShippingHistory.xsd</span><span class="sxs-lookup"><span data-stu-id="86a9c-276">BPELSource\ShippingHistory.xsd</span></span>|<span data-ttu-id="86a9c-277">出貨歷程記錄文件。</span><span class="sxs-lookup"><span data-stu-id="86a9c-277">Shipping history document.</span></span>|  
|<span data-ttu-id="86a9c-278">BPELSource\ShipRequestAckMessage.xsd</span><span class="sxs-lookup"><span data-stu-id="86a9c-278">BPELSource\ShipRequestAckMessage.xsd</span></span>|<span data-ttu-id="86a9c-279">出貨要求通知。</span><span class="sxs-lookup"><span data-stu-id="86a9c-279">Ship request acknowledgment.</span></span>|  
|<span data-ttu-id="86a9c-280">BPELSource\ShipRequestMessage.xsd</span><span class="sxs-lookup"><span data-stu-id="86a9c-280">BPELSource\ShipRequestMessage.xsd</span></span>|<span data-ttu-id="86a9c-281">出貨要求訊息。</span><span class="sxs-lookup"><span data-stu-id="86a9c-281">Ship request message.</span></span>|  
|<span data-ttu-id="86a9c-282">BPELSource\ShipStatusMessage.xsd</span><span class="sxs-lookup"><span data-stu-id="86a9c-282">BPELSource\ShipStatusMessage.xsd</span></span>|<span data-ttu-id="86a9c-283">出貨狀態訊息。</span><span class="sxs-lookup"><span data-stu-id="86a9c-283">Ship status message.</span></span>|  
|<span data-ttu-id="86a9c-284">Solution\bindings\BPELBindings.xml</span><span class="sxs-lookup"><span data-stu-id="86a9c-284">Solution\bindings\BPELBindings.xml</span></span>|<span data-ttu-id="86a9c-285">指定 BPELShipping 協調流程之連接埠繫結的繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="86a9c-285">Binding file specifying port bindings for the BPELShipping orchestration.</span></span>|  
|<span data-ttu-id="86a9c-286">Solution\bindings\ShipperBindings.xml</span><span class="sxs-lookup"><span data-stu-id="86a9c-286">Solution\bindings\ShipperBindings.xml</span></span>|<span data-ttu-id="86a9c-287">指定 ShipperProcess 協調流程之連接埠繫結的繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="86a9c-287">Binding file specifying port bindings for the ShipperProcess orchestration.</span></span>|  
|<span data-ttu-id="86a9c-288">Solution\BPELShipping\BindAndStartOnly.bat</span><span class="sxs-lookup"><span data-stu-id="86a9c-288">Solution\BPELShipping\BindAndStartOnly.bat</span></span>|<span data-ttu-id="86a9c-289">在手動建置和部署 BPELImport 協調流程之後，用來繫結和啟動該協調流程的批次檔案。</span><span class="sxs-lookup"><span data-stu-id="86a9c-289">Batch file to use for binding and starting the BPELImport orchestration after it has been built manually and deployed.</span></span>|  
|<span data-ttu-id="86a9c-290">Solution\BPELShipping\cleanup.bat</span><span class="sxs-lookup"><span data-stu-id="86a9c-290">Solution\BPELShipping\cleanup.bat</span></span>|<span data-ttu-id="86a9c-291">用來移除 BPELShipping 程序的批次檔案。</span><span class="sxs-lookup"><span data-stu-id="86a9c-291">Batch file to use to remove the BPELShipping process.</span></span>|  
|<span data-ttu-id="86a9c-292">Solution\BPELShipping\Setup.bat</span><span class="sxs-lookup"><span data-stu-id="86a9c-292">Solution\BPELShipping\Setup.bat</span></span>|<span data-ttu-id="86a9c-293">用來安裝和啟動所安裝之 BPELShipping 範例的批次檔案。</span><span class="sxs-lookup"><span data-stu-id="86a9c-293">Batch file to use to install and start the provided BPELShipping sample.</span></span>|  
|<span data-ttu-id="86a9c-294">Solution\BPELShipping\BPELShipping.sln</span><span class="sxs-lookup"><span data-stu-id="86a9c-294">Solution\BPELShipping\BPELShipping.sln</span></span>|<span data-ttu-id="86a9c-295">預先建置的 BPELShipping 範例。</span><span class="sxs-lookup"><span data-stu-id="86a9c-295">The prebuilt BPELShipping sample.</span></span>|  
<span data-ttu-id="86a9c-296">olution\BPELShipping\BPELShipping\Invoice2Ack.btm</span><span class="sxs-lookup"><span data-stu-id="86a9c-296">olution\BPELShipping\BPELShipping\Invoice2Ack.btm</span></span>|<span data-ttu-id="86a9c-297">發票到發票通知的對應。</span><span class="sxs-lookup"><span data-stu-id="86a9c-297">Invoice to invoice acknowledgment map.</span></span>|  
|<span data-ttu-id="86a9c-298">Solution\BPELShipping\BPELShipping\Order2FinalConfirmation.btm</span><span class="sxs-lookup"><span data-stu-id="86a9c-298">Solution\BPELShipping\BPELShipping\Order2FinalConfirmation.btm</span></span>|<span data-ttu-id="86a9c-299">從訂單訊息轉換為最後出貨確認的對應。</span><span class="sxs-lookup"><span data-stu-id="86a9c-299">Map to convert from Order message to final shipment confirmation.</span></span>|  
|<span data-ttu-id="86a9c-300">Solution\BPELShipping\BPELShipping\Order2OrderAck.btm</span><span class="sxs-lookup"><span data-stu-id="86a9c-300">Solution\BPELShipping\BPELShipping\Order2OrderAck.btm</span></span>|<span data-ttu-id="86a9c-301">從訂單訊息轉換為訂單通知的對應。</span><span class="sxs-lookup"><span data-stu-id="86a9c-301">Map to convert from Order message to order acknowledgment.</span></span>|  
|<span data-ttu-id="86a9c-302">Solution\BPELShipping\BPELShipping\Order2OrderNack.btm</span><span class="sxs-lookup"><span data-stu-id="86a9c-302">Solution\BPELShipping\BPELShipping\Order2OrderNack.btm</span></span>|<span data-ttu-id="86a9c-303">從訂單訊息轉換為訂單負值通知的對應。</span><span class="sxs-lookup"><span data-stu-id="86a9c-303">Map to convert from Order message to order negative acknowledgment.</span></span>|  
|<span data-ttu-id="86a9c-304">Solution\BPELShipping\BPELShipping\Order2ShipHistory.btm</span><span class="sxs-lookup"><span data-stu-id="86a9c-304">Solution\BPELShipping\BPELShipping\Order2ShipHistory.btm</span></span>|<span data-ttu-id="86a9c-305">從訂單訊息轉換為出貨歷程記錄文件的對應。</span><span class="sxs-lookup"><span data-stu-id="86a9c-305">Map to convert from Order message to Shipping history document.</span></span>|  
|<span data-ttu-id="86a9c-306">Solution\BPELShipping\BPELShipping\Order2ShipRequest.btm</span><span class="sxs-lookup"><span data-stu-id="86a9c-306">Solution\BPELShipping\BPELShipping\Order2ShipRequest.btm</span></span>|<span data-ttu-id="86a9c-307">從訂單訊息轉換為訂單出貨要求的對應。</span><span class="sxs-lookup"><span data-stu-id="86a9c-307">Map to convert from Order message to order Shipping request.</span></span>|  
|<span data-ttu-id="86a9c-308">Solution\BPELShipping\BPELShipping\ShipRequest2Completed.btm</span><span class="sxs-lookup"><span data-stu-id="86a9c-308">Solution\BPELShipping\BPELShipping\ShipRequest2Completed.btm</span></span>|<span data-ttu-id="86a9c-309">設定要完成之出貨歷程記錄的對應。</span><span class="sxs-lookup"><span data-stu-id="86a9c-309">Map to set the Shipping history to completed.</span></span>|  
|<span data-ttu-id="86a9c-310">Solution\ShipperProcess\setup.bat</span><span class="sxs-lookup"><span data-stu-id="86a9c-310">Solution\ShipperProcess\setup.bat</span></span>|<span data-ttu-id="86a9c-311">建置、部署、繫結和啟動 ShipperProcess 協助程式協調流程及其連接埠的批次檔案。</span><span class="sxs-lookup"><span data-stu-id="86a9c-311">Batch file to build, deploy, bind, and start the ShipperProcess helper orchestration and its ports.</span></span>|  
|<span data-ttu-id="86a9c-312">Solution\ShipperProcess\cleanup.bat</span><span class="sxs-lookup"><span data-stu-id="86a9c-312">Solution\ShipperProcess\cleanup.bat</span></span>|<span data-ttu-id="86a9c-313">停止、取消登錄和解除部署 ShipperProcess 協助程式協調流程及其連接埠的批次檔案。</span><span class="sxs-lookup"><span data-stu-id="86a9c-313">Batch file to stop, unenlist, and undeploy the ShipperProcess helper orchestration and its ports.</span></span>|  

## <a name="building-and-initializing-this-sample"></a><span data-ttu-id="86a9c-314">建置和初始化此範例</span><span class="sxs-lookup"><span data-stu-id="86a9c-314">Building and Initializing This Sample</span></span>  
 <span data-ttu-id="86a9c-315">第一個步驟為建置和初始化用來模擬 Wide World Importers 的 ShipperProcess 應用程式。</span><span class="sxs-lookup"><span data-stu-id="86a9c-315">The first step is to build and initialize the ShipperProcess application used to simulate Wide World Importers.</span></span>  

#### <a name="to-build-and-initialize-the-shipperprocess-application"></a><span data-ttu-id="86a9c-316">建置和初始化 ShipperProcess 應用程式</span><span class="sxs-lookup"><span data-stu-id="86a9c-316">To build and initialize the ShipperProcess application</span></span>  

1. <span data-ttu-id="86a9c-317">開始**Visual Studio 命令提示字元**。</span><span class="sxs-lookup"><span data-stu-id="86a9c-317">Start **Visual Studio Command Prompt**.</span></span>  

2. <span data-ttu-id="86a9c-318">從[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]命令提示字元，變更目錄 (**cd**) 至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="86a9c-318">From the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] command prompt, change directory (**cd**) to the following folder:</span></span>  

    <span data-ttu-id="86a9c-319">*\<範例路徑\>* \Orchestrations\BPELImport\Solution\ShipperProcess</span><span class="sxs-lookup"><span data-stu-id="86a9c-319">*\<Samples Path\>* \Orchestrations\BPELImport\Solution\ShipperProcess</span></span>  

3. <span data-ttu-id="86a9c-320">執行檔案 Setup.bat，這會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="86a9c-320">Run the file Setup.bat, which performs the following actions:</span></span>  

   -   <span data-ttu-id="86a9c-321">建置 ShippingSchemas 專案，此專案包含用於 ShipperProcess 和 BPELShipping 程序中的結構描述</span><span class="sxs-lookup"><span data-stu-id="86a9c-321">Builds the ShippingSchemas project, which contains the schemas used in the ShipperProcess and the BPELShipping process</span></span>  

   -   <span data-ttu-id="86a9c-322">建置 ShipperProcess</span><span class="sxs-lookup"><span data-stu-id="86a9c-322">Builds the ShipperProcess</span></span>  

   -   <span data-ttu-id="86a9c-323">部署 ShippingSchemas 和 ShipperProcess 專案</span><span class="sxs-lookup"><span data-stu-id="86a9c-323">Deploys the ShippingSchemas and ShipperProcess projects</span></span>  

   -   <span data-ttu-id="86a9c-324">建立和繫結 ShipperProcess 使用的傳送和接收埠</span><span class="sxs-lookup"><span data-stu-id="86a9c-324">Creates and binds the send and receive ports used by ShipperProcess</span></span>  

   -   <span data-ttu-id="86a9c-325">啟動 ShipperProcess 使用的連接埠</span><span class="sxs-lookup"><span data-stu-id="86a9c-325">Starts the ports used by ShipperProcess</span></span>  

   -   <span data-ttu-id="86a9c-326">登錄和啟動 ShipperProcess 協調流程</span><span class="sxs-lookup"><span data-stu-id="86a9c-326">Enlists and starts the ShipperProcess orchestration</span></span>  

   <span data-ttu-id="86a9c-327">在嘗試執行此範例之前，您應該確認在建置和初始化程序期間沒有報告錯誤。</span><span class="sxs-lookup"><span data-stu-id="86a9c-327">You should confirm that no errors were reported during the build and initialization process before attempting to run this sample.</span></span> <span data-ttu-id="86a9c-328">下列一或多個警告可能會顯示；您可忽略這些警告。</span><span class="sxs-lookup"><span data-stu-id="86a9c-328">One or more of the following warnings may be displayed; you can ignore these.</span></span>  

```  
The 'http://contoso.org/samples/Fragments:XXXX' element is not declared. An error occurred at , (35, 16).  
<SAMPLE_LOCATION>\Orchestrations\BPELImport\Solution\ShipperProcess\ShipperProcess\ShipperProcess.odx(701,13): warning X4014: convoy processing will not occur -- check your protocol if you were expecting it  
<SAMPLE_LOCATION>\Samples\Orchestrations\BPELImport\Solution\ShipperProcess\ShipperProcess\ShipperProcess.odx(667,22): convoy found at 'activate receive(Receive_ShipOrder.Operation_1, Request, initialize Correl)'  
<SAMPLE_LOCATION>\Samples\Orchestrations\BPELImport\Solution\ShipperProcess\ShipperProcess\ShipperProcess.odx(701,13): and 'receive(ReceiveInvoiceAck.Operation_1, Invoice_Ack, Correl)'  
```  

> [!NOTE]
>  <span data-ttu-id="86a9c-329">如果您已完成＜從 BPEL 匯入並建置有效的解決方案＞中所述的步驟，就不需要執行下列步驟。</span><span class="sxs-lookup"><span data-stu-id="86a9c-329">You do not need to perform the following steps if you completed the steps described in "To import from BPEL and build a working solution."</span></span>  

#### <a name="to-build-and-initialize-the-bpelshipping-application"></a><span data-ttu-id="86a9c-330">建置和初始化 BPELShipping 應用程式</span><span class="sxs-lookup"><span data-stu-id="86a9c-330">To build and initialize the BPELShipping application</span></span>  

1. > [!WARNING]
   >  <span data-ttu-id="86a9c-331">然後再執行這些步驟，您必須完成上述標題為 < 建置和初始化 ShipperProcess 應用程式 」 步驟。</span><span class="sxs-lookup"><span data-stu-id="86a9c-331">Before executing these steps, you must complete the steps above entitled “To build and initialize the ShipperProcess application”.</span></span>  

    <span data-ttu-id="86a9c-332">從[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]命令提示字元，變更目錄 (**cd**) 至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="86a9c-332">From the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] command prompt, change directory (**cd**) to the following folder:</span></span>  

    <span data-ttu-id="86a9c-333">*\<範例路徑\>* \Orchestrations\BPELImport\Solution\BPELShipping</span><span class="sxs-lookup"><span data-stu-id="86a9c-333">*\<Samples Path\>* \Orchestrations\BPELImport\Solution\BPELShipping</span></span>  

2. <span data-ttu-id="86a9c-334">執行檔案 Setup.bat，這會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="86a9c-334">Run the file Setup.bat, which performs the following actions:</span></span>  

   -   <span data-ttu-id="86a9c-335">建置 BPELShipping 專案</span><span class="sxs-lookup"><span data-stu-id="86a9c-335">Builds the BPELShipping project</span></span>  

   -   <span data-ttu-id="86a9c-336">部署 BPELShipping 專案</span><span class="sxs-lookup"><span data-stu-id="86a9c-336">Deploys the BPELShipping project</span></span>  

   -   <span data-ttu-id="86a9c-337">建立和繫結 BPELShipping 程序使用的傳送和接收埠</span><span class="sxs-lookup"><span data-stu-id="86a9c-337">Creates and binds the send and receive ports used by the BPELShipping process</span></span>  

   -   <span data-ttu-id="86a9c-338">啟動 BPELShipping 程序使用的連接埠</span><span class="sxs-lookup"><span data-stu-id="86a9c-338">Starts the ports used by the BPELShipping process</span></span>  

   -   <span data-ttu-id="86a9c-339">登錄和啟動 BPELShipping 協調流程</span><span class="sxs-lookup"><span data-stu-id="86a9c-339">Enlists and starts the BPELShipping orchestration</span></span>  

## <a name="running-this-sample"></a><span data-ttu-id="86a9c-340">執行此範例</span><span class="sxs-lookup"><span data-stu-id="86a9c-340">Running This Sample</span></span>  

#### <a name="to-run-the-bpel-import-sample"></a><span data-ttu-id="86a9c-341">執行 BPEL 匯入範例</span><span class="sxs-lookup"><span data-stu-id="86a9c-341">To run the BPEL Import sample</span></span>  

1.  <span data-ttu-id="86a9c-342">複製**Order.xml**檔案*\<範例路徑\>* \Orchestrations\BPELImport\Solution 資料夾\<*範例路徑\>* \Orchestrations\BPELImport\Solution\Ports\ReceiveOrder 資料夾。</span><span class="sxs-lookup"><span data-stu-id="86a9c-342">Copy the **Order.xml** file from the *\<Samples Path\>* \Orchestrations\BPELImport\Solution folder to the \<*Samples Path\>* \Orchestrations\BPELImport\Solution\Ports\ReceiveOrder folder.</span></span>  

2.  <span data-ttu-id="86a9c-343">BPELShipping 協調流程收取為訂單從客戶訂單處理系統，此檔案跑遍出貨程序，並產生一個檔案中的每個\<*範例路徑*\>\Orchestrations\BPELImport\Solution\Ports\SendOrder 資料夾和\<*範例路徑*\>\Orchestrations\BPELImport\Solution\Ports\FinalConfirmation 資料夾。</span><span class="sxs-lookup"><span data-stu-id="86a9c-343">The BPELShipping orchestration picks up this file as an order from the customer order processing system, runs through the shipping process, and produces one file each in the \<*Samples Path*\>\Orchestrations\BPELImport\Solution\Ports\SendOrder folder and the \<*Samples Path*\>\Orchestrations\BPELImport\Solution\Ports\FinalConfirmation folder.</span></span> <span data-ttu-id="86a9c-344">這些檔案的名稱的格式是\< *MessageID*\>.xml，其中*\<MessageID\>* 產生來唯一識別的 GUID訊息。</span><span class="sxs-lookup"><span data-stu-id="86a9c-344">The format of the name of these files is \<*MessageID*\>.xml, where *\<MessageID\>* is the GUID generated to uniquely identify the message.</span></span>  

## <a name="uninstalling-this-sample"></a><span data-ttu-id="86a9c-345">解除安裝這個範例</span><span class="sxs-lookup"><span data-stu-id="86a9c-345">Uninstalling This Sample</span></span>  

#### <a name="to-uninstall-the-bpel-import-sample"></a><span data-ttu-id="86a9c-346">解除安裝 BPEL 匯入範例</span><span class="sxs-lookup"><span data-stu-id="86a9c-346">To uninstall the BPEL Import sample</span></span>  

1. <span data-ttu-id="86a9c-347">在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]命令提示字元，變更目錄 (**cd**) 來\<*範例路徑*\>\Orchestrations\BPELImport\BPELShipping。</span><span class="sxs-lookup"><span data-stu-id="86a9c-347">At a [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] command prompt, change directory (**cd**) to \<*Samples Path*\>\Orchestrations\BPELImport\BPELShipping.</span></span>  

2. <span data-ttu-id="86a9c-348">執行 Cleanup.bat。</span><span class="sxs-lookup"><span data-stu-id="86a9c-348">Run Cleanup.bat.</span></span>  

3. <span data-ttu-id="86a9c-349">瀏覽至\<*範例路徑*\>\Orchestrations\BPELImport\ShipperProcess。</span><span class="sxs-lookup"><span data-stu-id="86a9c-349">Browse to \<*Samples Path*\>\Orchestrations\BPELImport\ShipperProcess.</span></span>  

4. <span data-ttu-id="86a9c-350">執行 Cleanup.bat。</span><span class="sxs-lookup"><span data-stu-id="86a9c-350">Run Cleanup.bat.</span></span>  

## <a name="see-also"></a><span data-ttu-id="86a9c-351">另請參閱</span><span class="sxs-lookup"><span data-stu-id="86a9c-351">See Also</span></span>  
 [<span data-ttu-id="86a9c-352">協調流程 (BizTalk Server Samples 資料夾)</span><span class="sxs-lookup"><span data-stu-id="86a9c-352">Orchestrations (BizTalk Server Samples Folder)</span></span>](../core/orchestrations-biztalk-server-samples-folder.md)