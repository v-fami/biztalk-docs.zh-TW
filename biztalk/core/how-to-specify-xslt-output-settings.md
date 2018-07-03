---
title: 如何指定 XSLT 輸出設定 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4c541432-fd4e-41cc-8bcc-f570ce5df439
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1d55a8ddccb996f11315c8856797147083da9123
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36998031"
---
# <a name="set-map-compilation-and-output-settings"></a><span data-ttu-id="07ae6-102">設定對應編譯和輸出設定</span><span class="sxs-lookup"><span data-stu-id="07ae6-102">Set map compilation and output settings</span></span>
<span data-ttu-id="07ae6-103">設定 BizTalk 對應工具中的對應屬性。</span><span class="sxs-lookup"><span data-stu-id="07ae6-103">Set the map properties in the BizTalk mapper.</span></span> 

<span data-ttu-id="07ae6-104">使用這些屬性對應，您可以設定如何編譯對應、 包含或排除 XML 宣告，以及設定的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="07ae6-104">Using these map properties, you can set how maps are compiled, include or exclude an XML declaration, and set the encoding.</span></span> 

<span data-ttu-id="07ae6-105">本主題說明如何設定這些屬性在地圖上。</span><span class="sxs-lookup"><span data-stu-id="07ae6-105">This topic shows you how to set these properties on your map.</span></span>

## <a name="set-the-map-level-compilation"></a><span data-ttu-id="07ae6-106">設定對應層級的編譯</span><span class="sxs-lookup"><span data-stu-id="07ae6-106">Set the map-level compilation</span></span>

<span data-ttu-id="07ae6-107">**開頭[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]** ，您選擇`XslTransform`或`XslCompiledTransform`類別來編譯您的對應。</span><span class="sxs-lookup"><span data-stu-id="07ae6-107">**Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)]**, you choose the `XslTransform` or the `XslCompiledTransform` class to compile your maps.</span></span> 

1. <span data-ttu-id="07ae6-108">方格檢視中開啟您的對應。</span><span class="sxs-lookup"><span data-stu-id="07ae6-108">Open your map in the Grid view.</span></span>
2. <span data-ttu-id="07ae6-109">以滑鼠右鍵按一下對應工具方格中的任何位置，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="07ae6-109">Right-click anywhere in the mapper grid, and select **Properties**.</span></span>  
3. <span data-ttu-id="07ae6-110">設定**使用 XSL 轉換**屬性：</span><span class="sxs-lookup"><span data-stu-id="07ae6-110">Set the **Use XSL Transform** property:</span></span> 

    | <span data-ttu-id="07ae6-111">選項</span><span class="sxs-lookup"><span data-stu-id="07ae6-111">Option</span></span> | <span data-ttu-id="07ae6-112">描述</span><span class="sxs-lookup"><span data-stu-id="07ae6-112">Description</span></span> |
    | --- | --- |
    | <span data-ttu-id="07ae6-113">未定義</span><span class="sxs-lookup"><span data-stu-id="07ae6-113">Undefined</span></span> | <span data-ttu-id="07ae6-114">使用 XslTransform 設定的登錄旗標：</span><span class="sxs-lookup"><span data-stu-id="07ae6-114">The registry flag for the XslTransform setting is used:</span></span> <ul><li><span data-ttu-id="07ae6-115">64 位元主控件執行個體： `HKLM\SOFTWARE\Microsoft\BizTalk Server\3.0\Configuration`</span><span class="sxs-lookup"><span data-stu-id="07ae6-115">64-bit host instances: `HKLM\SOFTWARE\Microsoft\BizTalk Server\3.0\Configuration`</span></span></li><li><span data-ttu-id="07ae6-116">32 位元主控件執行個體，以及 Visual Studio 的 [測試對應] 功能： `HKLM\SOFTWARE\Wow6432Node\Microsoft\BizTalk Server\3.0\Configuration`</span><span class="sxs-lookup"><span data-stu-id="07ae6-116">32-bit host instances, and Visual Studio’s Test Map functionality: `HKLM\SOFTWARE\Wow6432Node\Microsoft\BizTalk Server\3.0\Configuration`</span></span></li></ul> | 
    | <span data-ttu-id="07ae6-117">True</span><span class="sxs-lookup"><span data-stu-id="07ae6-117">True</span></span> | <span data-ttu-id="07ae6-118">對應層級的編譯屬性設定為`XslTransform`（舊版行為）</span><span class="sxs-lookup"><span data-stu-id="07ae6-118">The map level compilation property is set to `XslTransform` (legacy behavior)</span></span> | 
    | <span data-ttu-id="07ae6-119">False</span><span class="sxs-lookup"><span data-stu-id="07ae6-119">False</span></span> | <span data-ttu-id="07ae6-120">對應層級的編譯屬性設定為 `XslCompiledTransform`</span><span class="sxs-lookup"><span data-stu-id="07ae6-120">The map level compilation property is set to `XslCompiledTransform`</span></span> | 

> [!NOTE]
> <span data-ttu-id="07ae6-121">從 BizTalk Server 2013，對應工具編譯行為已變更從`XslTransform`至`XslCompiledTransform`。</span><span class="sxs-lookup"><span data-stu-id="07ae6-121">Starting with BizTalk Server 2013, the mapper compilation behavior was changed from `XslTransform` to `XslCompiledTransform`.</span></span> <span data-ttu-id="07ae6-122">[什麼 Mapper Updates Mean for You](http://www.quicklearn.com/blog/2013/05/24/what-the-biztalk-server-2013-mapper-updates-mean-for-you/)部落格文章提供詳細說明了行為，以及其潛在的影響。</span><span class="sxs-lookup"><span data-stu-id="07ae6-122">The [What the Mapper Updates Mean for You](http://www.quicklearn.com/blog/2013/05/24/what-the-biztalk-server-2013-mapper-updates-mean-for-you/) blog post provides a great explanation of the behavior, and its potential impact.</span></span> 
> 
> <span data-ttu-id="07ae6-123">從開始[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]，您可以選擇哪一個類別來編譯您的對應。</span><span class="sxs-lookup"><span data-stu-id="07ae6-123">Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)], you can choose which class to compile your maps.</span></span> 
  
## <a name="include-or-exclude-an-xml-declaration"></a><span data-ttu-id="07ae6-124">包含或排除 XML 宣告</span><span class="sxs-lookup"><span data-stu-id="07ae6-124">Include or exclude an XML declaration</span></span>  
<span data-ttu-id="07ae6-125">您可以選擇是否 XML 宣告是否為輸出。</span><span class="sxs-lookup"><span data-stu-id="07ae6-125">You can choose whether an XML declaration is output or not.</span></span> 

1. <span data-ttu-id="07ae6-126">方格檢視中開啟您的對應。</span><span class="sxs-lookup"><span data-stu-id="07ae6-126">Open your map in the Grid view.</span></span>
2. <span data-ttu-id="07ae6-127">以滑鼠右鍵按一下對應工具方格中的任何位置，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="07ae6-127">Right-click anywhere in the mapper grid, and select **Properties**.</span></span>  
3. <span data-ttu-id="07ae6-128">中的下拉式清單**省略 XML 宣告**屬性中，選取**是**省略 XML 宣告。</span><span class="sxs-lookup"><span data-stu-id="07ae6-128">In the drop-down list for the **Omit XML Declaration** property, select **Yes** to omit an XML declaration.</span></span> <span data-ttu-id="07ae6-129">選取  **No**不表示省略 XML 宣告。</span><span class="sxs-lookup"><span data-stu-id="07ae6-129">Select **No** not to omit an XML declaration.</span></span>  

<span data-ttu-id="07ae6-130">XML 宣告會出現 (如果您選取**No**) 如下所示。</span><span class="sxs-lookup"><span data-stu-id="07ae6-130">An XML declaration would appear (if you selected **No**) similar to the following.</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
```  
  
## <a name="set-encoding-for-output-instance-data"></a><span data-ttu-id="07ae6-131">設定編碼方式輸出執行個體資料</span><span class="sxs-lookup"><span data-stu-id="07ae6-131">Set encoding for output instance data</span></span>  
<span data-ttu-id="07ae6-132">編碼提供執行階段引擎所需的資訊，用以決定在建立對應的輸出結果時要使用哪個字元集。</span><span class="sxs-lookup"><span data-stu-id="07ae6-132">Encoding provides the run-time engine with the information it needs to determine which character set to use when creating the output result of a map.</span></span>  
   
1. <span data-ttu-id="07ae6-133">方格檢視中開啟您的對應。</span><span class="sxs-lookup"><span data-stu-id="07ae6-133">Open your map in the Grid view.</span></span>
2. <span data-ttu-id="07ae6-134">以滑鼠右鍵按一下對應工具方格中的任何位置，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="07ae6-134">Right-click anywhere in the mapper grid, and select **Properties**.</span></span>    
3.  <span data-ttu-id="07ae6-135">中的下拉式清單**XSLT 編碼**屬性中，選取您要字元集用於輸出執行個體資料。</span><span class="sxs-lookup"><span data-stu-id="07ae6-135">In the drop-down list for the **XSLT Encoding** property, select the character set you want used for the output instance data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07ae6-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="07ae6-136">See Also</span></span>  
 <span data-ttu-id="07ae6-137">[編譯和測試對應](../core/compiling-and-testing-maps.md) </span><span class="sxs-lookup"><span data-stu-id="07ae6-137">[Compiling and Testing Maps](../core/compiling-and-testing-maps.md) </span></span>  
 <span data-ttu-id="07ae6-138">[使用 BizTalk 對應工具](../core/using-biztalk-mapper.md) </span><span class="sxs-lookup"><span data-stu-id="07ae6-138">[Using BizTalk Mapper](../core/using-biztalk-mapper.md) </span></span>  
 [<span data-ttu-id="07ae6-139">有效的 BizTalk 對應工具 XSLT 編碼類型</span><span class="sxs-lookup"><span data-stu-id="07ae6-139">Valid BizTalk Mapper XSLT Encoding Types</span></span>](../core/valid-biztalk-mapper-xslt-encoding-types.md)