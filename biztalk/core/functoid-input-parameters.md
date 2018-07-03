---
title: 運算質輸入參數 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cca24f93-74a8-460c-b9ab-9aa2c767fe2f
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6a4a93d827a5f58401bb9b8fcdf9727c2a61767e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37008095"
---
# <a name="functoid-input-parameters"></a><span data-ttu-id="8dc26-102">運算質輸入參數</span><span class="sxs-lookup"><span data-stu-id="8dc26-102">Functoid Input Parameters</span></span>
<span data-ttu-id="8dc26-103">在您的對應中使用運算質的重要層面可能會正確設定運算質的輸入參數。</span><span class="sxs-lookup"><span data-stu-id="8dc26-103">A critical aspect of using functoids in your maps is properly configuring the input parameters to the functoid.</span></span> <span data-ttu-id="8dc26-104">雖然輸入參數的順序不重要的所有運算質 (例如**加法**運算質，它會顯示相同關聯預期從加法的屬性)，許多運算質必須有其輸入的參數指定正確的順序。</span><span class="sxs-lookup"><span data-stu-id="8dc26-104">While the order of input parameters is not critical for all functoids (such as the **Addition** functoid, which displays the same associate properties that one expects from addition), many functoids must have their input parameters specified in the correct order.</span></span>  
  
## <a name="create-input-paramaters"></a><span data-ttu-id="8dc26-105">建立輸入的參數</span><span class="sxs-lookup"><span data-stu-id="8dc26-105">Create input paramaters</span></span>
 <span data-ttu-id="8dc26-106">有兩種方式可以建立運算質的輸入參數：</span><span class="sxs-lookup"><span data-stu-id="8dc26-106">There are two ways that input parameters to a functoid can be created:</span></span>  
  
- <span data-ttu-id="8dc26-107">在所顯示之格線頁的運算質左邊建立連結。</span><span class="sxs-lookup"><span data-stu-id="8dc26-107">By creating links into the left side of a functoid in the displayed grid page.</span></span> <span data-ttu-id="8dc26-108">您用來建立連結的順序就是將關聯輸入參數傳遞給運算質的順序。</span><span class="sxs-lookup"><span data-stu-id="8dc26-108">The order in which you create the links is the order in which the associated input parameters are passed to the functoid.</span></span>  
  
- <span data-ttu-id="8dc26-109">藉由開啟**設定\<運算質\>運算質**對話方塊，並加入新的輸入參數。</span><span class="sxs-lookup"><span data-stu-id="8dc26-109">By opening the **Configure \<Functoid\> Functoid** dialog box and adding new input parameters.</span></span> <span data-ttu-id="8dc26-110">因為此對話方塊可讓您重新排序運算質的輸入參數，使其以正確的順序排列，所以此對話方塊也十分重要。</span><span class="sxs-lookup"><span data-stu-id="8dc26-110">This dialog box is also important because it allows you to reorder the input parameters to a functoid so that they are in the correct order.</span></span> <span data-ttu-id="8dc26-111">例如，如果您是以錯誤的順序建立運算質的連結，則可移至此對話方塊，並進行必要的修正。</span><span class="sxs-lookup"><span data-stu-id="8dc26-111">For example, if you create links to the functoid in the incorrect order, you can go to this dialog box and make the necessary corrections.</span></span> <span data-ttu-id="8dc26-112">如需設定運算質的輸入的參數的逐步指示，請參閱 <<c0> [ 如何設定運算質輸入參數](../core/how-to-configure-functoid-input-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="8dc26-112">For step-by-step instructions on configuring the input parameters for a functoid, see [How to Configure Functoid Input Parameters](../core/how-to-configure-functoid-input-parameters.md).</span></span>  
  
  <span data-ttu-id="8dc26-113">您必須使用**設定\<運算質\>運算質**對話方塊來建立本身為常數輸入的參數。</span><span class="sxs-lookup"><span data-stu-id="8dc26-113">You must use the **Configure \<Functoid\> Functoid** dialog box to create input parameters that are constants.</span></span>  
  
  <span data-ttu-id="8dc26-114">當您連結或運算質使用提供的標籤時**標籤**時選取連結或運算質中的 屬性 視窗中的屬性，該標籤會顯示在**設定\<運算質\>運算質** 對話方塊中，而非對應的結構描述 節點中，XPath 或做為輸入參數的運算質的名稱。</span><span class="sxs-lookup"><span data-stu-id="8dc26-114">When you provide a label for a link or functoid using the **Label** property in the Properties window when the link or functoid is selected, that label will be shown in the **Configure \<Functoid\> Functoid** dialog box rather than the corresponding XPath of a schema node, or the name of a functoid being used as an input parameter.</span></span> <span data-ttu-id="8dc26-115">有了標籤後，會比較容易分辨參數，並且可用正確順序排列參數。</span><span class="sxs-lookup"><span data-stu-id="8dc26-115">With labels, it will be much easier to tell which parameter is which, and to get them into the correct order.</span></span>  
  
  <span data-ttu-id="8dc26-116">可靠的運算質輸入參數的正確順序的詳細資訊，請參閱**運算質參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="8dc26-116">For definitive information about the correct order of functoid input parameters, see the **Functoid Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
## <a name="see-also"></a><span data-ttu-id="8dc26-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8dc26-117">See Also</span></span>  
 <span data-ttu-id="8dc26-118">[設定運算質輸入參數](../core/how-to-configure-functoid-input-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="8dc26-118">[Configure Functoid Input Parameters](../core/how-to-configure-functoid-input-parameters.md) </span></span>  
 <span data-ttu-id="8dc26-119">[設定指令碼處理運算質](../core/how-to-configure-the-scripting-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="8dc26-119">[Configure the Scripting Functoid](../core/how-to-configure-the-scripting-functoid.md) </span></span>  
 [<span data-ttu-id="8dc26-120">設定表格迴圈和表格擷取程式運算質</span><span class="sxs-lookup"><span data-stu-id="8dc26-120">Configure the Table Looping and Table Extractor Functoids</span></span>](../core/how-to-configure-the-table-looping-and-table-extractor-functoids.md)