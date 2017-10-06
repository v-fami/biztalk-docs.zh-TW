---
title: "如何： 將交換分割，並將產生的訊息路由至多個檔案位置使用不同的行程 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ccd46bee-e4a1-4846-8bde-b0460bda1e72
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4c752c4b98f6a68e0a86ba4a418eab0705a7c513
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-split-an-interchange-and-route-the-resulting-messages-to-multiple-file-locations-using-distinct-itineraries"></a><span data-ttu-id="6d1f9-102">如何： 將交換分割，並將產生的訊息路由至多個使用不同的行程的檔案位置</span><span class="sxs-lookup"><span data-stu-id="6d1f9-102">How to: Split an Interchange and Route the Resulting Messages to Multiple File Locations Using Distinct Itineraries</span></span>
## <a name="goal"></a><span data-ttu-id="6d1f9-103">目標</span><span class="sxs-lookup"><span data-stu-id="6d1f9-103">Goal</span></span>  
 <span data-ttu-id="6d1f9-104">本節示範如何建立 ESB 上手使用**ItinerarySelectReceiveXml**略過的管線，以及如何設定管線元件來分割輸入的交換和選取適當的路由每個產生的訊息，根據訊息內容。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-104">This section demonstrates how to create an ESB on-ramp that uses the **ItinerarySelectReceiveXml** pipeline and how to configure the pipeline's components to split an inbound interchange and select the appropriate routing slip for each resulting message, based on message context.</span></span> <span data-ttu-id="6d1f9-105">會使用商務規則原則，解析路線的選取項目，訊息會路由傳送不同客戶的所在的區域為基礎。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-105">Itinerary selection will be resolved using a business rules policy, and messages will be routed differently based on the region in which the customer resides.</span></span>  
  
 <span data-ttu-id="6d1f9-106">在此 「 如何 」 主題，您將完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="6d1f9-106">In this How-to topic, you will complete the following steps:</span></span>  
  
-   <span data-ttu-id="6d1f9-107">建立 ESB 上手分割 XML 交換。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-107">Create an ESB on-ramp that splits an XML interchange.</span></span>  
  
-   <span data-ttu-id="6d1f9-108">設定要用來選取適當的行程的商務規則原則路線選取器管線元件。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-108">Configure the Itinerary Selector pipeline component to use a business rules policy to select the appropriate itinerary.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="6d1f9-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="6d1f9-109">Prerequisites</span></span>  
 <span data-ttu-id="6d1f9-110">在此 「 如何 」 主題中的程序需要完成[開發活動的必要條件](../esb-toolkit/prerequisites-for-the-development-activities.md)。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-110">The procedures in this How-to topic require the completion of the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md).</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="6d1f9-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="6d1f9-111">Before You Begin</span></span>  
 <span data-ttu-id="6d1f9-112">在執行本使用說明主題中稍後的步驟之前，請完成下列工作：</span><span class="sxs-lookup"><span data-stu-id="6d1f9-112">Complete the following tasks before you perform the steps later in this How-to topic:</span></span>  
  
-   <span data-ttu-id="6d1f9-113">建立必要的成品。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-113">Create the required artifacts.</span></span>  
  
-   <span data-ttu-id="6d1f9-114">將結構描述專案加入至模式的方案。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-114">Add a schemas project to the Patterns solution.</span></span>  
  
-   <span data-ttu-id="6d1f9-115">將成品新增至結構描述專案。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-115">Add the artifacts to the Schemas project.</span></span>  
  
-   <span data-ttu-id="6d1f9-116">建立 BRE 原則，選取 使用自訂訊息屬性的路線。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-116">Create a BRE policy to select an itinerary using custom message properties.</span></span>  
  
-   <span data-ttu-id="6d1f9-117">加入客戶 GlobalBank 西選取範圍規則。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-117">Add a selection rule for customer GlobalBank West.</span></span>  
  
-   <span data-ttu-id="6d1f9-118">加入客戶 GlobalBank 東部的選取範圍規則。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-118">Add a selection rule for customer GlobalBank East.</span></span>  
  
-   <span data-ttu-id="6d1f9-119">發佈和部署原則。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-119">Publish and deploy the policy.</span></span>  
  
-   <span data-ttu-id="6d1f9-120">建立 GlobalBank 西訊息 ESB 路線網域特定領域語言 (DSL) 模型。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-120">Create an ESB itinerary domain-specific language (DSL) model for GlobalBank West messages.</span></span>  
  
-   <span data-ttu-id="6d1f9-121">設定 GlobalBank 西路線的屬性。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-121">Configure the properties of the GlobalBank West itinerary.</span></span>  
  
-   <span data-ttu-id="6d1f9-122">定義 GlobalBank 西路線的結構。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-122">Define the structure of the GlobalBank West itinerary.</span></span>  
  
-   <span data-ttu-id="6d1f9-123">GlobalBank 西模型匯出到路線的資料庫。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-123">Export the GlobalBank West model to the itinerary database.</span></span>  
  
-   <span data-ttu-id="6d1f9-124">建立 GlobalBank 東部訊息的 ESB 路線 DSL 模型。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-124">Create an ESB itinerary DSL model for GlobalBank East messages.</span></span>  
  
-   <span data-ttu-id="6d1f9-125">設定 GlobalBank 東部路線的屬性。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-125">Configure the properties of the GlobalBank East itinerary.</span></span>  
  
-   <span data-ttu-id="6d1f9-126">定義 GlobalBank 東部路線的結構。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-126">Define the structure of the GlobalBank East itinerary.</span></span>  
  
-   <span data-ttu-id="6d1f9-127">GlobalBank 東部模型匯出到路線的資料庫。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-127">Export the GlobalBank East model to the itinerary database.</span></span>  
  
     <span data-ttu-id="6d1f9-128">下列程序說明如何執行每一種。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-128">The following procedures describe how to do each of these.</span></span>  
  
#### <a name="to-create-the-required-artifacts"></a><span data-ttu-id="6d1f9-129">若要建立必要的成品</span><span class="sxs-lookup"><span data-stu-id="6d1f9-129">To create the required artifacts</span></span>  
  
1.  <span data-ttu-id="6d1f9-130">在 Windows 檔案總管，瀏覽至 C:\HowTos。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-130">In Windows Explorer, browse to C:\HowTos.</span></span>  
  
2.  <span data-ttu-id="6d1f9-131">建立名為 OrderDocEnvelope.xsd 新文字文件。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-131">Create a new text document named OrderDocEnvelope.xsd.</span></span>  
  
3.  <span data-ttu-id="6d1f9-132">在記事本中開啟 OrderDocEnvelope.xsd 結構描述。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-132">Open the OrderDocEnvelope.xsd schema in Notepad.</span></span>  
  
4.  <span data-ttu-id="6d1f9-133">編輯文件使用下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-133">Edit the document using the following code.</span></span>  
  
    ```  
    <?xml version="1.0" ?>  
    <xs:schema xmlns:ns0="http://globalbank.esb.dynamicresolution.com/northamericanservices/" xmlns:b="http://schemas.microsoft.com/BizTalk/2003" xmlns="http://ESB.BizUnit.Map.Test" targetNamespace="http://ESB.BizUnit.Map.Test" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  
      <xs:import schemaLocation="GlobalBank.ESB.DynamicResolution.Schemas.NAOrderDoc" namespace="http://globalbank.esb.dynamicresolution.com/northamericanservices/" />  
      <xs:annotation>  
        <xs:appinfo>  
          <b:schemaInfo is_envelope="yes" xmlns:b="http://schemas.microsoft.com/BizTalk/2003" />  
          <b:references>  
            <b:reference targetNamespace="http://globalbank.esb.dynamicresolution.com/northamericanservices/" />  
          </b:references>  
        </xs:appinfo>  
      </xs:annotation>  
      <xs:element name="OrderEnvelope">  
        <xs:annotation>  
          <xs:appinfo>  
            <b:recordInfo body_xpath="/*[local-name()='OrderEnvelope' and namespace-uri()='http://ESB.BizUnit.Map.Test']" />  
          </xs:appinfo>  
        </xs:annotation>  
        <xs:complexType>  
          <xs:sequence>  
            <xs:element ref="ns0:OrderDoc" />  
          </xs:sequence>  
        </xs:complexType>  
      </xs:element>  
    </xs:schema>  
    ```  
  
5.  <span data-ttu-id="6d1f9-134">儲存 OrderDocEnvelope.xsd 為 utf-8，，然後關閉 [記事本]。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-134">Save OrderDocEnvelope.xsd as UTF-8, and then close Notepad.</span></span>  
  
6.  <span data-ttu-id="6d1f9-135">在 [C:\HowTos] 資料夾中，建立名為 Batch.xml 新文字文件。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-135">In the C:\HowTos folder, create a new text document named Batch.xml.</span></span>  
  
7.  <span data-ttu-id="6d1f9-136">在 [記事本] 開啟 Batch.xml。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-136">In Notepad, open Batch.xml.</span></span>  
  
8.  <span data-ttu-id="6d1f9-137">編輯文件使用下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-137">Edit the document using the following code.</span></span>  
  
    ```  
    <?xml version="1.0" ?>  
    <ns0:OrderEnvelope xmlns:ns0="http://ESB.BizUnit.Map.Test">  
      <ns0:OrderDoc xmlns:ns0="http://globalbank.esb.dynamicresolution.com/northamericanservices/">  
        <ns0:customerName>GlobalBankWest</ns0:customerName>  
        <ns0:ID>ns0:ID_0</ns0:ID>  
        <ns0:requestType>10</ns0:requestType>  
      </ns0:OrderDoc>  
      <ns0:OrderDoc xmlns:ns0="http://globalbank.esb.dynamicresolution.com/northamericanservices/">  
        <ns0:customerName>GlobalBankEast</ns0:customerName>  
        <ns0:ID>ns0:ID_0</ns0:ID>  
        <ns0:requestType>11</ns0:requestType>  
      </ns0:OrderDoc>  
      <ns0:OrderDoc xmlns:ns0="http://globalbank.esb.dynamicresolution.com/northamericanservices/">  
        <ns0:customerName>GlobalBankEast</ns0:customerName>  
        <ns0:ID>ns0:ID_0</ns0:ID>  
        <ns0:requestType>12</ns0:requestType>  
      </ns0:OrderDoc>  
    </ns0:OrderEnvelope>  
    ```  
  
9. <span data-ttu-id="6d1f9-138">儲存並關閉 Batch.xml。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-138">Save and close Batch.xml.</span></span>  
  
#### <a name="to-add-a-schemas-project-to-the-patterns-solution"></a><span data-ttu-id="6d1f9-139">將結構描述專案加入至模式的方案</span><span class="sxs-lookup"><span data-stu-id="6d1f9-139">To add a schemas project to the Patterns solution</span></span>  
  
1.  <span data-ttu-id="6d1f9-140">在[!INCLUDE[vs2010](../includes/vs2010-md.md)]，開啟 C:\HowTos\Patterns\Patterns.sln。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-140">In [!INCLUDE[vs2010](../includes/vs2010-md.md)], open C:\HowTos\Patterns\Patterns.sln.</span></span>  
  
2.  <span data-ttu-id="6d1f9-141">在 方案總管 中，以滑鼠右鍵按一下**方案 '模式'**，指向 **新增**，然後按一下**新專案**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-141">In Solution Explorer, right-click **Solution 'Patterns'**, point to **Add**, and then click **New Project**.</span></span>  
  
3.  <span data-ttu-id="6d1f9-142">在**加入新的專案**對話方塊，在 [專案類型] 窗格中，按一下**BizTalk 專案**，然後執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="6d1f9-142">In the **Add New Project** dialog box, in the Project types pane, click **BizTalk Projects**, and then do the following:</span></span>  
  
    1.  <span data-ttu-id="6d1f9-143">在 [範本] 窗格中，按一下**空白 BizTalk Server 專案**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-143">In the Templates pane, click **Empty BizTalk Server Project**.</span></span>  
  
    2.  <span data-ttu-id="6d1f9-144">在**名稱**方塊中，輸入**Patterns.Schemas**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-144">In the **Name** box, type **Patterns.Schemas**, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="6d1f9-145">在 [方案總管] 中，以滑鼠右鍵按一下**Patterns.Schemas**，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-145">In Solution Explorer, right-click **Patterns.Schemas**, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="6d1f9-146">在 [屬性] 視窗上**簽署**索引標籤上，選取**簽署組件**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-146">In the Properties window, on the **Signing** tab, select the **Sign the assembly** check box.</span></span>  
  
6.  <span data-ttu-id="6d1f9-147">在**選擇強式名稱金鑰檔**下拉式清單中，按一下  **\<新增...>**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-147">In the **Choose a strong name key file** drop-down list, click **\<New...>**.</span></span>  
  
7.  <span data-ttu-id="6d1f9-148">在**建立強式名稱金鑰**對話方塊方塊中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="6d1f9-148">In the **Create Strong Name Key** dialog box, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="6d1f9-149">在**金鑰檔名稱**方塊中，輸入**分割**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-149">In the **Key file name** box, type **Splitting**.</span></span>  
  
    2.  <span data-ttu-id="6d1f9-150">清除**保護我的密碼金鑰檔**核取方塊，然後**確定**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-150">Clear the **Protect my key file with a password** check box, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="6d1f9-151">在 [屬性] 視窗上**部署**索引標籤的**應用程式名稱**方塊中，輸入**Microsoft.Practices.ESB**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-151">In the Properties window, on the **Deployment** tab, in the **Application Name** box, type **Microsoft.Practices.ESB**.</span></span>  
  
9. <span data-ttu-id="6d1f9-152">關閉 [屬性] 視窗。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-152">Close the Properties window.</span></span>  
  
#### <a name="to-add-the-artifacts-to-the-schemas-project"></a><span data-ttu-id="6d1f9-153">若要將成品新增至結構描述專案</span><span class="sxs-lookup"><span data-stu-id="6d1f9-153">To add the artifacts to the Schemas project</span></span>  
  
1.  <span data-ttu-id="6d1f9-154">在 [方案總管] 中，以滑鼠右鍵按一下**Patterns.Schemas**，然後按一下**加入參考**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-154">In Solution Explorer, right-click **Patterns.Schemas**, and then click **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="6d1f9-155">在**瀏覽** 索引標籤**加入參考**對話方塊中，瀏覽並選取 C:\Projects\Microsoft.Practices.ESB\Source\Samples\DynamicResolution\Source\ESB。DynamicResolution.Schemas\bin\Debug\GlobalBank.ESB.DynamicResolution.Schemas.dll，然後再按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-155">On the **Browse** tab of the **Add Reference** dialog box, browse to and select C:\Projects\Microsoft.Practices.ESB\Source\Samples\DynamicResolution\Source\ESB.DynamicResolution.Schemas\bin\Debug\GlobalBank.ESB.DynamicResolution.Schemas.dll, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="6d1f9-156">在 方案總管 中，以滑鼠右鍵按一下**Patterns.Schemas**，指向 **新增**，然後按一下**現有項目**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-156">In Solution Explorer, right-click **Patterns.Schemas**, point to **Add**, and then click **Existing Item**.</span></span>  
  
4.  <span data-ttu-id="6d1f9-157">在**加入現有項目**對話方塊中，瀏覽至並選取 C:\HowTos\OrderDocEnvelope.xsd，，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-157">In the **Add Existing Item** dialog box, browse to and select C:\HowTos\OrderDocEnvelope.xsd, and then click **Add**.</span></span>  
  
5.  <span data-ttu-id="6d1f9-158">儲存方案的所有成品。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-158">Save all solution artifacts.</span></span>  
  
6.  <span data-ttu-id="6d1f9-159">在 [方案總管] 中，以滑鼠右鍵按一下**Patterns.Schemas**，然後按一下**部署**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-159">In Solution Explorer, right-click **Patterns.Schemas**, and then click **Deploy**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6d1f9-160">此說明主題使用與中所建立的相同商務規則原則和旅[如何： 選取 使用商務規則原則路線](../esb-toolkit/how-to-select-an-itinerary-using-a-business-rules-policy.md)主題。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-160">This How-to topic uses the same business rules policy and itineraries as those created in the [How to: Select an Itinerary Using a Business Rules Policy](../esb-toolkit/how-to-select-an-itinerary-using-a-business-rules-policy.md) topic.</span></span> <span data-ttu-id="6d1f9-161">如果您尚未完成該區段，請完成下列額外的步驟。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-161">If you have not already completed that section, please complete the following additional steps.</span></span> <span data-ttu-id="6d1f9-162">如果您已經完成該區段，繼續 < 步驟 > 一節。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-162">If you have completed that section, continue directly to the "Steps" section.</span></span>  
  
#### <a name="to-create-a-business-rules-engine-bre-policy-to-select-an-itinerary-using-custom-message-properties"></a><span data-ttu-id="6d1f9-163">若要建立商務規則引擎 (BRE) 原則，選取 使用自訂訊息屬性路線</span><span class="sxs-lookup"><span data-stu-id="6d1f9-163">To create a Business Rules Engine (BRE) policy to select an itinerary using custom message properties</span></span>  
  
1.  <span data-ttu-id="6d1f9-164">按一下**啟動**在工作列上，指向**所有程式**，指向   **[!INCLUDE[prague](../includes/prague-md.md)]** ，然後按一下**商務規則編輯器 」**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-164">Click **Start** on the taskbar, point to **All Programs**, point to **[!INCLUDE[prague](../includes/prague-md.md)]**, and then click **Business Rule Composer**.</span></span>  
  
2.  <span data-ttu-id="6d1f9-165">在 [原則總管] 中，以滑鼠右鍵按一下**原則**，然後按一下**新增原則**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-165">In Policy Explorer, right-click **Policies**, and then click **Add New Policy**.</span></span> <span data-ttu-id="6d1f9-166">命名原則**ResolveItineraryBasedOnCustomer**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-166">Name the policy **ResolveItineraryBasedOnCustomer**.</span></span>  
  
#### <a name="to-add-a-selection-rule-for-customer-globalbank-west"></a><span data-ttu-id="6d1f9-167">若要加入客戶 GlobalBank 西的選取範圍規則</span><span class="sxs-lookup"><span data-stu-id="6d1f9-167">To add a selection rule for customer GlobalBank West</span></span>  
  
1.  <span data-ttu-id="6d1f9-168">在**ResolveItineraryBasedOnCustomer**原則，以滑鼠右鍵按一下**版本 1.0 （未儲存）**，然後按一下**新增規則**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-168">In the **ResolveItineraryBasedOnCustomer** policy, right-click **Version 1.0 (not saved)**, and then click **Add New Rule**.</span></span> <span data-ttu-id="6d1f9-169">命名規則**SetGlobalBankWestItinerary**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-169">Name the rule **SetGlobalBankWestItinerary**.</span></span>  
  
2.  <span data-ttu-id="6d1f9-170">在 事實總管 中，按一下  **XML 結構描述**索引標籤上，以滑鼠右鍵按一下**結構描述**，然後按一下**瀏覽**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-170">In Facts Explorer, click the **XML Schemas** tab, right-click **Schemas**, and then click **Browse**.</span></span>  
  
3.  <span data-ttu-id="6d1f9-171">在**結構描述檔案**對話方塊中，瀏覽至 C:\Projects\Microsoft.Practices.ESB\Source\Samples\DynamicResolution\Source\ESB。DynamicResolution.Schemas，選取 NAOrderDoc.xsd，，然後按一下**開啟**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-171">In the **Schema Files** dialog box, browse to C:\Projects\Microsoft.Practices.ESB\Source\Samples\DynamicResolution\Source\ESB.DynamicResolution.Schemas, select NAOrderDoc.xsd, and then click **Open**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6d1f9-172">這是定義用來建立將用於測試的西和東訊息 NAOrderDoc.xml 訊息的結構描述。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-172">This is the schema that defines the NAOrderDoc.xml message, which was used to create the West and East messages you will use for testing.</span></span>  
  
4.  <span data-ttu-id="6d1f9-173">在 事實總管 中，按一下 NAOrderDoc.xsd 中，按一下**文件類型**屬性 屬性 窗格中，然後輸入**GlobalBank.ESB.DynamicResolution.Schemas.NAOrderDoc**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-173">In Facts Explorer, click NAOrderDoc.xsd, click the **Document Type** property in the Properties pane, and then type **GlobalBank.ESB.DynamicResolution.Schemas.NAOrderDoc**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6d1f9-174">這是結構描述的完整的名稱。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-174">This is the fully qualified name of the schema.</span></span>  
  
5.  <span data-ttu-id="6d1f9-175">在 [事實總管] 中，展開**NAOrderDoc.xsd**，然後展開**OrderDoc**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-175">In Facts Explorer, expand **NAOrderDoc.xsd**, and then expand **OrderDoc**.</span></span>  
  
6.  <span data-ttu-id="6d1f9-176">在 規則 視窗中，以滑鼠右鍵按一下**條件**，指向 **述詞**，然後按一下**等於**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-176">In the Rule window, right-click **Conditions**, point to **Predicates**, and then click **Equal**.</span></span>  
  
7.  <span data-ttu-id="6d1f9-177">從 [事實總管] 中，拖曳**customerName**元素**引數 1**節點下的**條件**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-177">From Facts Explorer, drag the **customerName** element to the **argument1** node under **Conditions**.</span></span>  
  
8.  <span data-ttu-id="6d1f9-178">按一下**引數 2**  節點，然後輸入**GlobalBankWest**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-178">Click the **argument2** node, and then type **GlobalBankWest**.</span></span>  
  
9. <span data-ttu-id="6d1f9-179">在 [事實總管] 中，按一下 [**詞彙**] 索引標籤。展開**ESB。行程**詞彙中，展開**1.1 版**，然後將拖曳**設定路線名稱**定義，以**動作**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-179">In Facts Explorer, click the **Vocabularies** tab. Expand the **ESB.Itinerary** vocabulary, expand **Version 1.1**, and then drag the **Set Itinerary Name** definition to **Actions**.</span></span>  
  
10. <span data-ttu-id="6d1f9-180">按一下**\<空字串 >** ，然後輸入**GlobalBankWestItinerary**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-180">Click **\<empty string>** and then type **GlobalBankWestItinerary**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6d1f9-181">稍後在本使用說明主題中，您會根據 GlobalBank 西這個行程建立來處理訊息。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-181">Later in this How-to topic, you will create this itinerary to process messages from GlobalBank West.</span></span>  
  
#### <a name="to-add-a-selection-rule-for-customer-globalbank-east"></a><span data-ttu-id="6d1f9-182">若要加入客戶 GlobalBank 東部的選取範圍規則</span><span class="sxs-lookup"><span data-stu-id="6d1f9-182">To add a selection rule for customer GlobalBank East</span></span>  
  
1.  <span data-ttu-id="6d1f9-183">在 [原則總管] 中，以滑鼠右鍵按一下**SetGlobalBankWestItinerary**規則，，然後按一下**複製**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-183">In Policy Explorer, right-click the **SetGlobalBankWestItinerary** rule, and then click **Copy**.</span></span>  
  
2.  <span data-ttu-id="6d1f9-184">以滑鼠右鍵按一下**版本 1.0 （未儲存）**，然後按一下**貼上**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-184">Right-click **Version 1.0 (not saved)**, and then click **Paste**.</span></span>  
  
3.  <span data-ttu-id="6d1f9-185">在**新規則的名稱** 對話方塊中，輸入**SetGlobalBankEastItinerary**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-185">In the **New Rule Name** dialog box, type **SetGlobalBankEastItinerary**, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="6d1f9-186">在 原則總管 中，按一下  **SetGlobalBankEastItinerary**規則。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-186">In Policy Explorer, click the **SetGlobalBankEastItinerary** rule.</span></span>  
  
5.  <span data-ttu-id="6d1f9-187">在**條件**區段中，以滑鼠右鍵按一下**GlobalBankWest**，然後按一下**重設引數**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-187">In the **Conditions** section, right-click **GlobalBankWest**, and then click **Reset argument**.</span></span>  
  
6.  <span data-ttu-id="6d1f9-188">按一下**引數 2**，然後輸入**GlobalBankEast**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-188">Click **argument2**, and then type **GlobalBankEast**.</span></span>  
  
7.  <span data-ttu-id="6d1f9-189">在**動作**區段中，以滑鼠右鍵按一下**GlobalBankWestItinerary**，然後按一下**重設引數**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-189">In the **Actions** section, right-click **GlobalBankWestItinerary**, and then click **Reset argument**.</span></span>  
  
8.  <span data-ttu-id="6d1f9-190">按一下**\<空字串 >** ，然後輸入**GlobalBankEastItinerary。**</span><span class="sxs-lookup"><span data-stu-id="6d1f9-190">Click **\<empty string>** and then type **GlobalBankEastItinerary.**</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6d1f9-191">稍後在本使用說明主題中，您將從 GlobalBank 東這個行程建立來處理訊息。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-191">Later in this How-to topic, you will create this itinerary to process messages from GlobalBank East.</span></span>  
  
#### <a name="to-publish-and-deploy-the-policy"></a><span data-ttu-id="6d1f9-192">若要發行和部署原則</span><span class="sxs-lookup"><span data-stu-id="6d1f9-192">To publish and deploy the policy</span></span>  
  
1.  <span data-ttu-id="6d1f9-193">在 [原則總管] 中，在**ResolveItineraryBasedOnCustomer**原則，按一下**版本 1.0 （未儲存）**，然後按一下**發行**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-193">In Policy Explorer, under the **ResolveItineraryBasedOnCustomer** policy, click **Version 1.0 (not saved)**, and then click **Publish**.</span></span>  
  
2.  <span data-ttu-id="6d1f9-194">在 [原則總管] 中，在**ResolveItineraryBasedOnCustomer**原則，按一下**1.0 版-已發佈**，然後按一下**部署**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-194">In Policy Explorer, under the **ResolveItineraryBasedOnCustomer** policy, click **Version 1.0 - Published**, and then click **Deploy**.</span></span>  
  
#### <a name="to-create-an-esb-itinerary-dsl-model-for-globalbank-west-messages"></a><span data-ttu-id="6d1f9-195">若要建立 GlobalBank 西訊息 ESB 路線 DSL 模型</span><span class="sxs-lookup"><span data-stu-id="6d1f9-195">To create an ESB itinerary DSL model for GlobalBank West messages</span></span>  
  
1.  <span data-ttu-id="6d1f9-196">在 **[!INCLUDE[vs2010](../includes/vs2010-md.md)]** ，開啟 C:\HowTos\Patterns\Patterns.sln。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-196">In **[!INCLUDE[vs2010](../includes/vs2010-md.md)]**, open C:\HowTos\Patterns\Patterns.sln.</span></span>  
  
2.  <span data-ttu-id="6d1f9-197">在 [方案總管] 中，以滑鼠右鍵按一下**ItineraryLibrary**專案，指向**新增**，然後按一下**新的行程**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-197">In Solution Explorer, right-click the **ItineraryLibrary** project, point to **Add**, and then click **New Itinerary**.</span></span>  
  
3.  <span data-ttu-id="6d1f9-198">在**加入新項目**對話方塊，在 [範本] 窗格中，按一下**ItineraryDsl**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-198">In the **Add New Item** dialog box, in the Templates pane, click **ItineraryDsl**.</span></span>  
  
4.  <span data-ttu-id="6d1f9-199">在**名稱**方塊中，輸入**GlobalBankWestItinerary**，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-199">In the **Name** box, type **GlobalBankWestItinerary**, and then click **Add**.</span></span>  
  
#### <a name="to-configure-the-properties-of-the-globalbank-west-itinerary"></a><span data-ttu-id="6d1f9-200">若要設定 GlobalBank 西路線的屬性</span><span class="sxs-lookup"><span data-stu-id="6d1f9-200">To configure the properties of the GlobalBank West itinerary</span></span>  
  
1.  <span data-ttu-id="6d1f9-201">在 Visual Studio 中，按一下設計介面的**GlobalBankWestItinerary.itinerary**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-201">In Visual Studio, click the design surface of **GlobalBankWestItinerary.itinerary**.</span></span> <span data-ttu-id="6d1f9-202">在**GlobalBankWestItinerary**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="6d1f9-202">In the **GlobalBankWestItinerary** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="6d1f9-203">在**模型匯出工具**下拉式清單中，按一下 **資料庫路線匯出工具**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-203">In the **Model Exporter** drop-down list, click **Database Itinerary Exporter**.</span></span>  
  
    2.  <span data-ttu-id="6d1f9-204">按一下旁邊的省略符號按鈕 （...）**路線資料庫**屬性。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-204">Click the ellipsis button (...) next to the **Itinerary Database** property.</span></span>  
  
    3.  <span data-ttu-id="6d1f9-205">在**連接屬性**對話方塊中，選擇裝載路線的儲存機制資料庫，SQL Server，，然後指定資料庫的名稱 (預設名稱是**EsbItineraryDb**)。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-205">In the **Connection Properties** dialog box, choose the SQL Server that hosts the itinerary repository database, and then specify the name of the database (the default name is **EsbItineraryDb**).</span></span>  
  
2.  <span data-ttu-id="6d1f9-206">在**路線狀態**下拉式清單中，按一下 **部署**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-206">In the **Itinerary Status** drop-down list, click **Deployed**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6d1f9-207">這個步驟可讓您匯出至中央儲存機制; 路線可以選取和接收訊息時就會從這個儲存機制附加行程。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-207">This step enables you to export the itinerary to a central repository; itineraries can be selected and attached from this repository when messages are received.</span></span> <span data-ttu-id="6d1f9-208">您稍後將設定要用於評估內送的訊息，並從這個儲存機制中選取適當的行程 BRI 解析程式路線選取器管線元件。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-208">You will later configure the Itinerary Selector pipeline component to use the BRI resolver to evaluate inbound messages and select the appropriate itinerary from this repository.</span></span>  
  
#### <a name="to-define-the-structure-of-the-globalbank-west-itinerary"></a><span data-ttu-id="6d1f9-209">若要定義 GlobalBank 西路線的結構</span><span class="sxs-lookup"><span data-stu-id="6d1f9-209">To define the structure of the GlobalBank West itinerary</span></span>  
  
1.  <span data-ttu-id="6d1f9-210">從 [工具箱] 拖曳**上手**至設計介面的模型項目。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-210">From the Toolbox, drag an **On-Ramp** model element to the design surface.</span></span> <span data-ttu-id="6d1f9-211">在**OnRamp1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="6d1f9-211">In the **OnRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="6d1f9-212">按一下**名稱**屬性，，然後輸入**ReceiveNAOrder**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-212">Click the **Name** property, and then type **ReceiveNAOrder**.</span></span>  
  
    2.  <span data-ttu-id="6d1f9-213">在**Extender**下拉式清單中，按一下 **上手 ESB 服務延伸模組**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-213">In the **Extender** drop-down list, click **On-Ramp ESB Service Extension**.</span></span>  
  
    3.  <span data-ttu-id="6d1f9-214">在**BizTalk 應用程式**下拉式清單中，按一下  **Microsoft.Practices.ESB**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-214">In the **BizTalk Application** drop-down list, click **Microsoft.Practices.ESB**.</span></span>  
  
    4.  <span data-ttu-id="6d1f9-215">在**接收埠**下拉式清單中，按一下  **OnRamp.Itinerary**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-215">In the **Receive Port** drop-down list, click **OnRamp.Itinerary**.</span></span>  
  
2.  <span data-ttu-id="6d1f9-216">從 [工具箱] 拖曳**匝道**模型項目至設計介面，然後再將它放右邊的**ReceiveNAOrder**模型項目。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-216">From the Toolbox, drag an **Off-Ramp** model element to the design surface, and then place it to the right of the **ReceiveNAOrder** model element.</span></span> <span data-ttu-id="6d1f9-217">在**OffRamp1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="6d1f9-217">In the **OffRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="6d1f9-218">按一下**名稱**屬性，，然後輸入**SendNAOrder**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-218">Click the **Name** property, and then type **SendNAOrder**.</span></span>  
  
    2.  <span data-ttu-id="6d1f9-219">在**Extender**下拉式清單中，按一下 **匝道 ESB 服務延伸模組**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-219">In the **Extender** drop-down list, click **Off-Ramp ESB Service Extension**.</span></span>  
  
    3.  <span data-ttu-id="6d1f9-220">在**BizTalk 應用程式**下拉式清單中，按一下  **GlobalBank.ESB**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-220">In the **BizTalk Application** drop-down list, click **GlobalBank.ESB**.</span></span>  
  
    4.  <span data-ttu-id="6d1f9-221">在**傳送埠**下拉式清單中，按一下  **DynamicResolutionOneWay**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-221">In the **Send Port** drop-down list, click **DynamicResolutionOneWay**.</span></span>  
  
3.  <span data-ttu-id="6d1f9-222">從 [工具箱] 拖曳**路線服務**模型項目至設計介面，並將其之間放置**ReceiveNAOrder**模型項目和**SendNAOrder**模型項目。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-222">From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it between the **ReceiveNAOrder** model element and the **SendNAOrder** model element.</span></span> <span data-ttu-id="6d1f9-223">在**ItineraryService1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="6d1f9-223">In the **ItineraryService1** properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="6d1f9-224">按一下**名稱**屬性，，然後輸入**RouteMessage**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-224">Click the **Name** property, and then type **RouteMessage**.</span></span>  
  
    2.  <span data-ttu-id="6d1f9-225">在**路線服務的擴充項**下拉式清單中，按一下 **匝道路線服務延伸模組**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-225">In the **Itinerary Service Extender** drop-down list, click **Off-Ramp Itinerary Service Extension**.</span></span>  
  
    3.  <span data-ttu-id="6d1f9-226">在**匝道**下拉式清單中，展開**SendNAOrder**，然後按一下**傳送處理常式**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-226">In the **Off-Ramp** drop-down list, expand **SendNAOrder**, and then click **Send Handlers**.</span></span>  
  
4.  <span data-ttu-id="6d1f9-227">以滑鼠右鍵按一下**解析程式**集合**RouteMessage**模型項目，然後按一下**加入新的解析程式**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-227">Right-click the **Resolver** collection of the **RouteMessage** model element, and then click **Add new Resolver**.</span></span> <span data-ttu-id="6d1f9-228">在**Resolver1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="6d1f9-228">In the **Resolver1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="6d1f9-229">按一下**名稱**屬性，，然後輸入**StaticResolver**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-229">Click the **Name** property, and then type **StaticResolver**.</span></span>  
  
    2.  <span data-ttu-id="6d1f9-230">在**解析程式實作**下拉式清單中，按一下 **靜態解析程式擴充功能**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-230">In the **Resolver Implementation** drop-down list, click **Static Resolver Extension**.</span></span>  
  
    3.  <span data-ttu-id="6d1f9-231">在**傳輸名稱**下拉式清單中，按一下 **檔案**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-231">In the **Transport Name** drop-down list, click **FILE**.</span></span>  
  
    4.  <span data-ttu-id="6d1f9-232">按一下**傳輸位置**屬性，，然後輸入**C:\HowTos\Out\West%MessageID%.xml**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-232">Click the **Transport Location** property, and then type **C:\HowTos\Out\West%MessageID%.xml**.</span></span>  
  
5.  <span data-ttu-id="6d1f9-233">在工具箱中，按一下 **連接器**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-233">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="6d1f9-234">拖曳連接**ReceiveNAOrder**模型項目的**RouteMessage**模型項目。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-234">Drag a connection from the **ReceiveNAOrder** model element to the  **RouteMessage** model element.</span></span>  
  
6.  <span data-ttu-id="6d1f9-235">在工具箱中，按一下 **連接器**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-235">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="6d1f9-236">拖曳連接**RouteMessage**模型項目的**SendNAOrder**模型項目。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-236">Drag a connection from the **RouteMessage** model element to the **SendNAOrder** model element.</span></span>  
  
#### <a name="to-export-the-globalbank-west-model-to-the-itinerary-database"></a><span data-ttu-id="6d1f9-237">將 GlobalBank 西模型匯出至路線資料庫</span><span class="sxs-lookup"><span data-stu-id="6d1f9-237">To export the GlobalBank West model to the itinerary database</span></span>  
  
1.  <span data-ttu-id="6d1f9-238">在 Visual Studio 中，以滑鼠右鍵按一下設計介面的**GlobalBankWestItinerary**路線，然後再按一下**匯出模型**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-238">In Visual Studio, right-click the design surface of the **GlobalBankWestItinerary** itinerary, and then click **Export Model**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6d1f9-239">路線已經匯出成路線的資料庫，現在可供路線選取器元件。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-239">The itinerary has been exported to the itinerary database and can now be used by the Itinerary Selector component.</span></span>  
  
2.  <span data-ttu-id="6d1f9-240">儲存專案的所有成品。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-240">Save all project artifacts.</span></span>  
  
#### <a name="to-create-an-esb-itinerary-dsl-model-for-globalbank-east-message"></a><span data-ttu-id="6d1f9-241">若要建立 GlobalBank 東部訊息 ESB 路線 DSL 模型</span><span class="sxs-lookup"><span data-stu-id="6d1f9-241">To create an ESB itinerary DSL model for GlobalBank East message</span></span>  
  
1.  <span data-ttu-id="6d1f9-242">在 **[!INCLUDE[vs2010](../includes/vs2010-md.md)]** ，開啟 C:\HowTos\Patterns.sln。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-242">In **[!INCLUDE[vs2010](../includes/vs2010-md.md)]**, open C:\HowTos\Patterns.sln.</span></span>  
  
2.  <span data-ttu-id="6d1f9-243">在 [方案總管] 中，以滑鼠右鍵按一下**ItineraryLibrary**專案，指向**新增**，然後按一下**新的行程**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-243">In Solution Explorer, right-click the **ItineraryLibrary** project, point to **Add**, and then click **New Itinerary**.</span></span>  
  
3.  <span data-ttu-id="6d1f9-244">在**加入新項目**對話方塊，在 [範本] 窗格中，按一下**ItineraryDsl**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-244">In the **Add New Item** dialog box, in the Templates pane, click **ItineraryDsl**.</span></span>  
  
4.  <span data-ttu-id="6d1f9-245">在**名稱**方塊中，輸入**GlobalBankEastItinerary**，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-245">In the **Name** box, type **GlobalBankEastItinerary**, and then click **Add**.</span></span>  
  
#### <a name="to-configure-the-properties-of-the-globalbank-east-itinerary"></a><span data-ttu-id="6d1f9-246">若要設定的 GlobalBank 東部路線屬性</span><span class="sxs-lookup"><span data-stu-id="6d1f9-246">To configure the properties of the GlobalBank East itinerary</span></span>  
  
1.  <span data-ttu-id="6d1f9-247">在 Visual Studio 中，按一下設計介面的**GlobalBankEastItinerary.itinerary**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-247">In Visual Studio, click the design surface of **GlobalBankEastItinerary.itinerary**.</span></span> <span data-ttu-id="6d1f9-248">在**GlobalBankEastItinerary**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="6d1f9-248">In the **GlobalBankEastItinerary** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="6d1f9-249">在**模型匯出工具**下拉式清單中，按一下 **資料庫路線匯出工具**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-249">In the **Model Exporter** drop-down list, click **Database Itinerary Exporter**.</span></span>  
  
    2.  <span data-ttu-id="6d1f9-250">按一下旁邊的省略符號按鈕 （...）**路線資料庫**屬性。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-250">Click the ellipsis button (...) next to the **Itinerary Database** property.</span></span>  
  
    3.  <span data-ttu-id="6d1f9-251">在**連接屬性**對話方塊中，選擇裝載路線的儲存機制資料庫，SQL Server，，然後指定資料庫的名稱 (預設名稱是**EsbItineraryDb**)。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-251">In the **Connection Properties** dialog box, choose the SQL Server that hosts the itinerary repository database, and then specify the name of the database (the default name is **EsbItineraryDb**).</span></span>  
  
2.  <span data-ttu-id="6d1f9-252">在**路線狀態**下拉式清單中，按一下 **部署**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-252">In the **Itinerary Status** drop-down list, click **Deployed**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6d1f9-253">這個步驟可讓您匯出至中央儲存機制; 路線可以選取和接收訊息時就會從這個儲存機制附加行程。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-253">This step enables you to export the itinerary to a central repository; itineraries can be selected and attached from this repository when messages are received.</span></span> <span data-ttu-id="6d1f9-254">您稍後將設定要用於評估內送的訊息，並從這個儲存機制中選取適當的行程 BRI 解析程式路線選取器管線元件。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-254">You will later configure the Itinerary Selector pipeline component to use the BRI resolver to evaluate inbound messages and select the appropriate itinerary from this repository.</span></span>  
  
#### <a name="to-define-the-structure-of-the-globalbank-east-itinerary"></a><span data-ttu-id="6d1f9-255">若要定義 GlobalBank 東部路線的結構</span><span class="sxs-lookup"><span data-stu-id="6d1f9-255">To define the structure of the GlobalBank East itinerary</span></span>  
  
1.  <span data-ttu-id="6d1f9-256">從 [工具箱] 拖曳**上手**至設計介面的模型項目。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-256">From the Toolbox, drag an **On-Ramp** model element to the design surface.</span></span> <span data-ttu-id="6d1f9-257">在**OnRamp1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="6d1f9-257">In the **OnRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="6d1f9-258">按一下**名稱**屬性，，然後輸入**ReceiveNAOrder**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-258">Click the **Name** property, and then type **ReceiveNAOrder**.</span></span>  
  
    2.  <span data-ttu-id="6d1f9-259">在**Extender**下拉式清單中，按一下 **上手 ESB 服務延伸模組**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-259">In the **Extender** drop-down list, click **On-Ramp ESB Service Extension**.</span></span>  
  
    3.  <span data-ttu-id="6d1f9-260">在**BizTalk 應用程式**下拉式清單中，按一下  **Microsoft.Practices.ESB**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-260">In the **BizTalk Application** drop-down list, click **Microsoft.Practices.ESB**.</span></span>  
  
    4.  <span data-ttu-id="6d1f9-261">在**接收埠**下拉式清單中，按一下  **OnRamp.Itinerary**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-261">In the **Receive Port** drop-down list, click **OnRamp.Itinerary**.</span></span>  
  
2.  <span data-ttu-id="6d1f9-262">從 [工具箱] 拖曳**匝道**模型項目至設計介面，然後再將它放右邊的**ReceiveNAOrder**模型項目。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-262">From the Toolbox, drag an **Off-Ramp** model element to the design surface, and then place it to the right of the **ReceiveNAOrder** model element.</span></span> <span data-ttu-id="6d1f9-263">在**OffRamp1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="6d1f9-263">In the **OffRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="6d1f9-264">按一下**名稱**屬性，，然後輸入**SendNAOrder**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-264">Click the **Name** property, and then type **SendNAOrder**.</span></span>  
  
    2.  <span data-ttu-id="6d1f9-265">在**Extender**下拉式清單中，按一下 **匝道 ESB 服務延伸模組**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-265">In the **Extender** drop-down list, click **Off-Ramp ESB Service Extension**.</span></span>  
  
    3.  <span data-ttu-id="6d1f9-266">在**BizTalk 應用程式**下拉式清單中，按一下  **GlobalBank.ESB**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-266">In the **BizTalk Application** drop-down list, click **GlobalBank.ESB**.</span></span>  
  
    4.  <span data-ttu-id="6d1f9-267">在**傳送埠**下拉式清單中，按一下  **DynamicResolutionOneWay**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-267">In the **Send Port** drop-down list, click **DynamicResolutionOneWay**.</span></span>  
  
3.  <span data-ttu-id="6d1f9-268">從 [工具箱] 拖曳**路線服務**模型項目至設計介面，並將其之間放置**ReceiveNAOrder**模型項目和**SendNAOrder**模型項目。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-268">From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it between the **ReceiveNAOrder** model element and the **SendNAOrder** model element.</span></span> <span data-ttu-id="6d1f9-269">在**ItineraryService1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="6d1f9-269">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="6d1f9-270">按一下**名稱**屬性，，然後輸入**RouteMessage**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-270">Click the **Name** property, and then type **RouteMessage**.</span></span>  
  
    2.  <span data-ttu-id="6d1f9-271">在**路線服務的擴充項**下拉式清單中，按一下 **匝道路線服務延伸模組**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-271">In the **Itinerary Service Extender** drop-down list, click **Off-Ramp Itinerary Service Extension**.</span></span>  
  
    3.  <span data-ttu-id="6d1f9-272">在**匝道**下拉式清單中，展開**SendNAOrder**，然後按一下**傳送處理常式**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-272">In the **Off-Ramp** drop-down list, expand **SendNAOrder**, and then click **Send Handlers**.</span></span>  
  
4.  <span data-ttu-id="6d1f9-273">以滑鼠右鍵按一下**解析程式**集合**RouteMessage**模型項目，然後按一下**加入新的解析程式**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-273">Right-click the **Resolver** collection of the **RouteMessage** model element, and then click **Add new Resolver**.</span></span> <span data-ttu-id="6d1f9-274">在**Resolver1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="6d1f9-274">In the **Resolver1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="6d1f9-275">按一下**名稱**屬性，，然後輸入**StaticResolver**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-275">Click the **Name** property, and then type **StaticResolver**.</span></span>  
  
    2.  <span data-ttu-id="6d1f9-276">在**解析程式實作**下拉式清單中，按一下 **靜態解析程式擴充功能**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-276">In the **Resolver Implementation** drop-down list, click **Static Resolver Extension**.</span></span>  
  
    3.  <span data-ttu-id="6d1f9-277">在**傳輸名稱**下拉式清單中，按一下 **檔案**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-277">In the **Transport Name** drop-down list, click **FILE**.</span></span>  
  
    4.  <span data-ttu-id="6d1f9-278">按一下**傳輸位置**屬性，，然後輸入**C:\HowTos\Out\East%MessageID%.xml**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-278">Click the **Transport Location** property, and then type **C:\HowTos\Out\East%MessageID%.xml**.</span></span>  
  
5.  <span data-ttu-id="6d1f9-279">在工具箱中，按一下 **連接器**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-279">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="6d1f9-280">拖曳連接**ReceiveNAOrder**模型項目的**RouteMessage**模型項目。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-280">Drag a connection from the **ReceiveNAOrder** model element to the **RouteMessage** model element.</span></span>  
  
6.  <span data-ttu-id="6d1f9-281">在工具箱中，按一下 **連接器**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-281">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="6d1f9-282">拖曳連接**RouteMessage**模型項目的**SendNAOrder**模型項目。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-282">Drag a connection from the **RouteMessage** model element to the **SendNAOrder** model element.</span></span>  
  
#### <a name="to-export-the-globalbank-east-model-to-the-itinerary-database"></a><span data-ttu-id="6d1f9-283">將 GlobalBank 東部模型匯出至路線資料庫</span><span class="sxs-lookup"><span data-stu-id="6d1f9-283">To export the GlobalBank East model to the itinerary database</span></span>  
  
1.  <span data-ttu-id="6d1f9-284">在 Visual Studio 中，以滑鼠右鍵按一下設計介面的**GlobalBankEastItinerary**路線，然後再按一下**匯出模型**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-284">In Visual Studio, right-click the design surface of the **GlobalBankEastItinerary** itinerary, and then click **Export Model**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6d1f9-285">路線已經匯出成路線的資料庫，現在可供路線選取器元件。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-285">The itinerary has been exported to the itinerary database and can now be used by the Itinerary Selector component.</span></span>  
  
2.  <span data-ttu-id="6d1f9-286">儲存專案的所有成品。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-286">Save all project artifacts.</span></span>  
  
## <a name="steps"></a><span data-ttu-id="6d1f9-287">步驟</span><span class="sxs-lookup"><span data-stu-id="6d1f9-287">Steps</span></span>  
  
#### <a name="to-create-and-configure-an-esb-on-ramp"></a><span data-ttu-id="6d1f9-288">若要建立及設定 ESB 上手</span><span class="sxs-lookup"><span data-stu-id="6d1f9-288">To create and configure an ESB on-ramp</span></span>  
  
1.  <span data-ttu-id="6d1f9-289">按一下**啟動**在工作列上，指向**所有程式**，指向   **[!INCLUDE[prague](../includes/prague-md.md)]** ，然後按一下 **BizTalk Server 管理**.</span><span class="sxs-lookup"><span data-stu-id="6d1f9-289">Click **Start** on the taskbar, point to **All Programs**, point to **[!INCLUDE[prague](../includes/prague-md.md)]**, and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="6d1f9-290">在[!INCLUDE[prague](../includes/prague-md.md)]管理主控台中，展開  **BizTalk 群組**，依序展開**應用程式**，然後展開**Microsoft.Practices.ESB**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-290">In the [!INCLUDE[prague](../includes/prague-md.md)] Administration Console, expand **BizTalk Group**, expand **Applications**, and then expand **Microsoft.Practices.ESB**.</span></span>  
  
3.  <span data-ttu-id="6d1f9-291">以滑鼠右鍵按一下**接收位置**，指向 **新增**，然後按一下**單向接收位置**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-291">Right-click **Receive Locations**, point to **New**, and then click **One-way Receive Location**.</span></span>  
  
4.  <span data-ttu-id="6d1f9-292">在**選取接收埠**對話方塊中，按一下  **OnRamp.Itinerary**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-292">In the **Select a Receive Port** dialog box, click **OnRamp.Itinerary**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="6d1f9-293">在**接收位置屬性**對話方塊中，於**名稱**方塊中，輸入**OnRamp.Itinerary.HowTo**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-293">In the **Receive Location Properties** dialog box, in the **Name** box, type **OnRamp.Itinerary.HowTo**.</span></span>  
  
6.  <span data-ttu-id="6d1f9-294">在**類型**下拉式清單中，按一下 **檔案，** ，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-294">In the **Type** drop-down list, click **FILE,** and then click **Configure**.</span></span>  
  
7.  <span data-ttu-id="6d1f9-295">中**FILE 傳輸屬性**對話方塊中，於**接收資料夾**方塊中，輸入**C:\HowTos\DropFolder**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-295">In the **FILE Transport Properties** dialog box, in the **Receive folder** box, type **C:\HowTos\DropFolder**, and then click **OK**.</span></span>  
  
#### <a name="to-configure-the-itinerary-selector-pipeline-component"></a><span data-ttu-id="6d1f9-296">若要設定路線選取器管線元件</span><span class="sxs-lookup"><span data-stu-id="6d1f9-296">To configure the Itinerary Selector pipeline component</span></span>  
  
1.  <span data-ttu-id="6d1f9-297">在**接收位置屬性**對話方塊中，按一下  **ItinerarySelectReceiveXml**中**接收管線**下拉式清單，，然後按一下省略符號按鈕 （...）。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-297">In the **Receive Location Properties** dialog box, click **ItinerarySelectReceiveXml** in the **Receive pipeline** drop-down list, and then click the ellipsis button (...).</span></span>  
  
2.  <span data-ttu-id="6d1f9-298">使用**設定管線**對話方塊來設定下列**路線選取器**元件屬性：</span><span class="sxs-lookup"><span data-stu-id="6d1f9-298">Use the **Configure Pipeline** dialog box to configure the following **Itinerary Selector** component properties:</span></span>  
  
    1.  <span data-ttu-id="6d1f9-299">按一下**ItineraryFactKey**屬性，，然後輸入**Resolver.Itinerary**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-299">Click the **ItineraryFactKey** property, and then type **Resolver.Itinerary**.</span></span>  
  
    2.  <span data-ttu-id="6d1f9-300">按一下**ResolverConnectionString**屬性，，然後輸入**BRI:\\\policy=ResolveItineraryBasedOnCustomer;useMsg=true;recognizeMessageFormat=true;**</span><span class="sxs-lookup"><span data-stu-id="6d1f9-300">Click the **ResolverConnectionString** property, and then type **BRI:\\\policy=ResolveItineraryBasedOnCustomer;useMsg=true;recognizeMessageFormat=true;**</span></span>  
  
    3.  <span data-ttu-id="6d1f9-301">按一下**確定**關閉**設定管線** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-301">Click **OK** to close the **Configure Pipeline** dialog box.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="6d1f9-302">由於此接收位置解譯 XML 交換，XML 解譯器元件就不需要設定。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-302">Because this receive location is disassembling an XML interchange, no XML Disassembler component configuration is required.</span></span>  
  
3.  <span data-ttu-id="6d1f9-303">按一下**確定**關閉**接收位置屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-303">Click **OK** to close the **Receive Location Properties** dialog box.</span></span>  
  
4.  <span data-ttu-id="6d1f9-304">在[!INCLUDE[prague](../includes/prague-md.md)]管理主控台中，以滑鼠右鍵按一下**OnRamp.Itinerary.HowTo**接收位置，然後按一下**啟用**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-304">In the [!INCLUDE[prague](../includes/prague-md.md)] Administration Console, right-click the **OnRamp.Itinerary.HowTo** receive location, and then click **Enable**.</span></span>  
  
#### <a name="to-test-the-itinerary-selector-and-business-rules"></a><span data-ttu-id="6d1f9-305">若要測試的行程選取器 」 和 「 商務規則</span><span class="sxs-lookup"><span data-stu-id="6d1f9-305">To test the Itinerary Selector and business rules</span></span>  
  
1.  <span data-ttu-id="6d1f9-306">在 Windows 檔案總管，瀏覽至 C:\HowTos。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-306">In Windows Explorer, browse to C:\HowTos.</span></span>  
  
2.  <span data-ttu-id="6d1f9-307">複製 （不會移動） Batch.xml DropFolder 資料夾。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-307">Copy (do not move) Batch.xml to the DropFolder folder.</span></span>  
  
3.  <span data-ttu-id="6d1f9-308">瀏覽至 C:\HowTos\Out。請確認的已寫入一個 West%MessageID%.xml 訊息與兩個 East%MessageID%.xml 訊息目錄。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-308">Browse to C:\HowTos\Out. Verify that one West%MessageID%.xml message and two East%MessageID%.xml messages have been written to the directory.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6d1f9-309">雖然訊息是相同的但客戶元素的值，但它們的處理使用不同的行程，根據路線選取器管線元件的解析度。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-309">Although the messages are identical except for the value of the customer element, they were processed using different itineraries, based on the resolution of the Itinerary Selector pipeline component.</span></span>  
  
4.  <span data-ttu-id="6d1f9-310">在[!INCLUDE[prague](../includes/prague-md.md)]管理主控台中，以滑鼠右鍵按一下 OnRamp.Itinerary.HowTo 接收位置，然後按一下停用。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-310">In the [!INCLUDE[prague](../includes/prague-md.md)] Administration Console, right-click the OnRamp.Itinerary.HowTo receive location, and then click Disable.</span></span>  
  
5.  <span data-ttu-id="6d1f9-311">之後**OnRamp.Itinerary.HowTo**接收位置已停用，以滑鼠右鍵按一下，，然後按一下**刪除**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-311">After the **OnRamp.Itinerary.HowTo** receive location is disabled, right-click it, and then click **Delete**.</span></span> <span data-ttu-id="6d1f9-312">在**確認刪除接收位置**對話方塊中，按一下 **是**。</span><span class="sxs-lookup"><span data-stu-id="6d1f9-312">In the **Confirm delete receive location** dialog box, click **Yes**.</span></span>  
  
## <a name="additional-resources"></a><span data-ttu-id="6d1f9-313">其他資源</span><span class="sxs-lookup"><span data-stu-id="6d1f9-313">Additional Resources</span></span>  
 <span data-ttu-id="6d1f9-314">如需詳細資訊，請參閱下列相關主題：</span><span class="sxs-lookup"><span data-stu-id="6d1f9-314">For more information, see the following related topics:</span></span>  
  
-   [<span data-ttu-id="6d1f9-315">如何： 選取 使用商務規則原則路線</span><span class="sxs-lookup"><span data-stu-id="6d1f9-315">How to: Select an Itinerary Using a Business Rules Policy</span></span>](../esb-toolkit/how-to-select-an-itinerary-using-a-business-rules-policy.md)  
  
-   [<span data-ttu-id="6d1f9-316">開發活動</span><span class="sxs-lookup"><span data-stu-id="6d1f9-316">Development Activities</span></span>](../esb-toolkit/development-activities.md)  
  
-   [<span data-ttu-id="6d1f9-317">安裝及執行動態解析範例</span><span class="sxs-lookup"><span data-stu-id="6d1f9-317">Installing and Running the Dynamic Resolution Sample</span></span>](../esb-toolkit/installing-and-running-the-dynamic-resolution-sample.md)  
  
-   [<span data-ttu-id="6d1f9-318">使用動態解析和路由</span><span class="sxs-lookup"><span data-stu-id="6d1f9-318">Using Dynamic Resolution and Routing</span></span>](../esb-toolkit/using-dynamic-resolution-and-routing.md)  
  
-   [<span data-ttu-id="6d1f9-319">訊息的路由模式</span><span class="sxs-lookup"><span data-stu-id="6d1f9-319">Message Routing Patterns</span></span>](../esb-toolkit/message-routing-patterns.md)