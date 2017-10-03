---
title: "如何建立 XML 訊息的結構描述 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a0270293-fe23-42bd-b090-e877d5e9ce0b
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 83a06aa7ca1ee4e37c29083ac38f5285565b7325
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-schemas-for-xml-messages"></a><span data-ttu-id="904d0-102">如何建立 XML 訊息的結構描述</span><span class="sxs-lookup"><span data-stu-id="904d0-102">How to Create Schemas for XML Messages</span></span>
<span data-ttu-id="904d0-103">有數種方法可以建立 BizTalk 訊息結構描述。</span><span class="sxs-lookup"><span data-stu-id="904d0-103">There are several methods for creating BizTalk message schemas.</span></span> <span data-ttu-id="904d0-104">本主題提供部分這些方法的逐步指示。</span><span class="sxs-lookup"><span data-stu-id="904d0-104">This topic provides step-by-step instructions for some of those methods.</span></span>  
  
### <a name="to-create-a-new-schema"></a><span data-ttu-id="904d0-105">建立新結構描述</span><span class="sxs-lookup"><span data-stu-id="904d0-105">To create a new schema</span></span>  
  
1.  <span data-ttu-id="904d0-106">在**方案總管 中**，選取您要新增結構描述的 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="904d0-106">In **Solution Explorer**, select the BizTalk project to which you want to add a schema.</span></span>  
  
2.  <span data-ttu-id="904d0-107">在 [專案] 功能表上，按一下 [加入新項目]。</span><span class="sxs-lookup"><span data-stu-id="904d0-107">On the **Project** menu, click **Add New Item**.</span></span>  
  
3.  <span data-ttu-id="904d0-108">在**加入新項目- \<* BizTalk ProjectName*> * * 對話方塊中，於**範本**區段中，按一下**結構描述**。</span><span class="sxs-lookup"><span data-stu-id="904d0-108">In the **Add New Item - \<*BizTalk ProjectName*>** dialog box, in the **Templates** section, click **Schema**.</span></span>  
  
4.  <span data-ttu-id="904d0-109">在**名稱**方塊、 輸入結構描述的名稱，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="904d0-109">In the **Name** box, type a name for the schema, and then click **Add**.</span></span>  
  
5.  <span data-ttu-id="904d0-110">如有需要，請按 F4，開啟 [[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 屬性] 視窗。</span><span class="sxs-lookup"><span data-stu-id="904d0-110">If necessary, press F4 to open the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window.</span></span>  
  
6.  <span data-ttu-id="904d0-111">在結構描述樹狀結構檢視中，選取**結構描述** 節點，然後在 屬性 視窗中，選取**目標命名空間**內容，然後輸入目標命名空間的名稱。</span><span class="sxs-lookup"><span data-stu-id="904d0-111">In the schema tree view, select the **Schema** node, and then in the Properties window, select the **Target Namespace** property and type a name for the target namespace.</span></span> <span data-ttu-id="904d0-112">您在建立結構描述; 的初始階段中設定這個屬性很重要請避免使用預設**目標命名空間**屬性值。</span><span class="sxs-lookup"><span data-stu-id="904d0-112">It is important that you set this property in this initial phase of schema creation; avoid using the default **Target Namespace** property value.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="904d0-113">某些專案成員檔案 (例如結構描述檔案) 名稱的選擇，可能會因為和 C# 保留字、.NET Framework 類型及命名空間名稱 (例如 System) 衝突，而在之後造成編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="904d0-113">Certain name choices for project member files, such as schema files, can cause compilation errors later on due to conflicts with C# reserved words and.NET Framework type and namespace names (such as System).</span></span> <span data-ttu-id="904d0-114">結構描述的範例包括 schema.xsd、XmlContent 及 RootNodes。</span><span class="sxs-lookup"><span data-stu-id="904d0-114">Examples for schemas include schema.xsd, XmlContent, and RootNodes.</span></span> <span data-ttu-id="904d0-115">這是因為**型別名稱**屬性預設為基底 （不含副檔名） 部分**Filename**屬性。</span><span class="sxs-lookup"><span data-stu-id="904d0-115">This is because the **Type Name** property defaults to the base (non-extension) portion of the  **Filename** property.</span></span> <span data-ttu-id="904d0-116">您可以藉由明確地變更的值解決這種類型的編譯錯誤**型別名稱**為不衝突的屬性。</span><span class="sxs-lookup"><span data-stu-id="904d0-116">You can work around this type of compilation error by explicitly changing the value of the **Type Name** property to something that does not conflict.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="904d0-117">您可能需要新增、刪除和修改結構描述中的記錄和欄位，及其關聯的屬性。</span><span class="sxs-lookup"><span data-stu-id="904d0-117">You may need to add, delete, and modify the records and fields in your schema along with their associated properties.</span></span> <span data-ttu-id="904d0-118">若要深入了解，請參閱[管理內結構描述節點](../core/managing-the-nodes-within-a-schema.md)。</span><span class="sxs-lookup"><span data-stu-id="904d0-118">To learn more about this, see [Managing the Nodes Within a Schema](../core/managing-the-nodes-within-a-schema.md).</span></span>  
  
### <a name="to-generate-a-schema-from-a-non-xsd-source"></a><span data-ttu-id="904d0-119">從非 XSD 來源產生結構描述</span><span class="sxs-lookup"><span data-stu-id="904d0-119">To generate a schema from a non-XSD source</span></span>  
  
1.  <span data-ttu-id="904d0-120">在**方案總管] 中**，以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後按一下 [**新增產生的項目**。</span><span class="sxs-lookup"><span data-stu-id="904d0-120">In **Solution Explorer**, right-click a BizTalk project, point to **Add**, and then click **Add Generated Items**.</span></span>  
  
2.  <span data-ttu-id="904d0-121">在**新增產生的項目- \<* BizTalk ProjectName*> * * 對話方塊中，於**範本**區段中，按一下**產生結構描述**，然後按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="904d0-121">In the **Add Generated Items - \<*BizTalk ProjectName*>** dialog box, in the **Templates** section, click **Generate Schemas**, and then click **Add**.</span></span>  
  
3.  <span data-ttu-id="904d0-122">在**產生結構描述**對話方塊中，於**文件類型**下拉式清單中，選取**XDR 結構描述**， **DTD 結構描述**，或**格式正確的 XML**。</span><span class="sxs-lookup"><span data-stu-id="904d0-122">In the **Generate Schemas** dialog box, in the **Document type** drop-down list, select **XDR Schema**, **DTD Schema**, or **Well-Formed XML**.</span></span>  
  
     <span data-ttu-id="904d0-123">如果您看到**DTD （未載入）**或**格式正確的 XML （未載入）**在下拉式清單中，選取適當的文件類型，並將引導您安裝的程序遺失的 DLL。</span><span class="sxs-lookup"><span data-stu-id="904d0-123">If you see either **DTD (Not Loaded)** or **Well-Formed XML (Not Loaded)** in the drop-down list, select the appropriate document type anyway, and you will be guided through the process of installing the missing DLL.</span></span> <span data-ttu-id="904d0-124">接著，請重複這些步驟。</span><span class="sxs-lookup"><span data-stu-id="904d0-124">Then repeat these steps.</span></span>  
  
4.  <span data-ttu-id="904d0-125">在**產生結構描述**對話方塊中，按一下 **瀏覽**，找出您想要匯入，然後按一下 的檔案**開啟**。</span><span class="sxs-lookup"><span data-stu-id="904d0-125">In the **Generate Schemas** dialog box, click **Browse**, locate the file you want to import, and then click **Open**.</span></span> <span data-ttu-id="904d0-126">您找到的檔案必須符合您在上一個步驟中選取的文件類型。</span><span class="sxs-lookup"><span data-stu-id="904d0-126">The file you locate must match the document type you selected in the previous step.</span></span>  
  
     <span data-ttu-id="904d0-127">此時會從指定的檔案產生新的結構描述，此結構描述會使用與該檔案相同的名稱並含有副檔名 .xsd，並在 [BizTalk 編輯器] 中開啟。</span><span class="sxs-lookup"><span data-stu-id="904d0-127">A new schema is generated from the specified file, using the same name as that file with the .xsd extension, and opened in BizTalk Editor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="904d0-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="904d0-128">See Also</span></span>  
 [<span data-ttu-id="904d0-129">管理專案中的結構描述</span><span class="sxs-lookup"><span data-stu-id="904d0-129">Managing Schemas Within Projects</span></span>](../core/managing-schemas-within-projects.md)