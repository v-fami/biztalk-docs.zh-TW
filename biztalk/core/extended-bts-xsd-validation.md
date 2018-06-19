---
title: 擴充 (BTS-XSD) 驗證 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f225115d-8890-4149-8e46-d1bc8af17e62
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ed147515b48a23c55e552710d6a76d6df981edd7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22245950"
---
# <a name="extended-bts-xsd-validation"></a><span data-ttu-id="0133b-102">擴充 (BTS-XSD) 驗證</span><span class="sxs-lookup"><span data-stu-id="0133b-102">Extended (BTS-XSD) Validation</span></span>
<span data-ttu-id="0133b-103">唯有當結構描述已經自訂了資料型別不同於 EDI 資料型別的元素時，EDI 接收管線和 EDI 傳送管線才會執行擴充驗證。</span><span class="sxs-lookup"><span data-stu-id="0133b-103">The EDI receive pipeline and EDI send pipeline perform extended validation only if the schema has been customized with elements whose data type is not an EDI data type.</span></span> <span data-ttu-id="0133b-104">這些加入的元素不會由 EDI 驗證方法予以驗證，所以會納入擴充驗證範圍。</span><span class="sxs-lookup"><span data-stu-id="0133b-104">These added elements would not be validated by EDI validation, so will be covered by extended validation.</span></span> <span data-ttu-id="0133b-105">擴充驗證會使用 `System.Xml.XmlValidatingReader`，並會包括可在標準 XSD 中定義的所有檢查。</span><span class="sxs-lookup"><span data-stu-id="0133b-105">Extended validation uses `System.Xml.XmlValidatingReader` and includes all checks that can be defined in a standard XSD.</span></span>  
  
 <span data-ttu-id="0133b-106">您可以為與某個合作對象往返的所有訊息設定擴充驗證。</span><span class="sxs-lookup"><span data-stu-id="0133b-106">You configure extended validation for all messages to or from a party.</span></span> <span data-ttu-id="0133b-107">這麼做即可**擴充驗證**中的核取方塊**驗證**頁面 (下**交易集設定**> 一節針對 X12 或 EDIFACT) 上在單向協議索引標籤**協議屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0133b-107">You do so by selecting the **Extended Validation** checkbox in the **Validation** page (under the **Transaction Set Settings** section for either X12 or EDIFACT), on the one-way agreement tab in the **Agreement Properties** dialog box.</span></span> <span data-ttu-id="0133b-108">您可以啟用擴充驗證而不需要啟用 EDI 驗證，或者反之亦然。</span><span class="sxs-lookup"><span data-stu-id="0133b-108">You can enable extension validation without enabling EDI validation, or vice versa.</span></span>  
  
 <span data-ttu-id="0133b-109">擴充驗證是由下列檢查所組成：</span><span class="sxs-lookup"><span data-stu-id="0133b-109">Extended validation consists of the following checks:</span></span>  
  
-   <span data-ttu-id="0133b-110">資料元素需求和允許的重複</span><span class="sxs-lookup"><span data-stu-id="0133b-110">Data element requirement and allowed repetition</span></span>  
  
-   <span data-ttu-id="0133b-111">列舉型別</span><span class="sxs-lookup"><span data-stu-id="0133b-111">Enumerations</span></span>  
  
-   <span data-ttu-id="0133b-112">資料元素長度驗證 (最小/最大)</span><span class="sxs-lookup"><span data-stu-id="0133b-112">Data element length validation (min/max).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0133b-113">不支援延伸的驗證，EDI 傳送端批次訊息。</span><span class="sxs-lookup"><span data-stu-id="0133b-113">Extended Validation for batched messages on the EDI send side is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0133b-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0133b-114">See Also</span></span>  
 [<span data-ttu-id="0133b-115">EDI 訊息驗證</span><span class="sxs-lookup"><span data-stu-id="0133b-115">EDI Message Validation</span></span>](../core/edi-message-validation.md)