---
title: "關於 sap SAPDiscoveredObjects.xml 檔案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SAPDiscoveredObjects.xml
- .NET Framework Data Provider for mySAP Business Suite
- Data Provider for SAP
- Visual Studio DDEX plug-in
ms.assetid: 46ef600d-57ae-4c42-94ce-3099e42482f1
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 428d2987465ff1fe09f01979bbe9036def6350b8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="about-the-sapdiscoveredobjectsxml-file-in-sap"></a>關於 sap SAPDiscoveredObjects.xml 檔案
如果您選擇要安裝[!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)]([!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]) 連同[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝，安裝程式會複製 SAPDiscoveredObjects.xml 檔案通常位於\<安裝磁碟機 >: \Program Files\Common Files\MicrosoftShared\Adapters\SAP。 全新安裝之後的檔案內容[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]，如下所示。  
  
```  
<DiscoveredObjects>  
  <SAP>  
  </SAP>  
</DiscoveredObjects>  
```  
  
 SAPDiscoveredObjects.xml 檔案的目的是要儲存您探索使用的 SAP 物件 （資料表和 Rfc） [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] DDEX 外掛程式。 一旦您已經使用 DDEX 外掛程式來新增更多的 SAP 物件，它們會加到這個 XML 檔案。 XML 檔案，看起來像這樣。  
  
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
  
 `name`屬性 < 伺服器\>元素包含伺服器連線到使用 DDEX 外掛程式的名稱。 `user`和`client`屬性的 < 伺服器\>元素分別包含使用者名稱和用戶端編號。 `type`屬性包含連接字串 （A、 B 或 a） 用來連接到 SAP 系統的型別。 如需類型的連接字串的詳細資訊，請參閱[閱讀 SAP 連接字串的資料提供者類型](../../adapters-and-accelerators/adapter-sap/read-about-data-provider-types-for-the-sap-connection-string.md)。  
  
 \<表格 > 項目包含的資料表，您將使用的外掛程式的名稱。 同樣地， \<Rfc > 項目包含您將使用的外掛程式的 Rfc。 如果您連接到多個 SAP 伺服器，另一個\<伺服器 > 項目會加入至 XML 檔案，而且對應的資料表和 Rfc 列在\<資料表 > 和\<Rfc > 項目。  
  
> [!NOTE]
>  如需使用 Visual Studio DDEX 外掛程式的指示，請參閱[使用資料提供者的 DDEX 外掛程式與 SAP](../../adapters-and-accelerators/adapter-sap/use-the-data-provider-for-sap-with-the-ddex-plug-in.md)。  
  
## <a name="see-also"></a>另請參閱  
 [關於.NET Framework Data Provider for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/about-the-net-framework-data-provider-for-mysap-business-suite.md)