---
title: Siebel 連接字串的資料提供者屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- conncting, to the Siebel system
- Data Provider for Siebel, connection string
ms.assetid: 8ab0c29e-e06b-4e74-be4e-9aa862a05539
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0954cbec3c2dbd044037cc817a8ef97b1250bf8b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36988823"
---
# <a name="data-provider-properties-for-the-siebel-connection-string"></a>Siebel 連接字串的資料提供者屬性
[!INCLUDE[adoprovidersiebellong](../../includes/adoprovidersiebellong-md.md)] ([!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]) 會使用[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]存取 Siebel 系統。 [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]依次用以存取 Siebel 系統的 Siebel COM 資料控制項程式庫。 Siebel COM 資料控制項隨附 Siebel Web 用戶端。  

 若要建立 Siebel 系統的連線，ADO.NET 用戶端必須指定編碼成資料庫連接字串的 Siebel 連接屬性。 這是必要的因為[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]會實作**DbConnection**存取基礎[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]繫結。  

 若要連接到 Siebel 系統使用的連接字串[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]包含下列屬性。  


|        屬性        |                                                                                                                                                     描述                                                                                                                                                      |
|------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|        [密碼]        |            Siebel 系統; 上使用者的密碼這個值會區分大小寫。 **注意︰** [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]保留大小寫的值，可以開啟 Siebel 系統上的連線時，您輸入的密碼。             |
|        使用者名稱        |                  Siebel 系統; 中的使用者名稱這個值會區分大小寫。 **注意︰** [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]保留值，可以開啟 Siebel 系統上的連線時，您輸入使用者名稱的大小寫。                  |
|      壓縮       |      之間使用的壓縮演算法[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]與 Siebel 系統。 支援的值為**無**或是**zlib**。 這個參數是選擇性的。 如果未指定，因此 Siebel 系統會提供預設值 (**zlib**)。       |
|       加密       | 若要使用之間的加密類型[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]與 Siebel 系統。 支援的值為**無**， **mscrypto**，或**rsa**。 這個參數是選擇性的。 如果未指定，因此 Siebel 系統會提供預設值 (**無**)。 |
|        語言        |                                                                                                             物件管理員語言。 範例值是**繁體中文**。 此參數為必要。                                                                                                             |
| SiebelEnterpriseServer |                                                                                                                        Siebel Enterprise Server 的名稱。 此參數為必要。                                                                                                                         |
|     SiebelGateway      |                                                                                                                     Siebel 伺服器的 IP 和連接埠組成。 比方說，Siebel_Server:1234。                                                                                                                      |
|  SiebelObjectManager   |                                                                                                             企業伺服器上的 Siebel 物件管理員名稱。 此參數為必要。                                                                                                              |
|    SiebelRepository    |                                     Siebel 儲存機制。 需要伺服器上是否有多個存放庫否則為選擇性。 **注意：** 如果伺服器上有多個存放庫，您必須指定一個目標存放庫 SiebelRepository 參數。                                      |
|      SiebelServer      |                                                                                                       Siebel 伺服器。 所需的所有 Siebel 7.5 伺服器連接數;否則，請勿設定此參數。                                                                                                       |
|       傳輸        |                                                                               傳輸方式;只有**tcpip**支援。 這個參數是選擇性的。 如果未指定，因此 Siebel 系統會提供預設值 (**tcpip**)。                                                                                |

 例如：  

```  
Username=YourUserName;Password=YourPassword;SiebelGateway=Siebel_Server:1234;SiebelObjectManager=obj_mgr;SiebelEnterpriseServer=ent_server;Language=enu;SiebelRepository=siebel_rep  
```  

## <a name="see-also"></a>另請參閱  
 [使用 .NET Framework Data Provider for Siebel eBusiness 應用程式](../../adapters-and-accelerators/adapter-siebel/use-the-net-framework-data-provider-for-siebel-ebusiness-applications.md)