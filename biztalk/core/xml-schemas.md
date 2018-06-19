---
title: XML 結構描述 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1ec364e7-866d-4164-be91-be75a40ce878
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 86760d50b729419f31ba8186033181e0d03ad14c
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26008095"
---
# <a name="xml-schemas"></a><span data-ttu-id="4a682-102">XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="4a682-102">XML Schemas</span></span>
<span data-ttu-id="4a682-103">XML 結構描述會說明以 XML 呈現的商務文件。</span><span class="sxs-lookup"><span data-stu-id="4a682-103">An XML schema describes a business document that is represented in XML.</span></span> <span data-ttu-id="4a682-104">因為 Microsoft BizTalk Server 會使用 XML 做為其標準表示商務文件，所以輸入和輸出文件不需要進行任何轉譯。</span><span class="sxs-lookup"><span data-stu-id="4a682-104">Because Microsoft BizTalk Server uses XML as its canonical representation for business documents, inbound and outbound documents do not require any translation.</span></span> <span data-ttu-id="4a682-105">可以在 BizTalk 編輯器中只使用所有結構描述內均提供的基本屬性組來建立 XML 結構描述，而不需啟用任何的結構描述編輯器延伸模組。</span><span class="sxs-lookup"><span data-stu-id="4a682-105">XML schemas can be created in BizTalk Editor using only the basic set of properties that are available within all schemas, and do not require any schema editor extensions to be enabled.</span></span>  
  
 <span data-ttu-id="4a682-106">有幾種的方式，您可以在其中建立 BizTalk Server 中的 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="4a682-106">There are several ways in which you can create XML schemas in BizTalk Server.</span></span> <span data-ttu-id="4a682-107">其中包括：</span><span class="sxs-lookup"><span data-stu-id="4a682-107">These include:</span></span>  
  
-   <span data-ttu-id="4a682-108">**建立新的結構描述**。</span><span class="sxs-lookup"><span data-stu-id="4a682-108">**Creating a new schema**.</span></span> <span data-ttu-id="4a682-109">此種建立結構描述的方法涉及將結構描述新增到 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="4a682-109">This method of schema creation involves adding a new schema to a BizTalk project.</span></span> <span data-ttu-id="4a682-110">在**方案總管] 中**、 以滑鼠右鍵按一下 BizTalk 專案、 按一下**新增**，按一下**新項目**，然後按一下 [**結構描述**。</span><span class="sxs-lookup"><span data-stu-id="4a682-110">In **Solution Explorer**, right-click the BizTalk project, click **Add**, click **New Item**, and then click **Schema**.</span></span> <span data-ttu-id="4a682-111">在結構描述樹狀結構檢視中新增各種節點來建置結構描述的結構。</span><span class="sxs-lookup"><span data-stu-id="4a682-111">Build up the structure of the schema by adding various nodes in the schema tree view.</span></span>  
  
-   <span data-ttu-id="4a682-112">**建立新的結構描述中，搭配其他結構描述**。</span><span class="sxs-lookup"><span data-stu-id="4a682-112">**Creating a new schema, in conjunction with other schemas**.</span></span> <span data-ttu-id="4a682-113">對於實際上複雜的結構描述，您更有可能會使用其他現有結構描述所提供的類型，來建置訊息的結構描述。</span><span class="sxs-lookup"><span data-stu-id="4a682-113">For complex schemas in the real world, you are more likely to build the schemas for your messages by using types provided in other existing schemas.</span></span> <span data-ttu-id="4a682-114">藉由使用 XML 結構描述定義 (XSD) 語言的匯入、包括和重新定義結構描述等概念，您便可以利用其他結構描述中已經定義的類型。</span><span class="sxs-lookup"><span data-stu-id="4a682-114">By using the XML Schema definition (XSD) language concepts of importing, including, and redefining schemas, you can take advantage of types already defined in other schemas.</span></span> <span data-ttu-id="4a682-115">如需有關如何同時使用多個結構描述的詳細資訊，請參閱[使用其他結構描述的](../core/schemas-that-use-other-schemas.md)。</span><span class="sxs-lookup"><span data-stu-id="4a682-115">For more information about using multiple schemas together, see [Schemas That Use Other Schemas](../core/schemas-that-use-other-schemas.md).</span></span>  
  
-   <span data-ttu-id="4a682-116">**從執行個體訊息產生結構描述**。</span><span class="sxs-lookup"><span data-stu-id="4a682-116">**Generating a schema from an instance message**.</span></span> <span data-ttu-id="4a682-117">您可以產生對應於特定執行個體訊息的 XML 結構描述，只要該特定執行個體訊息是由格式正確的 XML 組成即可。</span><span class="sxs-lookup"><span data-stu-id="4a682-117">You can generate an XML schema that corresponds to a particular instance message as long as that instance message consists of well-formed XML.</span></span> <span data-ttu-id="4a682-118">使用**新增產生的項目-  *\<BizTalk 專案名稱\>*** 對話方塊中，按一下，即可存取**新增產生的項目**上**專案**功能表上，若要執行這種類型的結構描述產生作業。</span><span class="sxs-lookup"><span data-stu-id="4a682-118">Use the **Add Generated Items - *\<BizTalk Project Name\>*** dialog box, accessed by clicking **Add Generated Items** on the **Project** menu, to perform this type of schema generation operation.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4a682-119">此類型的產生作業僅可用於產生 XML 結構描述，不可用於屬性結構描述或一般檔案結構描述。</span><span class="sxs-lookup"><span data-stu-id="4a682-119">This type of generation operation can only be used to generate XML schemas, not property schemas or flat file schemas.</span></span>  
  
-   <span data-ttu-id="4a682-120">**將結構描述從舊版的結構描述規格語言移轉至 XSD**。</span><span class="sxs-lookup"><span data-stu-id="4a682-120">**Migrating a schema from an older schema specification language to XSD**.</span></span> <span data-ttu-id="4a682-121">您可以從使用舊版的 XML 資料精簡 (XDR) 格式儲存結構描述的 BizTalk Server 所開發的結構描述，以便讓 BizTalk Server 產生的 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="4a682-121">You can generate an XML schema for BizTalk Server from a schema that was developed by using a previous version of BizTalk Server, which stored schemas in XML-Data Reduced (XDR) format.</span></span> <span data-ttu-id="4a682-122">如需如何將較舊的 XDR 結構描述移轉至 BizTalk Server 所使用的 XSD 格式的詳細資訊，請參閱[從先前舊版 BizTalk Server 移轉結構描述](../core/schema-migration-from-previous-versions-of-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="4a682-122">For more information about how to migrate older XDR schemas to the XSD format used by BizTalk Server, see [Schema Migration from Previous Versions of BizTalk Server](../core/schema-migration-from-previous-versions-of-biztalk-server.md).</span></span>  
  
     <span data-ttu-id="4a682-123">您也可以從使用文件類型定義 (DTD) 語法表示的文件結構描述，根據 XSD 來產生 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="4a682-123">You can also generate an XML schema based on XSD from a document schema expressed by using the Document Type Definition (DTD) syntax.</span></span>  
  
     <span data-ttu-id="4a682-124">使用**新增產生的項目-  *\<BizTalk 專案名稱\>*** 對話方塊中，按一下，即可存取**新增產生的項目**上**專案**功能表上，若要執行這種類型的結構描述產生作業。</span><span class="sxs-lookup"><span data-stu-id="4a682-124">Use the **Add Generated Items - *\<BizTalk Project Name\>*** dialog box, accessed by clicking **Add Generated Items** on the **Project** menu, to perform this type of schema generation operation.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4a682-125">這些類型的產生作業僅可用於產生 XML 結構描述，不可用於屬性結構描述或一般檔案結構描述。</span><span class="sxs-lookup"><span data-stu-id="4a682-125">These types of generation operations can only be used to generate XML schemas, not property schemas or flat file schemas.</span></span>  
  
 <span data-ttu-id="4a682-126">無論您使用何種結構描述建立技術，都需要繼續修改結構描述，以便充分提供對應執行個體訊息的完整描述。</span><span class="sxs-lookup"><span data-stu-id="4a682-126">Whichever schema creation technique you use, you will continue by modifying the schema so that it provides a sufficiently complete description of its corresponding instance messages.</span></span> <span data-ttu-id="4a682-127">若要開始這些工作，請參閱[管理內結構描述節點](../core/managing-the-nodes-within-a-schema.md)，[設定節點屬性](../core/how-to-set-node-properties.md)，和[使用現有的節點](../core/working-with-existing-nodes.md)。</span><span class="sxs-lookup"><span data-stu-id="4a682-127">To get started on these tasks, see [Managing the Nodes Within a Schema](../core/managing-the-nodes-within-a-schema.md), [Setting Node Properties](../core/how-to-set-node-properties.md), and [Working with Existing Nodes](../core/working-with-existing-nodes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a682-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="4a682-128">See Also</span></span>  
 [<span data-ttu-id="4a682-129">不同類型的 BizTalk 結構描述</span><span class="sxs-lookup"><span data-stu-id="4a682-129">Different Types of BizTalk Schemas</span></span>](../core/different-types-of-biztalk-schemas.md)