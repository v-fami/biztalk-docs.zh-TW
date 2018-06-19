---
title: 管理預設對應工具的行為使用&lt;mapsource&gt; |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: deea839c-e52e-44c6-ac0d-4396dc5b10d8
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 44e2e66350709c6b857d875ec3979fe3f7059648
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22263374"
---
# <a name="managing-default-mapper-behavior-using-ltmapsourcegt"></a><span data-ttu-id="0781a-102">管理預設對應工具的行為使用&lt;mapsource&gt;</span><span class="sxs-lookup"><span data-stu-id="0781a-102">Managing Default Mapper Behavior Using &lt;mapsource&gt;</span></span>
<span data-ttu-id="0781a-103">您可以藉由修改屬性來修改 BizTalk 對應工具的特定預設行為**mapsource**直接在對應來源 (.btm) 檔案中的項目。</span><span class="sxs-lookup"><span data-stu-id="0781a-103">You can modify certain default behaviors of BizTalk Mapper by modifying attributes of the **mapsource** element directly in a map source (.btm) file.</span></span>  
  
## <a name="optimizing-value-mapping-functoid-code-generation"></a><span data-ttu-id="0781a-104">最佳化值對應運算質程式碼的產生</span><span class="sxs-lookup"><span data-stu-id="0781a-104">Optimizing Value Mapping Functoid Code Generation</span></span>  
 <span data-ttu-id="0781a-105">當對應工具會產生 XSLT 程式碼以呼叫**值對應**運算質，變數用來儲存結果。</span><span class="sxs-lookup"><span data-stu-id="0781a-105">When the Mapper generates XSLT code to call the **Value Mapping** functoid, a variable is used to store the result.</span></span> <span data-ttu-id="0781a-106">您可以使用**OptimizeValueMapping**旗標來最佳化**值對應**運算質，讓產生變數時，才`if`陳述式會評估為`True`。</span><span class="sxs-lookup"><span data-stu-id="0781a-106">You can use the **OptimizeValueMapping** flag to optimize the **Value Mapping** functoid so that a variable is generated only when the `if` statement evaluates to `True`.</span></span> <span data-ttu-id="0781a-107">例如，與**OptimizeValueMapping**設**否**:</span><span class="sxs-lookup"><span data-stu-id="0781a-107">For example, with **OptimizeValueMapping** set to **No**:</span></span>  
  
```  
<xsl:variable name="var:v5" select="ScriptNS0:FormatMessage(…)" />  
<xsl:if test="string($var:v4)='true'">  
     <xsl:variable name="var:v6" select="string($var:v5)" />  
     <ns0:text>  
          <xsl:value-of select="$var:v6" />  
     </ns0:text>  
</xsl:if>  
```  
  
 <span data-ttu-id="0781a-108">這段程式碼無法進行最佳化，藉由移動**值對應**運算質引動過程傳入的主體`if`陳述式，確保引動過程發生當它時才需要。</span><span class="sxs-lookup"><span data-stu-id="0781a-108">This code could be optimized by moving the **Value Mapping** functoid invocation into the body of the `if` statement, ensuring that invocation occurs only when it is required.</span></span> <span data-ttu-id="0781a-109">設定**OptimizeValueMapping**至**是**會產生下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="0781a-109">Setting **OptimizeValueMapping** to **Yes** yields the following code:</span></span>  
  
```  
<xsl:if test="string($var:v4)='true'">  
     <xsl:variable name="var:v5" select="ScriptNS0:FormatMessage(…)" />  
     <xsl:variable name="var:v6" select="string($var:v5)" />  
     <ns0:text>  
          <xsl:value-of select="$var:v6" />  
     </ns0:text>  
</xsl:if>  
```  
  
 <span data-ttu-id="0781a-110">對應工具會自動進行最佳化如果您設定**OptimizeValueMapping**屬性**mapsource**對應來源 (.btm) 檔案中的項目**是**為顯示：</span><span class="sxs-lookup"><span data-stu-id="0781a-110">The Mapper does this optimization automatically if you set the **OptimizeValueMapping** attribute of the **mapsource** element in the map source (.btm) file to **Yes** as shown:</span></span>  
  
```  
<mapsource Name="BizTalk Map" BizTalkServerMapperTool_Version="2.0" Version="2" XRange="100" YRange="420" OmitXmlDeclaration="Yes" TreatElementsAsRecords="No" OptimizeValueMapping="Yes" GenerateDefaultFixedNodes="Yes" CopyPIs="No" method="xml" xmlVersion="1.0" IgnoreNamespacesForLinks="Yes">  
```  
  
## <a name="accommodating-schemas-with-large-footprints"></a><span data-ttu-id="0781a-111">配合佔用空間很大的結構描述</span><span class="sxs-lookup"><span data-stu-id="0781a-111">Accommodating Schemas with Large Footprints</span></span>  
 <span data-ttu-id="0781a-112">當對應工具所使用的結構描述具有佔用空間很大的執行個體以及複雜的多層級結構和 (或) 遞迴式節點時，在測試、驗證或編譯對應時，就可能要花費很長的時間，在較差的情況下還會導致「記憶體不足」的錯誤。</span><span class="sxs-lookup"><span data-stu-id="0781a-112">When the Mapper is using a schema that has a very large instance footprint with deep complex structures and/or recursive nodes, testing the map, validating the map, or compiling the map could take a long time or, in the worse case, result in an "out of memory" error.</span></span> <span data-ttu-id="0781a-113">這種情況可能發生於小型的複雜結構描述，也可能發生於大型的結構描述。</span><span class="sxs-lookup"><span data-stu-id="0781a-113">This could happen with small, complex schemas as well as with large schemas.</span></span>  
  
 <span data-ttu-id="0781a-114">複雜的結構描述的問題是因為，對應工具必須遞迴地載入整個結構描述樹狀目錄中尋找的節點，請將連接連結，或有**值**對它們設定屬性。</span><span class="sxs-lookup"><span data-stu-id="0781a-114">The problem with complex schemas is due to the fact that the Mapper has to recursively load the entire schema tree looking for nodes that either have links connected to them or have the **Value** property set on them.</span></span> <span data-ttu-id="0781a-115">您可以藉由設定來減輕此問題**GenerateDefaultFixedNodes**旗標**mapsource** .btm 檔案中的項目**否**所示：</span><span class="sxs-lookup"><span data-stu-id="0781a-115">You can alleviate this problem by setting the **GenerateDefaultFixedNodes** flag of the **mapsource** element in the .btm files to **No** as shown:</span></span>  
  
```  
<mapsource Name="BizTalk Map" BizTalkServerMapperTool_Version="2.0" Version="2" XRange="100" YRange="420" OmitXmlDeclaration="Yes" TreatElementsAsRecords="No" OptimizeValueMapping="No" GenerateDefaultFixedNodes="No" CopyPIs="No" method="xml" xmlVersion="1.0" IgnoreNamespacesForLinks="Yes">  
```  
  
 <span data-ttu-id="0781a-116">使用這項設定後，對應工具就不需要建立與目標結構描述的每個結構描述節點相關的內部編譯器節點，</span><span class="sxs-lookup"><span data-stu-id="0781a-116">With this setting, the Mapper does not need to create internal compiler nodes associated with each schema node of a target schema.</span></span> <span data-ttu-id="0781a-117">編譯器只會考慮連結的節點。</span><span class="sxs-lookup"><span data-stu-id="0781a-117">Only linked nodes are taken into account by the compiler.</span></span> <span data-ttu-id="0781a-118">如此可以在執行「測試對應」或「驗證對應」作業、編譯對應或儲存對應時，大幅降低記憶體的耗用量並加速處理程序。</span><span class="sxs-lookup"><span data-stu-id="0781a-118">This significantly reduces the memory consumption and speeds up the process when doing a "test map" or "validate map" operation, compiling the map, or saving the map.</span></span>  
  
 <span data-ttu-id="0781a-119">不過，當**GenerateDefaultFixedNodes**旗標設為**否**，目標結構描述中設定的預設欄位值不會保留在對應所產生的執行個體。</span><span class="sxs-lookup"><span data-stu-id="0781a-119">However, when the **GenerateDefaultFixedNodes** flag is set to **No**, the default field values set in the target schema are not preserved in the instance produced by the map.</span></span> <span data-ttu-id="0781a-120">這在目標執行個體需要使用這些值時，會造成問題。</span><span class="sxs-lookup"><span data-stu-id="0781a-120">This is a problem when these values are required in the target instance.</span></span> <span data-ttu-id="0781a-121">為了避免這個問題，必須在對應中再次明確地設定必要的值。</span><span class="sxs-lookup"><span data-stu-id="0781a-121">To circumvent this, the required values have to be set again explicitly in the map.</span></span> <span data-ttu-id="0781a-122">您可以設定**GenerateDefaultFixedNodes**旗標設為**RequiredDefaults**，這表示所有必要的節點都會納入考量。</span><span class="sxs-lookup"><span data-stu-id="0781a-122">You can set the **GenerateDefaultFixedNodes** flag to **RequiredDefaults**, which means that all required nodes are taken into account.</span></span> <span data-ttu-id="0781a-123">這包括連結的節點、 具有預設值的節點**MinOccurs**屬性設定為大於或等於一，且其父代所需的節點。</span><span class="sxs-lookup"><span data-stu-id="0781a-123">This covers linked nodes, nodes that have default values, nodes with the **MinOccurs** property set to greater than or equal to one, and nodes whose parents are required.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0781a-124">設定之後**GenerateDefaultFixedNodes**至**否**或**RequiredDefaults**，您應該測試對應，並確認輸出時相同**GenerateDefaultFixedNodes**設定的預設值為**是**中的所有節點都會都納入考量，編譯器。</span><span class="sxs-lookup"><span data-stu-id="0781a-124">After you set **GenerateDefaultFixedNodes** to **No** or **RequiredDefaults**, you should test the map and verify that the output is the same as when **GenerateDefaultFixedNodes** is set to its default value of **Yes**, in which all nodes are taken into account by the compiler.</span></span>  
  
## <a name="managing-for-each-usage-with-looping-conditional-and-value-mapping-functoids"></a><span data-ttu-id="0781a-125">使用迴圈、條件和值對應運算質管理 for-each 用法</span><span class="sxs-lookup"><span data-stu-id="0781a-125">Managing for-each Usage with Looping, Conditional, and Value Mapping Functoids</span></span>  
 <span data-ttu-id="0781a-126">當您使用**迴圈**運算質，**條件**運算質，或**值對應**運算質，`xsl:for-each`會產生陳述式在已編譯的對應。</span><span class="sxs-lookup"><span data-stu-id="0781a-126">When you use a **Looping** functoid, a **Conditional** functoid, or a **Value Mapping** functoid, an `xsl:for-each` statement is generated in the compiled map.</span></span> <span data-ttu-id="0781a-127">如果目的結構描述的子欄位具有未繫結的最大相符項目，則 `xsl:for-each` 陳述式會置於子欄位。</span><span class="sxs-lookup"><span data-stu-id="0781a-127">If the child field of the destination schema has unbounded maximum occurrences, the `xsl:for-each` statement is put at the child field.</span></span> <span data-ttu-id="0781a-128">如果子欄位沒有未繫結的最大相符項目，則 `xsl:for-each` 陳述式會置於子欄位的父欄位。</span><span class="sxs-lookup"><span data-stu-id="0781a-128">If the child field does not have unbounded maximum occurrences, the `xsl:for-each` statement is put at the parent field of the child field.</span></span>  
  
 <span data-ttu-id="0781a-129">不過，因為位置`xsl:for-each`陳述式會影響對應結果，您可能會想`xsl:for-each`陳述式置於目的結構描述，不論子欄位的最大相符項目設定為子欄位**1**。</span><span class="sxs-lookup"><span data-stu-id="0781a-129">However, because the location of the `xsl:for-each` statement affects the map result, you may want the `xsl:for-each` statement to be put at the child field of the destination schema, regardless of whether the maximum occurrence of the child field is set to **1**.</span></span>  
  
 <span data-ttu-id="0781a-130">您可以控制的位置`xsl:for-each`陳述式所修改的值**TreatElementsAsRecords**屬性對應 (.btm) 檔案中所示：</span><span class="sxs-lookup"><span data-stu-id="0781a-130">You can control the placement of the `xsl:for-each` statement by modifying the value of the **TreatElementsAsRecords** attribute in the map (.btm) file as shown:</span></span>  
  
```  
<mapsource Name="BizTalk Map" BizTalkServerMapperTool_Version="2.0" Version="2" XRange="100" YRange="420" OmitXmlDeclaration="Yes" TreatElementsAsRecords="No" OptimizeValueMapping="No" GenerateDefaultFixedNodes="Yes" CopyPIs="No" method="xml" xmlVersion="1.0" IgnoreNamespacesForLinks="Yes">  
```  
  
 <span data-ttu-id="0781a-131">當這個屬性設定為**是**、`xsl:for-each`陳述式會置於目的結構描述，不論子欄位的最大相符項目設定為的子欄位**1**。</span><span class="sxs-lookup"><span data-stu-id="0781a-131">When this attribute is set to **Yes**, the `xsl:for-each` statement is put at the child field of the destination schema, regardless of whether the maximum occurrence of the child field is set to **1**.</span></span>  
  
## <a name="preserving-the-order-when-mapping-a-repeating-sequence-group"></a><span data-ttu-id="0781a-132">在對應重複 Sequence 群組時保留順序</span><span class="sxs-lookup"><span data-stu-id="0781a-132">Preserving the Order When Mapping a Repeating Sequence Group</span></span>  
 <span data-ttu-id="0781a-133">XSD 結構描述中的 Sequence 群組並未提供迴內容，因為這些群組在訊息執行個體中並無代表項目。</span><span class="sxs-lookup"><span data-stu-id="0781a-133">Sequence groups in XSD schemas do not provide a looping context because they are not represented in the message instance.</span></span> <span data-ttu-id="0781a-134">由於 Sequence 群組沒有迴圈的可能性，所以對應工具編譯器並不會產生適當的 XSLT 來維持區段的順序。</span><span class="sxs-lookup"><span data-stu-id="0781a-134">Without looping possibilities on the sequence group, the Mapper compiler does not generate the appropriate XSLT to maintain the segment order.</span></span> <span data-ttu-id="0781a-135">因此，輸入執行個體中的相關內容將會遺失，而使輸出執行個體無法用於相依於相關內容的進一步處理。</span><span class="sxs-lookup"><span data-stu-id="0781a-135">As a result, relative context that is present in the input instance is lost, which makes the output instances useless for further processing that depends on the relative context.</span></span>  
  
 <span data-ttu-id="0781a-136">您可以使用**PreserveSequenceOrder**旗標來維持記錄順序，對應重複時另一個重複序列的序列。</span><span class="sxs-lookup"><span data-stu-id="0781a-136">You can use the **PreserveSequenceOrder** flag to maintain record order when mapping a repeating sequence to another repeating sequence.</span></span> <span data-ttu-id="0781a-137">根據預設，旗標的值設定為**否**保留現有的對應中稍早建立的功能[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]版本旗標不存在。</span><span class="sxs-lookup"><span data-stu-id="0781a-137">By default, the value of the flag is set to **No** to preserve the functionality of existing maps created in earlier [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] versions where the flag is not present.</span></span> <span data-ttu-id="0781a-138">新建立的對應中的旗標將會顯示其值設為**否**。</span><span class="sxs-lookup"><span data-stu-id="0781a-138">In the newly created maps, the flag will be present with its value set to **No**.</span></span> <span data-ttu-id="0781a-139">為了維持區段順序，您必須明確設定值為**是**示在.btm 檔案中：</span><span class="sxs-lookup"><span data-stu-id="0781a-139">To maintain segment order, you must explicitly set the value to **Yes** in the .btm files as shown:</span></span>  
  
```  
<mapsource Name="BizTalk Map" BizTalkServerMapperTool_Version="2.0" Version="2" XRange="100" YRange="420" OmitXmlDeclaration="Yes" TreatElementsAsRecords="No" OptimizeValueMapping="No" GenerateDefaultFixedNodes="Yes" PreserveSequenceOrder="Yes" CopyPIs="No" method="xml" xmlVersion="1.0" IgnoreNamespacesForLinks="Yes">  
```  
  
 <span data-ttu-id="0781a-140">以下為輸入執行個體範例：</span><span class="sxs-lookup"><span data-stu-id="0781a-140">The following is a sample input instance:</span></span>  
  
```  
<Name>Person1</Name>  
<Gender>Male</Gender>  
<Address>Bellevue</Address>  
<Name>Person2</Name>  
<Gender>Female</Gender>  
<Address>Redmond</Address>  
```  
  
 <span data-ttu-id="0781a-141">與**PreserveSequenceOrder**旗標設為**否**，輸出執行個體將會如下所示：</span><span class="sxs-lookup"><span data-stu-id="0781a-141">With the **PreserveSequenceOrder** flag set to **No**, the output instance will look like the following:</span></span>  
  
```  
<Name>Person1</Name>  
<Name>Person2</Name>  
<Gender>Male</Gender>  
<Gender>Female</Gender>  
<Address>Bellevue</Address>  
<Address>Redmond</Address>  
```  
  
 <span data-ttu-id="0781a-142">與**PreserveSequenceOrder**旗標設為**是**，輸出執行個體將會如下所示：</span><span class="sxs-lookup"><span data-stu-id="0781a-142">With the **PreserveSequenceOrder** flag set to **Yes**, the output instance will look like the following:</span></span>  
  
```  
<Name>Person1</Name>  
<Gender>Male</Gender>  
<Address>Bellevue</Address>  
<Name>Person2</Name>  
<Gender>Female</Gender>  
<Address>Redmond</Address>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0781a-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0781a-143">See Also</span></span>  
 [<span data-ttu-id="0781a-144">使用 BizTalk 對應工具建立對應</span><span class="sxs-lookup"><span data-stu-id="0781a-144">Creating Maps Using BizTalk Mapper</span></span>](../core/creating-maps-using-biztalk-mapper.md)