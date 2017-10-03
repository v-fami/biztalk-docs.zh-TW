---
title: "接收 Oracle 資料庫的變更通知 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3ffabf27-7223-4473-b33e-af6f2990cb96
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1d1c33ef7bacf96a152d4b02d0c8c08991f96d64
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="receive-oracle-database-change-notifications"></a>接收 Oracle 資料庫的變更通知
[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]支援 ODP.NET 資料庫變更通知功能。 使用這項功能，配接器用戶端可以註冊的 SELECT 陳述式與通知查詢資料庫，而資料庫將通知傳送給配接器用戶端，並在結果集的 SELECT 陳述式變更時。 配接器使用 OracleDependency 類別中實作的資料庫變更通知。 如需 ODP.NET 和 OracleDependency 類別中的資料庫變更的支援功能的詳細資訊，請參閱[http://go.microsoft.com/fwlink/?LinkId=124801](http://go.microsoft.com/fwlink/?LinkId=124801)。  
  
 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]公開的輸入的作業通知，以支援資料庫的變更通知。 不過，資料庫的變更通知，才能使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，您必須確定下列：  
  
-   連接到 Oracle 資料庫與基底的 Oracle 資料庫版本 10.2 或更新版本。 10.2 之前的 oracle 資料庫版本不支援通知。  
  
-   擁有建立通知登錄的變更通知權限的使用者身分連接到 Oracle 資料庫。 若要變更通知權限授與使用者，具有系統管理權限的使用者身分連接到 Oracle 資料庫並在 SQL 提示字元執行下列命令：  
  
    ```  
    grant change notification to <user name>  
    ```  
  
-   決定可供 ODP.NET 接收從 Oracle 資料庫的資料庫變更通知的 TCP 通訊埠。 加入 Windows 防火牆例外清單中的 TCP 連接埠。 如需如何將連接埠新增至 Windows 防火牆例外清單的指示，請參閱[http://go.microsoft.com/fwlink/?LinkID=196959](http://go.microsoft.com/fwlink/?LinkID=196959)。 您必須提供相同的 TCP 通訊埠編號，如**NotificationPort**繫結屬性。 如需繫結屬性的詳細資訊，請參閱[使用繫結屬性](https://msdn.microsoft.com/library/dd788467.aspx)。  
  
 通知使用一般的資料庫變更[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]牽涉到下列：  
  
1.  配接器用戶端必須指定`Notification`為中的輸入作業**InboundOperationType**繫結屬性。 正在輪詢此繫結屬性的預設值。  
  
2.  配接器用戶端必須指定 SQL SELECT 陳述式資料庫中的變更通知註冊**NotificationStatement**繫結屬性。 從 Oracle 資料庫視為，並在結果集為指定的 SQL 陳述式變更時，配接器用戶端會收到通知。  
  
3.  配接器用戶端必須指定是否配接器傳送通知給配接器用戶端以啟動接聽程式之後儘速**NotifyOnListenerStart**繫結屬性。  
  
4.  通知會傳送至配接器用戶端，做為並結果集的 SELECT 陳述式中指定**NotificationStatement**繫結屬性已變更。  
  
> [!CAUTION]
>  如果沒有 Oracle 資料庫與配接器用戶端之間的網路中斷，通知不會傳送到配接器用戶端網路中斷，這段期間完成的 Oracle 資料庫上的變更之後。 因此，您必須使用輪詢作業，而不是用在關鍵狀況通知操作。  
  
## <a name="differences-between-notification-and-polling"></a>通知輪詢之間的差異  
 雖然告知和輪詢這兩個輸入的作業，然後通知配接器用戶端有關 Oracle 資料庫中的資料變更下, 表將說明兩者之間的一些差異。 下列差異，可協助您決定在針對作業，視您的需求而定：  
  
|通知|輪詢|  
|------------------|-------------|  
|通知是支援僅針對 Oracle 資料庫版本 10.2 和更新版本。|支援的所有 Oracle 資料庫版本都支援輪詢[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。|  
|資料變更通知是一律在瞬間完成。|您可以設定輪詢間隔，以檢查適用於定期輪詢資料，或立即一樣，當有可用的資料。 **提示：**輪詢可讓您更佳的輸送量持續發生資料變更並不想為每項變更，並發生時加以通知。 相反地，您可以指定您要在其後發生是因為最後一個變更通知的所有變更的通知輪詢間隔。|  
|通知是由 Oracle 資料庫啟動。 只在配接器發出的通知陳述式會指示資料庫在陳述式的結果集變更的情況下起始通知。 通知是 Oracle 資料庫的功能。|輪詢配接器所起始。 若要驗證是否資料適用於輪詢，並以起始輪詢執行輪詢陳述式，如果某些資料可用於輪詢 SQL 陳述式執行配接器。|  
|您可以使用通知陳述式只讀取 Oracle 資料庫中的資料。|您可以使用輪詢陳述式來讀取或更新的 Oracle 資料庫中的資料。|  
|通知會告知中插入，例如資料的變更類型的相關更新和刪除。|輪詢會通知您有關已變更的實際資料。|  
  
 如需詳細資訊：  
  
-   繫結屬性與通知作業，請參閱[使用繫結屬性](https://msdn.microsoft.com/library/dd788467.aspx)。  
  
-   如何使用中的通知作業[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，請參閱[接收 Oracle 資料庫變更通知使用 BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/receive-oracle-database-change-notifications-using-biztalk-server.md)。  
  
## <a name="see-also"></a>另請參閱  
 [哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)