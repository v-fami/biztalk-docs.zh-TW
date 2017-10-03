---
title: "資料提供者內容，針對 Siebel 的連接字串 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- conncting, to the Siebel system
- Data Provider for Siebel, connection string
ms.assetid: 8ab0c29e-e06b-4e74-be4e-9aa862a05539
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1caedbc1e9560c1bc4d97669241046f0959c2db6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="data-provider-properties-for-the-siebel-connection-string"></a>Siebel 連接字串的資料提供者內容
[!INCLUDE[adoprovidersiebellong](../../includes/adoprovidersiebellong-md.md)] ([!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]) 會使用[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]存取 Siebel 系統。 [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]依次用以存取 Siebel 系統的 Siebel 資料的 COM 控制項程式庫。 Siebel COM 資料控制項來自配套 Siebel Web 用戶端。  
  
 若要建立 Siebel 系統的連接能力，ADO.NET 用戶端必須指定編碼成資料庫連接字串的 Siebel 連接屬性。 這是必要的因為[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]實作**DbConnection**存取基礎[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]繫結。  
  
 若要連接至 Siebel 系統使用的連接字串[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]包含下列屬性。  
  
|屬性|Description|  
|--------------|-----------------|  
|密碼|Siebel 系統; 上使用者的密碼這個值會區分大小寫。 **注意：** [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]保留開啟 Siebel 系統上的連線時，您輸入的密碼值的大小寫。|  
|使用者名稱|Siebel 系統; 上的使用者名稱這個值會區分大小寫。 **注意：** [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]保留開啟 Siebel 系統上的連線時，您輸入使用者名稱值的大小寫。|  
|壓縮|之間使用的壓縮演算法[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]與 Siebel 系統。 支援的值為**無**或**zlib**。 這個參數是選擇性的。 如果未指定，則 Siebel 系統會提供預設值 (**zlib**)。|  
|加密|使用之間的加密類型[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]與 Siebel 系統。 支援的值為**無**， **mscrypto**，或**rsa**。 這個參數是選擇性的。 如果未指定，則 Siebel 系統會提供預設值 (**無**)。|  
|語言|物件管理員語言。 範例值是**繁體中文**。 此參數為必要。|  
|SiebelEnterpriseServer|Siebel 企業伺服器名稱。 此參數為必要。|  
|SiebelGateway|Siebel 伺服器的 IP 和連接埠所組成。 例如，Siebel_Server:1234。|  
|SiebelObjectManager|企業伺服器上的 Siebel 物件管理員名稱。 此參數為必要。|  
|SiebelRepository|Siebel 儲存機制。 需要伺服器上是否有一個以上的儲存機制否則為選擇性。 **注意：**如果伺服器上有一個以上的儲存機制，您必須指定一個目標存放庫 SiebelRepository 參數中。|  
|SiebelServer|Siebel 伺服器。 所需的所有 Siebel 7.5 伺服器連接。否則，請勿設定此參數。|  
|傳輸|傳輸方式;只有**tcpip**支援。 這個參數是選擇性的。 如果未指定，則 Siebel 系統會提供預設值 (**tcpip**)。|  
  
 例如：  
  
```  
Username=YourUserName;Password=YourPassword;SiebelGateway=Siebel_Server:1234;SiebelObjectManager=obj_mgr;SiebelEnterpriseServer=ent_server;Language=enu;SiebelRepository=siebel_rep  
```  
  
## <a name="see-also"></a>另請參閱  
 [使用.NET Framework Data Provider for Siebel eBusiness 應用程式](../../adapters-and-accelerators/adapter-siebel/use-the-net-framework-data-provider-for-siebel-ebusiness-applications.md)