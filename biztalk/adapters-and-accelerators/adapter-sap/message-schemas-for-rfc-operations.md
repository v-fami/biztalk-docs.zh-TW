---
title: RFC 作業的訊息結構描述 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- RFC operations, message structure for
- RFC operations, message actions for
ms.assetid: 50cd9b28-2e66-4c76-9d19-f0da6e7b8e10
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ef9d1dfe3ff3cef27269facfe89d3aea8f43cb10
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22217302"
---
# <a name="message-schemas-for-rfc-operations"></a><span data-ttu-id="bf147-102">RFC 作業的訊息結構描述</span><span class="sxs-lookup"><span data-stu-id="bf147-102">Message Schemas for RFC Operations</span></span>
<span data-ttu-id="bf147-103">[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]呈現 SAP 遠端函式呼叫 (RFC) 做為作業。</span><span class="sxs-lookup"><span data-stu-id="bf147-103">The [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] surfaces SAP Remote Function Calls (RFC) as operations.</span></span> <span data-ttu-id="bf147-104">本主題包含的訊息結構描述 」 和 「 用於 RFC 作業的訊息動作的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="bf147-104">This topic contains information about the message schemas and message actions used for RFC operations.</span></span> <span data-ttu-id="bf147-105">訊息結構是相同的輸入和輸出 RFC 作業。</span><span class="sxs-lookup"><span data-stu-id="bf147-105">The message structure is the same for inbound and outbound RFC operations.</span></span> <span data-ttu-id="bf147-106">如需配接器支援的 RFC 作業的概觀，請參閱[作業中 SAP Rfc](../../adapters-and-accelerators/adapter-sap/operations-on-rfcs-in-sap.md)。</span><span class="sxs-lookup"><span data-stu-id="bf147-106">For an overview of the RFC operations that the adapter supports, see [Operations on RFCs in SAP](../../adapters-and-accelerators/adapter-sap/operations-on-rfcs-in-sap.md).</span></span>  
  
 <span data-ttu-id="bf147-107">您也可以使用做為介面卡上的 RFC 作業叫用的 Bapi。</span><span class="sxs-lookup"><span data-stu-id="bf147-107">You can also invoke BAPIs as RFC operations on the adapter.</span></span> <span data-ttu-id="bf147-108">本主題會包含這類引動過程訊息結構的範例。</span><span class="sxs-lookup"><span data-stu-id="bf147-108">An example of the message structure for such an invocation is included in this topic.</span></span>  
  
## <a name="message-structure-for-rfc-operations"></a><span data-ttu-id="bf147-109">RFC 作業的訊息結構</span><span class="sxs-lookup"><span data-stu-id="bf147-109">Message Structure for RFC Operations</span></span>  
 <span data-ttu-id="bf147-110">下表顯示 RFC 訊息結構描述。</span><span class="sxs-lookup"><span data-stu-id="bf147-110">The following table shows the RFC message schemas.</span></span> <span data-ttu-id="bf147-111">每個 RFC 作業包含要求訊息和回覆 （回應） 的訊息。</span><span class="sxs-lookup"><span data-stu-id="bf147-111">Each RFC operation consists of a request message and a reply (response) message.</span></span>  
  
|<span data-ttu-id="bf147-112">訊息</span><span class="sxs-lookup"><span data-stu-id="bf147-112">Message</span></span>|<span data-ttu-id="bf147-113">XML 訊息結構</span><span class="sxs-lookup"><span data-stu-id="bf147-113">XML Message Structure</span></span>|<span data-ttu-id="bf147-114">Description</span><span class="sxs-lookup"><span data-stu-id="bf147-114">Description</span></span>|  
|-------------|---------------------------|-----------------|  
|<span data-ttu-id="bf147-115">RFC</span><span class="sxs-lookup"><span data-stu-id="bf147-115">RFC</span></span><br /><br /> <span data-ttu-id="bf147-116">([RFC_NAME])</span><span class="sxs-lookup"><span data-stu-id="bf147-116">([RFC_NAME])</span></span>|`<[RFC_NAME] xmlns="[VERSION]/Rfc/">   <IN1_PARAM_NAME>v1</IN1_PARAM_NAME>   <IN2_PARAM_NAME>v2</IN2_PARAM_NAME>   …   <INOUT1_PARAM_NAME>v3</INOUT1_PARAM_NAME>   <INOUT2_PARAM_NAME>v4</INOUT2_PARAM_NAME>   …   <TABLE1_PARAM_NAME xmlns="[VERSION]/Types/Rfc/">     <STRUCT1_PARAM_NAME>       <[FIELD1_NAME]>value1</[FIELD1_NAME]>       <[FIELD2_NAME]>value2</[FIELD2_NAME]>       …     </STRUCT1_PARAM_NAME>     …   </TABLE1_PARAM_NAME>   … </[RFC_NAME]>`|<span data-ttu-id="bf147-117">叫用的 RFC，SAP 系統上。</span><span class="sxs-lookup"><span data-stu-id="bf147-117">Invoke an RFC on the SAP system.</span></span><br /><br /> <span data-ttu-id="bf147-118">-匯入，變更，以及支援資料表參數。</span><span class="sxs-lookup"><span data-stu-id="bf147-118">- Import, changing, and table parameters are supported.</span></span><br /><br /> <span data-ttu-id="bf147-119">-匯入，變更參數可以是 SAP 結構類型、 SAP 資料表類型或 SAP 簡單資料類型。</span><span class="sxs-lookup"><span data-stu-id="bf147-119">- Import and changing parameters can be of SAP STRUCTURE TYPES, SAP TABLE TYPES or SAP simple data types.</span></span>|  
|<span data-ttu-id="bf147-120">RFC 回應 （[RFC_NAME] 回應）</span><span class="sxs-lookup"><span data-stu-id="bf147-120">RFC Response ([RFC_NAME]Response)</span></span>|`<[RFC_NAME]Response xmlns="[VERSION]/Rfc/">   <OUT1_PARAM_NAME>v1</OUT1_PARAM_NAME>   <OUT2_PARAM_NAME>v2</OUT2_PARAM_NAME>   …   <INOUT1_PARAM_NAME>v3</INOUT1_PARAM_NAME>   <INOUT2_PARAM_NAME>v4</INOUT2_PARAM_NAME>   …   <TABLE1_PARAM_NAME>     <STRUCT1_PARAM_NAME>       <[FIELD1_NAME]>value1</[FIELD1_NAME]>       <[FIELD2_NAME]>value2</[FIELD2_NAME]>       …     </STRUCT1_PARAM_NAME>     …   </TABLE1_PARAM_NAME>   … </[RFC_NAME]Response>`|<span data-ttu-id="bf147-121">傳回的 RFC。</span><span class="sxs-lookup"><span data-stu-id="bf147-121">RFC return.</span></span><br /><br /> <span data-ttu-id="bf147-122">-Export，變更，並支援資料表參數。</span><span class="sxs-lookup"><span data-stu-id="bf147-122">- Export, changing, and table parameters are supported.</span></span><br /><br /> <span data-ttu-id="bf147-123">**注意：** 根據預設，資料表參數不會顯示在回應訊息中。</span><span class="sxs-lookup"><span data-stu-id="bf147-123">**Note:** By default, table parameters are not surfaced in the response message.</span></span> <span data-ttu-id="bf147-124">如果您需要在回應訊息中的資料表參數時，您必須在要求訊息中傳遞空資料表參數。</span><span class="sxs-lookup"><span data-stu-id="bf147-124">If you require table parameters in response message, you must pass empty table parameters in the request message.</span></span><br /><br /> <span data-ttu-id="bf147-125">-匯入，變更參數可以是 SAP 結構類型、 SAP 資料表類型或 SAP 簡單資料類型。</span><span class="sxs-lookup"><span data-stu-id="bf147-125">- Import and changing parameters can be of SAP STRUCTURE TYPES, SAP TABLE TYPES or SAP simple data types.</span></span>|  
|<span data-ttu-id="bf147-126">RfcGetAttributes</span><span class="sxs-lookup"><span data-stu-id="bf147-126">RfcGetAttributes</span></span><br /><br /> <span data-ttu-id="bf147-127">(RfcGetAttributes)</span><span class="sxs-lookup"><span data-stu-id="bf147-127">(RfcGetAttributes)</span></span>|`<RfcGetAttributes> </RfcGetAttributes>`|<span data-ttu-id="bf147-128">RfcGetAttributes 是呈現由 RFC SDK API 作業[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="bf147-128">RfcGetAttributes is an RFC SDK API operation that is surfaced by the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span> <span data-ttu-id="bf147-129">RfcGetAttributes 作業可讓用戶端程式擷取語言、 系統識別碼，以及與 RFC 連線相關聯的夥伴字碼頁。</span><span class="sxs-lookup"><span data-stu-id="bf147-129">The RfcGetAttributes operation enables a client program to retrieve the language, the system ID, and the partner code page that are associated with the RFC connection.</span></span>|  
|<span data-ttu-id="bf147-130">RfcGetAttributes 回應</span><span class="sxs-lookup"><span data-stu-id="bf147-130">RfcGetAttributes Response</span></span><br /><br /> <span data-ttu-id="bf147-131">(RfcGetAttributesResponse)</span><span class="sxs-lookup"><span data-stu-id="bf147-131">(RfcGetAttributesResponse)</span></span>|`<RfcGetAttributesResponse>   <Language>lang</Language>   <SysId>id</SysId>   <PartnerCodePage>pnrcp</PartnerCodePage> </RfcGetAttributesResponse>`|<span data-ttu-id="bf147-132">RfcGetAttributes 作業的回應傳回語言、 系統識別碼，以及與 RFC 連線相關聯的夥伴字碼頁。</span><span class="sxs-lookup"><span data-stu-id="bf147-132">The response to the RfcGetAttributes operation returns the language, the system ID, and the partner code page that are associated with the RFC connection.</span></span>|  
  
 <span data-ttu-id="bf147-133">[版本] = 訊息版本字串。例如，http://Microsoft.LobServices.SAP/2007/03。</span><span class="sxs-lookup"><span data-stu-id="bf147-133">[VERSION] = The message version string; for example, http://Microsoft.LobServices.SAP/2007/03.</span></span>  
  
 <span data-ttu-id="bf147-134">[RFC_NAME] = RFC; 的名稱例如，RFC_CUSTOMER_GET。</span><span class="sxs-lookup"><span data-stu-id="bf147-134">[RFC_NAME] = Name of the RFC; for example, RFC_CUSTOMER_GET.</span></span>  
  
 <span data-ttu-id="bf147-135">[IN_PARAM_NAME] = RFC 匯入參數名稱。</span><span class="sxs-lookup"><span data-stu-id="bf147-135">[IN_PARAM_NAME] = The name of an RFC Import parameter.</span></span>  
  
 <span data-ttu-id="bf147-136">[OUT_PARAM_NAME] = 匯出 RFC 參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="bf147-136">[OUT_PARAM_NAME] = The name of an RFC Export parameter.</span></span>  
  
 <span data-ttu-id="bf147-137">[INOUT_PARAM_NAME] = RFC 變更參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="bf147-137">[INOUT_PARAM_NAME] = The name of an RFC Changing parameter.</span></span>  
  
 <span data-ttu-id="bf147-138">[TABLE_PARAM_NAME] = RFC 資料表參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="bf147-138">[TABLE_PARAM_NAME] = The name of an RFC Table parameter.</span></span>  
  
 <span data-ttu-id="bf147-139">[STRUCT_PARAM_NAME] = RFC 結構參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="bf147-139">[STRUCT_PARAM_NAME] = The name of an RFC Structure parameter.</span></span>  
  
## <a name="message-actions-for-rfc-operations"></a><span data-ttu-id="bf147-140">RFC 作業的訊息動作</span><span class="sxs-lookup"><span data-stu-id="bf147-140">Message Actions for RFC Operations</span></span>  
 <span data-ttu-id="bf147-141">下表顯示 RFC 作業的訊息動作。</span><span class="sxs-lookup"><span data-stu-id="bf147-141">The following table shows the message actions for RFC operations.</span></span>  
  
|<span data-ttu-id="bf147-142">作業</span><span class="sxs-lookup"><span data-stu-id="bf147-142">Operation</span></span>|<span data-ttu-id="bf147-143">訊息的動作</span><span class="sxs-lookup"><span data-stu-id="bf147-143">Message Action</span></span>|<span data-ttu-id="bf147-144">範例</span><span class="sxs-lookup"><span data-stu-id="bf147-144">Example</span></span>|  
|---------------|--------------------|-------------|  
|<span data-ttu-id="bf147-145">[RFC_NAME]</span><span class="sxs-lookup"><span data-stu-id="bf147-145">[RFC_NAME]</span></span>|<span data-ttu-id="bf147-146">[版本] /Rfc/ [RFC_NAME]</span><span class="sxs-lookup"><span data-stu-id="bf147-146">[VERSION]/Rfc/[RFC_NAME]</span></span>|<span data-ttu-id="bf147-147">http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_CUSTOMER_GET</span><span class="sxs-lookup"><span data-stu-id="bf147-147">http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_CUSTOMER_GET</span></span>|  
|<span data-ttu-id="bf147-148">[RFC_NAME]回應</span><span class="sxs-lookup"><span data-stu-id="bf147-148">[RFC_NAME] Response</span></span>|<span data-ttu-id="bf147-149">[版本] /Rfc/ [RFC_NAME] / 回應</span><span class="sxs-lookup"><span data-stu-id="bf147-149">[VERSION]/Rfc/[RFC_NAME]/response</span></span>|<span data-ttu-id="bf147-150">http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_CUSTOMER_GET/response</span><span class="sxs-lookup"><span data-stu-id="bf147-150">http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_CUSTOMER_GET/response</span></span>|  
|<span data-ttu-id="bf147-151">RfcGetAttributes</span><span class="sxs-lookup"><span data-stu-id="bf147-151">RfcGetAttributes</span></span>|<span data-ttu-id="bf147-152">[版本] / RfcGetAttributes</span><span class="sxs-lookup"><span data-stu-id="bf147-152">[VERSION]/RfcGetAttributes</span></span>|<span data-ttu-id="bf147-153">http://Microsoft.LobServices.Sap/2007/03/RfcGetAttributes</span><span class="sxs-lookup"><span data-stu-id="bf147-153">http://Microsoft.LobServices.Sap/2007/03/RfcGetAttributes</span></span>|  
|<span data-ttu-id="bf147-154">RfcGetAttributes 回應</span><span class="sxs-lookup"><span data-stu-id="bf147-154">RfcGetAttributes Response</span></span>|<span data-ttu-id="bf147-155">[版本/RfcGetAttributes/回應</span><span class="sxs-lookup"><span data-stu-id="bf147-155">[VERSION/RfcGetAttributes/response</span></span>|<span data-ttu-id="bf147-156">http://Microsoft.LobServices.Sap/2007/03/RfcGetAttributes/response</span><span class="sxs-lookup"><span data-stu-id="bf147-156">http://Microsoft.LobServices.Sap/2007/03/RfcGetAttributes/response</span></span>|  
  
 <span data-ttu-id="bf147-157">[版本] = 訊息版本字串。例如，http://Microsoft.LobServices.Sap/2007/03。</span><span class="sxs-lookup"><span data-stu-id="bf147-157">[VERSION] = The message version string; for example, http://Microsoft.LobServices.Sap/2007/03.</span></span>  
  
 <span data-ttu-id="bf147-158">[RFC_NAME] = 要叫用; RFC 的名稱例如，RFC_CUSTOMER_GET。</span><span class="sxs-lookup"><span data-stu-id="bf147-158">[RFC_NAME] = The name of the RFC to be invoked; for example, RFC_CUSTOMER_GET.</span></span>  
  
## <a name="invoking-a-bapi-as-an-rfc-operation"></a><span data-ttu-id="bf147-159">以 RFC 作業叫用 BAPI</span><span class="sxs-lookup"><span data-stu-id="bf147-159">Invoking a BAPI as an RFC Operation</span></span>  
 <span data-ttu-id="bf147-160">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]呈現 Bapi 同時 RFC 作業和商務物件的方法。</span><span class="sxs-lookup"><span data-stu-id="bf147-160">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] surfaces BAPIs both as RFC operations and as methods of business objects.</span></span> <span data-ttu-id="bf147-161">做為 RFC 作業便會依名稱顯示 Bapi。</span><span class="sxs-lookup"><span data-stu-id="bf147-161">As RFC operations, BAPIs are surfaced by name.</span></span> <span data-ttu-id="bf147-162">如需使用商務物件介面叫用的 Bapi 的詳細資訊，請參閱[SAP 中的 Bapi 作業](../../adapters-and-accelerators/adapter-sap/operations-on-bapis-in-sap.md)。</span><span class="sxs-lookup"><span data-stu-id="bf147-162">For more information about invoking BAPIs by using the business object interface, see [Operations on BAPIs in SAP](../../adapters-and-accelerators/adapter-sap/operations-on-bapis-in-sap.md).</span></span>  
  
 <span data-ttu-id="bf147-163">下列 XML 顯示 BAPI (BAPI_CUSTOMER_GETDETAIL2) 以 RFC 叫用的訊息結構。</span><span class="sxs-lookup"><span data-stu-id="bf147-163">The following XML shows the message structure for a BAPI (BAPI_CUSTOMER_GETDETAIL2) that is invoked as an RFC.</span></span> <span data-ttu-id="bf147-164">這項作業的訊息動作是： http://Microsoft.LobServices.Sap/2007/03/Rfc/BAPI_CUSTOMER_GETDETAIL2。</span><span class="sxs-lookup"><span data-stu-id="bf147-164">The message action for this operation is: http://Microsoft.LobServices.Sap/2007/03/Rfc/BAPI_CUSTOMER_GETDETAIL2.</span></span>  
  
```  
<BAPI_CUSTOMER_GETDETAIL2 xmlns="http://Microsoft.LobServices.Sap/2007/03/Rfc/">  
  <COMPANYCODE>1001</COMPANYCODE>  
  <CUSTOMERNO>0000001001</CUSTOMERNO>  
  <CUSTOMERBANKDETAIL>  
    <BAPICUSTOMER_02 xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">  
      <CUSTOMER />  
      <BANK_CTRY />  
      <BANK_KEY />  
      <BANK_ACCT />  
      <CTRL_KEY />  
      <PARTNER_BK />  
      <COLL_AUTH />  
      <BANK_REF />  
    </BAPICUSTOMER_02>  
  </CUSTOMERBANKDETAIL>  
</BAPI_CUSTOMER_GETDETAIL2>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bf147-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bf147-165">See Also</span></span>  
 [<span data-ttu-id="bf147-166">訊息和訊息結構描述，BizTalk adapter for mySAP Business Suite</span><span class="sxs-lookup"><span data-stu-id="bf147-166">Messages and Message Schemas for BizTalk Adapter for mySAP Business Suite</span></span>](../../adapters-and-accelerators/adapter-sap/messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md)