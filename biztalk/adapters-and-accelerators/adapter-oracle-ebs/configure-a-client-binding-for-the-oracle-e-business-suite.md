---
title: "設定用戶端繫結 for Oracle E-business Suite |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1347cbca-5567-43f8-a75e-a23b108692bc
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6a1f3eafdf423926dab4cf48efae8db3044aba9b
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="configure-a-client-binding-for-the-oracle-e-business-suite"></a><span data-ttu-id="ad5fa-102">設定用戶端 for Oracle E-business Suite 繫結</span><span class="sxs-lookup"><span data-stu-id="ad5fa-102">Configure a client binding for the Oracle E-Business Suite</span></span>
<span data-ttu-id="ad5fa-103">產生 WCF 用戶端類別後，您可以建立 WCF 用戶端 （執行個體），並叫用其方法來取用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ad5fa-103">After you have generated the WCF client class, you can create a WCF client (instance) and invoke its methods to consume the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span></span>  
  
 <span data-ttu-id="ad5fa-104">若要建立 WCF 用戶端，您必須指定端點位址和繫結。</span><span class="sxs-lookup"><span data-stu-id="ad5fa-104">To create the WCF client, you must specify an endpoint address and a binding.</span></span> <span data-ttu-id="ad5fa-105">端點位址必須包含有效的 Oracle E-business Suite 連線 URI，而且繫結必須是 Oracle E-business Suite 繫結執行個體 (**OracleEBSBinding**)。</span><span class="sxs-lookup"><span data-stu-id="ad5fa-105">The endpoint address must contain a valid Oracle E-Business Suite connection URI, and the binding must be an instance of an Oracle E-Business Suite binding (**OracleEBSBinding**).</span></span> <span data-ttu-id="ad5fa-106">如需 Oracle E-business Suite 連線 URI 的詳細資訊，請參閱[建立 Oracle E-business Suite 連線](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-connection-to-oracle-e-business-suite.md)。</span><span class="sxs-lookup"><span data-stu-id="ad5fa-106">For more information about the Oracle E-Business Suite connection URI, see [Create a Connection to the Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-connection-to-oracle-e-business-suite.md).</span></span> <span data-ttu-id="ad5fa-107">我們建議您不要指定使用者認證連線 URI 的一部分。</span><span class="sxs-lookup"><span data-stu-id="ad5fa-107">We recommend that you do not specify the user credentials as part of the connection URI.</span></span> <span data-ttu-id="ad5fa-108">您可以改為使用**ClientCredentials** WCF 用戶端，如本主題所述的屬性。</span><span class="sxs-lookup"><span data-stu-id="ad5fa-108">You may instead use the **ClientCredentials** property of the WCF client, as explained in this topic.</span></span>  
  
 <span data-ttu-id="ad5fa-109">在您的程式碼或組態檔中，您可以指定 Oracle E-business Suite 繫結和端點位址。</span><span class="sxs-lookup"><span data-stu-id="ad5fa-109">You can specify the Oracle E-Business Suite binding and the endpoint address in your code or in a configuration file.</span></span> <span data-ttu-id="ad5fa-110">當您使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]產生 WCF 用戶端類別，組態檔 (app.config) 也會建立專案。</span><span class="sxs-lookup"><span data-stu-id="ad5fa-110">When you use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] to generate the WCF client class, a configuration file (app.config) is also created for your project.</span></span> <span data-ttu-id="ad5fa-111">這個檔案包含反映的繫結屬性和連接資訊 （除了認證），當您連接至 Oracle E-business Suite，與您指定的組態設定[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ad5fa-111">This file contains configuration settings that reflect the binding properties and connection information (except credentials) that you specified when you connected to the Oracle E-Business Suite with the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
## <a name="specifying-the-binding-and-endpoint-address-in-code"></a><span data-ttu-id="ad5fa-112">在程式碼中指定的繫結和端點位址</span><span class="sxs-lookup"><span data-stu-id="ad5fa-112">Specifying the Binding and Endpoint Address in Code</span></span>  
 <span data-ttu-id="ad5fa-113">下列程式碼示範如何建立 WCF 用戶端藉由在程式碼中使用指定的繫結與端點位址**ClientCredentials** WCF 用戶端的屬性。</span><span class="sxs-lookup"><span data-stu-id="ad5fa-113">The following code shows how to create a WCF client by specifying the binding and endpoint address in code using the **ClientCredentials** property of the WCF client.</span></span>  
  
```  
//Create an Oracle EBS binding and set the binding properties  
OracleEBSBinding binding = new OracleEBSBinding();  
binding.OracleUserName = "myOracleEBSUser";  
binding.OraclePassword = "myOracleEBSPassword";  
binding.OracleEBSResponsibilityName = "Responsibility";  
binding.OracleEBSOrganizationId = "204";  
  
//Create the client endpoint   
EndpointAddress address = new EndpointAddress("oracleebs://<oracleebs_instance_name>/");  
  
//Create the client and specify the credentials  
ConcurrentPrograms_ARClient client = new ConcurrentPrograms_ARClient(binding,address);  
client.ClientCredentials.UserName.UserName = "myuser";  
client.ClientCredentials.UserName.Password = "mypassword";  
  
//Open the client  
client.Open();  
```  
  
## <a name="specifying-the-binding-and-endpoint-address-in-a-configuration-file"></a><span data-ttu-id="ad5fa-114">在組態檔中指定的繫結和端點位址</span><span class="sxs-lookup"><span data-stu-id="ad5fa-114">Specifying the Binding and Endpoint Address in a Configuration File</span></span>  
 <span data-ttu-id="ad5fa-115">下列程式碼會示範如何建立 WCF 用戶端的 app.config 檔案中指定的繫結和端點位址。</span><span class="sxs-lookup"><span data-stu-id="ad5fa-115">The following code shows how to create a WCF client by specifying the binding and endpoint address in an app.config file.</span></span>  
  
```  
//Create the client by specifying the endpoint name in the app.config. In this case, the binding properties  
//must also be specified in the app.config.  
ConcurrentPrograms_ARClient client = new ConcurrentPrograms_ARClient("OracleEBSBinding_ConcurrentPrograms_AR");  
  
//Specify the credentials   
client.ClientCredentials.UserName.UserName = "myuser";  
client.ClientCredentials.UserName.Password = "mypassword";  
  
client.Open();  
```  
  
 <span data-ttu-id="ad5fa-116">下列 XML 顯示為建立的組態檔**客戶介面**並行程式[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ad5fa-116">The following XML shows the configuration file created for the **Customer Interface** concurrent program by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span> <span data-ttu-id="ad5fa-117">此檔案包含在上述範例中所參考的用戶端端點組態。</span><span class="sxs-lookup"><span data-stu-id="ad5fa-117">This file contains the client endpoint configuration referenced in the preceding example.</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<configuration xmlns="http://schemas.microsoft.com/.NetConfiguration/v2.0">  
    <system.serviceModel>  
        <bindings>  
            <oracleEBSBinding>  
                <binding openTimeout="00:05:00" name="OracleEBSBinding" closeTimeout="00:01:00"  
                    receiveTimeout="00:10:00" sendTimeout="00:01:00" clientCredentialType="Database"  
                    inboundOperationType="Polling" metadataPooling="true" statementCachePurge="false"  
                    statementCacheSize="10" pollWhileDataFound="false" pollingInterval="30"  
                    useOracleConnectionPool="true" minPoolSize="1" maxPoolSize="100"  
                    incrPoolSize="5" decrPoolSize="1" connectionLifetime="0" acceptCredentialsInUri="false"  
                    useAmbientTransaction="true" notifyOnListenerStart="true"  
                    notificationPort="-1" dataFetchSize="65536" longDatatypeColumnSize="32512"  
                    skipNilNodes="true" maxOutputAssociativeArrayElements="32"  
                    enableSafeTyping="false" insertBatchSize="20" useSchemaInNameSpace="true"  
                    enableBizTalkCompatibilityMode="true">  
                    <mlsSettings language="" dateFormat="" dateLanguage="" numericCharacters=""  
                        sort="" territory="" comparison="" currency="" dualCurrency=""  
                        iSOCurrency="" calendar="" lengthSemantics="" nCharConversionException="true"  
                        timeStampFormat="" timeStampTZFormat="" timeZone="" />  
                </binding>  
            </oracleEBSBinding>  
        </bindings>  
        <client>  
            <endpoint address="oracleebs://ebs-70-12/" binding="oracleEBSBinding"  
                bindingConfiguration="OracleEBSBinding" contract="ConcurrentPrograms_AR"  
                name="OracleEBSBinding_ConcurrentPrograms_AR" />  
        </client>  
    </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="ad5fa-118">如果專案有一個以上的 WCF 用戶端，會有多個用戶端組態檔中定義的端點項目。</span><span class="sxs-lookup"><span data-stu-id="ad5fa-118">If a project has more than one WCF client, there will be multiple client endpoint entries defined in the configuration file.</span></span> <span data-ttu-id="ad5fa-119">每個 WCF 用戶端項目必須根據其繫結組態和目標 Oracle E-business Suite 成品的唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="ad5fa-119">Each WCF client entry will have a unique name based on its binding configuration and target Oracle E-Business Suite artifact.</span></span> <span data-ttu-id="ad5fa-120">如果您連接多個的時間，以建立 WCF 用戶端專案中，多個繫結組態項目將會建立，其中每個連接。</span><span class="sxs-lookup"><span data-stu-id="ad5fa-120">If you connect multiple times to create the WCF clients in your project, multiple binding configuration entries will be created, one for each connection.</span></span> <span data-ttu-id="ad5fa-121">這些繫結組態項目將會透過下列方式命名： OracleEBSBinding、 OracleEBSBinding1，依此類推。</span><span class="sxs-lookup"><span data-stu-id="ad5fa-121">These binding configuration entries will be named in the following manner: OracleEBSBinding, OracleEBSBinding1, and so on.</span></span> <span data-ttu-id="ad5fa-122">在特定的連接期間建立的每個用戶端端點項目會參考該連接期間所建立的繫結項目。</span><span class="sxs-lookup"><span data-stu-id="ad5fa-122">Each client endpoint entry created during a specific connection will reference the binding entry created during that connection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad5fa-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="ad5fa-123">See Also</span></span>  
 [<span data-ttu-id="ad5fa-124">開發 Oracle E-business Suite 應用程式使用 WCF 服務模型</span><span class="sxs-lookup"><span data-stu-id="ad5fa-124">Develop Oracle E-Business Suite Applications using the WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/develop-oracle-e-business-suite-applications-using-the-wcf-service-model.md)