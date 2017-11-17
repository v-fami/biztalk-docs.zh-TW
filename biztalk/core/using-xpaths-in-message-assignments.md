---
title: "訊息指派中使用 Xpath |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XPaths, XPath function
- XPaths, messages
- code samples, XPaths
- messages, XPaths
- XPath function
- XPaths, code samples
- XPaths, nodes
ms.assetid: f2e12409-bb77-4315-b03b-5c7736ae51d5
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d9ec1e5b56f382601c79324df8651c91c483cb4a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-xpaths-in-message-assignments"></a><span data-ttu-id="acc56-102">訊息指派中使用 Xpath</span><span class="sxs-lookup"><span data-stu-id="acc56-102">Using XPaths in Message Assignments</span></span>
<span data-ttu-id="acc56-103">您可以使用**xpath**函式將 XPath 值指派至訊息部分，或將值指派給參考訊息部分的 XPath。</span><span class="sxs-lookup"><span data-stu-id="acc56-103">You can use the **xpath** function to assign an XPath value to a message part, or to assign a value to an XPath that refers to a message part.</span></span> <span data-ttu-id="acc56-104">如需有關將指派給訊息和訊息部分的詳細資訊，請參閱[建構訊息](../core/constructing-messages.md)。</span><span class="sxs-lookup"><span data-stu-id="acc56-104">For more information on assigning to messages and message parts, see [Constructing Messages](../core/constructing-messages.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="acc56-105">如需 xpath 函式的詳細資訊，請參閱 XML 路徑語言 (XPath) 的協力廠商文件。</span><span class="sxs-lookup"><span data-stu-id="acc56-105">For more information on the xpath function, see third-party documentation on the XML Path Language (XPath).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="acc56-106">使用**xpath**函式並不限於訊息指派。</span><span class="sxs-lookup"><span data-stu-id="acc56-106">The use of the **xpath** function is not limited to message assignment.</span></span> <span data-ttu-id="acc56-107">您也可以將它用於任何運算式，例如：</span><span class="sxs-lookup"><span data-stu-id="acc56-107">You can also use it in any expression, for example:</span></span>  
  
```  
If ((System.Double) xpath(_RequestMessage.part, "number(//book[last()]/price)") == 75.00 && (System.Boolean) xpath(msgBoolean, "string(//boolean)") == false)...  
```  
  
> [!NOTE]
>  <span data-ttu-id="acc56-108">如果想要將值指派給字串，請使用 XPath string() 函式。</span><span class="sxs-lookup"><span data-stu-id="acc56-108">If you want to assign a value to a string, use the XPath string() function.</span></span> <span data-ttu-id="acc56-109">例如：</span><span class="sxs-lookup"><span data-stu-id="acc56-109">For example:</span></span>  
  
```  
myString = xpath(msg, "string(/*/book[1]/title)");  
```  
  
> [!NOTE]
>  <span data-ttu-id="acc56-110">引擎並非結構描述感知，所以您只能從包含節點的訊息中 (必須有完整的路徑)，從節點讀取值或將值寫入至節點，否則引擎會引發例外狀況。</span><span class="sxs-lookup"><span data-stu-id="acc56-110">The engine is not schema-aware, so you can only read values from or write values to a node that exists in the containing message (the complete path must exist), or the engine will raise an exception.</span></span> <span data-ttu-id="acc56-111">即使提供預設值，這種情況還是會發生。</span><span class="sxs-lookup"><span data-stu-id="acc56-111">This is true even if you supply a default value.</span></span>  
  
## <a name="assigning-to-an-xpath-in-a-message-part"></a><span data-ttu-id="acc56-112">指派至訊息部分中的 XPath</span><span class="sxs-lookup"><span data-stu-id="acc56-112">Assigning to an XPath in a message part</span></span>  
 <span data-ttu-id="acc56-113">請參考下列結構描述：</span><span class="sxs-lookup"><span data-stu-id="acc56-113">Consider the following schema:</span></span>  
  
```  
<?xml version="1.0" encoding="utf-16"?>  
<xs:schema xmlns:b="http://schemas.microsoft.com/BizTalk/2003" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:element name="catalog">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element minOccurs="1" maxOccurs="unbounded" name="book">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="title" type="xs:string" />  
              <xs:element name="author">  
                <xs:complexType>  
                  <xs:sequence>  
                    <xs:element name="FirstName" type="xs:string" />  
                    <xs:element name="LastName" type="xs:string" />  
                  </xs:sequence>  
                </xs:complexType>  
              </xs:element>  
              <xs:element name="price" type="xs:string" />  
            </xs:sequence>  
            <xs:attribute name="country" type="xs:string" />  
          </xs:complexType>  
        </xs:element>  
      </xs:sequence>  
    </xs:complexType>  
  </xs:element>  
</xs:schema>  
```  
  
 <span data-ttu-id="acc56-114">您可以使用下列函式，在該結構描述類型的文件執行個體上設定值。</span><span class="sxs-lookup"><span data-stu-id="acc56-114">You can use the  function as follows to set values on a document instance of that schema type:</span></span>  
  
```  
//assumes that a message named _ResponseMessage is already constructed  
_ResponseMessage.part = _RequestMessage.part;  
xpath(_ResponseMessage.part, "/*/book[1]/@country") = "USA";  
xpath(_ResponseMessage.part, "/*/book[1]/title") = "Legends";  
xpath(_ResponseMessage.part, "/*/book[1]/author/FirstName") = "A";  
xpath(_ResponseMessage.part, "/*/book[1]/author/LastName") = "B";  
xpath(_ResponseMessage.part, "/*/book[1]/price") = 50;  
```  
  
## <a name="assigning-to-a-message-part-from-an-xpath"></a><span data-ttu-id="acc56-115">從 XPath 指派至訊息部分</span><span class="sxs-lookup"><span data-stu-id="acc56-115">Assigning to a message part from an XPath</span></span>  
  
```  
//assumes that a message named objMessage is already constructed  
objMessage.BooleanPart = xpath("false()");  
objMessage.IntPart = xpath("100");  
objMessage.StringPart = xpath("'Hello'");  
objMessage.StringPart2 = xpath("'World'");  
```  
  
## <a name="using-xpath-to-assign-from-nodes-and-node-sets"></a><span data-ttu-id="acc56-116">使用 XPath 從節點和節點組合進行指派</span><span class="sxs-lookup"><span data-stu-id="acc56-116">Using XPath to assign from nodes and node sets</span></span>  
 <span data-ttu-id="acc56-117">您也可以使用 XPath，將 XML 節點和節點組合指派至 XML 項目、類別或以結構描述為基礎或以類別為基礎的訊息。</span><span class="sxs-lookup"><span data-stu-id="acc56-117">You can also use XPath to assign XML nodes and node sets to an XML element, a class, or a schema-based or class-based message.</span></span>  
  
 <span data-ttu-id="acc56-118">假設您有稱為 Book 的 XML 可序列化的類別，請考慮下列的範例：</span><span class="sxs-lookup"><span data-stu-id="acc56-118">Suppose you have an XML-serializable class called Book, and consider the following examples:</span></span>  
  
```  
[Serializable]  
Class Book {...}  
```  
  
 <span data-ttu-id="acc56-119">範例一：從目錄選取第四個 book 項目，然後將它指派給 XML 項目變數：</span><span class="sxs-lookup"><span data-stu-id="acc56-119">Example One — select the fourth book element from the catalog, and assign it to an XML element variable:</span></span>  
  
```  
myXmlElement = xpath(myMsg, "/catalog/book[3]");  
```  
  
 <span data-ttu-id="acc56-120">範例二：從目錄選取第四個 book 項目，然後使用 XML 序列化將它轉換為 Book 類別執行個體：</span><span class="sxs-lookup"><span data-stu-id="acc56-120">Example Two — select the fourth book element from the catalog, and convert it using XML deserialization into a Book class instance:</span></span>  
  
```  
myBook = xpath(myMsg, "/catalog/book[3]");  
```  
  
 <span data-ttu-id="acc56-121">範例三：從目錄選取第四個 book 項目，然後將它轉換為型別 Book 的訊息：</span><span class="sxs-lookup"><span data-stu-id="acc56-121">Example Three — select the fourth book element from the catalog, and convert it a message of type Book:</span></span>  
  
```  
myBookMsg = xpath(myMsg, "/catalog/book[3]");  
```  
  
 <span data-ttu-id="acc56-122">範例四：選取目錄中的所有 book 項目，其中 MyMethod 會使用 XmlNodeSet 做為參數：</span><span class="sxs-lookup"><span data-stu-id="acc56-122">Example Four — select all book elements in the catalog, where MyMethod takes an XmlNodeSet as a parameter:</span></span>  
  
```  
MyMethod(xpath(myMsg, "/catalog/book"));  
```  
  
 <span data-ttu-id="acc56-123">範例五：將 book 項目新增至 "BookOfTheMonth" 容器：</span><span class="sxs-lookup"><span data-stu-id="acc56-123">Example Five — add a book element to the "BookOfTheMonth" container:</span></span>  
  
```  
xpath(MyMsg2, "/RecommendedBooks/BookOfTheMonth") = myBook;  
```  
  
 <span data-ttu-id="acc56-124">範例六：將定價為 20 或更低的所有書籍新增至一組推薦的書籍：</span><span class="sxs-lookup"><span data-stu-id="acc56-124">Example Six — add all books that are priced at twenty or less to a set of recommended books:</span></span>  
  
```  
xpath(MyMsg2, "/RecommendedBooks/BestPriceBooks") = xpath(MyMsg, "/catalog/book[@price <= 20]");  
```  
  
 <span data-ttu-id="acc56-125">範例七：呼叫傳回 XML 項目的使用者程式碼：</span><span class="sxs-lookup"><span data-stu-id="acc56-125">Example Seven — call user code that returns an XML element:</span></span>  
  
```  
xpath(MyMsg2, "/RecommendedBooks/AdvertisedByPartner") = GetPartnerAdvertisedBook();  
```  
  
 <span data-ttu-id="acc56-126">在套用範例五及範例七之前：</span><span class="sxs-lookup"><span data-stu-id="acc56-126">Before applying examples five and seven:</span></span>  
  
```  
<RecommendedBooks>  
       <BookOfTheMonth/>  
       <BestPriceBooks/>  
       <AdvertisedByPartner/>  
</RecommendedBooks>  
```  
  
 <span data-ttu-id="acc56-127">在套用範例五及範例七之後：</span><span class="sxs-lookup"><span data-stu-id="acc56-127">After applying examples five and seven:</span></span>  
  
```  
<RecommendedBooks>  
       <BookOfTheMonth>  
              <Book country="USA">  
                     <title>McSharry</title>  
                     <author>  
                            <FirstName>Nancy</FirstName>  
                            <LastName>Jensen</LastName>  
                     </author>  
              </Book>  
       </BookOfTheMonth>  
       <BestPriceBooks/>  
       <AdvertisedByPartner>  
              <Book country="USA">  
                     <title>The Rooster</title>  
                     <author>  
                            <FirstName>Mindy</FirstName>  
                            <LastName>Martin</LastName>  
                     </author>  
              </Book>  
       </AdvertisedByPartner>  
</RecommendedBooks>  
```