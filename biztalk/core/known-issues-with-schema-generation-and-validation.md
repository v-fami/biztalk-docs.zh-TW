---
title: "結構描述產生和驗證的已知問題 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df1eaa6c-0d3e-4aec-9de0-8b9817b7bb97
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0b830e955b54ae8e3ba7fc05f21f22acd97f290a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="known-issues-with-schema-generation-and-validation"></a><span data-ttu-id="53d83-102">結構描述的產生和驗證的已知的問題</span><span class="sxs-lookup"><span data-stu-id="53d83-102">Known Issues with Schema Generation and Validation</span></span>
<span data-ttu-id="53d83-103">本主題提供產生和驗證結構描述的已知問題相關資訊。</span><span class="sxs-lookup"><span data-stu-id="53d83-103">This topic provides information about known issues with schema generation and validation.</span></span>  
  
## <a name="an-instance-message-generated-for-a-positional-record-with-tags-could-be-incorrect"></a><span data-ttu-id="53d83-104">為具有標記的位置記錄產生的執行個體訊息有可能不正確</span><span class="sxs-lookup"><span data-stu-id="53d83-104">An instance message generated for a positional record with tags could be incorrect</span></span>  
 <span data-ttu-id="53d83-105">就位置記錄而言，標記可以在欄位之中或是跨越欄位之間。</span><span class="sxs-lookup"><span data-stu-id="53d83-105">For positional records, the tag can be within a field or can span between fields.</span></span> <span data-ttu-id="53d83-106">不論哪一種情況，產生的執行個體將無效，而且可能在剖析階段期間的「剖析引擎」中導致失敗。</span><span class="sxs-lookup"><span data-stu-id="53d83-106">In either case, the instance generated will not be valid and will cause a failure in the Parsing Engine during the parsing stage.</span></span>  
  
 <span data-ttu-id="53d83-107">若標記不屬於任何子系 (子記錄或子欄位) 的一部分，就不會發生此問題。</span><span class="sxs-lookup"><span data-stu-id="53d83-107">If the tag is not part of any children (child records or child fields), this problem will not occur.</span></span>  
  
 <span data-ttu-id="53d83-108">若要解決此問題，請在結構描述中包含標記的實際值做為預設。</span><span class="sxs-lookup"><span data-stu-id="53d83-108">To work around this issue, include the actual value of the tag as the default in the schema.</span></span> <span data-ttu-id="53d83-109">在一般檔案延伸 BizTalk 編輯器中，您可以設定**固定值**或**預設值**屬性的適當位置欄位標籤的值。</span><span class="sxs-lookup"><span data-stu-id="53d83-109">In the flat file extension of the BizTalk Editor, you can set the **Fixed Value** or **Default Value** property of the appropriate positional field with the value of the tag.</span></span>  
  
## <a name="an-instance-message-generated-for-a-field-with-some-restrictions-may-not-pass-validation"></a><span data-ttu-id="53d83-110">為具有某些限制的欄位所產生的執行個體訊息可能無法通過驗證</span><span class="sxs-lookup"><span data-stu-id="53d83-110">An instance message generated for a field with some restrictions may not pass validation</span></span>  
 <span data-ttu-id="53d83-111">當您從包含一或多個結構描述產生執行個體訊息時**欄位項目**和**欄位屬性**具有使用限制機制，例如衍生的資料類型的節點當**模式**屬性時，產生這類欄位的範例資料可能不符合需求的限制，因此可以防止使用相同的結構描述，從該執行個體訊息的驗證成功它所產生。</span><span class="sxs-lookup"><span data-stu-id="53d83-111">When you generate an instance message from a schema that contains one or more **Field Element** and **Field Attribute** nodes that have data types that have been derived using the restriction mechanism, such as when the **Pattern** property is used, the sample data generated for such fields may not conform to the requirements of the restriction, thereby preventing successful validation of that instance message using the same schema from which it was generated.</span></span>  
  
## <a name="an-instance-message-generated-for-a-schema-that-contains-an-infinite-loop-may-not-be-valid"></a><span data-ttu-id="53d83-112">為包含無限迴圈的結構描述所產生的執行個體訊息可能無效。</span><span class="sxs-lookup"><span data-stu-id="53d83-112">An instance message generated for a schema that contains an infinite loop may not be valid.</span></span>  
 <span data-ttu-id="53d83-113">包含節點的循環參考時，您的結構描述可以包含無限迴圈**Min Occurs**大於或等於一，本質上會防止終止條件的屬性值。</span><span class="sxs-lookup"><span data-stu-id="53d83-113">Your schema can contain an infinite loop when it contains a circular reference to a node with a **Min Occurs** property value greater than or equal to one, essentially preventing a termination condition.</span></span> <span data-ttu-id="53d83-114">您需要人工終止產生執行個體訊息，才能完成產生作業，但是產生的執行個體訊息也因此不符合產生它的結構描述。</span><span class="sxs-lookup"><span data-stu-id="53d83-114">Instance message generation will artificially terminate so that the generation operation can complete, but the produced instance message will thereby not conform to the schema from which it was generated.</span></span> <span data-ttu-id="53d83-115">這樣的結構描述通常是有問題的。</span><span class="sxs-lookup"><span data-stu-id="53d83-115">Such schemas are usually suspect.</span></span>  
  
## <a name="validation-of-xml-instance-fails-for-document-schema-which-has-the-target-namespacehttpwwww3orgxml1998namespace"></a><span data-ttu-id="53d83-116">文件結構描述的 XML 執行個體驗證失敗，其 target namespace="http://www.w3.org/XML/1998/namespace"</span><span class="sxs-lookup"><span data-stu-id="53d83-116">Validation of XML instance fails for document schema which has the target namespace="http://www.w3.org/XML/1998/namespace"</span></span>  
 <span data-ttu-id="53d83-117">"超連結"http://www.w3.org/XML/1998/namespace"http://www.w3.org/XML/1998/namespace"是保留的命名空間，其前置詞應該為"XML"。</span><span class="sxs-lookup"><span data-stu-id="53d83-117">The “ HYPERLINK "http://www.w3.org/XML/1998/namespace" http://www.w3.org/XML/1998/namespace” is a reserved namespace whose prefix should be “XML”.</span></span> <span data-ttu-id="53d83-118">您可以手動將前置詞編輯為 "XML"。</span><span class="sxs-lookup"><span data-stu-id="53d83-118">You can manually edit the prefix to “XML”.</span></span>

## <a name="see-also"></a><span data-ttu-id="53d83-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="53d83-119">See also</span></span>
<span data-ttu-id="53d83-120">這些屬性的詳細[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="53d83-120">More details on these properties [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>