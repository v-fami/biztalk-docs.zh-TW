---
title: 最佳作法來保護 SAP 配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- security, best practices
ms.assetid: e60014b5-ce2f-4fd4-be2a-921d5cd81267
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 34d6c56af06bb6b8dc0831c354d494bb62ad5bfa
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2018
ms.locfileid: "22217878"
---
# <a name="best-practices-to-secure-the-sap-adapter"></a>若要保護 SAP 配接器的最佳作法
本章節提供更完整地保護機密資料，當您使用或開發使用的應用程式時，應該遵循的最佳作法[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]。  
  
## <a name="security-best-practices-for-the-connection-between-the-sap-adapter-and-the-sap-system"></a>SAP 配接器與 SAP 系統之間的連線的安全性最佳作法  
  
-   您必須確定適當的配接器與 SAP 系統之間交換資料的安全性等級。 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]支援 SAP 安全網路通訊 (SNC)。 您可以啟用 SNC，或提供替代機制，可協助配接器與 SAP 系統之間的通訊安全。  
  
-   請提供使用者名稱密碼認證的連線 URI 中的 SAP 系統。 請參閱下列章節，以另一種方法提供的認證來[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
-   請確認只有您想要收到 SAP 成品 （Rfc、 Idoc 和 tRFCs） 從 SAP 程式 ID 的接聽程式可以存取該程式識別碼。 這是因為任何具有接聽程式的存取權的程式識別碼可以接收成品從該程式識別碼。  
  
-   請注意，如果多個接聽程式同時使用 SAP 程式 ID，SAP 會隨機選擇每個外寄的成品 （RFC、 IDOC 或 tRFC） 接聽程式。  
  
 如需詳細資訊，請參閱[SAP 系統與配接器之間的安全性](../../adapters-and-accelerators/adapter-sap/security-between-the-sap-system-and-the-adapter.md)。
  
## <a name="security-best-practices-for-consuming-the-sap-adapter-with-biztalk-server"></a>使用 BizTalk Server 與 SAP 配接器的安全性最佳作法  
  
-   請提供使用者名稱密碼認證的連線 URI 中的 SAP 系統。  
  
-   當您使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，輸入從 SAP 系統的使用者名稱密碼認證**安全性** 索引標籤**設定配接器** 對話方塊。  
  
-   當您設定的 BizTalk Wcf-custom 配接器[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]傳送埠，輸入使用者名稱密碼認證從 SAP 系統**認證** 索引標籤**設定 WCF 自訂傳輸**  對話方塊。  
  
-   當您設定的 BizTalk Wcf-custom 配接器[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]上接收位置，輸入使用者名稱密碼認證從 SAP 系統**其他** 索引標籤**設定 WCF 自訂傳輸**  對話方塊。  
  
 如需詳細資訊，請參閱[安全性與 SAP 配接器和 BizTalk Server](../../adapters-and-accelerators/adapter-sap/security-with-the-sap-adapter-and-biztalk-server.md)。
  
## <a name="security-best-practices-for-consuming-the-sap-adapter-with-programming-solutions"></a>使用 SAP 配接器使用程式設計方案的安全性最佳作法  
  
-   有時候是必要的 SAP 系統連接 URI，提供使用者名稱密碼認證不過，如果可能的話，您應該避免這樣。  
  
-   當您使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]，輸入從 SAP 系統的使用者名稱密碼認證**安全性** 索引標籤**設定配接器** 對話方塊。  
  
-   在 WCF 通道模型程式設計中，使用**認證**設定 SAP 系統的使用者名稱密碼認證的通道處理站上的屬性。  
  
-   在 WCF 服務模型程式設計中，使用**ClientCredentials** WCF 用戶端設定的使用者名稱密碼認證的 SAP 系統上的屬性。  
  
-   如果應用程式取用[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]會將訊息傳送包含機密的資料庫資訊跨處理序界限，另一個服務或用戶端，確保這些訊息有足夠的安全性措施套用至提供足夠的資料您的環境中的保護。  
  
 如需詳細資訊，請參閱[SAP 配接器使用的安全程式設計](../../adapters-and-accelerators/adapter-sap/secure-programming-with-the-sap-adapter.md)。  
  
## <a name="security-best-practices-for-hosting-the-sap-adapter-in-iis"></a>裝載在 IIS 中的 SAP 配接器的安全性最佳作法  
  
-   裝載[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]中 Microsoft 網際網路資訊服務 (IIS) 做為 Web 服務會公開作業由顯示[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]給 Web 用戶端。 這些作業可能會牽涉到網際網路的交換敏感性資料，所以您應該採取以確保這項資料會儘可能安全的量值。  
  
     [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] 提供兩個標準 HTTP 傳輸繫結： **BasicHttpBinding**提供基本的 HTTP 傳輸與任何安全性機制; **WSHttpBinding**支援這兩種傳輸層級和訊息層級安全性機制。  
  
     您可以使用**BasicHttpBinding**透過 HTTPS 連線或使用**WSHttpBinding**來協助保護您的資料。 [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]包含[!INCLUDE[afsvcdevwizlong](../../includes/afsvcdevwizlong-md.md)]以產生 LOB 成品的 WCF 服務。 此精靈只支援使用**BasicHttpBinding**。  
  
     您也可以開發自訂 HTTP 繫結利用您的環境所提供的額外的安全性機制。 如需安全性功能[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]提供，請參閱[保護服務和用戶端](https://msdn.microsoft.com/library/ms734736.aspx)。 
  
## <a name="security-best-practices-for-wcf-diagnostic-tracing-and-message-logging"></a>WCF 的診斷追蹤和訊息記錄的安全性最佳作法  
 [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] 支援診斷追蹤和訊息記錄。 透過組態檔或使用 Windows Management Instrumentation (WMI) 設定診斷追蹤和訊息記錄。 根據您設定時，組態選項[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]診斷追蹤或記錄可以發出記錄敏感資訊的訊息檔案，其中它可能有可能會公開給觀察未經授權的使用者。  
  
 請遵循 WCF 文件中提供的建議，以降低潛在的安全性威脅，啟用這些功能。 最少，您應該會看到診斷追蹤和訊息記錄的下列最佳作法：  
  
-   請勿啟用"verbose"或實際執行環境中的 「 資訊 」 追蹤。 這可能會導致效能降低。 不過，您必須啟用 「 警告 」 和 「 錯誤 」 追蹤，在生產環境中。 如果您啟用追蹤，您必須採取適當的安全性措施來保護您的資料。 請參閱 WCF 文件，如需詳細資訊。  
  
-   請確定記錄檔和組態檔已受到存取控制清單 (Acl)。  
  
 下列的警告特別適用於用戶端應用程式之間交換的訊息和[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]:  
  
-   [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] 診斷追蹤可以使用記錄交換的訊息標頭 （但不是主體） [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。 因為訊息標頭的訊息動作，這會顯示上叫用之作業[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]用戶端。  
  
-   如果[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]啟用訊息記錄和`logMessagesAtServiceLevel`是`true`，配接器用戶端之間交換的訊息，訊息標頭 （但不是訊息內文） 和[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]記錄。 因為訊息標頭的訊息動作，這會顯示用戶端叫用作業[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。 如果`logEntireMessage`也`true`，將會記錄訊息內文。 這可能會顯示敏感性資料庫資訊。  
  
     如需加強安全性，當您啟用診斷追蹤的詳細資訊，請參閱[安全性考量及實用秘訣，追蹤](https://msdn.microsoft.com/library/ms733053.aspx)。 如需加強安全性，當您啟用訊息記錄的詳細資訊，請參閱[訊息記錄的安全性疑慮](https://msdn.microsoft.com/library/ms730318.aspx)。  
  
## <a name="see-also"></a>另請參閱  
[保護您的 SAP 應用程式](../../adapters-and-accelerators/adapter-sap/secure-your-sap-applications.md)   