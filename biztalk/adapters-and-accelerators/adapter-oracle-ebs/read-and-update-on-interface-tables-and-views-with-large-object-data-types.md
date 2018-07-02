---
title: 在介面資料表、 介面檢視、 資料表和檢視表包含 LOB 資料的作業 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f6e8db6-ba68-4e3f-84b2-1cc31ce89bcb
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4f1336c1d6f5fb6ea7c0b68e4c7670616f141583
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36967687"
---
# <a name="operations-on-interface-tables-interface-views-tables-and-views-that-contain-lob-data"></a>在介面資料表、 介面檢視、 資料表和檢視表包含 LOB 資料的作業
[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]提供 Oracle 的大型物件 (LOB) 資料類型的支援：  
  
- 二進位大型物件 (BLOB)  
  
- 字元大型物件 (CLOB)  
  
- 國家字元大型物件 (NCLOB)  
  
- 二進位檔案 (BFILE)。 如需詳細資訊，請參閱 <<c0> [ 資料表，包含 BFILE 資料型別上的作業](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-tables-that-contain-bfile-data-types.md)。  
  
  在基礎 Oracle 資料庫時，LOB 資料類型用來儲存大量資料，最多為 4 gb (GB)。 BFILE 資料型別，除了 LOB 資料類型會支援輸入和輸出資料流。  

## <a name="operations-for-tables-and-views"></a>資料表和檢視表的作業  
 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]呈現介面資料表、 介面檢視、 資料表和包含 LOB 資料行的檢視執行下列作業：  
  
- **Read_\<LOBColName\>**:`Read_<LOBColName>`作業會顯示介面資料表、 介面檢視、 資料表和檢視表，包含 BLOB、 CLOB、 NCLOB、 和 BFILE 資料行，其中\<LOBColName\>是 BLOB、 CLOB、 NCLOB 或 BFILE 類型的資料行的名稱。 使用 Read_\<LOBColName\>作業中，配接器用戶端可以讀取 LOB 資料行做為資料流中的值。 這項作業會接受做為參數的篩選條件字串。  
  
  > [!NOTE]
  >  `Read_<LOBColName>`作業設計來支援 WCF 服務模型中的 LOB 資料的輸入資料流。 您應該使用資料表的選取作業來讀取 WCF 通道模型中的 LOB 資料或[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]解決方案。  
  
- **Update_\<LOBColName\>**:`Update_<LOBColName>`作業會顯示介面資料表和資料表只可包含 BLOB、 CLOB、 和 NCLOB 資料行，其中\<LOBColName\>的名稱資料行中的輸入 BLOB、 CLOB、 和 NCLOB。 使用 Update_\<LOBColName\>作業中，配接器用戶端可以更新 LOB 資料行中的值。 BLOB 資料類型，此作業需要 base64binary 編碼資料做為參數，而針對 CLOB 和 NCLOB 資料類型，這項作業會採用字串篩選條件做為參數。  
  
  > [!NOTE]
  >  `Update_<LOBColName>`作業：  
  > 
  > - 不支援 BFILE 資料型別。 配接器用戶端，或者可以使用更新作業。 如需詳細資訊，請參閱 <<c0> [ 資料表，包含 BFILE 資料型別上的作業](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-tables-that-contain-bfile-data-types.md)。  
  >   -   不會公開的介面檢視和檢視。  
  >   -   必須被執行交易的一部分。 為了確保功效， **UseAmbientTransaction**繫結屬性必須設定為 **，則為 True**。 如需**UseAmbientTransaction**繫結屬性，請參閱[Rad BizTalk Adapter for Oracle E-business Suite 繫結屬性的相關](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。  
  
> [!IMPORTANT]
>  [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]表面`Read_<LOBColName>`和`Update_<LOBColName>`資料表中每一個 LOB 資料行的作業。 因此，如果資料表 （LOBCol1 和 LOBCol2） 中有兩個 LOB 資料行，您有兩個`Read_<LOBColName>`作業 （Read_LOBCol1 和 Read_LOBCol2） 和兩個`Update_<LOBColName>`作業 （Update_LOBCol1 和 Update_LOBCol2）。  
  
## <a name="more-good-info"></a>良好的詳細資訊  
  
- 叫用`Read_<LOBColName>`並`Update_<LOBColName>`基礎資料庫中使用 Oracle E-business Suite 資料表上的作業[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，請參閱[含有大型資料類型使用 BizTalk Server 的資料表上執行的作業](../../adapters-and-accelerators/adapter-sql/run-operations-on-tables-and-views-with-large-data-types-using-the-sql-adapter.md)。  
  
- 訊息結構和 SOAP 動作，來執行`Read_<LOBColName>`並`Update_<LOBColName>`作業，請參閱[特殊 LOB 作業的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-special-lob-operations1.md)。  
  
## <a name="see-also"></a>另請參閱  
 [哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)