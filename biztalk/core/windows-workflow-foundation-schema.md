---
title: "Windows Workflow Foundation 結構描述 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dd017df1-1b98-4e4a-83ad-61e8ec4b428d
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2b680a21fe892c2599cb43643cadc68fbb74f89c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="windows-workflow-foundation-schema"></a>Windows Workflow Foundation 結構描述
本節包含 Windows Workflow Framework 攔截器的結構描述。  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema targetNamespace="http://schemas.microsoft.com/BizTalkServer/2004/10/BAM/WorkflowInterceptorConfiguration" elementFormDefault="qualified" xmlns="http://schemas.microsoft.com/BizTalkServer/2004/10/BAM/WorkflowInterceptorConfiguration" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  
  <xs:element name="Operation">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="Argument" type="xs:string" minOccurs="0" maxOccurs="unbounded" />  
      </xs:sequence>  
      <xs:attribute name="Name" type="WorkflowOperationType" use="required" />  
    </xs:complexType>  
  </xs:element>  
  
  <xs:simpleType name="WorkflowOperationType">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="GetActivityName" />  
      <xs:enumeration value="GetActivityEvent" />  
      <xs:enumeration value="GetWorkflowEvent" />  
      <xs:enumeration value="GetActivityType" />  
      <xs:enumeration value="GetUserDataType" />  
      <xs:enumeration value="GetUserKey" />  
      <xs:enumeration value="GetUserData" />  
      <xs:enumeration value="GetWorkflowProperty" />  
      <xs:enumeration value="GetActivityProperty" />  
      <xs:enumeration value="GetContextProperty" />  
    </xs:restriction>  
  </xs:simpleType>  
  
</xs:schema>   
```  
  
## <a name="see-also"></a>另請參閱  
 [攔截器組態結構描述](../core/interceptor-configuration-schema.md)   
 [Windows Communication Foundation 結構描述](../core/windows-communication-foundation-schema.md)