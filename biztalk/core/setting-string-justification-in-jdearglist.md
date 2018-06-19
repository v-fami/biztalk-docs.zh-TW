---
title: 在 JD Edwards OneWorld 配接器中設定字串左右對齊 |Microsoft 文件
description: 更新 jdearglist 檔案，以在 BizTalk Server 協調流程中使用 JD Edwards OneWorld 配接器
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1c9b013a-839d-45f1-9da0-c96fd45b25e5
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 70b32d0106d95a1970b480e32dfa47a81ebf98ca
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
ms.locfileid: "24012997"
---
# <a name="set-string-justification-in-jdearglist"></a><span data-ttu-id="2edda-103">在 Jdearglist 中設定字串左右對齊</span><span class="sxs-lookup"><span data-stu-id="2edda-103">Set string Justification in Jdearglist</span></span>

## <a name="overview"></a><span data-ttu-id="2edda-104">概觀</span><span class="sxs-lookup"><span data-stu-id="2edda-104">Overview</span></span>
<span data-ttu-id="2edda-105">若要在 JD Edwards OneWorld jdearglist.txt 檔案中，將一些字串引數設定為靠右對齊 (填補左方)，您必須知道所想要存取的商務功能，特別是您必須知道您想要呼叫商務功能中的哪一個欄位。</span><span class="sxs-lookup"><span data-stu-id="2edda-105">To configure certain string arguments as right-justified (and left padded) in the JD Edwards OneWorld jdearglist.txt file, you must know what business function you want to access; specifically, you must know which fields in the business function you want to call.</span></span>  
  
 <span data-ttu-id="2edda-106">您必須先更新 jdearglist.txt，然後才能在協調流程中產生繫結 (結構描述)。</span><span class="sxs-lookup"><span data-stu-id="2edda-106">You must update the jdearglist.txt before you generate the bindings (schemas) in the orchestration.</span></span> <span data-ttu-id="2edda-107">更新 jdearglist.txt 檔案的指示所述[處理字串值](../core/handling-string-values1.md)。</span><span class="sxs-lookup"><span data-stu-id="2edda-107">The instructions for updating the jdearglist.txt file are outlined in [Handling String Values](../core/handling-string-values1.md).</span></span>  
  
 <span data-ttu-id="2edda-108">如果您在稽核記錄中收到 jdearglist.txt 警告訊息，它是通知您找不到 jdearglist.txt。</span><span class="sxs-lookup"><span data-stu-id="2edda-108">If you receive a jdearglist.txt warning message in the audit log, it informs you that the jdearglist.txt is missing.</span></span> <span data-ttu-id="2edda-109">如果您執行 SalesOrder 或 PurchaseOrder 商務功能，您的 PATH 中必須要有此檔案，否則商務功能將無法運作。</span><span class="sxs-lookup"><span data-stu-id="2edda-109">If you run the SalesOrder or PurchaseOrder business functions, you must have the file in your PATH, or it will not work.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2edda-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2edda-110">See Also</span></span>  
[<span data-ttu-id="2edda-111">使用 BizTalk Server 例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="2edda-111">Use BizTalk Server Exception Handling</span></span>](using-biztalk-server-exception-handling1.md)