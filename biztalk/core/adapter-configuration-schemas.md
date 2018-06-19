---
title: 配接器組態結構描述 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cc08fa71-c5f7-4365-9506-e02351b17567
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 89ca7d02c756fdbdf819e1a15069a95d0784d764
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25966500"
---
# <a name="adapter-configuration-schemas"></a><span data-ttu-id="10aa7-102">配接器組態結構描述</span><span class="sxs-lookup"><span data-stu-id="10aa7-102">Adapter Configuration Schemas</span></span>
<span data-ttu-id="10aa7-103">配接器的設計階段組態中會使用不同類型的結構描述。</span><span class="sxs-lookup"><span data-stu-id="10aa7-103">Different types of schemas are used in design-time configuration of an adapter.</span></span> <span data-ttu-id="10aa7-104">依據屬性值的可見性和範圍，將會修改及使用不同的結構描述。</span><span class="sxs-lookup"><span data-stu-id="10aa7-104">Depending upon the visibility and scope of property values, different schemas are modified and used.</span></span>  
  
## <a name="handler-schemas"></a><span data-ttu-id="10aa7-105">處理常式結構描述</span><span class="sxs-lookup"><span data-stu-id="10aa7-105">Handler Schemas</span></span>  
 <span data-ttu-id="10aa7-106">來自處理常式的配接器組態適用於全域範圍的配接器及其所有取用者。</span><span class="sxs-lookup"><span data-stu-id="10aa7-106">Adapter configuration that comes from a handler applies to the adapter and all its consumers on a global scope.</span></span> <span data-ttu-id="10aa7-107">系統管理員可以在設計階段靜態地變更處理常式組態，方法是使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台展開配接器的接收或傳送處理常式，並顯示指定之主控件的屬性。</span><span class="sxs-lookup"><span data-stu-id="10aa7-107">An administrator can statically alter handler configuration at design time by using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console to expand the adapter's receive or send handler and bring up the properties of the specified host.</span></span>  
  
 <span data-ttu-id="10aa7-108">SDK 中包含的範例 FILE 配接器具有一組 XSD 檔案，可以用來設定其接收位置、傳送埠、接收處理常式和傳送處理常式。</span><span class="sxs-lookup"><span data-stu-id="10aa7-108">The sample file adapter included in the SDK has a set of XSD files used to configure its receive location, send port, receive handler, and send handler.</span></span> <span data-ttu-id="10aa7-109">請修改這些 XSD 檔案，讓您的自訂配接器可以接收需要的組態屬性。</span><span class="sxs-lookup"><span data-stu-id="10aa7-109">Modify these XSD files so that your custom adapter receives the configuration properties it requires.</span></span> <span data-ttu-id="10aa7-110">在範例 FILE 配接器隨附的檔案中，您必須修改的檔案包括 TransmitHandler.xsd 和 ReceiveHandler.xsd 結構描述檔案。</span><span class="sxs-lookup"><span data-stu-id="10aa7-110">The files included with the sample file adapter that you need to modify are the TransmitHandler.xsd and ReceiveHandler.xsd schema files.</span></span> <span data-ttu-id="10aa7-111">這些檔案會藉由控制用來在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台中設定處理常式的屬性頁，以設定傳送處理常式和接收處理常式。</span><span class="sxs-lookup"><span data-stu-id="10aa7-111">These files configure the send handler and receive handler, respectively, by controlling the property pages used to configure the handlers in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
 <span data-ttu-id="10aa7-112">請依照您的配接器需求，建立每個端點所需的組態屬性清單。</span><span class="sxs-lookup"><span data-stu-id="10aa7-112">Using your adapter requirements, create a list of configuration properties required for each of the endpoints.</span></span> <span data-ttu-id="10aa7-113">如果所有的組態屬性都是全域屬性，則可能只需修改傳送和接收埠組態。</span><span class="sxs-lookup"><span data-stu-id="10aa7-113">If all of your configuration properties are global, you may only need to modify the send and receive port configurations.</span></span> <span data-ttu-id="10aa7-114">如果您需要為每個傳送埠或接收位置設定配接器屬性，則必須同時修改接收位置和傳送埠組態檔案。</span><span class="sxs-lookup"><span data-stu-id="10aa7-114">If the adapter properties need to be set for each send port or receive location, you have to modify the receive location and send port configuration files as well.</span></span>  
  
 <span data-ttu-id="10aa7-115">配接器架構會提供結構描述延伸模組和進階組態選項，以支援一般配接器的組態需求。</span><span class="sxs-lookup"><span data-stu-id="10aa7-115">The Adapter Framework provides schema extensions and advanced configuration options to support common adapter configuration requirements.</span></span> <span data-ttu-id="10aa7-116">它也提供了不在範例 FILE 配接器隨附之結構描述中的延伸模組。</span><span class="sxs-lookup"><span data-stu-id="10aa7-116">It also provides extensions that are not in the schema included with the sample file adapter.</span></span> <span data-ttu-id="10aa7-117">如需配接器架構結構描述延伸模組的詳細資訊，請參閱[配接器架構組態結構描述延伸模組](../core/adapter-framework-configuration-schema-extensions.md)。</span><span class="sxs-lookup"><span data-stu-id="10aa7-117">For more information about the Adapter Framework schema extensions, see [Adapter Framework Configuration Schema Extensions](../core/adapter-framework-configuration-schema-extensions.md).</span></span> <span data-ttu-id="10aa7-118">如需自訂下拉式編輯器和自訂類型轉換器等進階的組態選項的詳細資訊，請參閱[介面卡的進階組態元件](../core/advanced-configuration-components-for-adapters.md)。</span><span class="sxs-lookup"><span data-stu-id="10aa7-118">For more information about advanced configuration options such as custom drop-down editors and custom type converters, see [Advanced Configuration Components for Adapters](../core/advanced-configuration-components-for-adapters.md).</span></span>  
  
 <span data-ttu-id="10aa7-119">本主題結尾的程式碼來自 TransmitHandler.xsd 檔案，而且會產生下列屬性頁。</span><span class="sxs-lookup"><span data-stu-id="10aa7-119">The code at the end of this topic is from the TransmitHandler.xsd file, and produces the following property page.</span></span>  
  
 <span data-ttu-id="10aa7-120">![](../core/media/ebiz-prog-custad-sh.gif "ebiz_prog_custad_sh")</span><span class="sxs-lookup"><span data-stu-id="10aa7-120">![](../core/media/ebiz-prog-custad-sh.gif "ebiz_prog_custad_sh")</span></span>  
<span data-ttu-id="10aa7-121">TransmitHandler.xsd 檔案建立的傳送處理常式屬性頁</span><span class="sxs-lookup"><span data-stu-id="10aa7-121">Send handler property page created by the TransmitHandler.xsd file</span></span>  
  
 <span data-ttu-id="10aa7-122">請注意使用\<baf: designer\>， \<baf:displayname\>，和\<baf: description\>如下所示之 TransmitHandler.xsd 程式碼中的標記。</span><span class="sxs-lookup"><span data-stu-id="10aa7-122">Note the use of the \<baf:designer\>, \<baf:displayname\>, and \<baf:description\> tags in the TransmitHandler.xsd code that is shown below.</span></span> <span data-ttu-id="10aa7-123">這些標記是配接器架構提供的自訂裝飾，可以加快產生這些屬性頁的速度。</span><span class="sxs-lookup"><span data-stu-id="10aa7-123">These are custom decorations provided by the Adapter Framework to make the generation of these property pages faster.</span></span>  
  
 <span data-ttu-id="10aa7-124">如需所有可用的配接器架構內使用的裝飾的清單，請參閱[配接器架構組態結構描述裝飾標記](../core/adapter-framework-configuration-schema-decoration-tags.md)。</span><span class="sxs-lookup"><span data-stu-id="10aa7-124">For a list of all of the decorations available for use within the Adapter Framework, see [Adapter Framework Configuration Schema Decoration Tags](../core/adapter-framework-configuration-schema-decoration-tags.md).</span></span>  
  
 <span data-ttu-id="10aa7-125">請注意，此結構描述只有一個項目，且未包含 URI 項目。</span><span class="sxs-lookup"><span data-stu-id="10aa7-125">Note that the schema has only one element and does not contain a URI element.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="10aa7-126">請勿將敏感的顧客資料儲存在預設的配接器結構描述中。</span><span class="sxs-lookup"><span data-stu-id="10aa7-126">Do not store sensitive customer data in the default adapter schema.</span></span> <span data-ttu-id="10aa7-127">基於安全性考量，您只能在部署配接器之後設定使用者名稱及密碼資訊。</span><span class="sxs-lookup"><span data-stu-id="10aa7-127">For security reasons, configure user name and password information only after you deploy an adapter.</span></span> <span data-ttu-id="10aa7-128">如此即可確保這些資訊會儲存到企業單一登入 (SSO) 資料庫中。</span><span class="sxs-lookup"><span data-stu-id="10aa7-128">This ensures that the information gets stored in the Enterprise Single Sign-On (SSO) database.</span></span> <span data-ttu-id="10aa7-129">如需 SSO 資料庫的詳細資訊，請參閱[使用 SSO](../core/using-sso.md)。</span><span class="sxs-lookup"><span data-stu-id="10aa7-129">For more information about the SSO database, see [Using SSO](../core/using-sso.md).</span></span>  
  
```  
<?xml version="1.0" encoding="utf-16"?>  
<xs:schema xmlns:baf="BiztalkAdapterFramework.xsd"   
xmlns:b="http://schemas.microsoft.com/BizTalk/2003"   
xmlns="http://tempuri.org/XMLSchema1.xsd"   
elementFormDefault="qualified" targetNamespace="http://tempuri.org/XMLSchema1.xsd"   
id="TransmitHandler" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:element name="Config">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element default="50" name="sendBatchSize" type="xs:int" >  
      <xs:annotation>  
         <xs:appinfo>  
            <baf:designer>  
               <baf:displayname _locID="sendBatchSizeName">Batch Size</baf:displayname>  
               <baf:description _locID="sendBatchSizeDesc">Enter the   
maximum number of files to be transmitted per batch</baf:description>  
            </baf:designer>  
         </xs:appinfo>  
      </xs:annotation>  
   </xs:element>  
  
        <xs:element default="4096" name="bufferSize" type="xs:int" >  
      <xs:annotation>  
         <xs:appinfo>  
            <baf:designer>  
               <baf:displayname _locID="bufferSizeName">Write Buffer Size</baf:displayname>  
               <baf:description _locID="bufferSizeDesc">Enter the size of   
the buffer used to write the file</baf:description>  
            </baf:designer>  
         </xs:appinfo>  
      </xs:annotation>  
   </xs:element>  
  
        <xs:element default="1" name="threadsPerCPU" type="xs:int" >  
      <xs:annotation>  
         <xs:appinfo>  
            <baf:designer>  
               <baf:displayname _locID="threadsPerCPUName">Threads Per CPU</baf:displayname>  
               <baf:description _locID="threadsPerCPUDesc">Enter the   
number of threads per CPU to execute in the thread pool</baf:description>  
            </baf:designer>  
         </xs:appinfo>  
      </xs:annotation>  
   </xs:element>  
  
      </xs:sequence>  
    </xs:complexType>  
  </xs:element>  
</xs:schema>  
```  
  
## <a name="send-port-and-receive-location-schemas"></a><span data-ttu-id="10aa7-130">傳送埠和接收位置結構描述</span><span class="sxs-lookup"><span data-stu-id="10aa7-130">Send Port and Receive Location Schemas</span></span>  
 <span data-ttu-id="10aa7-131">若要為配接器設定連接埠專用的屬性，請修改接收位置和傳送埠組態結構描述。</span><span class="sxs-lookup"><span data-stu-id="10aa7-131">To set port-specific properties for your adapter, modify the receive location and send port configuration schemas.</span></span> <span data-ttu-id="10aa7-132">TransmitLocation.xsd 和 ReceiveLocation.xsd 結構描述檔案會分別設定傳送埠和接收位置。</span><span class="sxs-lookup"><span data-stu-id="10aa7-132">The TransmitLocation.xsd and ReceiveLocation.xsd schema files configure the send port and receive location, respectively.</span></span>  
  
 <span data-ttu-id="10aa7-133">配接器架構會提供結構描述延伸模組和進階組態選項，以支援一般配接器的組態需求。</span><span class="sxs-lookup"><span data-stu-id="10aa7-133">The Adapter Framework provides schema extensions and advanced configuration options to support common adapter configuration requirements.</span></span> <span data-ttu-id="10aa7-134">如需配接器架構結構描述延伸模組的詳細資訊，請參閱[配接器架構組態結構描述延伸模組](../core/adapter-framework-configuration-schema-extensions.md)。</span><span class="sxs-lookup"><span data-stu-id="10aa7-134">For more information about the Adapter Framework schema extensions, see [Adapter Framework Configuration Schema Extensions](../core/adapter-framework-configuration-schema-extensions.md).</span></span> <span data-ttu-id="10aa7-135">如需自訂下拉式編輯器和自訂類型轉換器等進階的組態選項的詳細資訊，請參閱[介面卡的進階組態元件](../core/advanced-configuration-components-for-adapters.md)。</span><span class="sxs-lookup"><span data-stu-id="10aa7-135">For more information about advanced configuration options such as custom drop-down editors and custom type converters, see [Advanced Configuration Components for Adapters](../core/advanced-configuration-components-for-adapters.md).</span></span>  
  
 <span data-ttu-id="10aa7-136">下列程式碼來自 TransmitLocation.xsd 檔案，而且會產生下列屬性頁。</span><span class="sxs-lookup"><span data-stu-id="10aa7-136">The code that follows is from the TransmitLocation.xsd file, and produces the following property page.</span></span>  
  
 <span data-ttu-id="10aa7-137">![](../core/media/ebiz-prog-custad-sp.gif "ebiz_prog_custad_sp")</span><span class="sxs-lookup"><span data-stu-id="10aa7-137">![](../core/media/ebiz-prog-custad-sp.gif "ebiz_prog_custad_sp")</span></span>  
<span data-ttu-id="10aa7-138">說明範例 FILE 配接器的傳送埠屬性頁</span><span class="sxs-lookup"><span data-stu-id="10aa7-138">Illustrates the send port property page for the sample file adapter</span></span>  
  
 <span data-ttu-id="10aa7-139">請注意下列 TransmitLocation.xsd 檔案中的傳送埠組態包含\<baf: designer\>， \<baf:displayname\>，和\<baf: description\>一樣標記傳送處理常式，它也會使用\<baf:category\>標記。</span><span class="sxs-lookup"><span data-stu-id="10aa7-139">Note in the TransmitLocation.xsd file below that the send port configuration contains the \<baf:designer\>, \<baf:displayname\>, and \<baf:description\> tags, just like the send handler, and it also uses the \<baf:category\> tag.</span></span> <span data-ttu-id="10aa7-140">類別標記可以讓您將屬性群組在一起。</span><span class="sxs-lookup"><span data-stu-id="10aa7-140">The category tag enables you to group properties together.</span></span> <span data-ttu-id="10aa7-141">如果您有多種類別，則類別將可展開及摺疊，而且會顯示成該類別中屬性上方的灰色標頭。</span><span class="sxs-lookup"><span data-stu-id="10aa7-141">If you have more than one category, the category is expandable and collapsible and appears in gray as a header above the properties in that category.</span></span> <span data-ttu-id="10aa7-142">如需詳細資訊，請參閱[配接器架構組態結構描述延伸模組](../core/adapter-framework-configuration-schema-extensions.md)。</span><span class="sxs-lookup"><span data-stu-id="10aa7-142">For more information, see [Adapter Framework Configuration Schema Extensions](../core/adapter-framework-configuration-schema-extensions.md).</span></span>  
  
 <span data-ttu-id="10aa7-143">此結構描述也包含 URI 欄位。</span><span class="sxs-lookup"><span data-stu-id="10aa7-143">This schema also contains a URI field.</span></span> <span data-ttu-id="10aa7-144">在配接器進行驗證處理期間，當您在傳送埠屬性頁中輸入所有欄位資訊之後，將會顯示一個頁面，並在該頁面上填入這個欄位。</span><span class="sxs-lookup"><span data-stu-id="10aa7-144">This is populated on the page that appears after you enter all of the field information on the send port property page during the validation processing by the adapter.</span></span>  
  
```  
<?xml version="1.0" encoding="utf-16"?>  
<xs:schema xmlns:baf="BiztalkAdapterFramework.xsd" xmlns:b="http://schemas.microsoft.com/BizTalk/2003" xmlns="http://tempuri.org/XMLSchema1.xsd" elementFormDefault="qualified" targetNamespace="http://tempuri.org/XMLSchema1.xsd" id="TransmitLocation" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:element name="Config">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="directory" type="xs:string">  
      <xs:annotation>  
         <xs:appinfo>  
            <baf:designer xmlns:baf="BiztalkAdapterFramework.xsd">  
               <baf:displayname _locID="sendDirectoryName">Directory</baf:displayname>  
               <baf:description _locID="sendDirectoryDesc">Directory to write the file to</baf:description>  
                         <baf:category _locID="transmitLocationCategory">Transmit Location</baf:category>  
                    </baf:designer>  
         </xs:appinfo>  
      </xs:annotation>  
        </xs:element>  
  
        <xs:element default="%MessageID%.xml" name="fileName" type="xs:string">  
          <xs:annotation>  
            <xs:appinfo>  
              <baf:designer xmlns:baf="BiztalkAdapterFramework.xsd">  
                <baf:displayname _locID="fileNameName">File Name</baf:displayname>  
      <baf:description _locID="fileNameDesc">The name of the file that will be written</baf:description>  
                <baf:category _locID="transmitLocationCategory">Transmit Location</baf:category>  
              </baf:designer>  
            </xs:appinfo>  
          </xs:annotation>  
        </xs:element>  
  
        <xs:element default="2" name="fileCopyMode" type="CopyMode">  
          <xs:annotation>  
            <xs:appinfo>  
              <baf:designer xmlns:baf="BiztalkAdapterFramework.xsd">  
                <baf:displayname _locID="fileCopyModeName">File Mode</baf:displayname>  
                <baf:category _locID="transmitLocationCategory">Transmit Location</baf:category>  
              </baf:designer>  
            </xs:appinfo>  
          </xs:annotation>  
        </xs:element>  
  
        <xs:element name="uri" type="xs:string">  
          <xs:annotation>  
            <xs:appinfo>  
              <baf:designer xmlns:baf="BiztalkAdapterFramework.xsd">  
                <baf:browsable show="false" />  
              </baf:designer>  
            </xs:appinfo>  
          </xs:annotation>  
        </xs:element>  
  
   <!-- An example of how an SSO affiliate application would be configured for this endpoint: -->  
   <!--  
   <xs:element name="ssoAffiliateApplication" type="baf:SSOList">  
      <xs:annotation>  
         <xs:appinfo>  
            <baf:designer>  
               <baf:displayname _locID="ssoAffiliateApplicationName">SSO Affiliate</baf:displayname>  
               <baf:description _locID="ssoAffiliateApplicationDesc">The Single Sign On (SSO) Affiliate Application</baf:description>  
               <baf:category _locID="ftpCategory">FTP</baf:category>  
            </baf:designer>  
         </xs:appinfo>  
      </xs:annotation>  
   </xs:element>  
   -->  
  
      </xs:sequence>  
    </xs:complexType>  
  </xs:element>  
  
  <xs:simpleType name="CopyMode">  
    <xs:restriction base="xs:int">  
      <xs:enumeration value="0">  
        <xs:annotation>  
          <xs:appinfo>  
            <baf:designer xmlns:baf="BiztalkAdapterFramework.xsd">  
              <baf:displayname _locID="appendName">Append</baf:displayname>  
            </baf:designer>  
          </xs:appinfo>  
        </xs:annotation>  
      </xs:enumeration>  
      <xs:enumeration value="1">  
        <xs:annotation>  
          <xs:appinfo>  
            <baf:designer xmlns:baf="BiztalkAdapterFramework.xsd">  
              <baf:displayname _locID="createName">Create</baf:displayname>  
            </baf:designer>  
          </xs:appinfo>  
        </xs:annotation>  
      </xs:enumeration>  
      <xs:enumeration value="2">  
        <xs:annotation>  
          <xs:appinfo>  
            <baf:designer xmlns:baf="BiztalkAdapterFramework.xsd">  
              <baf:displayname _locID="createNewName">CreateNew</baf:displayname>  
            </baf:designer>  
          </xs:appinfo>  
        </xs:annotation>  
      </xs:enumeration>  
    </xs:restriction>  
  </xs:simpleType>  
</xs:schema>  
```