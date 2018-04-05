---
title: Oracle Database 的 BizTalk 配接器的限制 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- adapter, limitations of
ms.assetid: eab4ddea-f986-43c2-82bb-b9fe37961a5b
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cd6cfea523333752c0ee18fefbc6a1848057fe36
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="limitations-of-biztalk-adapter-for-oracle-database"></a>Oracle Database 的 BizTalk 配接器的限制
## <a name="general"></a>一般  
 下列已知限制[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]:  
  
-   限制某些例外狀況，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]與配接器之前的版本相容。 上次發行以來發生的變更清單，請參閱[BizTalk Adapter for Oracle 資料庫中的金鑰功能](../../adapters-and-accelerators/adapter-oracle-database/key-features-in-biztalk-adapter-for-oracle-database.md)。  
  
-   [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]不支援 XML 型別。  
  
-   SQLEXECUTE 作業不會傳回值，代表 OUT 或 IN OUT 參數的程序、 函數或封裝。 基於這個理由，您必須叫用程序、 函數以及封裝使用專用的作業，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]公開 （expose) 這些 Oracle 成品。  
  
-   從使用 proxy 的程式設計、 Oracle 資料庫擷取資料時[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]無法還原序列化 XML 訊息有多個 65536 的節點。 請確定回應訊息具有節點小於或等於為 65536。 您可以修改您的應用程式的 app.config 檔案，以解決這項限制。 如需指示，請參閱[操作 Oracle 資料庫配接器問題的疑難排解](../../adapters-and-accelerators/adapter-oracle-database/troubleshoot-operational-issues-with-the-oracle-database-adapter.md)。  
  
-   [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]會採用輸入字串和建構 SQL 命令，然後執行配接器。 不過，輸入的字串可能包含其他的 SQL 命令，也會執行，而且可能會中斷作業合約。  
  
     假設其中配接器會提供預存程序輸入的 REF CURSOR。 在這種情況下，配接器用戶端必須提供的命令，在執行時，會取得 REF CURSOR。 配接器接著會傳遞 REF 資料指標預存程序。 不過，如果取得 REF CURSOR 的命令會執行一些額外的修改資料庫，執行預存程序的作業合約會中斷。  
  
-   [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]支援巢狀只有最多兩個層級的 UDT。  
  
-   使用與介面卡時[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，如果的認證在 WCF 自訂傳送連接埠不正確，無法處理要求訊息。 指定正確的認證之後，訊息會傳送到 Oracle 資料庫，並收到回應。 不過，回應訊息不適用於輸出通訊埠。 在這種情況下，您可能需要重新啟動主控件執行個體。  
  
-   [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]不支援複雜型別 （例如記錄類型，資料表類型、 UDT，以及 VARRAY） 內 BFILE 資料型別。  
  
-   [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]不支援具有循環參考的使用者定義型別 (Udt)。  
  
-   [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]不支援包含的欄位的記錄是否輸入 PL/SQL 資料表的記錄類型。  
  
-   [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]不會啟用用戶端設定為 NULL 的 VARRAY 中的第一個元素的值。  
  
-   除了 PL/SQL 資料表[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]不支援封裝內定義的 Udt。  
  
## <a name="limitations-due-to-odpnet"></a>由於 ODP.NET 限制  
 下列已知限制[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]基於 ODP.NET 限制：  
  
-   接受十進位值的 Oracle 資料類型，ODP.NET 不會擲回例外狀況如果輸入的值包含字母字元。 因為[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]使用 Oracle 資料庫時，配接器介面 ODP.NET 太不會擲回例外狀況時傳遞字母字元。 例如：  
  
    -   傳遞的值"54r 」 插入作業不會擲回例外狀況。而被插入值"54"。  
  
    -   傳遞的值"r54 」 插入作業不會擲回例外狀況。而被插入值"0"。  
  
-   由於 ODP.NET 的限制，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]不支援使用強型別和弱式類型的 REF CURSOR 的多載程序使用。 就內部而言，配接器會將這兩個強型別和弱型別 REF 資料指標視為只 REF CURSOR。  
  
-   [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]不支援 PL/SQL 資料表未建立索引的數值欄位。  
  
-   [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]不支援不包含任何元素的關聯陣列。  
  
-   [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]不支援包含時間戳記資料類型，以本地時間區域屬性 (TimeStampLTZ) 的 Udt。  
  
-   [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]不支援包含 Udt"。" （句號） 在其名稱中。  
  
-   [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]不支援 Udt，包含 BLOB、 CLOB、 和 NCLOB 資料類型做為 IN OUT 參數。  
  
-   [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]不支援 Varray 的下列簡單型別的 Varray: BFILE、 IntervalDS、 IntervalYM、 TimeStampLTZ 和 TimeStampTZ。  
  
-   由於關聯陣列的限制，PL/SQL 資料表或包含下列資料類型的資料錄的 PL/SQL 資料表中不支援[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]:  
  
    -   BFILE  
  
    -   BLOB  
  
    -   CLOB  
  
    -   IntervalDS  
  
    -   IntervalYM  
  
    -   長整數  
  
    -   NCLOB  
  
    -   RowID  
  
    -   TimeStamp  
  
    -   TimeStampLTZ  
  
    -   TimeStampTZ  
  
## <a name="see-also"></a>另請參閱  
 [瞭解 BizTalk Adapter for Oracle 資料庫](../../adapters-and-accelerators/adapter-oracle-database/understand-the-biztalk-adapter-for-oracle-database.md)