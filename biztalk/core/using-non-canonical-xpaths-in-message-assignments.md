---
title: 訊息指派中使用非標準 Xpath |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 052d1d72-43ce-4654-bf29-86f82ad65e91
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 201d6f8b6bc910faf79b64ac0b4617530b20608a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22287622"
---
# <a name="using-non-canonical-xpaths-in-message-assignments"></a><span data-ttu-id="c688a-102">在訊息指派中使用非標準 XPath</span><span class="sxs-lookup"><span data-stu-id="c688a-102">Using Non-Canonical XPaths in Message Assignments</span></span>
<span data-ttu-id="c688a-103">如果您使用 .Net 訊息部分，您的程式碼可以使用 XML 序列化屬性加以附註，當伴隨著辨別欄位和/或屬性附註時，將產生相當複雜 XPath 運算式。</span><span class="sxs-lookup"><span data-stu-id="c688a-103">If you use .Net message parts, it is possible to annotate your code with the XML serialization attribute that, when also accompanied by distinguished fields and/or property annotations, can result in fairly complex XPath expressions.</span></span> <span data-ttu-id="c688a-104">這些複雜的 XPath 運算式可能是非標準的運算式。</span><span class="sxs-lookup"><span data-stu-id="c688a-104">It is possible that these complex XPath expressions will be non-canonical.</span></span> <span data-ttu-id="c688a-105">非標準 XPath 只能在直接繫結協調流程中使用，並且可能在邏輯或實際繫結協調流程中失敗。</span><span class="sxs-lookup"><span data-stu-id="c688a-105">Non-canonical XPath should only be used in direct bound orchestrations and may fail with logically or physically bound orchestrations.</span></span> <span data-ttu-id="c688a-106">直接繫結協調流程並不依賴管線來處理 XML 文件，因此整個 XML 文件會在處理之前載入記憶體。</span><span class="sxs-lookup"><span data-stu-id="c688a-106">Direct bound orchestrations do not rely on a pipeline for processing the XML document; as a result, the entire XML document is loaded in memory prior to processing.</span></span>  
  
## <a name="canonical-and-non-canonical-xpath"></a><span data-ttu-id="c688a-107">標準和非標準 XPath</span><span class="sxs-lookup"><span data-stu-id="c688a-107">Canonical and Non-Canonical XPath</span></span>  
 <span data-ttu-id="c688a-108">標準或簡短格式的 XPath 使用 XPath 規格的縮寫的語法 ([http://www.w3.org/TR/xpath](http://go.microsoft.com/fwlink/?LinkId=119567)) 指定的位置路徑。</span><span class="sxs-lookup"><span data-stu-id="c688a-108">The canonical or short-form of XPath uses the abbreviated syntax from the XPath specification ([http://www.w3.org/TR/xpath](http://go.microsoft.com/fwlink/?LinkId=119567)) to specify a location path.</span></span> <span data-ttu-id="c688a-109">部分標準 XPath 運算式的辨別屬性如下：</span><span class="sxs-lookup"><span data-stu-id="c688a-109">Some distinguishing properties of canonical XPath expressions include:</span></span>  
  
-   <span data-ttu-id="c688a-110">運算式的每個步驟預設採用 `child::` 座標軸</span><span class="sxs-lookup"><span data-stu-id="c688a-110">The `child::` axis is assumed by default for each step of the expression</span></span>  
  
-   <span data-ttu-id="c688a-111">`@` 是 `attribute::` 的簡式。</span><span class="sxs-lookup"><span data-stu-id="c688a-111">`@` is short for `attribute::`.</span></span>  
  
-   <span data-ttu-id="c688a-112">`//` 是 `/descendant-or-self::node()/` 的簡式。</span><span class="sxs-lookup"><span data-stu-id="c688a-112">`//` is short for `/descendant-or-self::node()/`.</span></span>  
  
-   <span data-ttu-id="c688a-113">`.` 是 `self::node()` 的簡式。</span><span class="sxs-lookup"><span data-stu-id="c688a-113">`.` is short for `self::node()`.</span></span>  
  
-   <span data-ttu-id="c688a-114">`..` 是 `parent::node()` 的簡式。</span><span class="sxs-lookup"><span data-stu-id="c688a-114">`..` is short for `parent::node()`.</span></span>  
  
 <span data-ttu-id="c688a-115">標準 XPath 運算式是簡單的運算式，例如 `/*[local-name()='element-name' and namespaceURI()='http://MyUri.org']/*[local-name()='element-name']/@*[local-name='attribute-name']`。</span><span class="sxs-lookup"><span data-stu-id="c688a-115">Canonical XPath expressions are simple expressions such as `/*[local-name()='element-name' and namespaceURI()='http://MyUri.org']/*[local-name()='element-name']/@*[local-name='attribute-name']`.</span></span>  
  
 <span data-ttu-id="c688a-116">您可以將此運算式對照 XPath 的非標準格式。</span><span class="sxs-lookup"><span data-stu-id="c688a-116">This can be contrasted with the non-canonical form of XPath.</span></span> <span data-ttu-id="c688a-117">此表單就是所謂的 「 一般格式 」 或 「 任意 XPath 」，並區分由任意複雜且可結合多個軸的運算式： `//element-name//*[local-name()='element-name' and position()=2]`。</span><span class="sxs-lookup"><span data-stu-id="c688a-117">This form is also known as the "general form" or "arbitrary XPath" and is distinguished by expressions that are arbitrarily complex and may combine multiple axes: `//element-name//*[local-name()='element-name' and position()=2]`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c688a-118">範例</span><span class="sxs-lookup"><span data-stu-id="c688a-118">Example</span></span>  
 <span data-ttu-id="c688a-119">請考慮下列程式：</span><span class="sxs-lookup"><span data-stu-id="c688a-119">Consider the following program:</span></span>  
  
```  
using System;  
using System.IO;  
using System.Xml.Serialization;  
using Microsoft.XLANGs.BaseTypes;  
  
namespace ComplexNetXPath  
{  
    public class Animal  
    {  
        [Property( typeof(BTS.RetryCount) )]  
        public int NumberOfLegs;  
    }   
    public class Snake : Animal  
    {  
        public Snake()  
        {  
            NumberOfLegs = 0;  
        }  
    }   
    public class Dog : Animal  
    {  
        public Dog()  
        {  
            NumberOfLegs = 4;  
        }  
    }   
    public class Zoo  
    {  
        //  
        // Dogs and snakes are the possible animals of  
        // the week.  
        //  
        [XmlElement(typeof(Snake))]  
        [XmlElement(typeof(Dog))]  
        public Animal AnimalOfTheWeek;  
    }  
    class Class1  
    {  
        static void Main(string[] args)  
        {  
            XmlSerializer ser = new XmlSerializer(typeof(Zoo));  
            Stream s = Console.OpenStandardOutput();  
            Zoo z = new Zoo();  
            z.AnimalOfTheWeek = new Dog();  
            ser.Serialize( s, z );  
            s.Flush();  
            Console.WriteLine("------------------");  
            z.AnimalOfTheWeek = new Snake();  
            ser.Serialize( s, z );  
            s.Flush();  
        }  
    }  
}   
```  
  
 <span data-ttu-id="c688a-120">Zoo 類型包含 Animal 欄位，可能是 Snake 或 Dog。</span><span class="sxs-lookup"><span data-stu-id="c688a-120">The Zoo type contains an Animal field that may be either a Snake or a Dog.</span></span> <span data-ttu-id="c688a-121">Animal 執行個體具有由 PropertyAttribute 附註的 NumberOfLegs 欄位，而 PropertyAttribute 指派 BTS.RetryCount 屬性給此欄位。</span><span class="sxs-lookup"><span data-stu-id="c688a-121">The Animal instance has a NumberOfLegs field that is annotated with the PropertyAttribute which assigns the BTS.RetryCount property to this field.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c688a-122">實際的應用程式將會定義其本身的屬性。</span><span class="sxs-lookup"><span data-stu-id="c688a-122">A real application would define its own properties.</span></span>  
  
 <span data-ttu-id="c688a-123">當每週的代表動物是狗時，序列化的 Zoo 執行個體會像這樣：</span><span class="sxs-lookup"><span data-stu-id="c688a-123">When the animal of the week is a dog, the serialized Zoo instance looks like this:</span></span>  
  
```  
<Zoo>  
  <Dog>  
    <NumberOfLegs>4</NumberOfLegs>  
  </Dog>  
</Zoo>   
```  
  
 <span data-ttu-id="c688a-124">當每週的代表動物是蛇時，序列化的 Zoo 執行個體會像這樣：</span><span class="sxs-lookup"><span data-stu-id="c688a-124">When the animal of the week is a snake, the serialized Zoo instance looks like this:</span></span>  
  
```  
<Zoo>  
  <Snake>  
    <NumberOfLegs>0</NumberOfLegs>  
  </Snake>  
</Zoo>  
```  
  
 <span data-ttu-id="c688a-125">因為 XML 結構描述等同 .Net Zoo 類別，用於選取 RetryCount 屬性的 XPath 運算式允許讓 Snake 或 Dog 步驟在屬性的路徑上出現：</span><span class="sxs-lookup"><span data-stu-id="c688a-125">Considering the Xml schema equivalent to the .Net Zoo class, the XPath expression for selecting the RetryCount property would allow for either a Snake or a Dog step to appear on the path to the property:</span></span>  
  
```  
/*[local-name()='Zoo' and namespace-uri()='']/*[(local-name()='Dog' and namespace-uri()='') or (local-name()='Snake' and namespace-uri()='')]/*[local-name()='NumberOfLegs' and namespace-uri()='']  
```  
  
 <span data-ttu-id="c688a-126">XML 管線元件無法處理這個非標準 XPath 運算式。</span><span class="sxs-lookup"><span data-stu-id="c688a-126">The XML pipeline components cannot handle this non-canonical XPath expression.</span></span> <span data-ttu-id="c688a-127">若要避免這種情況，就不應該搭配 XML 管線使用多重選擇的 XML 序列化屬性，並且在使用下列 XML 序列化屬性時，還要多加小心：</span><span class="sxs-lookup"><span data-stu-id="c688a-127">To avoid this situation, multiple-choice Xml serialization attributes should not be used in conjunction with the XML pipelines and care should be taken when using the following xml serialization attributes:</span></span>  
  
-   <span data-ttu-id="c688a-128">XmlElementAttribute</span><span class="sxs-lookup"><span data-stu-id="c688a-128">XmlElementAttribute</span></span>  
  
-   <span data-ttu-id="c688a-129">XmlAttributeAttribute</span><span class="sxs-lookup"><span data-stu-id="c688a-129">XmlAttributeAttribute</span></span>  
  
-   <span data-ttu-id="c688a-130">XmlArrayItemAttribute</span><span class="sxs-lookup"><span data-stu-id="c688a-130">XmlArrayItemAttribute</span></span>