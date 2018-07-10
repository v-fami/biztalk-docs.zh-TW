---
title: BAPI 作業的訊息結構描述 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BAPI operations, message schemas for
- BAPI operations, message structure for
- BAPI operations, message actions for
ms.assetid: ef4d88e8-f31a-4b68-a303-6885b6f8c083
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 796e7beb428e6f9a4f0df63eff9cf45e9d5410bb
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36995215"
---
# <a name="message-schemas-for-bapi-operations"></a><span data-ttu-id="3ad1c-102">BAPI 作業的訊息結構描述</span><span class="sxs-lookup"><span data-stu-id="3ad1c-102">Message Schemas for BAPI Operations</span></span>
<span data-ttu-id="3ad1c-103">下列各節描述的訊息結構描述和使用上叫用 Bapi 的訊息動作[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]當做商務物件的方法。</span><span class="sxs-lookup"><span data-stu-id="3ad1c-103">The following sections describe the message schemas and message actions used to invoke BAPIs on the [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] as methods of business objects.</span></span> <span data-ttu-id="3ad1c-104">您也可以做為介面卡上的 RFC 作業叫用 Bapi。</span><span class="sxs-lookup"><span data-stu-id="3ad1c-104">You can also invoke BAPIs as RFC operations on the adapter.</span></span> <span data-ttu-id="3ad1c-105">如需有關用來叫用 Rfc 之訊息的詳細資訊，請參閱[RFC 作業的訊息結構描述](../../adapters-and-accelerators/adapter-sap/message-schemas-for-rfc-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="3ad1c-105">For more information about the messages used to invoke RFCs, see [Message Schemas for RFC Operations](../../adapters-and-accelerators/adapter-sap/message-schemas-for-rfc-operations.md).</span></span> <span data-ttu-id="3ad1c-106">不論您如何叫用 BAPI 的介面卡上，配接器永遠會叫用 BAPI 為 SAP 系統的 RFC。</span><span class="sxs-lookup"><span data-stu-id="3ad1c-106">Regardless of how you invoke a BAPI on the adapter, the adapter always invokes the BAPI as an RFC on the SAP system.</span></span> <span data-ttu-id="3ad1c-107">如需如何[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]支援 Bapi，請參閱[對 SAP 中的 Bapi 的作業](../../adapters-and-accelerators/adapter-sap/operations-on-bapis-in-sap.md)。</span><span class="sxs-lookup"><span data-stu-id="3ad1c-107">For an overview of how the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] supports BAPIs, see [Operations on BAPIs in SAP](../../adapters-and-accelerators/adapter-sap/operations-on-bapis-in-sap.md).</span></span>  

## <a name="message-structure-for-business-object-operations"></a><span data-ttu-id="3ad1c-108">適用於商務物件作業的訊息結構</span><span class="sxs-lookup"><span data-stu-id="3ad1c-108">Message Structure for Business Object Operations</span></span>  
 <span data-ttu-id="3ad1c-109">下表顯示用來叫用 BAPI 的商務物件方法為訊息結構描述。</span><span class="sxs-lookup"><span data-stu-id="3ad1c-109">The following table shows the message schemas used to invoke a BAPI as a business object method.</span></span>  

|<span data-ttu-id="3ad1c-110">作業</span><span class="sxs-lookup"><span data-stu-id="3ad1c-110">Operation</span></span>|<span data-ttu-id="3ad1c-111">XML 結構</span><span class="sxs-lookup"><span data-stu-id="3ad1c-111">XML Structure</span></span>|<span data-ttu-id="3ad1c-112">描述</span><span class="sxs-lookup"><span data-stu-id="3ad1c-112">Description</span></span>|  
|---------------|-------------------|-----------------|  
|<span data-ttu-id="3ad1c-113">[BUSOBJ_METHOD]</span><span class="sxs-lookup"><span data-stu-id="3ad1c-113">[BUSOBJ_METHOD]</span></span>|`<[BUSOBJ_METHOD] xmlns="[VERSION]/Bapi/[BUSOBJ]/">   <IN1_PARAM_NAME>v1</IN1_PARAM_NAME>   <IN2_PARAM_NAME>v2</IN2_PARAM_NAME>   …   <INOUT1_PARAM_NAME>v3</INOUT1_PARAM_NAME>   <INOUT2_PARAM_NAME>v4</INOUT2_PARAM_NAME>   …   <TABLE1_PARAM_NAME xmlns="[VERSION]/Types/Rfc/">     <STRUCT1_PARAM_NAME>       <[FIELD1_NAME]>value1</[FIELD1_NAME]>       <[FIELD2_NAME]>value2</[FIELD2_NAME]>       …     </STRUCT1_PARAM_NAME>     …   </TABLE1_PARAM_NAME>   … </[BUSOBJ_METHOD]>`|<span data-ttu-id="3ad1c-114">在 SAP 系統的商務物件方法來叫用。</span><span class="sxs-lookup"><span data-stu-id="3ad1c-114">Invoke a business object method on an SAP system.</span></span><br /><br /> <span data-ttu-id="3ad1c-115">支援匯入、 變更和資料表參數。</span><span class="sxs-lookup"><span data-stu-id="3ad1c-115">Import, changing, and table parameters are supported.</span></span>|  
|<span data-ttu-id="3ad1c-116">[BUSOBJ_METHOD]回應</span><span class="sxs-lookup"><span data-stu-id="3ad1c-116">[BUSOBJ_METHOD] Response</span></span>|`<[BUSOBJ_METHOD]Response xmlns="[VERSION]/Bapi/[BUSOBJ]/">   <OUT1_PARAM_NAME>v1</OUT1_PARAM_NAME>   <OUT2_PARAM_NAME>v2</OUT2_PARAM_NAME>   …   <INOUT1_PARAM_NAME>v3</INOUT1_PARAM_NAME>   <INOUT2_PARAM_NAME>v4</INOUT2_PARAM_NAME>   …   <TABLE1_PARAM_NAME xmlns="[VERSION]/Types/Rfc/">     <STRUCT1_PARAM_NAME>       <[FIELD1_NAME]>value1</[FIELD1_NAME]>       <[FIELD2_NAME]>value2</[FIELD2_NAME]>       …     </STRUCT1_PARAM_NAME>     …   </TABLE1_PARAM_NAME>   … </[BUSOBJ_METHOD]Response>`|<span data-ttu-id="3ad1c-117">商務物件方法的回應。</span><span class="sxs-lookup"><span data-stu-id="3ad1c-117">Business object method response.</span></span><br /><br /> <span data-ttu-id="3ad1c-118">匯出，請變更，並支援資料表參數。</span><span class="sxs-lookup"><span data-stu-id="3ad1c-118">Export, changing, and table parameters are supported.</span></span><br /><br /> <span data-ttu-id="3ad1c-119">**請注意**根據預設，資料表參數不會顯示在回應訊息中。</span><span class="sxs-lookup"><span data-stu-id="3ad1c-119">**Note** By default, table parameters are not surfaced in the response message.</span></span> <span data-ttu-id="3ad1c-120">如果您需要在回應訊息中的資料表參數時，您必須傳遞空的資料表參數在要求訊息中。</span><span class="sxs-lookup"><span data-stu-id="3ad1c-120">If you require table parameters in response message, you must pass empty table parameters in the request message.</span></span>|  

 <span data-ttu-id="3ad1c-121">[VERSION] = 訊息版本字串;比方說， http://Microsoft.LobServices.Sap/2007/03。</span><span class="sxs-lookup"><span data-stu-id="3ad1c-121">[VERSION] = The message version string; for example, http://Microsoft.LobServices.Sap/2007/03.</span></span>  

 <span data-ttu-id="3ad1c-122">[BUSOBJ_METHOD] = 商務物件方法; 的名稱比方說，CREATEFROMDAT2。</span><span class="sxs-lookup"><span data-stu-id="3ad1c-122">[BUSOBJ_METHOD] = The name of a business object method; for example, CREATEFROMDAT2.</span></span>  

 <span data-ttu-id="3ad1c-123">[IN_PARAM_NAME] = BAPI 匯入參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="3ad1c-123">[IN_PARAM_NAME] =The name of a BAPI import parameter.</span></span>  

 <span data-ttu-id="3ad1c-124">[OUT_PARAM_NAME] = BAPI 匯出參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="3ad1c-124">[OUT_PARAM_NAME] = The name of a BAPI export parameter.</span></span>  

 <span data-ttu-id="3ad1c-125">[INOUT_PARAM_NAME] = BAPI 變更參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="3ad1c-125">[INOUT_PARAM_NAME] = The name of a BAPI changing parameter.</span></span>  

 <span data-ttu-id="3ad1c-126">[TABLE_PARAM_NAME] = BAPI 資料表參數名稱。</span><span class="sxs-lookup"><span data-stu-id="3ad1c-126">[TABLE_PARAM_NAME] = The name of a BAPI table parameter.</span></span>  

 <span data-ttu-id="3ad1c-127">[STRUCT_PARAM_NAME] = BAPI 結構參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="3ad1c-127">[STRUCT_PARAM_NAME] = The name of a BAPI structure parameter.</span></span>  

## <a name="message-actions-for-business-object-operations"></a><span data-ttu-id="3ad1c-128">適用於商務物件作業的訊息動作</span><span class="sxs-lookup"><span data-stu-id="3ad1c-128">Message Actions for Business Object Operations</span></span>  
 <span data-ttu-id="3ad1c-129">下表顯示用來叫用 Bapi 當做商務物件方法的訊息動作。</span><span class="sxs-lookup"><span data-stu-id="3ad1c-129">The following table shows the message actions that are used to invoke BAPIs as business object methods.</span></span>  


|        <span data-ttu-id="3ad1c-130">作業</span><span class="sxs-lookup"><span data-stu-id="3ad1c-130">Operation</span></span>         |                            <span data-ttu-id="3ad1c-131">訊息的動作</span><span class="sxs-lookup"><span data-stu-id="3ad1c-131">Message Action</span></span>                             |                                                   <span data-ttu-id="3ad1c-132">範例</span><span class="sxs-lookup"><span data-stu-id="3ad1c-132">Example</span></span>                                                    |
|--------------------------|-----------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|
|     <span data-ttu-id="3ad1c-133">[BUSOBJ_METHOD]</span><span class="sxs-lookup"><span data-stu-id="3ad1c-133">[BUSOBJ_METHOD]</span></span>      |     <span data-ttu-id="3ad1c-134">[VERSION]/Bapi/[BUSOBJ_NAME]/[BUSOBJ_METHOD]/[BAPI_RFC_NAME]</span><span class="sxs-lookup"><span data-stu-id="3ad1c-134">[VERSION]/Bapi/[BUSOBJ_NAME]/[BUSOBJ_METHOD]/[BAPI_RFC_NAME]</span></span>      |     http://Microsoft.LobServices.Sap/2007/03/Bapi/BUS2032/CREATEFROMDAT2/BAPI_SALESORDER_CREATEFROMDAT2      |
| <span data-ttu-id="3ad1c-135">[BUSOBJ_METHOD]回應</span><span class="sxs-lookup"><span data-stu-id="3ad1c-135">[BUSOBJ_METHOD] Response</span></span> | <span data-ttu-id="3ad1c-136">[VERSION]/Bapi/[BUSOBJ_NAME]/[BUSOBJ_METHOD]/[BAPI_RFC_NAME]/response</span><span class="sxs-lookup"><span data-stu-id="3ad1c-136">[VERSION]/Bapi/[BUSOBJ_NAME]/[BUSOBJ_METHOD]/[BAPI_RFC_NAME]/response</span></span> | http://Microsoft.LobServices.Sap/2007/03/Bapi/BUS2032/CREATEFROMDAT2/BAPI_SALESORDER_CREATEFROMDAT2/response |

 <span data-ttu-id="3ad1c-137">[VERSION] = 訊息版本字串;比方說， http://Microsoft.LobServices.Sap/2007/03。</span><span class="sxs-lookup"><span data-stu-id="3ad1c-137">[VERSION] = The message version string; for example, http://Microsoft.LobServices.Sap/2007/03.</span></span>  

 <span data-ttu-id="3ad1c-138">[BUSOBJ_NAME] = 商務物件的名稱比方說，BUS2032。</span><span class="sxs-lookup"><span data-stu-id="3ad1c-138">[BUSOBJ_NAME] = The name of the business object; for example, BUS2032.</span></span>  

 <span data-ttu-id="3ad1c-139">[BUSOBJ_METHOD] = 商務物件方法比方說，CREATEFROMDAT2。</span><span class="sxs-lookup"><span data-stu-id="3ad1c-139">[BUSOBJ_METHOD] = The method of the business object; for example, CREATEFROMDAT2.</span></span>  

 <span data-ttu-id="3ad1c-140">[BAPI_RFC_NAME] = [RFC 名稱 BAPI;比方說，BAPI_SALESORDER_CREATEFROMDAT2。</span><span class="sxs-lookup"><span data-stu-id="3ad1c-140">[BAPI_RFC_NAME] = The RFC name for the BAPI; for example, BAPI_SALESORDER_CREATEFROMDAT2.</span></span>  

## <a name="see-also"></a><span data-ttu-id="3ad1c-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3ad1c-141">See Also</span></span>  
 [<span data-ttu-id="3ad1c-142">訊息和訊息結構描述，BizTalk adapter for mySAP Business Suite</span><span class="sxs-lookup"><span data-stu-id="3ad1c-142">Messages and Message Schemas for BizTalk Adapter for mySAP Business Suite</span></span>](../../adapters-and-accelerators/adapter-sap/messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md)