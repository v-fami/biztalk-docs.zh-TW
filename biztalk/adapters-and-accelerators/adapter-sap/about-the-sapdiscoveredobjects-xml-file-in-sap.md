---
title: 關於 sap SAPDiscoveredObjects.xml 檔案 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SAPDiscoveredObjects.xml
- .NET Framework Data Provider for mySAP Business Suite
- Data Provider for SAP
- Visual Studio DDEX plug-in
ms.assetid: 46ef600d-57ae-4c42-94ce-3099e42482f1
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1ba0c156e2ad6ab0fcbccb5ba7629f63b0aa490e
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25960716"
---
# <a name="about-the-sapdiscoveredobjectsxml-file-in-sap"></a><span data-ttu-id="1b213-102">關於 sap SAPDiscoveredObjects.xml 檔案</span><span class="sxs-lookup"><span data-stu-id="1b213-102">About the SAPDiscoveredObjects.xml File in SAP</span></span>
<span data-ttu-id="1b213-103">如果您選擇要安裝[!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)] ([!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]) 連同[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝，安裝程式會複製 SAPDiscoveredObjects.xml 檔案通常位於\<安裝磁碟機\>: \Program Files\Common 檔案\Microsoft Shared\Adapters\SAP。</span><span class="sxs-lookup"><span data-stu-id="1b213-103">If you chose to install the [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)] ([!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]) along with the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] installation, the setup program copies the SAPDiscoveredObjects.xml file typically at \<installation drive\>:\Program Files\Common Files\Microsoft Shared\Adapters\SAP.</span></span> <span data-ttu-id="1b213-104">全新安裝之後的檔案內容[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]，如下所示。</span><span class="sxs-lookup"><span data-stu-id="1b213-104">The contents of the file, after a fresh installation of the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], resemble the following.</span></span>  
  
```  
<DiscoveredObjects>  
  <SAP>  
  </SAP>  
</DiscoveredObjects>  
```  
  
 <span data-ttu-id="1b213-105">SAPDiscoveredObjects.xml 檔案的目的是要儲存您探索使用的 SAP 物件 （資料表和 Rfc） [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] DDEX 外掛程式。</span><span class="sxs-lookup"><span data-stu-id="1b213-105">The purpose of the SAPDiscoveredObjects.xml file is to store the SAP objects (tables and RFCs) that you discover using the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)][!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] DDEX plug-in.</span></span> <span data-ttu-id="1b213-106">一旦您已經使用 DDEX 外掛程式來新增更多的 SAP 物件，它們會加到這個 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="1b213-106">Once you have used the DDEX plug-in to add more SAP objects, they are added to this XML file.</span></span> <span data-ttu-id="1b213-107">XML 檔案，看起來像這樣。</span><span class="sxs-lookup"><span data-stu-id="1b213-107">The XML file looks like this.</span></span>  
  
```  
<DiscoveredObjects>  
  <SAP>  
    <Server name="server_name" user="user_name" client="800" type="connection_type">  
      <Tables>  
        <Table>KNA1</Table>  
        <Table>KNAS</Table>  
        <Table>KNAT</Table>  
      </Tables>  
      <RFCs>  
        <RFC>CUSTOMER_CONTACTPS_GET</RFC>  
        <RFC>CUSTOMER_CONTROL_AREA_DATA</RFC>  
        <RFC>CUSTOMER_PARTNERFS_GET</RFC>  
      </RFCs>  
    </Server>  
  </SAP>  
</DiscoveredObjects>  
```  
  
 <span data-ttu-id="1b213-108">`name`屬性 < 伺服器\>元素包含伺服器連線到使用 DDEX 外掛程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="1b213-108">The `name` property of the <Server\> element contains the name of the server that you connect to using the DDEX plug-in.</span></span> <span data-ttu-id="1b213-109">`user`和`client`屬性的 < 伺服器\>元素分別包含使用者名稱和用戶端編號。</span><span class="sxs-lookup"><span data-stu-id="1b213-109">The `user` and `client` properties of the <Server\> element contain the user name and client numbers, respectively.</span></span> <span data-ttu-id="1b213-110">`type`屬性包含連接字串 （A、 B 或 a） 用來連接到 SAP 系統的型別。</span><span class="sxs-lookup"><span data-stu-id="1b213-110">The `type` property contains the type of connection string (A, B, or D) used to connect to an SAP system.</span></span> <span data-ttu-id="1b213-111">如需類型的連接字串的詳細資訊，請參閱[閱讀 SAP 連接字串的資料提供者類型](../../adapters-and-accelerators/adapter-sap/read-about-data-provider-types-for-the-sap-connection-string.md)。</span><span class="sxs-lookup"><span data-stu-id="1b213-111">For more information about the types of connection strings, see [Read about Data Provider types for the SAP Connection String](../../adapters-and-accelerators/adapter-sap/read-about-data-provider-types-for-the-sap-connection-string.md).</span></span>  
  
 <span data-ttu-id="1b213-112">\<資料表\>元素包含的資料表，您將使用的外掛程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="1b213-112">The \<Tables\> element contains the name of the tables that you add using the plug-in.</span></span> <span data-ttu-id="1b213-113">同樣地， \<Rfc\>元素包含您將使用的外掛程式的 Rfc。</span><span class="sxs-lookup"><span data-stu-id="1b213-113">Similarly, the \<RFCs\> element contains the RFCs that you add using the plug-in.</span></span> <span data-ttu-id="1b213-114">如果您連接到多個 SAP 伺服器，另一個\<伺服器\>項目會加入至 XML 檔案，而且對應的資料表和 Rfc 列在\<資料表\>和\<Rfc\>項目。</span><span class="sxs-lookup"><span data-stu-id="1b213-114">If you connect to more than one SAP server, another \<Server\> element is added to the XML file, and the corresponding tables and RFCs are listed under the \<Table\> and \<RFCs\> element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1b213-115">如需使用 Visual Studio DDEX 外掛程式的指示，請參閱[使用資料提供者的 DDEX 外掛程式與 SAP](../../adapters-and-accelerators/adapter-sap/use-the-data-provider-for-sap-with-the-ddex-plug-in.md)。</span><span class="sxs-lookup"><span data-stu-id="1b213-115">For instructions on using the Visual Studio DDEX plug-in, see [Use the Data Provider for SAP with the DDEX Plug-in](../../adapters-and-accelerators/adapter-sap/use-the-data-provider-for-sap-with-the-ddex-plug-in.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b213-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="1b213-116">See Also</span></span>  
 [<span data-ttu-id="1b213-117">關於 .NET Framework Data Provider for mySAP Business Suite</span><span class="sxs-lookup"><span data-stu-id="1b213-117">About the .NET Framework Data Provider for mySAP Business Suite</span></span>](../../adapters-and-accelerators/adapter-sap/about-the-net-framework-data-provider-for-mysap-business-suite.md)