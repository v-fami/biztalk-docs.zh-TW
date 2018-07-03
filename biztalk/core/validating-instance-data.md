---
title: 驗證執行個體資料 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 19c3ca83-0abf-42ba-8e29-653ff12d5e20
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 939c13c246aaed7db40b723845d6f0a7b95817bd
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37007151"
---
# <a name="validate-instance-data"></a><span data-ttu-id="36a44-102">驗證執行個體資料</span><span class="sxs-lookup"><span data-stu-id="36a44-102">Validate Instance Data</span></span>

## <a name="overview"></a><span data-ttu-id="36a44-103">概觀</span><span class="sxs-lookup"><span data-stu-id="36a44-103">Overview</span></span>
<span data-ttu-id="36a44-104">在測試對應程序期間，您可能想要針對來源與目的結構描述驗證執行個體資料，以確認執行個體資料符合結構描述的結構。</span><span class="sxs-lookup"><span data-stu-id="36a44-104">During the process of testing a map, you may want to validate instance data against the source and destination schemas to verify that the instance data adheres to the schema structure.</span></span> <span data-ttu-id="36a44-105">若要驗證對來源或目的結構描述的執行個體訊息，以滑鼠右鍵按一下 方案總管 中的結構描述，然後按一下 **驗證執行個體**。</span><span class="sxs-lookup"><span data-stu-id="36a44-105">To validate an instance message against the source or destination schema, right-click the schema in the Solution Explorer, and then click **Validate Instance**.</span></span>  

> [!IMPORTANT]
>  <span data-ttu-id="36a44-106">若您在輸出中使用自訂資料或常數，則必須確認來源測試資料和目標常數值的資料型別是否有效。</span><span class="sxs-lookup"><span data-stu-id="36a44-106">If you use custom data or constants in your output, you must verify that the data types of your source test data and target constant values are valid.</span></span> <span data-ttu-id="36a44-107">當您驗證對應時，「BizTalk 對應工具」並不會檢查執行個體資料是否違反結構描述所定義的任何資料型別。</span><span class="sxs-lookup"><span data-stu-id="36a44-107">When you validate a map, BizTalk Mapper does not check whether or not the instance data violates any data types defined by the schemas.</span></span> <span data-ttu-id="36a44-108">在您測試對應或驗證執行個體資料時，已完成此項檢查。</span><span class="sxs-lookup"><span data-stu-id="36a44-108">This is done when you test the map or validate the instance data.</span></span>  

 <span data-ttu-id="36a44-109">如需如何產生和驗證使用 BizTalk 編輯器的執行個體資料的詳細資訊，請參閱[執行個體訊息產生和驗證](../core/instance-message-generation-and-validation.md)並[執行個體驗證](../core/instance-validation.md)。</span><span class="sxs-lookup"><span data-stu-id="36a44-109">For more information about how to generate and validate instance data by using BizTalk Editor, see [Instance Message Generation and Validation](../core/instance-message-generation-and-validation.md) and [Instance Validation](../core/instance-validation.md).</span></span> <span data-ttu-id="36a44-110">執行個體時提供 SQL Server 登入。</span><span class="sxs-lookup"><span data-stu-id="36a44-110">.</span></span> <span data-ttu-id="36a44-111">**值**結構描述的節點屬性也會影響 BizTalk 產生執行個體資料的方式。</span><span class="sxs-lookup"><span data-stu-id="36a44-111">The **Value** property of the node of a schema also affects how BizTalk generates instance data.</span></span> <span data-ttu-id="36a44-112">如需詳細資訊，請參閱 <<c0>  **結構描述節點屬性** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="36a44-112">For more information, see the **Schema Node Properties** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>

## <a name="see-also"></a><span data-ttu-id="36a44-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="36a44-113">See Also</span></span>  
- [<span data-ttu-id="36a44-114">產生和驗證執行個體訊息</span><span class="sxs-lookup"><span data-stu-id="36a44-114">Instance Message Generation and Validation</span></span>](../core/instance-message-generation-and-validation.md)   
- [<span data-ttu-id="36a44-115">如何驗證在 Visual Studio 中的結構描述</span><span class="sxs-lookup"><span data-stu-id="36a44-115">How to Validate Schemas in Visual Studio</span></span>](../core/how-to-validate-schemas-in-visual-studio.md)   
- <span data-ttu-id="36a44-116">**對應屬性參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="36a44-116">**Map Property Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>  
- [<span data-ttu-id="36a44-117">測試對應</span><span class="sxs-lookup"><span data-stu-id="36a44-117">Testing Maps</span></span>](../core/testing-maps.md)
