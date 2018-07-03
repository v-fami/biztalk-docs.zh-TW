---
title: 建立對應 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cc9f8ad1-4aad-4866-8aa4-4877fdc5e5f9
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0e27f4fae142f4c781f95be148ec80e2dff51383
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37003095"
---
# <a name="creating-maps"></a><span data-ttu-id="a8d0a-102">建立對應</span><span class="sxs-lookup"><span data-stu-id="a8d0a-102">Creating Maps</span></span>
<span data-ttu-id="a8d0a-103">BizTalk 對應工具的主要使用者介面會顯示在索引標籤內[!INCLUDE[btsCoName](../includes/btsconame-md.md)][!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]編輯視窗。</span><span class="sxs-lookup"><span data-stu-id="a8d0a-103">The primary user interface for BizTalk Mapper is displayed on a tab within the [!INCLUDE[btsCoName](../includes/btsconame-md.md)][!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] editing window.</span></span> <span data-ttu-id="a8d0a-104">此顯示分成三個窗格。</span><span class="sxs-lookup"><span data-stu-id="a8d0a-104">This display is divided into three panes.</span></span> <span data-ttu-id="a8d0a-105">左窗格以樹狀結構顯示來源結構描述，</span><span class="sxs-lookup"><span data-stu-id="a8d0a-105">The left pane displays the source schema as a tree.</span></span> <span data-ttu-id="a8d0a-106">而右窗格會將目的結構描述顯示為樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="a8d0a-106">The right pane displays the destination schema as a tree.</span></span> <span data-ttu-id="a8d0a-107">中間窗格則會將格線顯示為多頁。</span><span class="sxs-lookup"><span data-stu-id="a8d0a-107">The middle pane displays the grid as multiple pages.</span></span> <span data-ttu-id="a8d0a-108">若要指出您想要如何將資料從來源結構描述對應至目的結構描述，則您可以在想要對應的記錄與欄位之間繪製線條。</span><span class="sxs-lookup"><span data-stu-id="a8d0a-108">To indicate how you want to map data from the source schema to the destination schema, you draw lines between the records and fields you want to map.</span></span> <span data-ttu-id="a8d0a-109">這些線條稱為*連結*，而且是指定之資料的對應最基本的方式。</span><span class="sxs-lookup"><span data-stu-id="a8d0a-109">These lines are called *links*, and they are the most basic way to specify the mapping of data.</span></span> <span data-ttu-id="a8d0a-110">如需連結記錄和欄位的詳細資訊，請參閱 <<c0> [ 對應中的連結](../core/links-in-maps.md)。</span><span class="sxs-lookup"><span data-stu-id="a8d0a-110">For more information about linking records and fields, see [Links in Maps](../core/links-in-maps.md).</span></span>  
  
 <span data-ttu-id="a8d0a-111">如果您需要實作更進階的對應方法，可以使用運算質。</span><span class="sxs-lookup"><span data-stu-id="a8d0a-111">If you want to implement more advanced mapping methods, you can use functoids.</span></span> <span data-ttu-id="a8d0a-112">運算質是位於 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 工具箱內 BizTalk 對應工具索引標籤上的工具，</span><span class="sxs-lookup"><span data-stu-id="a8d0a-112">Functoids are tools available on BizTalk Mapper tabs within the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Toolbox.</span></span> <span data-ttu-id="a8d0a-113">可以讓您建立對應來執行較複雜的作業，例如：</span><span class="sxs-lookup"><span data-stu-id="a8d0a-113">They enable you to create maps to perform more complex operations, such as:</span></span>  
  
- <span data-ttu-id="a8d0a-114">在來源結構描述的兩個欄位中新增值，然後將結果放置在目的結構描述的一個欄位中。</span><span class="sxs-lookup"><span data-stu-id="a8d0a-114">Adding the values in two fields in a source schema and putting the result in a field in the destination schema.</span></span>  
  
- <span data-ttu-id="a8d0a-115">計算迴圈記錄中之一個欄位的平均值，然後將結果放置在目的結構描述的一個欄位中。</span><span class="sxs-lookup"><span data-stu-id="a8d0a-115">Calculating the average value of a field in a looping record and putting the result in a field in the destination schema.</span></span>  
  
- <span data-ttu-id="a8d0a-116">視您的商務需求，適當地撰寫自訂指令碼來處理執行個體資料。</span><span class="sxs-lookup"><span data-stu-id="a8d0a-116">Writing a custom script to manipulate instance data as appropriate for your business needs.</span></span>  
  
  <span data-ttu-id="a8d0a-117">如需運算質的詳細資訊，請參閱[運算質在對應中的](../core/functoids-in-maps.md)。</span><span class="sxs-lookup"><span data-stu-id="a8d0a-117">For more information about functoids, see [Functoids in Maps](../core/functoids-in-maps.md).</span></span>  
  
  <span data-ttu-id="a8d0a-118">BizTalk 對應工具可以支援許多不同的對應實例，範圍從簡單的父-子關係到詳細且複雜的記錄迴圈和階層。</span><span class="sxs-lookup"><span data-stu-id="a8d0a-118">BizTalk Mapper can support many different mapping scenarios from simple parent-child relationships to detailed, complex looping of records and hierarchies.</span></span> <span data-ttu-id="a8d0a-119">建立對應時請考量下列事項：</span><span class="sxs-lookup"><span data-stu-id="a8d0a-119">Consider the following when you create maps:</span></span>  
  
- <span data-ttu-id="a8d0a-120">BizTalk 對應工具不支援合併與排序。</span><span class="sxs-lookup"><span data-stu-id="a8d0a-120">BizTalk Mapper does not support merge and sort.</span></span>  
  
- <span data-ttu-id="a8d0a-121">如果來源和目標結構描述結構差異很大，則可能無法在單一對應中執行轉換。</span><span class="sxs-lookup"><span data-stu-id="a8d0a-121">If the source and target schema structures are extremely different, it is possible that the transformation cannot be done in a single map.</span></span> <span data-ttu-id="a8d0a-122">您可能需要採用雙重對應。</span><span class="sxs-lookup"><span data-stu-id="a8d0a-122">You may need a double pass.</span></span>  
  
- <span data-ttu-id="a8d0a-123">**迴圈**運算質有彈性且功能強大，但您無法中斷反覆運算時偵測到來源結構描述的值變更來啟動目標迴圈的下一個反覆項目。</span><span class="sxs-lookup"><span data-stu-id="a8d0a-123">**Looping** functoids are flexible and powerful, yet you will not be able to break up the iteration when a change in value on the source schema is detected to start the next iteration of the target loop.</span></span>  
  
- <span data-ttu-id="a8d0a-124">您可以宣告的變數中的方法外**指令碼處理**運算質，會導致變數會出現在對應的存留期內的範圍。</span><span class="sxs-lookup"><span data-stu-id="a8d0a-124">You can declare a variable outside the method in a **Scripting** functoid, which results in the variable being in scope for the life of the map.</span></span> <span data-ttu-id="a8d0a-125">因此，您可以使用**指令碼處理**」 運算質轉換的各個範圍區之間保留值。</span><span class="sxs-lookup"><span data-stu-id="a8d0a-125">Therefore, you can use the **Scripting** functoid for holding values between scope areas of the transformation.</span></span>  
  
  <span data-ttu-id="a8d0a-126">處理的所有資料[!INCLUDE[btsCoName](../includes/btsconame-md.md)][!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在執行階段必須是 XML 格式。</span><span class="sxs-lookup"><span data-stu-id="a8d0a-126">All data processed by [!INCLUDE[btsCoName](../includes/btsconame-md.md)][!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] at run time must be in XML format.</span></span> <span data-ttu-id="a8d0a-127">所有非 XML 資料都必須轉譯成相等的 XML 格式，才能進行對應。</span><span class="sxs-lookup"><span data-stu-id="a8d0a-127">All non-XML data must be translated to an equivalent XML format before mapping.</span></span> <span data-ttu-id="a8d0a-128">同樣地，當對應程序完成時，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會使用對應作業的輸出來建立檔案格式，而這是接收資料的交易夥伴或應用程式可辨識的檔案格式。</span><span class="sxs-lookup"><span data-stu-id="a8d0a-128">Similarly, when the mapping process is complete, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses the output of a mapping operation to create a file format that is recognized by the trading partner or application to which the data is sent.</span></span>  
  
  <span data-ttu-id="a8d0a-129">BizTalk 對應工具包含一個編譯器。</span><span class="sxs-lookup"><span data-stu-id="a8d0a-129">BizTalk Mapper includes a compiler.</span></span> <span data-ttu-id="a8d0a-130">此工具層次的元件會產生可延伸樣式表語言轉換 (XSLT)，且必須有 XSLT 才能將輸入執行個體訊息轉換或轉譯成輸出執行個體訊息。</span><span class="sxs-lookup"><span data-stu-id="a8d0a-130">This tool-level component generates the Extensible Stylesheet Language Transformations (XSLT) needed to transform or translate input instance messages to output instance messages.</span></span>  
  
  <span data-ttu-id="a8d0a-131">本節提供使用 BizTalk 對應工具在兩個結構描述之間建立對應的工作特定資訊。</span><span class="sxs-lookup"><span data-stu-id="a8d0a-131">This section provides task-specific information about using BizTalk Mapper to create the mapping between two schemas.</span></span> <span data-ttu-id="a8d0a-132">假設您已開啟 BizTalk 對應工具，且已選擇您的來源與目的結構描述。</span><span class="sxs-lookup"><span data-stu-id="a8d0a-132">It assumes that you already have BizTalk Mapper open, and have chosen your source and destination schemas.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a8d0a-133">本節內容</span><span class="sxs-lookup"><span data-stu-id="a8d0a-133">In This Section</span></span>  
  
-   [<span data-ttu-id="a8d0a-134">管理專案中的對應</span><span class="sxs-lookup"><span data-stu-id="a8d0a-134">Managing Maps Within Projects</span></span>](../core/managing-maps-within-projects.md)  
  
-   [<span data-ttu-id="a8d0a-135">使用連結指定記錄和欄位對應</span><span class="sxs-lookup"><span data-stu-id="a8d0a-135">Using Links to Specify Record and Field Mappings</span></span>](../core/using-links-to-specify-record-and-field-mappings.md)  
  
-   [<span data-ttu-id="a8d0a-136">使用運算質建立更多複雜對應</span><span class="sxs-lookup"><span data-stu-id="a8d0a-136">Using Functoids to Create More Complex Mappings</span></span>](../core/using-functoids-to-create-more-complex-mappings.md)  
  
-   [<span data-ttu-id="a8d0a-137">如何建立不含對應</span><span class="sxs-lookup"><span data-stu-id="a8d0a-137">How to Create a Map without Maps</span></span>](../core/how-to-create-a-map-without-maps.md)  
  
-   [<span data-ttu-id="a8d0a-138">管理預設對應工具的行為使用\<mapsource\></span><span class="sxs-lookup"><span data-stu-id="a8d0a-138">Managing Default Mapper Behavior Using \<mapsource\></span></span>](../core/managing-default-mapper-behavior-using-mapsource.md)