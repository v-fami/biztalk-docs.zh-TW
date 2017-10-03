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
# <a name="examples-of-custom-configuration-schemas-for-adapters"></a>自訂組態結構描述的配接器的範例
本節提供下列範例，說明如何為配接器自訂組態結構描述：  
  
-   **範例 1**顯示完整自訂 XSD 結構描述檔案代表使用 baf: designer 和 baf: description 延伸模組的配接器屬性頁。  
  
-   **範例 2**也使用 baf: designer 和 baf: description 延伸模組，顯示如何建立自訂的屬性值視窗**BatchSize**只接受介於 1 到 99 （含) 之間的值的屬性。  
  
-   **範例 3**顯示如何將 baf: password 為 8 個字元的限制。 根據預設，會允許 22 個字元。  
  
-   **範例 4**示範如何實作模式比對屬性值的條件約束，因為 XSD 模式不受支援。  
  
## <a name="example-1"></a>範例 1  
 這個範例顯示一個完整的自訂 XSD 結構描述。 它代表使用 baf:designer 和 baf:description 延伸模組的配接器屬性頁。  
  
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
  
## <a name="example-2"></a>範例 2  
 此範例使用 baf: designer 和 baf: description 延伸模組來示範如何建立自訂的屬性值視窗**BatchSize**只接受介於 1 到 99 （含) 之間的值的屬性。  
  
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
  
## <a name="example-3"></a>範例 3  
 這個範例顯示如何將 baf:Password 限制為 8 個字元。 根據預設，會允許 22 個字元。  
  
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
  
## <a name="example-4"></a>範例 4  
 這個範例顯示如何在屬性值實作模式比對的條件約束，這是因為 XSD 模式不受支援。  
  
 這類欄位**ClientIdentifier**永遠是三個字元的數值字串。 屬性值 10 無效，010 則為有效。 下列組態結構描述分割定義**ClientIdentifier**屬性。 **ClientIdentifierConverter**類別，實作您的配接器組件中實作模式比對。 在此情況下，自訂類型轉換器會將值限制為剛好三個位數 (000 到 999) 的字串。 在組態結構描述中，請確定 baf:converter 節點有正確設定組件和類型完整名稱。 如果使用者嘗試輸入無效的值，當在屬性頁中發生驗證錯誤時，便會出現例外狀況訊息。  
  
 您可以在配接器屬性頁組態結構描述中使用下列程式碼。  
  
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
  
 您可以將下列程式碼放在配接器組件中。  
  
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
  
## <a name="see-also"></a>另請參閱  
 [配接器架構組態結構描述延伸模組](../core/adapter-framework-configuration-schema-extensions.md)