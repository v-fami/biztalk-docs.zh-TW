---
title: "介面資料表、 介面檢視、 資料表和檢視表包含 LOB 資料的作業 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f6e8db6-ba68-4e3f-84b2-1cc31ce89bcb
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8a0804aa58174912a29cec9039d55579e4e705a5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="operations-on-interface-tables-interface-views-tables-and-views-that-contain-lob-data"></a>介面資料表、 介面檢視、 資料表和檢視表包含 LOB 資料的作業
[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]提供 Oracle 大型物件 (LOB) 資料類型的支援：  
  
-   二進位大型物件 (BLOB)  
  
-   字元大型物件 (CLOB)  
  
-   國家 （地區） 的字元大型物件 (NCLOB)  
  
-   二進位檔案 (BFILE)。 如需詳細資訊，請參閱[資料表，包含 BFILE 資料型別上的作業](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-tables-that-contain-bfile-data-types.md)。  
  
 在基礎 Oracle 資料庫時，LOB 資料類型用來儲存大量的資料，最多為 4 gb (GB)。 除了 BFILE 資料型別，LOB 資料類型支援輸入和輸出資料流。  

## <a name="operations-for-tables-and-views"></a>資料表和檢視表的作業  
 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]呈現介面資料表、 介面檢視、 資料表和檢視表包含 LOB 資料行的下列作業：  
  
-   **Read_\<LOBColName >**:`Read_<LOBColName>`作業會顯示介面資料表、 介面檢視、 資料表和檢視表，包含 BLOB、 CLOB、 NCLOB、 和 BFILE 資料行，其中\<LOBColName > 是的名稱類型 BLOB、 CLOB、 NCLOB 或 BFILE 資料行。 使用 Read_\<LOBColName > 作業，配接器用戶端可以讀取 LOB 資料行做為資料流中的值。 這項作業會接受做為參數的篩選條件字串。  
  
    > [!NOTE]
    >  `Read_<LOBColName>`作業設計來支援 WCF 服務模型中的 LOB 資料的輸入資料流。 您應該使用資料表的 Select 作業讀取 WCF 通道模型中的 LOB 資料或[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]方案。  
  
-   **Update_\<LOBColName >**:`Update_<LOBColName>`作業中會顯示介面資料表和資料表只包含 BLOB、 CLOB、 和 NCLOB 資料行，其中\<LOBColName > 類型 BLOB、 CLOB、 資料行名稱與 NCLOB。 使用 Update_\<LOBColName > 作業，配接器用戶端可以更新 LOB 資料行中的值。 BLOB 資料類型，這項作業接受 base64binary 編碼的資料做為參數，而對於 CLOB 和 NCLOB 資料類型，這項作業會做為參數字串篩選條件。  
  
    > [!NOTE]
    >  `Update_<LOBColName>`作業：  
    >   
    >  -   不支援 BFILE 資料型別。 或者，配接器用戶端可以使用更新作業。 如需詳細資訊，請參閱[資料表，包含 BFILE 資料型別上的作業](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-tables-that-contain-bfile-data-types.md)。  
    > -   不會公開的介面檢視和檢視。  
    > -   必須執行交易的一部分。 若要確保這點， **UseAmbientTransaction**繫結屬性必須設定為**True**。 如需有關資訊**UseAmbientTransaction**繫結屬性，請參閱[Rad BizTalk Adapter for Oracle E-business Suite 繫結屬性的相關](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。  
  
> [!IMPORTANT]
>  [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]介面`Read_<LOBColName>`和`Update_<LOBColName>`資料表中每一個 LOB 資料行的作業。 因此，如果資料表 （LOBCol1 和 LOBCol2） 中有兩個 LOB 資料行，您有兩個`Read_<LOBColName>`作業 （Read_LOBCol1 和 Read_LOBCol2） 和兩個`Update_<LOBColName>`作業 （Update_LOBCol1 和 Update_LOBCol2）。  
  
## <a name="more-good-info"></a>良好的詳細資訊  
  
-   叫用`Read_<LOBColName>`和`Update_<LOBColName>`在 Oracle E-business Suite 中使用基礎資料庫中資料表上的作業[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，請參閱[大型資料類型使用 BizTalk Server 之資料表上執行的作業](../../adapters-and-accelerators/adapter-sql/run-operations-on-tables-and-views-with-large-data-types-using-the-sql-adapter.md)。  
  
-   訊息結構和 SOAP 動作來執行`Read_<LOBColName>`和`Update_<LOBColName>`作業，請參閱[特殊 LOB 作業的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-special-lob-operations1.md)。  
  
## <a name="see-also"></a>另請參閱  
 [哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)