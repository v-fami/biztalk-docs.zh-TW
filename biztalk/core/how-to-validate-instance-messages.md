---
title: 如何驗證執行個體訊息 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9f6302c6-b56b-4572-aa76-0f4c4599672a
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bd0baa898f801c924cffc5a446aa1a22d063a8fc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22256790"
---
# <a name="how-to-validate-instance-messages"></a><span data-ttu-id="c3d5b-102">如何驗證執行個體訊息</span><span class="sxs-lookup"><span data-stu-id="c3d5b-102">How to Validate Instance Messages</span></span>
<span data-ttu-id="c3d5b-103">建構結構描述之後，您可以根據此結構描述，驗證您所知可正確代表這類執行個體訊息的已存在執行個體訊息，來檢查您的工作。</span><span class="sxs-lookup"><span data-stu-id="c3d5b-103">After you have constructed a schema, you can check your work by validating a pre-existing instance message that you know is a good representation of such instance messages against the schema.</span></span>  
  
 <span data-ttu-id="c3d5b-104">本主題提供此驗證工作的逐步說明。</span><span class="sxs-lookup"><span data-stu-id="c3d5b-104">This topic provides step-by-step instructions for this validation task.</span></span>  
  
### <a name="to-validate-an-instance-message-against-a-schema"></a><span data-ttu-id="c3d5b-105">依據結構描述驗證執行個體訊息</span><span class="sxs-lookup"><span data-stu-id="c3d5b-105">To validate an instance message against a schema</span></span>  
  
1.  <span data-ttu-id="c3d5b-106">在 方案總管 中，結構描述中，以滑鼠右鍵按一下，然後按一下 **屬性**。</span><span class="sxs-lookup"><span data-stu-id="c3d5b-106">In Solution Explorer, right-click the schema, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="c3d5b-107">如有必要，在 [屬性] 視窗中，依序展開**一般**區段**一般**索引標籤上，按一下其加號 （+） 圖示。</span><span class="sxs-lookup"><span data-stu-id="c3d5b-107">If necessary, in the Properties window, expand the **General** section of the **General** tab by clicking its plus (+) icon.</span></span>  
  
3.  <span data-ttu-id="c3d5b-108">在**輸入執行個體檔案名稱**屬性值欄位中，輸入檔案名稱或使用省略符號 (**...**) 按鈕來瀏覽檔案包含執行個體訊息來進行驗證的結構描述，然後按一下 [值] 欄位右端**開啟**。</span><span class="sxs-lookup"><span data-stu-id="c3d5b-108">In the **Input Instance Filename** property value field, either type the name of a file or use the ellipsis (**...**) button at the right end of the value field to browse for a file that contains the instance message to be validated against the schema, and then click **Open**.</span></span>  
  
4.  <span data-ttu-id="c3d5b-109">在**方案總管 中**，結構描述名稱，以滑鼠右鍵按一下，然後按一下**驗證執行個體**。</span><span class="sxs-lookup"><span data-stu-id="c3d5b-109">In **Solution Explorer**, right-click the schema name, and then click **Validate Instance**.</span></span>  
  
5.  <span data-ttu-id="c3d5b-110">在 [輸出] 視窗中檢視結果。</span><span class="sxs-lookup"><span data-stu-id="c3d5b-110">In the Output window, view the results.</span></span> <span data-ttu-id="c3d5b-111">成功和錯誤訊息會顯示在此視窗中。</span><span class="sxs-lookup"><span data-stu-id="c3d5b-111">Success and error messages are displayed in this window.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c3d5b-112">在某些情況下，從特定結構描述產生的執行個體訊息，可能無法通過依據該相同結構描述進行的驗證。</span><span class="sxs-lookup"><span data-stu-id="c3d5b-112">There are some cases instance messages generated from a particular schema may not pass validation with that same schema.</span></span> <span data-ttu-id="c3d5b-113">如需這種情況下的詳細資訊，請參閱[已知問題與結構描述產生和驗證](../core/known-issues-with-schema-generation-and-validation.md)。</span><span class="sxs-lookup"><span data-stu-id="c3d5b-113">For more information about such cases, see [Known Issues with Schema Generation and Validation](../core/known-issues-with-schema-generation-and-validation.md).</span></span> <span data-ttu-id="c3d5b-114">通常，您會想要編輯產生的執行個體訊息和變更所含的資料，使其更能實際表現您的狀況。</span><span class="sxs-lookup"><span data-stu-id="c3d5b-114">Generally, you will want to edit a generated instance message and change the data it contains so that it more realistically represents your scenario.</span></span> <span data-ttu-id="c3d5b-115">然後再使用此變更過的執行個體訊息來驗證您的結構描述。</span><span class="sxs-lookup"><span data-stu-id="c3d5b-115">Then use this modified instance message to validate your schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3d5b-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c3d5b-116">See Also</span></span>  
 <span data-ttu-id="c3d5b-117">[測試結構描述](../core/testing-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="c3d5b-117">[Testing Schemas](../core/testing-schemas.md) </span></span>  
 <span data-ttu-id="c3d5b-118">[結構描述驗證](../core/schema-validation1.md) </span><span class="sxs-lookup"><span data-stu-id="c3d5b-118">[Schema Validation](../core/schema-validation1.md) </span></span>  
 [<span data-ttu-id="c3d5b-119">執行個體訊息產生和驗證</span><span class="sxs-lookup"><span data-stu-id="c3d5b-119">Instance Message Generation and Validation</span></span>](../core/instance-message-generation-and-validation.md)