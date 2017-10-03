---
title: "自訂組態結構描述的配接器的範例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 31b188de-9363-4f4c-b40a-149ff59ddf8d
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b11cb16c7b7ae9285b6ffb77c7177964d211482f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="examples-of-custom-configuration-schemas-for-adapters"></a><span data-ttu-id="a138a-102">自訂組態結構描述的配接器的範例</span><span class="sxs-lookup"><span data-stu-id="a138a-102">Examples of Custom Configuration Schemas for Adapters</span></span>
<span data-ttu-id="a138a-103">本節提供下列範例，說明如何為配接器自訂組態結構描述：</span><span class="sxs-lookup"><span data-stu-id="a138a-103">This section provides the following examples for how to customize configuration schemas for adapters:</span></span>  
  
-   <span data-ttu-id="a138a-104">**範例 1**顯示完整自訂 XSD 結構描述檔案代表使用 baf: designer 和 baf: description 延伸模組的配接器屬性頁。</span><span class="sxs-lookup"><span data-stu-id="a138a-104">**Example 1** shows a complete custom XSD schema file representing an adapter property page using the baf:designer and baf:description extensions.</span></span>  
  
-   <span data-ttu-id="a138a-105">**範例 2**也使用 baf: designer 和 baf: description 延伸模組，顯示如何建立自訂的屬性值視窗**BatchSize**只接受介於 1 到 99 （含) 之間的值的屬性。</span><span class="sxs-lookup"><span data-stu-id="a138a-105">**Example 2** also uses the baf:designer and baf:description extensions to show how to create a custom property value window for the **BatchSize** property that only accepts values between 1 and 99, inclusive.</span></span>  
  
-   <span data-ttu-id="a138a-106">**範例 3**顯示如何將 baf: password 為 8 個字元的限制。</span><span class="sxs-lookup"><span data-stu-id="a138a-106">**Example 3** shows how to limit the baf:Password to 8 characters.</span></span> <span data-ttu-id="a138a-107">根據預設，會允許 22 個字元。</span><span class="sxs-lookup"><span data-stu-id="a138a-107">By default, it allows 22 characters.</span></span>  
  
-   <span data-ttu-id="a138a-108">**範例 4**示範如何實作模式比對屬性值的條件約束，因為 XSD 模式不受支援。</span><span class="sxs-lookup"><span data-stu-id="a138a-108">**Example 4** shows how to implement pattern-matching constraints on property values because XSD patterns are not supported.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="a138a-109">範例 1</span><span class="sxs-lookup"><span data-stu-id="a138a-109">Example 1</span></span>  
 <span data-ttu-id="a138a-110">這個範例顯示一個完整的自訂 XSD 結構描述。</span><span class="sxs-lookup"><span data-stu-id="a138a-110">This example shows a complete custom XSD schema.</span></span> <span data-ttu-id="a138a-111">它代表使用 baf:designer 和 baf:description 延伸模組的配接器屬性頁。</span><span class="sxs-lookup"><span data-stu-id="a138a-111">It represents an adapter property page using the baf:designer and baf:description extensions.</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<xs:schema   targetNamespace="http://tempuri.org/XMLSchema.xsd"   
         elementFormDefault="qualified" xmlns="http://tempuri.org/XMLSchema.xsd"   
         xmlns:baf="BiztalkAdapterFramework.xsd"   
         xmlns:xs="http://www.w3.org/2001/XMLSchema"   
         xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
   <xs:import namespace="BiztalkAdapterFramework.xsd" />  
   <xs:element name="Send">  
      <xs:complexType>  
         <xs:sequence>  
            <xs:element name="directory" type="xs:string" />  
               <xs:annotation>  
                  <xs:appinfo>  
                     <baf:designer>  
                        <baf:description>Enter the directory that will receive sent files..  
                        </baf:description>  
                     </baf:designer>  
                  </xs:appinfo>  
               </xs:annotation>  
            </xs:element>  
            <xs:element name="fileName" type="" />  
            <xs:element name="sendBatchSize" type="xs:int" />  
            <xs:element name="fileCopyMode" type="CopyMode" />  
            <xs:element name="uri" type="xs:string" >  
               <xs:annotation>  
                  <xs:appinfo>  
                     <baf:designer>  
                        <baf:browsable show="false" />  
                     </baf:designer>  
                  </xs:appinfo>  
               </xs:annotation>  
            </xs:element>  
         </xs:sequence>  
      </xs:complexType>  
   </xs:element>  
   <xs:simpleType name="CopyMode">  
      <xs:restriction base="xs:string">  
         <xs:enumeration value="Append">  
            <xs:annotation>  
               <xs:documentation>= 0</xs:documentation>  
            </xs:annotation>  
         <xs:enumeration value="Create">  
            <xs:annotation>  
               <xs:documentation>= 1</xs:documentation>  
            </xs:annotation>  
         <xs:enumeration value="CreateNew">  
            <xs:annotation>  
               <xs:documentation>= 2</xs:documentation>  
            </xs:annotation>  
         </xs:enumeration>  
      </xs:restriction>  
   </xs:simpleType>  
</xs:schema>  
```  
  
## <a name="example-2"></a><span data-ttu-id="a138a-112">範例 2</span><span class="sxs-lookup"><span data-stu-id="a138a-112">Example 2</span></span>  
 <span data-ttu-id="a138a-113">此範例使用 baf: designer 和 baf: description 延伸模組來示範如何建立自訂的屬性值視窗**BatchSize**只接受介於 1 到 99 （含) 之間的值的屬性。</span><span class="sxs-lookup"><span data-stu-id="a138a-113">This example uses the baf:designer and baf:description extensions to show how to create a custom property value window for the **BatchSize** property that only accepts values between 1 and 99, inclusive.</span></span>  
  
```  
   <xs:element name="BatchSize">  
          <xs:simpleType>  
            <xs:annotation>  
              <xs:appinfo>  
                <baf:designer>  
                  <baf:displayname>Batch Size</baf:displayname>  
                  <baf:description>Enter the batch size (1-99)</baf:description>  
                </baf:designer>  
              </xs:appinfo>  
            </xs:annotation>  
            <xs:restriction base="xs:int">  
              <xs:minInclusive value="1" />  
              <xs:maxInclusive value="99" />  
            </xs:restriction>  
          </xs:simpleType>  
        </xs:element>  
```  
  
## <a name="example-3"></a><span data-ttu-id="a138a-114">範例 3</span><span class="sxs-lookup"><span data-stu-id="a138a-114">Example 3</span></span>  
 <span data-ttu-id="a138a-115">這個範例顯示如何將 baf:Password 限制為 8 個字元。</span><span class="sxs-lookup"><span data-stu-id="a138a-115">This example shows how to limit the baf:Password to 8 characters.</span></span> <span data-ttu-id="a138a-116">根據預設，會允許 22 個字元。</span><span class="sxs-lookup"><span data-stu-id="a138a-116">By default, it allows 22 characters.</span></span>  
  
```  
<xs:element name="AdapterPassword">  
          <xs:simpleType>  
            <xs:annotation>  
              <xs:appinfo>  
                <baf:designer>  
                  <baf:displayname>Adapter Password</baf:displayname>  
                  <baf:description>Enter the password (up to 8 characters)</baf:description>  
                  <baf:editor assembly="%BTSROOT%\\Developer Tools\\Microsoft.BizTalk.Adapter.Framework.dll">Microsoft.BizTalk.Adapter.Framework.ComponentModel.PasswordUITypeEditor</baf:editor>  
                  <baf:converter assembly="%BTSROOT%\\Developer Tools\\Microsoft.BizTalk.Adapter.Framework.dll">Microsoft.BizTalk.Adapter.Framework.ComponentModel.PasswordTypeConverter</baf:converter>  
                </baf:designer>  
              </xs:appinfo>  
            </xs:annotation>  
            <xs:restriction base="xs:string">  
              <xs:maxLength value="8" />  
            </xs:restriction>  
          </xs:simpleType>  
        </xs:element>  
```  
  
## <a name="example-4"></a><span data-ttu-id="a138a-117">範例 4</span><span class="sxs-lookup"><span data-stu-id="a138a-117">Example 4</span></span>  
 <span data-ttu-id="a138a-118">這個範例顯示如何在屬性值實作模式比對的條件約束，這是因為 XSD 模式不受支援。</span><span class="sxs-lookup"><span data-stu-id="a138a-118">This example shows how to implement pattern-matching constraints on property values because XSD patterns are not supported.</span></span>  
  
 <span data-ttu-id="a138a-119">這類欄位**ClientIdentifier**永遠是三個字元的數值字串。</span><span class="sxs-lookup"><span data-stu-id="a138a-119">Fields such as **ClientIdentifier** are always a three-character numeric string.</span></span> <span data-ttu-id="a138a-120">屬性值 10 無效，010 則為有效。</span><span class="sxs-lookup"><span data-stu-id="a138a-120">A property value of 10 is not valid, whereas 010 is valid.</span></span> <span data-ttu-id="a138a-121">下列組態結構描述分割定義**ClientIdentifier**屬性。</span><span class="sxs-lookup"><span data-stu-id="a138a-121">The following configuration schema fragment defines a **ClientIdentifier** property.</span></span> <span data-ttu-id="a138a-122">**ClientIdentifierConverter**類別，實作您的配接器組件中實作模式比對。</span><span class="sxs-lookup"><span data-stu-id="a138a-122">The **ClientIdentifierConverter** class, implemented in your adapter assembly, implements pattern matching.</span></span> <span data-ttu-id="a138a-123">在此情況下，自訂類型轉換器會將值限制為剛好三個位數 (000 到 999) 的字串。</span><span class="sxs-lookup"><span data-stu-id="a138a-123">In this case, the custom type converter restricts values to a string of exactly three digits (000 to 999).</span></span> <span data-ttu-id="a138a-124">在組態結構描述中，請確定 baf:converter 節點有正確設定組件和類型完整名稱。</span><span class="sxs-lookup"><span data-stu-id="a138a-124">In the configuration schema, make sure the baf:converter node has the assembly and type full name set correctly.</span></span> <span data-ttu-id="a138a-125">如果使用者嘗試輸入無效的值，當在屬性頁中發生驗證錯誤時，便會出現例外狀況訊息。</span><span class="sxs-lookup"><span data-stu-id="a138a-125">If the user attempts to enter a value that is not valid, an exception message pops up when a validation error occurs in the property page.</span></span>  
  
 <span data-ttu-id="a138a-126">您可以在配接器屬性頁組態結構描述中使用下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="a138a-126">You can use the following code in the adapter property page configuration schemas.</span></span>  
  
```  
        <xs:element name="ClientIdentifier" type="xs:string">  
          <xs:annotation>  
            <xs:appinfo>  
              <baf:designer>  
                <baf:displayname>Adapter Client</baf:displayname>  
                <baf:description>Enter the Adapter Client (3 digit string)</baf:description>  
                <baf:converter assembly="%BTSROOT%\\Developer Tools\\Microsoft.BizTalk.TestAdapter.dll">Microsoft.BizTalk.TestAdapter.ClientIdentifierConverter</baf:converter>  
              </baf:designer>  
            </xs:appinfo>  
          </xs:annotation>  
        </xs:element>  
```  
  
 <span data-ttu-id="a138a-127">您可以將下列程式碼放在配接器組件中。</span><span class="sxs-lookup"><span data-stu-id="a138a-127">You can place the following code in your adapter assembly.</span></span>  
  
```  
using System;  
using System.ComponentModel;  
using System.Globalization;  
using System.Text.RegularExpressions;  
  
namespace Microsoft.BizTalk.TestAdapter  
{  
       /// <summary>  
       /// Summary description for ClientIdentifierConverter.  
       /// </summary>  
       public class ClientIdentifierConverter : System.ComponentModel.StringConverter   
       {  
              private void Validate(string value)  
              {  
                     Regex regex = new Regex(@"^\d{3}$"); // ^=begin, \d=digit, {3}=exactly 3 occurrences, $=end  
                     Match match = regex.Match((string)value);  
                     if (!match.Success)  
                     {  
                           throw new ApplicationException("Value does not match pattern \"" + regex.ToString() + "\".");  
                     }  
              }  
  
              public override object ConvertFrom(ITypeDescriptorContext context, CultureInfo culture, object value)  
              {  
                     if (value is string)  
                     {  
                           this.Validate((string)value);  
                     }  
                     return base.ConvertFrom(context, culture, value);  
              }  
  
              public override object ConvertTo(ITypeDescriptorContext context, CultureInfo culture, object value, Type destinationType)  
              {  
                     if (typeof(string) == destinationType && value is string)  
                     {  
                           this.Validate((string)value);  
                     }  
                     return base.ConvertTo(context, culture, value, destinationType);  
              }  
       }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="a138a-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a138a-128">See Also</span></span>  
 [<span data-ttu-id="a138a-129">配接器架構組態結構描述延伸模組</span><span class="sxs-lookup"><span data-stu-id="a138a-129">Adapter Framework Configuration Schema Extensions</span></span>](../core/adapter-framework-configuration-schema-extensions.md)