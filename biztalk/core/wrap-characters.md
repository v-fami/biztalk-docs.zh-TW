---
title: 換行字元 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d7268f46-9bf6-4c76-9b3a-b4ee0e8db997
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b7d88c412c94505600443d351a150b6ca8a6876a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36996591"
---
# <a name="wrap-characters"></a><span data-ttu-id="1e603-102">換行字元</span><span class="sxs-lookup"><span data-stu-id="1e603-102">Wrap Characters</span></span>

## <a name="overview"></a><span data-ttu-id="1e603-103">概觀</span><span class="sxs-lookup"><span data-stu-id="1e603-103">Overview</span></span>
<span data-ttu-id="1e603-104">換行字元是在欄位中用來將資料字元換行的單一字元，目的在於抑制任何資料字元可能另外具有的特殊意義。</span><span class="sxs-lookup"><span data-stu-id="1e603-104">A wrap character is a single character that is used to wrap the data characters in a field for the purpose of suppressing any special meaning that any of those data characters would otherwise have.</span></span> <span data-ttu-id="1e603-105">例如，若您定義一般檔案記錄為具備下列特性：</span><span class="sxs-lookup"><span data-stu-id="1e603-105">For example, if you define a flat file record as having the following characteristics:</span></span>  
  
- <span data-ttu-id="1e603-106">名稱 = Record1</span><span class="sxs-lookup"><span data-stu-id="1e603-106">Name = Record1</span></span>  
  
- <span data-ttu-id="1e603-107">使用分隔符號</span><span class="sxs-lookup"><span data-stu-id="1e603-107">Delimited</span></span>  
  
- <span data-ttu-id="1e603-108">子分隔符號 = 逗號字元 (,)</span><span class="sxs-lookup"><span data-stu-id="1e603-108">Child delimiter = comma character (,)</span></span>  
  
- <span data-ttu-id="1e603-109">Child order = infix</span><span class="sxs-lookup"><span data-stu-id="1e603-109">Child order = infix</span></span>  
  
- <span data-ttu-id="1e603-110">逸出字元 = 反斜線字元 (\\)</span><span class="sxs-lookup"><span data-stu-id="1e603-110">Escape character = backslash character (\\)</span></span>  
  
- <span data-ttu-id="1e603-111">標記 = RECORD1</span><span class="sxs-lookup"><span data-stu-id="1e603-111">Tag = RECORD1</span></span>  
  
- <span data-ttu-id="1e603-112">三個名為 Field1、Field2 及 Field3 的欄位，每個都已定義為使用數字符號字元 (#) 做為其換行字元。</span><span class="sxs-lookup"><span data-stu-id="1e603-112">Three fields named Field1, Field2, and Field3, each defined to use the number sign character (#) as their wrap character.</span></span>  
  
  <span data-ttu-id="1e603-113">然後，下列一般檔案資料要求取得記錄。</span><span class="sxs-lookup"><span data-stu-id="1e603-113">Then the following flat file data applies for the record.</span></span>  
  
```  
RECORD1#field1#,#field2#,#field3#  
  
```  
  
 <span data-ttu-id="1e603-114">資料會解譯為下列 XML 分割。</span><span class="sxs-lookup"><span data-stu-id="1e603-114">The data is disassembled into the following fragment of XML.</span></span>  
  
```  
<Record1>  
    <Field1></Field1>  
    <Field2></Field2>  
    <Field3></Field3>  
</Record1>  
  
```  
  
 <span data-ttu-id="1e603-115">請注意，包圍在粗體資料字元 field1、field2 及 field3 的換行字元 (#) 已移除。</span><span class="sxs-lookup"><span data-stu-id="1e603-115">Note that the wrap characters (#) surrounding the bolded data characters field1, field2, and field3 have been removed.</span></span>  
  
 <span data-ttu-id="1e603-116">當一般檔案組合器執行反向作業時，將記錄的 XML 版本轉換為其相等的一般檔案記錄時，插入之前和之後的每個欄位，產生的原始順序的資料字元換行字元一般檔案字元。</span><span class="sxs-lookup"><span data-stu-id="1e603-116">When the flat file assembler performs the reverse operation, converting the XML version of the record to its equivalent flat file record, the wrap characters are inserted before and after the data characters of each of the fields, yielding the original sequence of flat file characters.</span></span>  
  
 <span data-ttu-id="1e603-117">定義的逸出字元可與定義的換行字元搭配使用。</span><span class="sxs-lookup"><span data-stu-id="1e603-117">The defined escape character can be used in conjunction with the defined wrap character.</span></span> <span data-ttu-id="1e603-118">例如，假設 Field1 的值已變更，如下所示 (以粗體顯示)。</span><span class="sxs-lookup"><span data-stu-id="1e603-118">For example, suppose the value of Field1 is changed as follows (shown in bold type).</span></span>  
  
```  
<Record1>  
    <Field1></Field1>  
    <Field2>field2</Field2>  
    <Field3>field3</Field3>  
</Record1>  
  
```  
  
 <span data-ttu-id="1e603-119">使用提供的記錄與欄位定義來組合此 XML 分割時，會產生一般檔案字元的下列順序 (逸出的數字符號字元順序會以粗體顯示)。</span><span class="sxs-lookup"><span data-stu-id="1e603-119">When this XML fragment is assembled, using the record and field definitions provided, the following sequence of flat file characters is produced (the escaped number sign character sequence is shown in bold type).</span></span>  
  
```  
RECORD1#field1#,#field2#,#field3#  
  
```  
  
 <span data-ttu-id="1e603-120">在建立時使用 「 BizTalk 編輯器的一般檔案結構描述，您可以定義整個結構描述使用的預設換行字元**預設換行字元**並**預設換行字元類型**屬性**結構描述**節點。</span><span class="sxs-lookup"><span data-stu-id="1e603-120">When creating a flat file schema using BizTalk Editor, you can define a default wrap character for the entire schema using the **Default Wrap Character** and **Default Wrap Character Type** properties of the **Schema** node.</span></span> <span data-ttu-id="1e603-121">然後，您可以設定為使用此預設換行字元或自訂的特定欄位的換行字元，使用結構描述中的每個個別的欄位**換行字元**並**Wrap Character Type**屬性**欄位項目**或是**Field 屬性**一般檔案結構描述中的節點。</span><span class="sxs-lookup"><span data-stu-id="1e603-121">Then, you can configure each individual field in the schema to either use this default wrap character or a custom, field-specific wrap character using the **Wrap Character** and **Wrap Character Type** properties of the **Field Element** or **Field Attribute** nodes in flat file schemas.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="1e603-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1e603-122">See Also</span></span>  
- [<span data-ttu-id="1e603-123">解譯特殊字元作為欄位值一部分的方式</span><span class="sxs-lookup"><span data-stu-id="1e603-123">Ways to Interpret Special Characters as Part of a Field Value</span></span>](../core/ways-to-interpret-special-characters-as-part-of-a-field-value.md)  
- <span data-ttu-id="1e603-124">換行字元屬性[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]:</span><span class="sxs-lookup"><span data-stu-id="1e603-124">Wrap character properties [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]:</span></span>  
    -  <span data-ttu-id="1e603-125">預設換行字元 （一般檔案結構描述的節點屬性</span><span class="sxs-lookup"><span data-stu-id="1e603-125">Default Wrap Character (Node Property of Flat File Schemas</span></span>
    -  <span data-ttu-id="1e603-126">預設換行字元類型 （一般檔案結構描述的節點屬性</span><span class="sxs-lookup"><span data-stu-id="1e603-126">Default Wrap Character Type (Node Property of Flat File Schemas</span></span>
    -  <span data-ttu-id="1e603-127">換行字元 （一般檔案結構描述的節點屬性</span><span class="sxs-lookup"><span data-stu-id="1e603-127">Wrap Character (Node Property of Flat File Schemas</span></span>  
    -  <span data-ttu-id="1e603-128">換行字元類型 （一般檔案結構描述的節點屬性</span><span class="sxs-lookup"><span data-stu-id="1e603-128">Wrap Character Type (Node Property of Flat File Schemas</span></span>