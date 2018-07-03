---
title: 最佳作法來保護 SQL 配接器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e32379d7-800a-49b7-a09a-6b3f04a6e5ef
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1a5bb38e1ffd8c40e56b6e581273b8507159268b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37007775"
---
# <a name="best-practices-to-secure-the-sql-adapter"></a>若要保護的 SQL 配接器的最佳作法
您應該完全遵循以更多的最佳作法保護機密資料，當您使用，或開發應用程式，使用[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]。  
  
## <a name="security-best-practices-for-the-connection-between-the-sql-adapter-and-the-sql-server-database"></a>SQL 配接器與 SQL Server 資料庫之間的連線的安全性最佳作法  
  
- [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]不提供支援協助它與 SQL Server 資料庫之間的安全通訊。 您必須提供一個機制，可協助您確保適當的配接器與 SQL Server 資料庫之間交換資料的安全性等級。  
  
- 基於安全性理由，[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]不允許您為 SQL Server 資料庫的連線 URI 中提供使用者名稱密碼認證。 請參閱本主題其餘部分的另一種方法提供的認證進行[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  
  
- [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]也可讓您使用 Windows 驗證連接到 SQL Server 時，產生中繼資料，並執行作業，不論是透過[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]或[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 之前使用 Windows 驗證，您必須為 SQL Server Management Studio 中的使用者加入 Windows 使用者。 如需詳細資訊，請參閱 <<c0> [ 連接到 SQL 配接器搭配使用 Windows 驗證的 SQL Server](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md)。  
  
  如需詳細資訊，請參閱 < [SQL Server 與配接器之間的安全性](../../adapters-and-accelerators/adapter-sql/security-between-the-sql-server-and-the-adapter.md)。
  
## <a name="security-best-practices-for-consuming-the-sql-adapter-with-biztalk-server"></a>使用 SQL 配接器與 BizTalk Server 的安全性最佳作法  
  
- [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]不允許您為 SQL Server 資料庫的連線 URI 中提供使用者名稱密碼認證。  
  
- 當您使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，從 SQL Server 資料庫中輸入使用者名稱密碼認證**安全性**索引標籤**設定配接器** 對話方塊。  
  
- 當您設定的 BizTalk Wcf-custom 配接器[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]傳送埠，輸入從 SQL Server 資料庫使用者名稱密碼認證**認證**索引標籤**Wcf-custom 傳輸屬性** 對話方塊。  
  
- 當您設定的 BizTalk Wcf-custom 配接器[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]在接收位置，輸入從 SQL Server 資料庫使用者名稱密碼認證**其他**索引標籤**Wcf-custom 傳輸屬性** 對話方塊。  
  
- 同時使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]產生中繼資料，設定傳送埠，或設定接收埠時，您也可以使用 Windows 驗證。 之前使用 Windows 驗證，您必須為 SQL Server Management Studio 中的使用者加入 Windows 使用者。 如需詳細資訊，請參閱 <<c0> [ 連接到 SQL 配接器搭配使用 Windows 驗證的 SQL Server](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md)。  
  
  如需詳細資訊，請參閱 < [SQL 配接器與 BizTalk Server 安全性](../../adapters-and-accelerators/adapter-sql/security-with-the-sql-adapter-and-biztalk-server.md)。
  
## <a name="security-best-practices-for-consuming-the-sql-adapter-with-programming-solutions"></a>使用 SQL 配接器程式設計解決方案的安全性最佳作法  
  
- 有時候是必要的 SQL Server 資料庫中的連線 URI，提供使用者名稱密碼認證不過，如果可能的話，您應該避免執行此動作。  
  
- 當您使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]，從 SQL Server 資料庫中輸入使用者名稱密碼認證**安全性**索引標籤**設定配接器** 對話方塊。  
  
- 在 WCF 通道模型程式設計中，使用**認證**屬性上設定 SQL Server 資料庫的使用者名稱密碼認證之通道處理站。  
  
- 在 WCF 服務模型程式設計中，使用**ClientCredentials** WCF 用戶端設定的 SQL Server 資料庫的使用者名稱密碼認證上的屬性。  
  
- 如果應用程式取用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]會將訊息傳送包含機密的資料庫資訊跨處理序界限至另一個服務或用戶端，確保這些訊息有足夠的安全性措施來提供足夠的資料您的環境中的保護。  
  
- 同時使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]或從.NET 應用程式連線到 SQL Server，您也可以使用 Windows 驗證。 之前使用 Windows 驗證，您必須為 SQL Server Management Studio 中的使用者加入 Windows 使用者。 如需詳細資訊，請參閱 <<c0> [ 連接到 SQL 配接器搭配使用 Windows 驗證的 SQL Server](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md)。  
  
  如需詳細資訊，請參閱 <<c0> [ 使用 SQL 配接器安全的程式設計](../../adapters-and-accelerators/adapter-sql/secure-programming-with-the-sql-adapter.md)。 
  
## <a name="security-best-practices-for-hosting-the-sql-adapter-in-iis"></a>裝載在 IIS 中的 SQL 配接器的安全性最佳作法  
 裝載[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]在 Microsoft 網際網路資訊服務 (IIS) 為 Web 服務會公開所呈現的作業[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]給 Web 用戶端。 這些作業可能牽涉到網際網路，交換的敏感性資料，因此您應該採取措施以確保這項資料是盡可能安全。  
  
 [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] 提供兩個標準 HTTP 傳輸繫結： **BasicHttpBinding**不提供任何安全性機制; 中的基本 HTTP 傳輸**WSHttpBinding**支援這兩個傳輸層級和訊息層級安全性機制。  
  
 您可以使用**BasicHttpBinding**透過 HTTPS 連線或使用**WSHttpBinding**來協助保護您的資料。 [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]包含[!INCLUDE[afsvcdevwizlong](../../includes/afsvcdevwizlong-md.md)]產生 LOB 成品的 WCF 服務。 此精靈只支援使用**BasicHttpBinding**。  
  
 您也可以開發自訂的 HTTP 繫結，以利用您的環境提供額外的安全性機制。 如需安全性功能[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]提供，請參閱 < [Securing Services and Clients](https://msdn.microsoft.com/library/ms734736.aspx)。 
  
 當裝載[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]為 Web 服務，Web 開發人員都應當採取措施來防止直接傳遞至 SQL Server 資料庫的使用者所輸入的字串。 比方說，如果網站可讓使用者輸入的值，將會在 SELECT 陳述式中的 WHERE 子句的一部分，以防止加入陳述式中的其他命令應該會掃描輸入的字串。  
  
## <a name="security-best-practices-for-wcf-diagnostic-tracing-and-message-logging"></a>WCF 診斷追蹤和訊息記錄的安全性最佳作法  
 [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] 支援診斷追蹤和訊息記錄。 透過組態檔或使用 Windows Management Instrumentation (WMI) 設定診斷追蹤和訊息記錄。 根據您設定時，組態選項[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]診斷追蹤或訊息記錄可以發出記錄的機密資訊的檔案，其中它可能有可能會公開至觀察未經授權的使用者。  
  
 請依照下列 WCF 文件中所提供的建議，以緩解潛在的安全性威脅，啟用這些功能。 最少，您應該會看到下列診斷追蹤與訊息記錄的最佳作法：  
  
- 請勿啟用"verbose"或生產環境中的 「 資訊 」 追蹤。 這可能會導致效能降低。 不過，您必須啟用 「 警告 」 和在生產環境中的 「 錯誤 」 追蹤。 如果您啟用追蹤時，您必須採取適當的安全性措施，以保護您的資料。 請參閱 WCF 文件，如需詳細資訊。  
  
- 請確定記錄檔和組態檔會受到存取控制清單 (Acl)。  
  
  下列的警告僅適用於用戶端應用程式之間交換的訊息和[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]:  
  
- [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] 診斷追蹤可使用登交換的訊息標頭 （但不是主體） [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。 由於訊息動作是在訊息標頭，這會顯示上叫用之作業[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]用戶端。  
  
- 如果[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]啟用訊息記錄時，`logMessagesAtServiceLevel`是`true`，配接器用戶端之間交換的訊息，訊息標頭 （但沒有訊息內文） 和[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]記錄。 由於訊息動作是在訊息標頭，這會顯示用戶端叫用作業[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。 如果`logEntireMessage`還有`true`，將記錄訊息內文。 這可能會顯示機密的資料庫資訊。  
  
  如需有關如何改善安全性，當您啟用診斷追蹤的詳細資訊，請參閱[安全性考量及實用秘訣，追蹤](https://msdn.microsoft.com/library/ms733053.aspx)。 如需有關如何改善安全性，當您啟用訊息記錄的詳細資訊，請參閱[訊息記錄的安全性疑慮](https://msdn.microsoft.com/library/ms730318.aspx)。
  
## <a name="see-also"></a>另請參閱  
[保護您的 SQL 應用程式](../../adapters-and-accelerators/adapter-sql/secure-your-sql-applications.md)