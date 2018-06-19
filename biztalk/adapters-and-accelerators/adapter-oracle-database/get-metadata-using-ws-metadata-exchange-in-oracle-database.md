---
title: 取得中繼資料的 Oracle 資料庫中使用 Ws-metadata Exchange |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WS-Metadata Exchange, retrieving metadata
- metadata, retrieving using WS-Metadata Exchange
ms.assetid: 6ff34438-7260-489d-a5f0-6e53f8fe43be
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2be3f829d41b77dc7897d7b3f4300d82e7a3c100
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22214854"
---
# <a name="get-metadata-using-ws-metadata-exchange-in-oracle-database"></a><span data-ttu-id="06709-102">取得使用 Ws-metadata Exchange Oracle 資料庫中的中繼資料</span><span class="sxs-lookup"><span data-stu-id="06709-102">Get Metadata Using WS-Metadata Exchange in Oracle Database</span></span>
<span data-ttu-id="06709-103">做為[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]自訂繫結，[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]公開 WS 中繼資料交換 (MEX) 端點可讓您擷取從特定作業的中繼資料[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="06709-103">As a [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] custom binding, the [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] exposes a WS-Metadata Exchange (MEX) endpoint that you can use to retrieve metadata for specific operations from the [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)].</span></span>  
  
 <span data-ttu-id="06709-104">WCF 提供豐富的基礎結構的匯出、 發行、 擷取及匯入服務的相關中繼資料。</span><span class="sxs-lookup"><span data-stu-id="06709-104">WCF provides a rich infrastructure for exporting, publishing, retrieving and importing metadata about a service.</span></span> <span data-ttu-id="06709-105">WCF 服務，類似配接器，會使用中繼資料描述如何與服務端點互動，以便等 svcutil.exe 工具，可以自動產生用戶端使用服務的程式碼。</span><span class="sxs-lookup"><span data-stu-id="06709-105">WCF services, like the adapter, use metadata to describe how to interact with the service endpoints so that tools, like svcutil.exe, can automatically generate client code for consuming the service.</span></span> <span data-ttu-id="06709-106">WCF 服務的中繼資料表示的執行個體**MetadataSet**型別，強式繫結至定義在 WS 中繼資料交換 (MEX) 中繼資料序列化格式。</span><span class="sxs-lookup"><span data-stu-id="06709-106">WCF represents the metadata for a service as an instance of the **MetadataSet** type, which is strongly tied to the metadata serialization format defined in WS-Metadata Exchange (MEX).</span></span> <span data-ttu-id="06709-107">您可以建立**MetadataSet**目標上的作業使用配接器**MetadataExchangeClient**。</span><span class="sxs-lookup"><span data-stu-id="06709-107">You can create a **MetadataSet** for targeted operations on the adapter by using a **MetadataExchangeClient**.</span></span>  
  
 <span data-ttu-id="06709-108">WCF 支援的中繼資料交換是以免受到擴充主題和超出範圍的這份文件。</span><span class="sxs-lookup"><span data-stu-id="06709-108">WCF support for metadata exchange is an expansive topic and beyond the scope of this documentation.</span></span> <span data-ttu-id="06709-109">如需支援的 WCF 中的中繼資料的詳細資訊，請參閱[中繼資料](https://msdn.microsoft.com/library/ms731823.aspx)。</span><span class="sxs-lookup"><span data-stu-id="06709-109">For more information about support for metadata in WCF, see [Metadata](https://msdn.microsoft.com/library/ms731823.aspx).</span></span> <span data-ttu-id="06709-110">特別適合用架構、 類別和 WCF 公開中繼資料的命名空間的說明，請參閱[中繼資料架構概觀](https://msdn.microsoft.com/library/ms730243.aspx)。</span><span class="sxs-lookup"><span data-stu-id="06709-110">For a particularly good description of the architecture, classes, and namespaces that WCF exposes for metadata, see [Metadata Architecture Overview](https://msdn.microsoft.com/library/ms730243.aspx).</span></span> <span data-ttu-id="06709-111">您應該熟悉後再繼續這些 WCF 主題中的 WCF 服務中擷取中繼資料與相關的內容。</span><span class="sxs-lookup"><span data-stu-id="06709-111">You should familiarize yourself with the content related to retrieving metadata from a WCF service in these WCF topics before proceeding.</span></span>  
  
 <span data-ttu-id="06709-112">下列主題包含有關如何使用資訊**MetadataExchangeClient**來擷取中繼資料從[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="06709-112">The following topics contain information about how to use a **MetadataExchangeClient** to retrieve metadata from the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span>  
  
## <a name="using-a-metadataexchangeclient-to-retrieve-metadata"></a><span data-ttu-id="06709-113">使用 MetadataExchangeClient 來擷取中繼資料</span><span class="sxs-lookup"><span data-stu-id="06709-113">Using a MetadataExchangeClient to Retrieve Metadata</span></span>  
 <span data-ttu-id="06709-114">若要使用**MetadataExchangeClient**您必須指定連線 URI 和繫結 (**OracleDBBinding**)。</span><span class="sxs-lookup"><span data-stu-id="06709-114">To use a **MetadataExchangeClient** you must specify a connection URI and a binding (**OracleDBBinding**).</span></span> <span data-ttu-id="06709-115">連線 URI 識別您要擷取中繼資料的作業。</span><span class="sxs-lookup"><span data-stu-id="06709-115">The connection URI identifies the operations for which you want to retrieve metadata.</span></span>  
  
 <span data-ttu-id="06709-116">下列各節包含有關如何指定連線 URI、 重要的繫結屬性，以及如何使用資訊**MetadataExchangeClient**從配接器擷取中繼資料。</span><span class="sxs-lookup"><span data-stu-id="06709-116">The following sections contain information about how to specify the connection URI, important binding properties, and how to use a **MetadataExchangeClient** to retrieve metadata from the adapter.</span></span>  
  
### <a name="the-connection-uri"></a><span data-ttu-id="06709-117">連線 URI</span><span class="sxs-lookup"><span data-stu-id="06709-117">The Connection URI</span></span>  
 <span data-ttu-id="06709-118">若要使用**MetadataExchangeClient**您必須提供的 Oracle 連接指定 MEX 端點和作業，或者您要擷取中繼資料作業的 URI。</span><span class="sxs-lookup"><span data-stu-id="06709-118">To use the **MetadataExchangeClient** you must supply an Oracle connection URI that specifies a MEX endpoint and the operation or operations for which you want to retrieve metadata.</span></span> <span data-ttu-id="06709-119">您可以在 連線 URI 中，指定 MEX 端點和目標作業來以下列方式：</span><span class="sxs-lookup"><span data-stu-id="06709-119">You specify a MEX endpoint and target operations in the connection URI in the following manner:</span></span>  
  
-   <span data-ttu-id="06709-120">您必須在查詢字串中包含"wsdl 」 參數。</span><span class="sxs-lookup"><span data-stu-id="06709-120">You must include the "wsdl" parameter in the query string.</span></span> <span data-ttu-id="06709-121">如果查詢字串中的第一個參數，它會指定後方問號 （？）。</span><span class="sxs-lookup"><span data-stu-id="06709-121">If it is the first parameter in the query string, it is specified just after the question mark (?).</span></span> <span data-ttu-id="06709-122">如果不是第一個參數，它應該在前面加上連字號 (&)。</span><span class="sxs-lookup"><span data-stu-id="06709-122">If it is not the first parameter, it should be preceded with an ampersand (&).</span></span>  
  
-   <span data-ttu-id="06709-123">您必須遵循一或多個"op"參數"wsdl 」 的參數。</span><span class="sxs-lookup"><span data-stu-id="06709-123">You must follow the "wsdl" parameter by one or more "op" parameters.</span></span> <span data-ttu-id="06709-124">每個"op"參數加上連字號 (&)，並指定目標作業的訊息動作 (節點 ID)。</span><span class="sxs-lookup"><span data-stu-id="06709-124">Each "op" parameter is preceded by an ampersand (&) and specifies the message action (node ID) of a target operation.</span></span>  
  
 <span data-ttu-id="06709-125">例如，下列連線 URI 為目標 SCOTT 的 Insert 和 Delete 作業。EMP 資料表。</span><span class="sxs-lookup"><span data-stu-id="06709-125">For example, the following connection URI targets the Insert and Delete operations for the SCOTT.EMP table.</span></span> <span data-ttu-id="06709-126">「 Wsdl"和"op"參數會反白顯示。</span><span class="sxs-lookup"><span data-stu-id="06709-126">The "wsdl" and "op" parameters are highlighted.</span></span>  
  
```  
"oracledb://ADAPTER?wsdl&op=http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Insert&op=http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Delete"  
```  
  
> [!NOTE]
>  <span data-ttu-id="06709-127">如果您想要修改產生 POLLINGSTMT 作業的命名空間，您應該指定 PollingId 參數查詢字串中。</span><span class="sxs-lookup"><span data-stu-id="06709-127">If you want to modify the namespace generated for the POLLINGSTMT operation you should specify a PollingId parameter in the query string.</span></span>  
  
 <span data-ttu-id="06709-128">您將此連線 URI 的傳遞至**MetadataExchangeClient**取決於哪一種多載的方法您用於建立用戶端，並從配接器擷取中繼資料。</span><span class="sxs-lookup"><span data-stu-id="06709-128">How you pass this connection URI to the **MetadataExchangeClient** depends on which of the overloaded methods you use to create the client and retrieve metadata from the adapter.</span></span>  
  
 <span data-ttu-id="06709-129">如需 Oracle 連線 URI 的詳細資訊，請參閱[建立 Oracle 資料庫連線 URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md)。</span><span class="sxs-lookup"><span data-stu-id="06709-129">For more information about the Oracle connection URI, see [Create the Oracle Database connection URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md).</span></span>  
  
### <a name="binding-properties"></a><span data-ttu-id="06709-130">繫結屬性</span><span class="sxs-lookup"><span data-stu-id="06709-130">Binding Properties</span></span>  
 <span data-ttu-id="06709-131">當您建立**MetadataExchangeClient**，您必須指定**OracleDBBinding**。</span><span class="sxs-lookup"><span data-stu-id="06709-131">When you create the **MetadataExchangeClient**, you must specify an **OracleDBBinding**.</span></span>  
  
 <span data-ttu-id="06709-132">有幾個會影響配接器如何產生中繼資料的繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="06709-132">There are several binding properties that affect how the adapter generates metadata.</span></span> <span data-ttu-id="06709-133">這些屬性如下：</span><span class="sxs-lookup"><span data-stu-id="06709-133">These properties are:</span></span>  
  
-   <span data-ttu-id="06709-134">**EnableSafeTyping**</span><span class="sxs-lookup"><span data-stu-id="06709-134">**EnableSafeTyping**</span></span>  
  
-   <span data-ttu-id="06709-135">**UseSchemaInNamespace**</span><span class="sxs-lookup"><span data-stu-id="06709-135">**UseSchemaInNamespace**</span></span>  
  
-   <span data-ttu-id="06709-136">**PollingStatement**</span><span class="sxs-lookup"><span data-stu-id="06709-136">**PollingStatement**</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="06709-137">如果您想要擷取 POLLINGSTMT 作業的中繼資料必須先設定**PollingStatement**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="06709-137">If you want to retrieve metadata for the POLLINGSTMT operation you must set the **PollingStatement** binding property.</span></span>  
  
 <span data-ttu-id="06709-138">您應該確定這些繫結屬性設定為您叫用之前，您的應用程式所需的值**GetMetadata**方法**MetadataExchangeClient**。</span><span class="sxs-lookup"><span data-stu-id="06709-138">You should ensure that these binding properties are set to the values required for your application before you invoke the **GetMetadata** method on the **MetadataExchangeClient**.</span></span> <span data-ttu-id="06709-139">如需有關[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]繫結屬性，請參閱[閱讀有關 Oracle 資料庫配接器繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="06709-139">For more information about the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] binding properties, see [Read about the Oracle Database adapter binding properties](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md).</span></span>  
  
### <a name="example"></a><span data-ttu-id="06709-140">範例</span><span class="sxs-lookup"><span data-stu-id="06709-140">Example</span></span>  
 <span data-ttu-id="06709-141">下列範例會使用**MetadataExchangeClient**為 Insert、 Update、 Delete 與 SCOTT 上的 Select 作業建立的服務描述 （WSDL 文件）。EMP 資料表。</span><span class="sxs-lookup"><span data-stu-id="06709-141">The following example uses a **MetadataExchangeClient** to create a service description (WSDL document) for the Insert, Update, Delete, and Select operations on the SCOTT.EMP table.</span></span> <span data-ttu-id="06709-142">WSDL 會儲存至檔案，EmpOperations.wsdl。</span><span class="sxs-lookup"><span data-stu-id="06709-142">The WSDL is saved to a file, EmpOperations.wsdl.</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
using System.Collections.ObjectModel;  
  
// Needed for WCF and Oracle Adapter  
using System.ServiceModel;  
using Microsoft.ServiceModel.Channels;  
using Microsoft.Adapters.OracleDB;  
  
// Needced for MetadataExchangeClient class  
using System.ServiceModel.Description;  
// Needed for ServiceDescription class  
using System.Web.Services;  
  
namespace OracleMetadataExchange  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            //create a binding  
            OracleDBBinding binding = new OracleDBBinding();  
  
            //create a metadata exchange client that will retrieve metadata according to the WS-MEX standard  
            MetadataExchangeClient client = new MetadataExchangeClient(binding);  
            client.SoapCredentials.UserName.UserName = "SCOTT";  
            client.SoapCredentials.UserName.Password = "TIGER";  
  
            //set up an endpoint address and specifies the operations for which we want metadata  
            string connectionUri = "oracledb://ADAPTER?wsdl"  
                + "&op="  
                + "http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Insert"  
                + "&op="  
                + "http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Update"  
                + "&op="  
                + "http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Delete"  
                + "&op="  
                + "http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Select";  
  
            EndpointAddress address = new EndpointAddress(connectionUri);  
  
            //get the metadata  
            MetadataSet ms = client.GetMetadata(address);  
  
            // Check for the metadata set size   
            Collection<MetadataSection> documentCollection = ms.MetadataSections;  
            if (documentCollection != null && documentCollection.Count > 0)  
            {  
                //get the wsdl from the metadata set  
                System.Web.Services.Description.ServiceDescription wsdl = (System.Web.Services.Description.ServiceDescription)documentCollection[0].Metadata;  
  
                //save the wsdl to a file  
                wsdl.Write("EmpOperations.wsdl");  
  
            }  
  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="06709-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="06709-143">See Also</span></span>  
 [<span data-ttu-id="06709-144">以程式設計方式從 Oracle 資料庫中取得中繼資料</span><span class="sxs-lookup"><span data-stu-id="06709-144">Get Metadata Programmatically from the Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-programmatically-from-the-oracle-database.md)