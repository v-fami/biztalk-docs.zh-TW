---
title: "產生和驗證訊息執行個體 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7a306846-3942-4ba1-a74e-6ead8deb0322
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 964f9bd2ee2b8bb20872bc593723cea778b5ed81
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="instance-message-generation-and-validation"></a><span data-ttu-id="720fe-102">產生和驗證執行個體訊息</span><span class="sxs-lookup"><span data-stu-id="720fe-102">Instance Message Generation and Validation</span></span>
<span data-ttu-id="720fe-103">驗證結構描述之後，您可以用它來產生範例執行個體訊息。</span><span class="sxs-lookup"><span data-stu-id="720fe-103">After you have validated a schema, you can use it to generate a sample instance message.</span></span> <span data-ttu-id="720fe-104">產生的範例執行個體訊息包含由結構描述指定的項目和屬性結構，並且在必要時產生假資料。</span><span class="sxs-lookup"><span data-stu-id="720fe-104">The sample instance message that is generated contains the element and attribute structure specified by the schema, and generate fake data where required.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="720fe-105">產生執行個體訊息不不夠精細，產生根據指定的數個屬性值的資料時使用的資料產生機制。</span><span class="sxs-lookup"><span data-stu-id="720fe-105">The data-generation mechanism used when generating instance messages is not sufficiently sophisticated to generate data according to values specified for several properties.</span></span> <span data-ttu-id="720fe-106">例如，如果結構描述中包含的任何值**模式**屬性，這是用於**限制**類別**欄位項目**節點和**欄位屬性**節點時其**Derived By**屬性設定為**限制**，產生的執行個體訊息不能做為輸入**驗證執行個體**作業。</span><span class="sxs-lookup"><span data-stu-id="720fe-106">For example, if the schema contains any values for the **Pattern** property, which is available in the **Restrictions** category for **Field Element** nodes and **Field Attribute** nodes when their **Derived By** property is set to **Restriction**, the generated instance message cannot be used as is, as input to the **Validate Instance** operation.</span></span>  
  
 <span data-ttu-id="720fe-107">若要從結構描述產生範例執行個體訊息，請使用**產生執行個體**在方案總管 中的結構描述相關聯的捷徑功能表上的命令。</span><span class="sxs-lookup"><span data-stu-id="720fe-107">To generate a sample instance message from a schema, use the **Generate Instance** command on the shortcut menu associated with the schema in Solution Explorer.</span></span> <span data-ttu-id="720fe-108">執行個體訊息產生作業的結果會顯示在 [[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 輸出] 視窗中。</span><span class="sxs-lookup"><span data-stu-id="720fe-108">The results of the instance message generation operation are reported in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Output window.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="720fe-109">**產生執行個體**作業包含**驗證結構描述**作業。</span><span class="sxs-lookup"><span data-stu-id="720fe-109">The **Generate Instance** operation includes the **Validate Schema** operation.</span></span> <span data-ttu-id="720fe-110">若驗證失敗，則不會產生任何範例執行個體訊息。</span><span class="sxs-lookup"><span data-stu-id="720fe-110">If validation fails, no sample instance message will be generated.</span></span>  
  
 <span data-ttu-id="720fe-111">如有關如何從結構描述，包括如何設定輸出檔案包含產生的執行個體訊息中，產生執行個體訊息的詳細逐步指示，請參閱[產生執行個體訊息](../core/how-to-generate-instance-messages.md)。</span><span class="sxs-lookup"><span data-stu-id="720fe-111">For detailed step-by-step instructions regarding how to generate an instance message from a schema, including how to configure an output file to contain the generated instance message, see [Generating Instance Messages](../core/how-to-generate-instance-messages.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="720fe-112">如果您未指定的值**根參考**屬性**結構描述**節點，BizTalk 編輯器產生結構描述中的第一個根節點的執行個體訊息。</span><span class="sxs-lookup"><span data-stu-id="720fe-112">If you do not specify a value for the **Root Reference** property of the **Schema** node, BizTalk Editor generates an instance message for the first root node in the schema.</span></span> <span data-ttu-id="720fe-113">如果您指定的值**根參考**屬性，BizTalk 編輯器會產生指定之根執行個體訊息。</span><span class="sxs-lookup"><span data-stu-id="720fe-113">If you specify a value for the **Root Reference** property, BizTalk Editor generates an instance message for the specified root.</span></span>  
  
 <span data-ttu-id="720fe-114">若您已驗證結構描述，可以使用「BizTalk 編輯器」判斷執行個體訊息是否符合該結構描述。</span><span class="sxs-lookup"><span data-stu-id="720fe-114">If you have validated your schema, you can use BizTalk Editor to determine whether an instance message conforms to that schema.</span></span>  
  
 <span data-ttu-id="720fe-115">若要驗證執行個體訊息結構描述，使用**驗證執行個體**在方案總管 中的結構描述相關聯的捷徑功能表上的命令。</span><span class="sxs-lookup"><span data-stu-id="720fe-115">To validate an instance message against a schema, use the **Validate Instance** command on the shortcut menu associated with the schema in Solution Explorer.</span></span> <span data-ttu-id="720fe-116">驗證的結果會顯示在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] [輸出] 視窗中。</span><span class="sxs-lookup"><span data-stu-id="720fe-116">The results of the validation are reported in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Output window.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="720fe-117">在某些情況下，產生的執行個體訊息無法通過針對產生該執行個體訊息的相同結構描述之驗證。</span><span class="sxs-lookup"><span data-stu-id="720fe-117">There are cases in which a generated instance message will not pass validation against the same schema from which it was generated.</span></span> <span data-ttu-id="720fe-118">例如，如果您嘗試驗證由使用產生的執行個體訊息**產生執行個體**BizTalk 編輯器 」 以及相關的結構描述中的命令包含任何**欄位項目**節點或**欄位屬性**有的節點及其**Derived By**屬性設定為**限制**及其中使用**模式**屬性來指定對應的資料必須遵守的模式，驗證將會失敗。</span><span class="sxs-lookup"><span data-stu-id="720fe-118">For example, if you attempt to validate an instance message that was generated by using the **Generate Instance** command in BizTalk Editor, and the relevant schema includes any **Field Element** nodes or **Field Attribute** nodes that have their **Derived By** property set to **Restriction** and which use the **Pattern** property to specify a pattern to which the corresponding data must conform, the validation will fail.</span></span> <span data-ttu-id="720fe-119">這是因為不產生執行個體訊息時使用的資料產生機制不夠精細，產生的資料，根據指定的值是**模式**屬性。</span><span class="sxs-lookup"><span data-stu-id="720fe-119">This is because the data-generation mechanism used when generating instance messages is not sufficiently sophisticated to generate data according to values specified for the **Pattern** property.</span></span> <span data-ttu-id="720fe-120">還有其他狀況也會導致驗證失敗。</span><span class="sxs-lookup"><span data-stu-id="720fe-120">Other cases also exist.</span></span>  
  
 <span data-ttu-id="720fe-121">如需詳細的逐步指示，有關如何驗證執行個體訊息，包括如何指定執行個體訊息，進行驗證，請參閱[驗證結構描述](../core/how-to-validate-schemas-in-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="720fe-121">For detailed step-by-step instructions regarding how to validate an instance message, including how to specify the instance message to be validated, see [Validating Schemas](../core/how-to-validate-schemas-in-visual-studio.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="720fe-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="720fe-122">See Also</span></span>  
 <span data-ttu-id="720fe-123">[關於結構描述](../core/about-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="720fe-123">[About Schemas](../core/about-schemas.md) </span></span>  
 [<span data-ttu-id="720fe-124">測試結構描述</span><span class="sxs-lookup"><span data-stu-id="720fe-124">Testing Schemas</span></span>](../core/testing-schemas.md)