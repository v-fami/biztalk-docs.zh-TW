---
title: 如何建立屬性結構描述 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 24086dea-62b8-4ef6-8af8-eb4ab7c3c018
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ee97f4cb3065fdb201ec19f88a79e7899f03ac49
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25970476"
---
# <a name="how-to-create-property-schemas"></a><span data-ttu-id="4ddcc-102">如何建立屬性結構描述</span><span class="sxs-lookup"><span data-stu-id="4ddcc-102">How to Create Property Schemas</span></span>
<span data-ttu-id="4ddcc-103">如果您選擇要升級為屬性欄位的欄位，您必須先定義屬性結構描述。</span><span class="sxs-lookup"><span data-stu-id="4ddcc-103">If you choose to promote fields as property fields, you will need to define a property schema first.</span></span> <span data-ttu-id="4ddcc-104">此屬性結構描述將指定未結構化的欄位集合，您可以將欄位從與屬性結構描述相關之結構描述所定義的執行個體訊息升級至其中。</span><span class="sxs-lookup"><span data-stu-id="4ddcc-104">This property schema specifies an unstructured collection of fields into which you can promote fields from within an instance message defined by a schema associated with your property schema.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4ddcc-105">請勿複製和編輯現有的屬性結構描述，來建立新的結構描述。</span><span class="sxs-lookup"><span data-stu-id="4ddcc-105">Do not copy and edit an existing property schema to create a new schema.</span></span> <span data-ttu-id="4ddcc-106">屬性結構描述會包含結構描述特定的內部資料。</span><span class="sxs-lookup"><span data-stu-id="4ddcc-106">The property schema contains schema-specific internal data.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4ddcc-107">您不需要建立屬性結構描述以升級辨別欄位。</span><span class="sxs-lookup"><span data-stu-id="4ddcc-107">You do not need to create a property schema to promote distinguished fields.</span></span>  
  
### <a name="to-create-a-property-schema"></a><span data-ttu-id="4ddcc-108">建立屬性結構描述</span><span class="sxs-lookup"><span data-stu-id="4ddcc-108">To create a property schema</span></span>  
  
1.  <span data-ttu-id="4ddcc-109">在**方案總管] 中**，以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後按一下 [**新項目**。</span><span class="sxs-lookup"><span data-stu-id="4ddcc-109">In **Solution Explorer**, right-click a BizTalk project, point to **Add**, and then click **New Item**.</span></span>  
  
2.  <span data-ttu-id="4ddcc-110">在**加入新項目**對話方塊中，於**範本**區段中，按一下**屬性結構描述**。</span><span class="sxs-lookup"><span data-stu-id="4ddcc-110">In the **Add New Item** dialog box, in the **Templates** section, click **Property Schema**.</span></span>  
  
3.  <span data-ttu-id="4ddcc-111">在**名稱**方塊、 輸入結構描述的名稱，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="4ddcc-111">In the **Name** box, type a name for the schema, and then click **Add**.</span></span>  
  
     <span data-ttu-id="4ddcc-112">開啟新的屬性結構描述，且它已包含**欄位項目**名為 Property1 的節點。</span><span class="sxs-lookup"><span data-stu-id="4ddcc-112">The new property schema opens, and it already contains a **Field Element** node named Property1.</span></span>  
  
4.  <span data-ttu-id="4ddcc-113">在結構描述樹狀目錄中，使用滑鼠右鍵按一下**欄位項目**] 節點，按一下 [**重新命名**中結構描述中，輸入第一個屬性的描述性名稱，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="4ddcc-113">In the schema tree, right-click that **Field Element** node, click **Rename**, type a descriptive name for the first property in the schema, and then press ENTER.</span></span>  
  
5.  <span data-ttu-id="4ddcc-114">設定**資料型別**和其他相關的屬性，適當地為**欄位項目**屬性 視窗中的節點。</span><span class="sxs-lookup"><span data-stu-id="4ddcc-114">Set the **Data Type** and other relevant properties, as appropriate, for the **Field Element** node in the Properties window.</span></span>  
  
6.  <span data-ttu-id="4ddcc-115">如果您想要插入**欄位項目**節點的其他屬性，以滑鼠右鍵按一下\<結構描述\>節點中，按一下 **插入結構描述節點**，然後按一下  **子欄位項目**，然後重複步驟 4 和 5。</span><span class="sxs-lookup"><span data-stu-id="4ddcc-115">If you want to insert **Field Element** nodes for additional properties, right-click the \<Schema\> node, click **Insert Schema Node**, and then click **Child Field Element**, and then repeat steps 4 and 5.</span></span> <span data-ttu-id="4ddcc-116">若要建立一組必要的視需要重複**欄位項目**您打算從執行個體訊息升級值的節點。</span><span class="sxs-lookup"><span data-stu-id="4ddcc-116">Repeat as necessary to create the required set of **Field Element** nodes into which you intend to promote values from instance messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ddcc-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="4ddcc-117">See Also</span></span>  
 [<span data-ttu-id="4ddcc-118">管理專案中的結構描述</span><span class="sxs-lookup"><span data-stu-id="4ddcc-118">Managing Schemas Within Projects</span></span>](../core/managing-schemas-within-projects.md)