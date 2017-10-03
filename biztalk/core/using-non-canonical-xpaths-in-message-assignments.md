---
title: "訊息指派中使用非標準 Xpath |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 052d1d72-43ce-4654-bf29-86f82ad65e91
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 201d6f8b6bc910faf79b64ac0b4617530b20608a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-non-canonical-xpaths-in-message-assignments"></a>在訊息指派中使用非標準 XPath
如果您使用 .Net 訊息部分，您的程式碼可以使用 XML 序列化屬性加以附註，當伴隨著辨別欄位和/或屬性附註時，將產生相當複雜 XPath 運算式。 這些複雜的 XPath 運算式可能是非標準的運算式。 非標準 XPath 只能在直接繫結協調流程中使用，並且可能在邏輯或實際繫結協調流程中失敗。 直接繫結協調流程並不依賴管線來處理 XML 文件，因此整個 XML 文件會在處理之前載入記憶體。  
  
## <a name="canonical-and-non-canonical-xpath"></a>標準和非標準 XPath  
 標準或簡短格式的 XPath 使用 XPath 規格的縮寫的語法 ([http://www.w3.org/TR/xpath](http://go.microsoft.com/fwlink/?LinkId=119567)) 指定的位置路徑。 部分標準 XPath 運算式的辨別屬性如下：  
  
-   運算式的每個步驟預設採用 `child::` 座標軸  
  
-   `@` 是 `attribute::` 的簡式。  
  
-   `//` 是 `/descendant-or-self::node()/` 的簡式。  
  
-   `.` 是 `self::node()` 的簡式。  
  
-   `..` 是 `parent::node()` 的簡式。  
  
 標準 XPath 運算式是簡單的運算式，例如 `/*[local-name()='element-name' and namespaceURI()='http://MyUri.org']/*[local-name()='element-name']/@*[local-name='attribute-name']`。  
  
 您可以將此運算式對照 XPath 的非標準格式。 此表單就是所謂的 「 一般格式 」 或 「 任意 XPath 」，並區分由任意複雜且可結合多個軸的運算式： `//element-name//*[local-name()='element-name' and position()=2]`。  
  
## <a name="example"></a>範例  
 請考慮下列程式：  
  
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
  
 Zoo 類型包含 Animal 欄位，可能是 Snake 或 Dog。 Animal 執行個體具有由 PropertyAttribute 附註的 NumberOfLegs 欄位，而 PropertyAttribute 指派 BTS.RetryCount 屬性給此欄位。  
  
> [!NOTE]
>  實際的應用程式將會定義其本身的屬性。  
  
 當每週的代表動物是狗時，序列化的 Zoo 執行個體會像這樣：  
  
```  
<Zoo>  
  <Dog>  
    <NumberOfLegs>4</NumberOfLegs>  
  </Dog>  
</Zoo>   
```  
  
 當每週的代表動物是蛇時，序列化的 Zoo 執行個體會像這樣：  
  
```  
<Zoo>  
  <Snake>  
    <NumberOfLegs>0</NumberOfLegs>  
  </Snake>  
</Zoo>  
```  
  
 因為 XML 結構描述等同 .Net Zoo 類別，用於選取 RetryCount 屬性的 XPath 運算式允許讓 Snake 或 Dog 步驟在屬性的路徑上出現：  
  
```  
/*[local-name()='Zoo' and namespace-uri()='']/*[(local-name()='Dog' and namespace-uri()='') or (local-name()='Snake' and namespace-uri()='')]/*[local-name()='NumberOfLegs' and namespace-uri()='']  
```  
  
 XML 管線元件無法處理這個非標準 XPath 運算式。 若要避免這種情況，就不應該搭配 XML 管線使用多重選擇的 XML 序列化屬性，並且在使用下列 XML 序列化屬性時，還要多加小心：  
  
-   XmlElementAttribute  
  
-   XmlAttributeAttribute  
  
-   XmlArrayItemAttribute