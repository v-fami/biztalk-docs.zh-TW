---
title: 剖析模式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- pipeline components [custom], code samples
- pipeline components [custom], parsing
ms.assetid: b1188720-e5ae-47ae-ab8e-16d7ed08b778
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cf8f9b2618b8cafd7813f08217457227a0f21809
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22263302"
---
# <a name="parsing-modes"></a><span data-ttu-id="819b5-102">剖析模式</span><span class="sxs-lookup"><span data-stu-id="819b5-102">Parsing Modes</span></span>
<span data-ttu-id="819b5-103">剖析模式是 schemaInfo 記錄上的屬性，它有兩個模式：速度和複雜性。</span><span class="sxs-lookup"><span data-stu-id="819b5-103">The parsing mode is an attribute on the schemaInfo record, with two modes: speed and complexity.</span></span> <span data-ttu-id="819b5-104">您可在 BizTalk 結構描述編輯器中設定「剖析器最佳化」屬性。</span><span class="sxs-lookup"><span data-stu-id="819b5-104">The Parser Optimization property can be configured within the BizTalk Schema Editor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="819b5-105">範例</span><span class="sxs-lookup"><span data-stu-id="819b5-105">Example</span></span>  
  
```  
<b:schemaInfo count_positions_by_byte="false" standard="Flat File"   
root_reference="document" parser_optimization="complexity" />.  
```  
  
 <span data-ttu-id="819b5-106">在速度模式中，剖析器會嘗試如同在資料流中一般提供資料。</span><span class="sxs-lookup"><span data-stu-id="819b5-106">In speed mode, the parser tries to fit data as they appear in the stream.</span></span> <span data-ttu-id="819b5-107">例如，提供下列結構描述。</span><span class="sxs-lookup"><span data-stu-id="819b5-107">For example, given the following schema.</span></span>  
  
```  
<schema>  
   Root ("," prefix)  
      Field1   opt  
      Field2   opt  
      Field3   opt  
      Field4   opt  
      Record ("," infix)  
            Field5  
            Field6  
</schema>  
```  
  
 <span data-ttu-id="819b5-108">及輸入訊息。</span><span class="sxs-lookup"><span data-stu-id="819b5-108">and input message.</span></span>  
  
```  
,1,2,3,4  
```  
  
 <span data-ttu-id="819b5-109">在速度模式中，會取得下列 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="819b5-109">with speed mode the following XML document is obtained.</span></span>  
  
```  
<Root>  
   <Field1>1</Field1>  
   <Field2>2</Field2>  
   <Field3>3</Field3>  
   <Field4>4</Field4>  
</Root>  
```  
  
 <span data-ttu-id="819b5-110">在複雜性模式中，相同的結構描述則會產生下列輸出。</span><span class="sxs-lookup"><span data-stu-id="819b5-110">With complexity mode, the same schema produces the following output.</span></span>  
  
```  
<Root>  
   <Field1>1</Field1>  
   <Field2>2</Field2>  
      <Record>  
         <Field5>3</Field5>  
         <Field6>4</Field6>  
      </Record>  
</Root>  
```  
  
 <span data-ttu-id="819b5-111">在複雜性模式中，一般檔案剖析引擎會同時使用由上至下和由下至上的剖析，並嘗試提供更精確的資料。</span><span class="sxs-lookup"><span data-stu-id="819b5-111">In complexity mode, the flat file parsing engine uses both top-down and bottom-up parsing, and tries to fit data more accurately.</span></span> <span data-ttu-id="819b5-112">在速度模式中，剖析器會嘗試如同在資料流中一般提供資料。</span><span class="sxs-lookup"><span data-stu-id="819b5-112">In speed mode, the parser tries to fit data as they appear in the stream.</span></span>  
  
 <span data-ttu-id="819b5-113">例如，如果您擁有具有必要項目的選用項目時。</span><span class="sxs-lookup"><span data-stu-id="819b5-113">If you have optional elements with required elements, for example.</span></span>  
  
```  
<schema>  
   Root  
      Record1 (required)  
  
      Record2 (optional)  
  
      Record3 (required)  
  
```  
  
 <span data-ttu-id="819b5-114">您必須使用複雜性模式才可正確剖析資料，因為剖析器會在內部將剖析器表示為</span><span class="sxs-lookup"><span data-stu-id="819b5-114">you must use complexity mode to correctly parse the data, because the parser represents the schema internally as.</span></span>  
  
```  
<schema>  
   Root  
      Record1 (required)  
      <sequence> (optional)  
         Record2 (required)  
         Record3 (required)  
```  
  
## <a name="see-also"></a><span data-ttu-id="819b5-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="819b5-115">See Also</span></span>  
 [<span data-ttu-id="819b5-116">使用一般檔案剖析引擎</span><span class="sxs-lookup"><span data-stu-id="819b5-116">Using the Flat File Parsing Engine</span></span>](../core/using-the-flat-file-parsing-engine.md)