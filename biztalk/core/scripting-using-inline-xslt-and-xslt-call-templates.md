---
title: "使用內嵌 XSLT 與 XSLT 呼叫範本指令碼 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e3168417-3653-4c9e-a09c-184ffdc0ccb2
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d7c4c1d8eff582d15f9ce022053b80f2dea2f856
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="scripting-using-inline-xslt-and-xslt-call-templates"></a><span data-ttu-id="e7765-102">使用內嵌 XSLT 與 XSLT 呼叫範本的指令碼處理</span><span class="sxs-lookup"><span data-stu-id="e7765-102">Scripting Using Inline XSLT and XSLT Call Templates</span></span>
<span data-ttu-id="e7765-103">您可以直接編寫用於可延伸樣式表語言轉換 (XSLT) 樣式表**指令碼處理**運算質。</span><span class="sxs-lookup"><span data-stu-id="e7765-103">You can directly write Extensible Stylesheet Language Transformations (XSLT) stylesheets for use in the **Scripting** functoid.</span></span> <span data-ttu-id="e7765-104">如此可讓您執行轉換，而連結與內建的運算質可能不會顯示。</span><span class="sxs-lookup"><span data-stu-id="e7765-104">This enables you to perform transformations, that links and built-in functoids may not be able to represent.</span></span> <span data-ttu-id="e7765-105">XSLT 指令碼分為兩種：內嵌 XSLT 與 XSLT 呼叫範本。</span><span class="sxs-lookup"><span data-stu-id="e7765-105">There are two kinds of XSLT scripts: inline XSLT and XSLT call templates.</span></span> <span data-ttu-id="e7765-106">選取任一種**選取指令碼類型**下拉式清單中的**設定指令碼處理運算質**對話方塊中，範例程式碼會顯示您可以使用。</span><span class="sxs-lookup"><span data-stu-id="e7765-106">When you select either in the **Select script type** dropdown in the **Configure Scripting Functoid** dialog box, sample code appears that you may use.</span></span>  
  
 <span data-ttu-id="e7765-107">內嵌 XSLT 指令碼與 XSLT 呼叫範本可能呼叫外部組件中的函式。</span><span class="sxs-lookup"><span data-stu-id="e7765-107">Inline XSLT scripts and inline XSLT call templates may call functions in external assemblies.</span></span> <span data-ttu-id="e7765-108">進行這種呼叫需要設定**自訂延伸模組 XML**方格的屬性。</span><span class="sxs-lookup"><span data-stu-id="e7765-108">Making such calls requires setting the **Custom Extension XML** property of the grid.</span></span> <span data-ttu-id="e7765-109">如需詳細資訊，請參閱**自訂延伸模組 XML （格線屬性）** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="e7765-109">For more information, see **Custom Extension XML (Grid Property)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
## <a name="inline-xslt"></a><span data-ttu-id="e7765-110">內嵌 XSLT</span><span class="sxs-lookup"><span data-stu-id="e7765-110">Inline XSLT</span></span>  
 <span data-ttu-id="e7765-111">內嵌 XSLT 指令碼可能只產生輸出。</span><span class="sxs-lookup"><span data-stu-id="e7765-111">An inline XSLT script may only produce output.</span></span> <span data-ttu-id="e7765-112">**指令碼處理**運算質可能沒有任何輸入的連結。</span><span class="sxs-lookup"><span data-stu-id="e7765-112">The **Scripting** functoid may not have any input links.</span></span> <span data-ttu-id="e7765-113">運算質還必須直接連結到目的結構描述中的記錄或欄位。</span><span class="sxs-lookup"><span data-stu-id="e7765-113">The functoid must also directly link to a record or field in the destination schema.</span></span>  
  
 <span data-ttu-id="e7765-114">此外，指令碼還負責建立目標節點及其之下的任何結構。</span><span class="sxs-lookup"><span data-stu-id="e7765-114">In addition, the script is responsible for creating the target node and any structures underneath it.</span></span>  
  
 <span data-ttu-id="e7765-115">下列輸入執行個體訊息包含代表連絡資訊的兩個項目。</span><span class="sxs-lookup"><span data-stu-id="e7765-115">The following input instance message contains two elements representing contact information.</span></span>  
  
```  
<ns0:SourceInstance xmlns:ns0="http://SourceInstanceNamespace">  
    <Address>  
        <Contact>Karin Zimprich</Contact>  
        <ContactType>Referral</ContactType>  
    </Address>  
</ns0:SourceInstance>  
```  
  
 <span data-ttu-id="e7765-116">下列內嵌 XSLT 指令碼，在指令碼緩衝區中，輸入將轉換**連絡人**和**ContactType**屬性的欄位。</span><span class="sxs-lookup"><span data-stu-id="e7765-116">The following inline XSLT script, entered in the script buffer, converts the **Contact** and **ContactType** fields to attributes.</span></span>  
  
```  
<ContactInfo xmlns:p="http://SourceInstanceNamespace">  
     <xsl:variable name="var:var1" select="/p:SourceInstance/Address/ContactType" />  
     <xsl:attribute name="ContactType">  
          <xsl:value-of select="$var:var1" />  
     </xsl:attribute>  
     <xsl:variable name="var:var2" select="/p:SourceInstance/Address/Contact" />  
     <xsl:attribute name="Contact">  
          <xsl:value-of select="$var:var2" />  
     </xsl:attribute>  
</ContactInfo>  
```  
  
 <span data-ttu-id="e7765-117">在針對先前的輸入執行個體訊息執行時，此指令碼產生下列輸出 (假設為適當的輸出結構描述)。</span><span class="sxs-lookup"><span data-stu-id="e7765-117">The script produces the following output, assuming an appropriate output schema, when run against the preceding input instance message.</span></span>  
  
```  
<ns0:OutInstance xmlns:ns0="http://More_XSLT.Out">  
    <ContactInfo ContactType="Referral" Contact="Karin Zimprich" xmlns:p="http://SourceInstanceNamespace">  
    </ContactInfo>  
</ns0:OutInstance>  
```  
  
 <span data-ttu-id="e7765-118">請注意，缺少連結**指令碼處理**運算質不會防止 XSLT 指令碼從輸入執行個體訊息中取得資料。</span><span class="sxs-lookup"><span data-stu-id="e7765-118">Notice that the absence of links to the **Scripting** functoid does not prevent the XSLT script from getting data from the input instance message.</span></span> <span data-ttu-id="e7765-119">此指令碼指定輸入執行個體值的路徑。</span><span class="sxs-lookup"><span data-stu-id="e7765-119">The script specifies paths to the input instance values.</span></span>  
  
 <span data-ttu-id="e7765-120">如需內嵌 XSLT 指令碼的其他範例，請參閱[（BizTalk Server 範例資料夾） 的 XML 工具](../core/xml-tools-biztalk-server-samples-folder.md)。</span><span class="sxs-lookup"><span data-stu-id="e7765-120">For another example of an inline XSLT script, see [XML Tools (BizTalk Server Samples Folder)](../core/xml-tools-biztalk-server-samples-folder.md).</span></span>  
  
## <a name="inline-xslt-call-templates"></a><span data-ttu-id="e7765-121">內嵌 XSLT 呼叫範本</span><span class="sxs-lookup"><span data-stu-id="e7765-121">Inline XSLT Call Templates</span></span>  
 <span data-ttu-id="e7765-122">與內嵌 XSLT 指令碼類似，內嵌 XSLT 呼叫範本必須直接連接到目的節點。</span><span class="sxs-lookup"><span data-stu-id="e7765-122">Like an inline XSLT script, an inline XSLT call template must connect directly to a destination node.</span></span> <span data-ttu-id="e7765-123">不過，內嵌 XSLT 呼叫範本可能使用來源結構描述與其他運算質的連結。</span><span class="sxs-lookup"><span data-stu-id="e7765-123">However, an inline XSLT call template may use links from the source schema and from other functoids.</span></span>  
  
 <span data-ttu-id="e7765-124">呼叫範本還負責建立目的節點及其任何子結構。</span><span class="sxs-lookup"><span data-stu-id="e7765-124">The call template is responsible for creating the destination node and any of its substructures.</span></span>  
  
 <span data-ttu-id="e7765-125">串連兩個項目的範例 XSLT 呼叫範本會出現在**輸入指令碼**緩衝處理，當您選取**內嵌 XSLT 呼叫範本**中**選取指令碼類型**在下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="e7765-125">A sample XSLT call template that concatenates two elements appears in the **Input script** buffer when you select **Inline XSLT Call Template** in the **Select script type** dropdown.</span></span>  
  
 <span data-ttu-id="e7765-126">如需內嵌 XSLT 呼叫範本的其他範例，請參閱[（BizTalk Server 範例資料夾） 的 XML 工具](../core/xml-tools-biztalk-server-samples-folder.md)。</span><span class="sxs-lookup"><span data-stu-id="e7765-126">For another example of an inline XSLT call template, see [XML Tools (BizTalk Server Samples Folder)](../core/xml-tools-biztalk-server-samples-folder.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7765-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e7765-127">See Also</span></span>  
 <span data-ttu-id="e7765-128">[指令碼處理運算質](../core/scripting-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="e7765-128">[Scripting Functoid](../core/scripting-functoid.md) </span></span>  
 <span data-ttu-id="e7765-129">[使用外部組件指令碼](../core/scripting-using-external-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="e7765-129">[Scripting Using External Assemblies](../core/scripting-using-external-assemblies.md) </span></span>  
 <span data-ttu-id="e7765-130">[使用內嵌 C#、 JScript.NET 和 Visual Basic.NET 指令碼](../core/scripting-using-inline-csharp-jscript-net-and-visual-basic-net.md) </span><span class="sxs-lookup"><span data-stu-id="e7765-130">[Scripting Using Inline C#, JScript .NET, and Visual Basic .NET](../core/scripting-using-inline-csharp-jscript-net-and-visual-basic-net.md) </span></span>  
 <span data-ttu-id="e7765-131">[如何新增指令碼運算質至對應](../core/how-to-add-scripting-functoids-to-a-map.md) </span><span class="sxs-lookup"><span data-stu-id="e7765-131">[How to Add Scripting Functoids to a Map](../core/how-to-add-scripting-functoids-to-a-map.md) </span></span>  
 [<span data-ttu-id="e7765-132">How to Configure the Scripting Functoid</span><span class="sxs-lookup"><span data-stu-id="e7765-132">How to Configure the Scripting Functoid</span></span>](../core/how-to-configure-the-scripting-functoid.md)