---
title: 訊息指派中使用 Xpath |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
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
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d9ec1e5b56f382601c79324df8651c91c483cb4a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22288110"
---
# <a name="using-xpaths-in-message-assignments"></a>訊息指派中使用 Xpath
您可以使用**xpath**函式將 XPath 值指派至訊息部分，或將值指派給參考訊息部分的 XPath。 如需有關將指派給訊息和訊息部分的詳細資訊，請參閱[建構訊息](../core/constructing-messages.md)。  
  
> [!NOTE]
>  如需 xpath 函式的詳細資訊，請參閱 XML 路徑語言 (XPath) 的協力廠商文件。  
  
> [!NOTE]
>  使用**xpath**函式並不限於訊息指派。 您也可以將它用於任何運算式，例如：  
  
```  
If ((System.Double) xpath(_RequestMessage.part, "number(//book[last()]/price)") == 75.00 && (System.Boolean) xpath(msgBoolean, "string(//boolean)") == false)...  
```  
  
> [!NOTE]
>  如果想要將值指派給字串，請使用 XPath string() 函式。 例如：  
  
```  
myString = xpath(msg, "string(/*/book[1]/title)");  
```  
  
> [!NOTE]
>  引擎並非結構描述感知，所以您只能從包含節點的訊息中 (必須有完整的路徑)，從節點讀取值或將值寫入至節點，否則引擎會引發例外狀況。 即使提供預設值，這種情況還是會發生。  
  
## <a name="assigning-to-an-xpath-in-a-message-part"></a>指派至訊息部分中的 XPath  
 請參考下列結構描述：  
  
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
  
 您可以使用下列函式，在該結構描述類型的文件執行個體上設定值。  
  
```  
//assumes that a message named _ResponseMessage is already constructed  
_ResponseMessage.part = _RequestMessage.part;  
xpath(_ResponseMessage.part, "/*/book[1]/@country") = "USA";  
xpath(_ResponseMessage.part, "/*/book[1]/title") = "Legends";  
xpath(_ResponseMessage.part, "/*/book[1]/author/FirstName") = "A";  
xpath(_ResponseMessage.part, "/*/book[1]/author/LastName") = "B";  
xpath(_ResponseMessage.part, "/*/book[1]/price") = 50;  
```  
  
## <a name="assigning-to-a-message-part-from-an-xpath"></a>從 XPath 指派至訊息部分  
  
```  
//assumes that a message named objMessage is already constructed  
objMessage.BooleanPart = xpath("false()");  
objMessage.IntPart = xpath("100");  
objMessage.StringPart = xpath("'Hello'");  
objMessage.StringPart2 = xpath("'World'");  
```  
  
## <a name="using-xpath-to-assign-from-nodes-and-node-sets"></a>使用 XPath 從節點和節點組合進行指派  
 您也可以使用 XPath，將 XML 節點和節點組合指派至 XML 項目、類別或以結構描述為基礎或以類別為基礎的訊息。  
  
 假設您有稱為 Book 的 XML 可序列化的類別，請考慮下列的範例：  
  
```  
[Serializable]  
Class Book {...}  
```  
  
 範例一：從目錄選取第四個 book 項目，然後將它指派給 XML 項目變數：  
  
```  
myXmlElement = xpath(myMsg, "/catalog/book[3]");  
```  
  
 範例二：從目錄選取第四個 book 項目，然後使用 XML 序列化將它轉換為 Book 類別執行個體：  
  
```  
myBook = xpath(myMsg, "/catalog/book[3]");  
```  
  
 範例三：從目錄選取第四個 book 項目，然後將它轉換為型別 Book 的訊息：  
  
```  
myBookMsg = xpath(myMsg, "/catalog/book[3]");  
```  
  
 範例四：選取目錄中的所有 book 項目，其中 MyMethod 會使用 XmlNodeSet 做為參數：  
  
```  
MyMethod(xpath(myMsg, "/catalog/book"));  
```  
  
 範例五：將 book 項目新增至 "BookOfTheMonth" 容器：  
  
```  
xpath(MyMsg2, "/RecommendedBooks/BookOfTheMonth") = myBook;  
```  
  
 範例六：將定價為 20 或更低的所有書籍新增至一組推薦的書籍：  
  
```  
xpath(MyMsg2, "/RecommendedBooks/BestPriceBooks") = xpath(MyMsg, "/catalog/book[@price <= 20]");  
```  
  
 範例七：呼叫傳回 XML 項目的使用者程式碼：  
  
```  
xpath(MyMsg2, "/RecommendedBooks/AdvertisedByPartner") = GetPartnerAdvertisedBook();  
```  
  
 在套用範例五及範例七之前：  
  
```  
<RecommendedBooks>  
       <BookOfTheMonth/>  
       <BestPriceBooks/>  
       <AdvertisedByPartner/>  
</RecommendedBooks>  
```  
  
 在套用範例五及範例七之後：  
  
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