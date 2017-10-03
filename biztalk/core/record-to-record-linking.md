---
title: "記錄對記錄連結 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a3fa4d7-5689-4f55-af1b-369defa37037
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ac6abc3d27ad3ee2f135e3ff5c8c1749fcae5f4a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="record-to-record-linking"></a><span data-ttu-id="8f027-102">記錄對記錄連結</span><span class="sxs-lookup"><span data-stu-id="8f027-102">Record-to-Record Linking</span></span>

## <a name="overview"></a><span data-ttu-id="8f027-103">概觀</span><span class="sxs-lookup"><span data-stu-id="8f027-103">Overview</span></span>
<span data-ttu-id="8f027-104">在 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，您可以使用 BizTalk 對應工具來建立一次的來源和目的地結構描述的相似部分之間的多個連結。</span><span class="sxs-lookup"><span data-stu-id="8f027-104">In Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you can use BizTalk Mapper to create multiple links between similar portions of the source and destination schemas at the same time.</span></span> <span data-ttu-id="8f027-105">在舊版的 BizTalk Server 中，您必須一次一個個別地建立這類連結。</span><span class="sxs-lookup"><span data-stu-id="8f027-105">In previous versions of BizTalk Server, you had to create such links individually, one at a time.</span></span> <span data-ttu-id="8f027-106">記錄對記錄連結有兩種不同類型，根據所連結的來源與目的結構描述記錄的結構相似程度，每一種各適用於不同的實例，如下所示：</span><span class="sxs-lookup"><span data-stu-id="8f027-106">There are two distinct types of record-to-record linking, each appropriate to different scenarios based on the degree of similarity of the structures of the source and destination schema records being linked, as follows:</span></span>  
  
-   <span data-ttu-id="8f027-107">**結構連結。**</span><span class="sxs-lookup"><span data-stu-id="8f027-107">**Structure linking.**</span></span> <span data-ttu-id="8f027-108">當您的來源與目的結構描述中所連結的記錄結構完全相同或非常相似時，使用結構連結。</span><span class="sxs-lookup"><span data-stu-id="8f027-108">Use structure linking when the structure of the records being linked in your source and destination schemas are the same or very similar.</span></span>  
  
-   <span data-ttu-id="8f027-109">**名稱相符連結。**</span><span class="sxs-lookup"><span data-stu-id="8f027-109">**Name-matching linking.**</span></span> <span data-ttu-id="8f027-110">當您的來源與目的結構描述中所連結的記錄結構相似而且記錄與欄位名稱相符，但結構例外狀況多過於可使用的結構連結時，則使用名稱相符連結。</span><span class="sxs-lookup"><span data-stu-id="8f027-110">Use name-matching linking when the structure of the records being linked in your source and destination schemas are still similar, and with matching record and field names, but with more structural exceptions than are workable with structure linking.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8f027-111">記錄對記錄連結適用於值複製連結僅設定使用**來源連結**屬性。</span><span class="sxs-lookup"><span data-stu-id="8f027-111">Record-to-record linking applies to value-copy linking only, as configured using the **Source Links** property.</span></span>  
  
## <a name="record-to-record-linking-structure-links"></a><span data-ttu-id="8f027-112">記錄對記錄連結：結構連結</span><span class="sxs-lookup"><span data-stu-id="8f027-112">Record-to-Record Linking: Structure Links</span></span>  
 <span data-ttu-id="8f027-113">當您在來源與目的結構描述中所要連結的記錄結構完全相同或幾乎完全相同時，使用結構連結。</span><span class="sxs-lookup"><span data-stu-id="8f027-113">Use structure linking when the structure of the records that you want to link in your source and destination schemas is the same or almost exactly the same.</span></span>  
  
 <span data-ttu-id="8f027-114">若結構描述的結構完全相同，只需要在每個結構描述的根節點增加一個連結。</span><span class="sxs-lookup"><span data-stu-id="8f027-114">If the structure of your schemas is exactly the same, you need only add one link at the root node of each schema.</span></span> <span data-ttu-id="8f027-115">在捷徑功能表中，選取想要的連結模式。</span><span class="sxs-lookup"><span data-stu-id="8f027-115">In the shortcut menu, select the desired mode of linking.</span></span>  
  
 <span data-ttu-id="8f027-116">若結構描述中特定記錄的結構完全相同，只需要在每個結構描述中的那些記錄之間增加一個連結。</span><span class="sxs-lookup"><span data-stu-id="8f027-116">If the structure of particular records in your schemas is exactly the same, you need only add one link between those records in each schema.</span></span> <span data-ttu-id="8f027-117">在捷徑功能表中，選取想要的連結模式。</span><span class="sxs-lookup"><span data-stu-id="8f027-117">In the shortcut menu, select the desired mode of linking.</span></span>  
  
 <span data-ttu-id="8f027-118">有關如何設定記錄對記錄連結的使用結構連結，或按一下 名稱比對連結，請參閱[自動連結記錄](../core/how-to-link-records-automatically.md)。</span><span class="sxs-lookup"><span data-stu-id="8f027-118">For information about how to configure record-to-record linking as using either structure linking or name-matching linking, see [Link Records Automatically](../core/how-to-link-records-automatically.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8f027-119">結構連結為記錄對記錄連結的預設類型。</span><span class="sxs-lookup"><span data-stu-id="8f027-119">Structure links are the default type of record-to-record linking.</span></span>  
  
## <a name="record-to-record-linking-name-matching-links"></a><span data-ttu-id="8f027-120">記錄對記錄連結：名稱相符連結</span><span class="sxs-lookup"><span data-stu-id="8f027-120">Record-to-Record Linking: Name-Matching Links</span></span>  
 <span data-ttu-id="8f027-121">當您在來源與目的結構描述中所要連結的記錄結構十分相似，但不完全相同時，可使用名稱相符連結。</span><span class="sxs-lookup"><span data-stu-id="8f027-121">Use name-matching links when the structure of the records that you want to link in your source and destination schemas is very similar, but not exactly the same.</span></span> <span data-ttu-id="8f027-122">例如，在來源或目的結構描述中所要連結的節點內的附屬記錄或欄位，可能多過於另一個結構描述中的附屬記錄或欄位。</span><span class="sxs-lookup"><span data-stu-id="8f027-122">For example, the source or destination schema might have more subordinate records or fields within the nodes to be linked than in the other schema.</span></span>  
  
 <span data-ttu-id="8f027-123">若要在結構幾乎相符之來源與目的結構描述的部分之間建立名稱相符連結 (可能的話，包括整個結構描述)，請建立以某個子階層父節點為起點，並以另一個子階層父節點為終點的連結。</span><span class="sxs-lookup"><span data-stu-id="8f027-123">To create a name-matching link between portions of your source and destination schemas that have nearly matching structures, including the entire schemas where applicable, create a link originating from a sub-hierarchy parent node and ending on another sub-hierarchy parent node.</span></span> <span data-ttu-id="8f027-124">在捷徑功能表中，選取想要的模式。</span><span class="sxs-lookup"><span data-stu-id="8f027-124">In the shortcut menu, select the desired mode.</span></span> <span data-ttu-id="8f027-125">在連結節點之後，就會為來源與目的結構描述中，名稱相同且擁有相同子結構的所有附屬記錄與欄位自動建立連結。</span><span class="sxs-lookup"><span data-stu-id="8f027-125">After you link the nodes, links are automatically created for all of the subordinate records and fields in the source and destination schemas that are named the same and have the same substructure.</span></span>  
  
 <span data-ttu-id="8f027-126">有關如何設定記錄對記錄連結的使用結構連結，或按一下 名稱比對連結，請參閱[自動連結記錄](../core/how-to-link-records-automatically.md)。</span><span class="sxs-lookup"><span data-stu-id="8f027-126">For information about how to configure record-to-record linking as using either structure linking or name-matching linking, see [Link Records Automatically](../core/how-to-link-records-automatically.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f027-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8f027-127">See Also</span></span>  
 <span data-ttu-id="8f027-128">[自動連結記錄](../core/how-to-link-records-automatically.md) </span><span class="sxs-lookup"><span data-stu-id="8f027-128">[Link Records Automatically](../core/how-to-link-records-automatically.md) </span></span>  
 [<span data-ttu-id="8f027-129">編輯連結屬性</span><span class="sxs-lookup"><span data-stu-id="8f027-129">Edit Link Properties</span></span>](../core/how-to-edit-link-properties.md)