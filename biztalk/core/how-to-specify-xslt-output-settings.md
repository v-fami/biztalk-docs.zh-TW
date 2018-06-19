---
title: 如何指定 XSLT 輸出設定 |Microsoft 文件
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
ms.openlocfilehash: e1aa3eea4c3f2f4696d3dc1fdf8109aeddec3ff8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22255334"
---
# <a name="set-map-compilation-and-output-settings"></a><span data-ttu-id="b9f8d-102">設定對應編譯和輸出設定</span><span class="sxs-lookup"><span data-stu-id="b9f8d-102">Set map compilation and output settings</span></span>
<span data-ttu-id="b9f8d-103">BizTalk 對應工具中設定對應屬性。</span><span class="sxs-lookup"><span data-stu-id="b9f8d-103">Set the map properties in the BizTalk mapper.</span></span> 

<span data-ttu-id="b9f8d-104">使用這些對應屬性，您可以設定如何編譯對應、 包含或排除 XML 宣告，以及設定的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="b9f8d-104">Using these map properties, you can set how maps are compiled, include or exclude an XML declaration, and set the encoding.</span></span> 

<span data-ttu-id="b9f8d-105">本主題會示範如何在地圖上設定這些屬性。</span><span class="sxs-lookup"><span data-stu-id="b9f8d-105">This topic shows you how to set these properties on your map.</span></span>

## <a name="set-the-map-level-compilation"></a><span data-ttu-id="b9f8d-106">設定地圖層級編譯</span><span class="sxs-lookup"><span data-stu-id="b9f8d-106">Set the map-level compilation</span></span>

<span data-ttu-id="b9f8d-107">**從開始[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]** ，您選擇`XslTransform`或`XslCompiledTransform`類別來編譯您的對應。</span><span class="sxs-lookup"><span data-stu-id="b9f8d-107">**Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)]**, you choose the `XslTransform` or the `XslCompiledTransform` class to compile your maps.</span></span> 

1. <span data-ttu-id="b9f8d-108">在方格檢視中開啟您的對應。</span><span class="sxs-lookup"><span data-stu-id="b9f8d-108">Open your map in the Grid view.</span></span>
2. <span data-ttu-id="b9f8d-109">在對應工具方格中，按一下滑鼠右鍵，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="b9f8d-109">Right-click anywhere in the mapper grid, and select **Properties**.</span></span>  
3. <span data-ttu-id="b9f8d-110">設定**使用 XSL 轉換**屬性：</span><span class="sxs-lookup"><span data-stu-id="b9f8d-110">Set the **Use XSL Transform** property:</span></span> 

    | <span data-ttu-id="b9f8d-111">選項</span><span class="sxs-lookup"><span data-stu-id="b9f8d-111">Option</span></span> | <span data-ttu-id="b9f8d-112">Description</span><span class="sxs-lookup"><span data-stu-id="b9f8d-112">Description</span></span> |
    | --- | --- |
    | <span data-ttu-id="b9f8d-113">未定義</span><span class="sxs-lookup"><span data-stu-id="b9f8d-113">Undefined</span></span> | <span data-ttu-id="b9f8d-114">會使用 XslTransform 設定的登錄旗標：</span><span class="sxs-lookup"><span data-stu-id="b9f8d-114">The registry flag for the XslTransform setting is used:</span></span> <ul><li><span data-ttu-id="b9f8d-115">64 位元主控件執行個體：`HKLM\SOFTWARE\Microsoft\BizTalk Server\3.0\Configuration`</span><span class="sxs-lookup"><span data-stu-id="b9f8d-115">64-bit host instances: `HKLM\SOFTWARE\Microsoft\BizTalk Server\3.0\Configuration`</span></span></li><li><span data-ttu-id="b9f8d-116">32 位元主控件執行個體，以及 Visual Studio 的 [測試對應] 功能：`HKLM\SOFTWARE\Wow6432Node\Microsoft\BizTalk Server\3.0\Configuration`</span><span class="sxs-lookup"><span data-stu-id="b9f8d-116">32-bit host instances, and Visual Studio’s Test Map functionality: `HKLM\SOFTWARE\Wow6432Node\Microsoft\BizTalk Server\3.0\Configuration`</span></span></li></ul> | 
    | <span data-ttu-id="b9f8d-117">True</span><span class="sxs-lookup"><span data-stu-id="b9f8d-117">True</span></span> | <span data-ttu-id="b9f8d-118">對應層級編譯屬性設定為`XslTransform`（舊版的行為）</span><span class="sxs-lookup"><span data-stu-id="b9f8d-118">The map level compilation property is set to `XslTransform` (legacy behavior)</span></span> | 
    | <span data-ttu-id="b9f8d-119">False</span><span class="sxs-lookup"><span data-stu-id="b9f8d-119">False</span></span> | <span data-ttu-id="b9f8d-120">對應層級編譯屬性設定為`XslCompiledTransform`</span><span class="sxs-lookup"><span data-stu-id="b9f8d-120">The map level compilation property is set to `XslCompiledTransform`</span></span> | 

> [!NOTE] 
> <span data-ttu-id="b9f8d-121">從 BizTalk Server 2013 開始，對應工具編譯行為已變更從`XslTransform`至`XslCompiledTransform`。</span><span class="sxs-lookup"><span data-stu-id="b9f8d-121">Starting with BizTalk Server 2013, the mapper compilation behavior was changed from `XslTransform` to `XslCompiledTransform`.</span></span> <span data-ttu-id="b9f8d-122">[對應工具更新意義您](http://www.quicklearn.com/blog/2013/05/24/what-the-biztalk-server-2013-mapper-updates-mean-for-you/)部落格文章提供絕佳說明的行為和其潛在的影響。</span><span class="sxs-lookup"><span data-stu-id="b9f8d-122">The [What the Mapper Updates Mean for You](http://www.quicklearn.com/blog/2013/05/24/what-the-biztalk-server-2013-mapper-updates-mean-for-you/) blog post provides a great explanation of the behavior, and its potential impact.</span></span> 
> 
> <span data-ttu-id="b9f8d-123">從開始[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]，您可以選擇哪一個類別來編譯您的對應。</span><span class="sxs-lookup"><span data-stu-id="b9f8d-123">Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)], you can choose which class to compile your maps.</span></span> 
  
## <a name="include-or-exclude-an-xml-declaration"></a><span data-ttu-id="b9f8d-124">包含或排除 XML 宣告</span><span class="sxs-lookup"><span data-stu-id="b9f8d-124">Include or exclude an XML declaration</span></span>  
<span data-ttu-id="b9f8d-125">您可以選擇不論 XML 宣告是否為輸出。</span><span class="sxs-lookup"><span data-stu-id="b9f8d-125">You can choose whether an XML declaration is output or not.</span></span> 

1. <span data-ttu-id="b9f8d-126">在方格檢視中開啟您的對應。</span><span class="sxs-lookup"><span data-stu-id="b9f8d-126">Open your map in the Grid view.</span></span>
2. <span data-ttu-id="b9f8d-127">在對應工具方格中，按一下滑鼠右鍵，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="b9f8d-127">Right-click anywhere in the mapper grid, and select **Properties**.</span></span>  
3. <span data-ttu-id="b9f8d-128">在下拉式清單中**省略 XML 宣告**屬性選取**是**省略 XML 宣告。</span><span class="sxs-lookup"><span data-stu-id="b9f8d-128">In the drop-down list for the **Omit XML Declaration** property, select **Yes** to omit an XML declaration.</span></span> <span data-ttu-id="b9f8d-129">選取**否**不以省略 XML 宣告。</span><span class="sxs-lookup"><span data-stu-id="b9f8d-129">Select **No** not to omit an XML declaration.</span></span>  

<span data-ttu-id="b9f8d-130">XML 宣告會出現 (如果您選取**否**) 與下列類似。</span><span class="sxs-lookup"><span data-stu-id="b9f8d-130">An XML declaration would appear (if you selected **No**) similar to the following.</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
```  
  
## <a name="set-encoding-for-output-instance-data"></a><span data-ttu-id="b9f8d-131">設定編碼輸出執行個體資料</span><span class="sxs-lookup"><span data-stu-id="b9f8d-131">Set encoding for output instance data</span></span>  
<span data-ttu-id="b9f8d-132">編碼提供執行階段引擎所需的資訊，用以決定在建立對應的輸出結果時要使用哪個字元集。</span><span class="sxs-lookup"><span data-stu-id="b9f8d-132">Encoding provides the run-time engine with the information it needs to determine which character set to use when creating the output result of a map.</span></span>  
   
1. <span data-ttu-id="b9f8d-133">在方格檢視中開啟您的對應。</span><span class="sxs-lookup"><span data-stu-id="b9f8d-133">Open your map in the Grid view.</span></span>
2. <span data-ttu-id="b9f8d-134">在對應工具方格中，按一下滑鼠右鍵，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="b9f8d-134">Right-click anywhere in the mapper grid, and select **Properties**.</span></span>    
3.  <span data-ttu-id="b9f8d-135">在下拉式清單中**XSLT 編碼**屬性中，選取您要字元集用於輸出執行個體資料。</span><span class="sxs-lookup"><span data-stu-id="b9f8d-135">In the drop-down list for the **XSLT Encoding** property, select the character set you want used for the output instance data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9f8d-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b9f8d-136">See Also</span></span>  
 <span data-ttu-id="b9f8d-137">[編譯和測試對應](../core/compiling-and-testing-maps.md) </span><span class="sxs-lookup"><span data-stu-id="b9f8d-137">[Compiling and Testing Maps](../core/compiling-and-testing-maps.md) </span></span>  
 <span data-ttu-id="b9f8d-138">[使用 BizTalk 對應工具](../core/using-biztalk-mapper.md) </span><span class="sxs-lookup"><span data-stu-id="b9f8d-138">[Using BizTalk Mapper](../core/using-biztalk-mapper.md) </span></span>  
 [<span data-ttu-id="b9f8d-139">有效的 BizTalk 對應工具 XSLT 編碼類型</span><span class="sxs-lookup"><span data-stu-id="b9f8d-139">Valid BizTalk Mapper XSLT Encoding Types</span></span>](../core/valid-biztalk-mapper-xslt-encoding-types.md)