---
title: "處理標記位置記錄中 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7c85d695-6dc9-4200-a453-dc576832adca
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 804647b3cf43b9b6747b2e5f50e05e38313b03d9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="tag-handling-in-positional-records"></a><span data-ttu-id="aa08e-102">位置記錄中處理標記</span><span class="sxs-lookup"><span data-stu-id="aa08e-102">Tag Handling in Positional Records</span></span>

## <a name="overview"></a><span data-ttu-id="aa08e-103">概觀</span><span class="sxs-lookup"><span data-stu-id="aa08e-103">Overview</span></span>
<span data-ttu-id="aa08e-104">位置記錄可包含熟知的字元順序 (稱為標記)，可用來區別記錄中的不同類型。</span><span class="sxs-lookup"><span data-stu-id="aa08e-104">Positional records can include a well-known sequence of characters, known as a tag, which can be used to disambiguate one type of record from another.</span></span> <span data-ttu-id="aa08e-105">這可讓一般檔案解譯器適當地識別適當**記錄**包含正確剖析一般檔案記錄所需的資訊的結構描述中節點。</span><span class="sxs-lookup"><span data-stu-id="aa08e-105">This allows the flat file disassembler to properly identify the appropriate **Record** node in the schema that contains the information required to correctly parse the flat file record.</span></span>  
  
 <span data-ttu-id="aa08e-106">您可以使用**[標記識別項**和**標記位移**一起指定標記和其位置在位置記錄中的屬性。</span><span class="sxs-lookup"><span data-stu-id="aa08e-106">You can use the **[Tag Identifier** and **Tag Offset** properties together to specify the tag and its position within a positional record.</span></span> <span data-ttu-id="aa08e-107">請注意，這可以讓標記取決於您設定的任何位置出現在位置記錄， **Positional Length**和**Positional Offset**內各個欄位的屬性記錄中，標記可解譯為與其中一個相關聯的資料的一部分，或多個這些欄位。</span><span class="sxs-lookup"><span data-stu-id="aa08e-107">Note that this allows the tag to occur anywhere within the positional record and that depending on your settings for the **Positional Length** and **Positional Offset** properties of the various fields within the record, the tag can be interpreted as part of data associated with one or more of these fields.</span></span>  
  
 <span data-ttu-id="aa08e-108">**Positional Offset**屬性也可讓您將標記分開從記錄中的資料。</span><span class="sxs-lookup"><span data-stu-id="aa08e-108">The **Positional Offset** property also allows you to treat the tag separately from the data in the record.</span></span> <span data-ttu-id="aa08e-109">例如，如果標記就會發生在記錄開頭且四個字元的長度，您可以設定的值**Positional Offset**到四個，進而有效地略過記錄中的第一個欄位的屬性位置記錄標記時記錄的對等的 XML 格式轉譯的第一個欄位的值。</span><span class="sxs-lookup"><span data-stu-id="aa08e-109">For example, if the tag occurs at the beginning of the record and is four characters in length, you could set the value of the **Positional Offset** property of the first field in the record to four, thereby effectively skipping over the positional record tag when the value of the first field is translated in the equivalent XML format of the record.</span></span>  

<span data-ttu-id="aa08e-110">這些屬性的詳細[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="aa08e-110">More details on these properties [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="aa08e-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aa08e-111">See Also</span></span>  
 [<span data-ttu-id="aa08e-112">位置記錄的考量</span><span class="sxs-lookup"><span data-stu-id="aa08e-112">Positional Record Considerations</span></span>](../core/positional-record-considerations.md)   
