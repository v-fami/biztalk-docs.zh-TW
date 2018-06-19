---
title: 瀏覽 Oracle E-business Suite 作業的成品型檢視下 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 962ac1cc-826c-46d6-848a-4cd371804596
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 982f54878dc290871d7c82c4ebf124ec1f4ab903
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25966804"
---
# <a name="browse-for-oracle-e-business-suite-operations-under-the-artifact-based-view"></a>瀏覽 Oracle E-business Suite 作業下成品為基礎的檢視
您可以使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]瀏覽一概無法對 Oracle E-business Suite 的傳出和傳入作業使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。 本主題提供有關如何瀏覽成品為基礎的檢視之下的傳出和傳入作業的資訊。  
  
> [!NOTE]
>  [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]和[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]呈現基本上相同的介面，當您瀏覽和搜尋作業，因此相同的主題將涵蓋這兩個元件。  
  
## <a name="prerequisites"></a>必要條件  
 您可以瀏覽目標作業的中繼資料之前，您必須連接到 Oracle E-business Suite 的資訊。 如需如何連接到 Oracle 資料庫使用時[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，請參閱[連接到 Visual Studio 中的 Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-the-oracle-e-business-suite-in-visual-studio.md)。  
  
## <a name="browsing-for-outbound-operations"></a>瀏覽傳出作業  
 執行下列步驟來瀏覽成品為基礎的檢視之下的輸出作業。  
  
#### <a name="to-browse-metadata-for-outbound-operations-under-the-artifact-based-view"></a>若要瀏覽成品為基礎的檢視之下的輸出作業的中繼資料  
  
1.  連接到 Oracle E-business Suite 使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 請參閱[連接到 Visual Studio 中的 Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-the-oracle-e-business-suite-in-visual-studio.md)如需相關指示。  
  
2.  從**選取合約型別**傳出作業選取清單**用戶端 （輸出作業）**。  
  
3.  **選取類別目錄**方塊會列出 Oracle E-business Suite 成品會在其下分類的不同檢視。  
  
     下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。 選取根節點 （/），並在根節點下，您可以使用一般分類節點會列出**可用的類別和作業**方塊。  
  
     ![作業和根層級的類別目錄](../../adapters-and-accelerators/adapter-oracle-ebs/media/559a6652-2d9d-4ecd-a1bb-4f63750c9518.gif "559a6652-2d9d-4ecd-a1bb-4f63750c9518")  
  
    > [!NOTE]
    >  標準作業，例如 ExecuteReader、 ExecuteScalar 和 ExecuteNonQuery 可用根層級。 如需有關這些作業的詳細資訊，請參閱[ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 作業支援](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-executenonquery-executereader-and-executescalar-operations.md)。 如需有關如何執行這些作業使用指示[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，請參閱[ExecuteReader、 ExecuteScalar 或使用 BizTalk Server 的 SQL 中的 ExecuteNonQuery 作業](../../adapters-and-accelerators/adapter-sql/executereader-executescalar-or-executenonquery-in-sql-server-using-biztalk.md)。  
  
4.  展開**成品為基礎的檢視**節點以查看成品，同時用於 Oracle E-business Suite 和基礎資料庫的類別。 根據應用程式，它屬於 （適用於 Oracle-E-business Suite 的成品，例如介面資料表、 介面檢視、 並行程式和要求） 或 （oracle 資料庫成品，例如其所屬的結構描述進一步分類每個類別目錄PL-SQL Api、 程序、 函數、 資料表和檢視)。  
  
    > [!TIP]
    >  您可以直接移至 「 立即 」 的類別目錄節點或子類別目錄節點的樹狀目錄中，輸入時的焦點所在的樹狀檢視中的成品名稱**選取類別目錄**方塊。 例如，若要跳至**程序** 節點，將焦點放在**成品為基礎的檢視** 節點，然後輸入`Procedures`。  
  
5.  展開**介面資料表**節點以查看所有 Oracle E-business Suite 應用程式。 展開 Oracle E-business suite 應用程式來列出屬於該應用程式的所有介面資料表。 按一下以查看可用的作業，如資料表中的介面資料表名稱**可用的類別和作業**方塊。  
  
    > [!NOTE]
    >  如果介面資料表包含 BLOB 類型的資料行，CLOB、 NCLOB、 或 BFILE 配接器也會公開這類資料行中讀取資料的特定作業。 這類作業的名稱是 Read_\<LOBColName\>。 例如，如果介面資料表的資料行，FILE_DATA，BLOB 類型的配接器會公開**Read_FILE_DATA**作業。 如果介面資料表有一個以上的資料行的 BLOB 類型，CLOB、 NCLOB、 和 BFILE 配接器會公開任意數目 Read_\<LOBColName\>作業。  
    >   
    >  同樣地，如果介面資料表包含 BLOB 類型的資料行，CLOB 或 NCLOB 配接器也會公開成這類資料行中更新資料的特定作業。 這類作業的名稱是 Update_\<LOBColName\>。 例如，如果介面資料表的資料行，FILE_DATA，BLOB 類型的配接器會公開**Update_FILE_DATA**作業。 如果介面資料表有一個以上的資料行的 BLOB 類型，CLOB，並且 NCLOB 配接器會公開任意數目 Update_\<LOBColName\>作業。 請注意，更新作業不支援的型別 BFILE 資料行上。  
  
6.  展開**介面檢視**節點以查看所有 Oracle E-business Suite 應用程式。 展開 Oracle E-business suite 應用程式來列出屬於該應用程式的所有介面檢視。 按一下以查看作業可用來檢視中的介面檢視名稱**可用的類別和作業**方塊。  
  
    > [!NOTE]
    >  如果介面檢視包含 BLOB 類型的資料行，CLOB、 NCLOB、 或 BFILE 配接器也會公開這類資料行中讀取資料的特定作業。 這類作業的名稱是 Read_\<LOBColName\>。 例如，如果介面檢視有一個資料行，FILE_CONTENT，BLOB 類型的配接器會公開**Read_FILE_CONTENT**作業。 如果介面檢視有一個以上的資料行的 BLOB 類型，CLOB、 NCLOB、 或 BFILE 配接器會公開任意數目 Read_\<LOBColName\>作業。 請注意該 Update_\<LOBColName\>檢視上不支援作業。  
  
7.  展開**並行程式**節點以查看所有 Oracle E-business Suite 應用程式。 按一下 Oracle E-business suite 應用程式來列出屬於該應用程式中的所有並行程式**可用的類別和作業**方塊。  
  
    > [!IMPORTANT]
    >  [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] (或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]) 會顯示並行程式的易記名稱。 不過，並行處理程式的中繼資料會有並行程式的實際名稱。 例如，應收帳款應用程式包含 「 客戶介面 」 的並行處理程式。 不過，中繼資料會有並行的程式名稱為 RACUST，也就是並行程式的實際名稱。  
  
8.  展開**要求集**節點以查看所有 Oracle E-business Suite 應用程式。 按一下 Oracle E-business suite 應用程式來列出屬於該應用程式中的所有要求集**可用的類別和作業**方塊。  
  
    > [!IMPORTANT]
    >  [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] (或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]) 會顯示要求集合的易記名稱。 不過，要求集的中繼資料已實際要求集的名稱。 例如，應用程式 DBA 應用程式包含"DownloadPatches"要求集。 不過，中繼資料都有要求集名稱為 FNDRSSUB1623，並要求集合的實際名稱。  
  
9. 展開**PL-SQL Api**節點以查看目前的使用者結構描述 （與您登入） 和基礎的 Oracle 資料庫中定義的所有其他結構描述的類別目錄節點。 展開**目前結構描述 (\<結構描述名稱\>)** 節點，查看針對該結構描述定義的所有封裝。 按一下以查看函式和程序在封裝內的套件名稱**可用的類別和作業**方塊。  
  
     ![瀏覽 Oracle 資料庫中的套件](../../adapters-and-accelerators/adapter-oracle-ebs/media/7a9dc061-db0b-4a8e-bfc6-3a003ad687d8.gif "7a9dc061-db0b-4a8e-bfc6-3a003ad687d8")  
  
     同樣地，依序展開**所有結構描述**節點以查看在 Oracle 資料庫中定義的所有結構描述的清單。 展開結構描述節點以查看該結構描述定義的封裝清單。 按一下以查看函式和程序在封裝內的套件名稱**可用的類別和作業**方塊。  
  
     ![瀏覽所有結構描述的 Oracle 資料庫中的套件](../../adapters-and-accelerators/adapter-oracle-ebs/media/09a4841b-b88f-490d-a49a-94e392b5493c.gif "09a4841b-b88f-490d-a49a-94e392b5493c")  
  
10. 展開**程序**節點以查看目前的使用者結構描述 （與您登入） 和基礎的 Oracle 資料庫中定義的所有其他結構描述的類別目錄節點。 按一下**目前結構描述 (\<結構描述名稱\>)** 節點以查看針對該結構描述中定義的程序**可用的類別和作業**方塊。  
  
     ![瀏覽 Oracle 資料庫結構描述中的程序](../../adapters-and-accelerators/adapter-oracle-ebs/media/6d78563a-53f7-45cc-8652-f40d4703bdf4.gif "6d78563a-53f7-45cc-8652-f40d4703bdf4")  
  
     同樣地，依序展開**所有結構描述**節點以查看在 Oracle 資料庫中定義的所有結構描述的清單。 按一下 結構描述節點以查看針對該結構描述中定義的程序的清單**可用的類別和作業**方塊。  
  
     ![瀏覽 Oracle 資料庫結構描述中的程序](../../adapters-and-accelerators/adapter-oracle-ebs/media/a514d199-d6c1-44a0-bf6b-28ddf702081a.gif "a514d199-d6c1-44a0-bf6b-28ddf702081a")  
  
11. 展開**函式**節點以查看目前的使用者結構描述 （與您登入） 和基礎的 Oracle 資料庫中定義的所有其他結構描述的類別目錄節點。 按一下**目前結構描述 (\<結構描述名稱\>)** 節點以查看該結構描述中定義的所有函式**可用的類別和作業**方塊。  
  
     ![瀏覽 Oracle 資料庫結構描述中的函式](../../adapters-and-accelerators/adapter-oracle-ebs/media/22c1cabf-9754-4ecd-be37-dbeeb7a6a8fd.gif "22c1cabf-9754-4ecd-be37-dbeeb7a6a8fd")  
  
     同樣地，依序展開**所有結構描述**節點以查看在 Oracle 資料庫中定義的所有結構描述的清單。 按一下以查看該結構描述中定義的函式清單的結構描述節點**可用的類別和作業**方塊。  
  
     ![瀏覽 Oracle 資料庫中所有結構描述中的函式](../../adapters-and-accelerators/adapter-oracle-ebs/media/b4d29036-3d37-4a50-82c2-3532adbe2875.gif "b4d29036-3d37-4a50-82c2-3532adbe2875")  
  
12. 展開**資料表**節點以查看目前的使用者結構描述 （與您登入） 和基礎的 Oracle 資料庫中定義的所有其他結構描述的類別目錄節點。 展開**目前結構描述 (\<結構描述名稱\>)** 節點以查看針對該結構描述定義的所有資料表。 按一下資料表名稱，請參閱支援該資料表中的作業才能**可用的類別和作業**方塊。  
  
     ![瀏覽 Oracle 資料庫結構描述中的資料表](../../adapters-and-accelerators/adapter-oracle-ebs/media/6ba7420f-9893-4b3e-91cb-10f29d725ad3.gif "6ba7420f-9893-4b3e-91cb-10f29d725ad3")  
  
     同樣地，依序展開**所有結構描述**節點以查看在 Oracle 資料庫中定義的所有結構描述的清單。 展開結構描述節點以查看針對該結構描述定義資料表的清單。 按一下資料表名稱，請參閱支援該資料表中的作業才能**可用的類別和作業**方塊。  
  
     ![瀏覽所有結構描述的 Oracle 資料庫資料表](../../adapters-and-accelerators/adapter-oracle-ebs/media/d7c52ab4-ba27-404a-9db6-32b2a635ad2f.gif "d7c52ab4-ba27-404a-9db6-32b2a635ad2f")  
  
    > [!NOTE]
    >  如果資料表包含 BLOB 類型的資料行時，CLOB、 NCLOB、 或 BFILE 配接器也會公開這類資料行中讀取資料的特定作業。 這類作業的名稱是 Read_\<LOBColName\>。 例如，如果資料表有資料行，而相片，BLOB 類型的配接器會公開**Read_PHOTO**作業。 如果資料表有一個以上的資料行的類型 BLOB、 CLOB、 NCLOB、 和 BFILE 配接器會公開 Read_ 任意數目\<LOBColName\>作業。  
    >   
    >  同樣地，如果資料表包含 BLOB 類型的資料行時，CLOB 或 NCLOB 配接器也會公開成這類資料行中更新資料的特定作業。 這類作業的名稱是 Update_\<LOBColName\>。 例如，如果資料表有資料行，而相片，BLOB 類型的配接器會公開**Update_PHOTO**作業。 如果資料表有一個以上的資料行的 BLOB 類型，CLOB，並且 NCLOB 配接器會公開最多數目 Update_\<LOBColName\>作業。 請注意，更新作業不支援的型別 BFILE 資料行上。  
  
13. 展開**檢視**節點以查看目前的使用者結構描述 （與您登入） 和基礎的 Oracle 資料庫中定義的所有其他結構描述的類別目錄節點。 展開**目前結構描述 (\<結構描述名稱\>)** 節點以查看該定義的所有檢視。 按一下 檢視名稱，以查看在該檢視表上支援的作業**可用的類別和作業**方塊。  
  
     ![瀏覽 Oracle 資料庫中目前的結構描述中檢視](../../adapters-and-accelerators/adapter-oracle-ebs/media/2a38cfed-007d-431a-af60-c9c8be5369ab.gif "2a38cfed-007d-431a-af60-c9c8be5369ab")  
  
     同樣地，依序展開**所有結構描述**節點以查看在 Oracle 資料庫中定義的所有結構描述的清單。 展開結構描述節點以查看該結構描述定義檢視的清單。 按一下 檢視名稱，以查看在該檢視表上支援的作業**可用的類別和作業**方塊。  
  
     ![瀏覽所有結構描述的 Oracle 資料庫中的檢視](../../adapters-and-accelerators/adapter-oracle-ebs/media/67ca336c-62ac-4374-87da-07cf331ea4ad.gif "67ca336c-62ac-4374-87da-07cf331ea4ad")  
  
    > [!NOTE]
    >  如果檢視包含 BLOB 類型的資料行，CLOB、 NCLOB、 或 BFILE 配接器也會公開這類資料行中讀取資料的特定作業。 這類作業的名稱是 Read_\<LOBColName\>。 例如，如果檢視的資料行類型的 BLOB，而使用的規則，配接器會公開**Read_RULE**作業。 如果檢視有一個以上的資料行的類型 BLOB、 CLOB、 NCLOB、 或 BFILE 配接器會公開 Read_ 任意數目\<LOBColName\>作業。 請注意該 Update_\<LOBColName\>檢視上不支援作業。  
  
## <a name="browsing-for-inbound-operations"></a>瀏覽的輸入作業  
 執行下列步驟來瀏覽成品為基礎的檢視之下輸入的作業。  
  
#### <a name="to-browse-metadata-for-inbound-operations-under-the-artifact-based-view"></a>若要瀏覽成品為基礎的檢視之下的輸入作業的中繼資料  
  
1.  連接到 Oracle E-business Suite 使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 請參閱[連接到 Visual Studio 中的 Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-the-oracle-e-business-suite-in-visual-studio.md)如需相關指示。  
  
2.  從**選取合約型別**清單，輸入的作業選取**服務 （輸入操作）**。  
  
3.  **選取類別目錄**方塊會列出 Oracle E-business Suite 成品會在其下分類的不同檢視。  
  
     下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。 選取根節點 （/），並在根節點下，您可以使用一般分類節點會列出**可用的類別和作業**方塊。  
  
     ![輸入根層級作業](../../adapters-and-accelerators/adapter-oracle-ebs/media/9f9f95f3-c6cc-415c-b534-d5f1ad1963d5.gif "9f9f95f3-c6cc-415c-b534-d5f1ad1963d5")  
  
     輸入的作業，**通知**，也會提供根層級。  
  
4.  展開**成品為基礎的檢視**節點以查看成品，同時用於 Oracle E-business Suite 和基礎資料庫的類別。 根據應用程式，它屬於 （適用於 Oracle-E-business Suite 的成品，例如介面資料表和檢視介面） 或 （適用於 Oracle 資料庫成品，例如 PL-SQL Api 程序、 函數、 所屬的結構描述進一步分類每個類別目錄資料表和檢視表）。  
  
    > [!TIP]
    >  您可以直接移至 「 立即 」 的類別目錄節點或子類別目錄節點的樹狀目錄中，輸入時的焦點所在的樹狀檢視中的成品名稱**選取類別目錄**方塊。 例如，若要跳至**程序** 節點，將焦點放在**成品為基礎的檢視** 節點，然後輸入`Procedures`。  
  
    > [!NOTE]
    >  [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]不介面並行程式，要求的輸入操作的集合。  
  
5.  展開以查看介面資料表和可供該應用程式使用的介面檢視類別 Oracle 應用程式。 展開**介面資料表**和**介面檢視**節點，以查看 interface table 和 Oracle 應用程式的介面檢視。 按一下 若要查看輸入的作業使用的資料表或檢視中的介面資料表或介面檢視**可用的類別和作業**方塊。  
  
     在下圖中選取的介面檢視**選取類別目錄**方塊而在檢視上支援的輸入的操作則列於**可用的類別和作業**方塊。  
  
     ![介面檢視上的輸入操作](../../adapters-and-accelerators/adapter-oracle-ebs/media/937f46f2-d142-413f-8744-2180c7116fd4.gif "937f46f2-d142-413f-8744-2180c7116fd4")  
  
6.  展開**PL-SQL Api**節點以查看目前的使用者結構描述 （與您登入） 和基礎的 Oracle 資料庫中定義的所有其他結構描述的類別目錄節點。 展開**目前結構描述 (\<結構描述名稱\>)** 節點，查看針對該結構描述定義的所有封裝。 按一下以查看函式和程序在封裝內的套件名稱**可用的類別和作業**方塊。 每個所列出函式和程序可用於輪詢 Oracle 資料庫。  
  
     ![瀏覽 PL &#45;SQL Api 在 Oracle 資料庫進行輪詢](../../adapters-and-accelerators/adapter-oracle-ebs/media/4b31ea85-9c5a-42b4-82b2-2cb6d3ead35a.gif "4b31ea85-9c5a-42b4-82b2-2cb6d3ead35a")  
  
     同樣地，依序展開**所有結構描述**節點以查看在 Oracle 資料庫中定義的所有結構描述的清單。 展開結構描述節點以查看該結構描述定義的封裝清單。 按一下以查看函式和程序在封裝內的套件名稱**可用的類別和作業**方塊。 每個所列出函式和程序可用於輪詢 Oracle 資料庫。  
  
     ![瀏覽 PL &#45;所有的結構描述進行輪詢 SQL Api](../../adapters-and-accelerators/adapter-oracle-ebs/media/e28a803e-fcfb-4021-9225-924d54a484c0.gif "e28a803e-fcfb-4021-9225-924d54a484c0")  
  
7.  展開**程序**節點以查看目前的使用者結構描述 （與您登入） 和基礎的 Oracle 資料庫中定義的所有其他結構描述的類別目錄節點。 按一下**目前結構描述 (\<結構描述名稱\>)** 節點以查看針對該結構描述中定義的程序**可用的類別和作業**方塊。 每個列出的程序可用於輪詢 Oracle 資料庫。  
  
     ![瀏覽所有結構描述進行輪詢的程序](../../adapters-and-accelerators/adapter-oracle-ebs/media/5e78da80-d99a-44d3-8eac-f636828f8ceb.gif "5e78da80-d99a-44d3-8eac-f636828f8ceb")  
  
     同樣地，依序展開**所有結構描述**節點以查看在 Oracle 資料庫中定義的所有結構描述的清單。 按一下 結構描述節點以查看針對該結構描述中定義的程序的清單**可用的類別和作業**方塊。 每個列出的程序可用於輪詢 Oracle 資料庫。  
  
     ![瀏覽輪詢 Oracle 資料庫中的程序](../../adapters-and-accelerators/adapter-oracle-ebs/media/22d8e866-ed19-49f4-a6eb-683343b16cf5.gif "22d8e866-ed19-49f4-a6eb-683343b16cf5")  
  
8.  展開**函式**節點以查看目前的使用者結構描述 （與您登入） 和基礎的 Oracle 資料庫中定義的所有其他結構描述的類別目錄節點。 按一下**目前結構描述 (\<結構描述名稱\>)** 節點以查看該結構描述中定義的所有函式**可用的類別和作業**方塊。 每個所列出函式可用於輪詢 Oracle 資料庫。  
  
     ![瀏覽輪詢 Oracle 資料庫中的函式](../../adapters-and-accelerators/adapter-oracle-ebs/media/64c0a30d-a2d6-4dee-90cb-a7e7e2bf62cf.gif "64c0a30d-a2d6-4dee-90cb-a7e7e2bf62cf")  
  
     同樣地，依序展開**所有結構描述**節點以查看在 Oracle 資料庫中定義的所有結構描述的清單。 按一下以查看該結構描述中定義的函式清單的結構描述節點**可用的類別和作業**方塊。  每個所列出函式可用於輪詢 Oracle 資料庫。  
  
     ![瀏覽輪詢 Oracle 資料庫中的函式](../../adapters-and-accelerators/adapter-oracle-ebs/media/1d22c3c8-8c24-4905-8144-bdb4840244f1.gif "1d22c3c8-8c24-4905-8144-bdb4840244f1")  
  
9. 展開**資料表**節點以查看目前的使用者結構描述 （與您登入） 和基礎的 Oracle 資料庫中定義的所有其他結構描述的類別目錄節點。 展開**目前結構描述 (\<結構描述名稱\>)** 節點以查看針對該結構描述定義的所有資料表。 按一下資料表名稱，才能看到**輪詢**輸入該資料表中支援此作業**可用的類別和作業**方塊。  
  
     ![瀏覽輪詢 Oracle 資料庫中的資料表](../../adapters-and-accelerators/adapter-oracle-ebs/media/7c60dfbf-3836-4e72-abe8-5f32a0936807.gif "7c60dfbf-3836-4e72-abe8-5f32a0936807")  
  
     同樣地，依序展開**所有結構描述**節點以查看在 Oracle 資料庫中定義的所有結構描述的清單。 展開結構描述節點以查看針對該結構描述定義資料表的清單。 按一下資料表名稱，才能看到**輪詢**輸入該資料表中支援此作業**可用的類別和作業**方塊。  
  
     ![瀏覽輪詢 Oracle 資料庫中的資料表](../../adapters-and-accelerators/adapter-oracle-ebs/media/c5fbaf59-2e79-4141-8a85-1e1b8eedcea7.gif "c5fbaf59-2e79-4141-8a85-1e1b8eedcea7")  
  
10. 展開**檢視**節點以查看目前的使用者結構描述 （與您登入） 和基礎的 Oracle 資料庫中定義的所有其他結構描述的類別目錄節點。 展開**目前結構描述 (\<結構描述名稱\>)** 節點以查看該定義的所有檢視。 按一下 檢視名稱，以查看**輪詢**輸入該檢視中支援此作業**可用的類別和作業**方塊。  
  
     ![瀏覽 Oracle 資料庫進行輪詢中的檢視](../../adapters-and-accelerators/adapter-oracle-ebs/media/2299de79-9f50-433d-9e71-164f6d02bd78.gif "2299de79-9f50-433d-9e71-164f6d02bd78")  
  
     同樣地，依序展開**所有結構描述**節點以查看在 Oracle 資料庫中定義的所有結構描述的清單。 展開結構描述節點以查看該結構描述定義檢視的清單。 按一下 檢視名稱，以查看**輪詢**輸入該檢視中支援此作業**可用的類別和作業**方塊。  
  
     ![瀏覽 Oracle 資料庫進行輪詢中的檢視](../../adapters-and-accelerators/adapter-oracle-ebs/media/860e6636-1ef6-42ad-a0e2-d661e632b624.gif "860e6636-1ef6-42ad-a0e2-d661e632b624")  
  
## <a name="see-also"></a>請參閱  
 [瀏覽、 搜尋及取得 Oracle E-business Suite 作業的中繼資料](../../adapters-and-accelerators/adapter-oracle-ebs/browse-search-and-get-metadata-for-oracle-e-business-suite-operations.md)