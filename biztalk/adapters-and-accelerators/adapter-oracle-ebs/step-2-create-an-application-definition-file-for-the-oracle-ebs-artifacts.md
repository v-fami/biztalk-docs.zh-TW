---
title: 步驟 2： 建立 Oracle E-business Suite 成品的應用程式定義檔 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2665afde-0337-4795-ab4c-6223d39fdf9c
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f0bd73da129e978bfe2d4ad5af2b4f26fb9bcc16
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36970751"
---
# <a name="step-2-create-an-application-definition-file-for-the-oracle-e-business-suite-artifacts"></a><span data-ttu-id="519f0-102">步驟 2： 建立 Oracle E-business Suite 成品的應用程式定義檔</span><span class="sxs-lookup"><span data-stu-id="519f0-102">Step 2: Create an application definition file for the Oracle E-Business Suite artifacts</span></span>
<span data-ttu-id="519f0-103">![步驟 4 之 2](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-2of4.gif "Step_2of4")</span><span class="sxs-lookup"><span data-stu-id="519f0-103">![Step 2 of 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-2of4.gif "Step_2of4")</span></span>  
  
 <span data-ttu-id="519f0-104">**若要完成的時間：** 15 分鐘</span><span class="sxs-lookup"><span data-stu-id="519f0-104">**Time to complete:** 15 minutes</span></span>  
  
 <span data-ttu-id="519f0-105">**目標：** Microsoft SharePoint Server 中的商務資料目錄 」 功能會公開，並併入入口網站中的資料列的商務 (LOB) 應用程式。</span><span class="sxs-lookup"><span data-stu-id="519f0-105">**Objective:** The Business Data Catalog feature in Microsoft SharePoint Server exposes and incorporates data from line-of-business (LOB) applications into portals.</span></span> <span data-ttu-id="519f0-106">若要併入您的入口網站中的這項資料，您必須建置可取用 Microsoft Office SharePoint Server 的應用程式定義檔。</span><span class="sxs-lookup"><span data-stu-id="519f0-106">To incorporate this data into your portal site, you must build an application definition file that Microsoft Office SharePoint Server can consume.</span></span>  
  
 <span data-ttu-id="519f0-107">Business Data Catalog Definition Editor 工具，適用於 Microsoft Office SharePoint Server 2007 SDK，可讓您的商務資料目錄中建立應用程式定義檔案。</span><span class="sxs-lookup"><span data-stu-id="519f0-107">The Business Data Catalog Definition Editor tool, available with Microsoft Office SharePoint Server 2007 SDK, enables you to create an application definition file for the Business Data Catalog.</span></span> <span data-ttu-id="519f0-108">此工具會自動產生 XML 檔案定義檔，因此您不需要手動建立檔案的 xml 編輯器。</span><span class="sxs-lookup"><span data-stu-id="519f0-108">This tool automatically generates an XML file for the definition file, so you do not need to manually create the file in an XML editor.</span></span>  
  
 <span data-ttu-id="519f0-109">Microsoft Office SharePoint Server 應用程式所建立的目的是：</span><span class="sxs-lookup"><span data-stu-id="519f0-109">The purpose of the Microsoft Office SharePoint Server application that you are creating is to:</span></span>  
  
- <span data-ttu-id="519f0-110">使用商務資料清單 Web 組件 MS_SAMPLE_EMPLOYEE 介面資料表中員工的查詢會根據員工名稱。</span><span class="sxs-lookup"><span data-stu-id="519f0-110">Query for an employee in the MS_SAMPLE_EMPLOYEE interface table using a Business Data List Web Part based on an employee name.</span></span>  
  
- <span data-ttu-id="519f0-111">從 Microsoft Office SharePoint Server 對 MS_SAMPLE_EMPLOYEE 介面資料表的全文檢索搜尋。</span><span class="sxs-lookup"><span data-stu-id="519f0-111">Perform a full-text search from Microsoft Office SharePoint Server on the MS_SAMPLE_EMPLOYEE interface table.</span></span>  
  
  <span data-ttu-id="519f0-112">針對每個這些需求，您必須完成一的組 「 商務資料目錄定義編輯器 」 工具中的工作。</span><span class="sxs-lookup"><span data-stu-id="519f0-112">For each of these requirements, you must complete a set of tasks in the Business Data Catalog Definition Editor tool.</span></span> <span data-ttu-id="519f0-113">本主題提供有關如何執行這些工作的指示。</span><span class="sxs-lookup"><span data-stu-id="519f0-113">This topic provides instructions on how to perform these tasks.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="519f0-114">必要條件</span><span class="sxs-lookup"><span data-stu-id="519f0-114">Prerequisites</span></span>  
  
-   <span data-ttu-id="519f0-115">請確定您已安裝 Microsoft Office SharePoint Server 2007 SDK 的一部分為商務資料目錄定義編輯器。</span><span class="sxs-lookup"><span data-stu-id="519f0-115">Be sure that you have the Business Data Catalog Definition Editor installed as part of the Microsoft Office SharePoint Server 2007 SDK.</span></span> <span data-ttu-id="519f0-116">您可以下載從 SDK [ http://go.microsoft.com/fwlink/?LinkId=104130 ](http://go.microsoft.com/fwlink/?LinkId=104130)。</span><span class="sxs-lookup"><span data-stu-id="519f0-116">You can download the SDK from [http://go.microsoft.com/fwlink/?LinkId=104130](http://go.microsoft.com/fwlink/?LinkId=104130).</span></span>  
  
-   <span data-ttu-id="519f0-117">發佈 WCF 服務中所述[步驟 1： 使用 Oracle E-business 配接器，來建立及發佈 WCF 服務](../../adapters-and-accelerators/adapter-oracle-ebs/step-1-use-the-oracle-e-business-adapter-to-create-and-publish-a-wcf-service.md)。</span><span class="sxs-lookup"><span data-stu-id="519f0-117">Publish the WCF service as described in [Step 1: Use the Oracle E-Business Adapter to Create and Publish a WCF Service](../../adapters-and-accelerators/adapter-oracle-ebs/step-1-use-the-oracle-e-business-adapter-to-create-and-publish-a-wcf-service.md).</span></span>  
  

  
##  <a name="Connect"></a> <span data-ttu-id="519f0-118">連線到 WCF LOB 服務並建立實體</span><span class="sxs-lookup"><span data-stu-id="519f0-118">Connect to the WCF LOB Service and Create Entity</span></span>  
 <span data-ttu-id="519f0-119">您必須連接至 WCF 服務，以擷取 Web 服務描述語言 (WSDL) 服務。</span><span class="sxs-lookup"><span data-stu-id="519f0-119">You must connect to the WCF service to extract the Web Services Description Language (WSDL) for the service.</span></span> <span data-ttu-id="519f0-120">商務資料目錄定義編輯器會根據 WSDL、 擷取方法。</span><span class="sxs-lookup"><span data-stu-id="519f0-120">From the WSDL, the Business Data Catalog Definition Editor extracts the methods.</span></span> <span data-ttu-id="519f0-121">這些方法可用來建立實體。</span><span class="sxs-lookup"><span data-stu-id="519f0-121">These methods can be used to create entities.</span></span> <span data-ttu-id="519f0-122">本教學課程中，建立實體。</span><span class="sxs-lookup"><span data-stu-id="519f0-122">For this tutorial, an entity is created.</span></span>  
  
#### <a name="to-connect-to-the-wcf-service-and-create-entities"></a><span data-ttu-id="519f0-123">連接到 WCF 服務，並建立實體</span><span class="sxs-lookup"><span data-stu-id="519f0-123">To connect to the WCF service and create entities</span></span>  
  
1.  <span data-ttu-id="519f0-124">啟動商務資料目錄定義編輯器。</span><span class="sxs-lookup"><span data-stu-id="519f0-124">Start the Business Data Catalog Definition Editor.</span></span> <span data-ttu-id="519f0-125">在 **開始**功能表上，按一下**Microsoft Business Data Catalog Definition Editor**。</span><span class="sxs-lookup"><span data-stu-id="519f0-125">On the **Start** menu, click **Microsoft Business Data Catalog Definition Editor**.</span></span>  
  
2.  <span data-ttu-id="519f0-126">在工具列上，按一下**新增 LOB 系統**。</span><span class="sxs-lookup"><span data-stu-id="519f0-126">On the toolbar, click **Add LOB System**.</span></span>  
  
3.  <span data-ttu-id="519f0-127">在 [新增 LOB 系統] 視窗中，按一下**連接到 web 服務**。</span><span class="sxs-lookup"><span data-stu-id="519f0-127">In the Add LOB System window, click **Connect to Webservice**.</span></span>  
  
4.  <span data-ttu-id="519f0-128">在  **URL**方塊中，輸入 WCF 服務的 URL。</span><span class="sxs-lookup"><span data-stu-id="519f0-128">In the **URL** box, type the URL for the WCF service.</span></span> <span data-ttu-id="519f0-129">本教學課程中，URL 會是：</span><span class="sxs-lookup"><span data-stu-id="519f0-129">For this tutorial, the URL will be:</span></span>  
  
    ```  
    https://<COMPUTER_NAME>:<PORT_NUMBER>/MS_SAMPLE_EMPLOYEE/InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEE.svc  
    ```  
  
     <span data-ttu-id="519f0-130">當您測試是否成功，如中所述發行 WCF 服務時，URL 是可用[步驟 1： 使用 Oracle E-business 配接器，來建立及發佈 WCF 服務](../../adapters-and-accelerators/adapter-oracle-ebs/step-1-use-the-oracle-e-business-adapter-to-create-and-publish-a-wcf-service.md)。</span><span class="sxs-lookup"><span data-stu-id="519f0-130">The URL is available when you test whether the WCF service is published successfully, as described in [Step 1: Use the Oracle E-Business Adapter to Create and Publish a WCF Service](../../adapters-and-accelerators/adapter-oracle-ebs/step-1-use-the-oracle-e-business-adapter-to-create-and-publish-a-wcf-service.md).</span></span>  
  
5.  <span data-ttu-id="519f0-131">按一下 **[連接]**。</span><span class="sxs-lookup"><span data-stu-id="519f0-131">Click **Connect**.</span></span>  
  
6.  <span data-ttu-id="519f0-132">若要查看您在 WCF 配接器服務開發精靈中選取的作業，請按一下**新增 Web 方法** 索引標籤。您會看到下列方法：**選取**。</span><span class="sxs-lookup"><span data-stu-id="519f0-132">To see the operations you selected in the WCF Adapter Service Development Wizard, click the **Add Web Method** tab. You will see the following method: **Select**.</span></span>  
  
7.  <span data-ttu-id="519f0-133">拖曳**選取**至設計介面的方法。</span><span class="sxs-lookup"><span data-stu-id="519f0-133">Drag the **Select** methods to the Design Surface.</span></span> <span data-ttu-id="519f0-134">當您將方法拖曳至設計介面時，建立實體，且方法該實體的一部分。</span><span class="sxs-lookup"><span data-stu-id="519f0-134">As you drag the method to the Design Surface, an entity is created, and the method becomes part of that entity.</span></span>  
  
     <span data-ttu-id="519f0-135">![將選取的方法加入至設計介面](../../adapters-and-accelerators/adapter-oracle-ebs/media/05-add-lob-system.gif "05_Add_LOB_System")</span><span class="sxs-lookup"><span data-stu-id="519f0-135">![Add Select method to the Design Surface](../../adapters-and-accelerators/adapter-oracle-ebs/media/05-add-lob-system.gif "05_Add_LOB_System")</span></span>  
  
8.  <span data-ttu-id="519f0-136">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="519f0-136">Click **OK**.</span></span>  
  
9. <span data-ttu-id="519f0-137">在 **輸入 LOB 系統的名稱** 對話方塊中，輸入的名稱，在**LOB 系統名稱** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="519f0-137">In the **Enter the name for the LOB System** dialog box, type a name in the **LOB System Name** box.</span></span> <span data-ttu-id="519f0-138">針對此範例中，呼叫它**MS_SAMPLE_EMPLOYEE**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="519f0-138">For this example, call it **MS_SAMPLE_EMPLOYEE**, and then click **OK**.</span></span>  
  
10. <span data-ttu-id="519f0-139">在商務資料目錄定義編輯器中，新建立的實體會列為**Entity0**。</span><span class="sxs-lookup"><span data-stu-id="519f0-139">In the Business Data Catalog Definition Editor, the newly created entity is listed as **Entity0**.</span></span> <span data-ttu-id="519f0-140">重新命名的實體**員工**。</span><span class="sxs-lookup"><span data-stu-id="519f0-140">Rename the entity to **Employee**.</span></span> <span data-ttu-id="519f0-141">執行下列步驟來重新命名實體：</span><span class="sxs-lookup"><span data-stu-id="519f0-141">Perform the following steps to rename the entity:</span></span>  
  
    1.  <span data-ttu-id="519f0-142">依序展開**MS_SAMPLE_EMPLOYEE**節點，然後展開**實體**節點。</span><span class="sxs-lookup"><span data-stu-id="519f0-142">Expand the **MS_SAMPLE_EMPLOYEE** node, and then expand the **Entities** node.</span></span>  
  
    2.  <span data-ttu-id="519f0-143">選取  **Entity0**節點。</span><span class="sxs-lookup"><span data-stu-id="519f0-143">Select the **Entity0** node.</span></span>  
  
    3.  <span data-ttu-id="519f0-144">在 屬性 窗格中，輸入**員工**中**名稱** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="519f0-144">In the Properties pane, type **Employee** in the **Name** box.</span></span>  
  
         <span data-ttu-id="519f0-145">![重新命名實體](../../adapters-and-accelerators/adapter-oracle-ebs/media/06-entity-name.gif "06_Entity_Name")</span><span class="sxs-lookup"><span data-stu-id="519f0-145">![Rename the entity](../../adapters-and-accelerators/adapter-oracle-ebs/media/06-entity-name.gif "06_Entity_Name")</span></span>  
  
##  <a name="Headers"></a> <span data-ttu-id="519f0-146">指定使用者名稱和密碼標頭方法</span><span class="sxs-lookup"><span data-stu-id="519f0-146">Specify User Name and Password Headers for the Methods</span></span>  
 <span data-ttu-id="519f0-147">建立 WCF 服務時選取作業 MS_SAMPLE_EMPLOYEE 介面資料表上 Oracle E-business Suite 中，您會指定使用者名稱和密碼標頭中的端點行為組態的一部分[步驟 1： 使用 Oracle若要建立及發佈 WCF 服務的 E-business 配接器](../../adapters-and-accelerators/adapter-oracle-ebs/step-1-use-the-oracle-e-business-adapter-to-create-and-publish-a-wcf-service.md)。</span><span class="sxs-lookup"><span data-stu-id="519f0-147">When creating a WCF service for the Select operation on the MS_SAMPLE_EMPLOYEE interface table in Oracle E-Business Suite, you specified user name and password headers as part of the endpoint behavior configuration in [Step 1: Use the Oracle E-Business Adapter to Create and Publish a WCF Service](../../adapters-and-accelerators/adapter-oracle-ebs/step-1-use-the-oracle-e-business-adapter-to-create-and-publish-a-wcf-service.md).</span></span> <span data-ttu-id="519f0-148">您必須指定相同的值，Select 方法屬性。</span><span class="sxs-lookup"><span data-stu-id="519f0-148">You must specify the same values for the Select method property.</span></span>  
  
#### <a name="to-specify-user-name-and-password-headers-for-the-select-method"></a><span data-ttu-id="519f0-149">若要指定使用者名稱和密碼標頭 Select 方法</span><span class="sxs-lookup"><span data-stu-id="519f0-149">To specify user name and password headers for the Select method</span></span>  
  
1.  <span data-ttu-id="519f0-150">在 [中繼資料物件] 窗格中，依序展開**員工**節點，然後展開**方法**節點。</span><span class="sxs-lookup"><span data-stu-id="519f0-150">In the Metadata Objects pane, expand the **Employee** node, and then expand the **Methods** node.</span></span>  
  
2.  <span data-ttu-id="519f0-151">按一下 **選取 **節點，並在 屬性 窗格中，按一下 省略符號 （...） 按鈕，針對**屬性** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="519f0-151">Click the **Select** node, and in the Properties pane click the ellipsis (…) button against the **Properties** box.</span></span>  
  
3.  <span data-ttu-id="519f0-152">在 PropertyView 集合編輯器 視窗中，按一下**新增**，然後在 屬性 窗格中，輸入**HttpHeaderUserName** for**名稱** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="519f0-152">In the PropertyView Collection Editor window, click **Add**, and in the Property pane, type **HttpHeaderUserName** for the **Name** box.</span></span> <span data-ttu-id="519f0-153">型別**MyUserHeader** for **PropertyValue**  方塊中。</span><span class="sxs-lookup"><span data-stu-id="519f0-153">Type **MyUserHeader** for the **PropertyValue** box.</span></span> <span data-ttu-id="519f0-154">選取 [ **System.String** for**型別**] 方塊中。</span><span class="sxs-lookup"><span data-stu-id="519f0-154">Select **System.String** for the **Type** box.</span></span>  
  
4.  <span data-ttu-id="519f0-155">在 PropertyView 集合編輯器 視窗中，按一下**新增**，然後在 屬性 窗格中，輸入**HttpHeaderPassword** for**名稱** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="519f0-155">In the PropertyView Collection Editor window, click **Add**, and in the Property pane, type **HttpHeaderPassword** for the **Name** box.</span></span> <span data-ttu-id="519f0-156">同樣地，輸入**MyPasswordHeader** for **PropertyValue**  方塊中。</span><span class="sxs-lookup"><span data-stu-id="519f0-156">Similarly, type **MyPasswordHeader** for the **PropertyValue** box.</span></span> <span data-ttu-id="519f0-157">選取 [ **System.String** for**型別**] 方塊中。</span><span class="sxs-lookup"><span data-stu-id="519f0-157">Select **System.String** for the **Type** box.</span></span>  
  
     <span data-ttu-id="519f0-158">![將屬性加入](../../adapters-and-accelerators/adapter-oracle-ebs/media/07-propertviewcollection-editor.gif "07_PropertViewCollection_Editor")</span><span class="sxs-lookup"><span data-stu-id="519f0-158">![Add a property](../../adapters-and-accelerators/adapter-oracle-ebs/media/07-propertviewcollection-editor.gif "07_PropertViewCollection_Editor")</span></span>  
  
5.  <span data-ttu-id="519f0-159">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="519f0-159">Click **OK**.</span></span>  
  
##  <a name="Scenario1"></a> <span data-ttu-id="519f0-160">使用商務資料清單 Web 組件的員工的案例 1： 查詢</span><span class="sxs-lookup"><span data-stu-id="519f0-160">Scenario 1: Query for Employees using a Business Data List Web Part</span></span>  
 <span data-ttu-id="519f0-161">若要建立的應用程式定義檔案可以用來搜尋員工的商務資料清單 Web 組件，並根據員工的名稱，您必須執行下列一組工作。</span><span class="sxs-lookup"><span data-stu-id="519f0-161">To create an application definition file that can be used to search for employees from a Business Data List Web Part and based on employee name, you must perform the following set of tasks.</span></span>  
  
1.  <span data-ttu-id="519f0-162">在 **選取 **方法，建立篩選器，並將它對應至**篩選**參數。</span><span class="sxs-lookup"><span data-stu-id="519f0-162">In the **Select** method, create a filter and map it to the **FILTER** parameter.</span></span>  
  
2.  <span data-ttu-id="519f0-163">建立**Finder**方法執行個體**選取**方法。</span><span class="sxs-lookup"><span data-stu-id="519f0-163">Create a **Finder** method instance for the **Select** method.</span></span> <span data-ttu-id="519f0-164">A **Finder**方法會擷取篩選為基礎的記錄清單。</span><span class="sxs-lookup"><span data-stu-id="519f0-164">A **Finder** method retrieves a list of records based on a filter.</span></span>  
  
#### <a name="to-create-a-filter-and-map-it-to-the-filter-parameter"></a><span data-ttu-id="519f0-165">若要建立篩選器，並將它對應至篩選參數</span><span class="sxs-lookup"><span data-stu-id="519f0-165">To create a filter, and map it to the FILTER parameter</span></span>  
  
1.  <span data-ttu-id="519f0-166">建立篩選。</span><span class="sxs-lookup"><span data-stu-id="519f0-166">Create a filter.</span></span>  
  
    1.  <span data-ttu-id="519f0-167">在 [中繼資料物件] 窗格中，依序展開**員工**節點，然後展開**方法**節點。</span><span class="sxs-lookup"><span data-stu-id="519f0-167">In the Metadata Objects pane, expand the **Employee** node, and then expand the **Methods** node.</span></span>  
  
    2.  <span data-ttu-id="519f0-168">依序展開**選取**方法，以滑鼠右鍵按一下**篩選**，然後按一下**加入篩選**。</span><span class="sxs-lookup"><span data-stu-id="519f0-168">Expand the **Select** method, right-click **Filters**, and then click **Add Filter**.</span></span>  
  
         <span data-ttu-id="519f0-169">![將篩選加入至 SELECT 方法](../../adapters-and-accelerators/adapter-oracle-ebs/media/08-add-filter.gif "08_Add_Filter")</span><span class="sxs-lookup"><span data-stu-id="519f0-169">![Add a filter to the SELECT method](../../adapters-and-accelerators/adapter-oracle-ebs/media/08-add-filter.gif "08_Add_Filter")</span></span>  
  
    3.  <span data-ttu-id="519f0-170">在 [屬性] 窗格中，如**FilterType**屬性中，選取**等於**。</span><span class="sxs-lookup"><span data-stu-id="519f0-170">In the Properties pane, for the **FilterType** property, select **Equals**.</span></span>  
  
    4.  <span data-ttu-id="519f0-171">在 屬性 窗格中，輸入**EmployeeName**中**名稱** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="519f0-171">In the Properties pane, type **EmployeeName** in the **Name** box.</span></span>  
  
         <span data-ttu-id="519f0-172">![指定篩選條件屬性](../../adapters-and-accelerators/adapter-oracle-ebs/media/09-filter-properties.gif "09_Filter_Properties")</span><span class="sxs-lookup"><span data-stu-id="519f0-172">![Specify filter properties](../../adapters-and-accelerators/adapter-oracle-ebs/media/09-filter-properties.gif "09_Filter_Properties")</span></span>  
  
2.  <span data-ttu-id="519f0-173">若要將篩選器對應**篩選條件**中的參數**選取**方法。</span><span class="sxs-lookup"><span data-stu-id="519f0-173">Map the filter to the **FILTER** parameter in the **Select** method.</span></span>  
  
    1.  <span data-ttu-id="519f0-174">在 [中繼資料物件] 窗格中，依序展開**員工**節點，然後展開**方法**節點。</span><span class="sxs-lookup"><span data-stu-id="519f0-174">In the Metadata Objects pane, expand the **Employee** node, and then expand the **Methods** node.</span></span>  
  
    2.  <span data-ttu-id="519f0-175">依序展開**選取 **方法，然後展開**參數**節點。</span><span class="sxs-lookup"><span data-stu-id="519f0-175">Expand the **Select** method, and then expand the **Parameters** node.</span></span>  
  
    3.  <span data-ttu-id="519f0-176">依序展開**篩選器**節點，然後按一下第二個**篩選**節點。</span><span class="sxs-lookup"><span data-stu-id="519f0-176">Expand the **FILTER** node, and click the second **FILTER** node.</span></span>  
  
    4.  <span data-ttu-id="519f0-177">在 [屬性] 窗格中，選取**EmployeeName**從**FilterDescriptor**清單。</span><span class="sxs-lookup"><span data-stu-id="519f0-177">In the Properties pane, select **EmployeeName** from the **FilterDescriptor** list.</span></span>  
  
         <span data-ttu-id="519f0-178">![將篩選條件對應至 Select 方法參數](../../adapters-and-accelerators/adapter-oracle-ebs/media/10-map-filter.gif "10_Map_Filter")</span><span class="sxs-lookup"><span data-stu-id="519f0-178">![Map the filter to the Select method parameter](../../adapters-and-accelerators/adapter-oracle-ebs/media/10-map-filter.gif "10_Map_Filter")</span></span>  
  
#### <a name="to-create-a-finder-method-instance-for-the-select-method"></a><span data-ttu-id="519f0-179">若要建立 Finder 方法執行個體，Select 方法</span><span class="sxs-lookup"><span data-stu-id="519f0-179">To create a Finder method instance for the Select method</span></span>  
  
1.  <span data-ttu-id="519f0-180">在 [中繼資料物件] 窗格中，依序展開**員工**節點，然後展開**方法**節點。</span><span class="sxs-lookup"><span data-stu-id="519f0-180">In the Metadata Objects pane, expand the **Employee** node, and then expand the **Methods** node.</span></span>  
  
2.  <span data-ttu-id="519f0-181">依序展開**選取 **節點，以滑鼠右鍵按一下**執行個體**，然後按一下 **新增方法執行個體**。</span><span class="sxs-lookup"><span data-stu-id="519f0-181">Expand the **Select** node, right-click **Instances**, and then click **Add Method Instance**.</span></span>  
  
     <span data-ttu-id="519f0-182">![新增方法執行個體](../../adapters-and-accelerators/adapter-oracle-ebs/media/11-add-method-instance.gif "11_Add_Method_Instance")</span><span class="sxs-lookup"><span data-stu-id="519f0-182">![Add a method instance](../../adapters-and-accelerators/adapter-oracle-ebs/media/11-add-method-instance.gif "11_Add_Method_Instance")</span></span>  
  
3.  <span data-ttu-id="519f0-183">在 [建立方法執行個體] 視窗中，按一下**Finder** for**方法執行個體類型**。</span><span class="sxs-lookup"><span data-stu-id="519f0-183">In the Create Method Instance window, click **Finder** for **Method Instance Type**.</span></span> <span data-ttu-id="519f0-184">選取 **會傳回**for**的傳回 TypeDescriptor**。</span><span class="sxs-lookup"><span data-stu-id="519f0-184">Select **Return** for **Return TypeDescriptor**.</span></span>  
  
     <span data-ttu-id="519f0-185">![建立 Finder 方法執行個體](../../adapters-and-accelerators/adapter-oracle-ebs/media/12-create-method-instance.gif "12_Create_Method_Instance")</span><span class="sxs-lookup"><span data-stu-id="519f0-185">![Create a Finder method instance](../../adapters-and-accelerators/adapter-oracle-ebs/media/12-create-method-instance.gif "12_Create_Method_Instance")</span></span>  
  
4.  <span data-ttu-id="519f0-186">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="519f0-186">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="519f0-187">在 屬性 窗格中，輸入**Finder_Instance**中**名稱** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="519f0-187">In the Properties pane, type **Finder_Instance** in the **Name** box.</span></span>  
  
     <span data-ttu-id="519f0-188">![指定 Finder 方法執行個體的名稱](../../adapters-and-accelerators/adapter-oracle-ebs/media/13-instance-property.gif "13_Instance_Property")</span><span class="sxs-lookup"><span data-stu-id="519f0-188">![Specify a name for the Finder method instance](../../adapters-and-accelerators/adapter-oracle-ebs/media/13-instance-property.gif "13_Instance_Property")</span></span>  
  
##  <a name="Scenario2"></a> <span data-ttu-id="519f0-189">案例 2： 從 Microsoft Office SharePoint Server MS_SAMPLE_EMPLOYEE 介面資料表上的全文檢索搜尋</span><span class="sxs-lookup"><span data-stu-id="519f0-189">Scenario 2: Full-Text Search on MS_SAMPLE_EMPLOYEE Interface Table from Microsoft Office SharePoint Server</span></span>  
 <span data-ttu-id="519f0-190">若要建立可用來從 Microsoft Office SharePoint Server MS_SAMPLE_EMPLOYEE 介面資料表上執行的全文檢索搜尋的應用程式定義檔，您必須執行下列一組工作。</span><span class="sxs-lookup"><span data-stu-id="519f0-190">To create an application definition file that can be used to perform a full-text search on MS_SAMPLE_EMPLOYEE interface table from Microsoft Office SharePoint Server, you must perform the following set of tasks.</span></span>  
  
-   <span data-ttu-id="519f0-191">在 **選取**方法，建立識別項，並將它對應至篩選參數和傳回值可儲存員工名稱。</span><span class="sxs-lookup"><span data-stu-id="519f0-191">In the **Select** method, create an identifier, and map it to the FILTER parameter and the return value that stores the employee name.</span></span>  
  
-   <span data-ttu-id="519f0-192">建立**特定的 Finder**方法執行個體**選取**。</span><span class="sxs-lookup"><span data-stu-id="519f0-192">Create a **Specific Finder** method instance for the **Select**.</span></span> <span data-ttu-id="519f0-193">**特定的 Finder**方法可以找出特定的記錄識別碼為基礎，也就是將員工的姓名。</span><span class="sxs-lookup"><span data-stu-id="519f0-193">The **Specific Finder** method will find a specific record based on the identifier, that is, an employee name.</span></span>  
  
-   <span data-ttu-id="519f0-194">建立 ID Enumerator 方法執行個體。</span><span class="sxs-lookup"><span data-stu-id="519f0-194">Create an ID Enumerator method instance.</span></span>  
  
#### <a name="to-create-an-identifier-and-map-it-to-the-filter-parameter-and-employee-name-return-value"></a><span data-ttu-id="519f0-195">建立識別項，並將其對應至篩選參數及員工名稱傳回值</span><span class="sxs-lookup"><span data-stu-id="519f0-195">To create an identifier, and map it to the FILTER parameter and employee name return value</span></span>  
  
1.  <span data-ttu-id="519f0-196">建立的識別項**員工**實體。</span><span class="sxs-lookup"><span data-stu-id="519f0-196">Create an identifier for the **Employee** entity.</span></span>  
  
    1.  <span data-ttu-id="519f0-197">在 [中繼資料物件] 窗格中，依序展開**員工**節點。</span><span class="sxs-lookup"><span data-stu-id="519f0-197">In the Metadata Objects pane, expand the **Employee** node.</span></span>  
  
    2.  <span data-ttu-id="519f0-198">以滑鼠右鍵按一下**識別碼**節點，，然後選取**新增識別碼**。</span><span class="sxs-lookup"><span data-stu-id="519f0-198">Right-click the **Identifiers** node, and then select **Add Identifier**.</span></span>  
  
         <span data-ttu-id="519f0-199">![建立識別項](../../adapters-and-accelerators/adapter-oracle-ebs/media/14-create-identifier.gif "14_Create_Identifier")</span><span class="sxs-lookup"><span data-stu-id="519f0-199">![Create an Identifier](../../adapters-and-accelerators/adapter-oracle-ebs/media/14-create-identifier.gif "14_Create_Identifier")</span></span>  
  
    3.  <span data-ttu-id="519f0-200">在 屬性 窗格中，輸入**EmployeeName**中**名稱** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="519f0-200">In the Properties pane, type **EmployeeName** in the **Name** box.</span></span>  
  
    4.  <span data-ttu-id="519f0-201">選取 [ **System.String** for**型別**] 方塊中。</span><span class="sxs-lookup"><span data-stu-id="519f0-201">Select **System.String** for the **Type** box.</span></span>  
  
         <span data-ttu-id="519f0-202">![指定識別項屬性](../../adapters-and-accelerators/adapter-oracle-ebs/media/15-identifier-properties.gif "15_Identifier_Properties")</span><span class="sxs-lookup"><span data-stu-id="519f0-202">![Specify identifier properties](../../adapters-and-accelerators/adapter-oracle-ebs/media/15-identifier-properties.gif "15_Identifier_Properties")</span></span>  
  
2.  <span data-ttu-id="519f0-203">將識別碼對應至篩選參數，如**選取**方法。</span><span class="sxs-lookup"><span data-stu-id="519f0-203">Map the identifier to the FILTER parameter for the **Select** method.</span></span>  
  
    1.  <span data-ttu-id="519f0-204">在 [中繼資料物件] 窗格中，依序展開**員工**節點，然後展開**方法**節點。</span><span class="sxs-lookup"><span data-stu-id="519f0-204">In the Metadata Objects pane, expand the **Employee** node, and then expand the **Methods** node.</span></span>  
  
    2.  <span data-ttu-id="519f0-205">依序展開**選取 **方法，然後展開**參數**節點。</span><span class="sxs-lookup"><span data-stu-id="519f0-205">Expand the **Select** method, and then expand the **Parameters** node.</span></span>  
  
    3.  <span data-ttu-id="519f0-206">依序展開**篩選條件**參數，然後按一下 第二個**篩選**節點。</span><span class="sxs-lookup"><span data-stu-id="519f0-206">Expand the **FILTER** parameter, and then click the second **FILTER** node.</span></span>  
  
    4.  <span data-ttu-id="519f0-207">在 [屬性] 窗格中，選取**EmployeeName [Employee]** 從**識別項**清單。</span><span class="sxs-lookup"><span data-stu-id="519f0-207">In the Properties pane, select **EmployeeName[Employee]** from the **Identifier** list.</span></span>  
  
         <span data-ttu-id="519f0-208">![設定 FILTER 參數的識別項](../../adapters-and-accelerators/adapter-oracle-ebs/media/16-set-identifier.gif "16_Set_Identifier")</span><span class="sxs-lookup"><span data-stu-id="519f0-208">![Setting identifier for the FILTER parameter](../../adapters-and-accelerators/adapter-oracle-ebs/media/16-set-identifier.gif "16_Set_Identifier")</span></span>  
  
3.  <span data-ttu-id="519f0-209">將識別碼對應至員工名稱的傳回值。</span><span class="sxs-lookup"><span data-stu-id="519f0-209">Map the identifier to the employee name return value.</span></span>  
  
    1.  <span data-ttu-id="519f0-210">在 [中繼資料物件] 窗格中，依序展開**員工**節點，然後展開**方法**節點。</span><span class="sxs-lookup"><span data-stu-id="519f0-210">In the Metadata Objects pane, expand the **Employee** node, and then expand the **Methods** node.</span></span>  
  
    2.  <span data-ttu-id="519f0-211">依序展開**選取 **方法，然後展開**參數**節點。</span><span class="sxs-lookup"><span data-stu-id="519f0-211">Expand the **Select** method, and then expand the **Parameters** node.</span></span>  
  
    3.  <span data-ttu-id="519f0-212">依序展開**會傳回**節點，然後第二個**傳回**節點，則**項目**節點，然後再按一下**名稱**節點。</span><span class="sxs-lookup"><span data-stu-id="519f0-212">Expand the **Return** node, then the second **Return** node, then the **Item** node, and then click the **Name** node.</span></span>  
  
    4.  <span data-ttu-id="519f0-213">在 [屬性] 窗格中，選取**EmployeeName [Employee]** 從**識別項**清單。</span><span class="sxs-lookup"><span data-stu-id="519f0-213">In the Properties pane, select **EmployeeName[Employee]** from the **Identifier** list.</span></span>  
  
#### <a name="to-create-a-specific-finder-method-instance-for-the-select-method"></a><span data-ttu-id="519f0-214">若要建立特定的 Finder 方法執行個體，Select 方法</span><span class="sxs-lookup"><span data-stu-id="519f0-214">To create a Specific Finder method instance for the Select method</span></span>  
  
1.  <span data-ttu-id="519f0-215">在 [中繼資料物件] 窗格中，依序展開**員工**節點，然後**方法**節點。</span><span class="sxs-lookup"><span data-stu-id="519f0-215">In the Metadata Objects pane, expand the **Employee** node, and then the **Methods** node.</span></span>  
  
2.  <span data-ttu-id="519f0-216">依序展開**選取**節點，以滑鼠右鍵按一下**執行個體**，然後選取**新增方法執行個體**以開啟 [建立方法執行個體] 視窗。</span><span class="sxs-lookup"><span data-stu-id="519f0-216">Expand the **Select** node, right-click **Instances**, and then select **Add Method Instance** to open the Create Method Instance window.</span></span>  
  
     <span data-ttu-id="519f0-217">![新增方法執行個體](../../adapters-and-accelerators/adapter-oracle-ebs/media/11-add-method-instance.gif "11_Add_Method_Instance")</span><span class="sxs-lookup"><span data-stu-id="519f0-217">![Add a method instance](../../adapters-and-accelerators/adapter-oracle-ebs/media/11-add-method-instance.gif "11_Add_Method_Instance")</span></span>  
  
3.  <span data-ttu-id="519f0-218">在 [建立方法執行個體] 視窗中，選取**Specific Finder** for**方法執行個體類型**。</span><span class="sxs-lookup"><span data-stu-id="519f0-218">In the Create Method Instance window, select **Specific Finder** for **Method Instance Type**.</span></span> <span data-ttu-id="519f0-219">選取 **會傳回**for**的傳回 TypeDescriptor**。</span><span class="sxs-lookup"><span data-stu-id="519f0-219">Select **Return** for **Return TypeDescriptor**.</span></span>  
  
     <span data-ttu-id="519f0-220">![新增 Specific Finder 方法執行個體](../../adapters-and-accelerators/adapter-oracle-ebs/media/17-specific-finder.gif "17_Specific_Finder")</span><span class="sxs-lookup"><span data-stu-id="519f0-220">![Add a Specific Finder method instance](../../adapters-and-accelerators/adapter-oracle-ebs/media/17-specific-finder.gif "17_Specific_Finder")</span></span>  
  
4.  <span data-ttu-id="519f0-221">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="519f0-221">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="519f0-222">在 屬性 窗格中，輸入**SpeciFinder_Instance** for**名稱** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="519f0-222">In the Properties pane, type **SpeciFinder_Instance** for the **Name** box.</span></span>  
  
#### <a name="to-create-an-id-enumerator-method-instance-for-the-select-method"></a><span data-ttu-id="519f0-223">若要建立 Id Enumerator 方法執行個體的 Select 方法</span><span class="sxs-lookup"><span data-stu-id="519f0-223">To create an Id Enumerator method instance for the Select method</span></span>  
  
1.  <span data-ttu-id="519f0-224">在 [中繼資料物件] 窗格中，依序展開**員工**節點，然後**方法**節點。</span><span class="sxs-lookup"><span data-stu-id="519f0-224">In the Metadata Objects pane, expand the **Employee** node, and then the **Methods** node.</span></span>  
  
2.  <span data-ttu-id="519f0-225">依序展開**選取**節點，以滑鼠右鍵按一下**執行個體**，然後選取**新增方法執行個體**以開啟 [建立方法執行個體] 視窗。</span><span class="sxs-lookup"><span data-stu-id="519f0-225">Expand the **Select** node, right-click **Instances**, and then select **Add Method Instance** to open the Create Method Instance window.</span></span>  
  
     <span data-ttu-id="519f0-226">![新增方法執行個體](../../adapters-and-accelerators/adapter-oracle-ebs/media/11-add-method-instance.gif "11_Add_Method_Instance")</span><span class="sxs-lookup"><span data-stu-id="519f0-226">![Add a method instance](../../adapters-and-accelerators/adapter-oracle-ebs/media/11-add-method-instance.gif "11_Add_Method_Instance")</span></span>  
  
3.  <span data-ttu-id="519f0-227">在 [建立方法執行個體] 視窗中，選取**Id Enumerator** for**方法執行個體類型**。</span><span class="sxs-lookup"><span data-stu-id="519f0-227">In the Create Method Instance window, select **Id Enumerator** for **Method Instance Type**.</span></span> <span data-ttu-id="519f0-228">選取 **會傳回**for**的傳回 TypeDescriptor**。</span><span class="sxs-lookup"><span data-stu-id="519f0-228">Select **Return** for **Return TypeDescriptor**.</span></span>  
  
     <span data-ttu-id="519f0-229">![建立 Id Enumerator 方法執行個體](../../adapters-and-accelerators/adapter-oracle-ebs/media/18-id-enumerator.gif "18_ID_Enumerator")</span><span class="sxs-lookup"><span data-stu-id="519f0-229">![Create an Id Enumerator method instance](../../adapters-and-accelerators/adapter-oracle-ebs/media/18-id-enumerator.gif "18_ID_Enumerator")</span></span>  
  
4.  <span data-ttu-id="519f0-230">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="519f0-230">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="519f0-231">在 屬性 窗格中，輸入**IDEnumerator_Instance** for**名稱** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="519f0-231">In the Properties pane, type **IDEnumerator_Instance** for the **Name** box.</span></span>  
  
##  <a name="Defaults"></a> <span data-ttu-id="519f0-232">設定預設參數的方法執行個體</span><span class="sxs-lookup"><span data-stu-id="519f0-232">Set Default Parameters for the Method Instances</span></span>  
 <span data-ttu-id="519f0-233">Select 方法會要求您指定的資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="519f0-233">The Select method requires you to specify the column names.</span></span> <span data-ttu-id="519f0-234">因此，您需要指定的預設值**COLUMN_NAMES**稍早建立的搜尋、 特定搜尋工具和 Id Enumerator 方法執行個體的參數。</span><span class="sxs-lookup"><span data-stu-id="519f0-234">Therefore, you need to specify a default value for the **COLUMN_NAMES** parameter for the Finder, Specific Finder, and Id Enumerator method instances created earlier.</span></span> <span data-ttu-id="519f0-235">此外，您也應該指定的預設值**篩選**Id Enumerator 方法執行個體的參數。</span><span class="sxs-lookup"><span data-stu-id="519f0-235">Additionally, you should also specify a default value for the **FILTER** parameter for the Id Enumerator method instance.</span></span>  
  
#### <a name="to-set-the-default-parameters-for-the-method-instances"></a><span data-ttu-id="519f0-236">若要設定的方法執行個體的預設參數</span><span class="sxs-lookup"><span data-stu-id="519f0-236">To set the default parameters for the method instances</span></span>  
  
1.  <span data-ttu-id="519f0-237">在 [中繼資料物件] 窗格中，依序展開**員工**節點，然後展開**方法**節點。</span><span class="sxs-lookup"><span data-stu-id="519f0-237">In the Metadata Objects pane, expand the **Employee** node, and then expand the **Methods** node.</span></span>  
  
2.  <span data-ttu-id="519f0-238">依序展開**選取 **節點，然後展開**參數**節點。</span><span class="sxs-lookup"><span data-stu-id="519f0-238">Expand the **Select** node, and then expand the **Parameters** node.</span></span>  
  
3.  <span data-ttu-id="519f0-239">依序展開**COLUMN_NAMES**節點，，然後選取**COLUMN_NAMES**參數。</span><span class="sxs-lookup"><span data-stu-id="519f0-239">Expand the **COLUMN_NAMES** node, and then select the **COLUMN_NAMES** parameter.</span></span>  
  
4.  <span data-ttu-id="519f0-240">在 [屬性] 窗格中，按一下 [省略符號按鈕 （...），以針對**DefaultValues** ] 方塊中。</span><span class="sxs-lookup"><span data-stu-id="519f0-240">In the Properties pane, click the ellipsis button (…) against the **DefaultValues** box.</span></span>  
  
5.  <span data-ttu-id="519f0-241">在  **DefaultValueView 集合編輯器** 對話方塊中，按一下**新增**，然後在 屬性 窗格中，按一下  **Finder_Instance**在**SelectMethodInstance**清單。</span><span class="sxs-lookup"><span data-stu-id="519f0-241">In the **DefaultValueView Collection Editor** dialog box, click **Add**, and in the property pane, click **Finder_Instance** in the **SelectMethodInstance** list.</span></span>  
  
     <span data-ttu-id="519f0-242">![指定 Finder 執行個體的預設值](../../adapters-and-accelerators/adapter-oracle-ebs/media/19-finderinstance-defaults.gif "19_FinderInstance_Defaults")</span><span class="sxs-lookup"><span data-stu-id="519f0-242">![Specifying default value for the Finder instance](../../adapters-and-accelerators/adapter-oracle-ebs/media/19-finderinstance-defaults.gif "19_FinderInstance_Defaults")</span></span>  
  
6.  <span data-ttu-id="519f0-243">型別`*`中**值** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="519f0-243">Type `*` in the **Value** box.</span></span>  
  
7.  <span data-ttu-id="519f0-244">同樣地，重複步驟 5 和 6 來新增的預設值**SpecificFinder_Instance**並**IDEnumerator_Instance**方法執行個體。</span><span class="sxs-lookup"><span data-stu-id="519f0-244">Similarly, repeat steps 5 and 6 to add default values for the **SpecificFinder_Instance** and **IDEnumerator_Instance** method instances.</span></span>  
  
8.  <span data-ttu-id="519f0-245">在 [ **DefaultValueView 集合編輯器**] 對話方塊中，按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="519f0-245">In the **DefaultValueView Collection Editor** dialog box, click **OK**.</span></span>  
  
9. <span data-ttu-id="519f0-246">接下來，新增的預設值**篩選條件**參數**IDEnumerator_Instance**方法執行個體。</span><span class="sxs-lookup"><span data-stu-id="519f0-246">Next, add a default value for the **FILTER** parameter for the **IDEnumerator_Instance** method instance.</span></span> <span data-ttu-id="519f0-247">依序展開**篩選條件**節點，，然後選取**篩選**參數。</span><span class="sxs-lookup"><span data-stu-id="519f0-247">Expand the **FILTER** node, and then select the **FILTER** parameter.</span></span>  
  
10. <span data-ttu-id="519f0-248">在 [屬性] 窗格中，按一下 [省略符號按鈕 （...），以針對**DefaultValues** ] 方塊中。</span><span class="sxs-lookup"><span data-stu-id="519f0-248">In the Properties pane, click the ellipsis button (…) against the **DefaultValues** box.</span></span>  
  
11. <span data-ttu-id="519f0-249">在  **DefaultValueView 集合編輯器** 對話方塊中，按一下**新增**，然後在 屬性 窗格中，按一下  **IDEnumerator_Instance**在**SelectMethodInstance**清單。</span><span class="sxs-lookup"><span data-stu-id="519f0-249">In the **DefaultValueView Collection Editor** dialog box, click **Add**, and in the property pane, click **IDEnumerator_Instance** in the **SelectMethodInstance** list.</span></span>  
  
12. <span data-ttu-id="519f0-250">型別`%`中**值** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="519f0-250">Type `%` in the **Value** box.</span></span>  
  
     <span data-ttu-id="519f0-251">![Id Enumerator 執行個體的預設值](../../adapters-and-accelerators/adapter-oracle-ebs/media/20-idenumeratorinstance-defaults.gif "20_IDEnumeratorInstance_Defaults")</span><span class="sxs-lookup"><span data-stu-id="519f0-251">![Default values for the Id Enumerator instance](../../adapters-and-accelerators/adapter-oracle-ebs/media/20-idenumeratorinstance-defaults.gif "20_IDEnumeratorInstance_Defaults")</span></span>  
  
13. <span data-ttu-id="519f0-252">在 [ **DefaultValueView 集合編輯器**] 對話方塊中，按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="519f0-252">In the **DefaultValueView Collection Editor** dialog box, click **OK**.</span></span>  
  
##  <a name="SSO"></a> <span data-ttu-id="519f0-253">連線到 Oracle E-business Suite 中設定單一登入設定</span><span class="sxs-lookup"><span data-stu-id="519f0-253">Set up Single Sign-On for Connecting to Oracle E-Business Suite</span></span>  
 <span data-ttu-id="519f0-254">執行本主題中的所有程序完成之後，您會建立可匯入 SharePoint 應用程式的應用程式定義檔。</span><span class="sxs-lookup"><span data-stu-id="519f0-254">After you have finished performing all the procedures in this topic, you will have created an application definition file that can be imported into a SharePoint application.</span></span> <span data-ttu-id="519f0-255">從應用程式，您叫用的方法來擷取 Oracle E-business Suite 中的相關資料。</span><span class="sxs-lookup"><span data-stu-id="519f0-255">From the application, you invoke the methods to retrieve relevant data from Oracle E-Business Suite.</span></span> <span data-ttu-id="519f0-256">若要這麼做，您必須在 SharePoint 應用程式中建立 Oracle E-business Suite 中的使用者與使用者之間的對應。</span><span class="sxs-lookup"><span data-stu-id="519f0-256">To enable this, you must create a mapping between a user in the Oracle E-Business Suite and the user in the SharePoint application.</span></span> <span data-ttu-id="519f0-257">您已匯入應用程式定義檔之後，您可以建立在 SharePoint 中央系統管理主控台中的這種對應。</span><span class="sxs-lookup"><span data-stu-id="519f0-257">You create this mapping in SharePoint Central Administration console after you have imported the application definition file.</span></span>  
  
 <span data-ttu-id="519f0-258">不過，若要建立對應您必須設定屬性**SecondarySsoApplicationId**中商務資料目錄定義編輯器。</span><span class="sxs-lookup"><span data-stu-id="519f0-258">However, to create the mapping you must set a property **SecondarySsoApplicationId** in the Business Data Catalog Definition Editor.</span></span>  
  
#### <a name="to-set-the-secondaryssoapplicationid-property"></a><span data-ttu-id="519f0-259">若要設定 SecondarySsoApplicationId 屬性</span><span class="sxs-lookup"><span data-stu-id="519f0-259">To set the SecondarySsoApplicationId property</span></span>  
  
1.  <span data-ttu-id="519f0-260">在 [中繼資料物件] 窗格中，依序展開**MS_SAMPLE_EMPLOYEE**節點，然後展開**執行個體**節點。</span><span class="sxs-lookup"><span data-stu-id="519f0-260">In the Metadata Objects pane, expand the **MS_SAMPLE_EMPLOYEE** node, and then expand the **Instances** node.</span></span>  
  
2.  <span data-ttu-id="519f0-261">按一下  **MS_SAMPLE_EMPLOYEE_Instance**，並在 屬性 窗格中，按一下 省略符號 （...） 按鈕，針對**屬性** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="519f0-261">Click **MS_SAMPLE_EMPLOYEE_Instance**, and in the Properties pane, click the ellipsis (…) button against the **Properties** box.</span></span>  
  
3.  <span data-ttu-id="519f0-262">在  **PropertyView 集合編輯器** 對話方塊中，按一下**新增**，然後在 屬性 窗格中，輸入**SecondarySsoApplicationId**的**名稱**  方塊中。</span><span class="sxs-lookup"><span data-stu-id="519f0-262">In the **PropertyView Collection Editor** dialog box, click **Add**, and in the Property pane, type **SecondarySsoApplicationId** for the **Name** box.</span></span> <span data-ttu-id="519f0-263">同樣地，輸入**OracleSSO** for **PropertyValue**  方塊中。</span><span class="sxs-lookup"><span data-stu-id="519f0-263">Similarly, type **OracleSSO** for the **PropertyValue** box.</span></span> <span data-ttu-id="519f0-264">選取 [ **System.String** for**型別**] 方塊中。</span><span class="sxs-lookup"><span data-stu-id="519f0-264">Select **System.String** for the **Type** box.</span></span>  
  
     <span data-ttu-id="519f0-265">![新增 SSO 屬性](../../adapters-and-accelerators/adapter-oracle-ebs/media/21-sso.gif "21_SSO")</span><span class="sxs-lookup"><span data-stu-id="519f0-265">![Add the SSO Property](../../adapters-and-accelerators/adapter-oracle-ebs/media/21-sso.gif "21_SSO")</span></span>  
  
4.  <span data-ttu-id="519f0-266">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="519f0-266">Click **OK**.</span></span>  
  
##  <a name="Export"></a> <span data-ttu-id="519f0-267">匯出至檔案的應用程式定義</span><span class="sxs-lookup"><span data-stu-id="519f0-267">Export the Application Definition to a File</span></span>  
 <span data-ttu-id="519f0-268">您現在已建立應用程式定義，其中包含 Oracle E-business Suite 執行個體中繼資料。</span><span class="sxs-lookup"><span data-stu-id="519f0-268">You have now created an application definition that contains Oracle E-Business Suite instance metadata.</span></span> <span data-ttu-id="519f0-269">您必須將此定義匯出至 XML 檔案，可匯入至 Microsoft Office SharePoint Server。</span><span class="sxs-lookup"><span data-stu-id="519f0-269">You must export this definition to an XML file, which can be imported into Microsoft Office SharePoint Server.</span></span>  
  
#### <a name="to-export-the-application-definition-to-a-file"></a><span data-ttu-id="519f0-270">若要將應用程式定義匯出至檔案</span><span class="sxs-lookup"><span data-stu-id="519f0-270">To export the application definition to a file</span></span>  
  
1.  <span data-ttu-id="519f0-271">在 [中繼資料物件] 窗格中，以滑鼠右鍵按一下**MS_SAMPLE_EMPLOYEE**節點，然後再按一下**匯出**。</span><span class="sxs-lookup"><span data-stu-id="519f0-271">In the Metadata Objects pane, right-click the **MS_SAMPLE_EMPLOYEE** node, and then click **Export**.</span></span>  
  
2.  <span data-ttu-id="519f0-272">將檔案儲存為 Employee.xml 中。</span><span class="sxs-lookup"><span data-stu-id="519f0-272">Save the file as Employee.xml.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="519f0-273">後續步驟</span><span class="sxs-lookup"><span data-stu-id="519f0-273">Next Steps</span></span>  
 <span data-ttu-id="519f0-274">您現在必須建立 SharePoint 應用程式來擷取 Oracle E-business Suite 中的資料。</span><span class="sxs-lookup"><span data-stu-id="519f0-274">You must now create a SharePoint application to retrieve data from Oracle E-Business Suite.</span></span> <span data-ttu-id="519f0-275">如需相關指示，請參閱 <<c0> [ 步驟 3： 建立 SharePoint 應用程式以擷取資料從 Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/step-3-create-a-sharepoint-application-to-retrieve-data-from-oracle-ebs.md)。</span><span class="sxs-lookup"><span data-stu-id="519f0-275">For instructions, see [Step 3: Create a SharePoint Application to Retrieve Data from Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/step-3-create-a-sharepoint-application-to-retrieve-data-from-oracle-ebs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="519f0-276">另請參閱</span><span class="sxs-lookup"><span data-stu-id="519f0-276">See Also</span></span>  
 [<span data-ttu-id="519f0-277">教學課程： 將資料呈現從 SharePoint 網站上的 Oracle E-business Suite</span><span class="sxs-lookup"><span data-stu-id="519f0-277">Tutorial: Present Data from Oracle E-Business Suite on a SharePoint Site</span></span>](Tutorial:%20Present%20data%20from%20Oracle%20E-Business%20Suite%20on%20a%20SharePoint%20Site.md)