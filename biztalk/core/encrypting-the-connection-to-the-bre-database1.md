---
title: "加密 BRE Database1 連線 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 63edd2bb-97f1-4b8b-8cdc-f4792909ca86
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0dd585c596f7635417a4e22cbccda04593e7c598
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="encrypting-the-connection-to-the-bre-database"></a>加密 BRE 資料庫的連線
根據公司的安全性原則，請考慮對下列項目加密：  
  
-   登入程序期間傳輸的認證。  
  
-   在網路上，執行「商務規則引擎」(BRE) 原則的用戶端電腦和規則引擎資料庫之間傳輸的資料。  
  
 本主題說明如何對裝載在 [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)] 或 [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)] 上的 BRE 資料庫連線進行加密。  
  
## <a name="to-encrypt-the-connection-to-the-bre-database-hosted-on-sql-server-2008-sp1-or-sql-server-2008-r2"></a>若對 SQL Server 2008 SP1 或 SQL Server 2008 R2 裝載的 BRE 資料庫進行加密連線  
 依預設，用戶端應用程式連接到 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 時，登入程序期間傳輸的認證會經過加密。 如果伺服器未提供憑證，啟動時，[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 會產生自我簽署憑證，用它來對登入封包加密。  
  
 若要啟用之間透過網路傳輸資料的加密[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]和執行個體的用戶端[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]，應該設定**強制加密**在伺服器上的選項**是**或設定**強制通訊協定加密**選項設定為**是**用戶端上。  
  
 當**強制加密**選項設定為**是**在伺服器端，[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]使用 SSL 加密所有通訊*所有用戶端和資料庫伺服器之間*. 換言之，伺服器的所有輸入連線都會經過加密。 若要在伺服器啟用這個選項，建議您使用「SQL Server 組態管理員」，在伺服器中安裝憑證。 如果伺服器中未安裝憑證，伺服器便會在執行個體啟動時自動產生自我簽署憑證。  
  
 此自我簽署憑證可用來代替信任的憑證授權單位發行的憑證，但它並不提供詐騙識別威脅的任何安全防護。 在實際執行環境或連接到網際網路的伺服器上，您不應該仰賴使用自我簽署憑證的 SSL。 已設定選項時，會拒絕存取任何無法支援加密的用戶端。 必須重新啟動 SQL Server 設定後**強制加密**選項。 您可以透過 [SQL Server 組態管理員] ([[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 網路組態]) 設定這個選項。  
  
 當**強制通訊協定加密**設定在用戶端，[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]使用 SSL 加密所有通訊*該用戶端和所有伺服器之間*。 換言之，該用戶端的所有輸出連線都會經過加密。 若要啟用此選項，用戶端上的，您應該安裝憑證的伺服器上如果**信任伺服器憑證**用戶端上的選項設定為**否**。 如果**信任伺服器憑證**用戶端上的選項設定為**是**，用戶端不會驗證伺服器憑證，因此會啟用自我簽署憑證。 您可以透過「SQL Server 組態管理員」([SQL Native Client 組態]) 設定這個選項。  
  
 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]也可讓您啟用的加密*從用戶端到伺服器的特定連線*藉由設定**資料的加密/使用加密**旗標設為**是**中連接字串。 不過，BRE 會自動產生連接字串，而不加密選項設為**是**。 因此，您無法從用戶端電腦對「規則引擎」資料庫伺服器的特定連線進行加密。 相反地，您應該設定**強制通訊協定加密**選項在用戶端，如先前段落中所述。