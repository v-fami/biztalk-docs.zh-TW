---
title: "設定 Oracle E-business Suite 配接器用戶端 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 842b6ecc-5334-4cc0-af10-baa7f692ad23
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ada64bf6f54c95f3d6e1c8f968a506476dbbc6fd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configure-the-oracle-client-for-the-e-business-suite-adapter"></a>設定 Oracle E-business Suite 配接器用戶端
> [!IMPORTANT]
>  本主題是您用來連接到 Oracle 資料庫 tnsnames.ora 時才適用。  
  
 若要連接到[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]，配接器連接到電腦上安裝 Oracle 用戶端透過基礎的 Oracle 資料庫。 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]網路服務名稱將其傳遞您在 Oracle 用戶端，以連接到 Oracle E-business Suite 連線 URI 中指定。 網路服務名稱是用來取得目標 Oracle 資料庫服務的連接資訊的 Oracle 用戶端的別名。  
  
 網路服務的名稱是根據命名的方法而設定為使用 Oracle 用戶端解析。 您使用 Oracle Net Configuration Assistant 設定 Oracle 用戶端所使用的命名方法。 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]連接到 Oracle E-business Suite 支援本機命名的方法。 這個方法會使用本機檔案，tnsnames.ora，解析網路服務名稱。  
  
 Tnsnames.ora 檔案關聯網路服務名稱與連接描述元包含 Oracle 用戶端需要連接到特定的 Oracle 資料庫服務 （執行個體） 的資訊。 以下是從 tnsnames.ora 範例項目。  
  
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
oracleebs://ADAPTER  
```  
  
 如需有關使用 Oracle Net Configuration Assistant 以及 tnsnames.ora 有關的詳細資訊，請參閱 Oracle 資料庫網路服務系統管理員指南。 特定的安裝，請參閱您的資料庫管理員的相關設定詳細資料。  
  
## <a name="see-also"></a>另請參閱  
 [建立 Oracle E-business Suite 連線](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-connection-to-oracle-e-business-suite.md)