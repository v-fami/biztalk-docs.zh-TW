---
title: 分隔符號的已知的問題 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- known issues, delimiters
- delimiters
ms.assetid: 4eaacb3c-9d8d-43da-91dd-8bb25dec70e1
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6de686d136d0158315dfd00eba9690b8ffcbdccc
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36985647"
---
# <a name="delimiters-known-issues"></a><span data-ttu-id="51f0b-102">分隔符號的已知的問題</span><span class="sxs-lookup"><span data-stu-id="51f0b-102">Delimiters Known Issues</span></span>
<span data-ttu-id="51f0b-103">本節包含可協助您避免分隔符號錯誤的有用資訊。</span><span class="sxs-lookup"><span data-stu-id="51f0b-103">This section contains useful information that may help you avoid delimiter errors.</span></span>  
  
## <a name="characters-not-recommended-to-be-used-as-delimiters"></a><span data-ttu-id="51f0b-104">不建議用於做為分隔符號的字元</span><span class="sxs-lookup"><span data-stu-id="51f0b-104">Characters not recommended to be used as delimiters</span></span>  
 <span data-ttu-id="51f0b-105">它會建議您不要使用下列字元加做為分隔符號中，因為它們可能會造成錯誤：</span><span class="sxs-lookup"><span data-stu-id="51f0b-105">It is recommended that you do not use the following characters as delimiters as they might cause errors:</span></span>  
  
-   <span data-ttu-id="51f0b-106">Null 字元</span><span class="sxs-lookup"><span data-stu-id="51f0b-106">Null characters</span></span>  
  
-   <span data-ttu-id="51f0b-107">空格</span><span class="sxs-lookup"><span data-stu-id="51f0b-107">Spaces</span></span>  
  
## <a name="extra-delimiters-in-a-header-or-body-field-cause-multiple-errors"></a><span data-ttu-id="51f0b-108">中的標頭或主體欄位的額外分隔符號會造成多個錯誤</span><span class="sxs-lookup"><span data-stu-id="51f0b-108">Extra delimiters in a header or body field cause multiple errors</span></span>  
 <span data-ttu-id="51f0b-109">當您有額外的分隔符號 HL7 V2 中的欄位。訊息，Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 剖析器可能會產生兩個錯誤訊息，其中一個相關 XML 驗證，而其他與結構化驗證。</span><span class="sxs-lookup"><span data-stu-id="51f0b-109">When you have an extra delimiter in a field in an HL7 V2.X message, the Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) parser might generate two error messages, one related to XML validation and the other related to structural validation.</span></span>  
  
## <a name="trailing-delimiters-permitted-in-hl7-batch-segments"></a><span data-ttu-id="51f0b-110">HL7 批次區段中允許使用尾端分隔符號</span><span class="sxs-lookup"><span data-stu-id="51f0b-110">Trailing delimiters permitted in HL7 batch segments</span></span>  
 <span data-ttu-id="51f0b-111">HL7 定義批次區段例如 FHS、 BHS、 BTS 和 FTS 可以有尾端分隔符號，並不會受限於尾端分隔符號旗標，因為[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]不會驗證批次區段的尾端分隔符號。</span><span class="sxs-lookup"><span data-stu-id="51f0b-111">HL7 defined batch segments such as FHS, BHS, BTS, and FTS can have trailing delimiters and are not constrained by the trailing delimiter flag, because [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] does not validate trailing delimiters for batching segments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51f0b-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="51f0b-112">See Also</span></span>  
 [<span data-ttu-id="51f0b-113">已知問題</span><span class="sxs-lookup"><span data-stu-id="51f0b-113">Known Issues</span></span>](../../adapters-and-accelerators/accelerator-hl7/known-issues1.md)