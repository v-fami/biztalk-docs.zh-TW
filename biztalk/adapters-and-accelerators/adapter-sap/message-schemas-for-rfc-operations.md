---
title: RFC 作業的訊息結構描述 |Microsoft Docs
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
ms.openlocfilehash: 156b8e8c218c4ad23d49959323ed324b0c7cdfd0
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36972847"
---
# <a name="message-schemas-for-rfc-operations"></a><span data-ttu-id="13885-102">RFC 作業的訊息結構描述</span><span class="sxs-lookup"><span data-stu-id="13885-102">Message Schemas for RFC Operations</span></span>
<span data-ttu-id="13885-103">[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]呈現 SAP 遠端函式呼叫 (RFC) 做為作業。</span><span class="sxs-lookup"><span data-stu-id="13885-103">The [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] surfaces SAP Remote Function Calls (RFC) as operations.</span></span> <span data-ttu-id="13885-104">本主題包含的訊息結構描述 」 和 「 用於 RFC 作業的訊息動作的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="13885-104">This topic contains information about the message schemas and message actions used for RFC operations.</span></span> <span data-ttu-id="13885-105">訊息結構是輸入和輸出的 RFC 作業的相同。</span><span class="sxs-lookup"><span data-stu-id="13885-105">The message structure is the same for inbound and outbound RFC operations.</span></span> <span data-ttu-id="13885-106">如需配接器支援 RFC 作業的概觀，請參閱 <<c0> [ 對 sap Rfc 的作業](../../adapters-and-accelerators/adapter-sap/operations-on-rfcs-in-sap.md)。</span><span class="sxs-lookup"><span data-stu-id="13885-106">For an overview of the RFC operations that the adapter supports, see [Operations on RFCs in SAP](../../adapters-and-accelerators/adapter-sap/operations-on-rfcs-in-sap.md).</span></span>  

 <span data-ttu-id="13885-107">您也可以做為介面卡上的 RFC 作業叫用 Bapi。</span><span class="sxs-lookup"><span data-stu-id="13885-107">You can also invoke BAPIs as RFC operations on the adapter.</span></span> <span data-ttu-id="13885-108">本主題會包含這類引動過程的訊息結構的範例。</span><span class="sxs-lookup"><span data-stu-id="13885-108">An example of the message structure for such an invocation is included in this topic.</span></span>  

## <a name="message-structure-for-rfc-operations"></a><span data-ttu-id="13885-109">RFC 作業的訊息結構</span><span class="sxs-lookup"><span data-stu-id="13885-109">Message Structure for RFC Operations</span></span>  
 <span data-ttu-id="13885-110">下表顯示 RFC 訊息結構描述。</span><span class="sxs-lookup"><span data-stu-id="13885-110">The following table shows the RFC message schemas.</span></span> <span data-ttu-id="13885-111">每個 RFC 作業是由要求訊息和回覆 （回應） 訊息所組成。</span><span class="sxs-lookup"><span data-stu-id="13885-111">Each RFC operation consists of a request message and a reply (response) message.</span></span>  


|                             <span data-ttu-id="13885-112">訊息</span><span class="sxs-lookup"><span data-stu-id="13885-112">Message</span></span>                              |                                                                                                                                                                                                                         <span data-ttu-id="13885-113">XML 訊息結構</span><span class="sxs-lookup"><span data-stu-id="13885-113">XML Message Structure</span></span>                                                                                                                                                                                                                          |                                                                                                                                                                                                     <span data-ttu-id="13885-114">描述</span><span class="sxs-lookup"><span data-stu-id="13885-114">Description</span></span>                                                                                                                                                                                                      |
|------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                   <span data-ttu-id="13885-115">RFC</span><span class="sxs-lookup"><span data-stu-id="13885-115">RFC</span></span><br /><br /> <span data-ttu-id="13885-116">([RFC_NAME])</span><span class="sxs-lookup"><span data-stu-id="13885-116">([RFC_NAME])</span></span>                   | `<[RFC_NAME] xmlns="[VERSION]/Rfc/">   <IN1_PARAM_NAME>v1</IN1_PARAM_NAME>   <IN2_PARAM_NAME>v2</IN2_PARAM_NAME>   …   <INOUT1_PARAM_NAME>v3</INOUT1_PARAM_NAME>   <INOUT2_PARAM_NAME>v4</INOUT2_PARAM_NAME>   …   <TABLE1_PARAM_NAME xmlns="[VERSION]/Types/Rfc/">     <STRUCT1_PARAM_NAME>       <[FIELD1_NAME]>value1</[FIELD1_NAME]>       <[FIELD2_NAME]>value2</[FIELD2_NAME]>       …     </STRUCT1_PARAM_NAME>     …   </TABLE1_PARAM_NAME>   … </[RFC_NAME]>` |                                                                                              <span data-ttu-id="13885-117">叫用 RFC，SAP 系統上。</span><span class="sxs-lookup"><span data-stu-id="13885-117">Invoke an RFC on the SAP system.</span></span><br /><br /> <span data-ttu-id="13885-118">-匯入，變更，並支援資料表參數。</span><span class="sxs-lookup"><span data-stu-id="13885-118">- Import, changing, and table parameters are supported.</span></span><br /><br /> <span data-ttu-id="13885-119">-匯入並變更參數可以是 SAP 結構類型，SAP 資料表類型或 SAP 簡單資料型別。</span><span class="sxs-lookup"><span data-stu-id="13885-119">- Import and changing parameters can be of SAP STRUCTURE TYPES, SAP TABLE TYPES or SAP simple data types.</span></span>                                                                                              |
|                <span data-ttu-id="13885-120">RFC 回應 （[RFC_NAME] 回應）</span><span class="sxs-lookup"><span data-stu-id="13885-120">RFC Response ([RFC_NAME]Response)</span></span>                 |     `<[RFC_NAME]Response xmlns="[VERSION]/Rfc/">   <OUT1_PARAM_NAME>v1</OUT1_PARAM_NAME>   <OUT2_PARAM_NAME>v2</OUT2_PARAM_NAME>   …   <INOUT1_PARAM_NAME>v3</INOUT1_PARAM_NAME>   <INOUT2_PARAM_NAME>v4</INOUT2_PARAM_NAME>   …   <TABLE1_PARAM_NAME>     <STRUCT1_PARAM_NAME>       <[FIELD1_NAME]>value1</[FIELD1_NAME]>       <[FIELD2_NAME]>value2</[FIELD2_NAME]>       …     </STRUCT1_PARAM_NAME>     …   </TABLE1_PARAM_NAME>   … </[RFC_NAME]Response>`      | <span data-ttu-id="13885-121">傳回的 RFC。</span><span class="sxs-lookup"><span data-stu-id="13885-121">RFC return.</span></span><br /><br /> <span data-ttu-id="13885-122">-Export，變更，並支援資料表參數。</span><span class="sxs-lookup"><span data-stu-id="13885-122">- Export, changing, and table parameters are supported.</span></span><br /><br /> <span data-ttu-id="13885-123">**注意：** 根據預設，資料表參數不會顯示在回應訊息中。</span><span class="sxs-lookup"><span data-stu-id="13885-123">**Note:** By default, table parameters are not surfaced in the response message.</span></span> <span data-ttu-id="13885-124">如果您需要在回應訊息中的資料表參數時，您必須傳遞空的資料表參數在要求訊息中。</span><span class="sxs-lookup"><span data-stu-id="13885-124">If you require table parameters in response message, you must pass empty table parameters in the request message.</span></span><br /><br /> <span data-ttu-id="13885-125">-匯入並變更參數可以是 SAP 結構類型，SAP 資料表類型或 SAP 簡單資料型別。</span><span class="sxs-lookup"><span data-stu-id="13885-125">- Import and changing parameters can be of SAP STRUCTURE TYPES, SAP TABLE TYPES or SAP simple data types.</span></span> |
|         <span data-ttu-id="13885-126">RfcGetAttributes</span><span class="sxs-lookup"><span data-stu-id="13885-126">RfcGetAttributes</span></span><br /><br /> <span data-ttu-id="13885-127">(RfcGetAttributes)</span><span class="sxs-lookup"><span data-stu-id="13885-127">(RfcGetAttributes)</span></span>          |                                                                                                                                                                                                                `<RfcGetAttributes> </RfcGetAttributes>`                                                                                                                                                                                                                |                                                  <span data-ttu-id="13885-128">RfcGetAttributes 是 RFC SDK API 作業呈現的[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="13885-128">RfcGetAttributes is an RFC SDK API operation that is surfaced by the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span> <span data-ttu-id="13885-129">RfcGetAttributes 作業可讓用戶端程式擷取語言、 系統識別碼，以及 RFC 連線相關聯的夥伴字碼頁。</span><span class="sxs-lookup"><span data-stu-id="13885-129">The RfcGetAttributes operation enables a client program to retrieve the language, the system ID, and the partner code page that are associated with the RFC connection.</span></span>                                                   |
| <span data-ttu-id="13885-130">RfcGetAttributes 回應</span><span class="sxs-lookup"><span data-stu-id="13885-130">RfcGetAttributes Response</span></span><br /><br /> <span data-ttu-id="13885-131">(RfcGetAttributesResponse)</span><span class="sxs-lookup"><span data-stu-id="13885-131">(RfcGetAttributesResponse)</span></span> |                                                                                                                                                          `<RfcGetAttributesResponse>   <Language>lang</Language>   <SysId>id</SysId>   <PartnerCodePage>pnrcp</PartnerCodePage> </RfcGetAttributesResponse>`                                                                                                                                                           |                                                                                                                              <span data-ttu-id="13885-132">語言、 系統識別碼，以及 RFC 連線相關聯的夥伴字碼頁，則會傳回 RfcGetAttributes 作業的回應。</span><span class="sxs-lookup"><span data-stu-id="13885-132">The response to the RfcGetAttributes operation returns the language, the system ID, and the partner code page that are associated with the RFC connection.</span></span>                                                                                                                              |

 <span data-ttu-id="13885-133">[VERSION] = 訊息版本字串;比方說， http://Microsoft.LobServices.SAP/2007/03。</span><span class="sxs-lookup"><span data-stu-id="13885-133">[VERSION] = The message version string; for example, http://Microsoft.LobServices.SAP/2007/03.</span></span>  

 <span data-ttu-id="13885-134">[RFC_NAME] = RFC; 的名稱比方說，RFC_CUSTOMER_GET。</span><span class="sxs-lookup"><span data-stu-id="13885-134">[RFC_NAME] = Name of the RFC; for example, RFC_CUSTOMER_GET.</span></span>  

 <span data-ttu-id="13885-135">[IN_PARAM_NAME] = RFC 匯入參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="13885-135">[IN_PARAM_NAME] = The name of an RFC Import parameter.</span></span>  

 <span data-ttu-id="13885-136">[OUT_PARAM_NAME] = RFC 匯出參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="13885-136">[OUT_PARAM_NAME] = The name of an RFC Export parameter.</span></span>  

 <span data-ttu-id="13885-137">[INOUT_PARAM_NAME] = RFC 變更參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="13885-137">[INOUT_PARAM_NAME] = The name of an RFC Changing parameter.</span></span>  

 <span data-ttu-id="13885-138">[TABLE_PARAM_NAME] = RFC 資料表參數名稱。</span><span class="sxs-lookup"><span data-stu-id="13885-138">[TABLE_PARAM_NAME] = The name of an RFC Table parameter.</span></span>  

 <span data-ttu-id="13885-139">[STRUCT_PARAM_NAME] = RFC 結構參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="13885-139">[STRUCT_PARAM_NAME] = The name of an RFC Structure parameter.</span></span>  

## <a name="message-actions-for-rfc-operations"></a><span data-ttu-id="13885-140">RFC 作業的訊息動作</span><span class="sxs-lookup"><span data-stu-id="13885-140">Message Actions for RFC Operations</span></span>  
 <span data-ttu-id="13885-141">下表顯示 RFC 作業的訊息動作。</span><span class="sxs-lookup"><span data-stu-id="13885-141">The following table shows the message actions for RFC operations.</span></span>  


|         <span data-ttu-id="13885-142">作業</span><span class="sxs-lookup"><span data-stu-id="13885-142">Operation</span></span>         |           <span data-ttu-id="13885-143">訊息的動作</span><span class="sxs-lookup"><span data-stu-id="13885-143">Message Action</span></span>           |                                <span data-ttu-id="13885-144">範例</span><span class="sxs-lookup"><span data-stu-id="13885-144">Example</span></span>                                 |
|---------------------------|------------------------------------|------------------------------------------------------------------------|
|        <span data-ttu-id="13885-145">[RFC_NAME]</span><span class="sxs-lookup"><span data-stu-id="13885-145">[RFC_NAME]</span></span>         |      <span data-ttu-id="13885-146">[VERSION]/Rfc/[RFC_NAME]</span><span class="sxs-lookup"><span data-stu-id="13885-146">[VERSION]/Rfc/[RFC_NAME]</span></span>      |     http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_CUSTOMER_GET      |
|    <span data-ttu-id="13885-147">[RFC_NAME]回應</span><span class="sxs-lookup"><span data-stu-id="13885-147">[RFC_NAME] Response</span></span>    | <span data-ttu-id="13885-148">[VERSION] /Rfc/ [RFC_NAME] / 回應</span><span class="sxs-lookup"><span data-stu-id="13885-148">[VERSION]/Rfc/[RFC_NAME]/response</span></span>  | http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_CUSTOMER_GET/response |
|     <span data-ttu-id="13885-149">RfcGetAttributes</span><span class="sxs-lookup"><span data-stu-id="13885-149">RfcGetAttributes</span></span>      |     <span data-ttu-id="13885-150">[VERSION] / RfcGetAttributes</span><span class="sxs-lookup"><span data-stu-id="13885-150">[VERSION]/RfcGetAttributes</span></span>     |       http://Microsoft.LobServices.Sap/2007/03/RfcGetAttributes        |
| <span data-ttu-id="13885-151">RfcGetAttributes 回應</span><span class="sxs-lookup"><span data-stu-id="13885-151">RfcGetAttributes Response</span></span> | <span data-ttu-id="13885-152">[版本/RfcGetAttributes/回應</span><span class="sxs-lookup"><span data-stu-id="13885-152">[VERSION/RfcGetAttributes/response</span></span> |   http://Microsoft.LobServices.Sap/2007/03/RfcGetAttributes/response   |

 <span data-ttu-id="13885-153">[VERSION] = 訊息版本字串;比方說， http://Microsoft.LobServices.Sap/2007/03。</span><span class="sxs-lookup"><span data-stu-id="13885-153">[VERSION] = The message version string; for example, http://Microsoft.LobServices.Sap/2007/03.</span></span>  

 <span data-ttu-id="13885-154">[RFC_NAME] = 要叫用; RFC 的名稱比方說，RFC_CUSTOMER_GET。</span><span class="sxs-lookup"><span data-stu-id="13885-154">[RFC_NAME] = The name of the RFC to be invoked; for example, RFC_CUSTOMER_GET.</span></span>  

## <a name="invoking-a-bapi-as-an-rfc-operation"></a><span data-ttu-id="13885-155">叫用 RFC 作業的 BAPI</span><span class="sxs-lookup"><span data-stu-id="13885-155">Invoking a BAPI as an RFC Operation</span></span>  
 <span data-ttu-id="13885-156">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]作為 RFC 作業和商務物件的方法，請瀏覽 Bapi。</span><span class="sxs-lookup"><span data-stu-id="13885-156">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] surfaces BAPIs both as RFC operations and as methods of business objects.</span></span> <span data-ttu-id="13885-157">RFC 作業為 Bapi 會依名稱顯示。</span><span class="sxs-lookup"><span data-stu-id="13885-157">As RFC operations, BAPIs are surfaced by name.</span></span> <span data-ttu-id="13885-158">如需有關如何使用商務物件介面叫用 Bapi 的詳細資訊，請參閱[對 SAP 中的 Bapi 的作業](../../adapters-and-accelerators/adapter-sap/operations-on-bapis-in-sap.md)。</span><span class="sxs-lookup"><span data-stu-id="13885-158">For more information about invoking BAPIs by using the business object interface, see [Operations on BAPIs in SAP](../../adapters-and-accelerators/adapter-sap/operations-on-bapis-in-sap.md).</span></span>  

 <span data-ttu-id="13885-159">下列 XML 顯示 BAPI (BAPI_CUSTOMER_GETDETAIL2) 以 RFC 叫用的訊息結構。</span><span class="sxs-lookup"><span data-stu-id="13885-159">The following XML shows the message structure for a BAPI (BAPI_CUSTOMER_GETDETAIL2) that is invoked as an RFC.</span></span> <span data-ttu-id="13885-160">這項作業的訊息動作是： http://Microsoft.LobServices.Sap/2007/03/Rfc/BAPI_CUSTOMER_GETDETAIL2。</span><span class="sxs-lookup"><span data-stu-id="13885-160">The message action for this operation is: http://Microsoft.LobServices.Sap/2007/03/Rfc/BAPI_CUSTOMER_GETDETAIL2.</span></span>  

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

## <a name="see-also"></a><span data-ttu-id="13885-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="13885-161">See Also</span></span>  
 [<span data-ttu-id="13885-162">訊息和訊息結構描述，BizTalk adapter for mySAP Business Suite</span><span class="sxs-lookup"><span data-stu-id="13885-162">Messages and Message Schemas for BizTalk Adapter for mySAP Business Suite</span></span>](../../adapters-and-accelerators/adapter-sap/messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md)