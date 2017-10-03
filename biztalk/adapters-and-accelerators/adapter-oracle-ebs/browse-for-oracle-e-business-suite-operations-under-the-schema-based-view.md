---
title: "瀏覽 Oracle E-business Suite 作業的結構描述為基礎的檢視之下 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d004a99f-0db1-4cdb-80cd-ea71de4e1098
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8e3dea968a12470498012f7dae4fb3093fc05e59
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="browse-for-oracle-e-business-suite-operations-under-the-schema-based-view"></a>瀏覽 Oracle E-business Suite 作業在結構描述為基礎的檢視
您可以使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]瀏覽一概無法對 Oracle E-business Suite 的傳出和傳入作業使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。 本主題提供有關如何瀏覽結構描述為基礎的檢視之下的傳出和傳入作業的資訊。  
  
> [!NOTE]
>  [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]和[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]呈現基本上相同的介面，當您瀏覽和搜尋作業，因此相同的主題將涵蓋這兩個元件。  
  
## <a name="prerequisites"></a>必要條件  
 您可以瀏覽目標作業的中繼資料之前，您必須連接到 Oracle E-business Suite 的資訊。 如需如何連接到 Oracle 資料庫使用時[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，請參閱[連接到 Visual Studio 中的 Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-the-oracle-e-business-suite-in-visual-studio.md)。  
  
## <a name="browsing-for-outbound-operations"></a>瀏覽傳出作業  
 執行下列步驟來瀏覽之結構描述為基礎的檢視底下的輸出作業。  
  
#### <a name="to-browse-metadata-for-outbound-operations-under-the-schema-based-view"></a>若要瀏覽之結構描述為基礎的檢視底下的輸出作業的中繼資料  
  
1.  連接到 Oracle E-business Suite 使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 請參閱[連接到 Visual Studio 中的 Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-the-oracle-e-business-suite-in-visual-studio.md)如需相關指示。  
  
2.  從**選取合約型別**傳出作業選取清單**用戶端 （輸出作業）**。  
  
3.  **選取類別目錄**方塊會列出 Oracle E-business Suite 成品會在其下分類的不同檢視。  
  
     下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。 選取根節點 （/），並在根節點下，您可以使用一般分類節點會列出**可用的類別和作業**方塊。  
  
     ![作業和根層級的類別目錄](../../adapters-and-accelerators/adapter-oracle-ebs/media/559a6652-2d9d-4ecd-a1bb-4f63750c9518.gif "559a6652-2d9d-4ecd-a1bb-4f63750c9518")  
  
    > [!NOTE]
    >  標準作業，例如 ExecuteReader、 ExecuteScalar 和 ExecuteNonQuery 可用根層級。 如需有關這些作業的詳細資訊，請參閱[ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 作業支援](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-executenonquery-executereader-and-executescalar-operations.md)。 如需有關如何執行這些作業使用指示[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，請參閱[ExecuteReader、 ExecuteScalar 或使用 BizTalk Server 的 SQL 中的 ExecuteNonQuery 作業](../../adapters-and-accelerators/adapter-sql/executereader-executescalar-or-executenonquery-in-sql-server-using-biztalk.md)。  
  
4.  展開**結構描述為基礎的檢視**節點以查看基礎資料庫中定義之結構描述。 每個結構描述會進一步分類根據 PL-SQL Api、 程序、 函數、 資料表和檢視其中的內容。  
  
    > [!TIP]
    >  您可以直接移至 「 立即 」 的類別目錄節點或子類別目錄節點的樹狀目錄中，輸入時的焦點所在的樹狀檢視中的成品名稱**選取類別目錄**方塊。 例如，若要跳至**SCOTT**結構描述中，將焦點放在**結構描述為基礎的檢視** 節點，然後輸入`SCOTT`。  
  
5.  展開**PL-SQL Api**節點以查看特定的結構描述的 Oracle 資料庫中定義的封裝清單。 按一下以查看函式和在該封裝內定義的程序的套件名稱**可用的類別和作業**方塊。  
  
     ![瀏覽 Oracle 資料庫中的套件](../../adapters-and-accelerators/adapter-oracle-ebs/media/582a9bd7-beed-4b36-b465-f5c4ceb6e740.gif "582a9bd7-beed-4b36-b465-f5c4ceb6e740")  
  
6.  按一下**程序**節點，查看清單中的程序**可用的類別和作業**方塊。  
  
     ![瀏覽 Oracle 資料庫中的程序](../../adapters-and-accelerators/adapter-oracle-ebs/media/7213154e-6a26-4fc3-b4ec-1658779f77d3.gif "7213154e-6a26-4fc3-b4ec-1658779f77d3")  
  
7.  按一下**函式**節點，查看清單中的函式**可用的類別和作業**方塊。  
  
     ![瀏覽 Oracle 資料庫中的函式](../../adapters-and-accelerators/adapter-oracle-ebs/media/5df9b42c-9d8b-4c81-a0ae-ba5336445837.gif "5df9b42c-9d8b-4c81-a0ae-ba5336445837")  
  
8.  展開**資料表**節點以查看特定的結構描述的資料表清單。 按一下資料表名稱，請參閱中的資料表上支援的作業才能**可用的類別和作業**方塊。  
  
     ![瀏覽 Oracle 資料庫中資料表](../../adapters-and-accelerators/adapter-oracle-ebs/media/94dd4642-1178-4d88-986b-f0ad409c414c.gif "94dd4642-1178-4d88-986b-f0ad409c414c")  
  
    > [!NOTE]
    >  如果資料表包含 BLOB 類型的資料行時，CLOB、 NCLOB、 或 BFILE 配接器也會公開這類資料行中讀取資料的特定作業。 這類作業的名稱是 Read_\<LOBColName >。 例如，如果資料表有資料行，而相片，BLOB 類型的配接器會公開**Read_PHOTO**作業。 如果資料表有一個以上的資料行的類型 BLOB、 CLOB、 NCLOB、 和 BFILE 配接器會公開 Read_ 任意數目\<LOBColName > 作業。  
    >   
    >  同樣地，如果資料表包含 BLOB 類型的資料行時，CLOB 或 NCLOB 配接器也會公開成這類資料行中更新資料的特定作業。 這類作業的名稱是 Update_\<LOBColName >。 例如，如果資料表有資料行，而相片，BLOB 類型的配接器會公開**Update_PHOTO**作業。 如果資料表有一個以上的資料行的 BLOB 類型，CLOB，並且 NCLOB 配接器會公開最多數目 Update_\<LOBColName > 作業。 請注意，更新作業不支援的型別 BFILE 資料行上。  
  
9. 展開**檢視**節點以查看特定結構描述檢視的清單。 按一下 檢視名稱，若要查看的檢視支援的作業**可用的類別和作業**方塊。  
  
     ![瀏覽 Oracle 資料庫中的檢視](../../adapters-and-accelerators/adapter-oracle-ebs/media/e1893e48-065c-4642-b076-192758d103db.gif "e1893e48-065c-4642-b076-192758d103db")  
  
    > [!NOTE]
    >  如果檢視包含 BLOB 類型的資料行，CLOB、 NCLOB、 或 BFILE 配接器也會公開這類資料行中讀取資料的特定作業。 這類作業的名稱是 Read_\<LOBColName >。 例如，如果檢視的資料行類型的 BLOB，而使用的規則，配接器會公開**Read_RULE**作業。 如果檢視有一個以上的資料行的類型 BLOB、 CLOB、 NCLOB、 或 BFILE 配接器會公開 Read_ 任意數目\<LOBColName > 作業。 請注意該 Update_\<LOBColName > 檢視表上不支援作業。  
  
## <a name="browsing-for-inbound-operations"></a>瀏覽的輸入作業  
 執行下列步驟來瀏覽結構描述為基礎的檢視之下輸入的作業。  
  
#### <a name="to-browse-metadata-for-inbound-operations-under-the-schema-based-view"></a>若要瀏覽中繼資料的結構描述為基礎的檢視之下的輸入作業  
  
1.  連接到 Oracle E-business Suite 使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 請參閱[連接到 Visual Studio 中的 Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-the-oracle-e-business-suite-in-visual-studio.md)如需相關指示。  
  
2.  從**選取合約型別**清單，輸入的作業選取**服務 （輸入操作）**。  
  
3.  **選取類別目錄**方塊會列出 Oracle E-business Suite 成品會在其下分類的不同檢視。  
  
     下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。 選取根節點 （/），並在根節點下，您可以使用一般分類節點會列出**可用的類別和作業**方塊。  
  
     ![輸入根層級作業](../../adapters-and-accelerators/adapter-oracle-ebs/media/9f9f95f3-c6cc-415c-b534-d5f1ad1963d5.gif "9f9f95f3-c6cc-415c-b534-d5f1ad1963d5")  
  
     輸入的作業，**通知**，也會提供根層級。  
  
4.  展開**結構描述為基礎的檢視**節點以查看基礎資料庫中定義之結構描述。 每個結構描述會進一步分類根據 PL-SQL Api、 程序、 函數、 資料表和檢視其中的內容。  
  
    > [!TIP]
    >  您可以直接移至 「 立即 」 的類別目錄節點或子類別目錄節點的樹狀目錄中，輸入時的焦點所在的樹狀檢視中的成品名稱**選取類別目錄**方塊。 例如，若要跳至**SCOTT**結構描述中，將焦點放在**結構描述為基礎的檢視** 節點，然後輸入`SCOTT`。  
  
5.  展開**PL-SQL Api**節點以查看特定的結構描述的 Oracle 資料庫中定義的封裝清單。 按一下以查看函式和在該封裝內定義的程序的套件名稱**可用的類別和作業**方塊。 每個所列出函式和程序可用於輪詢 Oracle 資料庫。  
  
     ![瀏覽輪詢 Oracle 資料庫中的套件](../../adapters-and-accelerators/adapter-oracle-ebs/media/ab45e4a3-1425-4b23-afc2-8aecef546802.gif "ab45e4a3-1425-4b23-afc2-8aecef546802")  
  
6.  按一下**程序**節點，查看清單中的程序**可用的類別和作業**方塊。 每個列出的程序可用於輪詢 Oracle 資料庫。  
  
     ![瀏覽輪詢 Oracle 資料庫中的程序](../../adapters-and-accelerators/adapter-oracle-ebs/media/04538693-5abf-4162-82e9-4107b4088b56.gif "04538693-5abf-4162-82e9-4107b4088b56")  
  
7.  按一下**函式**節點，查看清單中的函式**可用的類別和作業**方塊。 每個所列出函式可用於輪詢 Oracle 資料庫。  
  
     ![瀏覽輪詢 Oracle 資料庫中的函式](../../adapters-and-accelerators/adapter-oracle-ebs/media/b3f4ea5b-d03f-4cb5-82b4-8fbf0a8af24b.gif "b3f4ea5b-d03f-4cb5-82b4-8fbf0a8af24b")  
  
8.  展開**資料表**節點以查看特定的結構描述的資料表清單。 按一下資料表名稱，才能看到**輪詢**輸入中的資料表上支援的作業**可用的類別和作業**方塊。  
  
     ![瀏覽輪詢 Oracle 資料庫中的資料表](../../adapters-and-accelerators/adapter-oracle-ebs/media/58e9315d-3194-4a01-a505-bd1514e9d7e3.gif "58e9315d-3194-4a01-a505-bd1514e9d7e3")  
  
9. 展開**檢視**節點以查看特定結構描述檢視的清單。 按一下 檢視名稱，以查看**輪詢**輸入中的檢視支援的作業**可用的類別和作業**方塊。  
  
     ![瀏覽 Oracle 資料庫進行輪詢中的檢視](../../adapters-and-accelerators/adapter-oracle-ebs/media/f1282f17-efbe-43e6-90fa-5676e04051e8.gif "f1282f17-efbe-43e6-90fa-5676e04051e8")  
  
## <a name="see-also"></a>另請參閱  
 [瀏覽、 搜尋及取得 Oracle E-business Suite 作業的中繼資料](../../adapters-and-accelerators/adapter-oracle-ebs/browse-search-and-get-metadata-for-oracle-e-business-suite-operations.md)