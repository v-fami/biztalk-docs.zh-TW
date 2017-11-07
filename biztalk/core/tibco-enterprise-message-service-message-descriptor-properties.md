---
title: "TIBCO EMS 訊息描述元屬性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc164c12-6dc3-4b74-9aa9-024e18faf80a
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c1a2a7d6529cffba6afa3969964d1ea436d7fcda
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="tibco-enterprise-message-service-message-descriptor-properties"></a><span data-ttu-id="7ea34-102">TIBCO Enterprise Message Service 訊息描述元屬性</span><span class="sxs-lookup"><span data-stu-id="7ea34-102">TIBCO Enterprise Message Service Message Descriptor Properties</span></span>

## <a name="descriptor-properties-and-values"></a><span data-ttu-id="7ea34-103">描述元屬性和值</span><span class="sxs-lookup"><span data-stu-id="7ea34-103">Descriptor properties, and values</span></span>
<span data-ttu-id="7ea34-104">下表顯示所有可用的「訊息描述元」(TibcoEMSMD 結構)」屬性及其對應的類型與值。</span><span class="sxs-lookup"><span data-stu-id="7ea34-104">The following table shows the complete set of available Message Descriptor (TibcoEMSMD structure) properties and their corresponding types and values.</span></span>  
  
|<span data-ttu-id="7ea34-105">名稱</span><span class="sxs-lookup"><span data-stu-id="7ea34-105">Name</span></span>|<span data-ttu-id="7ea34-106">型別</span><span class="sxs-lookup"><span data-stu-id="7ea34-106">Type</span></span>|<span data-ttu-id="7ea34-107">Value</span><span class="sxs-lookup"><span data-stu-id="7ea34-107">Value</span></span>|<span data-ttu-id="7ea34-108">注意</span><span class="sxs-lookup"><span data-stu-id="7ea34-108">Notes</span></span>|  
|----------|----------|-----------|-----------|  
|<span data-ttu-id="7ea34-109">TibcoEMS .CorrelationID</span><span class="sxs-lookup"><span data-stu-id="7ea34-109">TibcoEMS .CorrelationID</span></span>|<span data-ttu-id="7ea34-110">string</span><span class="sxs-lookup"><span data-stu-id="7ea34-110">string</span></span>|||  
|<span data-ttu-id="7ea34-111">TibcoEMS .DelieveryMode</span><span class="sxs-lookup"><span data-stu-id="7ea34-111">TibcoEMS .DelieveryMode</span></span>|<span data-ttu-id="7ea34-112">string</span><span class="sxs-lookup"><span data-stu-id="7ea34-112">string</span></span>|<span data-ttu-id="7ea34-113">PERSISENT 或 NON-PERSISTENT 之一</span><span class="sxs-lookup"><span data-stu-id="7ea34-113">One of PERSISENT or NON-PERSISTENT</span></span>||  
|<span data-ttu-id="7ea34-114">TibcoEMS .Destination</span><span class="sxs-lookup"><span data-stu-id="7ea34-114">TibcoEMS .Destination</span></span>|<span data-ttu-id="7ea34-115">string</span><span class="sxs-lookup"><span data-stu-id="7ea34-115">string</span></span>||<span data-ttu-id="7ea34-116">唯讀</span><span class="sxs-lookup"><span data-stu-id="7ea34-116">Read-only</span></span>|  
|<span data-ttu-id="7ea34-117">TibcoEMS .Expiration</span><span class="sxs-lookup"><span data-stu-id="7ea34-117">TibcoEMS .Expiration</span></span>|<span data-ttu-id="7ea34-118">long</span><span class="sxs-lookup"><span data-stu-id="7ea34-118">long</span></span>|||  
|<span data-ttu-id="7ea34-119">TibcoEMS .MessageID</span><span class="sxs-lookup"><span data-stu-id="7ea34-119">TibcoEMS .MessageID</span></span>|<span data-ttu-id="7ea34-120">string</span><span class="sxs-lookup"><span data-stu-id="7ea34-120">string</span></span>||<span data-ttu-id="7ea34-121">唯讀</span><span class="sxs-lookup"><span data-stu-id="7ea34-121">Read-only</span></span>|  
|<span data-ttu-id="7ea34-122">TibcoEMS .Priority</span><span class="sxs-lookup"><span data-stu-id="7ea34-122">TibcoEMS .Priority</span></span>|<span data-ttu-id="7ea34-123">integer</span><span class="sxs-lookup"><span data-stu-id="7ea34-123">integer</span></span>|<span data-ttu-id="7ea34-124">從 0 到 9</span><span class="sxs-lookup"><span data-stu-id="7ea34-124">From 0 to 9</span></span>||  
|<span data-ttu-id="7ea34-125">TibcoEMS .Redelivered</span><span class="sxs-lookup"><span data-stu-id="7ea34-125">TibcoEMS .Redelivered</span></span>|<span data-ttu-id="7ea34-126">boolean</span><span class="sxs-lookup"><span data-stu-id="7ea34-126">boolean</span></span>||<span data-ttu-id="7ea34-127">唯讀</span><span class="sxs-lookup"><span data-stu-id="7ea34-127">Read-only</span></span>|  
|<span data-ttu-id="7ea34-128">TibcoEMS .ReplyTo</span><span class="sxs-lookup"><span data-stu-id="7ea34-128">TibcoEMS .ReplyTo</span></span>|<span data-ttu-id="7ea34-129">string</span><span class="sxs-lookup"><span data-stu-id="7ea34-129">string</span></span>|<span data-ttu-id="7ea34-130">與 Destination 類似</span><span class="sxs-lookup"><span data-stu-id="7ea34-130">Similar to Destination</span></span>||  
|<span data-ttu-id="7ea34-131">TibcoEMS .Timestamp</span><span class="sxs-lookup"><span data-stu-id="7ea34-131">TibcoEMS .Timestamp</span></span>|<span data-ttu-id="7ea34-132">long</span><span class="sxs-lookup"><span data-stu-id="7ea34-132">long</span></span>||<span data-ttu-id="7ea34-133">唯讀</span><span class="sxs-lookup"><span data-stu-id="7ea34-133">Read-only</span></span>|  
  
 <span data-ttu-id="7ea34-134">當訊息傳遞給 Microsoft BizTalk Adapter for TIBCO EMS 時，由 TIBCO Enterprise Message Service 所設定的屬性會是唯讀屬性。</span><span class="sxs-lookup"><span data-stu-id="7ea34-134">The read-only properties are those properties that are set by TIBCO Enterprise Message Service when the message is delivered to Microsoft BizTalk Adapter for TIBCO EMS.</span></span> <span data-ttu-id="7ea34-135">雖然您可以在訊息指派圖形的運算式中變更值，但這麼做並不會影響訊息。</span><span class="sxs-lookup"><span data-stu-id="7ea34-135">Changing the value, although it is possible in the expression of the message assignment shape, does not affect the message.</span></span>  
  
 <span data-ttu-id="7ea34-136">對於其他必須從 EMS 訊息移至 BizTalk Server 訊息的屬性，您必須建立屬性 DLL 並在專案中加以使用。</span><span class="sxs-lookup"><span data-stu-id="7ea34-136">For other properties that must be moved from the EMS message to the BizTalk Server message, you must create a properties DLL and use it in the project.</span></span>  
  
 <span data-ttu-id="7ea34-137">下列範例屬性結構描述可讓協調流程使用 `JMSXDeliveryCount` 訊息屬性。</span><span class="sxs-lookup"><span data-stu-id="7ea34-137">The following sample properties schema enables the orchestration to use the `JMSXDeliveryCount` message property.</span></span>  
  
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
  
 <span data-ttu-id="7ea34-138">請確定已使用目標命名空間，只有使用此命名空間的屬性會複製到 BizTalk Server 訊息或 EMS 訊息。</span><span class="sxs-lookup"><span data-stu-id="7ea34-138">Make sure that the target namespace is used; only properties that use this namespace are copied to the BizTalk Server message or to the EMS message.</span></span> <span data-ttu-id="7ea34-139">如需 訊息內容屬性的詳細資訊，請參閱 BizTalk Server 文件。</span><span class="sxs-lookup"><span data-stu-id="7ea34-139">See the BizTalk Server documentation for more information about message context properties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ea34-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7ea34-140">See Also</span></span>  
[<span data-ttu-id="7ea34-141">TIBCO EMS 訊息內容屬性</span><span class="sxs-lookup"><span data-stu-id="7ea34-141">TIBCO EMS message context properties</span></span>](../core/message-context-properties-in-biztalk-server.md)