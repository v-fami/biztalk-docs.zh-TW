---
title: "資料表和檢視表包含 Oracle 資料庫中的 LOB 資料的作業 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data type
- binary file
- UpdateLOB
- ReadLOB
- LOB data types
- NCLOB
- large object
- binary large object
- CLOB
- national character large object
- BFILE
- BLOB
- character large object
ms.assetid: 25afd8c7-8ca3-4855-a231-2bec28c9a5cb
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ba5e110af598ac75ca9a8b6e7ebf2e5e8acc7aee
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="operations-on-tables-and-views-that-contain-lob-data-in-oracle-database"></a>資料表和檢視表包含 Oracle 資料庫中的 LOB 資料的作業
[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]提供 Oracle 大型物件 (LOB) 資料類型的支援：  
  
-   二進位大型物件 (BLOB)  
  
-   字元大型物件 (CLOB)  
  
-   國家 （地區） 的字元大型物件 (NCLOB)  
  
-   二進位檔案 (BFILE)。 如需詳細資訊，請參閱[資料表包含 BFILE 資料型別上的作業](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-tables-that-contain-bfile-data-types.md)。  
  
 在 Oracle 資料庫時，LOB 資料類型用來儲存大量資料 (最多 4 GB)。 LOB 類型支援輸入和輸出資料流。  
  
 [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]呈現資料表和檢視表包含 LOB 資料行的下列作業：  
  
-   **ReadLOB**。 ReadLOB 作業會顯示資料表和檢視表包含 BLOB、 CLOB、 NCLOB、 和 BFILE 資料行。 藉由使用 ReadLOB 作業，配接器用戶端可以做為資料流讀取的 LOB 資料行中的值。 這項作業會接受做為參數的 LOB 資料類型資料行名稱和篩選條件字串。 配接器用戶端必須確定篩選字串會提取一個相符的資料列。 如果有一個以上相符的資料列，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]只會傳回第一個 （符合） 的資料列的 LOB 資料行。  
  
    > [!NOTE]
    >  ReadLOB 作業被設計來支援 WCF 服務模型中的 LOB 資料的輸入資料流。 您應該使用資料表的 Select 作業讀取 WCF 通道模型中的 LOB 資料或[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]方案。 如需串流的詳細資訊，請參閱[Oracle 資料庫中的 LOB 資料類型的資料流支援](../../adapters-and-accelerators/adapter-oracle-database/streaming-support-for-lob-data-types-in-oracle-database.md)。  
  
-   **UpdateLOB**。 UpdateLOB 作業會顯示資料表和檢視表包含 BLOB、 CLOB、 和 NCLOB 資料行。 藉由使用 UpdateLOB 作業，配接器用戶端可以更新 LOB 資料行的值。 這項作業會採用的 LOB 資料類型資料行名稱，篩選條件字串，並 base64binary 編碼的資料做為參數。 配接器的用戶端必須確定篩選字串會提取一個相符的資料列。否則[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]XmlReaderParsingException 會擲回。  
  
    > [!NOTE]
    >  UpdateLOB 作業：  
    >   
    >  -   不支援 BFILE 資料型別。 或者，配接器用戶端可以使用更新作業。 如需詳細資訊，請參閱[資料表包含 BFILE 資料型別上的作業](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-tables-that-contain-bfile-data-types.md)。  
    > -   必須執行交易的一部分。 若要確保這點， **UseAmbientTransaction**繫結屬性必須設定為**True**。 如需有關資訊**UseAmbientTransaction**繫結屬性，請參閱[Oracle 資料庫的設定繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md)。  
  
> [!NOTE]
>  ReadLOB UpdateLOB 上進行作業的單一資料表資料列的單一 LOB 資料行。 為了在多個資料列的 LOB 資料行或單一資料列中的多個 LOB 資料行上運作，您必須叫用 ReadLOB 或 UpdateLOB 每個目標資料行內每一個目標資料列。  
  
 如需詳細資訊：  
  
-   叫用 Oracle 資料庫資料表使用 UpdateLOB 作業[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，請參閱[大型物件資料類型使用 BizTalk Server 所使用的資料表上執行的作業](https://msdn.microsoft.com/library/cc185405(v=bts.10).aspx)。 (您應該用來讀取 LOB 資料類型中的資料表的 Select 作業[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。)  
  
-   叫用 Oracle 資料庫資料表使用 WCF 服務模型上的 ReadLOB 和 UpdateLOB 作業，請參閱[使用 WCF 服務模型的大型物件類型之資料表上執行的作業](../../adapters-and-accelerators/adapter-sql/read-or-update-tables-and-views-with-large-data-types-in-sql-with-a-wcf-service.md)。  
  
-   訊息結構和執行 ReadLOB 和 UpdateLOB 作業的 SOAP 動作，請參閱[特殊 LOB 作業的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-special-lob-operations2.md)。  
  
## <a name="see-also"></a>另請參閱  
 [哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185259(v=bts.10).aspx)