---
title: "TIBCO 企業訊息服務訊息描述元屬性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: message descriptor properties
ms.assetid: fc164c12-6dc3-4b74-9aa9-024e18faf80a
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 80c75875c44c4d082089fc9394fef390a0f91571
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="tibco-enterprise-message-service-message-descriptor-properties"></a><span data-ttu-id="ec3b7-102">TIBCO Enterprise Message Service 訊息描述元屬性</span><span class="sxs-lookup"><span data-stu-id="ec3b7-102">TIBCO Enterprise Message Service Message Descriptor Properties</span></span>
<span data-ttu-id="ec3b7-103">下表顯示所有可用的「訊息描述元」(TibcoEMSMD 結構)」屬性及其對應的類型與值。</span><span class="sxs-lookup"><span data-stu-id="ec3b7-103">The following table shows the complete set of available Message Descriptor (TibcoEMSMD structure) properties and their corresponding types and values.</span></span>  
  
|<span data-ttu-id="ec3b7-104">名稱</span><span class="sxs-lookup"><span data-stu-id="ec3b7-104">Name</span></span>|<span data-ttu-id="ec3b7-105">型別</span><span class="sxs-lookup"><span data-stu-id="ec3b7-105">Type</span></span>|<span data-ttu-id="ec3b7-106">Value</span><span class="sxs-lookup"><span data-stu-id="ec3b7-106">Value</span></span>|<span data-ttu-id="ec3b7-107">注意</span><span class="sxs-lookup"><span data-stu-id="ec3b7-107">Notes</span></span>|  
|----------|----------|-----------|-----------|  
|<span data-ttu-id="ec3b7-108">TibcoEMS .CorrelationID</span><span class="sxs-lookup"><span data-stu-id="ec3b7-108">TibcoEMS .CorrelationID</span></span>|<span data-ttu-id="ec3b7-109">string</span><span class="sxs-lookup"><span data-stu-id="ec3b7-109">string</span></span>|||  
|<span data-ttu-id="ec3b7-110">TibcoEMS .DelieveryMode</span><span class="sxs-lookup"><span data-stu-id="ec3b7-110">TibcoEMS .DelieveryMode</span></span>|<span data-ttu-id="ec3b7-111">string</span><span class="sxs-lookup"><span data-stu-id="ec3b7-111">string</span></span>|<span data-ttu-id="ec3b7-112">PERSISENT 或 NON-PERSISTENT 之一</span><span class="sxs-lookup"><span data-stu-id="ec3b7-112">One of PERSISENT or NON-PERSISTENT</span></span>||  
|<span data-ttu-id="ec3b7-113">TibcoEMS .Destination</span><span class="sxs-lookup"><span data-stu-id="ec3b7-113">TibcoEMS .Destination</span></span>|<span data-ttu-id="ec3b7-114">string</span><span class="sxs-lookup"><span data-stu-id="ec3b7-114">string</span></span>||<span data-ttu-id="ec3b7-115">唯讀</span><span class="sxs-lookup"><span data-stu-id="ec3b7-115">Read-only</span></span>|  
|<span data-ttu-id="ec3b7-116">TibcoEMS .Expiration</span><span class="sxs-lookup"><span data-stu-id="ec3b7-116">TibcoEMS .Expiration</span></span>|<span data-ttu-id="ec3b7-117">long</span><span class="sxs-lookup"><span data-stu-id="ec3b7-117">long</span></span>|||  
|<span data-ttu-id="ec3b7-118">TibcoEMS .MessageID</span><span class="sxs-lookup"><span data-stu-id="ec3b7-118">TibcoEMS .MessageID</span></span>|<span data-ttu-id="ec3b7-119">string</span><span class="sxs-lookup"><span data-stu-id="ec3b7-119">string</span></span>||<span data-ttu-id="ec3b7-120">唯讀</span><span class="sxs-lookup"><span data-stu-id="ec3b7-120">Read-only</span></span>|  
|<span data-ttu-id="ec3b7-121">TibcoEMS .Priority</span><span class="sxs-lookup"><span data-stu-id="ec3b7-121">TibcoEMS .Priority</span></span>|<span data-ttu-id="ec3b7-122">integer</span><span class="sxs-lookup"><span data-stu-id="ec3b7-122">integer</span></span>|<span data-ttu-id="ec3b7-123">從 0 到 9</span><span class="sxs-lookup"><span data-stu-id="ec3b7-123">From 0 to 9</span></span>||  
|<span data-ttu-id="ec3b7-124">TibcoEMS .Redelivered</span><span class="sxs-lookup"><span data-stu-id="ec3b7-124">TibcoEMS .Redelivered</span></span>|<span data-ttu-id="ec3b7-125">boolean</span><span class="sxs-lookup"><span data-stu-id="ec3b7-125">boolean</span></span>||<span data-ttu-id="ec3b7-126">唯讀</span><span class="sxs-lookup"><span data-stu-id="ec3b7-126">Read-only</span></span>|  
|<span data-ttu-id="ec3b7-127">TibcoEMS .ReplyTo</span><span class="sxs-lookup"><span data-stu-id="ec3b7-127">TibcoEMS .ReplyTo</span></span>|<span data-ttu-id="ec3b7-128">string</span><span class="sxs-lookup"><span data-stu-id="ec3b7-128">string</span></span>|<span data-ttu-id="ec3b7-129">與 Destination 類似</span><span class="sxs-lookup"><span data-stu-id="ec3b7-129">Similar to Destination</span></span>||  
|<span data-ttu-id="ec3b7-130">TibcoEMS .Timestamp</span><span class="sxs-lookup"><span data-stu-id="ec3b7-130">TibcoEMS .Timestamp</span></span>|<span data-ttu-id="ec3b7-131">long</span><span class="sxs-lookup"><span data-stu-id="ec3b7-131">long</span></span>||<span data-ttu-id="ec3b7-132">唯讀</span><span class="sxs-lookup"><span data-stu-id="ec3b7-132">Read-only</span></span>|  
  
 <span data-ttu-id="ec3b7-133">當訊息傳遞給 Microsoft BizTalk Adapter for TIBCO EMS 時，由 TIBCO Enterprise Message Service 所設定的屬性會是唯讀屬性。</span><span class="sxs-lookup"><span data-stu-id="ec3b7-133">The read-only properties are those properties that are set by TIBCO Enterprise Message Service when the message is delivered to Microsoft BizTalk Adapter for TIBCO EMS.</span></span> <span data-ttu-id="ec3b7-134">雖然您可以在訊息指派圖形的運算式中變更值，但這麼做並不會影響訊息。</span><span class="sxs-lookup"><span data-stu-id="ec3b7-134">Changing the value, although it is possible in the expression of the message assignment shape, does not affect the message.</span></span>  
  
 <span data-ttu-id="ec3b7-135">對於其他必須從 EMS 訊息移至 BizTalk Server 訊息的屬性，您必須建立屬性 DLL 並在專案中加以使用。</span><span class="sxs-lookup"><span data-stu-id="ec3b7-135">For other properties that must be moved from the EMS message to the BizTalk Server message, you must create a properties DLL and use it in the project.</span></span>  
  
 <span data-ttu-id="ec3b7-136">下列範例屬性結構描述可讓協調流程使用 `JMSXDeliveryCount` 訊息屬性。</span><span class="sxs-lookup"><span data-stu-id="ec3b7-136">The following sample properties schema enables the orchestration to use the `JMSXDeliveryCount` message property.</span></span>  
  
```  
<?xml version="1.0" encoding="utf-16"?>  
<xs:schema xmlns:b="http://schemas.microsoft.com/BizTalk/2003" targetNamespace="http://schemas.microsoft.com/BizTalk/TibcoEMS-properties" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:annotation>  
        <xs:appinfo>  
            <b:schemaInfo schema_type="property" xmlns:b="http://schemas.microsoft.com/BizTalk/2003" />  
        </xs:appinfo>  
    </xs:annotation>  
    <xs:element name="JMSXDeliveryCount" type="xs:long">  
        <xs:annotation>  
            <xs:appinfo>  
                <b:fieldInfo propertyGuid="f62f1a4b-a528-45fb-b1f8-bd880e9f46db" />  
            </xs:appinfo>  
        </xs:annotation>  
    </xs:element>  
</xs:schema>   
```  
  
 <span data-ttu-id="ec3b7-137">請確定已使用目標命名空間，只有使用此命名空間的屬性會複製到 BizTalk Server 訊息或 EMS 訊息。</span><span class="sxs-lookup"><span data-stu-id="ec3b7-137">Make sure that the target namespace is used; only properties that use this namespace are copied to the BizTalk Server message or to the EMS message.</span></span> <span data-ttu-id="ec3b7-138">如需 訊息內容屬性的詳細資訊，請參閱 BizTalk Server 文件。</span><span class="sxs-lookup"><span data-stu-id="ec3b7-138">See the BizTalk Server documentation for more information about message context properties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec3b7-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ec3b7-139">See Also</span></span>  
 [<span data-ttu-id="ec3b7-140">訊息內容屬性</span><span class="sxs-lookup"><span data-stu-id="ec3b7-140">Message Context Properties</span></span>](../core/message-context-properties2.md)