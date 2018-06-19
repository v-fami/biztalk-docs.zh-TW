---
title: 最佳作法來保護在 Siebel 介面卡 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- security best practices, for consuming the Siebel adapter with BizTalk Server
- security best practices, for connection between the Siebel adapter and Siebel system
- best practices, security
- security, best practices
- security best practices, for hosting the Siebel adapter in IIS
- security best practices, for WCF diagnostic tracing and message logging
- security best practices, for consuming the Siebel adapter with programming solutions
ms.assetid: da89fcc5-2705-4198-8df6-64b2c532ef41
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f131bb7f0b1d4c4c0106ae5678864517edda0887
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22218558"
---
# <a name="best-practices-to-secure-the-siebel-adapter"></a>若要保護 Siebel 配接器的最佳作法
本章節提供更完整地保護機密資料，當您使用或開發使用的應用程式時，應該遵循的最佳作法[!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]。  
  
## <a name="security-best-practices-for-the-connection-between-the-siebel-adapter-and-the-siebel-system"></a>在 Siebel 介面卡與 Siebel 系統之間的連線的安全性最佳作法  
  
-   [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] Mscrypto 或 rsa 加密支援的介面卡與 Siebel 系統之間交換的資料。 為了確保隱私權的介面卡與 Siebel 系統之間交換資料，您應該啟用其中一個加密模式。  
  
-   [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]不提供來協助確保資料完整性或進行驗證和授權，它與 Siebel 系統之間交換的資料提供的機制。 您必須提供這種機制，如果您的環境中存在這些考量。  
  
-   請針對 Siebel 系統連接 URI 中提供使用者名稱密碼認證。 請參閱本主題其餘部分提供的認證來替代方法[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。  
  
 如需詳細資訊，請參閱[Siebel 與配接器之間的安全性](../../adapters-and-accelerators/adapter-siebel/security-between-the-siebel-system-and-the-adapter.md)
  
## <a name="security-best-practices-for-consuming-the-siebel-adapter-with-biztalk-server"></a>使用 Siebel 配接器與 BizTalk Server 的安全性最佳作法  
  
-   請針對 Siebel 系統連接 URI 中提供使用者名稱密碼認證。  
  
-   當您使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，輸入從 Siebel 系統的使用者名稱密碼認證**安全性** 索引標籤**設定配接器** 對話方塊。  
  
-   當您設定的 BizTalk Wcf-custom 配接器[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]在傳送埠，輸入使用者名稱密碼認證從 Siebel 系統**認證** 索引標籤**設定 WCF 自訂傳輸**  對話方塊。  
  
-   當您設定的 BizTalk Wcf-custom 配接器[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]上接收位置，輸入使用者名稱密碼認證從 Siebel 系統**其他** 索引標籤**設定 WCF 自訂傳輸**  對話方塊。  
  
 如需詳細資訊，請參閱[Siebel 配接器與 BizTalk Server 安全性](../../adapters-and-accelerators/adapter-siebel/security-with-siebel-adapter-and-biztalk-server.md)
  
## <a name="security-best-practices-for-consuming-the-siebel-adapter-with-programming-solutions"></a>使用 Siebel 配接器使用程式設計方案的安全性最佳作法  
  
-   有時是為了提供使用者名稱密碼認證 Siebel 系統連接 URI，不過，如果可能的話，您應該避免這樣。  
  
-   當您使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]，輸入從 Siebel 系統的使用者名稱密碼認證**安全性** 索引標籤**設定配接器** 對話方塊。  
  
-   在 WCF 通道模型程式設計中，使用**認證**通道處理站，以設定使用者名稱密碼認證，針對 Siebel 系統的屬性。  
  
-   在 WCF 服務模型程式設計中，使用**ClientCredentials** WCF 用戶端設定的使用者名稱密碼認證，針對 Siebel 系統上的屬性。  
  
-   如果應用程式取用[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]會將訊息傳送包含機密的資料庫資訊跨處理序界限，另一個服務或用戶端，確保這些訊息有足夠的安全性措施套用至提供足夠的資料您的環境中的保護。  
  
 如需詳細資訊，請參閱[Siebel 配接器使用的安全程式設計](../../adapters-and-accelerators/adapter-siebel/secure-programming-with-the-siebel-adapter.md) 
  
## <a name="security-best-practices-for-hosting-the-siebel-adapter-in-iis"></a>裝載在 IIS 中的 Siebel 配接器的安全性最佳作法  
  
-   裝載[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]中 Microsoft 網際網路資訊服務 (IIS) 做為 Web 服務會公開作業由顯示[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]給 Web 用戶端。 這些作業可能會牽涉到網際網路的交換敏感性資料，所以您應該採取以確保這項資料會儘可能安全的量值。  
  
     [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]提供兩個標準 HTTP 傳輸繫結： **BasicHttpBinding**提供基本的 HTTP 傳輸與任何安全性機制; **WSHttpBinding**支援這兩種傳輸層級和訊息層級安全性機制。  
  
     您可以使用**BasicHttpBinding**透過 HTTPS 連線或使用**WSHttpBinding**來協助保護您的資料。 [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]包含[!INCLUDE[afsvcdevwizlong](../../includes/afsvcdevwizlong-md.md)]產生 LOB 成品的 WCF 服務。 此精靈只支援使用**BasicHttpBinding**。  
  
     您也可以開發自訂 HTTP 繫結利用您的環境所提供的額外的安全性機制。 如需安全性功能[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]提供，請參閱[保護服務和用戶端](https://msdn.microsoft.com/library/ms734736.aspx)。
  
## <a name="security-best-practices-for-wcf-diagnostic-tracing-and-message-logging"></a>WCF 的診斷追蹤和訊息記錄的安全性最佳作法  
 [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]支援診斷追蹤和訊息記錄。 透過組態檔或使用 Windows Management Instrumentation (WMI) 設定診斷追蹤和訊息記錄。 根據您設定時，組態選項[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]診斷追蹤或記錄可以發出記錄敏感資訊的訊息檔案，其中它可能有可能會公開給觀察未經授權的使用者。  
  
 請遵循 WCF 文件中提供的建議，以降低潛在的安全性威脅，啟用這些功能。 最少，您應該會看到診斷追蹤和訊息記錄的下列最佳作法：  
  
-   請勿啟用"verbose"或實際執行環境中的 「 資訊 」 追蹤。 這可能會導致效能降低。 不過，您必須啟用 「 警告 」 和 「 錯誤 」 追蹤，在生產環境中。 如果您啟用追蹤，您必須採取適當的安全性措施來保護您的資料。 請參閱 WCF 文件，如需詳細資訊。  
  
-   請確定記錄檔和組態檔已受到存取控制清單 (Acl)。  
  
 下列的警告特別適用於用戶端應用程式之間交換的訊息和[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]:  
  
-   [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]診斷追蹤可以使用記錄交換的訊息標頭 （但不是主體） [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。 因為訊息標頭的訊息動作，這會顯示上叫用之作業[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]用戶端。  
  
-   如果[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]啟用訊息記錄和`logMessagesAtServiceLevel`是`true`，配接器用戶端之間交換的訊息，訊息標頭 （但不是訊息內文） 和[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]記錄。 因為訊息標頭的訊息動作，這會顯示用戶端叫用作業[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。 如果`logEntireMessage`也`true`，將會記錄訊息內文。 這可能會顯示敏感性資料庫資訊。  
  
 如需加強安全性，當您啟用診斷追蹤的詳細資訊，請參閱[安全性考量及實用秘訣，追蹤](https://msdn.microsoft.com/library/ms733053.aspx)。 如需加強安全性，當您啟用訊息記錄的詳細資訊，請參閱[訊息記錄的安全性疑慮](https://msdn.microsoft.com/library/ms730318.aspx)。
  
## <a name="see-also"></a>另請參閱  
[保護您的 Siebel 應用程式](../../adapters-and-accelerators/adapter-siebel/secure-your-siebel-applications.md)