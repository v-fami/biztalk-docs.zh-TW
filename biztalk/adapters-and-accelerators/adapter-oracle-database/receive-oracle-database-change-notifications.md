---
title: 接收 Oracle 資料庫變更通知 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3ffabf27-7223-4473-b33e-af6f2990cb96
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bd12434ab94d99dc7f002f1997d92f3ae5553981
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36989687"
---
# <a name="receive-oracle-database-change-notifications"></a>接收 Oracle 資料庫變更通知
[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]支援 ODP.NET 資料庫變更通知功能。 使用這項功能，配接器用戶端可以登錄的 SELECT 陳述式以通知查詢資料庫，而資料庫在配接器用戶端，並在結果集的 SELECT 陳述式變更時，會將傳送通知。 配接器使用 OracleDependency 類別中實作資料庫變更通知。 如需 ODP.NET 和 OracleDependency 類別中的資料庫變更的支援功能的詳細資訊，請參閱[ http://go.microsoft.com/fwlink/?LinkId=124801 ](http://go.microsoft.com/fwlink/?LinkId=124801)。  

 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]公開 （expose) 的輸入的作業通知，以支援資料庫變更通知。 不過，資料庫變更通知，以使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，您必須確認下列：  

- 連接到 Oracle 資料庫與基礎的 Oracle 資料庫版本 10.2 或更新版本。 10.2 之前的 oracle 資料庫版本不支援通知。  

- 已建立通知註冊變更通知權限的使用者身分連接到 Oracle 資料庫。 若要變更通知的權限授與使用者，以系統管理權限的使用者身分連接到 Oracle 資料庫並在 SQL 提示字元執行下列命令：  

  ```  
  grant change notification to <user name>  
  ```  

- 決定可供 ODP.NET 從 Oracle 資料庫接收資料庫變更通知的 TCP 通訊埠。 加入 Windows 防火牆例外清單中的 TCP 連接埠。 如需如何將 Windows 防火牆例外清單中的連接埠的指示，請參閱 < [ http://go.microsoft.com/fwlink/?LinkID=196959 ](http://go.microsoft.com/fwlink/?LinkID=196959)。 您必須提供相同的 TCP 連接埠號碼，如**NotificationPort**繫結屬性。 如需有關繫結屬性的詳細資訊，請參閱[使用繫結屬性](https://msdn.microsoft.com/library/dd788467.aspx)。  

  一般的資料庫變更通知使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]牽涉到下列：  

1.  配接器用戶端必須指定`Notification`中輸入作業**InboundOperationType**繫結屬性。 這個繫結屬性的預設值輪詢。  

2.  配接器用戶端必須指定 SQL SELECT 陳述式中的資料庫變更通知註冊**NotificationStatement**繫結屬性。 從 Oracle 資料庫視為，並在結果集為指定的 SQL 陳述式變更時，配接器用戶端會取得通知。  

3.  配接器用戶端必須指定是否配接器傳送通知給配接器用戶端，以啟動接聽程式**NotifyOnListenerStart**繫結屬性。  

4.  通知會傳送至配接器用戶端，做為並結果集的 SELECT 陳述式中指定**NotificationStatement**繫結屬性變更。  

> [!CAUTION]
>  針對在網路中斷期間在 Oracle 資料庫上所做的變更，將通知 Oracle 資料庫與配接器用戶端之間的網路中斷時，將不傳送給配接器用戶端，之後。 因此，您必須使用輪詢作業，而非通知作業的重要案例。  

## <a name="differences-between-notification-and-polling"></a>告知和輪詢之間的差異  
 告知和輪詢是這兩個輸入的作業，而且配接器用戶端告知 Oracle 資料庫中的資料變更，但下表說明兩者之間的一些差異。 下列差異將協助您決定的作業，視您的需求而定：  


|                                                                                                                              通知                                                                                                                               |                                                                                                                                                                                                                                                      輪詢                                                                                                                                                                                                                                                      |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                                                                               只支援 Oracle 資料庫版本 10.2 和更新版本通知。                                                                                               |                                                                                                                                                                          支援的所有 Oracle 資料庫版本都支援輪詢[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。                                                                                                                                                                           |
|                                                                                                          資料變更通知是一律在瞬間完成。                                                                                                          | 您可以設定輪詢間隔，以檢查適用於定期輪詢資料，或立即一樣，當有可用的資料。 **提示：** 輪詢可讓您更佳的輸送量的資料變更會持續發生，並不想為每項變更並發生時收到通知。 相反地，您可以指定之後，您想要的上次變更通知，因為發生錯誤的所有變更的通知的輪詢間隔。 |
| 通知是由 Oracle 資料庫啟動。 只在配接器發出的通知陳述式會指示要起始通知，萬一沒有陳述式的結果集變更的資料庫。 通知是 Oracle 資料庫的功能。 |                                                                                                                                         輪詢配接器所起始。 若要驗證是否可供輪詢，資料，並藉由執行輪詢陳述式，如果某些資料已可供輪詢起始輪詢 SQL 陳述式執行配接器。                                                                                                                                         |
|                                                                                             您可以使用 notification 陳述式只讀取 Oracle 資料庫中的資料。                                                                                             |                                                                                                                                                                                                                 您可以使用輪詢陳述式來讀取或更新的 Oracle 資料庫中的資料。                                                                                                                                                                                                                  |
|                                                                                   通知只會通知的類型變更的資料，例如 Insert、 Update 和 Delete。                                                                                    |                                                                                                                                                                                                                            輪詢會告知您已變更的實際資料。                                                                                                                                                                                                                            |

 如需詳細資訊：  

- 繫結屬性與通知作業，請參閱[使用繫結屬性](https://msdn.microsoft.com/library/dd788467.aspx)。  

- 如何使用中的通知作業[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，請參閱 <<c2> [ 接收 Oracle 資料庫變更通知使用 BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/receive-oracle-database-change-notifications-using-biztalk-server.md)。  

## <a name="see-also"></a>另請參閱  
 [哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)