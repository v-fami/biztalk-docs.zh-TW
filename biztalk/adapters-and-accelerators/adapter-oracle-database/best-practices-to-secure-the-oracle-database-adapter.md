---
title: 最佳作法來保護 Oracle 資料庫配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- security, best practices for connection between the Oracle Database adapter and the Oracle database
- security, best practices for WCF diagnostic tracing and message logging
- security, best practices for hosting the Oracle Database adapter in IIS
- credentials
- security, best practices
- security
- security, best practices for consuming the Oracle Database adapter with BizTalk Server
- security, protecting sensitive data
- user name password credential
- security, best practices for consuming the Oracle Database adapter with programming solutions
ms.assetid: 689e8442-91c9-4fe0-a0a0-ce5f5a98ab38
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1b7fcebeb32d4eee9d0e98367d6a852056fe5a68
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22215726"
---
# <a name="best-practices-to-secure-the-oracle-database-adapter"></a>若要保護 Oracle 資料庫配接器的最佳作法
本章節提供更完整地保護機密資料，當您使用或開發使用的應用程式時，應該遵循的最佳作法[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]。  
  
## <a name="security-best-practices-for-the-connection-between-the-oracle-database-adapter-and-the-oracle-database"></a>Oracle 資料庫配接器與 Oracle 資料庫之間的連線的安全性最佳作法  
  
-   [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]不提供支援以便它與 Oracle 資料庫之間的安全通訊。 您必須提供一個機制，有助於確保適當的配接器與 Oracle 資料庫之間交換資料的安全性等級。  
  
-   Oracle 資料庫連線 URI 中未提供使用者名稱密碼認證。 請參閱下列章節，以另一種方法提供的認證來[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。  
  
-   [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]也可讓您使用 Windows 驗證連接到 Oracle 資料庫時，產生中繼資料，並執行作業，透過[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]或[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 之前使用 Windows 驗證，您必須先執行中所列的步驟[連接到 Oracle 資料庫使用 Windows 驗證](../../adapters-and-accelerators/adapter-oracle-database/connect-to-the-oracle-database-using-windows-authentication.md)。  
  
 如需詳細資訊，請參閱[Oracle 資料庫與配接器之間的安全性](../../adapters-and-accelerators/adapter-oracle-database/security-between-the-oracle-database-and-the-adapter.md)。  
  
## <a name="security-best-practices-for-consuming-the-oracle-database-adapter-with-biztalk-server"></a>使用 BizTalk Server 與 Oracle 資料庫配接器的安全性最佳作法  
  
-   Oracle 資料庫連線 URI 中未提供使用者名稱密碼認證。  
  
-   當您使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，輸入從 Oracle 資料庫使用者名稱密碼認證**安全性** 索引標籤**設定配接器** 對話方塊。  
  
-   當您設定的 BizTalk Wcf-custom 配接器[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]傳送埠，輸入從 Oracle 資料庫使用者名稱密碼認證**認證** 索引標籤**設定 WCF 自訂傳輸**  對話方塊。  
  
-   當您設定的 BizTalk Wcf-custom 配接器[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]上接收位置，輸入從 Oracle 資料庫使用者名稱密碼認證**其他** 索引標籤**設定 WCF 自訂傳輸**  對話方塊。  
  
-   [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]也可讓您使用 Windows 驗證連接到 Oracle 資料庫時，產生中繼資料，並執行作業，透過[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 之前使用 Windows 驗證，您必須先執行中所列的步驟[連接到 Oracle 資料庫使用 Windows 驗證](../../adapters-and-accelerators/adapter-oracle-database/connect-to-the-oracle-database-using-windows-authentication.md)。  
  
 如需詳細資訊，請參閱[安全性與 Oracle 資料庫配接器和 BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/security-with-the-oracle-database-adapter-and-biztalk-server.md)。
  
## <a name="security-best-practices-for-consuming-the-oracle-database-adapter-with-programming-solutions"></a>使用 Oracle 資料庫配接器，使用程式設計方案的安全性最佳作法  
  
-   有時候是必要的 Oracle 資料庫中的連線 URI，提供使用者名稱密碼認證不過，如果可能的話，您應該避免這樣。  
  
-   當您使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]，輸入從 Oracle 資料庫使用者名稱密碼認證**安全性** 索引標籤**設定配接器** 對話方塊。  
  
-   在 WCF 通道模型程式設計中，使用**認證**上通道處理站，以設定使用者名稱密碼認證，Oracle 資料庫的屬性。  
  
-   在 WCF 服務模型程式設計中，使用**ClientCredentials**設定 Oracle 資料庫的使用者名稱密碼認證將 WCF 用戶端上的屬性。  
  
-   如果應用程式取用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]會將訊息傳送包含機密的資料庫資訊跨處理序界限，另一個服務或用戶端，確保這些訊息有足夠的安全性措施套用至提供足夠的資料您的環境中的保護。  
  
-   [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]也可讓您使用 Windows 驗證連接到 Oracle 資料庫時，產生中繼資料，並執行作業，透過[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。 之前使用 Windows 驗證，您必須先執行中所列的步驟[連接到 Oracle 資料庫使用 Windows 驗證](../../adapters-and-accelerators/adapter-oracle-database/connect-to-the-oracle-database-using-windows-authentication.md)。  
  
 如需詳細資訊，請參閱[安全使用 Oracle 資料庫配接器程式設計](../../adapters-and-accelerators/adapter-oracle-database/secure-programming-with-the-oracle-database-adapter.md)。  
  
## <a name="security-best-practices-for-hosting-the-oracle-database-adapter-in-iis"></a>裝載在 IIS 中的 Oracle 資料庫配接器的安全性最佳作法  
 裝載[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]中 Microsoft 網際網路資訊服務 (IIS) 做為 Web 服務會公開作業由顯示[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]給 Web 用戶端。 這些作業可能會牽涉到網際網路的交換敏感性資料，所以您應該採取以確保這項資料會儘可能安全的量值。  
  
 [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]提供兩個標準 HTTP 傳輸繫結： **BasicHttpBinding**提供基本的 HTTP 傳輸與任何安全性機制; **WSHttpBinding**支援這兩種傳輸層級和訊息層級安全性機制。  
  
 您可以使用**BasicHttpBinding**透過 HTTPS 連線或使用**WSHttpBinding**來協助保護您的資料。 [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]包含[!INCLUDE[afsvcdevwizlong](../../includes/afsvcdevwizlong-md.md)]以產生 LOB 成品的 WCF 服務。 此精靈只支援使用**BasicHttpBinding**。  
  
 您也可以開發自訂 HTTP 繫結利用您的環境所提供的額外的安全性機制。 如需安全性功能[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]提供，請參閱[保護服務和用戶端](https://msdn.microsoft.com/library/ms734736.aspx)。  
  
## <a name="security-best-practices-for-wcf-diagnostic-tracing-and-message-logging"></a>WCF 的診斷追蹤和訊息記錄的安全性最佳作法  
 [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]支援診斷追蹤和訊息記錄。 透過組態檔或使用 Windows Management Instrumentation (WMI) 設定診斷追蹤和訊息記錄。 根據您設定時，組態選項[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]診斷追蹤或記錄可以發出記錄敏感資訊的訊息檔案，其中它可能有可能會公開給觀察未經授權的使用者。  
  
 請遵循 WCF 文件中提供的建議，以降低潛在的安全性威脅，啟用這些功能。 最少，您應該會看到診斷追蹤和訊息記錄的下列最佳作法：  
  
-   請勿啟用"verbose"或實際執行環境中的 「 資訊 」 追蹤。 這可能會導致效能降低。 不過，您必須啟用 「 警告 」 和 「 錯誤 」 追蹤，在生產環境中。 如果您啟用追蹤，您必須採取適當的安全性措施來保護您的資料。 請參閱 WCF 文件，如需詳細資訊。  
  
-   請確定記錄檔和組態檔已受到存取控制清單 (Acl)。  
  
 下列的警告特別適用於用戶端應用程式之間交換的訊息和[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]:  
  
-   [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]診斷追蹤可以使用記錄交換的訊息標頭 （但不是主體） [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。 因為訊息標頭的訊息動作，這會顯示上叫用之作業[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]用戶端。  
  
-   如果[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]啟用訊息記錄和`logMessagesAtServiceLevel`是`true`，配接器用戶端之間交換的訊息，訊息標頭 （但不是訊息內文） 和[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]記錄。 因為訊息標頭的訊息動作，這會顯示用戶端叫用作業[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。 如果`logEntireMessage`也`true`，將會記錄訊息內文。 這可能會顯示敏感性資料庫資訊。  
  
 如需加強安全性，當您啟用診斷追蹤的詳細資訊，請參閱[安全性考量及實用秘訣，追蹤](https://msdn.microsoft.com/library/ms733053.aspx)。 如需加強安全性，當您啟用訊息記錄的詳細資訊，請參閱[訊息記錄的安全性疑慮](https://msdn.microsoft.com/library/ms730318.aspx)。 
  
## <a name="see-also"></a>另請參閱  
[保護您的 Oracle 資料庫應用程式](../../adapters-and-accelerators/adapter-oracle-database/secure-your-oracle-database-applications.md)