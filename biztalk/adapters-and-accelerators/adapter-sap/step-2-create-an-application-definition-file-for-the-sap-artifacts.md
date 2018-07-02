---
title: 步驟 2： 建立 SAP 成品的應用程式定義檔案 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- application definition file, creating a
- Business Data Catalog Definition Editor
- Business Data Catalog
ms.assetid: d254b00e-dbeb-4167-ad57-6f0aa2e7a563
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 92e97a54a6818456efd2f4ac55ca7e2fc5bc7c35
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36970383"
---
# <a name="step-2-create-an-application-definition-file-for-the-sap-artifacts"></a><span data-ttu-id="5c0b0-102">步驟 2： 建立 SAP 成品的應用程式定義檔案</span><span class="sxs-lookup"><span data-stu-id="5c0b0-102">Step 2: Create an Application Definition File for the SAP Artifacts</span></span>
<span data-ttu-id="5c0b0-103">![步驟 4 之 2](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-2of4.gif "Step_2of4")</span><span class="sxs-lookup"><span data-stu-id="5c0b0-103">![Step 2 of 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-2of4.gif "Step_2of4")</span></span>  
  
 <span data-ttu-id="5c0b0-104">**若要完成的時間：** 15 分鐘</span><span class="sxs-lookup"><span data-stu-id="5c0b0-104">**Time to complete:** 15 minutes</span></span>  
  
 <span data-ttu-id="5c0b0-105">**目標：** Microsoft SharePoint Server 中的商務資料目錄 」 功能會公開，並併入入口網站中的資料列的商務 (LOB) 應用程式。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-105">**Objective:** The Business Data Catalog feature in Microsoft SharePoint Server exposes and incorporates data from line-of-business (LOB) applications into portals.</span></span> <span data-ttu-id="5c0b0-106">若要併入您的入口網站中的這項資料，您必須建置可取用 Microsoft Office SharePoint Server 的應用程式定義檔。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-106">To incorporate this data into your portal site, you must build an application definition file that Microsoft Office SharePoint Server can consume.</span></span>  
  
 <span data-ttu-id="5c0b0-107">Business Data Catalog Definition Editor 工具，適用於 Microsoft Office SharePoint Server 2007 SDK，可讓您的商務資料目錄中建立應用程式定義檔案。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-107">The Business Data Catalog Definition Editor tool, available with Microsoft Office SharePoint Server 2007 SDK,enables you to create an application definition file for the Business Data Catalog.</span></span> <span data-ttu-id="5c0b0-108">此工具會自動產生 XML 檔案定義檔，因此您不需要手動建立檔案的 xml 編輯器。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-108">This tool automatically generates an XML file for the definition file, so you do not need to manually create the file in an XML editor.</span></span>  
  
 <span data-ttu-id="5c0b0-109">Microsoft Office SharePoint Server 應用程式所建立的目的是：</span><span class="sxs-lookup"><span data-stu-id="5c0b0-109">The purpose of the Microsoft Office SharePoint Server application that you are creating is to:</span></span>  
  
- <span data-ttu-id="5c0b0-110">搜尋客戶名稱為主的 SAP 系統中的客戶。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-110">Search for a customer in the SAP system based on a customer name.</span></span>  
  
- <span data-ttu-id="5c0b0-111">從擷取的客戶清單中選取客戶並擷取客戶詳細資料。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-111">Select a customer from the list of fetched customers and retrieve the details for the customer.</span></span>  
  
- <span data-ttu-id="5c0b0-112">從擷取的客戶清單中選取客戶，並擷取客戶的銷售訂單。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-112">Select a customer from the list of fetched customers and retrieve the sales orders for the customer.</span></span>  
  
  <span data-ttu-id="5c0b0-113">針對每個這些需求，您必須完成一的組 「 商務資料目錄定義編輯器 」 工具中的工作。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-113">For each of these requirements, you must complete a set of tasks in the Business Data Catalog Definition Editor tool.</span></span> <span data-ttu-id="5c0b0-114">本主題提供有關如何執行這些工作的指示。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-114">This topic provides instructions on how to perform these tasks.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="5c0b0-115">必要條件</span><span class="sxs-lookup"><span data-stu-id="5c0b0-115">Prerequisites</span></span>  
  
-   <span data-ttu-id="5c0b0-116">請確定您已安裝 Microsoft Office SharePoint Server 2007 SDK 的一部分為商務資料目錄定義編輯器。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-116">Be sure that you have the Business Data Catalog Definition Editor installed as part of the Microsoft Office SharePoint Server 2007 SDK.</span></span> <span data-ttu-id="5c0b0-117">您可以下載從 SDK [ http://go.microsoft.com/fwlink/?LinkId=104130 ](http://go.microsoft.com/fwlink/?LinkId=104130)。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-117">You can download the SDK from [http://go.microsoft.com/fwlink/?LinkId=104130](http://go.microsoft.com/fwlink/?LinkId=104130).</span></span>  
  
-   <span data-ttu-id="5c0b0-118">發佈 WCF 服務中所述[步驟 1： 將 SAP 成品，做為 WCF 服務發佈](../../adapters-and-accelerators/adapter-sap/step-1-publish-the-sap-artifacts-as-a-wcf-service.md)。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-118">Publish the WCF service as described in [Step 1: Publish the SAP Artifacts as a WCF Service](../../adapters-and-accelerators/adapter-sap/step-1-publish-the-sap-artifacts-as-a-wcf-service.md).</span></span>  
  
## <a name="creating-an-application-definition-file"></a><span data-ttu-id="5c0b0-119">建立應用程式定義檔案</span><span class="sxs-lookup"><span data-stu-id="5c0b0-119">Creating an Application Definition File</span></span>  
 <span data-ttu-id="5c0b0-120">本主題提供逐步指示來建立 WCF 服務的應用程式定義檔。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-120">This topic provides step-by-step instructions to create an application definition file for the WCF service.</span></span>  
  
### <a name="connect-to-the-wcf-lob-service-and-create-entities"></a><span data-ttu-id="5c0b0-121">連線到 WCF LOB 服務，並建立實體</span><span class="sxs-lookup"><span data-stu-id="5c0b0-121">Connect to the WCF LOB Service, and Create Entities</span></span>  
 <span data-ttu-id="5c0b0-122">您必須連接至 WCF 服務，以擷取 Web 服務描述語言 (WSDL) 服務。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-122">You must connect to the WCF service to extract the Web Services Description Language (WSDL) for the service.</span></span> <span data-ttu-id="5c0b0-123">商務資料目錄定義編輯器會根據 WSDL、 擷取方法。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-123">From the WSDL, the Business Data Catalog Definition Editor extracts the methods.</span></span> <span data-ttu-id="5c0b0-124">這些方法可用來建立實體。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-124">These methods can be used to create entities.</span></span> <span data-ttu-id="5c0b0-125">對於此範例中，兩個實體建立，每個客戶和銷售訂單。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-125">For this example, two entities are created, one each for the customer and sales orders.</span></span>  
  
##### <a name="to-connect-to-the-wcf-service-and-create-entities"></a><span data-ttu-id="5c0b0-126">連接到 WCF 服務，並建立實體</span><span class="sxs-lookup"><span data-stu-id="5c0b0-126">To connect to the WCF service and create entities</span></span>  
  
1. <span data-ttu-id="5c0b0-127">啟動商務資料目錄定義編輯器。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-127">Start the Business Data Catalog Definition Editor.</span></span> <span data-ttu-id="5c0b0-128">在 **開始**功能表上，按一下**Microsoft Business Data Catalog Definition Editor**。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-128">On the **Start** menu, click **Microsoft Business Data Catalog Definition Editor**.</span></span>  
  
2. <span data-ttu-id="5c0b0-129">在工具列上，按一下**新增 LOB 系統**。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-129">On the toolbar, click **Add LOB System**.</span></span>  
  
3. <span data-ttu-id="5c0b0-130">在 [新增 LOB 系統] 視窗中，按一下**連接到 web 服務**。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-130">In the Add LOB System window, click **Connect to Webservice**.</span></span>  
  
4. <span data-ttu-id="5c0b0-131">在  **URL**方塊中，輸入 WCF 服務的 URL。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-131">In the **URL** box, type the URL for the WCF service.</span></span> <span data-ttu-id="5c0b0-132">這個 URL 必須以下列格式：</span><span class="sxs-lookup"><span data-stu-id="5c0b0-132">The URL must be in the following format:</span></span>  
  
   ```  
   https://<computer_name>/Customer_Order/Rfc.svc?wsdl  
   ```  
  
    <span data-ttu-id="5c0b0-133">其中 Rfc.svc 是 Rfc 合約建立的檔案。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-133">where Rfc.svc is the file created for the Rfc contract.</span></span>  
  
    <span data-ttu-id="5c0b0-134">當您測試是否成功，如本主題中所述發行 WCF 服務時，URL 是可用[步驟 1： 將 SAP 成品，做為 WCF 服務發佈](../../adapters-and-accelerators/adapter-sap/step-1-publish-the-sap-artifacts-as-a-wcf-service.md)。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-134">The URL is available when you test whether the WCF service is published successfully, as described in the topic [Step 1: Publish the SAP Artifacts as a WCF Service](../../adapters-and-accelerators/adapter-sap/step-1-publish-the-sap-artifacts-as-a-wcf-service.md).</span></span>  
  
5. <span data-ttu-id="5c0b0-135">按一下 **[連接]**。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-135">Click **Connect**.</span></span>  
  
6. <span data-ttu-id="5c0b0-136">若要查看您在 WCF 配接器服務開發精靈中選取的作業，請按一下**新增 Web 方法** 索引標籤。您會看到下列方法：</span><span class="sxs-lookup"><span data-stu-id="5c0b0-136">To see the operations you selected in the WCF Adapter Service Development Wizard, click the **Add Web Method** tab. You will see the following methods:</span></span>  
  
   - <span data-ttu-id="5c0b0-137">SD_RFC_CUSTOMER_GET</span><span class="sxs-lookup"><span data-stu-id="5c0b0-137">SD_RFC_CUSTOMER_GET</span></span>  
  
   - <span data-ttu-id="5c0b0-138">BAPI_SALESORDER_GETLIST</span><span class="sxs-lookup"><span data-stu-id="5c0b0-138">BAPI_SALESORDER_GETLIST</span></span>  
  
      <span data-ttu-id="5c0b0-139">![新增 web 方法至 BDC 應用程式](../../adapters-and-accelerators/adapter-sap/media/ea411db2-5cf4-4486-83da-57d3fc332448.gif "ea411db2-5cf4-4486-83da-57d3fc332448")</span><span class="sxs-lookup"><span data-stu-id="5c0b0-139">![Add web methods to the BDC application](../../adapters-and-accelerators/adapter-sap/media/ea411db2-5cf4-4486-83da-57d3fc332448.gif "ea411db2-5cf4-4486-83da-57d3fc332448")</span></span>  
  
     <span data-ttu-id="5c0b0-140">將方法拖曳至設計介面。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-140">Drag the methods to the Design Surface.</span></span> <span data-ttu-id="5c0b0-141">請確定您將這兩種作業拖曳到不同的實體。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-141">Make sure you drag both operations to the different entities.</span></span>  
  
     <span data-ttu-id="5c0b0-142">![建立 web 方法的實體](../../adapters-and-accelerators/adapter-sap/media/ce4e9bc3-1eae-43ae-8375-e44cf19aaffc.gif "ce4e9bc3-1eae-43ae-8375-e44cf19aaffc")</span><span class="sxs-lookup"><span data-stu-id="5c0b0-142">![Create entities for the web methods](../../adapters-and-accelerators/adapter-sap/media/ce4e9bc3-1eae-43ae-8375-e44cf19aaffc.gif "ce4e9bc3-1eae-43ae-8375-e44cf19aaffc")</span></span>  
  
7. <span data-ttu-id="5c0b0-143">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-143">Click **OK**.</span></span>  
  
8. <span data-ttu-id="5c0b0-144">在 **輸入 LOB 系統的名稱** 對話方塊中，輸入的名稱，在**LOB 系統名稱** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-144">In the **Enter the name for the LOB System** dialog box, type a name in the **LOB System Name** box.</span></span> <span data-ttu-id="5c0b0-145">針對此範例中，呼叫它**Customer_Order**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-145">For this example, call it **Customer_Order**, and then click **OK**.</span></span>  
  
9. <span data-ttu-id="5c0b0-146">在商務資料目錄定義編輯器中，兩個實體會列為**Entity0**並**Entity1**。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-146">In the Business Data Catalog Definition Editor, the two entities are listed as **Entity0** and **Entity1**.</span></span> <span data-ttu-id="5c0b0-147">為這些實體指定易記名稱。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-147">Give these entities friendly names.</span></span> <span data-ttu-id="5c0b0-148">重新命名實體針對至 SD_RFC_CUSTOMER_GET**客戶**，並將實體重新命名針對至 BAPI_SALESORDER_GETLIST **SalesOrder**。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-148">Rename the entity for SD_RFC_CUSTOMER_GET to **Customer**, and rename the entity for BAPI_SALESORDER_GETLIST to **SalesOrder**.</span></span> <span data-ttu-id="5c0b0-149">執行下列步驟來重新命名實體：</span><span class="sxs-lookup"><span data-stu-id="5c0b0-149">Perform the following steps to rename the entities:</span></span>  
  
    1.  <span data-ttu-id="5c0b0-150">依序展開**Customer_Order**節點，然後展開**實體**節點。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-150">Expand the **Customer_Order** node, and then expand the **Entities** node.</span></span>  
  
    2.  <span data-ttu-id="5c0b0-151">選取  **Entity0**節點。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-151">Select the **Entity0** node.</span></span>  
  
    3.  <span data-ttu-id="5c0b0-152">在 屬性 窗格中，輸入**客戶**中**名稱** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-152">In the Properties pane, type **Customer** in the **Name** box.</span></span>  
  
         <span data-ttu-id="5c0b0-153">![重新命名實體](../../adapters-and-accelerators/adapter-sap/media/4e83a036-3ab7-4f74-9f67-420574219d3d.gif "4e83a036-3ab7-4f74-9f67-420574219d3d")</span><span class="sxs-lookup"><span data-stu-id="5c0b0-153">![Rename the entity](../../adapters-and-accelerators/adapter-sap/media/4e83a036-3ab7-4f74-9f67-420574219d3d.gif "4e83a036-3ab7-4f74-9f67-420574219d3d")</span></span>  
  
    4.  <span data-ttu-id="5c0b0-154">選取  **Entity1**節點。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-154">Select the **Entity1** node.</span></span>  
  
    5.  <span data-ttu-id="5c0b0-155">在 屬性 窗格中，輸入**SalesOrder**中**名稱** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-155">In the Properties pane, type **SalesOrder** in the **Name** box.</span></span>  
  
### <a name="specify-user-name-and-password-headers-for-the-methods"></a><span data-ttu-id="5c0b0-156">指定使用者名稱和密碼標頭方法</span><span class="sxs-lookup"><span data-stu-id="5c0b0-156">Specify User Name and Password Headers for the Methods</span></span>  
 <span data-ttu-id="5c0b0-157">建立 WCF 服務時的所選的 Rfc SAP 系統中，您可以指定使用者名稱和密碼標頭做為端點行為組態的一部分。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-157">When creating a WCF service for the selected RFCs in the SAP system, you specified user name and password headers as part of the endpoint behavior configuration.</span></span> <span data-ttu-id="5c0b0-158">請參閱[步驟 1： 將 SAP 成品發佈為 WCF 服務](../../adapters-and-accelerators/adapter-sap/step-1-publish-the-sap-artifacts-as-a-wcf-service.md)。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-158">See [Step 1: Publish the SAP Artifacts as a WCF Service](../../adapters-and-accelerators/adapter-sap/step-1-publish-the-sap-artifacts-as-a-wcf-service.md).</span></span> <span data-ttu-id="5c0b0-159">您必須指定方法屬性相同的值。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-159">You must specify the same values for the method properties.</span></span>  
  
##### <a name="to-specify-user-name-and-password-headers"></a><span data-ttu-id="5c0b0-160">若要指定使用者名稱和密碼標頭</span><span class="sxs-lookup"><span data-stu-id="5c0b0-160">To specify user name and password headers</span></span>  
  
1.  <span data-ttu-id="5c0b0-161">新增 SD_RFC_CUSTOMER_GET 方法的使用者名稱和密碼標頭。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-161">Add the user name and password headers for the SD_RFC_CUSTOMER_GET method.</span></span>  
  
    1.  <span data-ttu-id="5c0b0-162">在 [中繼資料物件] 窗格中，依序展開**客戶**節點，然後展開**方法**節點。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-162">In the Metadata Objects pane, expand the **Customer** node, and then expand the **Methods** node.</span></span>  
  
    2.  <span data-ttu-id="5c0b0-163">按一下 [SD_RFC_CUSTOMER_GET] 節點中，並在 [屬性] 窗格中，按一下 [省略符號 （...） 按鈕，針對**屬性**] 方塊中。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-163">Click the SD_RFC_CUSTOMER_GET node, and in the Properties pane click the ellipsis (…) button against the **Properties** box.</span></span>  
  
    3.  <span data-ttu-id="5c0b0-164">在 PropertyView 集合編輯器 視窗中，按一下**新增**，然後在 屬性 窗格中，輸入**HttpHeaderUserName** for**名稱** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-164">In the PropertyView Collection Editor window, click **Add**, and in the Property pane, type **HttpHeaderUserName** for the **Name** box.</span></span> <span data-ttu-id="5c0b0-165">同樣地，輸入**MyUserHeader** for **PropertyValue**  方塊中。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-165">Similarly, type **MyUserHeader** for the **PropertyValue** box.</span></span> <span data-ttu-id="5c0b0-166">選取 [ **System.String** for**型別**] 方塊中。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-166">Select **System.String** for the **Type** box.</span></span>  
  
         <span data-ttu-id="5c0b0-167">![將屬性加入](../../adapters-and-accelerators/adapter-sap/media/9eef32ac-8a93-45dc-8d07-12b7dbf961ba.gif "9eef32ac-8a93-45dc-8d07-12b7dbf961ba")</span><span class="sxs-lookup"><span data-stu-id="5c0b0-167">![Add a property](../../adapters-and-accelerators/adapter-sap/media/9eef32ac-8a93-45dc-8d07-12b7dbf961ba.gif "9eef32ac-8a93-45dc-8d07-12b7dbf961ba")</span></span>  
  
    4.  <span data-ttu-id="5c0b0-168">在 PropertyView 集合編輯器 視窗中，按一下**新增**，然後在 屬性 窗格中，輸入**HttpHeaderPassword** for**名稱** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-168">In the PropertyView Collection Editor window, click **Add**, and in the Property pane, type **HttpHeaderPassword** for the **Name** box.</span></span> <span data-ttu-id="5c0b0-169">同樣地，輸入**MyPassHeader** for **PropertyValue**  方塊中。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-169">Similarly, type **MyPassHeader** for the **PropertyValue** box.</span></span> <span data-ttu-id="5c0b0-170">選取 [ **System.String** for**型別**] 方塊中。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-170">Select **System.String** for the **Type** box.</span></span>  
  
    5.  <span data-ttu-id="5c0b0-171">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-171">Click **OK**.</span></span>  
  
2.  <span data-ttu-id="5c0b0-172">新增 BAPI_SALESORDER_GETLIST 方法的使用者名稱和密碼標頭。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-172">Add the user name and password headers for the BAPI_SALESORDER_GETLIST method.</span></span>  
  
    1.  <span data-ttu-id="5c0b0-173">在 [中繼資料物件] 窗格中，依序展開**SalesOrder**節點，然後展開**方法**節點。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-173">In the Metadata Objects pane, expand the **SalesOrder** node, and then expand the **Methods** node.</span></span>  
  
    2.  <span data-ttu-id="5c0b0-174">按一下 [BAPI_SALESORDER_GETLIST] 節點中，並在 [屬性] 窗格中，按一下 [省略符號 （...） 按鈕，針對**屬性**] 方塊中。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-174">Click the BAPI_SALESORDER_GETLIST node, and in the Properties pane click the ellipsis (…) button against the **Properties** box.</span></span>  
  
    3.  <span data-ttu-id="5c0b0-175">在 PropertyView 集合編輯器 視窗中，按一下**新增**，然後在 屬性 窗格中，輸入**HttpHeaderUserName** for**名稱** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-175">In the PropertyView Collection Editor window, click **Add**, and in the Property pane, type **HttpHeaderUserName** for the **Name** box.</span></span> <span data-ttu-id="5c0b0-176">同樣地，輸入**MyUserHeader** for **PropertyValue**  方塊中。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-176">Similarly, type **MyUserHeader** for the **PropertyValue** box.</span></span> <span data-ttu-id="5c0b0-177">選取 [ **System.String** for**型別**] 方塊中。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-177">Select **System.String** for the **Type** box.</span></span>  
  
    4.  <span data-ttu-id="5c0b0-178">在 PropertyView 集合編輯器 視窗中，按一下**新增**，然後在 屬性 窗格中，輸入**HttpHeaderPassword** for**名稱** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-178">In the PropertyView Collection Editor window, click **Add**, and in the Property pane, type **HttpHeaderPassword** for the **Name** box.</span></span> <span data-ttu-id="5c0b0-179">同樣地，輸入**MyPassHeader** for **PropertyValue**  方塊中。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-179">Similarly, type **MyPassHeader** for the **PropertyValue** box.</span></span> <span data-ttu-id="5c0b0-180">選取 [ **System.String** for**型別**] 方塊中。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-180">Select **System.String** for the **Type** box.</span></span>  
  
    5.  <span data-ttu-id="5c0b0-181">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-181">Click **OK**.</span></span>  
  
### <a name="set-up-single-sign-on-for-connecting-to-the-sap-system"></a><span data-ttu-id="5c0b0-182">連線到 SAP 系統中設定單一登入設定</span><span class="sxs-lookup"><span data-stu-id="5c0b0-182">Set up Single Sign-On for Connecting to the SAP System</span></span>  
 <span data-ttu-id="5c0b0-183">執行本主題中的所有程序完成之後，您會建立可匯入 SharePoint 應用程式的應用程式定義檔。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-183">After you have finished performing all the procedures in this topic, you will have created an application definition file that can be imported into a SharePoint application.</span></span> <span data-ttu-id="5c0b0-184">從應用程式，您叫用來擷取相關的資料從 SAP 系統的 SAP 方法。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-184">From the application, you invoke the SAP methods to retrieve relevant data from the SAP system.</span></span> <span data-ttu-id="5c0b0-185">若要這麼做，您必須在 SharePoint 應用程式中建立 SAP 系統中的使用者與使用者之間的對應。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-185">To enable this, you must create a mapping between a user in the SAP system and the user in the SharePoint application.</span></span> <span data-ttu-id="5c0b0-186">您已匯入應用程式定義檔之後，您可以建立在 SharePoint 中央系統管理主控台中的這種對應。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-186">You create this mapping in SharePoint Central Administration console after you have imported the application definition file.</span></span>  
  
 <span data-ttu-id="5c0b0-187">不過，若要建立對應您必須設定屬性**SecondarySsoApplicationId**中商務資料目錄定義編輯器。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-187">However, to create the mapping you must set a property **SecondarySsoApplicationId** in the Business Data Catalog Definition Editor.</span></span>  
  
##### <a name="to-set-the-secondaryssoapplicationid-property"></a><span data-ttu-id="5c0b0-188">若要設定 SecondarySsoApplicationId 屬性</span><span class="sxs-lookup"><span data-stu-id="5c0b0-188">To set the SecondarySsoApplicationId property</span></span>  
  
1.  <span data-ttu-id="5c0b0-189">在 [中繼資料物件] 窗格中，依序展開**Customer_Order**節點，然後展開**執行個體**節點。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-189">In the Metadata Objects pane, expand the **Customer_Order** node, and then expand the **Instances** node.</span></span>  
  
2.  <span data-ttu-id="5c0b0-190">按一下  **Customer_Order_Instance**，並在 屬性 窗格中，按一下 省略符號 （...） 按鈕，針對**屬性** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-190">Click **Customer_Order_Instance**, and in the Properties pane, click the ellipsis (…) button against the **Properties** box.</span></span>  
  
3.  <span data-ttu-id="5c0b0-191">在 PropertyView 集合編輯器 視窗中，按一下**新增**，然後在 屬性 窗格中，輸入**SecondarySsoApplicationId** for**名稱** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-191">In the PropertyView Collection Editor window, click **Add**, and in the Property pane, type **SecondarySsoApplicationId** for the **Name** box.</span></span> <span data-ttu-id="5c0b0-192">同樣地，輸入**SAPSSO** for **PropertyValue**  方塊中。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-192">Similarly, type **SAPSSO** for the **PropertyValue** box.</span></span> <span data-ttu-id="5c0b0-193">選取 [ **System.String** for**型別**] 方塊中。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-193">Select **System.String** for the **Type** box.</span></span>  
  
     <span data-ttu-id="5c0b0-194">![新增 SSO 屬性](../../adapters-and-accelerators/adapter-sap/media/1eb813e4-fed2-45c2-8902-9af5dd3369bf.gif "1eb813e4-fed2-45c2-8902-9af5dd3369bf")</span><span class="sxs-lookup"><span data-stu-id="5c0b0-194">![Add the SSO property](../../adapters-and-accelerators/adapter-sap/media/1eb813e4-fed2-45c2-8902-9af5dd3369bf.gif "1eb813e4-fed2-45c2-8902-9af5dd3369bf")</span></span>  
  
4.  <span data-ttu-id="5c0b0-195">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-195">Click **OK**.</span></span>  
  
### <a name="requirement-1-search-for-customers-based-on-customer-name"></a><span data-ttu-id="5c0b0-196">需求 1： 客戶名稱為主的客戶搜尋</span><span class="sxs-lookup"><span data-stu-id="5c0b0-196">Requirement 1: Search for Customers Based on Customer Name</span></span>  
 <span data-ttu-id="5c0b0-197">若要建立可以用來搜尋客戶名稱為主的客戶應用程式定義檔，您必須執行下列一組工作。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-197">To create an application definition file that can be used to search for customers based on customer name, you must perform the following set of tasks.</span></span>  
  
-   <span data-ttu-id="5c0b0-198">在 SD_RFC_CUSTOMER_GET 方法中，建立篩選器，並將它對應至參數，其中儲存客戶的名稱。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-198">In the SD_RFC_CUSTOMER_GET method, create a filter and map it to the parameter that stores the customer name.</span></span>  
  
-   <span data-ttu-id="5c0b0-199">建立**Finder** SD_RFC_CUSTOMER_GET 方法的方法執行個體。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-199">Create a **Finder** method instance for the SD_RFC_CUSTOMER_GET method.</span></span> <span data-ttu-id="5c0b0-200">A **Finder**方法會擷取篩選為基礎的記錄清單。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-200">A **Finder** method retrieves a list of records based on a filter.</span></span>  
  
##### <a name="to-create-a-filter-and-map-it-to-the-customer-name-parameter"></a><span data-ttu-id="5c0b0-201">若要建立篩選器，並將它對應至客戶名稱參數</span><span class="sxs-lookup"><span data-stu-id="5c0b0-201">To create a filter, and map it to the customer name parameter</span></span>  
  
1.  <span data-ttu-id="5c0b0-202">建立篩選。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-202">Create a filter.</span></span>  
  
    1.  <span data-ttu-id="5c0b0-203">在 [中繼資料物件] 窗格中，依序展開**客戶**節點，然後展開**方法**節點。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-203">In the Metadata Objects pane, expand the **Customer** node, and then expand the **Methods** node.</span></span>  
  
    2.  <span data-ttu-id="5c0b0-204">展開 SD_RFC_CUSTOMER_GET 方法，以滑鼠右鍵按一下**篩選條件**，然後按一下**加入篩選**。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-204">Expand the SD_RFC_CUSTOMER_GET method, right-click **Filters**, and then click **Add Filter**.</span></span>  
  
         <span data-ttu-id="5c0b0-205">![將篩選新增至方法](../../adapters-and-accelerators/adapter-sap/media/23eaab24-66e4-486f-8f99-02a5e0fef984.gif "23eaab24-66e4-486f-8f99-02a5e0fef984")</span><span class="sxs-lookup"><span data-stu-id="5c0b0-205">![Add filter to a method](../../adapters-and-accelerators/adapter-sap/media/23eaab24-66e4-486f-8f99-02a5e0fef984.gif "23eaab24-66e4-486f-8f99-02a5e0fef984")</span></span>  
  
    3.  <span data-ttu-id="5c0b0-206">在 屬性 窗格中，輸入**CustomerName**中**名稱** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-206">In the Properties pane, type **CustomerName** in the **Name** box.</span></span>  
  
         <span data-ttu-id="5c0b0-207">![指定的名稱篩選條件](../../adapters-and-accelerators/adapter-sap/media/0a0d0f85-a16a-4969-a122-097355141c27.gif "0a0d0f85-a16a-4969-a122-097355141c27")</span><span class="sxs-lookup"><span data-stu-id="5c0b0-207">![Specify a name for the filter](../../adapters-and-accelerators/adapter-sap/media/0a0d0f85-a16a-4969-a122-097355141c27.gif "0a0d0f85-a16a-4969-a122-097355141c27")</span></span>  
  
    4.  <span data-ttu-id="5c0b0-208">針對**FilterType**屬性中，選取**WildcardFilter**。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-208">For the **FilterType** property, select **WildcardFilter**.</span></span>  
  
2.  <span data-ttu-id="5c0b0-209">若要將篩選器對應**NAME1** SD_RFC_CUSTOMER_GET 方法中的參數。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-209">Map the filter to the **NAME1** parameter in the SD_RFC_CUSTOMER_GET method.</span></span>  
  
    1.  <span data-ttu-id="5c0b0-210">在 [中繼資料物件] 窗格中，依序展開**客戶**節點，然後展開**方法**節點。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-210">In the Metadata Objects pane, expand the **Customer** node, and then expand the **Methods** node.</span></span>  
  
    2.  <span data-ttu-id="5c0b0-211">展開 SD_RFC_CUSTOMER_GET 方法，然後再展開**參數**節點。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-211">Expand the SD_RFC_CUSTOMER_GET method, and then expand the **Parameters** node.</span></span>  
  
    3.  <span data-ttu-id="5c0b0-212">依序展開**NAME1**節點，然後按一下第二個**NAME1**節點。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-212">Expand the **NAME1** node, and click the second **NAME1** node.</span></span> <span data-ttu-id="5c0b0-213">**NAME1**參數會包含客戶的名稱。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-213">The **NAME1** parameter contains the name of the customer.</span></span>  
  
    4.  <span data-ttu-id="5c0b0-214">在 [屬性] 窗格中，選取**CustomerName**從**FilterDescriptor**清單。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-214">In the Properties pane, select **CustomerName** from the **FilterDescriptor** list.</span></span>  
  
         <span data-ttu-id="5c0b0-215">![將篩選器對應至方法參數](../../adapters-and-accelerators/adapter-sap/media/6cc4ef85-503c-4847-95cb-633b902a715d.gif "6cc4ef85-503c-4847-95cb-633b902a715d")</span><span class="sxs-lookup"><span data-stu-id="5c0b0-215">![Map the filter to a method parameter](../../adapters-and-accelerators/adapter-sap/media/6cc4ef85-503c-4847-95cb-633b902a715d.gif "6cc4ef85-503c-4847-95cb-633b902a715d")</span></span>  
  
##### <a name="to-create-a-finder-method-instance-for-the-sdrfccustomerget-method"></a><span data-ttu-id="5c0b0-216">若要建立 Finder 方法執行個體 SD_RFC_CUSTOMER_GET 方法</span><span class="sxs-lookup"><span data-stu-id="5c0b0-216">To create a Finder method instance for the SD_RFC_CUSTOMER_GET method</span></span>  
  
1.  <span data-ttu-id="5c0b0-217">在 [中繼資料物件] 窗格中，依序展開**客戶**節點，然後展開**方法**節點。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-217">In the Metadata Objects pane, expand the **Customer** node, and then expand the **Methods** node.</span></span>  
  
2.  <span data-ttu-id="5c0b0-218">依序展開**SD_RFC_CUSTOMER_GET**節點，以滑鼠右鍵按一下**執行個體**，然後按一下**新增方法執行個體**以開啟 [建立方法執行個體] 視窗。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-218">Expand the **SD_RFC_CUSTOMER_GET** node, right-click **Instances**, and then click **Add Method Instance** to open the Create Method Instance window.</span></span>  
  
     <span data-ttu-id="5c0b0-219">![新增方法執行個體](../../adapters-and-accelerators/adapter-sap/media/f583f8ef-e364-4665-8514-db033219ba0b.gif "f583f8ef-e364-4665-8514-db033219ba0b")</span><span class="sxs-lookup"><span data-stu-id="5c0b0-219">![Add a method instance](../../adapters-and-accelerators/adapter-sap/media/f583f8ef-e364-4665-8514-db033219ba0b.gif "f583f8ef-e364-4665-8514-db033219ba0b")</span></span>  
  
3.  <span data-ttu-id="5c0b0-220">在 [建立方法執行個體] 視窗中，按一下**Finder** for**方法執行個體類型**。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-220">In the Create Method Instance window, click **Finder** for **Method Instance Type**.</span></span> <span data-ttu-id="5c0b0-221">選取  **CUSTOMER_T** for**的傳回 TypeDescriptor**。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-221">Select **CUSTOMER_T** for **Return TypeDescriptor**.</span></span>  
  
     <span data-ttu-id="5c0b0-222">![新增 Finder 方法執行個體](../../adapters-and-accelerators/adapter-sap/media/e9ae47f2-32f5-4586-8467-94e3713d2a06.gif "e9ae47f2-32f5-4586-8467-94e3713d2a06")</span><span class="sxs-lookup"><span data-stu-id="5c0b0-222">![Add a Finder method instance](../../adapters-and-accelerators/adapter-sap/media/e9ae47f2-32f5-4586-8467-94e3713d2a06.gif "e9ae47f2-32f5-4586-8467-94e3713d2a06")</span></span>  
  
4.  <span data-ttu-id="5c0b0-223">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-223">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="5c0b0-224">在 屬性 窗格中，輸入**GetCustomerByName_Instance**中**名稱** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-224">In the Properties pane, type **GetCustomerByName_Instance** in the **Name** box.</span></span>  
  
     <span data-ttu-id="5c0b0-225">![指定方法執行個體名稱](../../adapters-and-accelerators/adapter-sap/media/e44e02e8-b9fb-40ca-a55d-8bdc7ace02b5.gif "e44e02e8-b9fb-40ca-a55d-8bdc7ace02b5")</span><span class="sxs-lookup"><span data-stu-id="5c0b0-225">![Specify a name for the method instance](../../adapters-and-accelerators/adapter-sap/media/e44e02e8-b9fb-40ca-a55d-8bdc7ace02b5.gif "e44e02e8-b9fb-40ca-a55d-8bdc7ace02b5")</span></span>  
  
### <a name="requirement-2-retrieve-details-for-a-specific-customer-from-the-list-of-customers"></a><span data-ttu-id="5c0b0-226">需求 2： 擷取特定客戶從客戶清單的詳細資料</span><span class="sxs-lookup"><span data-stu-id="5c0b0-226">Requirement 2: Retrieve Details for a Specific Customer from the List of Customers</span></span>  
 <span data-ttu-id="5c0b0-227">若要建立可以用來搜尋客戶名稱為主的客戶應用程式定義檔，您必須執行下列一組工作。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-227">To create an application definition file that can be used to search for customers based on customer name, you must perform the following set of tasks.</span></span>  
  
-   <span data-ttu-id="5c0b0-228">在 SD_RFC_CUSTOMER_GET 方法中，建立識別項，並將它對應至參數，其中儲存客戶編號。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-228">In the SD_RFC_CUSTOMER_GET method, create an identifier, and map it to the parameter that stores the customer number.</span></span>  
  
-   <span data-ttu-id="5c0b0-229">建立**特定的 Finder** SD_RFC_CUSTOMER_GET 方法的方法執行個體。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-229">Create a **Specific Finder** method instance for the SD_RFC_CUSTOMER_GET method.</span></span> <span data-ttu-id="5c0b0-230">A**特定的 Finder**方法會尋找特定的記錄，根據識別項。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-230">A **Specific Finder** method finds a specific record based on an identifier.</span></span>  
  
##### <a name="to-create-an-identifier-and-map-it-to-the-customer-number-parameter"></a><span data-ttu-id="5c0b0-231">建立識別項，並將其對應至客戶的數字參數</span><span class="sxs-lookup"><span data-stu-id="5c0b0-231">To create an identifier, and map it to the customer number parameter</span></span>  
  
1.  <span data-ttu-id="5c0b0-232">建立的識別項**客戶**實體。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-232">Create an identifier for the **Customer** entity.</span></span>  
  
    1.  <span data-ttu-id="5c0b0-233">在 [中繼資料物件] 窗格中，依序展開**客戶**節點。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-233">In the Metadata Objects pane, expand the **Customer** node.</span></span>  
  
    2.  <span data-ttu-id="5c0b0-234">以滑鼠右鍵按一下**識別碼**節點，，然後選取**新增識別碼**。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-234">Right-click the **Identifiers** node, and then select **Add Identifier**.</span></span>  
  
         <span data-ttu-id="5c0b0-235">![新增識別碼至方法](../../adapters-and-accelerators/adapter-sap/media/3adeeda3-426c-41fe-8d5c-5ca5863fb430.gif "3adeeda3-426c-41fe-8d5c-5ca5863fb430")</span><span class="sxs-lookup"><span data-stu-id="5c0b0-235">![Add an identifier to a method](../../adapters-and-accelerators/adapter-sap/media/3adeeda3-426c-41fe-8d5c-5ca5863fb430.gif "3adeeda3-426c-41fe-8d5c-5ca5863fb430")</span></span>  
  
    3.  <span data-ttu-id="5c0b0-236">在 屬性 窗格中，輸入**CustomerID**中**名稱** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-236">In the Properties pane, type **CustomerID** in the **Name** box.</span></span>  
  
    4.  <span data-ttu-id="5c0b0-237">選取 [ **System.String** for**型別**] 方塊中。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-237">Select **System.String** for the **Type** box.</span></span>  
  
         <span data-ttu-id="5c0b0-238">![指定識別項的名稱](../../adapters-and-accelerators/adapter-sap/media/a2304bca-9a54-4d2b-ba9f-461cfaafccb0.gif "a2304bca-9a54-4d2b-ba9f-461cfaafccb0")</span><span class="sxs-lookup"><span data-stu-id="5c0b0-238">![Specify a name for the identifier](../../adapters-and-accelerators/adapter-sap/media/a2304bca-9a54-4d2b-ba9f-461cfaafccb0.gif "a2304bca-9a54-4d2b-ba9f-461cfaafccb0")</span></span>  
  
2.  <span data-ttu-id="5c0b0-239">將識別碼對應至 SD_RFC_CUSTOMER_GET 方法的索引鍵參數。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-239">Map the identifier to the key parameter for the SD_RFC_CUSTOMER_GET method.</span></span>  
  
    1.  <span data-ttu-id="5c0b0-240">在 [中繼資料物件] 窗格中，依序展開**客戶**節點，然後展開**方法**節點。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-240">In the Metadata Objects pane, expand the **Customer** node, and then expand the **Methods** node.</span></span>  
  
    2.  <span data-ttu-id="5c0b0-241">展開 SD_RFC_CUSTOMER_GET 方法，然後再展開**參數**節點。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-241">Expand the SD_RFC_CUSTOMER_GET method, and then expand the **Parameters** node.</span></span>  
  
    3.  <span data-ttu-id="5c0b0-242">依序展開**KUNNR**參數，然後按一下 第二個**KUNNR**節點。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-242">Expand the **KUNNR** parameter, and then click the second **KUNNR** node.</span></span>  
  
    4.  <span data-ttu-id="5c0b0-243">在 [屬性] 窗格中，選取**CustomerID [Customer]** 從**識別項**清單。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-243">In the Properties pane, select **CustomerID[Customer]** from the **Identifier** list.</span></span>  
  
         <span data-ttu-id="5c0b0-244">![將識別碼對應至參數](../../adapters-and-accelerators/adapter-sap/media/04ff6496-34a7-421b-ae9e-f9263895c153.gif "04ff6496-34a7-421b-ae9e-f9263895c153")</span><span class="sxs-lookup"><span data-stu-id="5c0b0-244">![Map the identifier to a parameter](../../adapters-and-accelerators/adapter-sap/media/04ff6496-34a7-421b-ae9e-f9263895c153.gif "04ff6496-34a7-421b-ae9e-f9263895c153")</span></span>  
  
3.  <span data-ttu-id="5c0b0-245">設定輸入和傳回參數之間的關聯。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-245">Set up an association between input and return parameters.</span></span>  
  
    1.  <span data-ttu-id="5c0b0-246">在 [中繼資料物件] 窗格中，依序展開**客戶**節點，然後展開**方法**節點。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-246">In the Metadata Objects pane, expand the **Customer** node, and then expand the **Methods** node.</span></span>  
  
    2.  <span data-ttu-id="5c0b0-247">展開 SD_RFC_CUSTOMER_GET 方法，然後再展開**參數**節點。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-247">Expand the SD_RFC_CUSTOMER_GET method, and then expand the **Parameters** node.</span></span>  
  
    3.  <span data-ttu-id="5c0b0-248">依序展開**CUSTOMER_T**節點，然後第二個**CUSTOMER_T**節點，然後在**項目**節點，然後再按一下**KUNNR**節點。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-248">Expand the **CUSTOMER_T** node, then the second **CUSTOMER_T** node, then the **Item** node, and then click the **KUNNR** node.</span></span>  
  
    4.  <span data-ttu-id="5c0b0-249">在 [屬性] 窗格中，選取**CustomerID [Customer]** 從**識別項**清單。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-249">In the Properties pane, select **CustomerID[Customer]** from the **Identifier** list.</span></span>  
  
##### <a name="to-create-a-specific-finder-method-instance-for-the-sdrfccustomerget-method"></a><span data-ttu-id="5c0b0-250">若要建立特定的 Finder 方法執行個體 SD_RFC_CUSTOMER_GET 方法</span><span class="sxs-lookup"><span data-stu-id="5c0b0-250">To create a Specific Finder method instance for the SD_RFC_CUSTOMER_GET method</span></span>  
  
1.  <span data-ttu-id="5c0b0-251">在 [中繼資料物件] 窗格中，依序展開**客戶**節點，然後**方法**節點。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-251">In the Metadata Objects pane, expand the **Customer** node, and then the **Methods** node.</span></span>  
  
2.  <span data-ttu-id="5c0b0-252">依序展開**SD_RFC_CUSTOMER_GET**節點，以滑鼠右鍵按一下**執行個體**，然後選取**新增方法執行個體**以開啟 [建立方法執行個體] 視窗。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-252">Expand the **SD_RFC_CUSTOMER_GET** node, right-click **Instances**, and then select **Add Method Instance** to open the Create Method Instance window.</span></span>  
  
     <span data-ttu-id="5c0b0-253">![新增方法執行個體](../../adapters-and-accelerators/adapter-sap/media/f583f8ef-e364-4665-8514-db033219ba0b.gif "f583f8ef-e364-4665-8514-db033219ba0b")</span><span class="sxs-lookup"><span data-stu-id="5c0b0-253">![Add a method instance](../../adapters-and-accelerators/adapter-sap/media/f583f8ef-e364-4665-8514-db033219ba0b.gif "f583f8ef-e364-4665-8514-db033219ba0b")</span></span>  
  
3.  <span data-ttu-id="5c0b0-254">在 [建立方法執行個體] 視窗中，選取**Specific Finder** for**方法執行個體類型**。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-254">In the Create Method Instance window, select **Specific Finder** for **Method Instance Type**.</span></span> <span data-ttu-id="5c0b0-255">同樣地，選取**CUSTOMER_T** for**傳回 TypeDescriptor**。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-255">Similarly, select **CUSTOMER_T** for **Return TypeDescriptor**.</span></span>  
  
     <span data-ttu-id="5c0b0-256">![新增 Specific Finder 方法執行個體](../../adapters-and-accelerators/adapter-sap/media/838eb512-b967-46e7-a865-0bf3651b02a1.gif "838eb512-b967-46e7-a865-0bf3651b02a1")</span><span class="sxs-lookup"><span data-stu-id="5c0b0-256">![Add a Specific Finder Method Instance](../../adapters-and-accelerators/adapter-sap/media/838eb512-b967-46e7-a865-0bf3651b02a1.gif "838eb512-b967-46e7-a865-0bf3651b02a1")</span></span>  
  
4.  <span data-ttu-id="5c0b0-257">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-257">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="5c0b0-258">在 屬性 窗格中，輸入**GetCustomerByNumber_Instance** for**名稱** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-258">In the Properties pane, type **GetCustomerByNumber_Instance** for the **Name** box.</span></span>  
  
     <span data-ttu-id="5c0b0-259">![指定方法執行個體名稱](../../adapters-and-accelerators/adapter-sap/media/970f543c-cd06-4921-86c9-c110abdc7994.gif "970f543c-cd06-4921-86c9-c110abdc7994")</span><span class="sxs-lookup"><span data-stu-id="5c0b0-259">![Specify a name for the method instance](../../adapters-and-accelerators/adapter-sap/media/970f543c-cd06-4921-86c9-c110abdc7994.gif "970f543c-cd06-4921-86c9-c110abdc7994")</span></span>  
  
### <a name="requirement-3-retrieve-sales-order-details-for-a-specific-customer-from-the-list-of-customers"></a><span data-ttu-id="5c0b0-260">需求 3： 擷取特定客戶從客戶清單的銷售訂單詳細資料</span><span class="sxs-lookup"><span data-stu-id="5c0b0-260">Requirement 3: Retrieve Sales Order Details for a Specific Customer from the List of Customers</span></span>  
 <span data-ttu-id="5c0b0-261">若要建立可用來擷取特定客戶的銷售訂單詳細資料的應用程式定義檔，您必須執行下列一組工作。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-261">To create an application definition file that can be used to retrieve sales order details for a specific customer, you must perform the following set of tasks.</span></span>  
  
-   <span data-ttu-id="5c0b0-262">設定之間的關聯**客戶**並**SalesOrder**實體。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-262">Set up an association between the **Customer** and **SalesOrder** entities.</span></span>  
  
-   <span data-ttu-id="5c0b0-263">建立**關聯**BAPI_SALESORDER_GETLIST 方法的方法。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-263">Create an **Association** method for the BAPI_SALESORDER_GETLIST method.</span></span>  
  
##### <a name="to-create-an-association-between-the-customer-and-salesorder-entities"></a><span data-ttu-id="5c0b0-264">若要建立客戶和 SalesOrder 實體之間的關聯</span><span class="sxs-lookup"><span data-stu-id="5c0b0-264">To create an association between the Customer and SalesOrder entities</span></span>  
  
1.  <span data-ttu-id="5c0b0-265">在 [中繼資料物件] 窗格中，依序展開**SalesOrder**節點，然後展開**方法**節點。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-265">In the Metadata Objects pane, expand the **SalesOrder** node, and then expand the **Methods** node.</span></span>  
  
2.  <span data-ttu-id="5c0b0-266">展開 BAPI_SALESORDER_GETLIST 方法，然後再展開**參數**節點。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-266">Expand the BAPI_SALESORDER_GETLIST method, and then expand the **Parameters** node.</span></span>  
  
3.  <span data-ttu-id="5c0b0-267">依序展開**CUSTOMER_NUMBER**節點，然後按一下 第二個**CUSTOMER_NUMBER**節點。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-267">Expand the **CUSTOMER_NUMBER** node, and then click the second **CUSTOMER_NUMBER** node.</span></span>  
  
4.  <span data-ttu-id="5c0b0-268">在 [屬性] 窗格中，選取**CustomerID [Customer]** 從**識別項**清單。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-268">In the Properties pane, select **CustomerID[Customer]** from the **Identifier** list.</span></span>  
  
     <span data-ttu-id="5c0b0-269">![建立兩個實體之間的關聯](../../adapters-and-accelerators/adapter-sap/media/ae7e1e7a-a12b-4905-b002-2a04c7050848.gif "ae7e1e7a-a12b-4905-b002-2a04c7050848")</span><span class="sxs-lookup"><span data-stu-id="5c0b0-269">![Create association between the two entities](../../adapters-and-accelerators/adapter-sap/media/ae7e1e7a-a12b-4905-b002-2a04c7050848.gif "ae7e1e7a-a12b-4905-b002-2a04c7050848")</span></span>  
  
##### <a name="to-create-an-association-method-instance-for-the-bapisalesordergetlist-method"></a><span data-ttu-id="5c0b0-270">若要建立 Association 方法執行個體 BAPI_SALESORDER_GETLIST 方法</span><span class="sxs-lookup"><span data-stu-id="5c0b0-270">To create an Association method instance for the BAPI_SALESORDER_GETLIST method</span></span>  
  
1.  <span data-ttu-id="5c0b0-271">在 [中繼資料物件] 窗格中，依序展開**SalesOrder**節點，然後展開**方法**節點。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-271">In the Metadata Objects pane, expand the **SalesOrder** node, and then expand the **Methods** node.</span></span>  
  
2.  <span data-ttu-id="5c0b0-272">依序展開**BAPI_SALESORDER_GETLIST**節點，以滑鼠右鍵按一下**執行個體**，然後選取**新增方法執行個體**以開啟 [建立方法執行個體] 視窗。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-272">Expand the **BAPI_SALESORDER_GETLIST** node, right-click **Instances**, and then select **Add Method Instance** to open the Create Method Instance window.</span></span>  
  
     <span data-ttu-id="5c0b0-273">![新增 Association 方法執行個體](../../adapters-and-accelerators/adapter-sap/media/c62a0d01-d4f3-470e-92f1-8a5cf666f8da.gif "c62a0d01-d4f3-470e-92f1-8a5cf666f8da")</span><span class="sxs-lookup"><span data-stu-id="5c0b0-273">![Add an Association Method Instance](../../adapters-and-accelerators/adapter-sap/media/c62a0d01-d4f3-470e-92f1-8a5cf666f8da.gif "c62a0d01-d4f3-470e-92f1-8a5cf666f8da")</span></span>  
  
3.  <span data-ttu-id="5c0b0-274">在 [建立方法執行個體] 視窗中，選取**關聯**for**方法執行個體類型**。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-274">In the Create Method Instance window, select **Association** for **Method Instance Type**.</span></span>  
  
4.  <span data-ttu-id="5c0b0-275">在 **來源實體**清單中，選取**客戶**。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-275">In the **Source Entities** list, select **Customer**.</span></span>  
  
5.  <span data-ttu-id="5c0b0-276">在 **傳回 TypeDescriptor**清單中，選取**SALES_ORDERS**...</span><span class="sxs-lookup"><span data-stu-id="5c0b0-276">In the **Return TypeDescriptor** list, select **SALES_ORDERS**..</span></span>  
  
     <span data-ttu-id="5c0b0-277">![建立 Association 方法執行個體](../../adapters-and-accelerators/adapter-sap/media/15975b78-8932-41ce-8c10-41891fc1fb22.gif "15975b78-8932-41ce-8c10-41891fc1fb22")</span><span class="sxs-lookup"><span data-stu-id="5c0b0-277">![Create an Association Method Instance](../../adapters-and-accelerators/adapter-sap/media/15975b78-8932-41ce-8c10-41891fc1fb22.gif "15975b78-8932-41ce-8c10-41891fc1fb22")</span></span>  
  
6.  <span data-ttu-id="5c0b0-278">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-278">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="5c0b0-279">在 屬性 窗格中，輸入**SalesOrderForCustomer_Instance** for**名稱** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-279">In the Properties pane, type **SalesOrderForCustomer_Instance** for the **Name** box.</span></span>  
  
     <span data-ttu-id="5c0b0-280">![指定 Association 方法的名稱](../../adapters-and-accelerators/adapter-sap/media/0f1d13e4-e5a3-49ec-92a7-6329c6db1eb0.gif "0f1d13e4-e5a3-49ec-92a7-6329c6db1eb0")</span><span class="sxs-lookup"><span data-stu-id="5c0b0-280">![Specify a name for the Association Method](../../adapters-and-accelerators/adapter-sap/media/0f1d13e4-e5a3-49ec-92a7-6329c6db1eb0.gif "0f1d13e4-e5a3-49ec-92a7-6329c6db1eb0")</span></span>  
  
### <a name="remove-parameters-of-systemnullable-type"></a><span data-ttu-id="5c0b0-281">移除 System.Nullable 類型的參數</span><span class="sxs-lookup"><span data-stu-id="5c0b0-281">Remove Parameters of System.Nullable Type</span></span>  
 <span data-ttu-id="5c0b0-282">在建立時**關聯**方法執行個體 BAPI_SALESORDER_GETLIST 方法中，您必須選取的傳回型別為 SALES_ORDERS。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-282">While creating the **Association** method instance for the BAPI_SALESORDER_GETLIST method, you selected the return type as SALES_ORDERS.</span></span> <span data-ttu-id="5c0b0-283">如果您展開 SALES_ORDER 參數時，您會發現某些參數屬於 System.Nullable 類型。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-283">If you expand the SALES_ORDER parameter, you will notice some parameters are of System.Nullable type.</span></span> <span data-ttu-id="5c0b0-284">您可以看到在商務資料目錄定義編輯器中，選取參數，並查看 值輸入參數**TypeName**屬性。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-284">You can see the parameter type by selecting the parameter in the Business Data Catalog Definition Editor, and looking at the value for the **TypeName** property.</span></span>  
  
 <span data-ttu-id="5c0b0-285">對於這類參數，商務資料目錄定義編輯器建立另一個參數具有相同名稱但加上"Specified"尾碼。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-285">For such parameters, the Business Data Catalog Definition Editor creates another parameter with the same name but with a “Specified” suffix.</span></span> <span data-ttu-id="5c0b0-286">例如，看看參數*ITM_NUMBER*並*ITM_NUMBERSpecified*。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-286">For example, look at parameters *ITM_NUMBER* and *ITM_NUMBERSpecified*.</span></span> <span data-ttu-id="5c0b0-287">Microsoft Office SharePoint Server 不支援 System.Nullable 參數。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-287">Microsoft Office SharePoint Server does not support System.Nullable parameters.</span></span> <span data-ttu-id="5c0b0-288">因此，當您嘗試包含 System.Nullable 參數類型的記錄時，它會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-288">So, when you try records that contain the System.Nullable parameter type, it throws an exception.</span></span> <span data-ttu-id="5c0b0-289">因此，您必須先移除兩個參數 （使用和不含"Specified"後置詞和具有相同名稱） 從商務資料目錄定義編輯器</span><span class="sxs-lookup"><span data-stu-id="5c0b0-289">Therefore, you must remove both the parameters (with and without the “Specified” suffix and having the same name) from the Business Data Catalog Definition Editor</span></span>  
  
##### <a name="to-remove-the-parameters-of-systemnullable-type"></a><span data-ttu-id="5c0b0-290">若要移除 System.Nullable 類型的參數</span><span class="sxs-lookup"><span data-stu-id="5c0b0-290">To remove the parameters of System.Nullable type</span></span>  
  
1.  <span data-ttu-id="5c0b0-291">在 [中繼資料物件] 窗格中，依序展開**SalesOrder**節點，然後展開**方法**節點。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-291">In the Metadata Objects pane, expand the **SalesOrder** node, and then expand the **Methods** node.</span></span>  
  
2.  <span data-ttu-id="5c0b0-292">依序展開**BAPI_SALESORDER_GETLIST**節點，然後展開**參數**節點。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-292">Expand the **BAPI_SALESORDER_GETLIST** node, and then expand the **Parameters** node.</span></span>  
  
3.  <span data-ttu-id="5c0b0-293">依序展開**SALES_ORDERS**，展開 第二個**SALES_ORDERS**，然後展開**項目**。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-293">Expand **SALES_ORDERS**, expand the second **SALES_ORDERS**, and then expand **Item**.</span></span>  
  
4.  <span data-ttu-id="5c0b0-294">以滑鼠右鍵按一下參數，其中包含在名稱中，"Specified"後的置詞，然後選取**刪除**。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-294">Right-click the parameter that contains the "Specified" suffix in the name, and then select **Delete**.</span></span>  
  
5.  <span data-ttu-id="5c0b0-295">以滑鼠右鍵按一下 已刪除，而不需要後置詞，參數名稱相同的參數，然後選取**刪除**。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-295">Right-click the parameter that has the same name as the parameter you deleted, without the suffix, and then select **Delete**.</span></span> <span data-ttu-id="5c0b0-296">一般而言，這個參數是正確"Specified"後置詞的參數之前。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-296">Typically, this parameter is right before the parameter that has the "Specified" suffix.</span></span>  
  
### <a name="set-default-parameters"></a><span data-ttu-id="5c0b0-297">設定預設參數</span><span class="sxs-lookup"><span data-stu-id="5c0b0-297">Set Default Parameters</span></span>  
 <span data-ttu-id="5c0b0-298">BAPI_SALESORDER_GETLIST 採用兩個參數。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-298">The BAPI_SALESORDER_GETLIST takes two parameters.</span></span> <span data-ttu-id="5c0b0-299">其中一個參數，TRANSACTION_GROUP，是預設參數。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-299">One of these parameters, TRANSACTION_GROUP, is the default parameter.</span></span> <span data-ttu-id="5c0b0-300">因此，您必須設定此參數的預設值。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-300">So, you must set the default value for this parameter.</span></span>  
  
##### <a name="to-set-the-default-value-for-transactiongroup"></a><span data-ttu-id="5c0b0-301">若要設定的預設值為 TRANSACTION_GROUP</span><span class="sxs-lookup"><span data-stu-id="5c0b0-301">To set the default value for TRANSACTION_GROUP</span></span>  
  
1.  <span data-ttu-id="5c0b0-302">在 [中繼資料物件] 窗格中，依序展開**SalesOrder**節點，然後展開**方法**節點。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-302">In the Metadata Objects pane, expand the **SalesOrder** node, and then expand the **Methods** node.</span></span>  
  
2.  <span data-ttu-id="5c0b0-303">依序展開**BAPI_SALESORDER_GETLIST**節點，然後展開**執行個體**節點。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-303">Expand the **BAPI_SALESORDER_GETLIST** node, and then expand the **Instances** node.</span></span>  
  
3.  <span data-ttu-id="5c0b0-304">選取  **SalesOrderForCustomer_Instance**方法執行個體，並在 屬性 窗格中，按一下 省略符號按鈕 （...），以對**DefaultValues**  方塊中。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-304">Select the **SalesOrderForCustomer_Instance** method instance, and in the Properties pane, click the ellipsis button (…) against the **DefaultValues** box.</span></span>  
  
4.  <span data-ttu-id="5c0b0-305">在 [編輯] 視窗中，依序展開**TRANSACTION_GROUP**節點，並針對**TRANSACTION_GROUP**方塊中，指定預設值 0。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-305">In the Edit window, expand **TRANSACTION_GROUP** node, and for the **TRANSACTION_GROUP** box, specify the default value 0.</span></span>  
  
     <span data-ttu-id="5c0b0-306">![指定方法執行個體的預設值](../../adapters-and-accelerators/adapter-sap/media/86e0a42d-61c0-4d5d-ba3f-55b328f79576.gif "86e0a42d-61c0-4d5d-ba3f-55b328f79576")</span><span class="sxs-lookup"><span data-stu-id="5c0b0-306">![Specify a default value for the method instance](../../adapters-and-accelerators/adapter-sap/media/86e0a42d-61c0-4d5d-ba3f-55b328f79576.gif "86e0a42d-61c0-4d5d-ba3f-55b328f79576")</span></span>  
  
5.  <span data-ttu-id="5c0b0-307">按一下 [ **關閉**]。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-307">Click **Close**.</span></span>  
  
### <a name="export-the-application-definition-to-a-file"></a><span data-ttu-id="5c0b0-308">匯出至檔案的應用程式定義</span><span class="sxs-lookup"><span data-stu-id="5c0b0-308">Export the Application Definition to a File</span></span>  
 <span data-ttu-id="5c0b0-309">您現在已建立應用程式定義，其中包含 SAP 系統的執行個體中繼資料。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-309">You have now created an application definition that contains the SAP system instance metadata.</span></span> <span data-ttu-id="5c0b0-310">您必須將此定義匯出至 XML 檔案，可匯入至 Microsoft Office SharePoint Server。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-310">You must export this definition to an XML file, which can be imported into Microsoft Office SharePoint Server.</span></span>  
  
##### <a name="to-export-the-application-definition-to-a-file"></a><span data-ttu-id="5c0b0-311">若要將應用程式定義匯出至檔案</span><span class="sxs-lookup"><span data-stu-id="5c0b0-311">To export the application definition to a file</span></span>  
  
1.  <span data-ttu-id="5c0b0-312">在 [中繼資料物件] 窗格中，以滑鼠右鍵按一下**Customer_Order**節點，然後再按一下**匯出**。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-312">In the Metadata Objects pane, right-click the **Customer_Order** node, and then click **Export**.</span></span>  
  
2.  <span data-ttu-id="5c0b0-313">將檔案儲存為 Customer_Order.xml 中。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-313">Save the file as Customer_Order.xml.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="5c0b0-314">後續步驟</span><span class="sxs-lookup"><span data-stu-id="5c0b0-314">Next Steps</span></span>  
 <span data-ttu-id="5c0b0-315">您現在必須建立 SharePoint 應用程式來擷取 SAP 系統中的資料。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-315">You must now create a SharePoint application to retrieve data from an SAP system.</span></span> <span data-ttu-id="5c0b0-316">請參閱[步驟 3： 建立 SharePoint 應用程式以擷取資料從 SAP](../../adapters-and-accelerators/adapter-sap/step-3-create-a-sharepoint-application-to-retrieve-data-from-sap.md)如需相關指示。</span><span class="sxs-lookup"><span data-stu-id="5c0b0-316">See [Step 3: Create a SharePoint Application to Retrieve Data from SAP](../../adapters-and-accelerators/adapter-sap/step-3-create-a-sharepoint-application-to-retrieve-data-from-sap.md) for instructions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c0b0-317">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5c0b0-317">See Also</span></span>  
 [<span data-ttu-id="5c0b0-318">教學課程 1：在 SharePoint 網站上呈現 SAP 系統的資料</span><span class="sxs-lookup"><span data-stu-id="5c0b0-318">Tutorial 1: Presenting Data from an SAP System on a SharePoint Site</span></span>](../../adapters-and-accelerators/adapter-sap/tutorial-1-presenting-data-from-an-sap-system-on-a-sharepoint-site.md)