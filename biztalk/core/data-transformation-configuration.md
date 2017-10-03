---
title: "資料轉換組態 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XSLT
- maps, compiling
- Source Links property
- BizTalk Mapper, compiler directives
- code samples, XSLT
- compiler directives, copy text and subcontentent value
- compiler directives, copy text value
- maps, XSLT
- compiler directives, copy name
- compiler directives
- maps, code sample [XSLT]
- XSLT, code samples
ms.assetid: 05abe091-5202-4590-99ec-e60ca53a4324
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8304d43f59f63e474a3257915521d5dc36c38d30
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="data-transformation-configuration"></a><span data-ttu-id="a9647-102">資料轉換組態</span><span class="sxs-lookup"><span data-stu-id="a9647-102">Data Transformation Configuration</span></span>
<span data-ttu-id="a9647-103">從項目進行對應時，典型的可延伸樣式表語言轉換 (XSLT) 看起來如下。</span><span class="sxs-lookup"><span data-stu-id="a9647-103">When mapping from an element, a typical Extensible Stylesheet Language Transformations (XSLT) looks as follows.</span></span>  
  
```  
<xsl:attribute name='CatalogPurposeCode'>  
     <xsl:value-of select='BCT/BCT01/text()'/>  
</xsl:attribute>  
```  
  
 <span data-ttu-id="a9647-104">如果項目**BCT01**包含混合的內容，text （） 的使用讓您能夠存取第一個文字只到時間點的第一個子項目，如果有的話。</span><span class="sxs-lookup"><span data-stu-id="a9647-104">If the element **BCT01** contains mixed content, the use of text() makes it possible to access the first text only up to the point of the first subelement, if any.</span></span> <span data-ttu-id="a9647-105">若在此 XSLT 陳述式中未使用 text()，則結果會造成所有文字內容，加上任何子項目的文字內容，對應為一個文字字串。</span><span class="sxs-lookup"><span data-stu-id="a9647-105">If text() were not used in this XSLT statement, the result would be that all text content, plus any text content of subelements, would be mapped as one string of text.</span></span> <span data-ttu-id="a9647-106">設定**來源連結**屬性的連結，可讓您控制複製到目的結構描述所定義之結構的資料來源。</span><span class="sxs-lookup"><span data-stu-id="a9647-106">Configuring the **Source Links** property for a link allows you to control the source of the data that is copied into the structure defined by the destination schema.</span></span>  
  
 <span data-ttu-id="a9647-107">當您在顯示的格線頁中選取的連結時，其中一個屬性顯示在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]屬性 視窗是**來源連結**屬性。</span><span class="sxs-lookup"><span data-stu-id="a9647-107">When you select a link in the displayed grid page, one of the properties displayed in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window is the **Source Links** property.</span></span> <span data-ttu-id="a9647-108">您可以為對應中的每個連結選擇以下可能的值：</span><span class="sxs-lookup"><span data-stu-id="a9647-108">You can choose between the following possible values for each link in your map:</span></span>  
  
-   <span data-ttu-id="a9647-109">**複製文字值。**</span><span class="sxs-lookup"><span data-stu-id="a9647-109">**Copy text value.**</span></span> <span data-ttu-id="a9647-110">此為預設值。您可以使用此值以複製輸入執行個體訊息中的項目值或屬性值。</span><span class="sxs-lookup"><span data-stu-id="a9647-110">Use this value, which is the default, to copy the value of the element or attribute in the input instance message.</span></span> <span data-ttu-id="a9647-111">例如，若相關項目為 BoldExample，如下所示：</span><span class="sxs-lookup"><span data-stu-id="a9647-111">For example, if the relevant element is BoldExample, as follows:</span></span>  
  
    ```  
    <BoldExample>This is a <B>Bold Text</B> example.</BoldExample>  
    ```  
  
     <span data-ttu-id="a9647-112">複製到輸出執行個體訊息中相關項目或屬性的值為 "This is a"。</span><span class="sxs-lookup"><span data-stu-id="a9647-112">The value copied into the relevant element or attribute in the output instance message is "This is a ".</span></span> <span data-ttu-id="a9647-113">對於此類混合內容項目而言，此結果可能並非預期。</span><span class="sxs-lookup"><span data-stu-id="a9647-113">For mixed content elements like this, this result may not be what is desired.</span></span> <span data-ttu-id="a9647-114">但因為混合內容項目是相當罕見，**複製文字值**設定**來源連結**屬性應該是最適合在大部分情況下。</span><span class="sxs-lookup"><span data-stu-id="a9647-114">But because mixed content elements are relatively rare, the **Copy text value** setting for the **Source Links** property is probably appropriate in most cases.</span></span>  
  
-   <span data-ttu-id="a9647-115">**複製名稱。**</span><span class="sxs-lookup"><span data-stu-id="a9647-115">**Copy name.**</span></span> <span data-ttu-id="a9647-116">使用此值以複製輸入執行個體訊息中的節點名稱。</span><span class="sxs-lookup"><span data-stu-id="a9647-116">Use this value to copy the name of the node in the input instance message.</span></span> <span data-ttu-id="a9647-117">例如在**複製文字值**描述結果可以是"BoldExample"，這是實際的項目名稱。</span><span class="sxs-lookup"><span data-stu-id="a9647-117">For the example in the **Copy text value** description, the result is "BoldExample", which is the actual name of the element.</span></span>  
  
-   <span data-ttu-id="a9647-118">**複製文字與子內容值。**</span><span class="sxs-lookup"><span data-stu-id="a9647-118">**Copy text and sub content value.**</span></span> <span data-ttu-id="a9647-119">使用此值以串連輸入執行個體訊息中的節點值與其所有子節點值。</span><span class="sxs-lookup"><span data-stu-id="a9647-119">Use this value to concatenate the values of the node and all values of its child nodes in the input instance message.</span></span> <span data-ttu-id="a9647-120">例如在**複製文字值**說明，結果會是這粗體文字範例。 」，這很可能是定義為包含混合的內容項目的適當的結果。</span><span class="sxs-lookup"><span data-stu-id="a9647-120">For the example in the **Copy text value** description, the result is "This is a Bold Text example.", which might very well be the appropriate result for elements defined to contain mixed content.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9647-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a9647-121">See Also</span></span>  
 <span data-ttu-id="a9647-122">[大量複製運算質](../core/mass-copy-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="a9647-122">[Mass Copy Functoid](../core/mass-copy-functoid.md) </span></span>  
 <span data-ttu-id="a9647-123">[如何設定來源連結編譯器值](../core/how-to-set-the-source-links-compiler-value.md) </span><span class="sxs-lookup"><span data-stu-id="a9647-123">[How to Set the Source Links Compiler Value](../core/how-to-set-the-source-links-compiler-value.md) </span></span>  
 [<span data-ttu-id="a9647-124">節點階層層級比對</span><span class="sxs-lookup"><span data-stu-id="a9647-124">Node-Hierarchy Level Matching</span></span>](../core/node-hierarchy-level-matching.md)