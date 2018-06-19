---
title: 如何產生執行個體訊息 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff74c67a-7e73-4153-9ec4-e6e50464ee92
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a911e4b0f1167e8ec200dad65b8dacb94bb08be3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22254398"
---
# <a name="how-to-generate-instance-messages"></a><span data-ttu-id="08c2b-102">如何產生執行個體訊息</span><span class="sxs-lookup"><span data-stu-id="08c2b-102">How to Generate Instance Messages</span></span>
<span data-ttu-id="08c2b-103">在您已經建構結構描述之後，可以利用從結構描述產生範例執行個體訊息的方法來檢查您的工作。</span><span class="sxs-lookup"><span data-stu-id="08c2b-103">After you have constructed a schema, one way to check your work is to generate a sample instance message from the schema.</span></span> <span data-ttu-id="08c2b-104">在許多方面，查看執行個體訊息會比查看結構描述樹狀結構，或是結構描述的 XML 結構描述定義 (XSD) 語言表示法更為直接。</span><span class="sxs-lookup"><span data-stu-id="08c2b-104">In many ways, looking at an instance message is much more straightforward than looking at either the schema tree or the XML Schema definition (XSD) language representation of the schema.</span></span> <span data-ttu-id="08c2b-105">這是因為結構描述需要描述對應的執行個體訊息的所有可能變化，而且特定的執行個體訊息只需要使用結構描述指定的格式即可傳遞某些資料。</span><span class="sxs-lookup"><span data-stu-id="08c2b-105">This is because the schema needs to describe all of the possible variations of the corresponding instance messages, and a specific instance message just needs to convey some data by using the format specified by the schema.</span></span> <span data-ttu-id="08c2b-106">產生的執行個體訊息只是範例，可能無法顯示由對應的結構描述定義的所有結構。</span><span class="sxs-lookup"><span data-stu-id="08c2b-106">The generated instance message is a sample and may not show all of the structures defined by the corresponding schema.</span></span>  
  
### <a name="to-explicitly-specify-a-file-to-contain-the-generated-instance-message"></a><span data-ttu-id="08c2b-107">明確指定檔案包含產生的執行個體訊息</span><span class="sxs-lookup"><span data-stu-id="08c2b-107">To explicitly specify a file to contain the generated instance message</span></span>  
  
1.  <span data-ttu-id="08c2b-108">在 方案總管 中，以滑鼠右鍵按一下您要產生執行個體訊息，然後按一下 結構的描述**屬性**。</span><span class="sxs-lookup"><span data-stu-id="08c2b-108">In Solution Explorer, right-click the schema for which you want to generate an instance message, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="08c2b-109">如有必要，在 [屬性] 視窗中，依序展開**一般**區段**一般**索引標籤上，按一下其加號 （+） 圖示。</span><span class="sxs-lookup"><span data-stu-id="08c2b-109">If necessary, in the Properties window, expand the **General** section of the **General** tab by clicking its plus (+) icon.</span></span>  
  
3.  <span data-ttu-id="08c2b-110">在**輸出執行個體檔案名稱**屬性值欄位中，輸入檔案名稱或使用省略符號 (**...**) 按鈕來瀏覽其產生的執行個體訊息檔案放置，然後按一下 [值] 欄位右端**儲存**。</span><span class="sxs-lookup"><span data-stu-id="08c2b-110">In the **Output Instance Filename** property value field, either type the name of a file or use the ellipsis (**...**) button at the right end of the value field to browse for a file into which generated instance messages will be placed, and then click **Save**.</span></span>  
  
### <a name="to-specify-the-type-of-the-generated-instance-message"></a><span data-ttu-id="08c2b-111">指定產生的執行個體訊息類型</span><span class="sxs-lookup"><span data-stu-id="08c2b-111">To specify the type of the generated instance message</span></span>  
  
1.  <span data-ttu-id="08c2b-112">在 方案總管 中，以滑鼠右鍵按一下您要產生執行個體訊息，然後按一下 結構的描述**屬性**。</span><span class="sxs-lookup"><span data-stu-id="08c2b-112">In Solution Explorer, right-click the schema for which you want to generate an instance message, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="08c2b-113">如有必要，在 [屬性] 視窗中，依序展開**一般**區段**一般**索引標籤上，按一下其加號 （+） 圖示。</span><span class="sxs-lookup"><span data-stu-id="08c2b-113">If necessary, in the Properties window, expand the **General** section of the **General** tab by clicking its plus (+) icon.</span></span>  
  
3.  <span data-ttu-id="08c2b-114">在**產生執行個體輸出類型**屬性值欄位中，使用下拉式清單來選取  **XML**或**原生**為產生的執行個體訊息的型別。</span><span class="sxs-lookup"><span data-stu-id="08c2b-114">In the **Generate Instance Output Type** property value field, use the drop-down list to select either **XML** or **Native** as the type of the instance message to be generated.</span></span>  
  
     <span data-ttu-id="08c2b-115">**XML**是預設值。</span><span class="sxs-lookup"><span data-stu-id="08c2b-115">**XML** is the default value.</span></span>  
  
### <a name="to-generate-a-sample-instance-message-for-a-schema"></a><span data-ttu-id="08c2b-116">產生結構描述的範例執行個體訊息</span><span class="sxs-lookup"><span data-stu-id="08c2b-116">To generate a sample instance message for a schema</span></span>  
  
1.  <span data-ttu-id="08c2b-117">在 方案總管 中，以滑鼠右鍵按一下您要產生執行個體訊息，然後按一下 結構的描述**產生執行個體**。</span><span class="sxs-lookup"><span data-stu-id="08c2b-117">In Solution Explorer, right-click the schema for which you want to generate an instance message, and then click **Generate Instance**.</span></span>  
  
2.  <span data-ttu-id="08c2b-118">在 [輸出] 視窗中檢視結果。</span><span class="sxs-lookup"><span data-stu-id="08c2b-118">In the Output window, view the results.</span></span> <span data-ttu-id="08c2b-119">成功和錯誤訊息會顯示在此視窗中。</span><span class="sxs-lookup"><span data-stu-id="08c2b-119">Success and error messages are displayed in this window.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="08c2b-120">若 [輸出] 視窗和/或 [工作清單] 視窗尚未開啟和顯示執行個體產生成功或失敗的資訊，您可以手動開啟它們。</span><span class="sxs-lookup"><span data-stu-id="08c2b-120">If the Output window and/or the Task List window did not open and display information about whether the instance generation succeeded or failed, you can open them manually.</span></span> <span data-ttu-id="08c2b-121">如需有關管理這些視窗的詳細資訊，請參閱[管理其他 Visual Studio 視窗](../core/how-to-manage-other-visual-studio-windows.md)。</span><span class="sxs-lookup"><span data-stu-id="08c2b-121">For more information about managing these windows, see [Managing Other Visual Studio Windows](../core/how-to-manage-other-visual-studio-windows.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="08c2b-122">如果您未指定的值**根參考**屬性，BizTalk 編輯器產生結構描述中的第一個根節點的範例執行個體訊息。</span><span class="sxs-lookup"><span data-stu-id="08c2b-122">If you do not specify a value for the **Root Reference** property, BizTalk Editor generates a sample instance message for the first root node in the schema.</span></span> <span data-ttu-id="08c2b-123">如果您指定的值**根參考**屬性，BizTalk 編輯器會產生範例執行個體訊息的根。</span><span class="sxs-lookup"><span data-stu-id="08c2b-123">If you specify a value for the **Root Reference** property, BizTalk Editor generates a sample instance message for that root.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="08c2b-124">在某些情況下，從特定結構描述產生的執行個體訊息，可能無法通過依據該相同結構描述進行的驗證。</span><span class="sxs-lookup"><span data-stu-id="08c2b-124">There are some cases instance messages generated from a particular schema may not pass validation with that same schema.</span></span> <span data-ttu-id="08c2b-125">如需這種情況下的詳細資訊，請參閱[已知問題與結構描述產生和驗證](../core/known-issues-with-schema-generation-and-validation.md)。</span><span class="sxs-lookup"><span data-stu-id="08c2b-125">For more information about such cases, see [Known Issues with Schema Generation and Validation](../core/known-issues-with-schema-generation-and-validation.md).</span></span> <span data-ttu-id="08c2b-126">一般而言，您會想要編輯產生的執行個體訊息並變更它所包含的資料，如此它就可以更真實地代表您的實例。</span><span class="sxs-lookup"><span data-stu-id="08c2b-126">Generally, you want to edit a generated instance message and change the data it contains so that it more realistically represents your scenario.</span></span> <span data-ttu-id="08c2b-127">然後再使用此變更過的執行個體訊息來驗證您的結構描述。</span><span class="sxs-lookup"><span data-stu-id="08c2b-127">Then use this modified instance message to validate your schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08c2b-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="08c2b-128">See Also</span></span>  
 <span data-ttu-id="08c2b-129">[測試結構描述](../core/testing-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="08c2b-129">[Testing Schemas](../core/testing-schemas.md) </span></span>  
 <span data-ttu-id="08c2b-130">[結構描述驗證](../core/schema-validation1.md) </span><span class="sxs-lookup"><span data-stu-id="08c2b-130">[Schema Validation](../core/schema-validation1.md) </span></span>  
 [<span data-ttu-id="08c2b-131">執行個體訊息產生和驗證</span><span class="sxs-lookup"><span data-stu-id="08c2b-131">Instance Message Generation and Validation</span></span>](../core/instance-message-generation-and-validation.md)