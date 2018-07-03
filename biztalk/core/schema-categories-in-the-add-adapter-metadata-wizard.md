---
title: 結構描述類別中的新增配接器中繼資料精靈 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3927c676-f60a-449e-be43-6f75e28aefe1
caps.latest.revision: 27
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 46fd9ffab7aa4f8617e08a18824cc251ad9f4173
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37008007"
---
# <a name="schema-categories-in-the-add-adapter-metadata-wizard"></a><span data-ttu-id="9e2f4-102">新增配接器中繼資料精靈中的結構描述類別</span><span class="sxs-lookup"><span data-stu-id="9e2f4-102">Schema Categories in the Add Adapter Metadata Wizard</span></span>

## <a name="overview"></a><span data-ttu-id="9e2f4-103">概觀</span><span class="sxs-lookup"><span data-stu-id="9e2f4-103">Overview</span></span>
> [!NOTE]
>  <span data-ttu-id="9e2f4-104">本主題是僅針對靜態配接器可實作**IStaticAdapterConfig**介面。</span><span class="sxs-lookup"><span data-stu-id="9e2f4-104">This topic is only for static adapters that implement the **IStaticAdapterConfig** interface.</span></span>  
  
 <span data-ttu-id="9e2f4-105">在將資料傳遞到 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 之前，配接器可能會使用數千種結構描述中的一種來進行轉換。</span><span class="sxs-lookup"><span data-stu-id="9e2f4-105">An adapter may use any one of thousands of schemas to transform data before passing it to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="9e2f4-106">在將中繼資料新增到 BizTalk 專案時，請使用 [新增配接器中繼資料精靈]，從配接器與其互動之所有結構描述的清單中，選取某個結構描述。</span><span class="sxs-lookup"><span data-stu-id="9e2f4-106">When adding metadata to a BizTalk project, use the Add Adapter Metadata Wizard to select a schema from a list of all the schemas with which the adapter interacts.</span></span>  
  
 <span data-ttu-id="9e2f4-107">在範例檔案配接器中，CategorySchema.xml 檔案是與配接器架構的 BiztalkAdapterFramework.xsd 檔案搭配使用，以填入服務結構描述之樹狀檢視組織的結構描述執行個體。</span><span class="sxs-lookup"><span data-stu-id="9e2f4-107">In the sample file adapter, the CategorySchema.xml file is a schema instance that is used in conjunction with the Adapter Framework's BiztalkAdapterFramework.xsd file to populate a tree-view organization of service schemas.</span></span>  <span data-ttu-id="9e2f4-108">BizTalkAdapterFramework.xsd 檔案位於 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Developer Tools 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="9e2f4-108">The BizTalkAdapterFramework.xsd file is located in the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Developer Tools folder.</span></span>  
  
 <span data-ttu-id="9e2f4-109">您應該建立這個檔案，以便以能夠從您解決方案直接取得的方式來組織結構描述。</span><span class="sxs-lookup"><span data-stu-id="9e2f4-109">You should create this file so that it organizes the schemas in a manner that is intuitive to your solution.</span></span> <span data-ttu-id="9e2f4-110">CategorySchema.xml 中的現有類別只是您可以在自己的樹狀結構中做到的範例。</span><span class="sxs-lookup"><span data-stu-id="9e2f4-110">The existing categories in CategorySchema.xml are just an example of what you can do in your own tree.</span></span> <span data-ttu-id="9e2f4-111">這些類別與範例配接器所傳遞的資料沒有任何特別關係。</span><span class="sxs-lookup"><span data-stu-id="9e2f4-111">The categories do not have any particular relevance to the data that is passed by the sample adapter.</span></span> <span data-ttu-id="9e2f4-112">結構描述的組織對於應用程式的特定配接器尤其重要，因為其中可能會有數千種不同的結構描述。</span><span class="sxs-lookup"><span data-stu-id="9e2f4-112">The organization of the schemas is particularly important with application-specific adapters, where thousands of different schemas may be available.</span></span> <span data-ttu-id="9e2f4-113">對於傳輸的特定配接器，這個樹狀檢視組織是不必要的。</span><span class="sxs-lookup"><span data-stu-id="9e2f4-113">For transport-specific adapters, this tree-view organization is unnecessary.</span></span>  
  
 <span data-ttu-id="9e2f4-114">下圖顯示**選取要匯入服務**「 新增配接器中繼資料精靈 」 的頁面。</span><span class="sxs-lookup"><span data-stu-id="9e2f4-114">The following figure shows the **Select Services to Import** page in the Add Adapter Metadata Wizard.</span></span>  
  
 <span data-ttu-id="9e2f4-115">![](../core/media/ebiz-prog-custad-tree.gif "ebiz_prog_custad_tree")</span><span class="sxs-lookup"><span data-stu-id="9e2f4-115">![](../core/media/ebiz-prog-custad-tree.gif "ebiz_prog_custad_tree")</span></span>  
<span data-ttu-id="9e2f4-116">[新增配接器中繼資料精靈] 中結構描述類別的樹狀檢視</span><span class="sxs-lookup"><span data-stu-id="9e2f4-116">Tree view of the schema categories in the Add Adapter Metadata Wizard</span></span>  


## <a name="sample-xml"></a><span data-ttu-id="9e2f4-117">範例 XML</span><span class="sxs-lookup"><span data-stu-id="9e2f4-117">Sample XML</span></span>
  
 <span data-ttu-id="9e2f4-118">下列程式碼顯示 CategorySchema.xml 檔案：</span><span class="sxs-lookup"><span data-stu-id="9e2f4-118">The following code shows the CategorySchema.xml file:</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<CategoryTree>  
     <DisplayName>Services Organization</DisplayName>  
     <DisplayDescription>An organization of application services</DisplayDescription>  
     <CategoryTreeNode>  
          <DisplayName>Health Care</DisplayName>  
          <Description>Services under Health Care</Description>  
          <CategoryTreeNode>  
               <DisplayName>Administrative</DisplayName>  
               <Description>Administrative Health Care Services</Description>  
               <ServiceTreeNode>  
                    <DisplayName>Eligibility</DisplayName>  
                    <Description>Eligibility Verification Transactions</Description>  
                    <WSDLReference>ANSI X 12 270</WSDLReference>  
               </ServiceTreeNode>  
          </CategoryTreeNode>  
     </CategoryTreeNode>  
     <CategoryTreeNode>  
          <DisplayName>Manufacturing</DisplayName>  
          <Description>Manufacturing Services</Description>  
          <CategoryTreeNode>  
               <DisplayName>Inventory</DisplayName>  
               <Description>Inventory Services</Description>  
               <ServiceTreeNode>  
                    <DisplayName>Requisition</DisplayName>  
                    <Description>Requisition</Description>  
                    <WSDLReference>RequisitionService</WSDLReference>  
               </ServiceTreeNode>  
          </CategoryTreeNode>  
     </CategoryTreeNode>  
</CategoryTree>  
```  
  
 <span data-ttu-id="9e2f4-119">下列節點類型出現在此結構描述執行個體中：</span><span class="sxs-lookup"><span data-stu-id="9e2f4-119">The following node types appear in this schema instance:</span></span>  
  
- <span data-ttu-id="9e2f4-120">**CategoryTree。**</span><span class="sxs-lookup"><span data-stu-id="9e2f4-120">**CategoryTree.**</span></span> <span data-ttu-id="9e2f4-121">系統資訊之模型的最上層結構。</span><span class="sxs-lookup"><span data-stu-id="9e2f4-121">Top-level structure of a model of system information.</span></span> <span data-ttu-id="9e2f4-122">包含零個或多個 CategoryTreeNode、ExpandableCategoryTreeNode 及 ServiceTreeNode 節點。</span><span class="sxs-lookup"><span data-stu-id="9e2f4-122">Contains zero or more of the CategoryTreeNode, ExpandableCategoryTreeNode, and ServiceTreeNode nodes.</span></span>  
  
- <span data-ttu-id="9e2f4-123">**CategoryTreeNode。**</span><span class="sxs-lookup"><span data-stu-id="9e2f4-123">**CategoryTreeNode.**</span></span> <span data-ttu-id="9e2f4-124">包含零個或多個 CategoryTreeNode 和 ServiceTreeNode 節點。</span><span class="sxs-lookup"><span data-stu-id="9e2f4-124">Contains zero or more CategoryTreeNode and ServiceTreeNode nodes.</span></span> <span data-ttu-id="9e2f4-125">使用在使用者介面 (UI) 中出現為資料夾的 CategoryTreeNode，將相關的一組服務編成群組。</span><span class="sxs-lookup"><span data-stu-id="9e2f4-125">Use the CategoryTreeNode that appears as a folder in the user interface (UI) to group a set of related services.</span></span> <span data-ttu-id="9e2f4-126">通常這會包含顯示名稱和所要顯示之服務的描述。</span><span class="sxs-lookup"><span data-stu-id="9e2f4-126">Typically this contains a display name and description of the services to be displayed.</span></span> <span data-ttu-id="9e2f4-127">如果子節點的數目不大，配接器便可以使用 CategoryTreeNode。</span><span class="sxs-lookup"><span data-stu-id="9e2f4-127">An adapter might use a CategoryTreeNode if the number of child nodes is small.</span></span>  
  
- <span data-ttu-id="9e2f4-128">**ExpandableCategoryTreeNode。**</span><span class="sxs-lookup"><span data-stu-id="9e2f4-128">**ExpandableCategoryTreeNode.**</span></span> <span data-ttu-id="9e2f4-129">在展開時便會被動態地填入的分葉節點。</span><span class="sxs-lookup"><span data-stu-id="9e2f4-129">A leaf node that is dynamically populated when expanded.</span></span> <span data-ttu-id="9e2f4-130">ExpandableCategoryTreeNode 具有預留位置的用途，並會在 UI 中以資料夾的形式出現。</span><span class="sxs-lookup"><span data-stu-id="9e2f4-130">The ExpandableCategoryTreeNode is used as a placeholder and appears as a folder in the UI.</span></span> <span data-ttu-id="9e2f4-131">在使用者按一下以展開節點前，這可以用來延遲以子項目填入類別節點。</span><span class="sxs-lookup"><span data-stu-id="9e2f4-131">This can be used to defer populating a category node with subelements until the user clicks to expand the node.</span></span> <span data-ttu-id="9e2f4-132">如果類別包含大量子節點，配接器便可以使用 ExpandableCategoryTreeNode。</span><span class="sxs-lookup"><span data-stu-id="9e2f4-132">An adapter might use an ExpandableCategoryTreeNode if a category contains a large number of child nodes.</span></span>  
  
- <span data-ttu-id="9e2f4-133">**ServiceTreeNode。**</span><span class="sxs-lookup"><span data-stu-id="9e2f4-133">**ServiceTreeNode.**</span></span> <span data-ttu-id="9e2f4-134">ServiceTreeNode 會出現為文件，或是 UI 中的分葉節點，並代表 Web 服務描述語言 (WSDL) 檔案。</span><span class="sxs-lookup"><span data-stu-id="9e2f4-134">A ServiceTreeNode appears as a document, or leaf node, in the UI and represents a Web Services Description Language (WSDL) file.</span></span>  
  
  <span data-ttu-id="9e2f4-135">當使用者按一下資料夾以展開節點時，配接器架構會呼叫**IStaticAdapterConfig.GetServiceOrganization**的值傳遞的節點名稱的介面卡上的方法**Istaticadapterconfig.getserviceorganization**屬性。</span><span class="sxs-lookup"><span data-stu-id="9e2f4-135">When a user clicks the folder to expand a node, the Adapter Framework calls the **IStaticAdapterConfig.GetServiceOrganization** method on the adapter passing the name of the node as the value of the **NodeIdentifier** attribute.</span></span> <span data-ttu-id="9e2f4-136">配接器應該會傳回一個 CategoryTree，其中包含要在 ExpandableCategoryTreeNode 下新增的子節點。</span><span class="sxs-lookup"><span data-stu-id="9e2f4-136">The adapter should return a CategoryTree containing the subnodes to add under the ExpandableCategoryTreeNode.</span></span> <span data-ttu-id="9e2f4-137">配接器架構會將 ExpandableCategoryTreeNode 取代為 CategoryTreeNode，並將其新增到傳回之 CategoryTree 的子系。</span><span class="sxs-lookup"><span data-stu-id="9e2f4-137">The Adapter Framework replaces the ExpandableCategoryTreeNode with a CategoryTreeNode and adds to it the children of the returned CategoryTree.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9e2f4-138">若要在初始呼叫中**IStaticAdapterConfig.GetServiceOrganization**配接器架構會傳遞 null 的節點識別碼。</span><span class="sxs-lookup"><span data-stu-id="9e2f4-138">In the initial call to **IStaticAdapterConfig.GetServiceOrganization** the Adapter Framework passes null for the node identifier.</span></span> <span data-ttu-id="9e2f4-139">這樣便會告知配接器傳回根層級的 CategoryTree。</span><span class="sxs-lookup"><span data-stu-id="9e2f4-139">This tells the adapter to return the root-level CategoryTree.</span></span>  
  
 <span data-ttu-id="9e2f4-140">以下是從 BiztalkAdapterFramework.xsd 檔案中擷取的類別樹狀結構描述。</span><span class="sxs-lookup"><span data-stu-id="9e2f4-140">Below is the category tree schema extracted from the BiztalkAdapterFramework.xsd file.</span></span> <span data-ttu-id="9e2f4-141">這會由 [新增配接器中繼資料精靈] 用來做為骨幹樹狀結構，並在其中填入 XML 檔案中的特定應用程式相依實體。</span><span class="sxs-lookup"><span data-stu-id="9e2f4-141">This is used by the Add Adapter Metadata Wizard as the skeleton tree with which to populate with specific application-dependent entities from an XML file.</span></span> <span data-ttu-id="9e2f4-142">在我們的範例中，該檔案是 CategorySchema.xml 檔案。</span><span class="sxs-lookup"><span data-stu-id="9e2f4-142">In our example that file is the CategorySchema.xml file.</span></span>  
  
```  
<!-- Service Organization Tree schema used by Add Adapter Wizard -->  
    <xs:element name="CategoryTree" type="CategoryTree" />  
    <xs:complexType name="CategoryTree">  
        <xs:sequence>  
            <xs:element name="DisplayName" type="xs:string" />  
            <xs:element name="DisplayDescription" type="xs:string" />  
            <xs:choice minOccurs="0" maxOccurs="unbounded">  
                <xs:element name="ExpandableCategoryTreeNode" type="ExpandableCategoryTreeNode" minOccurs="0" maxOccurs="unbounded" />  
                <xs:element name="CategoryTreeNode" type="CategoryTreeNode" minOccurs="0" maxOccurs="unbounded" />  
                <xs:element name="ServiceTreeNode" type="ServiceTreeNode" minOccurs="0" maxOccurs="unbounded" />  
            </xs:choice>  
        </xs:sequence>  
    </xs:complexType>  
    <xs:complexType name="ExpandableCategoryTreeNode">  
        <xs:sequence>  
            <xs:element name="DisplayName" type="xs:string" />  
            <xs:element name="Description" type="xs:string" />  
        </xs:sequence>  
        <xs:attribute name="NodeIdentifier" type="xs:string" use="required"></xs:attribute>  
    </xs:complexType>  
    <xs:complexType name="CategoryTreeNode">  
        <xs:sequence>  
            <xs:element name="DisplayName" type="xs:string" />  
            <xs:element name="Description" type="xs:string" />  
            <xs:choice minOccurs="0" maxOccurs="unbounded">  
                <xs:element name="ExpandableCategoryTreeNode" type="ExpandableCategoryTreeNode" minOccurs="0" maxOccurs="unbounded" />  
                <xs:element name="CategoryTreeNode" type="CategoryTreeNode" minOccurs="0" maxOccurs="unbounded" />  
                <xs:element name="ServiceTreeNode" type="ServiceTreeNode" minOccurs="0" maxOccurs="unbounded" />  
            </xs:choice>  
        </xs:sequence>  
    </xs:complexType>  
    <xs:complexType name="ServiceTreeNode">  
        <xs:sequence>  
            <xs:element name="DisplayName" type="xs:string" />  
            <xs:element name="Description" type="xs:string" />  
            <xs:element name="WSDLReference" type="xs:string" />  
        </xs:sequence>  
    </xs:complexType>  
</xs:schema>  
```  
  
 <span data-ttu-id="9e2f4-143">在修改過您的 CategorySchema.xml 檔案後，重新建置 AdapterManagement 專案，然後執行 [新增配接器中繼資料精靈]，確定 CategorySchema.xml 中表示的樹狀結構有正確出現。</span><span class="sxs-lookup"><span data-stu-id="9e2f4-143">After modifying your CategorySchema.xml file, rebuild the AdapterManagement project, and then run the Add Adapter Metadata Wizard to ensure that the tree represented in CategorySchema.xml appears correctly.</span></span>  
  
 <span data-ttu-id="9e2f4-144">如需執行 「 新增配接器中繼資料精靈 」 的資訊，請參閱**新增配接器中繼資料精靈 對話方塊** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="9e2f4-144">For information about running the Add Adapter Metadata Wizard, see the **Add Adapter Metadata Wizard Dialog Box** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>