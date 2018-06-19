---
title: ESB 路線結構描述 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 168e7b98-6282-494e-bde8-3171e0be7d59
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 66bcbe6780105a97e58df393d0e060688048a02b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22295222"
---
# <a name="the-esb-itinerary-schema"></a><span data-ttu-id="2e248-102">ESB 路線結構描述</span><span class="sxs-lookup"><span data-stu-id="2e248-102">The ESB Itinerary Schema</span></span>
<span data-ttu-id="2e248-103">名為 Itinerary.xsd ESB 行程結構描述會定義成一組處理指示，通常稱為路線服務的路線。</span><span class="sxs-lookup"><span data-stu-id="2e248-103">The ESB Itinerary schema named Itinerary.xsd defines an itinerary as a set of processing instructions, generally referred to as itinerary services.</span></span> <span data-ttu-id="2e248-104">路線的服務可能包含一或多個路線的服務和對應的解析程式連接字串，如下列的結構描述定義中所示。</span><span class="sxs-lookup"><span data-stu-id="2e248-104">An itinerary service may contain one or more itinerary services and the corresponding resolver connection strings, as shown in the following schema definition.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-16"?>  
  
<xs:schema xmlns:b="http://schemas.microsoft.com/BizTalk/2003" xmlns="http://schemas.microsoft.biztalk.practices.esb.com/itinerary" targetNamespace="http://schemas.microsoft.biztalk.practices.esb.com/itinerary" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  
  <xs:annotation>  
    <xs:appinfo>  
      <b:schemaInfo root_reference="Itinerary" xmlns:b="http://schemas.microsoft.con/BizTalk/2003" />  
    </xs:appinfo>  
  </xs:annotation>  
  <xs:element name="Itinerary">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="BizTalkSegment">  
          <xs:complexType>  
            <xs:attribute name="interchangeId" type="xs:string" />  
            <xs:attribute name="epmRRCorrelationToken" type="xs:string" />  
            <xs:attribute name="receiveInstanceId" type="xs:string" />  
            <xs:attribute name="messageId" type="xs:string" />  
          </xs:complexType>  
        </xs:element>  
        <xs:element name="ServiceInstance">  
          <xs:complexType>  
            <xs:attribute name="uuid" type="xs:string" />  
            <xs:attribute name="name" type="xs:string" />  
            <xs:attribute name="type" type="xs:string" />  
            <xs:attribute name="state" type="xs:string" />  
            <xs:attribute name="position" type="xs:int" />  
            <xs:attribute name="isRequestResponse" type="xs:boolean" />  
            <xs:attribute name="stage" type="Stages" />  
          </xs:complexType>  
        </xs:element>  
        <xs:element minOccurs="1" maxOccurs="unbounded" name="Services">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="Services">  
                <xs:complexType>  
                  <xs:sequence>  
                    <xs:element minOccurs="0" maxOccurs="1" name="PropertyBag" nillable="true">  
                      <xs:complexType>  
                        <xs:sequence minOccurs="0" maxOccurs="1">  
                          <xs:element minOccurs="0" maxOccurs="unbounded" name="Property">  
                            <xs:complexType>  
                              <xs:attribute name="name" type="xs:string" use="required" />  
                              <xs:attribute name="value" type="xs:string" use="required" />  
                            </xs:complexType>  
                          </xs:element>  
                        </xs:sequence>  
                      </xs:complexType>  
                    </xs:element>  
                  </xs:sequence>  
                  <xs:attribute name="uuid" type="xs:string" />  
                  <xs:attribute name="beginTime" type="xs:string" />  
                  <xs:attribute name="completeTime" type="xs:string" />  
                  <xs:attribute name="name" type="xs:string" />  
                  <xs:attribute name="type" type="xs:string" />  
                  <xs:attribute name="state" type="xs:string" />  
                  <xs:attribute name="resolve" type="xs:boolean" />  
                  <xs:attribute name="isRequestResponse" type="xs:boolean" />  
                  <xs:attribute name="position" type="xs:int" />  
                  <xs:attribute name="serviceInstanceId" type="xs:string" />  
                  <xs:attribute name="isTrackingEnabled">  
                    <xs:simpleType>  
                      <xs:restriction base="xs:boolean" />  
                    </xs:simpleType>  
                  </xs:attribute>  
                  <xs:attribute name="stage" type="Stages" />  
                </xs:complexType>  
              </xs:element>  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
        <xs:element name="ResolverGroups">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element maxOccurs="unbounded" name="Resolvers">  
                <xs:complexType>  
                  <xs:simpleContent>  
                    <xs:extension base="xs:string">  
                      <xs:attribute name="serviceId" type="xs:string" />  
                    </xs:extension>  
                  </xs:simpleContent>  
                </xs:complexType>  
              </xs:element>  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
      </xs:sequence>  
      <xs:attribute name="uuid" type="xs:string" />  
      <xs:attribute name="beginTime" type="xs:string" />  
      <xs:attribute name="completeTime" type="xs:string" />  
      <xs:attribute name="state" type="xs:string" />  
      <xs:attribute name="isRequestResponse" type="xs:boolean" />  
      <xs:attribute name="servicecount" type="xs:int" use="required" />  
    </xs:complexType>  
  </xs:element>  
  <xs:simpleType name="Stages">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="notSpecified" />  
      <xs:enumeration value="receiveInbound" />  
      <xs:enumeration value="receiveTransmit" />  
      <xs:enumeration value="sendTransmit" />  
      <xs:enumeration value="sendInbound" />  
    </xs:restriction>  
  </xs:simpleType>  
</xs:schema>  
```  
  
 <span data-ttu-id="2e248-105">**ServiceInstance**項目對應至目前的路線服務和包含屬性，例如**名稱**，**類型**，**狀態**，和**位置**，服務升級至訊息內容。</span><span class="sxs-lookup"><span data-stu-id="2e248-105">The **ServiceInstance** element corresponds to the current itinerary service and contains properties such as **name**, **type**, **state**, and **position** that the service promotes into the message context.</span></span> <span data-ttu-id="2e248-106">名為 System-Properties.xsd 中的結構描述**Microsoft.Practices.ESB.ItinerarySchemas**組件會定義這些屬性。</span><span class="sxs-lookup"><span data-stu-id="2e248-106">The schema named System-Properties.xsd in the **Microsoft.Practices.ESB.ItinerarySchemas** assembly defines these properties.</span></span>  
  
 <span data-ttu-id="2e248-107">**服務**項目代表一組路線的服務，與每個服務定義其狀態、 開始時間、 完成時間、 類型 (**協調流程**或**傳訊**)，並選擇性地階段 (**receiveInbound**， **receiveTransmit**， **sendTransmit**， **sendInbound**)。</span><span class="sxs-lookup"><span data-stu-id="2e248-107">The **Services** element represents a set of itinerary services, with each service defined by its state, begin time, completion time, type (**Orchestration** or **Messaging**), and, optionally, stage (**receiveInbound**, **receiveTransmit**, **sendTransmit**, **sendInbound**).</span></span>  
  
 <span data-ttu-id="2e248-108">**ResolverGroups**元素包含多個**解析程式**項目，其中每個定義一個或多個的解析程式連接字串透過參考路線**serviceid**屬性。</span><span class="sxs-lookup"><span data-stu-id="2e248-108">The **ResolverGroups** element contains multiple **Resolvers** elements, each of which defines one or more resolver connection strings that an itinerary references through the **serviceid** attribute.</span></span>  
  
 <span data-ttu-id="2e248-109">以下顯示 ESB 行程管線元件處理之前的提交路線 SOAP 標頭的範例。</span><span class="sxs-lookup"><span data-stu-id="2e248-109">The following shows a sample of a submitted itinerary SOAP header before it is processed by the ESB Itinerary Pipeline component.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Itinerary xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" uuid="" beginTime="" completeTime="" state="Pending" isRequestResponse="false" xmlns="http://schemas.microsoft.biztalk.practices.esb.com/itinerary">  
  
  <ServiceInstance uuid="" name="Microsoft.Practices.ESB.Services.Transform" type="Messaging" state="Pending" position="0" isRequestResponse="false" xmlns="" />  
  
  <Services xmlns="">  
    <Service uuid="" beginTime="" completeTime="" name="Microsoft.Practices.ESB.Services.Transform" type="Messaging" state="Pending" isRequestResponse="false" position="0" serviceInstanceId="" />  
  </Services>  
  
  <Services xmlns="">  
    <Service uuid="" beginTime="" completeTime="" name="DynamicResolutionSolicitResp" type="Messaging" state="Pending" isRequestResponse="true" position="1" serviceInstanceId="" />  
  </Services>  
  
  <ResolverGroups xmlns="">  
    <Resolvers serviceId="DynamicResolutionSolicitResp1"><![CDATA[BRE:\\policy=GetCanadaEndPoint;version=;useMsg=;]]></Resolvers>  
  
    <Resolvers serviceId="Microsoft.Practices.ESB.Services.Transform0"><![CDATA[BRE:\\policy=CanadaSubmitOrderMaps;version=;useMsg=;]]></Resolvers>  
  </ResolverGroups>  
  
</Itinerary>  
```