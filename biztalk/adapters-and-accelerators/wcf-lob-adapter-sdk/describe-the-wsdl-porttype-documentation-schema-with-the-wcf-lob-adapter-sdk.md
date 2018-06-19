---
title: 描述與 WCF LOB 配接器 SDK 的 WSDL PortType 文件結構描述 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9dd96eaf-b3b3-49b4-aea9-0ae1e8999d62
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 81e4977403da18229aea19beef21f361dfdd9391
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25965148"
---
# <a name="describe-the-wsdl-porttype-documentation-schema-with-the-wcf-lob-adapter-sdk"></a><span data-ttu-id="74fbe-102">描述與 WCF LOB 配接器 SDK 的 WSDL PortType 文件結構描述</span><span class="sxs-lookup"><span data-stu-id="74fbe-102">Describe the WSDL PortType Documentation Schema with the WCF LOB Adapter SDK</span></span>
<span data-ttu-id="74fbe-103">WSDL 的[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]會產生包含每個連接埠類型的其他描述性資訊。</span><span class="sxs-lookup"><span data-stu-id="74fbe-103">The WSDL that the  [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] generates contains additional descriptive information for each portType.</span></span> <span data-ttu-id="74fbe-104">此主題將說明這項額外資訊的結構描述。</span><span class="sxs-lookup"><span data-stu-id="74fbe-104">The schema for this additional information is described in this topic.</span></span>  
  
## <a name="documentation-xml-schema"></a><span data-ttu-id="74fbe-105">文件的 XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="74fbe-105">Documentation XML Schema</span></span>  
 <span data-ttu-id="74fbe-106">實作作業文件使用的連接埠類型註釋加入節點，表示作業的配接器文件。</span><span class="sxs-lookup"><span data-stu-id="74fbe-106">The operation documentation is implemented using annotation of the portType to add a node that represents the adapter documentation for the operation.</span></span> <span data-ttu-id="74fbe-107">這個節點包含子節點，進一步描述作業和參數。</span><span class="sxs-lookup"><span data-stu-id="74fbe-107">This node contains subnodes that further describe the operation and parameters.</span></span> <span data-ttu-id="74fbe-108">此結構描述定義，如下所示。</span><span class="sxs-lookup"><span data-stu-id="74fbe-108">This schema is defined as follows.</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:element name="adapterOperationDocumentation">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="summary" type="xs:string" />  
        <xs:element maxOccurs="unbounded" name="param">  
          <xs:complexType>  
            <xs:simpleContent>  
              <xs:extension base="xs:string">  
                <xs:attribute name="name" type="xs:string" use="required" />  
              </xs:extension>  
            </xs:simpleContent>  
          </xs:complexType>  
        </xs:element>  
        <xs:element name="returns" type="xs:string" />  
      </xs:sequence>  
    </xs:complexType>  
  </xs:element>  
</xs:schema>  
```  
  
 <span data-ttu-id="74fbe-109">指定作業產生 WSDL 時，上述的結構描述用來提供人類可讀取的格式中的其他描述性資訊。</span><span class="sxs-lookup"><span data-stu-id="74fbe-109">When WSDL is generated for a given operation, the preceding schema is used to provide additional descriptive information in human readable format.</span></span> <span data-ttu-id="74fbe-110">例如，下列連接埠類型資訊會傳回回應配接器的 EchoString 作業。</span><span class="sxs-lookup"><span data-stu-id="74fbe-110">For example, the following portType information is returned for the EchoString operation of the Echo Adapter.</span></span>  
  
```  
<wsdl:portType name="EchoService">  
  <wsdl:operation name="EchoString">  
    <wsdl:documentation>  
      <doc:adapterOperationDocumentation>  
        <doc:summary>String EchoString( string aName)\</doc:summary>  
        <doc:param name="aName">This string will be echoed back to the user.\</doc:param>  
        <doc:returns>String value containing the value of aName \</doc:returns>  
      </doc:adapterOperationDocumentation>  
    </wsdl:documentation>  
    <wsdl:input wsaw:Action="Echo/EchoString" message="ns2:EchoService_EchoString_InputMessage" />  
    <wsdl:output wsaw:Action="Echo/EchoString/response" message="ns2:EchoService_EchoString_OutputMessage" />  
  </wsdl:operation>  
</wsdl:portType>  
```  
  
 <span data-ttu-id="74fbe-111">文件元素的值取自`Microsoft.ServiceModel.Channels.Common.ParameterizedOperationMetadata`作業。</span><span class="sxs-lookup"><span data-stu-id="74fbe-111">The values for the documentation elements are obtained from `Microsoft.ServiceModel.Channels.Common.ParameterizedOperationMetadata` for the operation.</span></span> <span data-ttu-id="74fbe-112">下列範例而產生上述的範例。</span><span class="sxs-lookup"><span data-stu-id="74fbe-112">The preceding example was generated as a result of the following example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="74fbe-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="74fbe-113">See Also</span></span>  
 [<span data-ttu-id="74fbe-114">使用 WCF LOB 配接器 SDK 開發最佳作法</span><span class="sxs-lookup"><span data-stu-id="74fbe-114">Development best practices using the WCF LOB Adapter SDK</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/development-best-practices-using-the-wcf-lob-adapter-sdk.md)