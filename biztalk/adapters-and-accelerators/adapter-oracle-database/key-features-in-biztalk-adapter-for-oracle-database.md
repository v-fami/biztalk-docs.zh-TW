---
title: Oracle 資料庫的主要 BizTalk 配接器中的功能 |Microsoft Docs
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
ms.openlocfilehash: e63212e0f0c77e020ea4ad1a43639dff09cd7654
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36995687"
---
# <a name="key-features-in-biztalk-adapter-for-oracle-database"></a>BizTalk Adapter for Oracle 資料庫中的主要功能
此區段會列出新功能和已被取代功能[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]。  

  
## <a name="technology-related-features"></a>技術相關功能  
  
|                   功能                    |                                                                                                                                                                                                                                                                                                                                                                                                     註解                                                                                                                                                                                                                                                                                                                                                                                                     |
|----------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 連接到 Oracle 資料庫的新方式 | 除了連線到使用 net 的服務名稱 （如同在舊版配接器），tnsnames.ora 檔案中的 Oracle 資料庫配接器用戶端現在也可以連接到 Oracle 資料庫直接藉由指定連接參數，因此不需要使用 net 服務名稱或 tnsnames.ora 檔案。 不需要連接到 Oracle 資料庫 tnsnames.ora 檔案可讓您很麻煩地手動更新 連接參數 (net service name) 在每一部用戶端電腦上的 tnsnames.ora 檔案中新增或更新中的 Oracle 伺服器時您環境。 如需詳細資訊，請參閱 <<c0> [ 建立 Oracle 資料庫的連接](../../adapters-and-accelerators/adapter-oracle-database/create-a-connection-to-the-oracle-database.md)。 |
|      支援 Windows 驗證      |                                                                                                配接器用戶端可以使用 Windows 驗證來連接到 Oracle 資料庫。 Windows 驗證可讓您判斷 Windows 登入認證，為基礎的使用者的身分識別，並因此可協助您利用內建安全性的 Windows 環境。 如需有關在 Windows 驗證[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，請參閱 <<c2> [ 連接到 Oracle Database Using Windows Authentication](../../adapters-and-accelerators/adapter-oracle-database/connect-to-the-oracle-database-using-windows-authentication.md)。                                                                                                |
  
## <a name="operations-related-features"></a>作業相關的功能 
  
|                                   功能                                    |                                                                                                                                                                                                                                                                                                                                                              註解                                                                                                                                                                                                                                                                                                                                                              |
|------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|         支援在插入作業中指定內嵌值         |                                                    您可以使用**InlineValue**將計算的值插入至資料表或檢視表的 Oracle 資料庫中的插入作業中的屬性。 這是選擇性屬性，而且可供多個記錄插入作業中的所有簡單的資料記錄。 如果您指定這個屬性的值時，它會覆寫的一筆記錄指定的值。 如需有關 InlineValue 屬性的詳細資訊，請參閱[Insert、 Update、 Delete 與 Oracle 資料表和檢視表的選取作業](../../adapters-and-accelerators/adapter-oracle-database/insert-update-delete-and-select-operations-on-oracle-tables-and-views.md)。                                                    |
|                               增強的輪詢                               | [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]現在支援使用預存程序、 函數或封裝的程序或函式會定期輪詢 Oracle 資料庫接收 「 以輪詢為基礎 」 的資料變更訊息。 除了 SELECT 陳述式中，現在您可以指定預存程序、 函數或封裝的程序或函式做為輪詢 Oracle 資料庫定期執行配接器輪詢陳述式。 如需輪詢的詳細資訊，請參閱[接收輪詢為基礎的資料變更訊息的支援](../../adapters-and-accelerators/adapter-oracle-database/support-for-receiving-polling-based-data-changed-messages-in-oracle-database.md)。 |
|                 Oracle 使用者定義型別 (Udt) 的支援                 |                                                                                                                                                                [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]執行的 Oracle 資料庫中的成品的作業包含 Oracle Udt 的支援。 如需 UDT 支援的資訊，請參閱[支援 Oracle 資料庫中的 Oracle User-Defined 類型](../../adapters-and-accelerators/adapter-oracle-database/support-for-oracle-user-defined-types-in-oracle-database.md)。                                                                                                                                                                 |
|                       支援複合作業                       |                                         [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]可讓配接器用戶端執行的 Oracle 資料庫上的複合作業。 複合作業可以包含任意數目的下列作業，並依照任何順序：<br /><br /> -資料表和檢視上的作業。<br />預存程序、 函數和程序或呈現的封裝內的函式做為配接器中的作業。<br /><br /> 如需有關複合作業的詳細資訊，請參閱[複合作業的訊息結構描述](../../adapters-and-accelerators/adapter-sql/message-schemas-for-composite-operations.md)。                                         |
| 執行預存程序不是使用者所擁有的結構描述中的支援 |                           [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]可讓您執行預存程序的結構描述中，即使目前的使用者不是結構描述的擁有者提供使用者對結構描述在 Oracle 中的權限。 不過，如果預存程序會使用記錄類型，它們必須定義相同的結構描述與預存程序。 如需執行預存程序，使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，請參閱 <<c2> [ 函式和預存程序作業](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-functions-and-stored-procedures1.md)。                            |
|                  資料庫變更通知的支援                   |                                                                                                    配接器用戶端可以從觸發的 SELECT 陳述式為基礎的 Oracle 資料庫接收資料庫變更通知。 Oracle 資料庫與配接器用戶端，並在結果集的 SELECT 陳述式變更時，會傳送通知。 如需有關資料庫變更通知的詳細資訊，請參閱 <<c0> [ 接收資料庫變更通知的考量](../../adapters-and-accelerators/adapter-oracle-database/before-you-receive-database-change-notifications-using-the-oracle-db-adapter.md)。                                                                                                    |
|                             服務的同義字支援                             |                                                                                                                                       配接器用戶端可以執行作業的資料表、 檢視、 預存程序、 函數和封裝所建立的同義字。 如需有關同義字，以及如何使用資訊[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]為了執行在同義字上的作業，請參閱[對 Oracle 資料庫中的同義字的作業](../../adapters-and-accelerators/adapter-oracle-database/operations-on-synonyms-in-oracle-database.md)。                                                                                                                                        |
|            布林值參數的 PL/SQL 資料表類型的支援             |                                                                                                                                                                                                                                                                                                 配接器用戶端可以執行預存程序和函式，包含布林值參數和類型的 PL/SQL 資料表中的作業。                                                                                                                                                                                                                                                                                                  |
  
### <a name="other-features"></a>其他功能  
  
|                    功能                     |                                                                                                                                                                                                                                                                                                                                                                                                                                                                           註解                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 在 BizTalk Server 中使用配接器的新方式 | [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]可用於 BizTalk 做為 WCF 自訂連接埠或 Wcf-oracledb 連接埠。 如果您想要使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]透過 WCF 自訂連接埠，您不需要將 WCF 自訂連接埠新增至 BizTalk Server 管理主控台，因為 WCF 自訂連接埠，會依預設加入至 BizTalk Server 管理主控台。 不過，如果您想要使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]透過 Wcf-oracledb 連接埠，您必須先新增 Wcf-oracledb 配接器至 BizTalk Server 管理主控台。 如需詳細資訊，請參閱 <<c0> [ 將 Oracle 資料庫配接器新增至 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-oracle-database/adding-the-oracle-database-adapter-to-biztalk-server-administration-console.md)。 |
  
## <a name="deprecated-features-in-the-oracle-adapter"></a>在 Oracle 配接器已被取代的功能  
 下表列出的目前版本中已被取代的功能[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。  
  
|功能|註解|  
|-------------|-------------|  
|繫結屬性|**PollingRetryCount**， **TransactionIsolationLevel**，並**LongDataTypeColumnSize**繫結屬性已被取代。 <br/><br/>**請注意**若要設定的輸入操作的交易隔離等級，您必須設定適當的值加在設定接收埠的服務行為。 如需有關如何設定交易隔離等級的指示，請參閱 <<c0> [ 設定交易隔離等級和交易等待時間](../../adapters-and-accelerators/adapter-oracle-ebs/configure-transaction-isolation-level-and-transaction-timeout-with-oracle-ebs.md)。|  
  
## <a name="changes-to-note"></a>要注意的變更

### <a name="general"></a>一般  
* 類型在 OUT REF CURSOR 參數

    -   不會變更預存程序的 REF CURSOR 值時，輸出的值是輸入 REF 資料指標中的值相同。  
  
    -   REF CURSOR 中的輸入和輸出資料是類型的相同。  
  
* "Nil"屬性的不正確的行為： 所有的簡單資料型別，如果您設定的值為"true"，nil 屬性和欄位或參數的值不存在然後 Oracle 資料庫配接器不正確地將傳遞指定的值，而不是 NULL。 因應措施是，如果您想要傳遞 NULL 值的欄位或參數，您必須確定，會指定任何欄位或參數的值。 例如，傳遞 NULL 值的欄位稱為"name":  
  
  ```  
  <name xsi:nil="true"/>  
  ```  
* Real、 Float 和長時間資料類型和額外零 (0) 中，選取作業的結果集的值的結尾不會被截斷。 此外，一律選取作業的結果集傳回精確度 8 真實、 Float 和時間資料類型的值。  
  
* 處理的記錄類型的資料： 傳遞的值的值取決於這些節點**SkipNilNodes**繫結屬性。 如需有關這個繫結屬性的詳細資訊，請參閱[Oracle 資料庫設定的繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md)。 
  
* 傳出作業： 沒有值，指定在輸入 XML 檔中的參數會傳送任何值。 如果預存程序中指定的預設值，則 Oracle 資料庫會使用該值，因為配接器已不傳送的任何值。 如果為 NULL 值都需要傳送，使用者必須輸入的 XML 檔案中指定 NULL 節點設定為"true"。"nil"屬性的值  
  
* 支援命令逾時。  
  
* UpdateLOB 作業必須執行交易的一部分。 若要確保的值，這**UseAmbientTransaction**繫結屬性必須設定為 **，則為 True**。  
  
### <a name="biztalk-scenario"></a>BizTalk 案例  
  
- 傳出作業： 如果**UseAmbientTransaction**繫結屬性是"True"的 Oracle 資料庫上的作業和 BizTalk messagebox 資料庫會在相同的分散式交易內執行。 如需中的交易[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，請參閱 < [Oracle 資料庫配接器處理交易](../../adapters-and-accelerators/adapter-oracle-database/handle-transactions-with-the-oracle-database-adapter.md)。  
  
- 輸入作業： 您無法使用要求-回應接收埠中的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]輸入作業使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。 只有單向接收連接埠可用。  
  
### <a name="other-scenarios"></a>其他案例  
  
- 傳出作業： 配接器，不會啟動交易。 如果使用者想要在相同交易中插入多個資料列，是使用者的責任，若要執行 System.Transactions 交易範圍內的作業。 使用者也需要設定的值**UseAmbientTransaction**屬性設 **，則為 True**。 如需中的交易[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，請參閱 < [Oracle 資料庫配接器處理交易](../../adapters-and-accelerators/adapter-oracle-database/handle-transactions-with-the-oracle-database-adapter.md)。  
  
- 傳出作業： Sll 相同 IRequestChannel/proxy 物件上執行的作業可能不會執行相同的實體連接到 Oracle 資料庫上。  
  
- WCF 通道模型：[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]期間使用 WCF 通道模型不支援 IReplyChannel。 不過，您可以使用 IInputChannel 執行輸入的作業。 此外，關於交易，此配接器依賴 WCF 發送器起始交易執行輪詢陳述式，並後輪詢陳述式，針對 Oracle 資料庫。 交易隔離等級和 WCF 發送器起始交易的時間超出可以控制在 ServiceBehavior 中設定適當的值。  
  
## <a name="see-also"></a>另請參閱  
 [了解 Biztalk Adapter for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/understand-the-biztalk-adapter-for-oracle-database.md)