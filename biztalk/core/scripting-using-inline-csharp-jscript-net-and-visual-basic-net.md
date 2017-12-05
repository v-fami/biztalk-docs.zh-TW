---
title: "使用內嵌 C#、 JScript.NET 和 Visual Basic.NET 指令碼 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Scripting functoids, JScript
- Scripting functoids, warnings
- Scripting functoids, Visual Basic .NET
- Scripting functoids, inline C#
- Scripting functoids, .NET
ms.assetid: dda60024-58bd-483f-a750-31b21059eded
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fe2002bd92342a953406a21e076b801d3e90b938
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="scripting-using-inline-c-jscript-net-and-visual-basic-net"></a><span data-ttu-id="65c3e-102">使用內嵌 C#、JScript .NET 以及 Visual Basic .NET 的指令碼處理</span><span class="sxs-lookup"><span data-stu-id="65c3e-102">Scripting Using Inline C#, JScript .NET, and Visual Basic .NET</span></span>
<span data-ttu-id="65c3e-103">對於您不想在應用程式之其他地方使用的自訂程式碼而言，內嵌指令碼非常方便。</span><span class="sxs-lookup"><span data-stu-id="65c3e-103">Inline scripts are convenient for custom code that you are unlikely to use elsewhere in your application.</span></span>  
  
 <span data-ttu-id="65c3e-104">BizTalk 會在定義對應的可延伸樣式表語言轉換 (XSLT) 樣式表中儲存內嵌指令碼。</span><span class="sxs-lookup"><span data-stu-id="65c3e-104">BizTalk saves inline scripts in the Extensible Stylesheet Language Transformations (XSLT) stylesheet defining the map.</span></span> <span data-ttu-id="65c3e-105">因此，內嵌指令碼可以將相同的命名空間當成任何其他 XSLT 樣式表指令碼。</span><span class="sxs-lookup"><span data-stu-id="65c3e-105">Because of this, inline scripts may use the same namespaces as any other XSLT stylesheet script.</span></span> <span data-ttu-id="65c3e-106">下表顯示可用的命名空間。</span><span class="sxs-lookup"><span data-stu-id="65c3e-106">The following table shows the available namespaces.</span></span>  
  
|<span data-ttu-id="65c3e-107">命名空間</span><span class="sxs-lookup"><span data-stu-id="65c3e-107">Namespace</span></span>|<span data-ttu-id="65c3e-108">Description</span><span class="sxs-lookup"><span data-stu-id="65c3e-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="65c3e-109">系統</span><span class="sxs-lookup"><span data-stu-id="65c3e-109">System</span></span>|<span data-ttu-id="65c3e-110">系統類別。</span><span class="sxs-lookup"><span data-stu-id="65c3e-110">The System class.</span></span>|  
|<span data-ttu-id="65c3e-111">System.Collection</span><span class="sxs-lookup"><span data-stu-id="65c3e-111">System.Collection</span></span>|<span data-ttu-id="65c3e-112">集合類別。</span><span class="sxs-lookup"><span data-stu-id="65c3e-112">The collection classes.</span></span>|  
|<span data-ttu-id="65c3e-113">System.Text</span><span class="sxs-lookup"><span data-stu-id="65c3e-113">System.Text</span></span>|<span data-ttu-id="65c3e-114">文字類別。</span><span class="sxs-lookup"><span data-stu-id="65c3e-114">The text classes.</span></span>|  
|<span data-ttu-id="65c3e-115">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="65c3e-115">System.Text.RegularExpressions</span></span>|<span data-ttu-id="65c3e-116">規則運算式類別。</span><span class="sxs-lookup"><span data-stu-id="65c3e-116">The regular expression classes.</span></span>|  
|<span data-ttu-id="65c3e-117">System.Xml</span><span class="sxs-lookup"><span data-stu-id="65c3e-117">System.Xml</span></span>|<span data-ttu-id="65c3e-118">核心 XML 類別。</span><span class="sxs-lookup"><span data-stu-id="65c3e-118">The core XML classes.</span></span>|  
|<span data-ttu-id="65c3e-119">System.Xml.Xsl</span><span class="sxs-lookup"><span data-stu-id="65c3e-119">System.Xml.Xsl</span></span>|<span data-ttu-id="65c3e-120">XSLT 類別。</span><span class="sxs-lookup"><span data-stu-id="65c3e-120">The XSLT classes.</span></span>|  
|<span data-ttu-id="65c3e-121">System.Xml.Xpath</span><span class="sxs-lookup"><span data-stu-id="65c3e-121">System.Xml.Xpath</span></span>|<span data-ttu-id="65c3e-122">XPath 類別。</span><span class="sxs-lookup"><span data-stu-id="65c3e-122">The XPath classes.</span></span>|  
|<span data-ttu-id="65c3e-123">Microsoft.VisualBasic</span><span class="sxs-lookup"><span data-stu-id="65c3e-123">Microsoft.VisualBasic</span></span>|<span data-ttu-id="65c3e-124">Visual Basic 指令碼類別。</span><span class="sxs-lookup"><span data-stu-id="65c3e-124">The Visual Basic script classes.</span></span>|  
  
 <span data-ttu-id="65c3e-125">如需有關命名空間和資料類型的詳細資訊，搜尋"XSLT 樣式表指令碼處理使用\<msxsl: script\>"和"System.Xml.Xsl.XslCompiledTransform".NET Framework 集合中。</span><span class="sxs-lookup"><span data-stu-id="65c3e-125">For more information about namespaces and data types, search on "XSLT Stylesheet Scripting using \<msxsl:script\>" and on "System.Xml.Xsl.XslCompiledTransform" in the .NET Framework collection.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="65c3e-126">請避免重複使用相同的方法簽章。</span><span class="sxs-lookup"><span data-stu-id="65c3e-126">Avoid using the same method signature more than once.</span></span> <span data-ttu-id="65c3e-127">數個指令碼處理運算質具有相同的方法簽章時，BizTalk 會選取第一個實作，並捨棄其他實作。</span><span class="sxs-lookup"><span data-stu-id="65c3e-127">When several Scripting functoids have the same method signature, BizTalk selects the first implementation and disregards the others.</span></span>  
  
 <span data-ttu-id="65c3e-128">除了對一次指令碼相當方便以外，內嵌指令碼對於在一些指令碼之間宣告全域變數而言也相當有用。</span><span class="sxs-lookup"><span data-stu-id="65c3e-128">In addition to being convenient for one-time scripts, inline scripts are also useful for declaring global variables for use among a number of scripts.</span></span> <span data-ttu-id="65c3e-129">例如，在 C# 內嵌指令碼中，您可以將下列程式碼行放在任何類別外部。</span><span class="sxs-lookup"><span data-stu-id="65c3e-129">For example, in a C# inline script, you could place the following line of code outside of any class.</span></span>  
  
```  
ArrayList statusList = new ArrayList();  
```  
  
 <span data-ttu-id="65c3e-130">這會建立**ArrayList**， `statusList`，可在對應中的所有內嵌指令碼。</span><span class="sxs-lookup"><span data-stu-id="65c3e-130">This creates an **ArrayList**, `statusList`, available to all inline scripts in the map.</span></span>  
  
 <span data-ttu-id="65c3e-131">內嵌指令碼範例，請參閱[（BizTalk Server 範例資料夾） 的 XML 工具](../core/xml-tools-biztalk-server-samples-folder.md)。</span><span class="sxs-lookup"><span data-stu-id="65c3e-131">For a sample inline script, see [XML Tools (BizTalk Server Samples Folder)](../core/xml-tools-biztalk-server-samples-folder.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65c3e-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="65c3e-132">See Also</span></span>  
 <span data-ttu-id="65c3e-133">[指令碼處理運算質](../core/scripting-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="65c3e-133">[Scripting Functoid](../core/scripting-functoid.md) </span></span>  
 <span data-ttu-id="65c3e-134">[使用外部組件指令碼](../core/scripting-using-external-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="65c3e-134">[Scripting Using External Assemblies](../core/scripting-using-external-assemblies.md) </span></span>  
 <span data-ttu-id="65c3e-135">[使用內嵌 XSLT 與 XSLT 呼叫範本指令碼](../core/scripting-using-inline-xslt-and-xslt-call-templates.md) </span><span class="sxs-lookup"><span data-stu-id="65c3e-135">[Scripting Using Inline XSLT and XSLT Call Templates](../core/scripting-using-inline-xslt-and-xslt-call-templates.md) </span></span>  
 <span data-ttu-id="65c3e-136">[如何新增指令碼運算質至對應](../core/how-to-add-scripting-functoids-to-a-map.md) </span><span class="sxs-lookup"><span data-stu-id="65c3e-136">[How to Add Scripting Functoids to a Map](../core/how-to-add-scripting-functoids-to-a-map.md) </span></span>  
 [<span data-ttu-id="65c3e-137">How to Configure the Scripting Functoid</span><span class="sxs-lookup"><span data-stu-id="65c3e-137">How to Configure the Scripting Functoid</span></span>](../core/how-to-configure-the-scripting-functoid.md)