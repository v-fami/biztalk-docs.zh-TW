---
title: 如何標示連結 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5fb81763-8b50-4334-88a8-efad1c5d82d9
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c0e47a776fdbc8eccbc1037b3c73b069d810eee0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22253790"
---
# <a name="how-to-label-a-link"></a><span data-ttu-id="23ed1-102">如何標示連結</span><span class="sxs-lookup"><span data-stu-id="23ed1-102">How to Label a Link</span></span>
<span data-ttu-id="23ed1-103">標籤有助於記錄對應中的運算質或連結用途。</span><span class="sxs-lookup"><span data-stu-id="23ed1-103">Labels are helpful to document the purpose of a functoid or a link in a map.</span></span> <span data-ttu-id="23ed1-104">您可以使用**標籤**屬性命名連結。</span><span class="sxs-lookup"><span data-stu-id="23ed1-104">You can use the **Label** property to name a link.</span></span> <span data-ttu-id="23ed1-105">當您的對應包含大型的結構描述結構，識別運算質的輸入和輸出連結變得困難時，標籤就很有用。</span><span class="sxs-lookup"><span data-stu-id="23ed1-105">This is useful when your map contains big schema structures and identifying the inputs and output links to a functoid becomes difficult.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="23ed1-106">如需標籤和註解的運算質的如何資訊，請參閱[如何加上標籤與註解的運算質](../core/how-to-label-and-comment-a-functoid.md)。</span><span class="sxs-lookup"><span data-stu-id="23ed1-106">For information on how to label and comment functoids, see [How to Label and Comment a Functoid](../core/how-to-label-and-comment-a-functoid.md).</span></span>  
  
 <span data-ttu-id="23ed1-107">下圖顯示連結標籤。</span><span class="sxs-lookup"><span data-stu-id="23ed1-107">The following figure shows a link label.</span></span>  
  
 <span data-ttu-id="23ed1-108">![標示連結](../core/media/new-labelling-link.gif "New_Labelling_link")</span><span class="sxs-lookup"><span data-stu-id="23ed1-108">![Labelling a link](../core/media/new-labelling-link.gif "New_Labelling_link")</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="23ed1-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="23ed1-109">Prerequisites</span></span>  
 <span data-ttu-id="23ed1-110">這些指示需要執行中的 BizTalk 對應工具。</span><span class="sxs-lookup"><span data-stu-id="23ed1-110">These instructions require that BizTalk Mapper is running.</span></span>  
  
### <a name="to-add-a-label-to-a-link"></a><span data-ttu-id="23ed1-111">新增連結的標籤</span><span class="sxs-lookup"><span data-stu-id="23ed1-111">To add a label to a link</span></span>  
  
1.  <span data-ttu-id="23ed1-112">選取您要加上標籤的連結。</span><span class="sxs-lookup"><span data-stu-id="23ed1-112">Select the link you want to label.</span></span>  
  
2.  <span data-ttu-id="23ed1-113">在**屬性**視窗中，提供新的名稱在**標籤**欄位。</span><span class="sxs-lookup"><span data-stu-id="23ed1-113">In the **Properties** window, provide the new name in the **Label** field.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="23ed1-114">允許的字元數目上限是 256。</span><span class="sxs-lookup"><span data-stu-id="23ed1-114">The maximum number of characters allowed is 256.</span></span> <span data-ttu-id="23ed1-115">如果指定超過 256 個字元的字串，則接受前 256 個字元，其餘部分會被捨棄。</span><span class="sxs-lookup"><span data-stu-id="23ed1-115">If a string with more than 256 characters is specified, the first 256 characters are accepted and the rest are discarded.</span></span>  
  
     <span data-ttu-id="23ed1-116">![連結標籤屬性](../core/media/new-to-label-link.gif "New_To_Label_Link")</span><span class="sxs-lookup"><span data-stu-id="23ed1-116">![Link label properties](../core/media/new-to-label-link.gif "New_To_Label_Link")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23ed1-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="23ed1-117">See Also</span></span>  
 [<span data-ttu-id="23ed1-118">使用連結指定記錄和欄位對應</span><span class="sxs-lookup"><span data-stu-id="23ed1-118">Using Links to Specify Record and Field Mappings</span></span>](../core/using-links-to-specify-record-and-field-mappings.md)