---
title: 資料表和檢視表包含 Oracle 資料庫中的 LOB 資料的作業 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
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
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a35be7008c47e46ca65962d113c4604c1cfad42b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36984295"
---
# <a name="operations-on-tables-and-views-that-contain-lob-data-in-oracle-database"></a>資料表和檢視表包含 Oracle 資料庫中的 LOB 資料的作業
[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]提供 Oracle 的大型物件 (LOB) 資料類型的支援：  
  
- 二進位大型物件 (BLOB)  
  
- 字元大型物件 (CLOB)  
  
- 國家字元大型物件 (NCLOB)  
  
- 二進位檔案 (BFILE)。 如需詳細資訊，請參閱 <<c0> [ 資料表包含 BFILE 資料類型的作業](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-tables-that-contain-bfile-data-types.md)。  
  
  在 Oracle 資料庫時，LOB 資料類型用來儲存大量資料 (最多 4 GB)。 LOB 類型支援輸入和輸出資料流。  
  
  [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]呈現資料表和包含 LOB 資料行的檢視執行下列作業：  
  
- **ReadLOB**。 ReadLOB 作業會顯示資料表和檢視表包含 BLOB、 CLOB、 NCLOB、 和 BFILE 資料行。 藉由使用 ReadLOB 作業，配接器用戶端可以做為資料流讀取的 LOB 資料行中的值。 這項作業接受 LOB 資料類型資料行名稱和篩選條件字串，做為參數。 配接器用戶端必須確定篩選條件字串擷取一個相符的資料列。 如果有多個相符的資料列，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]只會傳回第一個 （符合） 的資料列的 LOB 資料行。  
  
  > [!NOTE]
  >  ReadLOB 作業被設計來支援 WCF 服務模型中的 LOB 資料的輸入資料流。 您應該使用資料表的選取作業來讀取 WCF 通道模型中的 LOB 資料或[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]解決方案。 如需串流的詳細資訊，請參閱 < [Oracle 資料庫中的 LOB 資料類型的資料流支援](../../adapters-and-accelerators/adapter-oracle-database/streaming-support-for-lob-data-types-in-oracle-database.md)。  
  
- **UpdateLOB**。 UpdateLOB 作業會顯示資料表和檢視表包含 BLOB、 CLOB、 和 NCLOB 資料行。 藉由使用 UpdateLOB 作業，配接器用戶端可以更新 LOB 資料行的值。 此作業需要的 LOB 資料類型資料行名稱，篩選條件字串，並 base64binary 編碼資料做為參數。 配接器用戶端必須確定篩選條件字串擷取一個相符的資料列;否則[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]XmlReaderParsingException 會擲回。  
  
  > [!NOTE]
  >  UpdateLOB 作業：  
  > 
  > - 不支援 BFILE 資料型別。 配接器用戶端，或者可以使用更新作業。 如需詳細資訊，請參閱 <<c0> [ 資料表包含 BFILE 資料類型的作業](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-tables-that-contain-bfile-data-types.md)。  
  >   -   必須被執行交易的一部分。 為了確保功效， **UseAmbientTransaction**繫結屬性必須設定為 **，則為 True**。 如需**UseAmbientTransaction**繫結屬性，請參閱[Oracle 資料庫設定的繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md)。  
  
> [!NOTE]
>  ReadLOB 和 UpdateLOB 對單一資料表資料列中的單一 LOB 資料行。 若要在多個資料列的 LOB 資料行上，或在單一資料列中的多個 LOB 資料行上操作，您必須叫用 ReadLOB 或 UpdateLOB 每個目標資料行中每個目標資料列。  
  
 如需詳細資訊：  
  
- 叫用 Oracle 資料庫資料表使用 UpdateLOB 作業[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，請參閱 <<c2> [ 大型物件資料類型使用 BizTalk Server 所使用的資料表上執行的作業](https://msdn.microsoft.com/library/cc185405(v=bts.10).aspx)。 (您應該使用資料表的選取作業來讀取在 LOB 資料型別[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。)  
  
- 叫用 ReadLOB 和 UpdateLOB 使用 WCF 服務模型的 Oracle 資料庫資料表上的作業，請參閱[與使用 WCF 服務模型的大型物件類型的資料表上執行的作業](../../adapters-and-accelerators/adapter-sql/read-or-update-tables-and-views-with-large-data-types-in-sql-with-a-wcf-service.md)。  
  
- 訊息結構和執行 ReadLOB 和 UpdateLOB 作業的 SOAP 動作，請參閱[特殊 LOB 作業的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-special-lob-operations2.md)。  
  
## <a name="see-also"></a>另請參閱  
 [哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185259(v=bts.10).aspx)