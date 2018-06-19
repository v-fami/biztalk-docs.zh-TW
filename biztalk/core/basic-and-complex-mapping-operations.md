---
title: 基本和複雜對應作業 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: da864b48-6255-4847-9a6f-13e489e8658d
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 82876310cfa497f8002e7df680281122e90884af
ms.sourcegitcommit: 32f380810b90b70e5df7be72a6a14988a747868e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2018
ms.locfileid: "29710309"
---
# <a name="basic-and-complex-mapping-operations"></a><span data-ttu-id="a9a57-102">基本和複雜對應作業</span><span class="sxs-lookup"><span data-stu-id="a9a57-102">Basic and Complex Mapping Operations</span></span>
<span data-ttu-id="a9a57-103">BizTalk 對應工具提供各種對應實例的解決方案，範圍從簡單父-子樹狀結構類型作業到涉及迴圈記錄和階層的詳細複雜作業。</span><span class="sxs-lookup"><span data-stu-id="a9a57-103">BizTalk Mapper provides solutions for a variety of mapping scenarios ranging from simple parent-child tree-type operations to detailed, complex operations involving looping records and hierarchies.</span></span> <span data-ttu-id="a9a57-104">對應實例的複雜度是根據您的喜好設定和商務需求；XML 結構描述定義 (XSD) 語言提供相當大的彈性讓您定義結構格式。</span><span class="sxs-lookup"><span data-stu-id="a9a57-104">The complexity of a mapping scenario depends on your preferences and business needs—XML Schema definition (XSD) language gives you considerable flexibility in defining structured formats.</span></span> <span data-ttu-id="a9a57-105">幾乎所有對應實例都可分為兩種類別：基本對應和複雜對應。</span><span class="sxs-lookup"><span data-stu-id="a9a57-105">Almost all mapping scenarios fall into one of two categories: basic mapping and complex mapping.</span></span>  
  
## <a name="basic-mapping"></a><span data-ttu-id="a9a57-106">基本對應</span><span class="sxs-lookup"><span data-stu-id="a9a57-106">Basic Mapping</span></span>  
 <span data-ttu-id="a9a57-107">基本對應是您可以建立的最常見對應類型。</span><span class="sxs-lookup"><span data-stu-id="a9a57-107">Basic mapping is the most common type of mapping you can create.</span></span> <span data-ttu-id="a9a57-108">在基本對應中，輸入和輸出項目都會有一對一的關係。</span><span class="sxs-lookup"><span data-stu-id="a9a57-108">In a basic map, input and output items have a one-to-one relationship.</span></span> <span data-ttu-id="a9a57-109">輸入項目會對應至一個輸出項目，且就只能對應至一個輸出項目。</span><span class="sxs-lookup"><span data-stu-id="a9a57-109">An input item maps to one and only one output item.</span></span> <span data-ttu-id="a9a57-110">雖然許多類型的轉換和轉譯是使用基本的對應，例如使用多個 *運算質* 和階層式運算質來處理正在複製的值，基礎實例仍相當地簡單。</span><span class="sxs-lookup"><span data-stu-id="a9a57-110">Although many types of transformations and translations are possible with basic mapping, such as using multiple *functoids* and cascading functoids to manipulate the value being copied, the underlying scenario remains relatively simple.</span></span> <span data-ttu-id="a9a57-111">基本對應作業同時也包含將來自兩個不同父記錄 (僅發生一次) 的欄位對應至目的結構描述中之單一父記錄下的欄位。</span><span class="sxs-lookup"><span data-stu-id="a9a57-111">Basic mapping operations also include mapping fields from two different parent records (occurring only once) to fields under a single parent record in the destination schema.</span></span>  
  
## <a name="complex-mapping"></a><span data-ttu-id="a9a57-112">複雜對應</span><span class="sxs-lookup"><span data-stu-id="a9a57-112">Complex Mapping</span></span>  
 <span data-ttu-id="a9a57-113">複雜對應涉及記錄或欄位的單一執行個體中發生多次 **記錄** 或 **欄位項目** 結構描述樹狀結構中的節點。</span><span class="sxs-lookup"><span data-stu-id="a9a57-113">Complex mapping involves records or fields that occur multiple times for a single instance of the **Record** or **Field Element** node in the schema tree.</span></span> <span data-ttu-id="a9a57-114">這類節點的其 **Max Occurs** 屬性設定值大於一 (1)，表示執行個體訊息中可能有一個以上的對應項目。</span><span class="sxs-lookup"><span data-stu-id="a9a57-114">Such nodes have their **Max Occurs** property set to a value greater than one (1), indicating there may be more than one corresponding element in an instance message.</span></span> <span data-ttu-id="a9a57-115">當 BizTalk 對應時，使用這種類型的可變計數對應 (也稱為 *迴圈*)，可延伸樣式表語言 (XSL) 樣式表編譯器必須能夠判斷正確的迴圈路徑，要重複執行以產生所需的輸出。</span><span class="sxs-lookup"><span data-stu-id="a9a57-115">When a BizTalk map uses this type of variable count mapping (also known as *looping*), the Extensible Stylesheet Language (XSL) style sheet compiler must be able to determine the proper loop path over which to iterate to produce the required output.</span></span>  
  
 <span data-ttu-id="a9a57-116">一般而言，您可以將來源結構描述之迴圈記錄中的欄位連結至目的結構描述之迴圈記錄中的欄位。</span><span class="sxs-lookup"><span data-stu-id="a9a57-116">In general, you can link a field in a looping record in the source schema to a field in a looping record in the destination schema.</span></span> <span data-ttu-id="a9a57-117">輸入執行個體訊息中的對應項目數會決定在輸出執行個體訊息中所建立的項目數。</span><span class="sxs-lookup"><span data-stu-id="a9a57-117">The number of corresponding elements in an input instance message determines the number of elements created in the output instance message.</span></span> <span data-ttu-id="a9a57-118">例如，從範例來源與目的結構描述考量下列 XSD 分割。</span><span class="sxs-lookup"><span data-stu-id="a9a57-118">Consider the following XSD fragments from example source and destination schemas.</span></span>  
  
### <a name="source-schema-fragment"></a><span data-ttu-id="a9a57-119">來源結構描述分割</span><span class="sxs-lookup"><span data-stu-id="a9a57-119">Source Schema Fragment</span></span>  
  
```  
<xs:element minOccurs="1" maxOccurs="5"  
            name="SrcLoopingRecord">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="" type="xs:string" />   
      <xs:element name="" type="xs:integer" />   
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
  
```  
  
### <a name="destination-schema-fragment"></a><span data-ttu-id="a9a57-120">目的結構描述分割</span><span class="sxs-lookup"><span data-stu-id="a9a57-120">Destination Schema Fragment</span></span>  
  
```  
<xs:element minOccurs="0" maxOccurs="unbounded"  
            name="DstLoopingRecord">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="" type="xs:string" />   
      <xs:element name="" type="xs:integer" />   
      </xs:sequence>  
    </xs:complexType>  
  </xs:element>  
  
```  
  
 <span data-ttu-id="a9a57-121">在這些分割中：</span><span class="sxs-lookup"><span data-stu-id="a9a57-121">In these fragments:</span></span>  
  
-   <span data-ttu-id="a9a57-122">**SrcLoopingRecord**, 、 **記錄** 輸入執行個體訊息中的節點可以發生一到五次。</span><span class="sxs-lookup"><span data-stu-id="a9a57-122">**SrcLoopingRecord**, a **Record** node in input instance messages, can occur from one to five times.</span></span> <span data-ttu-id="a9a57-123">它也包含子 **欄位項目** 節點 **Field1** （字串） 和 **Field2** （整數），每個執行個體其所有父出現一次。</span><span class="sxs-lookup"><span data-stu-id="a9a57-123">It also contains the child **Field Element** nodes **Field1** (a string) and **Field2** (an integer) that occur once for each instance of their parent.</span></span>  
  
-   <span data-ttu-id="a9a57-124">**DstLoopingRecord**, 、 **記錄** 零 (0) 或更多次，可能會發生在輸出執行個體訊息中的節點。</span><span class="sxs-lookup"><span data-stu-id="a9a57-124">**DstLoopingRecord**, a **Record** node in output instance messages, can occur zero (0) or more times, unbounded.</span></span> <span data-ttu-id="a9a57-125">它也包含子 **欄位項目** 節點 **FieldA** （字串） 和 **FieldB** （整數），每個執行個體其所有父出現一次。</span><span class="sxs-lookup"><span data-stu-id="a9a57-125">It also contains the child **Field Element** nodes **FieldA** (a string) and **FieldB** (an integer) that occur once for each instance of their parent.</span></span>  
  
 <span data-ttu-id="a9a57-126">假設 Field1 已對應至 FieldA 而 Field2 已對應至 FieldB，且來自輸入執行個體訊息的下列分割已處理那些對應，則會產生來自輸出執行個體訊息的下列分割。</span><span class="sxs-lookup"><span data-stu-id="a9a57-126">Assuming that Field1 is mapped to FieldA and Field2 is mapped to FieldB, and that the following fragment from an input instance message has processed those mappings, the following fragment from an output instance message would be produced.</span></span>  
  
### <a name="input-instance-message-fragment"></a><span data-ttu-id="a9a57-127">輸入執行個體訊息分割</span><span class="sxs-lookup"><span data-stu-id="a9a57-127">Input Instance Message Fragment</span></span>  
  
```  
<SrcLoopingRecord>  
    <Field1>A string</Field1>  
    <Field2>10</Field2>  
</SrcLoopingRecord>  
<SrcLoopingRecord>  
    <Field1>Another string</Field1>  
    <Field2>11</Field2>  
</SrcLoopingRecord>  
<SrcLoopingRecord>  
    <Field1>A ball of string</Field1>  
    <Field2>12</Field2>  
</SrcLoopingRecord>  
```  
  
### <a name="output-instance-message-fragment"></a><span data-ttu-id="a9a57-128">輸出執行個體訊息分割</span><span class="sxs-lookup"><span data-stu-id="a9a57-128">Output Instance Message Fragment</span></span>  
  
```  
<DstLoopingRecord>  
    <FieldA>A string</FieldA>  
    <FieldB>10</FieldB>  
</DstLoopingRecord>  
<DstLoopingRecord>  
  <FieldA>Another string</FieldA>  
  <FieldB>11</FieldB>  
</DstLoopingRecord>  
<DstLoopingRecord>  
    <FieldA>A ball of string</FieldA>  
    <FieldB>12</FieldB>  
</DstLoopingRecord>  
```  
  
 <span data-ttu-id="a9a57-129">發生次數 **SrcLoopingRecord** 輸入執行個體訊息 (3) 中的元素會決定的次數 **DstLoopingRecord** 輸出執行個體訊息中的項目。</span><span class="sxs-lookup"><span data-stu-id="a9a57-129">The number of occurrences of the **SrcLoopingRecord** element in the input instance message (3) determines the number of occurrences of the **DstLoopingRecord** element in the output instance message.</span></span>  
  
 <span data-ttu-id="a9a57-130">BizTalk 對應工具不支援使用多個迴圈路徑的對應類型。</span><span class="sxs-lookup"><span data-stu-id="a9a57-130">A type of mapping not supported by BizTalk Mapper is the use of multiple loop paths.</span></span> <span data-ttu-id="a9a57-131">這類型的對應涉及將來自來源結構描述中之兩個或更多迴圈記錄的欄位，對應至目的結構描述之單一迴圈記錄內的欄位。</span><span class="sxs-lookup"><span data-stu-id="a9a57-131">This type of mapping involves fields from two or more looping records in the source schema being mapped to fields within a single looping record in the destination schema.</span></span> <span data-ttu-id="a9a57-132">這會有一個問題，就是沒有有效的方式可判斷在輸出執行個體訊息中所產生的項目數目。</span><span class="sxs-lookup"><span data-stu-id="a9a57-132">This presents a problem—there is no effective way to determine the number of elements to produce in the output instance message.</span></span> <span data-ttu-id="a9a57-133">多個迴圈路徑會導致出現對應編譯警告，指出目的節點具有多個來源迴圈路徑。</span><span class="sxs-lookup"><span data-stu-id="a9a57-133">Multiple loop paths result in a map compilation warning indicating that the destination node has multiple source loop paths.</span></span> <span data-ttu-id="a9a57-134">然而，這只是一個警告，並會使用第一個來源迴圈路徑中的重複數目來判斷在輸出執行個體中所產生的項目數目。</span><span class="sxs-lookup"><span data-stu-id="a9a57-134">However, this is only a warning, and the number of iterations in the first source loop path is used to determine the number of elements produced in the output instance message.</span></span> <span data-ttu-id="a9a57-135">您可能需要明確控制迴圈行為使用 **迴圈** 運算質。</span><span class="sxs-lookup"><span data-stu-id="a9a57-135">You can take explicit control of looping behavior by using the **Looping** functoid.</span></span>  
  
 <span data-ttu-id="a9a57-136">Microsoft BizTalk Server 在引進新類型的迴圈，稱為表格驅動迴圈。</span><span class="sxs-lookup"><span data-stu-id="a9a57-136">Microsoft BizTalk Server introduced a new kind of looping called table-driven looping.</span></span> <span data-ttu-id="a9a57-137">當您的輸出執行個體訊息必須以來自輸入執行個體訊息 (結合一或多個條件約束、來源結構描述的連結或運算質) 的資料為基礎時，表格驅動迴圈就十分有用。</span><span class="sxs-lookup"><span data-stu-id="a9a57-137">Table-driven looping is useful when your output instance message needs to be based on data from the input instance message, combined with one or more constants, links from the source schema, or functoids.</span></span> <span data-ttu-id="a9a57-138">在這類情況下，輸出執行個體訊息可以有多個記錄以輸入執行個體訊息之單一記錄的資料為基礎 (而該輸入執行個體訊息會結合不同條件約束)，或可以有多個記錄以輸入執行個體訊息之多個記錄的資料為基礎。</span><span class="sxs-lookup"><span data-stu-id="a9a57-138">In such cases, the output instance message can have multiple records based on data from a single record in the input instance message that is combined with different constants, or based on data coming from multiple records in the input instance message.</span></span> <span data-ttu-id="a9a57-139">如需表格驅動迴圈使用**表格迴圈**和**表格抽選程式**運算質，請參閱[表格迴圈和表格擷取程式運算質](../core/table-looping-and-table-extractor-functoids.md)。</span><span class="sxs-lookup"><span data-stu-id="a9a57-139">For more information about table-driven looping using the **Table Looping** and **Table Extractor** functoids, see [Table Looping and Table Extractor Functoids](../core/table-looping-and-table-extractor-functoids.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9a57-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a9a57-140">See Also</span></span>  
 <span data-ttu-id="a9a57-141">[對應](../core/maps.md) </span><span class="sxs-lookup"><span data-stu-id="a9a57-141">[Maps](../core/maps.md) </span></span>  
 [<span data-ttu-id="a9a57-142">使用 BizTalk 對應工具建立對應</span><span class="sxs-lookup"><span data-stu-id="a9a57-142">Creating Maps Using BizTalk Mapper</span></span>](../core/creating-maps-using-biztalk-mapper.md)