---
title: BizTalk Adapter for Oracle 資料庫的限制 |Microsoft Docs
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
ms.openlocfilehash: 8138449cf3af067c9a76848f203c7e1809f6adbc
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36986607"
---
# <a name="limitations-of-biztalk-adapter-for-oracle-database"></a>BizTalk Adapter for Oracle 資料庫的限制
## <a name="general"></a>一般  
 下列已知限制[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]:  
  
- 限制某些例外狀況，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]相容於舊版的配接器。 自上次發行後發生的變更清單，請參閱 < [BizTalk Adapter for Oracle 資料庫中的重要功能](../../adapters-and-accelerators/adapter-oracle-database/key-features-in-biztalk-adapter-for-oracle-database.md)。  
  
- [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]不支援的 XML 型別。  
  
- SQLEXECUTE 作業不會傳回值的 OUT 或 IN 出程序、 函式，或封裝的參數。 基於這個理由，您必須叫用程序、 函數和封裝所使用的專用的作業，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]公開 （expose) 這些 Oracle 成品。  
  
- 從 使用 proxy 進行程式設計，Oracle 資料庫擷取資料時[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]不會還原序列化 XML 訊息，其超過 65536 的節點。 請確定回應訊息含有節點小於或等於為 65536。 您可以修改您的應用程式的 app.config 檔，以解決這項限制。 如需相關指示，請參閱 <<c0> [ 疑難排解操作問題的 Oracle 資料庫配接器](../../adapters-and-accelerators/adapter-oracle-database/troubleshoot-operational-issues-with-the-oracle-database-adapter.md)。  
  
- [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]會採用輸入字串，並建構然後配接器所執行的 SQL 命令。 不過，輸入的字串可能包含其他的 SQL 命令，也會執行，而且可能會中斷作業合約。  
  
   假設其中配接器會提供預存程序輸入的 REF CURSOR。 在這類案例中，配接器用戶端必須提供的命令，在執行時，取得 REF CURSOR。 配接器接著會傳遞 REF 資料指標預存程序。 不過，如果取得 REF CURSOR 的命令會執行一些額外的修改資料庫，執行預存程序的作業合約會中斷。  
  
- [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]支援巢狀只有最多兩個層級的 UDT。  
  
- 使用與介面卡時[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，如果您的認證，在 WCF 自訂傳送連接埠不正確，不會處理要求訊息。 指定正確的認證之後，將訊息傳送至 Oracle 資料庫，並在收到回應。 不過，回應訊息不適用於輸出連接埠。 在此情況下，您可能需要重新啟動主控件執行個體。  
  
- [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]不支援複雜類型 （例如記錄類型、 資料表類型、 UDT 和 VARRAY） 內的 BFILE 資料型別。  
  
- [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]不支援具有循環參考的使用者定義型別 (Udt)。  
  
- [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]執行不支援包含的欄位的記錄類型的記錄類型的 PL/SQL 資料表。  
  
- [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]不會啟用用戶端設定為 NULL 的 VARRAY 中的第一個元素的值。  
  
- PL/SQL 資料表，除了[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]不支援封裝內定義的 Udt。  
  
## <a name="limitations-due-to-odpnet"></a>由於 ODP.NET 的限制  
 下列已知限制[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]由於 ODP.NET 的限制：  
  
- 採用十進位值的 Oracle 資料類型，ODP.NET 不會擲回例外狀況如果輸入的值包含字母字元。 因為[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]使用 ODP.NET 來與 Oracle 資料庫時，配接器也不會擲回例外狀況時傳遞字母字元。 例如：  
  
  -   將插入作業的值"54r 」 傳遞不會擲回例外狀況;而被插入值"54"。  
  
  -   傳遞的值"r54 」 插入作業不會擲回例外狀況;而被插入值"0"。  
  
- 由於 ODP.NET 的限制，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]不支援使用多載使用強型別和弱型別 REF CURSOR 的程序。 就內部而言，配接器會將這兩個強型別和弱型別 REF 資料指標視為只是 REF CURSOR。  
  
- [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]不支援未編製索引為數值欄位的 PL/SQL 資料表。  
  
- [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]不支援不包含任何元素的關聯陣列。  
  
- [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]不支援包含當地時間區域屬性 (TimeStampLTZ) 的時間戳記資料類型的 Udt。  
  
- [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]不支援包含 Udt"。" （句號） 在其名稱中。  
  
- [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]不支援包含 BLOB、 CLOB、 和 NCLOB 資料類型為在 OUT 參數的 Udt。  
  
- [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] Nepodporuje Varray 的下列簡單型別的 Varray: BFILE、 IntervalDS、 IntervalYM、 TimeStampLTZ 和 TimeStampTZ。  
  
- 由於關聯陣列的限制，PL/SQL 資料表或包含下列資料類型的任何記錄的 PL/SQL 資料表中不支援[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]:  
  
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
 [了解 BizTalk Adapter for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/understand-the-biztalk-adapter-for-oracle-database.md)