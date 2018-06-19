---
title: 實作管線元件中的字元編碼方式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- pipeline components [custom], examples
- pipeline components [custom], code samples
- pipeline components [custom], encoding
ms.assetid: 862b56da-ec14-41f9-b63c-42d81124e167
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a1bc95dc44fa4a4905affaad969c248aa4b76d89
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22257046"
---
# <a name="implementing-character-encoding-in-a-pipeline-component"></a><span data-ttu-id="b78ce-102">實作管線元件中的字元編碼方式</span><span class="sxs-lookup"><span data-stu-id="b78ce-102">Implementing Character Encoding in a Pipeline Component</span></span>
<span data-ttu-id="b78ce-103">若要支援自訂字元編碼方式，您必須實作自訂編碼類別，藉由衍生自 Microsoft.NET Framework**編碼**類別，然後從標準一般繼承來建立自訂的一般檔案管線元件檔案解譯器 」 或 「 一般檔案組合器元件。</span><span class="sxs-lookup"><span data-stu-id="b78ce-103">To support custom character encoding, you must implement a custom encoding class by deriving from the Microsoft .NET Framework **Encoding** class, then create a custom flat file pipeline component by inheriting from the standard Flat File Disassembler or Flat File Assembler component.</span></span> <span data-ttu-id="b78ce-104">您可以藉由覆寫的受保護的虛擬方法提供新的編碼執行個體剖析引擎**FFDasmComp.GetDataReader**如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="b78ce-104">You can supply a new encoding instance to the parsing engine by overriding the protected virtual method **FFDasmComp.GetDataReader** as shown in the following example.</span></span>  
  
```  
/// <summary>  
/// Gets a data reader instance  
/// </summary>  
/// <param name="dataStream">Data stream</param>  
/// <param name="dataEncoding">Data encoding</param>  
/// <param name="detectEncodingFromByteOrderMarks">Detect encoding from a byte order mark</param>  
/// <returns>IDataReader instance</returns>  
      protected override IDataReader GetDataReader(Stream dataStream, Encoding dataEncoding, bool detectEncodingFromByteOrderMarks)  
      {  
         // Delegate call to the base implementation passing fixed UTF-7 encoding  
         return base.GetDataReader(dataStream, new CustomEncoding(), false);  
      }  
```  
  
## <a name="using-predefined-encoding-classes"></a><span data-ttu-id="b78ce-105">使用預先定義的編碼類別</span><span class="sxs-lookup"><span data-stu-id="b78ce-105">Using predefined encoding classes</span></span>  
 <span data-ttu-id="b78ce-106">下列編碼類型是由 Microsoft .NET Framework 所預先定義，而且可用來建構剖析器：</span><span class="sxs-lookup"><span data-stu-id="b78ce-106">The following encoding types are predefined by the Microsoft .NET Framework and can be used to construct the parser:</span></span>  
  
-   <span data-ttu-id="b78ce-107">ASCII</span><span class="sxs-lookup"><span data-stu-id="b78ce-107">ASCII</span></span>  
  
-   <span data-ttu-id="b78ce-108">UTF7</span><span class="sxs-lookup"><span data-stu-id="b78ce-108">UTF7</span></span>  
  
-   <span data-ttu-id="b78ce-109">UTF8</span><span class="sxs-lookup"><span data-stu-id="b78ce-109">UTF8</span></span>  
  
-   <span data-ttu-id="b78ce-110">Unicode (UTF16)</span><span class="sxs-lookup"><span data-stu-id="b78ce-110">Unicode (UTF16)</span></span>  
  
```  
XmlReader xr = docspec.Parse(new DataReader(System.Text.Encoding.UTF8));  
```  
  
## <a name="using-supported-code-pages"></a><span data-ttu-id="b78ce-111">使用支援的字碼頁</span><span class="sxs-lookup"><span data-stu-id="b78ce-111">Using supported code pages</span></span>  
 <span data-ttu-id="b78ce-112">使用下列程式碼可支援 Shift-JIS (字碼頁 932)。</span><span class="sxs-lookup"><span data-stu-id="b78ce-112">Use the following code to support Shift-JIS (codepage 932).</span></span>  
  

```  
XmlReader xr = docspec.Parse(new DataReader(System.Text.Encoding.GetEncoding(932)));  
```  
  
## <a name="using-a-private-encoding-class"></a><span data-ttu-id="b78ce-113">使用私用編碼類別</span><span class="sxs-lookup"><span data-stu-id="b78ce-113">Using a private encoding class</span></span>  
 <span data-ttu-id="b78ce-114">您可以建立您自己的編碼類別衍生自**System.Text.Encoding**抽象類別，並執行您自己編碼和解碼。</span><span class="sxs-lookup"><span data-stu-id="b78ce-114">You can create your own encoding class that derives from the **System.Text.Encoding** abstract class and perform your own encoding and decoding.</span></span>  
  
```  
class MyEncoding : System.Text.Encoding  
{  
   // overriding methods omitted  
}  
  
XmlReader xr = docspec.Parser(new DataReader(new MyEncoding()));  
```  
  
## <a name="using-a-private-datareader-class"></a><span data-ttu-id="b78ce-115">使用私用 DataReader 類別</span><span class="sxs-lookup"><span data-stu-id="b78ce-115">Using a private DataReader class</span></span>  

 <span data-ttu-id="b78ce-116">您可以建立自己[DataReader](https://msdn.microsoft.com/library/microsoft.biztalk.parsingengine.datareader.aspx)類別可實作`IDataReader`介面並執行讀取，而不建立任何編碼類別。</span><span class="sxs-lookup"><span data-stu-id="b78ce-116">You can create your own [DataReader](https://msdn.microsoft.com/library/microsoft.biztalk.parsingengine.datareader.aspx) class that implements the `IDataReader` interface and performs reading without creating any encoding classes.</span></span>  
  
```  
class MyDataReader : IDataReader  
{  
   // Implement data reader functions  
   // ...  
}  
  
XmlReader xr = docspec.Parse(new MyDataReader());  
```  
  
## <a name="see-also"></a><span data-ttu-id="b78ce-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b78ce-117">See Also</span></span>  
 [<span data-ttu-id="b78ce-118">使用剖析和序列化引擎</span><span class="sxs-lookup"><span data-stu-id="b78ce-118">Using the Parsing and Serializing Engines</span></span>](../core/using-the-parsing-and-serializing-engines.md)