---
title: "描述與 WCF LOB 配接器 SDK 的 WSDL PortType 文件結構描述 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9dd96eaf-b3b3-49b4-aea9-0ae1e8999d62
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 038b8ca075e756a0857e70a420c0fc7913113c92
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="describe-the-wsdl-porttype-documentation-schema-with-the-wcf-lob-adapter-sdk"></a>描述與 WCF LOB 配接器 SDK 的 WSDL PortType 文件結構描述
WSDL 的[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]會產生包含每個連接埠類型的其他描述性資訊。 此主題將說明這項額外資訊的結構描述。  
  
## <a name="documentation-xml-schema"></a>文件的 XML 結構描述  
 實作作業文件使用的連接埠類型註釋加入節點，表示作業的配接器文件。 這個節點包含子節點，進一步描述作業和參數。 此結構描述定義，如下所示。  
  
```  
\<?xml version="1.0" encoding="utf-8"?>  
\<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  \<xs:element name="adapterOperationDocumentation">  
    \<xs:complexType>  
      \<xs:sequence>  
        \<xs:element name="summary" type="xs:string" />  
        \<xs:element maxOccurs="unbounded" name="param">  
          \<xs:complexType>  
            \<xs:simpleContent>  
              \<xs:extension base="xs:string">  
                \<xs:attribute name="name" type="xs:string" use="required" />  
              \</xs:extension>  
            \</xs:simpleContent>  
          \</xs:complexType>  
        \</xs:element>  
        \<xs:element name="returns" type="xs:string" />  
      \</xs:sequence>  
    \</xs:complexType>  
  \</xs:element>  
\</xs:schema>  
```  
  
 指定作業產生 WSDL 時，上述的結構描述用來提供人類可讀取的格式中的其他描述性資訊。 例如，下列連接埠類型資訊會傳回回應配接器的 EchoString 作業。  
  
```  
\<wsdl:portType name="EchoService">  
  \<wsdl:operation name="EchoString">  
    \<wsdl:documentation>  
      \<doc:adapterOperationDocumentation>  
        \<doc:summary>String EchoString( string aName)\</doc:summary>  
        \<doc:param name="aName">This string will be echoed back to the user.\</doc:param>  
        \<doc:returns>String value containing the value of aName \</doc:returns>  
      \</doc:adapterOperationDocumentation>  
    \</wsdl:documentation>  
    \<wsdl:input wsaw:Action="Echo/EchoString" message="ns2:EchoService_EchoString_InputMessage" />  
    \<wsdl:output wsaw:Action="Echo/EchoString/response" message="ns2:EchoService_EchoString_OutputMessage" />  
  \</wsdl:operation>  
\</wsdl:portType>  
```  
  
 文件元素的值取自`Microsoft.ServiceModel.Channels.Common.ParameterizedOperationMetadata`作業。 下列範例而產生上述的範例。  
  
```csharp  
ParameterizedOperationMetadata om = new ParameterizedOperationMetadata(operationId, operationId);  
// set this if you want this operation to belong to this interface name  
// in the generated proxy, the interface name will be EchoService  
// and the client implementation name will be EchoServiceClient.  
om.OperationGroup = "EchoService";  
// set the operation namespace to be same as service namespace  
om.OperationNamespace = EchoAdapter.SERVICENAMESPACE;              
switch (operationId)  
{  
   case "Echo/EchoString":  
       om.DisplayName = "EchoString";  
       om.OriginalName = "targetSystemEchoString";  
       om.Description = "String EchoString( string aName)";  
       OperationParameter parm1 = new OperationParameter("aName", OperationParameterDirection.In, QualifiedType.StringType, false);  
       parm1.Description = "This string will be echoed back to the user.";  
       OperationResult result = new OperationResult(new SimpleQualifiedType(XmlTypeCode.String), false);  
       result.Description = "String value containing the value of aName";  
       om.Parameters.Add(parm1);  
       om.OperationResult = result;  
       return om;   
```  
  
## <a name="see-also"></a>另請參閱  
 [使用 WCF LOB 配接器 SDK 開發最佳作法](../../adapters-and-accelerators/wcf-lob-adapter-sdk/development-best-practices-using-the-wcf-lob-adapter-sdk.md)