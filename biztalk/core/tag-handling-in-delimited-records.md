---
title: "分隔記錄中標記處理 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 568eb804-bea5-46d4-8547-8bc30b87156c
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5be9d28e3de6b1a7613db8d0c5ac7365a298a679
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="tag-handling-in-delimited-records"></a><span data-ttu-id="20a23-102">分隔記錄中處理標記</span><span class="sxs-lookup"><span data-stu-id="20a23-102">Tag Handling in Delimited Records</span></span>

## <a name="overview"></a><span data-ttu-id="20a23-103">概觀</span><span class="sxs-lookup"><span data-stu-id="20a23-103">Overview</span></span>
<span data-ttu-id="20a23-104">分隔記錄可包含熟知的字元順序 (稱為標記)，可用來區別記錄中的不同類型。</span><span class="sxs-lookup"><span data-stu-id="20a23-104">Delimited records can include a well-known sequence of characters, known as a tag, which can be used to disambiguate one type of record from another.</span></span> <span data-ttu-id="20a23-105">這可讓一般檔案解譯器適當地識別適當**記錄**包含正確剖析一般檔案記錄所需的資訊的結構描述中節點。</span><span class="sxs-lookup"><span data-stu-id="20a23-105">This will allow the flat file disassembler to properly identify the appropriate **Record** node in the schema that contains the information required to correctly parse the flat file record.</span></span>  
  
 <span data-ttu-id="20a23-106">您可以使用**標記識別項**屬性，以指定分隔記錄中的標記。</span><span class="sxs-lookup"><span data-stu-id="20a23-106">You can use the **Tag Identifier** property to specify the tag within a delimited record.</span></span> <span data-ttu-id="20a23-107">與位置記錄中的標記不同，分隔記錄中的標記必須出現在分隔記錄的開頭，且在記錄轉譯為對等的 XML 格式時，自動排除在資料外。</span><span class="sxs-lookup"><span data-stu-id="20a23-107">Unlike tags in positional records, tags in delimited records must occur at the beginning of the delimited record and are automatically never included in the data when the record is translated to its equivalent XML format.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20a23-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="20a23-108">See Also</span></span>  
-  [<span data-ttu-id="20a23-109">分隔記錄的考量</span><span class="sxs-lookup"><span data-stu-id="20a23-109">Delimited Record Considerations</span></span>](../core/delimited-record-considerations.md)   
-  <span data-ttu-id="20a23-110">**標記識別項 （一般檔案結構描述中的節點屬性）**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="20a23-110">**Tag Identifier (Node Property of Flat File Schemas)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>