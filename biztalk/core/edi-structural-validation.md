---
title: "EDI 結構驗證 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 87086614-5616-441d-915c-2979c63c6e2f
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 505b9ac55eff0b6adb249d11788308f03902f1d5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="edi-structural-validation"></a><span data-ttu-id="abb5a-102">EDI 結構驗證</span><span class="sxs-lookup"><span data-stu-id="abb5a-102">EDI Structural Validation</span></span>
<span data-ttu-id="abb5a-103">X12 和 EDIFACT 編碼的 EDI 規格都針對 EDI 交換的結構定義了具體的規則和慣例。</span><span class="sxs-lookup"><span data-stu-id="abb5a-103">EDI specifications for both X12 and EDIFACT encoding define specific rules and conventions for the structure of EDI interchanges.</span></span> <span data-ttu-id="abb5a-104">EDIReceivePipeline 中的 EDI 解譯器會驗證每一則接收訊息的信封是否符合這些結構規則。</span><span class="sxs-lookup"><span data-stu-id="abb5a-104">The EDI Disassembler in the EDIReceivePipeline verifies that the envelope of each received message complies with these structural rules.</span></span> <span data-ttu-id="abb5a-105">EDISendPipeline 也會遵照這些規則來建置要傳送的每一則訊息，並在傳送之前驗證信封。</span><span class="sxs-lookup"><span data-stu-id="abb5a-105">The EDISendPipeline builds each message to be sent in accordance with these rules and validates the envelope before sending.</span></span>  
  
 <span data-ttu-id="abb5a-106">結構驗證可確保必要的標頭和結尾確實存在。</span><span class="sxs-lookup"><span data-stu-id="abb5a-106">The structural validation ensures that the required headers and trailers are present.</span></span> <span data-ttu-id="abb5a-107">結構完整性的檢查包括區段與迴圈排序與計數的檢查。</span><span class="sxs-lookup"><span data-stu-id="abb5a-107">The structural integrity checks include segment and loop ordering and count checks.</span></span> <span data-ttu-id="abb5a-108">這些檢查一定會執行，以確保文件能夠正確剖析或序列化。</span><span class="sxs-lookup"><span data-stu-id="abb5a-108">These checks are always performed to ensure that the document will parse or serialize correctly.</span></span> <span data-ttu-id="abb5a-109">這項驗證執行即使**EDI 類型驗證**及/或**擴充驗證**選項已停用。</span><span class="sxs-lookup"><span data-stu-id="abb5a-109">This validation is performed even if the **EDI Type Validation** and/or **Extended Validation** options are disabled.</span></span> <span data-ttu-id="abb5a-110">通過基本結構驗證的交換將遭擱置，即使**EDI 類型驗證**及/或**擴充驗證**選項已停用。</span><span class="sxs-lookup"><span data-stu-id="abb5a-110">An interchange that fails the basic structural validations will be suspended, even if the **EDI Type Validation** and/or **Extended Validation** options are disabled.</span></span>  
  
 <span data-ttu-id="abb5a-111">標頭和結尾內資料元素的值，以及標頭/結尾與資料元素分隔的方式，都是由協議決定。</span><span class="sxs-lookup"><span data-stu-id="abb5a-111">The values of the data elements within the headers and trailers, and how the headers/trailers and data elements are separated, are determined by the agreement.</span></span> <span data-ttu-id="abb5a-112">這些部分需透過結構描述驗證來進行驗證。</span><span class="sxs-lookup"><span data-stu-id="abb5a-112">These are validated through schema validation.</span></span>  
  
 <span data-ttu-id="abb5a-113">如需信封和內容標頭和結尾的每一組的詳細資訊，請參閱[EDI 訊息結構](../core/edi-message-structure.md)。</span><span class="sxs-lookup"><span data-stu-id="abb5a-113">For more information about the envelope and the contents within each set of headers and trailers, see [EDI Message Structure](../core/edi-message-structure.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abb5a-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="abb5a-114">See Also</span></span>  
 [<span data-ttu-id="abb5a-115">EDI 訊息驗證</span><span class="sxs-lookup"><span data-stu-id="abb5a-115">EDI Message Validation</span></span>](../core/edi-message-validation.md)