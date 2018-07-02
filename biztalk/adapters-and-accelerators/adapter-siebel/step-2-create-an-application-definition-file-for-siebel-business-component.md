---
title: 步驟 2： 建立 Siebel 商務元件作業的應用程式定義檔案 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 75d34c48-0f2a-42e4-a60b-e04bcf2404e1
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c017d5e71cdd2a4281849647727364520ad77784
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36967615"
---
# <a name="step-2-create-an-application-definition-file-for-siebel-business-component-operations"></a><span data-ttu-id="515e1-102">步驟 2： 建立 Siebel 商務元件作業的應用程式定義檔案</span><span class="sxs-lookup"><span data-stu-id="515e1-102">Step 2: Create an Application Definition File for Siebel Business Component Operations</span></span>
<span data-ttu-id="515e1-103">![步驟 4 之 2](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-2of4.gif "Step_2of4")</span><span class="sxs-lookup"><span data-stu-id="515e1-103">![Step 2 of 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-2of4.gif "Step_2of4")</span></span>  
  
 <span data-ttu-id="515e1-104">**若要完成的時間：** 15 分鐘</span><span class="sxs-lookup"><span data-stu-id="515e1-104">**Time to complete:** 15 minutes</span></span>  
  
 <span data-ttu-id="515e1-105">**目標：** 商務資料目錄公開 （expose） 和入口網站中併入的營運 (LOB) 應用程式的資料。</span><span class="sxs-lookup"><span data-stu-id="515e1-105">**Objective:** The Business Data Catalog exposes and incorporates data from line-of-business (LOB) applications into portals.</span></span> <span data-ttu-id="515e1-106">若要併入您的入口網站中的這項資料，您必須建置可取用 Microsoft Office SharePoint Server 的應用程式定義檔。</span><span class="sxs-lookup"><span data-stu-id="515e1-106">To incorporate this data into your portal site, you must build an application definition file that Microsoft Office SharePoint Server can consume.</span></span>  
  
 <span data-ttu-id="515e1-107">Business Data Catalog Definition Editor 工具可讓您的商務資料目錄中建立應用程式定義檔案。</span><span class="sxs-lookup"><span data-stu-id="515e1-107">The Business Data Catalog Definition Editor tool enables you to create an application definition file for the Business Data Catalog.</span></span> <span data-ttu-id="515e1-108">此工具會自動產生的 XML 定義檔。</span><span class="sxs-lookup"><span data-stu-id="515e1-108">This tool automatically generates the XML for the definition file.</span></span> <span data-ttu-id="515e1-109">因此，您不必以手動方式建立檔案的 xml 編輯器。</span><span class="sxs-lookup"><span data-stu-id="515e1-109">Therefore, you do not have to manually create the file in an XML editor.</span></span>  
  
 <span data-ttu-id="515e1-110">Microsoft Office SharePoint Server 應用程式所建立的目的是執行帳戶的商務元件，以擷取記錄清單上的查詢作業。</span><span class="sxs-lookup"><span data-stu-id="515e1-110">The purpose of the Microsoft Office SharePoint Server application that you are creating is to perform a Query operation on the Account business component to retrieve a list of records.</span></span> <span data-ttu-id="515e1-111">若要這麼做，您必須完成一的組工作中商務資料目錄定義編輯器。</span><span class="sxs-lookup"><span data-stu-id="515e1-111">To achieve this, you must complete a set of tasks in the Business Data Catalog Definition Editor.</span></span> <span data-ttu-id="515e1-112">本主題提供有關如何執行這些工作的指示。</span><span class="sxs-lookup"><span data-stu-id="515e1-112">This topic provides instructions on how to perform these tasks.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="515e1-113">必要條件</span><span class="sxs-lookup"><span data-stu-id="515e1-113">Prerequisites</span></span>  
  
-   <span data-ttu-id="515e1-114">您必須安裝 Microsoft Office SharePoint Server 2007 SDK 的一部分為商務資料目錄定義編輯器。</span><span class="sxs-lookup"><span data-stu-id="515e1-114">You must have the Business Data Catalog Definition Editor installed as part of the Microsoft Office SharePoint Server 2007 SDK.</span></span> <span data-ttu-id="515e1-115">您可以下載從 SDK [ http://go.microsoft.com/fwlink/?LinkId=104130 ](http://go.microsoft.com/fwlink/?LinkId=104130)。</span><span class="sxs-lookup"><span data-stu-id="515e1-115">You can download the SDK from [http://go.microsoft.com/fwlink/?LinkId=104130](http://go.microsoft.com/fwlink/?LinkId=104130).</span></span>  
  
-   <span data-ttu-id="515e1-116">您應該已發佈 WCF 服務，如中所述[步驟 1： 發佈為 WCF 服務的 Siebel 商務元件操作](../../adapters-and-accelerators/adapter-siebel/step-1-publish-the-siebel-business-component-operations-as-a-wcf-service.md)。</span><span class="sxs-lookup"><span data-stu-id="515e1-116">You should have published the WCF service, as described in [Step 1: Publish the Siebel Business Component Operations as a WCF Service](../../adapters-and-accelerators/adapter-siebel/step-1-publish-the-siebel-business-component-operations-as-a-wcf-service.md).</span></span>  
  
## <a name="creating-an-application-definition-file"></a><span data-ttu-id="515e1-117">建立應用程式定義檔案</span><span class="sxs-lookup"><span data-stu-id="515e1-117">Creating an Application Definition File</span></span>  
 <span data-ttu-id="515e1-118">本節提供逐步指示來建立 WCF 服務的應用程式定義檔。</span><span class="sxs-lookup"><span data-stu-id="515e1-118">This section provides step-by-step instructions to create an application definition file for the WCF service.</span></span>  
  
### <a name="connect-to-the-wcf-service-and-create-entities"></a><span data-ttu-id="515e1-119">連線到 WCF 服務，並建立實體</span><span class="sxs-lookup"><span data-stu-id="515e1-119">Connect to the WCF Service, and Create Entities</span></span>  
 <span data-ttu-id="515e1-120">您必須連接至 WCF 服務，以擷取 Web 服務描述語言 (WSDL) 服務。</span><span class="sxs-lookup"><span data-stu-id="515e1-120">You must connect to the WCF service to extract the Web Services Description Language (WSDL) for the service.</span></span> <span data-ttu-id="515e1-121">商務資料目錄定義編輯器會根據 WSDL、 擷取方法。</span><span class="sxs-lookup"><span data-stu-id="515e1-121">From the WSDL, the Business Data Catalog Definition Editor extracts the methods.</span></span> <span data-ttu-id="515e1-122">這些方法可用來建立實體。</span><span class="sxs-lookup"><span data-stu-id="515e1-122">These methods can be used to create entities.</span></span> <span data-ttu-id="515e1-123">此範例中，您必須建立帳戶的商務元件上的查詢作業的一個實體。</span><span class="sxs-lookup"><span data-stu-id="515e1-123">For this example, you must create one entity for the Query operation on the Account business component.</span></span>  
  
##### <a name="to-connect-to-the-wcf-service-and-create-entities"></a><span data-ttu-id="515e1-124">若要連線到 WCF 服務，並建立實體</span><span class="sxs-lookup"><span data-stu-id="515e1-124">To connect to the WCF service, and create entities</span></span>  
  
1.  <span data-ttu-id="515e1-125">啟動商務資料目錄定義編輯器。</span><span class="sxs-lookup"><span data-stu-id="515e1-125">Start the Business Data Catalog Definition Editor.</span></span> <span data-ttu-id="515e1-126">在 **開始**功能表上，按一下**Microsoft Business Data Catalog Definition Editor**。</span><span class="sxs-lookup"><span data-stu-id="515e1-126">On the **Start** menu, click **Microsoft Business Data Catalog Definition Editor**.</span></span>  
  
2.  <span data-ttu-id="515e1-127">在工具中，按一下**新增 LOB 系統**。</span><span class="sxs-lookup"><span data-stu-id="515e1-127">In the tool, click **Add LOB System**.</span></span>  
  
3.  <span data-ttu-id="515e1-128">在 [新增 LOB 系統] 視窗中，按一下**連接到 web 服務**。</span><span class="sxs-lookup"><span data-stu-id="515e1-128">In the Add LOB System window, click **Connect to Webservice**.</span></span>  
  
4.  <span data-ttu-id="515e1-129">在 [URL] 方塊中，輸入 WCF 服務的 URL。</span><span class="sxs-lookup"><span data-stu-id="515e1-129">In the URL box, type the URL for the WCF service.</span></span> <span data-ttu-id="515e1-130">這個 URL 必須以下列格式：</span><span class="sxs-lookup"><span data-stu-id="515e1-130">The URL must be in the following format:</span></span>  
  
    ```  
    https://<computer_name>/Siebel_Account/BusinessObjects_Account_Account_Operation.svc?wsdl  
    ```  
  
     <span data-ttu-id="515e1-131">其中，BusinessObjects_Account_Account_Operation.svc 是建立 Siebel 合約的服務檔案。</span><span class="sxs-lookup"><span data-stu-id="515e1-131">where, BusinessObjects_Account_Account_Operation.svc is the service file created for the Siebel contract.</span></span>  
  
     <span data-ttu-id="515e1-132">您必須輸入的 URL 時，使用您要測試是否 WCF 服務發佈成功，如中所述[步驟 1： 發佈為 WCF 服務的 Siebel 商務元件操作](../../adapters-and-accelerators/adapter-siebel/step-1-publish-the-siebel-business-component-operations-as-a-wcf-service.md)。</span><span class="sxs-lookup"><span data-stu-id="515e1-132">The URL that you must type is available when you test whether the WCF service is published successfully, as described in [Step 1: Publish the Siebel Business Component Operations as a WCF Service](../../adapters-and-accelerators/adapter-siebel/step-1-publish-the-siebel-business-component-operations-as-a-wcf-service.md).</span></span>  
  
5.  <span data-ttu-id="515e1-133">按一下 **[連接]**。</span><span class="sxs-lookup"><span data-stu-id="515e1-133">Click **Connect**.</span></span>  
  
6.  <span data-ttu-id="515e1-134">按一下 **新增 Web 方法**索引標籤，查看您在 WCF 配接器服務開發精靈中選取的作業。</span><span class="sxs-lookup"><span data-stu-id="515e1-134">Click the **Add Web Method** tab to see the operations you selected in the WCF Adapter Service Development Wizard.</span></span> <span data-ttu-id="515e1-135">您會看到**查詢**方法。</span><span class="sxs-lookup"><span data-stu-id="515e1-135">You will see the **Query** method.</span></span>  
  
     <span data-ttu-id="515e1-136">![新增 web 方法至 BDC 應用程式](../../adapters-and-accelerators/adapter-siebel/media/f9505cd3-67e3-4f99-b189-d010322a3137.gif "f9505cd3-67e3-4f99-b189-d010322a3137")</span><span class="sxs-lookup"><span data-stu-id="515e1-136">![Add web methods to BDC application](../../adapters-and-accelerators/adapter-siebel/media/f9505cd3-67e3-4f99-b189-d010322a3137.gif "f9505cd3-67e3-4f99-b189-d010322a3137")</span></span>  
  
7.  <span data-ttu-id="515e1-137">拖曳**查詢**方法至設計介面，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="515e1-137">Drag the **Query** method to the design surface and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="515e1-138">在 **輸入 LOB 系統的名稱** 對話方塊中，輸入的名稱，在**LOB 系統名稱** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="515e1-138">In the **Enter the name for the LOB System** dialog box, type a name in the **LOB System Name** box.</span></span> <span data-ttu-id="515e1-139">此範例中，輸入`Siebel_Account`，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="515e1-139">For this example, type `Siebel_Account`, and then click **OK**.</span></span> <span data-ttu-id="515e1-140">實體， **Entity0**，會建立在商務資料目錄定義編輯器。</span><span class="sxs-lookup"><span data-stu-id="515e1-140">An entity, **Entity0**, is created in the Business Data Catalog Definition Editor.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="515e1-141">Business Data Catalog Definition Editor 工具不會處理列舉的資料類型。</span><span class="sxs-lookup"><span data-stu-id="515e1-141">The Business Data Catalog Definition Editor tool does not handle enumerated data types.</span></span> <span data-ttu-id="515e1-142">直到它遇到列舉的資料類型，並忽略其餘的欄位中，因此，商務資料目錄定義編輯器工具會匯入的欄位。</span><span class="sxs-lookup"><span data-stu-id="515e1-142">So, the Business Data Catalog Definition Editor tool imports the fields till it encounters an enumerated data type and ignores the remaining fields.</span></span> <span data-ttu-id="515e1-143">Business Data Catalog Definition Editor 工具也會顯示錯誤。</span><span class="sxs-lookup"><span data-stu-id="515e1-143">The Business Data Catalog Definition Editor tool also gives an error.</span></span> <span data-ttu-id="515e1-144">您可以忽略此錯誤，並依序按一下 [確定] 繼續進行。</span><span class="sxs-lookup"><span data-stu-id="515e1-144">You can ignore this error and proceed by clicking OK.</span></span> <span data-ttu-id="515e1-145">您可以手動新增必要的欄位在應用程式定義檔中在稍後的階段。</span><span class="sxs-lookup"><span data-stu-id="515e1-145">You can manually add the required fields in the application definition file at a later stage.</span></span>  
  
9. <span data-ttu-id="515e1-146">變更實體名稱，以使用更多的易記名稱。</span><span class="sxs-lookup"><span data-stu-id="515e1-146">Change the entity names to use more friendly names.</span></span> <span data-ttu-id="515e1-147">此範例中，變更**Entity0**要**帳戶**。</span><span class="sxs-lookup"><span data-stu-id="515e1-147">For this example, change **Entity0** to **Account**.</span></span>  
  
    1.  <span data-ttu-id="515e1-148">依序展開**Siebel_Account**節點，然後展開**實體**節點。</span><span class="sxs-lookup"><span data-stu-id="515e1-148">Expand the **Siebel_Account** node, and then expand the **Entities** node.</span></span>  
  
    2.  <span data-ttu-id="515e1-149">選取  **Entity0**節點。</span><span class="sxs-lookup"><span data-stu-id="515e1-149">Select the **Entity0** node.</span></span>  
  
    3.  <span data-ttu-id="515e1-150">在 [屬性] 窗格中，輸入**帳號**中**名稱**欄位。</span><span class="sxs-lookup"><span data-stu-id="515e1-150">In the Properties pane, type **Account** in the **Name** field.</span></span>  
  
         <span data-ttu-id="515e1-151">![重新命名實體](../../adapters-and-accelerators/adapter-siebel/media/44eda1de-b348-4421-9c51-0355b51f4a90.gif "44eda1de-b348-4421-9c51-0355b51f4a90")</span><span class="sxs-lookup"><span data-stu-id="515e1-151">![Rename the entity](../../adapters-and-accelerators/adapter-siebel/media/44eda1de-b348-4421-9c51-0355b51f4a90.gif "44eda1de-b348-4421-9c51-0355b51f4a90")</span></span>  
  
### <a name="specify-user-name-and-password-headers-for-methods"></a><span data-ttu-id="515e1-152">指定使用者名稱和密碼標頭方法</span><span class="sxs-lookup"><span data-stu-id="515e1-152">Specify User Name and Password Headers for Methods</span></span>  
 <span data-ttu-id="515e1-153">建立 WCF 服務時選取的商務元件作業在 Siebel 系統中，您會指定使用者名稱和密碼標頭為端點行為組態的一部分 ([步驟 1： 將 Siebel 商務元件作業發佈做為 WCF 服務](../../adapters-and-accelerators/adapter-siebel/step-1-publish-the-siebel-business-component-operations-as-a-wcf-service.md))。</span><span class="sxs-lookup"><span data-stu-id="515e1-153">When creating a WCF service for the selected business component operations in the Siebel system, you specified user name and password headers as part of the endpoint behavior configuration ([Step 1: Publish the Siebel Business Component Operations as a WCF Service](../../adapters-and-accelerators/adapter-siebel/step-1-publish-the-siebel-business-component-operations-as-a-wcf-service.md)).</span></span> <span data-ttu-id="515e1-154">您必須指定方法屬性相同的值。</span><span class="sxs-lookup"><span data-stu-id="515e1-154">You must specify the same values for the method properties.</span></span>  
  
##### <a name="to-specify-user-name-and-password-headers-for-the-query-method"></a><span data-ttu-id="515e1-155">若要指定查詢方法的使用者名稱和密碼標頭</span><span class="sxs-lookup"><span data-stu-id="515e1-155">To specify user name and password headers for the Query method</span></span>  
  
1.  <span data-ttu-id="515e1-156">在 [中繼資料物件] 窗格中，依序展開**帳戶**節點，然後展開**方法**節點。</span><span class="sxs-lookup"><span data-stu-id="515e1-156">In the Metadata Objects pane, expand the **Account** node, and then expand the **Methods** node.</span></span>  
  
2.  <span data-ttu-id="515e1-157">按一下 **查詢**節點，並在 屬性 窗格中，按一下 省略符號 （...） 按鈕，針對**屬性**欄位。</span><span class="sxs-lookup"><span data-stu-id="515e1-157">Click the **Query** node, and in the Properties pane click the ellipsis (…) button against the **Properties** field.</span></span>  
  
3.  <span data-ttu-id="515e1-158">在 PropertyView 集合編輯器 對話方塊中，按一下 **新增**，然後在 屬性 窗格中，輸入`HttpHeaderUserName`如**名稱**欄位。</span><span class="sxs-lookup"><span data-stu-id="515e1-158">In the PropertyView Collection Editor dialog box, click **Add**, and in the Properties pane, type `HttpHeaderUserName` for the **Name** field.</span></span> <span data-ttu-id="515e1-159">同樣地，輸入`MyUserHeader`for **PropertyValue**欄位。</span><span class="sxs-lookup"><span data-stu-id="515e1-159">Similarly, type `MyUserHeader` for the **PropertyValue** field.</span></span> <span data-ttu-id="515e1-160">選取  **System.String** for**型別**欄位。</span><span class="sxs-lookup"><span data-stu-id="515e1-160">Select **System.String** for the **Type** field.</span></span>  
  
     <span data-ttu-id="515e1-161">![將屬性加入](../../adapters-and-accelerators/adapter-sap/media/9eef32ac-8a93-45dc-8d07-12b7dbf961ba.gif "9eef32ac-8a93-45dc-8d07-12b7dbf961ba")</span><span class="sxs-lookup"><span data-stu-id="515e1-161">![Add a property](../../adapters-and-accelerators/adapter-sap/media/9eef32ac-8a93-45dc-8d07-12b7dbf961ba.gif "9eef32ac-8a93-45dc-8d07-12b7dbf961ba")</span></span>  
  
4.  <span data-ttu-id="515e1-162">在 PropertyView 集合編輯器 視窗中，按一下 **新增**，然後在 屬性 窗格中，輸入`HttpHeaderPassword`如**名稱**欄位。</span><span class="sxs-lookup"><span data-stu-id="515e1-162">In the PropertyView Collection Editor window, click **Add**, and in the Properties pane, type `HttpHeaderPassword` for the **Name** field.</span></span> <span data-ttu-id="515e1-163">同樣地，輸入`MyPassHeader`for **PropertyValue**欄位。</span><span class="sxs-lookup"><span data-stu-id="515e1-163">Similarly, type `MyPassHeader` for the **PropertyValue** field.</span></span> <span data-ttu-id="515e1-164">選取  **System.String** for**型別**欄位。</span><span class="sxs-lookup"><span data-stu-id="515e1-164">Select **System.String** for the **Type** field.</span></span>  
  
5.  <span data-ttu-id="515e1-165">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="515e1-165">Click **OK**.</span></span>  
  
### <a name="set-up-single-sign-on-for-connecting-to-a-siebel-system"></a><span data-ttu-id="515e1-166">設定單一登入為連接至 Siebel 系統</span><span class="sxs-lookup"><span data-stu-id="515e1-166">Set up Single Sign-On for Connecting to a Siebel System</span></span>  
 <span data-ttu-id="515e1-167">執行本主題中的所有程序完成之後，您將建立應用程式定義可以匯入 SharePoint 應用程式的 XML。</span><span class="sxs-lookup"><span data-stu-id="515e1-167">After you have finished performing all the procedures in this topic, you will have created an application definition XML that can be imported into a SharePoint application.</span></span> <span data-ttu-id="515e1-168">從應用程式，您會 （公開為 Web 方法） 的 Siebel 商務元件作業叫用來擷取 Siebel 系統的相關資料。</span><span class="sxs-lookup"><span data-stu-id="515e1-168">From the application, you will invoke the Siebel business component operations (exposed as Web methods) to retrieve relevant data from the Siebel system.</span></span> <span data-ttu-id="515e1-169">若要這麼做，您必須在 SharePoint 應用程式中建立 Siebel 系統中的使用者與使用者之間的對應。</span><span class="sxs-lookup"><span data-stu-id="515e1-169">To enable this, you must create a mapping between a user in the Siebel system and the user in the SharePoint application.</span></span> <span data-ttu-id="515e1-170">您已匯入應用程式定義 XML 之後，您可以建立在 SharePoint 管理中心網站的此對應。</span><span class="sxs-lookup"><span data-stu-id="515e1-170">You create this mapping in SharePoint Central Administration Web site after you have imported the application definition XML.</span></span>  
  
 <span data-ttu-id="515e1-171">不過，若要建立對應您必須設定屬性**SecondarySsoApplicationId**中商務資料目錄定義編輯器。</span><span class="sxs-lookup"><span data-stu-id="515e1-171">However, to create the mapping you must set a property **SecondarySsoApplicationId** in the Business Data Catalog Definition Editor.</span></span>  
  
##### <a name="to-set-the-secondaryssoapplicationid-property"></a><span data-ttu-id="515e1-172">若要設定 SecondarySsoApplicationId 屬性</span><span class="sxs-lookup"><span data-stu-id="515e1-172">To set the SecondarySsoApplicationId property</span></span>  
  
1.  <span data-ttu-id="515e1-173">在 [中繼資料物件] 窗格中，依序展開**Siebel_Account**節點，然後展開**執行個體**節點。</span><span class="sxs-lookup"><span data-stu-id="515e1-173">In the Metadata Objects pane, expand the **Siebel_Account** node, and then expand the **Instances** node.</span></span>  
  
2.  <span data-ttu-id="515e1-174">按一下  **Siebel_Account_Instance**和 屬性 窗格中按一下 省略符號 （...） 按鈕，針對**屬性**欄位。</span><span class="sxs-lookup"><span data-stu-id="515e1-174">Click **Siebel_Account_Instance** and in the Properties pane click the ellipsis (…) button against the **Properties** field.</span></span>  
  
3.  <span data-ttu-id="515e1-175">在 PropertyView 集合編輯器 視窗中，按一下 **新增**，然後在 屬性 窗格中，輸入**SecondarySsoApplicationId**如**名稱**欄位。</span><span class="sxs-lookup"><span data-stu-id="515e1-175">In the PropertyView Collection Editor window, click **Add**, and in the Properties pane, type **SecondarySsoApplicationId** for the **Name** field.</span></span> <span data-ttu-id="515e1-176">同樣地，輸入**SiebelSSO** for **PropertyValue**欄位。</span><span class="sxs-lookup"><span data-stu-id="515e1-176">Similarly, type **SiebelSSO** for the **PropertyValue** field.</span></span> <span data-ttu-id="515e1-177">選取  **System.String** for**型別**欄位。</span><span class="sxs-lookup"><span data-stu-id="515e1-177">Select **System.String** for the **Type** field.</span></span>  
  
     <span data-ttu-id="515e1-178">![新增 SSO 屬性](../../adapters-and-accelerators/adapter-siebel/media/59ce70eb-498f-406b-965d-c273c2d6ed14.gif "59ce70eb-498f-406b-965d-c273c2d6ed14")</span><span class="sxs-lookup"><span data-stu-id="515e1-178">![Add the SSO property](../../adapters-and-accelerators/adapter-siebel/media/59ce70eb-498f-406b-965d-c273c2d6ed14.gif "59ce70eb-498f-406b-965d-c273c2d6ed14")</span></span>  
  
4.  <span data-ttu-id="515e1-179">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="515e1-179">Click **OK**.</span></span>  
  
### <a name="requirement-perform-a-query-operation-on-the-account-business-component"></a><span data-ttu-id="515e1-180">需求： 執行帳戶商務元件上的查詢作業</span><span class="sxs-lookup"><span data-stu-id="515e1-180">Requirement: Perform a Query Operation on the Account Business Component</span></span>  
 <span data-ttu-id="515e1-181">此範例中的第一個需求是建立可用來執行查詢作業帳戶商務元件上的應用程式定義。</span><span class="sxs-lookup"><span data-stu-id="515e1-181">The first requirement of this example is to create an application definition that can be used to perform a Query operation on the Account business component.</span></span> <span data-ttu-id="515e1-182">若要達到此需求，您必須執行下列一組工作：</span><span class="sxs-lookup"><span data-stu-id="515e1-182">To achieve this requirement, you must perform the following set of tasks:</span></span>  
  
-   <span data-ttu-id="515e1-183">在查詢方法中，建立篩選器，並將它對應至執行查詢作業的參數。</span><span class="sxs-lookup"><span data-stu-id="515e1-183">In the Query method, create a filter, and map it to the parameter on which the Query operation is performed.</span></span> <span data-ttu-id="515e1-184">針對帳戶商務元件，您將會執行查詢，使用**SearchExpr**參數。</span><span class="sxs-lookup"><span data-stu-id="515e1-184">For the Account business component, you will perform a query using the **SearchExpr** parameter.</span></span> <span data-ttu-id="515e1-185">因此，您將對應至篩選**SearchExpr**參數。</span><span class="sxs-lookup"><span data-stu-id="515e1-185">So, you will map the filter to the **SearchExpr** parameter.</span></span>  
  
-   <span data-ttu-id="515e1-186">建立 Finder 方法執行個體的查詢方法。</span><span class="sxs-lookup"><span data-stu-id="515e1-186">Create a Finder method instance for the Query method.</span></span> <span data-ttu-id="515e1-187">搜尋方法擷取篩選為基礎的記錄清單。</span><span class="sxs-lookup"><span data-stu-id="515e1-187">A Finder method retrieves a list of records based on a filter.</span></span>  
  
##### <a name="to-create-a-filter-and-map-it-to-the-searchexpr-parameter"></a><span data-ttu-id="515e1-188">若要建立篩選器，並將它對應至 SearchExpr 參數</span><span class="sxs-lookup"><span data-stu-id="515e1-188">To create a filter, and map it to the SearchExpr parameter</span></span>  
  
1.  <span data-ttu-id="515e1-189">建立篩選的查詢方法。</span><span class="sxs-lookup"><span data-stu-id="515e1-189">Create a filter for the Query method.</span></span>  
  
    1.  <span data-ttu-id="515e1-190">在 [中繼資料物件] 窗格中，依序展開**帳戶**節點，然後展開**方法**節點。</span><span class="sxs-lookup"><span data-stu-id="515e1-190">In the Metadata Objects pane, expand the **Account** node, and then expand the **Methods** node.</span></span>  
  
    2.  <span data-ttu-id="515e1-191">展開的查詢方法，以滑鼠右鍵按一下**篩選條件**，然後按一下**加入篩選**。</span><span class="sxs-lookup"><span data-stu-id="515e1-191">Expand the Query method, right-click **Filters**, and then click **Add Filter**.</span></span>  
  
         <span data-ttu-id="515e1-192">![將篩選新增至方法](../../adapters-and-accelerators/adapter-siebel/media/9cf7ccfd-6da0-44b7-b522-df327a74e7a2.gif "9cf7ccfd-6da0-44b7-b522-df327a74e7a2")</span><span class="sxs-lookup"><span data-stu-id="515e1-192">![Add filter to a method](../../adapters-and-accelerators/adapter-siebel/media/9cf7ccfd-6da0-44b7-b522-df327a74e7a2.gif "9cf7ccfd-6da0-44b7-b522-df327a74e7a2")</span></span>  
  
    3.  <span data-ttu-id="515e1-193">在 [屬性] 窗格中，輸入`SearchExpression`for**名稱**欄位。</span><span class="sxs-lookup"><span data-stu-id="515e1-193">In the Properties pane, type `SearchExpression` for the **Name** field.</span></span>  
  
    4.  <span data-ttu-id="515e1-194">針對**FilterType**屬性中，選取**等於**。</span><span class="sxs-lookup"><span data-stu-id="515e1-194">For the **FilterType** property, select **Equals**.</span></span>  
  
         <span data-ttu-id="515e1-195">![指定的篩選器名稱和類型](../../adapters-and-accelerators/adapter-siebel/media/9faa18e1-4d27-4ee4-960a-458f978812a7.gif "9faa18e1-4d27-4ee4-960a-458f978812a7")</span><span class="sxs-lookup"><span data-stu-id="515e1-195">![Specify a filter name and type](../../adapters-and-accelerators/adapter-siebel/media/9faa18e1-4d27-4ee4-960a-458f978812a7.gif "9faa18e1-4d27-4ee4-960a-458f978812a7")</span></span>  
  
2.  <span data-ttu-id="515e1-196">若要將篩選器對應**SearchExpr**查詢方法中的參數。</span><span class="sxs-lookup"><span data-stu-id="515e1-196">Map the filter to the **SearchExpr** parameter in the Query method.</span></span>  
  
    1.  <span data-ttu-id="515e1-197">在 [中繼資料物件] 窗格中，依序展開**帳戶**節點，然後展開**方法**節點。</span><span class="sxs-lookup"><span data-stu-id="515e1-197">In the Metadata Objects pane, expand the **Account** node, and then expand the **Methods** node.</span></span>  
  
    2.  <span data-ttu-id="515e1-198">展開查詢方法中，然後再展開**參數**節點。</span><span class="sxs-lookup"><span data-stu-id="515e1-198">Expand the Query method, and then expand the **Parameters** node.</span></span>  
  
    3.  <span data-ttu-id="515e1-199">依序展開**AccountQueryInputRecord**節點，然後展開 第二個**AccountQueryInputRecord**節點。</span><span class="sxs-lookup"><span data-stu-id="515e1-199">Expand the **AccountQueryInputRecord** node, and then expand the second **AccountQueryInputRecord** node.</span></span>  
  
    4.  <span data-ttu-id="515e1-200">按一下  **SearchExpr**節點，然後在 屬性 窗格中，選取**SearchExpression**從**FilterDescriptor**清單。</span><span class="sxs-lookup"><span data-stu-id="515e1-200">Click the **SearchExpr** node and in the Properties pane, select **SearchExpression** from the **FilterDescriptor**list.</span></span>  
  
         <span data-ttu-id="515e1-201">![將參數對應至篩選](../../adapters-and-accelerators/adapter-siebel/media/199c8ba7-d0e8-4fb4-9d73-9cf548512498.gif "199c8ba7-d0e8-4fb4-9d73-9cf548512498")</span><span class="sxs-lookup"><span data-stu-id="515e1-201">![Map a parameter to a filter](../../adapters-and-accelerators/adapter-siebel/media/199c8ba7-d0e8-4fb4-9d73-9cf548512498.gif "199c8ba7-d0e8-4fb4-9d73-9cf548512498")</span></span>  
  
        > [!IMPORTANT]
        >  <span data-ttu-id="515e1-202">**AccountQueryInputRecord**也包含 **# 10**節點，其中又包含**項目**節點。</span><span class="sxs-lookup"><span data-stu-id="515e1-202">The **AccountQueryInputRecord** also contains a **QueryFields** node, which in turn contains an **Item** node.</span></span> <span data-ttu-id="515e1-203">您必須先刪除**項目** 節點，否則帳戶商務元件上的查詢作業，可能無法提供想要的結果。</span><span class="sxs-lookup"><span data-stu-id="515e1-203">You must delete the **Item** node, otherwise the Query operation on the Account business component might not give the desired results.</span></span> <span data-ttu-id="515e1-204">若要刪除**項目**節點，以滑鼠右鍵按一下節點，然後按**刪除**。</span><span class="sxs-lookup"><span data-stu-id="515e1-204">To delete the **Item** node, right-click the node, and then select **Delete**.</span></span>  
  
##### <a name="to-create-a-finder-method-instance-for-query-method"></a><span data-ttu-id="515e1-205">若要建立 Finder 方法執行個體的查詢方法</span><span class="sxs-lookup"><span data-stu-id="515e1-205">To create a Finder method instance for Query method</span></span>  
  
1.  <span data-ttu-id="515e1-206">在 [中繼資料物件] 窗格中，依序展開**帳戶**節點，然後展開**方法**節點。</span><span class="sxs-lookup"><span data-stu-id="515e1-206">In the Metadata Objects pane, expand the **Account** node, and then expand the **Methods** node.</span></span>  
  
2.  <span data-ttu-id="515e1-207">依序展開**查詢**節點，以滑鼠右鍵按一下**執行個體**，然後按一下**新增方法執行個體**以開啟 [建立方法執行個體] 視窗。</span><span class="sxs-lookup"><span data-stu-id="515e1-207">Expand the **Query** node, right-click **Instances**, and then click **Add Method Instance** to open the Create Method Instance window.</span></span>  
  
     <span data-ttu-id="515e1-208">![新增 Finder 方法執行個體](../../adapters-and-accelerators/adapter-siebel/media/c90e7784-4fb7-4eb5-baf5-efbefba4bb1f.gif "c90e7784-4fb7-4eb5-baf5-efbefba4bb1f")</span><span class="sxs-lookup"><span data-stu-id="515e1-208">![Add a Finder method instance](../../adapters-and-accelerators/adapter-siebel/media/c90e7784-4fb7-4eb5-baf5-efbefba4bb1f.gif "c90e7784-4fb7-4eb5-baf5-efbefba4bb1f")</span></span>  
  
3.  <span data-ttu-id="515e1-209">在 [建立方法執行個體] 視窗中，按一下**Finder** for**方法執行個體類型**。</span><span class="sxs-lookup"><span data-stu-id="515e1-209">In the Create Method Instance window, click **Finder** for the **Method Instance Type**.</span></span>  
  
4.  <span data-ttu-id="515e1-210">按一下 **會傳回**從**傳回 TypeDescriptor**一節。</span><span class="sxs-lookup"><span data-stu-id="515e1-210">Click **Return** from **Return TypeDescriptor** section.</span></span>  
  
     <span data-ttu-id="515e1-211">![新增 Finder 方法執行個體](../../adapters-and-accelerators/adapter-siebel/media/e8343988-d7c1-4b04-85b0-ca7d07097490.gif "e8343988-d7c1-4b04-85b0-ca7d07097490")</span><span class="sxs-lookup"><span data-stu-id="515e1-211">![Add a Finder method instance](../../adapters-and-accelerators/adapter-siebel/media/e8343988-d7c1-4b04-85b0-ca7d07097490.gif "e8343988-d7c1-4b04-85b0-ca7d07097490")</span></span>  
  
5.  <span data-ttu-id="515e1-212">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="515e1-212">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="515e1-213">在 [屬性] 窗格中，輸入`QueryAccount`for**名稱**欄位。</span><span class="sxs-lookup"><span data-stu-id="515e1-213">In the Properties pane, type `QueryAccount` for the **Name** field.</span></span>  
  
     <span data-ttu-id="515e1-214">![指定方法執行個體名稱](../../adapters-and-accelerators/adapter-siebel/media/401223f3-806f-4010-8646-d5ac0c0e9f67.gif "401223f3-806f-4010-8646-d5ac0c0e9f67")</span><span class="sxs-lookup"><span data-stu-id="515e1-214">![Specify a name for the method instance](../../adapters-and-accelerators/adapter-siebel/media/401223f3-806f-4010-8646-d5ac0c0e9f67.gif "401223f3-806f-4010-8646-d5ac0c0e9f67")</span></span>  
  
### <a name="remove-the-parameters-of-systemnullable-type"></a><span data-ttu-id="515e1-215">移除 System.Nullable 類型的參數</span><span class="sxs-lookup"><span data-stu-id="515e1-215">Remove the Parameters of System.Nullable Type</span></span>  
 <span data-ttu-id="515e1-216">查詢函式的傳回參數可能會包含屬於 System.Nullable 類型的參數。</span><span class="sxs-lookup"><span data-stu-id="515e1-216">The return parameters for Query function may contain parameters that are of System.Nullable type.</span></span> <span data-ttu-id="515e1-217">在 應用程式定義這些參數的緣故，您可能會發生錯誤，同時 SharePoint 入口網站上呈現的 Siebel 資料。</span><span class="sxs-lookup"><span data-stu-id="515e1-217">Due to the presence of these parameters in the application definition, you might get an error while presenting Siebel data on a SharePoint portal.</span></span> <span data-ttu-id="515e1-218">因此，您必須將 System.Nullable 類型的參數移除應用程式定義。</span><span class="sxs-lookup"><span data-stu-id="515e1-218">So, you must remove the parameters of System.Nullable type from the application definition.</span></span>  
  
 <span data-ttu-id="515e1-219">此外，System.Nullable 類型的每個參數，商務資料目錄定義編輯器建立 System.Boolean 類型的另一個參數，並將"Specified"附加到參數名稱。</span><span class="sxs-lookup"><span data-stu-id="515e1-219">Also, for each parameter of System.Nullable type, the Business Data Catalog Definition Editor creates another parameter of System.Boolean type, and appends “Specified” to the parameter name.</span></span> <span data-ttu-id="515e1-220">例如，參數 AccountRole 屬於 System.Nullable 型別。</span><span class="sxs-lookup"><span data-stu-id="515e1-220">For example, the parameter AccountRole is of System.Nullable type.</span></span> <span data-ttu-id="515e1-221">因此，商務資料目錄定義編輯器會將 AccountRoleSpecified 參數加入至參數的清單。</span><span class="sxs-lookup"><span data-stu-id="515e1-221">So, the Business Data Catalog Definition Editor adds an AccountRoleSpecified parameter to the list of parameters.</span></span> <span data-ttu-id="515e1-222">您必須移除以及這類參數。</span><span class="sxs-lookup"><span data-stu-id="515e1-222">You must remove such parameters as well.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="515e1-223">您可以看到在商務資料目錄定義編輯器中，選取參數，並查看 [值輸入參數**TypeName**屬性] 窗格中的屬性。</span><span class="sxs-lookup"><span data-stu-id="515e1-223">You can see the parameter type by selecting the parameter in the Business Data Catalog Definition Editor, and looking at the value for the **TypeName** property in the Properties pane.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="515e1-224">如果應用程式不包含 System.Nullable 類型的任何參數，您可以略過此步驟。</span><span class="sxs-lookup"><span data-stu-id="515e1-224">You can skip this step if the application does not contain any parameters of System.Nullable type.</span></span>  
  
##### <a name="to-remove-the-parameters-of-systemnullable-type-for-the-query-method"></a><span data-ttu-id="515e1-225">若要移除的 System.Nullable Query 方法的型別參數</span><span class="sxs-lookup"><span data-stu-id="515e1-225">To remove the parameters of System.Nullable type for the Query method</span></span>  
  
1.  <span data-ttu-id="515e1-226">在 [中繼資料物件] 窗格中，依序展開**帳戶**節點，然後展開**方法**節點。</span><span class="sxs-lookup"><span data-stu-id="515e1-226">In the Metadata Objects pane, expand the **Account** node, and then expand the **Methods** node.</span></span>  
  
2.  <span data-ttu-id="515e1-227">依序展開**查詢**節點，然後展開**參數**節點。</span><span class="sxs-lookup"><span data-stu-id="515e1-227">Expand the **Query** node, and then expand the **Parameters** node.</span></span>  
  
3.  <span data-ttu-id="515e1-228">依序展開**會傳回**節點，然後展開 第二個**傳回**節點。</span><span class="sxs-lookup"><span data-stu-id="515e1-228">Expand the **Return** node, and then expand the second **Return** node.</span></span>  
  
4.  <span data-ttu-id="515e1-229">以滑鼠右鍵按一下您想要刪除此項目，然後選取的參數**刪除**。</span><span class="sxs-lookup"><span data-stu-id="515e1-229">Right-click the parameter you want to delete, and then select **Delete**.</span></span>  
  
5.  <span data-ttu-id="515e1-230">在對話方塊中，按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="515e1-230">In the dialog box, click **OK**.</span></span>  
  
### <a name="export-the-application-definition-to-a-file"></a><span data-ttu-id="515e1-231">匯出至檔案的應用程式定義</span><span class="sxs-lookup"><span data-stu-id="515e1-231">Export the Application Definition to a File</span></span>  
 <span data-ttu-id="515e1-232">您現在已建立應用程式定義，其中包含 Siebel 系統的執行個體中繼資料。</span><span class="sxs-lookup"><span data-stu-id="515e1-232">You have now created an application definition that contains the Siebel system instance metadata.</span></span> <span data-ttu-id="515e1-233">您必須將此定義匯出至 XML 檔案，可匯入至 Microsoft Office SharePoint Server。</span><span class="sxs-lookup"><span data-stu-id="515e1-233">You must export this definition to an XML file, which can be imported into Microsoft Office SharePoint Server.</span></span>  
  
##### <a name="to-export-the-application-definition-to-a-file"></a><span data-ttu-id="515e1-234">若要將應用程式定義匯出至檔案</span><span class="sxs-lookup"><span data-stu-id="515e1-234">To export the application definition to a file</span></span>  
  
1.  <span data-ttu-id="515e1-235">以滑鼠右鍵按一下**Siebel_Account**節點中的中繼資料物件 窗格中，然後按一下**匯出**。</span><span class="sxs-lookup"><span data-stu-id="515e1-235">Right-click the **Siebel_Account** node in the Metadata Objects pane, and then click **Export**.</span></span>  
  
2.  <span data-ttu-id="515e1-236">將檔案儲存為 Siebel_Account.xml 中。</span><span class="sxs-lookup"><span data-stu-id="515e1-236">Save the file as Siebel_Account.xml.</span></span>  
  
### <a name="modify-the-application-definition-file-to-include-specific-parameters"></a><span data-ttu-id="515e1-237">修改應用程式定義檔，以包含特定的參數</span><span class="sxs-lookup"><span data-stu-id="515e1-237">Modify the Application Definition File to Include Specific Parameters</span></span>  
 <span data-ttu-id="515e1-238">如本主題稍早所述，「 商務資料目錄定義編輯器工具不會處理列舉的資料類型。</span><span class="sxs-lookup"><span data-stu-id="515e1-238">As mentioned earlier in this topic, the Business Data Catalog Definition Editor tool does not handle enumerated data types.</span></span> <span data-ttu-id="515e1-239">Business Data Catalog Definition Editor 工具匯入的欄位，直到它遇到列舉的資料類型，並忽略其餘的欄位。</span><span class="sxs-lookup"><span data-stu-id="515e1-239">The Business Data Catalog Definition Editor tool imports the fields till it encounters an enumerated data type and ignores the remaining fields.</span></span> <span data-ttu-id="515e1-240">因此，可能會省略您想要在您的應用程式中的某些欄位。</span><span class="sxs-lookup"><span data-stu-id="515e1-240">So, certain fields that you want in your application might be omitted.</span></span> <span data-ttu-id="515e1-241">您可以手動編輯應用程式定義檔，以包含這些欄位。</span><span class="sxs-lookup"><span data-stu-id="515e1-241">You can manually edit the application definition file to include those fields.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="515e1-242">您必須先確定您要加入的參數中的 WCF 配接器服務開發精靈所產生的.cs 檔案中有[步驟 1： 發佈為 WCF 服務的 Siebel 商務元件操作](../../adapters-and-accelerators/adapter-siebel/step-1-publish-the-siebel-business-component-operations-as-a-wcf-service.md)。</span><span class="sxs-lookup"><span data-stu-id="515e1-242">You must make sure the parameters you are adding are present in the .cs file generated by the WCF Adapter Service Development Wizard in [Step 1: Publish the Siebel Business Component Operations as a WCF Service](../../adapters-and-accelerators/adapter-siebel/step-1-publish-the-siebel-business-component-operations-as-a-wcf-service.md).</span></span>  
  
 <span data-ttu-id="515e1-243">在此應用程式定義檔案中，您會決定要加入或移除的傳回參數**QueryAccount**方法。</span><span class="sxs-lookup"><span data-stu-id="515e1-243">In this application definition file, you will add or remove return parameters for the **QueryAccount** method.</span></span>  
  
##### <a name="to-modify-the-application-definition-file"></a><span data-ttu-id="515e1-244">若要修改應用程式定義檔</span><span class="sxs-lookup"><span data-stu-id="515e1-244">To modify the application definition file</span></span>  
  
1. <span data-ttu-id="515e1-245">使用開啟的應用程式定義檔，Siebel_Account.xml，[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]或任何其他編輯器。</span><span class="sxs-lookup"><span data-stu-id="515e1-245">Open the application definition file, Siebel_Account.xml, by using [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] or any other editor.</span></span>  
  
2. <span data-ttu-id="515e1-246">修改應用程式定義檔，來取代的參數**QueryAccount**方法。</span><span class="sxs-lookup"><span data-stu-id="515e1-246">Modify the application definition file to replace the parameters for the **QueryAccount** method.</span></span>  
  
   1.  <span data-ttu-id="515e1-247">在應用程式定義檔案中，搜尋下列：</span><span class="sxs-lookup"><span data-stu-id="515e1-247">Within the application definition file, search for the following:</span></span>  
  
       ```  
       <TypeDescriptor TypeName="BDC.AccountQueryRecord,Siebel_Account" Name="Item">  
       ```  
  
   2.  <span data-ttu-id="515e1-248">內`<TypeDescriptors>`標記中，取代現有`<TypeDescriptor>`具有下列項目：</span><span class="sxs-lookup"><span data-stu-id="515e1-248">Within the `<TypeDescriptors>` tag, replace the existing `<TypeDescriptor>` elements with the following:</span></span>  
  
       ```  
  
       <TypeDescriptor TypeName="System.String, mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=<token>" Name="Id" />  
       <TypeDescriptor TypeName="System.String, mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=<token>" Name="Country" />  
       <TypeDescriptor TypeName="System.String, mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=<token>" Name="Name" />  
       <TypeDescriptor TypeName="System.String, mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=<token>" Name="Location" />  
       ```  
  
   3.  <span data-ttu-id="515e1-249">儲存並關閉檔案。</span><span class="sxs-lookup"><span data-stu-id="515e1-249">Save and close the file.</span></span>  
  
   > [!TIP]
   >  <span data-ttu-id="515e1-250">您可以匯入更新的應用程式定義檔，在 商務資料目錄定義編輯器工具，以查看新加入的欄位。</span><span class="sxs-lookup"><span data-stu-id="515e1-250">You can import the updated application definition file back in the Business Data Catalog Definition Editor tool to see the newly added fields.</span></span> <span data-ttu-id="515e1-251">不過，匯入之前您必須從 Business Data Catalog Definition Editor 工具中移除現有的"Siebel_Account 」 應用程式。</span><span class="sxs-lookup"><span data-stu-id="515e1-251">However, before importing you will have to remove the existing “Siebel_Account” application from the Business Data Catalog Definition Editor tool.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="515e1-252">後續步驟</span><span class="sxs-lookup"><span data-stu-id="515e1-252">Next Steps</span></span>  
 <span data-ttu-id="515e1-253">您現在必須建立 SharePoint 應用程式來擷取 Siebel 系統中的資料。</span><span class="sxs-lookup"><span data-stu-id="515e1-253">You must now create a SharePoint application to retrieve data from a Siebel system.</span></span> <span data-ttu-id="515e1-254">請參閱[步驟 3： 建立 SharePoint 應用程式以擷取資料從 Siebel](../../adapters-and-accelerators/adapter-siebel/step-3-create-a-sharepoint-application-to-retrieve-data-from-siebel.md)如需相關指示。</span><span class="sxs-lookup"><span data-stu-id="515e1-254">See [Step 3: Create a SharePoint Application to Retrieve Data from Siebel](../../adapters-and-accelerators/adapter-siebel/step-3-create-a-sharepoint-application-to-retrieve-data-from-siebel.md) for instructions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="515e1-255">另請參閱</span><span class="sxs-lookup"><span data-stu-id="515e1-255">See Also</span></span>  
 [<span data-ttu-id="515e1-256">教學課程 1：在 SharePoint 網站上呈現 Siebel 系統的資料</span><span class="sxs-lookup"><span data-stu-id="515e1-256">Tutorial 1: Presenting Data From a Siebel System on a SharePoint Site</span></span>](../../adapters-and-accelerators/adapter-siebel/tutorial-1-presenting-data-from-a-siebel-system-on-a-sharepoint-site.md)