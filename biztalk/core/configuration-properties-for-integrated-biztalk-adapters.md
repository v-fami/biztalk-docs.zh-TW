---
title: 整合式的 BizTalk 配接器的組態屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- adapters, security
- adapters, passwords
- IReceiveLocation.CustomData property
- security, passwords
- ISendPort.CustomData property
- binding files, passwords
- adapters, properties
- binding files, security
ms.assetid: 4780a558-4322-428a-aa4a-0c32913faded
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 45779131906460040db969bd4ef412b8f9220ab6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37005983"
---
# <a name="configuration-properties-for-integrated-biztalk-adapters"></a><span data-ttu-id="6273d-102">整合式 BizTalk 配接器的組態屬性</span><span class="sxs-lookup"><span data-stu-id="6273d-102">Configuration Properties for Integrated BizTalk Adapters</span></span>
<span data-ttu-id="6273d-103">「 BizTalk 總管物件模型會公開**IReceiveLocation.CustomData**並**ISendPort.CustomData**包含配接器組態屬性包中的名稱/值形式的屬性組 XML 字串。</span><span class="sxs-lookup"><span data-stu-id="6273d-103">The BizTalk Explorer object model exposes the **IReceiveLocation.CustomData** and **ISendPort.CustomData** properties that contain the adapter configuration property bag in the form of a name/value pair XML string.</span></span> <span data-ttu-id="6273d-104">此名稱/值組 XML 字串會儲存在\<CustomProps\>內的項目\<TransportTypeData\>繫結檔案中的項目。</span><span class="sxs-lookup"><span data-stu-id="6273d-104">This name/value pair XML string is stored in a \<CustomProps\> element within a \<TransportTypeData\> element in a binding file.</span></span> <span data-ttu-id="6273d-105">中的資訊，大部分\<CustomProps\>元素都會對應到配接器可以設定 BizTalk Server 使用者介面 （例如 BizTalk 管理主控台或 BizTalk 總管 中） 中的資訊。</span><span class="sxs-lookup"><span data-stu-id="6273d-105">Most of the information in the \<CustomProps\> element corresponds to information that can be set for an adapter in the BizTalk Server user interface (such as the BizTalk Administration Console or BizTalk Explorer).</span></span> <span data-ttu-id="6273d-106">如果這些值存在於繫結檔案中，當匯入繫結檔案時，它們便會套用至指定之接收位置和傳送埠的配接器組態。</span><span class="sxs-lookup"><span data-stu-id="6273d-106">If these values are present in a binding file then they are applied to the adapter configuration for the specified receive locations and send ports when the binding file is imported.</span></span> <span data-ttu-id="6273d-107">所有配接器的組態資訊都會儲存在「單一登入」資料庫中。</span><span class="sxs-lookup"><span data-stu-id="6273d-107">Configuration information for all adapters is stored in the Single Sign-On database.</span></span>  
  
 <span data-ttu-id="6273d-108">本節描述可為每個整合式 BizTalk 配接器設定的組態屬性。</span><span class="sxs-lookup"><span data-stu-id="6273d-108">This section describes the configuration properties that can be set for each integrated BizTalk adapter.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6273d-109">密碼資訊儲存在\<TransportTypeData\>項目繫結檔案遮罩，如此敏感性資料不會儲存在純文字。</span><span class="sxs-lookup"><span data-stu-id="6273d-109">Password information that is stored in the \<TransportTypeData\> element of a binding file is masked so that sensitive data is not saved in clear text.</span></span> <span data-ttu-id="6273d-110">取決於傳輸方式，密碼資訊若非以 NULL 取代，就會以星號取代。</span><span class="sxs-lookup"><span data-stu-id="6273d-110">Depending on the transport, password information is either replaced with NULL or is replaced with asterisks.</span></span> <span data-ttu-id="6273d-111">將繫結檔案匯入到目標 BizTalk Server 組態之前，您必須以手動方式將此資訊輸入繫結檔案以更新配接器組態。</span><span class="sxs-lookup"><span data-stu-id="6273d-111">You must manually enter this information in the binding file to update the adapter configuration before importing the binding file into the target BizTalk Server configuration.</span></span>  
  
 <span data-ttu-id="6273d-112">使用配接器架構建置的配接器的組態資料儲存在\<AdapterConfig\>項目。</span><span class="sxs-lookup"><span data-stu-id="6273d-112">The configuration data for adapters built using the Adapter Framework is stored in an \<AdapterConfig\> element.</span></span> <span data-ttu-id="6273d-113">由於\<AdapterConfig\>項目會指定 VT_BSTR (vt ="8") 資料類型**\< \>** 必須逸出此項目中包含的字元，或會發生錯誤時您嘗試匯入繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="6273d-113">Since the \<AdapterConfig\> element specifies the VT_BSTR (vt="8") data type, the **\< \>** characters contained in this element must be escaped or an error will occur when you attempt to import the binding file.</span></span> <span data-ttu-id="6273d-114">這樣會使組態資料的文字，比沒有逸出字元時更加難以閱讀。</span><span class="sxs-lookup"><span data-stu-id="6273d-114">This causes the text for the configuration data to be less human readable than if these characters were not escaped.</span></span> <span data-ttu-id="6273d-115">下列範例說明從繫結至 POP3 配接器之傳送埠的範例組態資料，逸出這些字元的效果。</span><span class="sxs-lookup"><span data-stu-id="6273d-115">The following example illustrates the effect of escaping these characters from sample configuration data for a send port bound to the POP3 adapter.</span></span>  
  
 <span data-ttu-id="6273d-116">**不逸出所使用的 <> 字元的 TransportTypeData 組態資料\<AdapterConfig\>項目**</span><span class="sxs-lookup"><span data-stu-id="6273d-116">**TransportTypeData configuration data that does not escape the <> characters used in the \<AdapterConfig\> element**</span></span>  
  
 <span data-ttu-id="6273d-117">這項組態資料無效因為\<AdapterConfig\>項目會指定 VT_BSTR (vt ="8") 資料型別並\<\>中所包含的字元\<AdapterConfig\>項目不會逸出：</span><span class="sxs-lookup"><span data-stu-id="6273d-117">This configuration data is invalid because the \<AdapterConfig\> element specifies the VT_BSTR (vt="8") data type and the \< \> characters contained in the \<AdapterConfig\> element are not escaped:</span></span>  
  
```  
<TransportTypeData>  
<CustomProps>  
<AdapterConfig vt="8">  
<Config xmlns:xsi=http://www.w3.org/2001/XMLSchema-instance xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
<mailServer>test.microsoft.com</mailServer>  
<serverPort>0</serverPort>  
<userName>testuser</userName>  
<password>******</password>  
<authenticationScheme>Basic</authenticationScheme>  
<sslRequired>false</sslRequired>  
<applyMIME>true</applyMIME>  
<bodyPartContentType>text/xml</bodyPartContentType>  
<bodyPartIndex>1</bodyPartIndex>  
<errorThreshold>10</errorThreshold>  
<pollingInterval>5</pollingInterval>  
<pollingUnitOfMeasure>Minutes</pollingUnitOfMeasure>   
<uri>POP3://test.microsoft.com#testuser</uri>  
</Config>  
</AdapterConfig>  
</CustomProps>  
</TransportTypeData>  
```  
  
 <span data-ttu-id="6273d-118">**未逸出 <> 字元中使用的 TransportTypeData 組態資料\<AdapterConfig\>項目**</span><span class="sxs-lookup"><span data-stu-id="6273d-118">**TransportTypeData configuration data that does escape the <> characters used in the \<AdapterConfig\> element**</span></span>  
  
 <span data-ttu-id="6273d-119">由於\<AdapterConfig\>項目會指定 VT_BSTR (vt ="8") 資料類型\<\>必須逸出字元，從\<AdapterConfig\>項目，如下所示：</span><span class="sxs-lookup"><span data-stu-id="6273d-119">Since the \<AdapterConfig\> element specifies the VT_BSTR (vt="8") data type, the \< \> characters must be escaped from the \<AdapterConfig\> element as seen below:</span></span>  
  
```  
<TransportTypeData>  
<CustomProps>  
<AdapterConfig vt="8">  
<Config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"  
xmlns:xsd="http://www.w3.org/2001/XMLSchema"><mailServer>test  
microsoft.com</mailServer><serverPort>0</serverPort>&  
lt;userName>testuser</userName><password>******</pass  
word><authenticationScheme>Basic</authenticationScheme>&  
lt;sslRequired>false</sslRequired><applyMIME>true</ap  
plyMIME><bodyPartContentType>text/xml</bodyPartContentType&  
gt;<bodyPartIndex>1</bodyPartIndex><errorThreshold>10  
</errorThreshold><pollingInterval>5</pollingInterval>  
<pollingUnitOfMeasure>Minutes</pollingUnitOfMeasure><uri  
>POP3://test.microsoft.com#testuser</uri></Config>  
</AdapterConfig>  
</CustomProps>  
</TransportTypeData>  
```  
  
 <span data-ttu-id="6273d-120">以「配接器架構」建立的整合式配接器包括下列各項：</span><span class="sxs-lookup"><span data-stu-id="6273d-120">The integrated adapters that were created with the Adapter Framework include the following:</span></span>  
  
- <span data-ttu-id="6273d-121">FTP 配接器</span><span class="sxs-lookup"><span data-stu-id="6273d-121">FTP Adapter</span></span>  
  
- <span data-ttu-id="6273d-122">MQSeries 配接器</span><span class="sxs-lookup"><span data-stu-id="6273d-122">MQSeries Adapter</span></span>  
  
- <span data-ttu-id="6273d-123">MSMQ 配接器</span><span class="sxs-lookup"><span data-stu-id="6273d-123">MSMQ Adapter</span></span>  
  
- <span data-ttu-id="6273d-124">POP3 配接器</span><span class="sxs-lookup"><span data-stu-id="6273d-124">POP3 Adapter</span></span>  
  
- <span data-ttu-id="6273d-125">Windows Sharepoint Services 配接器</span><span class="sxs-lookup"><span data-stu-id="6273d-125">Windows Sharepoint Services Adapter</span></span>  
  
  <span data-ttu-id="6273d-126">若要檢視對每個整合式配接器用來做為 TransportTypeData 組態資料的範例字串，請參閱與此節中的配接器關聯的組態屬性主題。</span><span class="sxs-lookup"><span data-stu-id="6273d-126">To view a sample string used as the TransportTypeData configuration data for each integrated adapter, please see the configuration properties topic that is associated with the adapter in this section.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6273d-127">本節內容</span><span class="sxs-lookup"><span data-stu-id="6273d-127">In This Section</span></span>  
 [<span data-ttu-id="6273d-128">設定屬性變數類型</span><span class="sxs-lookup"><span data-stu-id="6273d-128">Configuration Property Variable Types</span></span>](../core/configuration-property-variable-types.md)  
  
 [<span data-ttu-id="6273d-129">File 配接器設定屬性</span><span class="sxs-lookup"><span data-stu-id="6273d-129">File Adapter Configuration Properties</span></span>](../core/file-adapter-configuration-properties.md)  
  
 [<span data-ttu-id="6273d-130">FTP 配接器設定屬性</span><span class="sxs-lookup"><span data-stu-id="6273d-130">FTP Adapter Configuration Properties</span></span>](../core/ftp-adapter-configuration-properties.md)  
  
 [<span data-ttu-id="6273d-131">HTTP 配接器設定屬性</span><span class="sxs-lookup"><span data-stu-id="6273d-131">HTTP Adapter Configuration Properties</span></span>](../core/http-adapter-configuration-properties.md)  
  
 [<span data-ttu-id="6273d-132">MQSeries 配接器設定屬性</span><span class="sxs-lookup"><span data-stu-id="6273d-132">MQSeries Adapter Configuration Properties</span></span>](../core/mqseries-adapter-configuration-properties.md)  
  
 [<span data-ttu-id="6273d-133">MSMQ 配接器設定屬性</span><span class="sxs-lookup"><span data-stu-id="6273d-133">MSMQ Adapter Configuration Properties</span></span>](../core/msmq-adapter-configuration-properties.md)  
  
 [<span data-ttu-id="6273d-134">POP3 配接器設定屬性</span><span class="sxs-lookup"><span data-stu-id="6273d-134">POP3 Adapter Configuration Properties</span></span>](../core/pop3-adapter-configuration-properties.md)  
  
 [<span data-ttu-id="6273d-135">SMTP 配接器設定屬性</span><span class="sxs-lookup"><span data-stu-id="6273d-135">SMTP Adapter Configuration Properties</span></span>](../core/smtp-adapter-configuration-properties.md)  
  
 [<span data-ttu-id="6273d-136">SOAP 配接器設定屬性</span><span class="sxs-lookup"><span data-stu-id="6273d-136">SOAP Adapter Configuration Properties</span></span>](../core/soap-adapter-configuration-properties.md)  
  
 [<span data-ttu-id="6273d-137">Windows Sharepoint Services 配接器設定屬性</span><span class="sxs-lookup"><span data-stu-id="6273d-137">Windows Sharepoint Services Adapter Configuration Properties</span></span>](../core/windows-sharepoint-services-adapter-configuration-properties.md)