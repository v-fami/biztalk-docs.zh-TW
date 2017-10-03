---
title: "以位元組為單位計算位置 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5cf666ec-d15e-4d2d-9df9-49189f352c65
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c3cdb7bbf1f0d6af04f0cc28ed1bdb7477b259de
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="position-counting-in-bytes"></a><span data-ttu-id="d9441-102">以位元組為單位計算位置</span><span class="sxs-lookup"><span data-stu-id="d9441-102">Position Counting in Bytes</span></span>

## <a name="overview"></a><span data-ttu-id="d9441-103">概觀</span><span class="sxs-lookup"><span data-stu-id="d9441-103">Overview</span></span>

<span data-ttu-id="d9441-104">您可以使用**Count Positions In Bytes**屬性**結構描述**節點：</span><span class="sxs-lookup"><span data-stu-id="d9441-104">You can use the **Count Positions In Bytes** property of the **Schema** node to:</span></span> 

* <span data-ttu-id="d9441-105">指定如何值 輸入**Positional Length**和**Positional Offset**解譯序數記錄中各個欄位的屬性</span><span class="sxs-lookup"><span data-stu-id="d9441-105">Specify how the values you enter for the **Positional Length** and **Positional Offset** properties of the various fields within positional records are interpreted</span></span>
* <span data-ttu-id="d9441-106">指定如何值 輸入**標記位移**解譯序數記錄其本身的屬性</span><span class="sxs-lookup"><span data-stu-id="d9441-106">Specify how the values you enter for the **Tag Offset** property of the positional records themselves are interpreted</span></span>

<span data-ttu-id="d9441-107">根據預設，這些值會解譯為字元的數目。</span><span class="sxs-lookup"><span data-stu-id="d9441-107">By default, these values are interpreted as a number of characters.</span></span> <span data-ttu-id="d9441-108">但是當**Count Positions In Bytes**屬性設定為**True**，這些值會解譯為位元組數目。</span><span class="sxs-lookup"><span data-stu-id="d9441-108">But when the **Count Positions In Bytes** property is set to **True**, these values are interpreted as a number of bytes.</span></span>  
  
 <span data-ttu-id="d9441-109">設定**Count Positions In Bytes**屬性**True**可能需要處理多位元組字元時設定 （MBCS 或 DBCS） 資料，或當一般檔案訊息肇因於 SAP、 大型主機，或其他的系統，可能會計算以位元組為單位的位置。</span><span class="sxs-lookup"><span data-stu-id="d9441-109">Setting the **Count Positions In Bytes** property to **True** might be necessary when dealing with multibyte character set (MBCS or DBCS) data, or when your flat file messages originate in SAP, mainframes, or other systems that may count positions in bytes.</span></span>  
  
 <span data-ttu-id="d9441-110">計算欄位長度，以位元組為單位可能很複雜，用來編碼字元的位元組數目是變數，以及可能會導致一些問題，相對於判斷欄位界限時。</span><span class="sxs-lookup"><span data-stu-id="d9441-110">Counting field lengths in bytes can be complicated when the number of bytes used to encode characters is variable, and can result in some issues with respect to determining field boundaries.</span></span> <span data-ttu-id="d9441-111">當一般檔案解譯器在這種狀況下剖析一般檔案時，會嘗試以其所瞭解之使用中的字元編碼為基礎進行適當的剖析決策。</span><span class="sxs-lookup"><span data-stu-id="d9441-111">When the flat file disassembler parses a flat file in such situations, it attempts to make appropriate parsing decisions based on its knowledge of the character encoding in use.</span></span>  
  
 <span data-ttu-id="d9441-112">這類剖析決策的範例與 MBCS 字元編碼中的前導位元有關。</span><span class="sxs-lookup"><span data-stu-id="d9441-112">An example of this type of parsing decision concerns lead bytes in MBCS character encodings.</span></span> <span data-ttu-id="d9441-113">前導位元為熟知的位元組值，可用來開始多位元組字元編碼，但它不可單獨發生。</span><span class="sxs-lookup"><span data-stu-id="d9441-113">Lead bytes are well-known byte values that are used to begin multibyte character encodings, and which should never occur on their own.</span></span> <span data-ttu-id="d9441-114">當使用位元組而不是以字元來指定欄位長度時，可能發生欄位中的最後一個位元組為前導位元，因而不能由其本身組成整個字元的狀況。</span><span class="sxs-lookup"><span data-stu-id="d9441-114">When specifying the length of the fields using bytes rather than character, situations may arise in which the last byte in a field is found to be a lead byte, which cannot constitute an entire character on its own.</span></span> <span data-ttu-id="d9441-115">在此情況下，一般檔案解譯器會將在前導位元之前發生的字元視為前一個欄位中的最後一個字元，並開始剖析以前導位元開始的下一個欄位。</span><span class="sxs-lookup"><span data-stu-id="d9441-115">In such cases, the flat file disassembler will treat the character occurring just prior to the lead byte as the last character in the previous field, and begin parsing the next field starting with the lead byte.</span></span>  

<span data-ttu-id="d9441-116">這些屬性的詳細[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="d9441-116">More details on these properties [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="d9441-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d9441-117">See Also</span></span>  
 [<span data-ttu-id="d9441-118">位置記錄的考量</span><span class="sxs-lookup"><span data-stu-id="d9441-118">Positional Record Considerations</span></span>](../core/positional-record-considerations.md)   
