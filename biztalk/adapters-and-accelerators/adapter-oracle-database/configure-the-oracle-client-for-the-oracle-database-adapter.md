---
title: 設定 Oracle 資料庫配接器的 Oracle 用戶端 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- net service name
- tnsnames.ora
- configuring, the Oracle client
- connect descriptor
- Oracle client, configuring
- Oracle Net Configuration Assistant
- Oracle Net Configuration Assistant, using the
ms.assetid: 2d4c0f20-b3a6-453f-a9b3-65fd5a38c020
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 209d5603a9f8ff8c09185093efb976afb6432d65
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22214110"
---
# <a name="configure-the-oracle-client-for-the-oracle-database-adapter"></a>設定 Oracle 資料庫配接器的 Oracle 用戶端
> [!IMPORTANT]
>  本主題是您用來連接到 Oracle 資料庫 tnsnames.ora 時才適用。  
  
 [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]會連接到 Oracle 資料庫，透過您的電腦上安裝 Oracle 用戶端。 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]網路服務名稱將其傳遞您指定連線 URI Oracle 用戶端，以連接到 Oracle 資料庫中。 網路服務名稱是用來取得目標 Oracle 資料庫服務的連接資訊的 Oracle 用戶端的別名。  
  
 網路服務的名稱是根據命名的方法而設定為使用 Oracle 用戶端解析。 您使用 Oracle Net Configuration Assistant 設定 Oracle 用戶端所使用的命名方法。 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]支援連接到 Oracle 資料庫的本機命名方法。 這個方法會使用本機檔案，tnsnames.ora，解析網路服務名稱。  
  
 Tnsnames.ora 檔案關聯網路服務名稱與連接描述元包含 Oracle 用戶端必須連接到特定的 Oracle 資料庫服務 （執行個體） 的資訊。 以下是從 tnsnames.ora 範例項目。  
  
```  
ADAPTER =  
  (DESCRIPTION =  
    (ADDRESS_LIST =  
      (ADDRESS = (PROTOCOL = TCP)(HOST = yourOracleServer)(PORT = 1521))  
    )  
    (CONNECT_DATA =  
      (SERVICE_NAME = yourOracleDatabaseServiceName)  
    )  
  )  
```  
  
 在此範例項目，配接器是網路服務名稱。 連接描述元指定位址資訊和使用配接器相關聯的 Oracle 資料庫服務的服務名稱。 您可以使用 Oracle Net Configuration Assistant 來建立及設定 tnsnames.ora 以網路服務名稱。 設定網路服務名稱之後，您可以如下列範例所示的連線 URI 中指定它。  
  
```  
oracledb://ADAPTER  
```  
  
 如需有關使用 Oracle Net Configuration Assistant 以及 tnsnames.ora 有關的詳細資訊，請參閱 Oracle 資料庫網路服務系統管理員指南。 特定的安裝，請參閱您的資料庫管理員的相關設定詳細資料。  
  
## <a name="see-also"></a>另請參閱  
[建立 Oracle 資料庫的連接](../../adapters-and-accelerators/adapter-oracle-database/create-a-connection-to-the-oracle-database.md)