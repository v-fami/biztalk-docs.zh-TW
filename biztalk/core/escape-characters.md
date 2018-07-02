---
title: 逸出字元 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3af800b9-d31b-487a-9a06-6eda47d1574e
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5f6f1ff202c1ffa96bc696415ab7ec1024ae57e9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36970647"
---
# <a name="escape-characters"></a><span data-ttu-id="162dc-102">逸出字元</span><span class="sxs-lookup"><span data-stu-id="162dc-102">Escape Characters</span></span>

## <a name="overview"></a><span data-ttu-id="162dc-103">概觀</span><span class="sxs-lookup"><span data-stu-id="162dc-103">Overview</span></span>
<span data-ttu-id="162dc-104">逸出字元是隱藏其後任何特殊意義字元的單一字元。</span><span class="sxs-lookup"><span data-stu-id="162dc-104">An escape character is a single character that suppresses any special meaning of the character that follows it.</span></span> <span data-ttu-id="162dc-105">例如，若您定義一般檔案記錄為具備下列特性：</span><span class="sxs-lookup"><span data-stu-id="162dc-105">For example, if you define a flat file record as having the following characteristics:</span></span>  
  
- <span data-ttu-id="162dc-106">名稱 = Record1</span><span class="sxs-lookup"><span data-stu-id="162dc-106">Name = Record1</span></span>  
  
- <span data-ttu-id="162dc-107">使用分隔符號</span><span class="sxs-lookup"><span data-stu-id="162dc-107">Delimited</span></span>  
  
- <span data-ttu-id="162dc-108">子分隔符號 = 逗號字元 (,)</span><span class="sxs-lookup"><span data-stu-id="162dc-108">Child delimiter = comma character (,)</span></span>  
  
- <span data-ttu-id="162dc-109">子順序 = 前置詞</span><span class="sxs-lookup"><span data-stu-id="162dc-109">Child order = prefix</span></span>  
  
- <span data-ttu-id="162dc-110">逸出字元 = 反斜線字元 (\\)</span><span class="sxs-lookup"><span data-stu-id="162dc-110">Escape character = backslash character (\\)</span></span>  
  
- <span data-ttu-id="162dc-111">標記 = RECORD1</span><span class="sxs-lookup"><span data-stu-id="162dc-111">Tag = RECORD1</span></span>  
  
- <span data-ttu-id="162dc-112">兩個欄位分別名為 Field1 和 Field2</span><span class="sxs-lookup"><span data-stu-id="162dc-112">Two fields named Field1 and Field2</span></span>  
  
  <span data-ttu-id="162dc-113">然後，下列一般檔案資料要求取得記錄。</span><span class="sxs-lookup"><span data-stu-id="162dc-113">Then the following flat file data applies for the record.</span></span>  
  
```  
RECORD1,testfield1\,testfield1,testfield2  
                  ^^  
  
```  
  
 <span data-ttu-id="162dc-114">資料將解譯為下列 XML 分割。</span><span class="sxs-lookup"><span data-stu-id="162dc-114">The data will be disassembled into the following fragment of XML.</span></span>  
  
```  
<Record1>  
    <Field1>testfield1,testfield1</Field1>  
    <Field2>testfield2</Field2>  
</Record1>  
  
```  
  
 <span data-ttu-id="162dc-115">請注意，在一般檔案記錄之後一行中指出的逸出字元順序 `\,` 已經轉換為單一逗號字元，對等 XML 記錄的 Field1 資料中沒有逸出字元。</span><span class="sxs-lookup"><span data-stu-id="162dc-115">Note that the escape character sequence `\,` indicated on the line following the flat file record, has been converted to a single comma character without the escape character in the data for Field1 in the equivalent XML record.</span></span> <span data-ttu-id="162dc-116">此外，該逗號字元不會和另外兩個逗號一樣解譯為欄位分隔符號。</span><span class="sxs-lookup"><span data-stu-id="162dc-116">Furthermore, that comma character was not interpreted as a field delimiter like the other two commas are.</span></span>  
  
 <span data-ttu-id="162dc-117">當一般檔案組合器執行反向作業，將記錄的 XML 版本轉換為其對等的一般檔案記錄時，會將逸出字元插入 Field1 中間的逗號之前，以此表示應該將它解譯為資料，而不是欄位分隔符號。</span><span class="sxs-lookup"><span data-stu-id="162dc-117">When the flat file assembler performs the reverse operation, converting the XML version of the record to its equivalent flat file record, the escape character will be inserted before the comma in the middle of Field1, thereby indicating that it should be interpreted as data rather than as a field delimiter.</span></span>  
  
 <span data-ttu-id="162dc-118">在建立時使用 「 BizTalk 編輯器的一般檔案結構描述，您可以定義整個結構描述使用的預設逸出字元**預設逸出字元**並**預設逸出字元類型**屬性**結構描述**節點。</span><span class="sxs-lookup"><span data-stu-id="162dc-118">When creating a flat file schema using BizTalk Editor, you can define a default escape character for the entire schema using the **Default Escape Character** and **Default Escape Character Type** properties of the **Schema** node.</span></span> <span data-ttu-id="162dc-119">然後，您可以設定為使用此預設逸出字元或自訂的記錄特定的逸出字元使用的結構描述的每個個別的資料錄**逸出字元]** 和**逸出字元類型**的屬性**記錄**節點。</span><span class="sxs-lookup"><span data-stu-id="162dc-119">Then, you can configure each individual record in the schema to either use this default escape character or a custom, record-specific escape character using the **Escape Character]** and **Escape Character Type** properties of the **Record** node.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="162dc-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="162dc-120">See Also</span></span>  
- [<span data-ttu-id="162dc-121">解譯特殊字元作為欄位值一部分的方式</span><span class="sxs-lookup"><span data-stu-id="162dc-121">Ways to Interpret Special Characters as Part of a Field Value</span></span>](../core/ways-to-interpret-special-characters-as-part-of-a-field-value.md)  
- <span data-ttu-id="162dc-122">逸出字元屬性[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]:</span><span class="sxs-lookup"><span data-stu-id="162dc-122">Escape character properties  [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]:</span></span>  
    - <span data-ttu-id="162dc-123">預設逸出字元 （一般檔案結構描述中的節點屬性）</span><span class="sxs-lookup"><span data-stu-id="162dc-123">Default Escape Character (Node Property of Flat File Schemas)</span></span>
    - <span data-ttu-id="162dc-124">預設逸出字元類型 （一般檔案結構描述中的節點屬性）</span><span class="sxs-lookup"><span data-stu-id="162dc-124">Default Escape Character Type (Node Property of Flat File Schemas)</span></span>
    - <span data-ttu-id="162dc-125">逸出字元 （一般檔案結構描述中的節點屬性）</span><span class="sxs-lookup"><span data-stu-id="162dc-125">Escape Character (Node Property of Flat File Schemas)</span></span>  
    - <span data-ttu-id="162dc-126">逸出字元類型 （一般檔案結構描述中的節點屬性）</span><span class="sxs-lookup"><span data-stu-id="162dc-126">Escape Character Type (Node Property of Flat File Schemas)</span></span>