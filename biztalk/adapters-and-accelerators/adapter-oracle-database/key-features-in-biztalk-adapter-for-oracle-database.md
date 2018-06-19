---
title: Oracle 資料庫的主要 BizTalk 配接器中的功能 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- features, operations-related
- adapters, new and deprecated features
- features, technology-related
- features, new and deprecated
- features, performance-related
- features, metadata-related
ms.assetid: 7e79714c-1472-4721-a693-5be2a9a0cd1f
caps.latest.revision: 26
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c4277c5d0691d44bdae26b6b395a91d2ecb8f093
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22215982"
---
# <a name="key-features-in-biztalk-adapter-for-oracle-database"></a>BizTalk Adapter for Oracle 資料庫中的重要功能
此區段會列出中的新和已被取代功能[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]。  

  
## <a name="technology-related-features"></a>技術相關功能  
  
|功能|註解|  
|-------------|-------------|  
|新的方式來連接到 Oracle 資料庫|除了連線到在 tnsnames.ora 檔案 （如同在舊版的配接器），使用 net 服務名稱與 Oracle 資料庫配接器用戶端現在也可以連接到 Oracle 資料庫直接藉由指定連接參數，因此因而不須使用 net 服務名稱或 tnsnames.ora 檔案。 不需要連接到 Oracle 資料庫 tnsnames.ora 檔案時，儲存您從之類的手動更新 連接參數 (net service name) tnsnames.ora 檔案，每個用戶端電腦上加入或更新中的 Oracle 伺服器程式環境。 如需詳細資訊，請參閱[建立連接到 Oracle 資料庫](../../adapters-and-accelerators/adapter-oracle-database/create-a-connection-to-the-oracle-database.md)。|  
|支援 Windows 驗證|配接器用戶端可以使用 Windows 驗證來連接到 Oracle 資料庫。 Windows 驗證可讓您判斷使用者的身分識別為基礎的 Windows 登入認證，並因此可協助您利用內建安全性的 Windows 環境。 如需有關在 Windows 驗證[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，請參閱[連接到 Oracle 資料庫使用 Windows 驗證](../../adapters-and-accelerators/adapter-oracle-database/connect-to-the-oracle-database-using-windows-authentication.md)。|  
  
## <a name="operations-related-features"></a>與作業相關的功能 
  
|功能|註解|  
|-------------|-------------|  
|支援用於插入作業中指定內嵌的值|您可以使用**InlineValue**將計算的值插入資料表或檢視表的 Oracle 資料庫中的插入作業中的屬性。 這是選擇性的屬性，可供多個記錄插入作業中所有的簡單資料記錄。 如果您指定這個屬性的值，它會覆寫某筆記錄指定的值。 如需 InlineValue 屬性的詳細資訊，請參閱[Insert、 Update、 Delete 和 Oracle 資料表和檢視表的選取作業](../../adapters-and-accelerators/adapter-oracle-database/insert-update-delete-and-select-operations-on-oracle-tables-and-views.md)。|  
|增強的輪詢|[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]現在支援使用預存程序、 函數或封裝的程序或函式，以定期輪詢 Oracle 資料庫接收 「 輪詢基礎 」 的資料變更的訊息。 除了 SELECT 陳述式中，現在您可以指定預存程序、 函數或封裝的程序或函式與輪詢 Oracle 資料庫執行定期配接器輪詢陳述式。 如需輪詢的詳細資訊，請參閱[支援接收輪詢基礎資料變更的訊息](../../adapters-and-accelerators/adapter-oracle-database/support-for-receiving-polling-based-data-changed-messages-in-oracle-database.md)。|  
|Oracle 使用者定義型別 (Udt) 的支援|[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] Oracle 資料庫中執行作業的成品包含 Oracle Udt 的支援。 如需 UDT 的支援資訊，請參閱[支援 Oracle 資料庫中的 Oracle User-Defined 類型](../../adapters-and-accelerators/adapter-oracle-database/support-for-oracle-user-defined-types-in-oracle-database.md)。|  
|複合作業的支援|[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]可讓配接器用戶端執行的 Oracle 資料庫上的複合作業。 複合作業可以包含任意數目的下列作業，並以任何順序：<br /><br /> 資料表和檢視表上作業。<br />預存程序、 函數和程序或函式，便會顯示封裝內做為配接器中的作業。<br /><br /> 如需複合操作的詳細資訊，請參閱[複合操作的訊息結構描述](../../adapters-and-accelerators/adapter-sql/message-schemas-for-composite-operations.md)。|  
|執行預存程序不是使用者所擁有的結構描述中的支援|[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]可讓您執行預存程序結構描述中，即使目前的使用者不是擁有者的結構描述中，提供使用者對 Oracle 中的結構描述的權限。 不過，如果預存程序會使用記錄類型，它們必須定義相同的結構描述與預存程序。 如需執行預存程序使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，請參閱[函式和預存程序上的作業](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-functions-and-stored-procedures1.md)。|  
|資料庫變更通知的支援|配接器用戶端可以接收來自根據觸發的 SELECT 陳述式的 Oracle 資料庫的資料庫變更通知。 通知會傳送 Oracle 資料庫配接器用戶端，以及當結果集的 SELECT 陳述式變更。 如需資料庫的變更通知的詳細資訊，請參閱[接收資料庫變更通知的考量](../../adapters-and-accelerators/adapter-oracle-database/before-you-receive-database-change-notifications-using-the-oracle-db-adapter.md)。|  
|支援的同義字|配接器用戶端可以執行在針對資料表、 檢視、 預存程序、 函數和封裝建立的同義字上的作業。 如需有關同義字，以及如何使用資訊[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]執行在同義字上的作業，請參閱[Oracle 資料庫內的同義字上的作業](../../adapters-and-accelerators/adapter-oracle-database/operations-on-synonyms-in-oracle-database.md)。|  
|布林值參數的 PL/SQL 資料表類型的支援|配接器用戶端可以執行預存程序和函式包含布林值參數和類型的 PL/SQL 資料表中的作業。|  
  
### <a name="other-features"></a>其他功能  
  
|功能|註解|  
|-------------|-------------|  
|新的方式來使用 BizTalk Server 中的配接器|[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]可用於 BizTalk 作為 WCF 自訂連接埠或 Wcf-oracledb 連接埠。 如果您想要使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]透過 WCF 自訂連接埠，您不需要將 WCF 自訂連接埠新增至 BizTalk Server 管理主控台中，因為 WCF 自訂連接埠，會依預設加入至 BizTalk Server 管理主控台。 不過，如果您想要使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]透過 Wcf-oracledb 連接埠，您必須先新增 Wcf-oracledb 配接器至 BizTalk Server 管理主控台。 如需詳細資訊，請參閱[將 Oracle 資料庫配接器新增至 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-oracle-database/adding-the-oracle-database-adapter-to-biztalk-server-administration-console.md)。|  
  
## <a name="deprecated-features-in-the-oracle-adapter"></a>在 Oracle 配接器已被取代的功能  
 下表列出在目前版本已被取代的功能[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。  
  
|功能|註解|  
|-------------|-------------|  
|繫結屬性|**PollingRetryCount**， **TransactionIsolationLevel**，和**LongDataTypeColumnSize**繫結屬性中已被取代。 <br/><br/>**請注意**若要設定的輸入操作的交易隔離等級，您必須設定適當的值，藉由設定接收埠時新增服務行為。 如需有關如何設定交易隔離等級的指示，請參閱[設定交易隔離等級和交易逾時](../../adapters-and-accelerators/adapter-oracle-ebs/configure-transaction-isolation-level-and-transaction-timeout-with-oracle-ebs.md)。|  
  
## <a name="changes-to-note"></a>請注意的變更

### <a name="general"></a>一般  
* 類型在 OUT REF CURSOR 參數

    -   如果有 REF 資料指標的值，預存程序內不會變更，輸出的值是輸入 REF 資料指標中的值相同。  
  
    -   REF 資料指標中的輸入和輸出資料是類型的相同。  
  
-   "Nil"屬性的不正確的行為： 對於所有的簡單資料類型，如果您設定為"true"，nil 屬性值，且目前的欄位或參數的值然後 Oracle 資料庫配接器不正確地將傳遞指定的值，而不是 NULL。 因應措施是，如果您想要傳遞 NULL 值的欄位或參數，您必須確定會指定任何欄位或參數的值。 例如，傳遞 NULL 值的欄位稱為"name":  
  
    ```  
    <name xsi:nil="true"/>  
    ```  
-   真正、 Float、 長時間資料類型，以及額外的零 (0) 結尾的選取作業的結果集中的值不會被截斷。 此外，一律選取作業的結果集傳回精確度 8 真正、 浮點數，與長時間資料類型值。  
  
-   處理資料的記錄類型： 傳遞給這些節點的值而定的值**SkipNilNodes**繫結屬性。 如需此繫結屬性的詳細資訊，請參閱[Oracle 資料庫的設定繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md)。 
  
-   傳出作業： 沒有值會傳送給沒有值，指定在輸入 XML 檔的參數。 如果預存程序中指定了預設值，將 Oracle 資料庫會使用該值，因為配接器不傳送任何值。 如果需要傳送 NULL 值，使用者需要在輸入 XML 檔案中指定 NULL 節點，藉由設定為"true"。"nil"屬性的值  
  
-   支援的命令逾時。  
  
-   必須執行 UpdateLOB 作業，因為交易的一部分。 若要確保的值，這**UseAmbientTransaction**繫結屬性必須設定為**True**。  
  
### <a name="biztalk-scenario"></a>BizTalk 案例  
  
-   傳出作業： 如果**UseAmbientTransaction**繫結屬性為"True"的 Oracle 資料庫上的作業和 BizTalk messagebox 資料庫會在相同的分散式交易內執行。 如需中的交易[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，請參閱[處理與 Oracle 資料庫配接器的交易](../../adapters-and-accelerators/adapter-oracle-database/handle-transactions-with-the-oracle-database-adapter.md)。  
  
-   輸入 operations： 您無法使用要求-回應接收埠中的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]輸入作業使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。 僅單向接收連接埠可用。  
  
### <a name="other-scenarios"></a>其他案例  
  
-   傳出作業： 配接器不會啟動交易。 如果使用者想要在相同交易中插入多個資料列，則執行 System.Transactions 交易範圍內操作使用者的責任。 使用者也需要設定的值**UseAmbientTransaction**屬性**True**。 如需中的交易[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，請參閱[處理與 Oracle 資料庫配接器的交易](../../adapters-and-accelerators/adapter-oracle-database/handle-transactions-with-the-oracle-database-adapter.md)。  
  
-   傳出作業： Sll 相同 IRequestChannel/proxy 物件上執行的作業可能無法對相同的實體連接到 Oracle 資料庫。  
  
-   WCF 通道模型：[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]期間使用的 WCF 通道模型不支援 IReplyChannel。 不過，您可以使用 IInputChannel 執行輸入的作業。 此外，大致相同的交易，此配接器依賴 WCF 發送器起始交易執行輪詢陳述式，並後輪詢陳述式針對 Oracle 資料庫。 交易隔離等級和 WCF 發送器起始交易的時間超出可以控制在 ServiceBehavior 中設定適當的值。  
  
## <a name="see-also"></a>另請參閱  
 [瞭解 Biztalk Adapter for Oracle 資料庫](../../adapters-and-accelerators/adapter-oracle-database/understand-the-biztalk-adapter-for-oracle-database.md)