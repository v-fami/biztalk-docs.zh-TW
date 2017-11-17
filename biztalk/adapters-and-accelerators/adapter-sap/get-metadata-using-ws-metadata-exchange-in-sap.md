---
title: "取得中繼資料在 SAP 中使用 Ws-metadata Exchange |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WS-Metadata Exchange
- how to, retrieve metadata
- retrieving metadata
ms.assetid: 29f85963-ac7f-4e13-96b8-bc2c94a9fcae
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ae33fd76725abf15f12d95be39997fc29e67403e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="get-metadata-using-ws-metadata-exchange-in-sap"></a><span data-ttu-id="6b1e7-102">取得使用 Ws-metadata Exchange SAP 中的中繼資料</span><span class="sxs-lookup"><span data-stu-id="6b1e7-102">Get Metadata Using WS-Metadata Exchange in SAP</span></span>
<span data-ttu-id="6b1e7-103">做為[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]自訂繫結，[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]公開 WS 中繼資料交換 (MEX) 端點可讓您擷取從特定作業的中繼資料[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6b1e7-103">As a [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] custom binding, the [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] exposes a WS-Metadata Exchange (MEX) endpoint that you can use to retrieve metadata for specific operations from the [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)].</span></span>  
  
 <span data-ttu-id="6b1e7-104">WCF 提供豐富的基礎結構的匯出、 發行、 擷取及匯入服務的相關中繼資料。</span><span class="sxs-lookup"><span data-stu-id="6b1e7-104">WCF provides a rich infrastructure for exporting, publishing, retrieving and importing metadata about a service.</span></span> <span data-ttu-id="6b1e7-105">WCF 服務，類似配接器，會使用中繼資料描述如何與服務端點互動，以便等 svcutil.exe 工具，可以自動產生用戶端使用服務的程式碼。</span><span class="sxs-lookup"><span data-stu-id="6b1e7-105">WCF services, like the adapter, use metadata to describe how to interact with the service endpoints so that tools, like svcutil.exe, can automatically generate client code for consuming the service.</span></span> <span data-ttu-id="6b1e7-106">WCF 服務的中繼資料表示的執行個體**MetadataSet**型別，強式繫結至定義在 WS 中繼資料交換 (MEX) 中繼資料序列化格式。</span><span class="sxs-lookup"><span data-stu-id="6b1e7-106">WCF represents the metadata for a service as an instance of the **MetadataSet** type, which is strongly tied to the metadata serialization format defined in WS-Metadata Exchange (MEX).</span></span> <span data-ttu-id="6b1e7-107">您可以建立**MetadataSet**目標上的作業使用配接器**MetadataExchangeClient**。</span><span class="sxs-lookup"><span data-stu-id="6b1e7-107">You can create a **MetadataSet** for targeted operations on the adapter by using a **MetadataExchangeClient**.</span></span>  
  
 <span data-ttu-id="6b1e7-108">WCF 支援的中繼資料交換是以免受到擴充主題和超出範圍的這份文件。</span><span class="sxs-lookup"><span data-stu-id="6b1e7-108">WCF support for metadata exchange is an expansive topic and beyond the scope of this documentation.</span></span> <span data-ttu-id="6b1e7-109">多個支援的 WCF 中的中繼資料的詳細資訊，請參閱 「 中繼資料 」，在 WCF 文件中[http://go.microsoft.com/fwlink/?LinkId=105634](http://go.microsoft.com/fwlink/?LinkId=105634)。</span><span class="sxs-lookup"><span data-stu-id="6b1e7-109">For more information about support for metadata in WCF, see "Metadata" in the WCF documentation at [http://go.microsoft.com/fwlink/?LinkId=105634](http://go.microsoft.com/fwlink/?LinkId=105634).</span></span> <span data-ttu-id="6b1e7-110">特別適合說明的架構，類別和命名空間，WCF 會公開中繼資料，請參閱 「 中繼資料架構概觀 」 在[http://go.microsoft.com/fwlink/?LinkId=105635](http://go.microsoft.com/fwlink/?LinkId=105635)。</span><span class="sxs-lookup"><span data-stu-id="6b1e7-110">For a particularly good description of the architecture, classes, and namespaces that WCF exposes for metadata, see "Metadata Architecture Overview" at [http://go.microsoft.com/fwlink/?LinkId=105635](http://go.microsoft.com/fwlink/?LinkId=105635).</span></span> <span data-ttu-id="6b1e7-111">您應該熟悉後再繼續這些 WCF 主題中的 WCF 服務中擷取中繼資料與相關的內容。</span><span class="sxs-lookup"><span data-stu-id="6b1e7-111">You should familiarize yourself with the content related to retrieving metadata from a WCF service in these WCF topics before proceeding.</span></span>  
  
 <span data-ttu-id="6b1e7-112">下列主題包含有關如何使用資訊**MetadataExchangeClient**來擷取中繼資料從[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6b1e7-112">The following topics contain information about how to use a **MetadataExchangeClient** to retrieve metadata from the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
## <a name="using-a-metadataexchangeclient-to-retrieve-metadata"></a><span data-ttu-id="6b1e7-113">使用 MetadataExchangeClient 來擷取中繼資料</span><span class="sxs-lookup"><span data-stu-id="6b1e7-113">Using a MetadataExchangeClient to Retrieve Metadata</span></span>  
 <span data-ttu-id="6b1e7-114">若要使用**MetadataExchangeClient**您必須指定連線 URI 和繫結 (**SAPBinding**)。</span><span class="sxs-lookup"><span data-stu-id="6b1e7-114">To use a **MetadataExchangeClient** you must specify a connection URI and a binding (**SAPBinding**).</span></span> <span data-ttu-id="6b1e7-115">連線 URI 識別您要擷取中繼資料的作業。</span><span class="sxs-lookup"><span data-stu-id="6b1e7-115">The connection URI identifies the operations for which you want to retrieve metadata.</span></span>  
  
 <span data-ttu-id="6b1e7-116">下列各節包含有關如何指定連線 URI、 重要的繫結屬性，以及如何使用資訊**MetadataExchangeClient**從配接器擷取中繼資料。</span><span class="sxs-lookup"><span data-stu-id="6b1e7-116">The following sections contain information about how to specify the connection URI, important binding properties, and how to use a **MetadataExchangeClient** to retrieve metadata from the adapter.</span></span>  
  
### <a name="the-connection-uri"></a><span data-ttu-id="6b1e7-117">連線 URI</span><span class="sxs-lookup"><span data-stu-id="6b1e7-117">The Connection URI</span></span>  
 <span data-ttu-id="6b1e7-118">若要使用**MetadataExchangeClient**您必須提供 SAP 連線指定 MEX 端點和作業，或者您要擷取中繼資料作業的 URI。</span><span class="sxs-lookup"><span data-stu-id="6b1e7-118">To use the **MetadataExchangeClient** you must supply a SAP connection URI that specifies a MEX endpoint and the operation or operations for which you want to retrieve metadata.</span></span> <span data-ttu-id="6b1e7-119">您可以在 連線 URI 中，指定 MEX 端點和目標作業來以下列方式：</span><span class="sxs-lookup"><span data-stu-id="6b1e7-119">You specify a MEX endpoint and target operations in the connection URI in the following manner:</span></span>  
  
-   <span data-ttu-id="6b1e7-120">您必須在查詢字串中包含"wsdl 」 參數。</span><span class="sxs-lookup"><span data-stu-id="6b1e7-120">You must include the "wsdl" parameter in the query string.</span></span> <span data-ttu-id="6b1e7-121">如果查詢字串中的第一個參數，它會指定後方問號 （？）。</span><span class="sxs-lookup"><span data-stu-id="6b1e7-121">If it is the first parameter in the query string, it is specified just after the question mark (?).</span></span> <span data-ttu-id="6b1e7-122">如果不是第一個參數，它應該在前面加上連字號 (&)。</span><span class="sxs-lookup"><span data-stu-id="6b1e7-122">If it is not the first parameter, it should be preceded with an ampersand (&).</span></span>  
  
-   <span data-ttu-id="6b1e7-123">您必須遵循一或多個"op"參數"wsdl 」 的參數。</span><span class="sxs-lookup"><span data-stu-id="6b1e7-123">You must follow the "wsdl" parameter by one or more "op" parameters.</span></span> <span data-ttu-id="6b1e7-124">每個"op"參數加上連字號 (&)，並指定目標作業的訊息動作 (節點 ID)。</span><span class="sxs-lookup"><span data-stu-id="6b1e7-124">Each "op" parameter is preceded by an ampersand (&) and specifies the message action (node ID) of a target operation.</span></span>  
  
 <span data-ttu-id="6b1e7-125">例如，下列連線 URI 為目標 SALESORDER_CREATEFROMDAT201 IDOC 和 SALESORDER_CREATEFROMDAT202 IDOC 的傳送作業。</span><span class="sxs-lookup"><span data-stu-id="6b1e7-125">For example, the following connection URI targets the Send operation for the SALESORDER_CREATEFROMDAT201 IDOC and the SALESORDER_CREATEFROMDAT202 IDOC.</span></span> <span data-ttu-id="6b1e7-126">「 Wsdl"和"op"參數會反白顯示。</span><span class="sxs-lookup"><span data-stu-id="6b1e7-126">The "wsdl" and "op" parameters are highlighted.</span></span>  
  
```  
"sap://User=YourUserName;Passwd=YourPassword;Client=800;Lang=EN;@a/YourSAPHost/00?wsdl&op=http://Microsoft.LobServices.Sap/2007/03/Idoc/3/SALESORDER_CREATEFROMDAT201//620/Send&op=http://Microsoft.LobServices.Sap/2007/03/Idoc/3/SALESORDER_CREATEFROMDAT202//620/Send"  
```  
  
> [!NOTE]
>  <span data-ttu-id="6b1e7-127">您不需要在 連線 URI 的輸入作業中包含接聽程式參數。</span><span class="sxs-lookup"><span data-stu-id="6b1e7-127">It is not necessary to include listener parameters in the connection URI for inbound operations.</span></span> <span data-ttu-id="6b1e7-128">配接器會為 SAP 系統從擷取中繼資料的用戶端連線。</span><span class="sxs-lookup"><span data-stu-id="6b1e7-128">The adapter connects as a client to retrieve metadata from the SAP system.</span></span>  
  
 <span data-ttu-id="6b1e7-129">您也可以使用在定義的常數`Microsoft.Adapters.SAP.SAPAdapterConstants.ActionConstants`可協助您指定的作業，當您建立連線的 URI。</span><span class="sxs-lookup"><span data-stu-id="6b1e7-129">You can also use the constants defined at `Microsoft.Adapters.SAP.SAPAdapterConstants.ActionConstants` to help you specify operations when you create a connection URI.</span></span> <span data-ttu-id="6b1e7-130">本主題結尾的程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="6b1e7-130">This is demonstrated in the code example at the end of this topic.</span></span>  
  
 <span data-ttu-id="6b1e7-131">您將此連線 URI 的傳遞至**MetadataExchangeClient**取決於哪一種多載的方法您用於建立用戶端，並從配接器擷取中繼資料。</span><span class="sxs-lookup"><span data-stu-id="6b1e7-131">How you pass this connection URI to the **MetadataExchangeClient** depends on which of the overloaded methods you use to create the client and retrieve metadata from the adapter.</span></span>  
  
 <span data-ttu-id="6b1e7-132">如需有關 SAP 連線 URI 的詳細資訊，請參閱[建立 SAP 系統連接 URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md)。</span><span class="sxs-lookup"><span data-stu-id="6b1e7-132">For more information about the SAP connection URI, see [Create the SAP System Connection URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md).</span></span>  
  
### <a name="binding-properties"></a><span data-ttu-id="6b1e7-133">繫結屬性</span><span class="sxs-lookup"><span data-stu-id="6b1e7-133">Binding Properties</span></span>  
 <span data-ttu-id="6b1e7-134">當您建立**MetadataExchangeClient**，您必須指定**SAPBinding**。</span><span class="sxs-lookup"><span data-stu-id="6b1e7-134">When you create the **MetadataExchangeClient**, you must specify an **SAPBinding**.</span></span>  
  
 <span data-ttu-id="6b1e7-135">有幾個會影響配接器如何產生中繼資料的繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="6b1e7-135">There are several binding properties that affect how the adapter generates metadata.</span></span> <span data-ttu-id="6b1e7-136">這些屬性如下：</span><span class="sxs-lookup"><span data-stu-id="6b1e7-136">These properties are:</span></span>  
  
-   <span data-ttu-id="6b1e7-137">**GenerateFlatfileCompatibleIdocSchema**</span><span class="sxs-lookup"><span data-stu-id="6b1e7-137">**GenerateFlatfileCompatibleIdocSchema**</span></span>  
  
-   <span data-ttu-id="6b1e7-138">**ReceiveIDocFormat**</span><span class="sxs-lookup"><span data-stu-id="6b1e7-138">**ReceiveIDocFormat**</span></span>  
  
-   <span data-ttu-id="6b1e7-139">**EnableSafeTyping**</span><span class="sxs-lookup"><span data-stu-id="6b1e7-139">**EnableSafeTyping**</span></span>  
  
-   <span data-ttu-id="6b1e7-140">**FlatFileSegmentIndicator**</span><span class="sxs-lookup"><span data-stu-id="6b1e7-140">**FlatFileSegmentIndicator**</span></span>  
  
 <span data-ttu-id="6b1e7-141">您應該確定這些繫結屬性設定為您叫用之前，您的應用程式所需的值**GetMetadata**方法**MetadataExchangeClient**。</span><span class="sxs-lookup"><span data-stu-id="6b1e7-141">You should ensure that these binding properties are set to the values required for your application before you invoke the **GetMetadata** method on the **MetadataExchangeClient**.</span></span> <span data-ttu-id="6b1e7-142">如需有關 SAP 配接器繫結屬性的詳細資訊，請參閱[了解 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="6b1e7-142">For more information about the SAP adapter binding properties, see [Read about BizTalk Adapter for mySAP Business Suite Binding Properties](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).</span></span>  
  
### <a name="example"></a><span data-ttu-id="6b1e7-143">範例</span><span class="sxs-lookup"><span data-stu-id="6b1e7-143">Example</span></span>  
 <span data-ttu-id="6b1e7-144">下列範例會使用**MetadataExchangeClient** BAPI_TRANSACTION_COMMIT 和 BAPI_TRANSACTION_ROLLBACK 作業建立的服務描述 （WSDL 文件）。</span><span class="sxs-lookup"><span data-stu-id="6b1e7-144">The following example uses a **MetadataExchangeClient** to create a service description (WSDL document) for the BAPI_TRANSACTION_COMMIT and BAPI_TRANSACTION_ROLLBACK operations.</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
using System.Collections.ObjectModel;  
  
// Needed for WCF and SAP adapter  
using System.ServiceModel;  
using Microsoft.ServiceModel.Channels;  
using Microsoft.Adapters.SAP;  
  
// Needed for MetadataExchangeClient class  
using System.ServiceModel.Description;  
// Needed for ServiceDescription class  
using System.Web.Services;  
  
namespace SapMetadataExchangeClient  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            //Create a binding  
            SAPBinding binding = new SAPBinding();  
  
            //Create a metadata exchange client that will retrieve metadata according to the WS-MEX standard.  
            MetadataExchangeClient client = new MetadataExchangeClient(binding);  
            client.SoapCredentials.UserName.UserName = "YourUserName";  
            client.SoapCredentials.UserName.Password = "YourPassword";  
  
            //Set up an endpoint address and specify the operation for which we want metadata.  
            string connectionUri = "sap://Client=800;lang=EN@A/YourSAPHost/00?wsdl&op="  
                + Microsoft.Adapters.SAP.SAPAdapterConstants.ActionConstants.RfcActionPrefix  
                + "BAPI_TRANSACTION_COMMIT"  
                + "&op="  
                + Microsoft.Adapters.SAP.SAPAdapterConstants.ActionConstants.RfcActionPrefix  
                + "BAPI_TRANSACTION_ROLLBACK";  
  
            EndpointAddress address = new EndpointAddress(connectionUri);  
  
            //Get the metadata.  
            MetadataSet ms = client.GetMetadata(address);  
  
            // Check for the metadata set size.   
            Collection<MetadataSection> documentCollection = ms.MetadataSections;  
            if (documentCollection != null && documentCollection.Count > 0)  
            {  
                //Get the WSDL from the metadata set  
                System.Web.Services.Description.ServiceDescription wsdl = (System.Web.Services.Description.ServiceDescription)documentCollection[0].Metadata;  
  
                //Save the WSDL to a file.  
                wsdl.Write("BapiTx.wsdl");    
  
            }  
  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="6b1e7-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6b1e7-145">See Also</span></span>  
 <span data-ttu-id="6b1e7-146">[以程式設計方式從 SAP 擷取中繼資料](../../adapters-and-accelerators/adapter-sap/get-metadata-programmatically-from-sap.md) </span><span class="sxs-lookup"><span data-stu-id="6b1e7-146">[Retrieving Metadata Programmatically from SAP](../../adapters-and-accelerators/adapter-sap/get-metadata-programmatically-from-sap.md) </span></span>  
 [<span data-ttu-id="6b1e7-147">使用 IMetadataRetrievalContract SAP 中擷取中繼資料</span><span class="sxs-lookup"><span data-stu-id="6b1e7-147">Retrieving Metadata in SAP using IMetadataRetrievalContract</span></span>](../../adapters-and-accelerators/adapter-sap/get-metadata-in-sap-using-imetadataretrievalcontract.md)