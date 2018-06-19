---
title: 如何建立使用其他結構描述的結構描述 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff0bcd9a-6c66-4c3b-bd41-64047a7c8392
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f427e5cd8e3f82e57dc8926c6e00889e1c97afe9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22249414"
---
# <a name="how-to-create-schemas-that-use-other-schemas"></a><span data-ttu-id="03ea9-102">如何建立使用其他結構描述的結構描述</span><span class="sxs-lookup"><span data-stu-id="03ea9-102">How to Create Schemas That Use Other Schemas</span></span>
<span data-ttu-id="03ea9-103">XML 結構描述定義 (XSD) 語言提供三個不同但相關的機制，以便在某個結構描述中使用另一個結構描述。</span><span class="sxs-lookup"><span data-stu-id="03ea9-103">XML Schema definition (XSD) language provides three different but related mechanisms for using one schema within another schema.</span></span> <span data-ttu-id="03ea9-104">這些機制為匯入結構描述、包含結構描述以及重新定義結構描述。</span><span class="sxs-lookup"><span data-stu-id="03ea9-104">These mechanisms are importing a schema, including a schema, and redefining a schema.</span></span> <span data-ttu-id="03ea9-105">這些機制及其有何差異的簡短摘要，請參閱[使用其他結構描述的](../core/schemas-that-use-other-schemas.md)。</span><span class="sxs-lookup"><span data-stu-id="03ea9-105">For a brief summary of these mechanisms and how they differ, see [Schemas That Use Other Schemas](../core/schemas-that-use-other-schemas.md).</span></span> <span data-ttu-id="03ea9-106">如需詳細資訊，請參閱[在網站上的 XSD 資源](../core/xsd-resources-on-the-web.md)取得 XSD 入門與規格的連結。</span><span class="sxs-lookup"><span data-stu-id="03ea9-106">For detailed information, see [XSD Resources on the Web](../core/xsd-resources-on-the-web.md) for links to the XSD primer and specifications.</span></span>  
  
 <span data-ttu-id="03ea9-107">本主題描述在進行開發的結構描述中匯入、包含及重新定義其他結構描述所需的步驟。</span><span class="sxs-lookup"><span data-stu-id="03ea9-107">This topic describes the steps required to import, include, and redefine other schemas within the schema you are developing.</span></span>  
  
### <a name="to-import-include-or-redefine-one-schema-within-another-schema"></a><span data-ttu-id="03ea9-108">在某個結構描述中匯入、包含或重新定義另一個結構描述</span><span class="sxs-lookup"><span data-stu-id="03ea9-108">To import, include, or redefine one schema within another schema</span></span>  
  
1.  <span data-ttu-id="03ea9-109">在 BizTalk 編輯器中，開啟要匯入、包含或重新定義某個結構描述的另一個結構描述。</span><span class="sxs-lookup"><span data-stu-id="03ea9-109">In BizTalk Editor, open the schema to which you want to import, include, or redefine another schema.</span></span> <span data-ttu-id="03ea9-110">您可以在 [方案總管] 中按兩下結構描述以開啟它。</span><span class="sxs-lookup"><span data-stu-id="03ea9-110">You can open a schema by double-clicking it in Solution Explorer.</span></span>  
  
2.  <span data-ttu-id="03ea9-111">選取**結構描述**節點在結構描述樹狀檢視的頂端。</span><span class="sxs-lookup"><span data-stu-id="03ea9-111">Select the **Schema** node at the top of the schema tree view.</span></span>  
  
3.  <span data-ttu-id="03ea9-112">如有需要，請按 F4，開啟 [[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 屬性] 視窗。</span><span class="sxs-lookup"><span data-stu-id="03ea9-112">If necessary, press F4 to open the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window.</span></span>  
  
4.  <span data-ttu-id="03ea9-113">在 [屬性] 視窗中**進階**類別目錄中的值部分**匯入**屬性中，按一下省略符號 (**...**) 按鈕。</span><span class="sxs-lookup"><span data-stu-id="03ea9-113">In the Properties window, in the **Advanced** category, in the value portion of the **Imports** property, click the ellipsis (**...**) button.</span></span>  
  
5.  <span data-ttu-id="03ea9-114">在**匯入**對話方塊中，於**匯入新結構描述為**清單中，選取**XSD 匯入**， **XSD Include**，或**XSD重新定義**，適當地，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="03ea9-114">In the **Imports** dialog box, in the **Import New Schema as** list, select **XSD Import**, **XSD Include**, or **XSD Redefine**, as appropriate, and then click **Add**.</span></span>  
  
6.  <span data-ttu-id="03ea9-115">在**BizTalk 型別選擇器**對話方塊方塊中，展開 **結構描述**節點在專案樹狀目錄中，選取您想要匯入、 包括或重新定義，然後按一下 結構描述**確定**。</span><span class="sxs-lookup"><span data-stu-id="03ea9-115">In the **BizTalk Type Picker** dialog box, expand the **Schema** node in the project tree, select the schema that you want to import, include, or redefine, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="03ea9-116">在**匯入**對話方塊中，按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="03ea9-116">In the **Imports** dialog box, click **OK**.</span></span>  
  
     <span data-ttu-id="03ea9-117">適當 XSD 指示詞，來實作匯入、 包含或重新定義作業加入至**結構描述**在 XSD 檢視中，包括新的項目**匯入**，**包含**，或**重新定義**項目，視需要。</span><span class="sxs-lookup"><span data-stu-id="03ea9-117">The appropriate XSD directives to implement the import, include, or redefine operation are added to the **schema** element in the XSD view, including a new **import**, **include**, or **redefine** element, as appropriate.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="03ea9-118">請確定您瞭解這三種機制的不同目的，例如它們在命名空間需求方面的差異。</span><span class="sxs-lookup"><span data-stu-id="03ea9-118">Make sure you understand the different purposes of these three mechanisms, such as how they differ with respect to namespace requirements.</span></span> <span data-ttu-id="03ea9-119">您可以隨時刪除先前已匯入、 包含或重新定義結構描述，然後使用其中一個其他兩個機制，但根據您如何廣泛地參考該結構描述，您可能需要重新據以處理您的結構描述。</span><span class="sxs-lookup"><span data-stu-id="03ea9-119">You can always delete a previously imported, included, or redefined schema and then use one of the other two mechanisms, but depending on how extensively you have referenced that schema, you may need to rework your schema accordingly.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="03ea9-120">在某個結構描述中匯入、包含和重新定義另一個結構描述的 XSD 機制是藉由參考至已匯入、已包含或已重新定義的結構描述來運作。</span><span class="sxs-lookup"><span data-stu-id="03ea9-120">The XSD mechanism for importing, including, and redefining one schema within another schema works by reference to the imported, included, or redefined schema.</span></span> <span data-ttu-id="03ea9-121">這表示若您對已匯入、已包含或已重新定義的結構描述進行變更，該變更將會反映在包含匯入、包含或重新定義參考的結構描述中。</span><span class="sxs-lookup"><span data-stu-id="03ea9-121">This means that if you make a change to the imported, included, or redefined schema, that change will be reflected in the schema containing the import, include, or redefine reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03ea9-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="03ea9-122">See Also</span></span>  
 <span data-ttu-id="03ea9-123">[管理專案中的結構描述](../core/managing-schemas-within-projects.md) </span><span class="sxs-lookup"><span data-stu-id="03ea9-123">[Managing Schemas Within Projects](../core/managing-schemas-within-projects.md) </span></span>  
 [<span data-ttu-id="03ea9-124">如何建立其他節點或類型的參考</span><span class="sxs-lookup"><span data-stu-id="03ea9-124">How to Create References to Another Node or Type</span></span>](../core/how-to-create-references-to-another-node-or-type.md)