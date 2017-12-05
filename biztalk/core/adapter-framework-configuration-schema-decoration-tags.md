---
title: "配接器架構組態結構描述裝飾標記 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d5d7f6b-2273-45a6-ba9d-43201760cf22
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d49aac9f11ef48bd0a66dcc9bda3a769cd6c34f4
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="adapter-framework-configuration-schema-decoration-tags"></a><span data-ttu-id="674ad-102">配接器架構組態結構描述裝飾標記</span><span class="sxs-lookup"><span data-stu-id="674ad-102">Adapter Framework Configuration Schema Decoration Tags</span></span>
<span data-ttu-id="674ad-103">您可以使用在此主題中描述，組態結構描述檔案內的標記，來顯示和組織配接器屬性頁上的資料。</span><span class="sxs-lookup"><span data-stu-id="674ad-103">You can use the tags described in this topic within the configuration schema files to display and organize data on the adapter property pages.</span></span>  
  
 <span data-ttu-id="674ad-104">下圖顯示 FTP 接收位置屬性頁如何實作這些標記中的一些標記。</span><span class="sxs-lookup"><span data-stu-id="674ad-104">The following figure shows how the FTP receive location property page implements some of these tags.</span></span>  
  
 <span data-ttu-id="674ad-105">![](../core/media/ebiz-prog-custad-tags.gif "ebiz_prog_custad_tags")</span><span class="sxs-lookup"><span data-stu-id="674ad-105">![](../core/media/ebiz-prog-custad-tags.gif "ebiz_prog_custad_tags")</span></span>  
<span data-ttu-id="674ad-106">\<描述\>， \<displayname\>，和\<類別\>FTP 配接器屬性頁中的標籤</span><span class="sxs-lookup"><span data-stu-id="674ad-106">The \<description\>, \<displayname\>, and \<category\> tags in the FTP adapter property page</span></span>  
  
## <a name="designer"></a><span data-ttu-id="674ad-107">\<設計工具\></span><span class="sxs-lookup"><span data-stu-id="674ad-107">\<designer\></span></span>  
 <span data-ttu-id="674ad-108">BizTalk 配接器架構會裝飾出現之間\<baf: designer\>標記和\</baf:designer\>結束標記。</span><span class="sxs-lookup"><span data-stu-id="674ad-108">The BizTalk Adapter Framework decorations appear between a \<baf:designer\> tag and \</baf:designer\> end tag.</span></span> <span data-ttu-id="674ad-109">\<Baf: designer\>標記可協助區分配接器架構\<appinfo\>和其他配接器提供\<appinfo\>資訊。</span><span class="sxs-lookup"><span data-stu-id="674ad-109">The \<baf:designer\> tag helps distinguish between Adapter Framework \<appinfo\> and other adapter-supplied \<appinfo\> information.</span></span>  
  
## <a name="category"></a><span data-ttu-id="674ad-110">\<類別目錄\></span><span class="sxs-lookup"><span data-stu-id="674ad-110">\<category\></span></span>  
 <span data-ttu-id="674ad-111">\<類別\>裝飾包含用來分隔在屬性方格中的項目分組的字串。</span><span class="sxs-lookup"><span data-stu-id="674ad-111">The \<category\> decoration contains the string used to separate entries in the property grid into groups.</span></span> <span data-ttu-id="674ad-112">此裝飾會將具有相同類別字串的所有項目都顯示為該類別的部屬項目。</span><span class="sxs-lookup"><span data-stu-id="674ad-112">The decoration displays all entries with the same category string as subordinate entries of the category.</span></span>  
  
 <span data-ttu-id="674ad-113">您可以當地語系化\<類別\>項目。</span><span class="sxs-lookup"><span data-stu-id="674ad-113">You can localize \<category\> entries.</span></span>  
  
## <a name="description"></a><span data-ttu-id="674ad-114">\<描述\></span><span class="sxs-lookup"><span data-stu-id="674ad-114">\<description\></span></span>  
 <span data-ttu-id="674ad-115">\<描述\>裝飾包含用來在屬性方格的底端的項目提供描述性文字的字串。</span><span class="sxs-lookup"><span data-stu-id="674ad-115">The \<description\> decoration contains the string used to provide descriptive text for entries at the bottom of the property grid.</span></span>  
  
 <span data-ttu-id="674ad-116">您可以當地語系化\<描述\>項目。</span><span class="sxs-lookup"><span data-stu-id="674ad-116">You can localize \<description\> entries.</span></span>  
  
## <a name="displayname"></a><span data-ttu-id="674ad-117">\<顯示名稱\></span><span class="sxs-lookup"><span data-stu-id="674ad-117">\<displayname\></span></span>  
 <span data-ttu-id="674ad-118">\<Displayname\>裝飾包含用來顯示的項目名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="674ad-118">The \<displayname\> decoration contains the string used for displaying the name of an entry.</span></span> <span data-ttu-id="674ad-119">這可讓您使用空格、 片語，依此類推，不會允許針對時\<元素\>或\<屬性\>名稱。</span><span class="sxs-lookup"><span data-stu-id="674ad-119">This enables you to use spaces, phrases, and so on, when they would not be allowed for an \<element\> or \<attribute\> name.</span></span>  
  
 <span data-ttu-id="674ad-120">您可以當地語系化\<displayname\>項目。</span><span class="sxs-lookup"><span data-stu-id="674ad-120">You can localize \<displayname\> entries.</span></span>  
  
## <a name="readonly"></a><span data-ttu-id="674ad-121">\<readonly\></span><span class="sxs-lookup"><span data-stu-id="674ad-121">\<readonly\></span></span>  
 <span data-ttu-id="674ad-122">\<Fixed =""\>裝飾可控制是否可編輯欄位。</span><span class="sxs-lookup"><span data-stu-id="674ad-122">The \<readonly fixed=""\> decoration controls whether a field may be edited.</span></span> <span data-ttu-id="674ad-123">`true` 的 "fixed" 屬性值 (預設值) 會使欄位變成唯讀。</span><span class="sxs-lookup"><span data-stu-id="674ad-123">A "fixed" attribute value of `true` (the default) makes a field read-only.</span></span>  
  
 <span data-ttu-id="674ad-124">當實作外部編輯器時，實作外部**TypeConverter**類別並覆寫**getstandardvaluesexclusive （itypedescriptorcontext)**方法改為。</span><span class="sxs-lookup"><span data-stu-id="674ad-124">When implementing an external editor, implement an external **TypeConverter** class and override the **GetStandardValuesExclusive(ITypeDescriptorContext)** method instead.</span></span> <span data-ttu-id="674ad-125">傳回 `true` 會使欄位變成唯讀，不過卻會保留對自訂編輯器的存取。</span><span class="sxs-lookup"><span data-stu-id="674ad-125">Returning `true` makes a field read-only but preserves access to the custom editor.</span></span>  
  
## <a name="browsable"></a><span data-ttu-id="674ad-126">\<可瀏覽\></span><span class="sxs-lookup"><span data-stu-id="674ad-126">\<browsable\></span></span>  
 <span data-ttu-id="674ad-127">\<可瀏覽顯示 =""\>裝飾可控制是否在屬性方格中顯示的欄位。</span><span class="sxs-lookup"><span data-stu-id="674ad-127">The \<browsable show=""\> decoration controls whether a field appears in the property grid.</span></span> <span data-ttu-id="674ad-128">`True` 的 "show" 屬性值 (預設值) 會使欄位出現在方格中。</span><span class="sxs-lookup"><span data-stu-id="674ad-128">A "show" attribute value of `True` (the default) makes a field appear in the grid.</span></span>  
  
## <a name="converter"></a><span data-ttu-id="674ad-129">\<轉換程式\></span><span class="sxs-lookup"><span data-stu-id="674ad-129">\<converter\></span></span>  
 <span data-ttu-id="674ad-130">\<轉換器組件 =""\>裝飾指定所要**TypeConverter**類別名稱\<元素\>或\<屬性\>。</span><span class="sxs-lookup"><span data-stu-id="674ad-130">The \<converter assembly=""\> decoration specifies the desired **TypeConverter** class name for the \<element\> or \<attribute\>.</span></span> <span data-ttu-id="674ad-131">選擇性的"assembly"屬性值指定包含所需的組件的路徑**TypeConverter**。</span><span class="sxs-lookup"><span data-stu-id="674ad-131">The optional "assembly" attribute value specifies the path to the assembly containing the desired **TypeConverter**.</span></span> <span data-ttu-id="674ad-132">當沒有指定 "assembly" 值時，類別名稱必須包含全域組件快取的組件名稱、索引鍵、文化特性和版本值。</span><span class="sxs-lookup"><span data-stu-id="674ad-132">With no "assembly" value specified, the class name must include the global assembly cache's assembly name, key, culture, and version values.</span></span>  
  
## <a name="editor"></a><span data-ttu-id="674ad-133">\<編輯器\></span><span class="sxs-lookup"><span data-stu-id="674ad-133">\<editor\></span></span>  
 <span data-ttu-id="674ad-134">\<編輯器組件 =""\>裝飾指定所要**UITypeEditor**類別名稱\<元素\>或\<屬性\>。</span><span class="sxs-lookup"><span data-stu-id="674ad-134">The \<editor assembly=""\> decoration specifies the desired **UITypeEditor** class name for the \<element\> or \<attribute\>.</span></span> <span data-ttu-id="674ad-135">選擇性的"assembly"屬性值指定包含所需的組件的路徑**UITypeEditor**。</span><span class="sxs-lookup"><span data-stu-id="674ad-135">The optional "assembly" attribute value specifies the path to the assembly containing the desired **UITypeEditor**.</span></span> <span data-ttu-id="674ad-136">當沒有指定 "assembly" 值時，類別名稱必須包含全域組件快取的組件名稱、索引鍵、文化特性和版本值。</span><span class="sxs-lookup"><span data-stu-id="674ad-136">With no "assembly" value specified, the class name must include the global assembly cache's assembly name, key, culture, and version values.</span></span>  
  
## <a name="null-values-for-optional-enumerations"></a><span data-ttu-id="674ad-137">選擇性列舉的 Null 值</span><span class="sxs-lookup"><span data-stu-id="674ad-137">Null Values for Optional Enumerations</span></span>  
 <span data-ttu-id="674ad-138">當使用選擇性的列舉，其中一個值應該是\<無\>來表示 null 值。</span><span class="sxs-lookup"><span data-stu-id="674ad-138">When using an optional enumeration, one of the values should be \<none\> to denote a null value.</span></span> <span data-ttu-id="674ad-139">這不是內建的標記，不過如果列舉衍生自 xsd:string，即可提供被視為「無」的列舉值以達成這點。</span><span class="sxs-lookup"><span data-stu-id="674ad-139">This is not a built-in tag, but may be achieved by providing an enumeration value that is treated as none if the enumeration is derived from xsd:string.</span></span> <span data-ttu-id="674ad-140">這對衍生自 xsd:int 的列舉則是不可能的，因為整數都必須保留值。</span><span class="sxs-lookup"><span data-stu-id="674ad-140">This is not possible for enumerations derived from xsd:int, because the integer must hold a value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="674ad-141">請參閱</span><span class="sxs-lookup"><span data-stu-id="674ad-141">See Also</span></span>  
 [<span data-ttu-id="674ad-142">配接器架構設定結構描述延伸模組</span><span class="sxs-lookup"><span data-stu-id="674ad-142">Adapter Framework Configuration Schema Extensions</span></span>](../core/adapter-framework-configuration-schema-extensions.md)