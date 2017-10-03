---
title: "瀏覽 Oracle E-business Suite 作業的應用程式為基礎的檢視之下 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb207869-1a19-4e19-ba47-c78d2a29b36d
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d06cf551d033614cb75456845e059c6ec4ec8fa8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="browse-for-oracle-e-business-suite-operations-under-the-application-based-view"></a>瀏覽 Oracle E-business Suite 作業下應用程式為基礎的檢視
您可以使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]瀏覽一概無法對 Oracle E-business Suite 的傳出和傳入作業使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。 本主題提供有關如何瀏覽應用程式為基礎的檢視之下的傳出和傳入作業的資訊。  
  
> [!NOTE]
>  [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]和[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]呈現基本上相同的介面，當您瀏覽和搜尋作業，因此相同的主題將涵蓋這兩個元件。  
  
## <a name="prerequisites"></a>必要條件  
 您可以瀏覽目標作業的中繼資料之前，您必須連接到 Oracle E-business Suite 的資訊。 如需如何連接到 Oracle 資料庫使用時[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，請參閱[連接到 Visual Studio 中的 Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-the-oracle-e-business-suite-in-visual-studio.md)。  
  
## <a name="browsing-for-outbound-operations"></a>瀏覽傳出作業  
 執行下列步驟來瀏覽應用程式為基礎的檢視底下的輸出作業。  
  
#### <a name="to-browse-metadata-for-outbound-operations-under-the-application-based-view"></a>若要瀏覽應用程式為基礎的檢視底下的輸出作業的中繼資料  
  
1.  連接到 Oracle E-business Suite 使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 請參閱[連接到 Visual Studio 中的 Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-the-oracle-e-business-suite-in-visual-studio.md)如需相關指示。  
  
2.  從**選取合約型別**清單中，選取**用戶端 （輸出作業）**。  
  
3.  **選取類別目錄**方塊會列出 Oracle E-business Suite 成品會在其下分類的不同檢視。  
  
     下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。 選取根節點 （/），並在根節點下，您可以使用一般分類節點會列出**可用的類別和作業**方塊。  
  
     ![作業和根層級的類別目錄](../../adapters-and-accelerators/adapter-oracle-ebs/media/559a6652-2d9d-4ecd-a1bb-4f63750c9518.gif "559a6652-2d9d-4ecd-a1bb-4f63750c9518")  
  
    > [!NOTE]
    >  標準作業，例如 ExecuteReader、 ExecuteScalar 和 ExecuteNonQuery 可用根層級。 如需有關這些作業的詳細資訊，請參閱[ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 作業支援](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-executenonquery-executereader-and-executescalar-operations.md)。 如需有關如何執行這些作業使用指示[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，請參閱[ExecuteReader、 ExecuteScalar 或使用 BizTalk Server 的 SQL 中的 ExecuteNonQuery 作業](../../adapters-and-accelerators/adapter-sql/executereader-executescalar-or-executenonquery-in-sql-server-using-biztalk.md)。  
  
4.  展開**應用程式為基礎的檢視**節點以查看您連線到伺服器上的所有 Oracle E-business suite 可用的應用程式。 展開以查看類別介面資料表、 檢視介面、 並行程式，應用程式，並要求設定適用於該應用程式。  
  
    > [!TIP]
    >  您可以直接移至 「 立即 」 的類別目錄節點或子類別目錄節點的樹狀目錄中，輸入中的成品名稱時的焦點所在的樹狀檢閱中**選取類別目錄**方塊。 例如，若要跳至**警示** 節點，將焦點放在**應用程式為基礎的檢視** 節點，然後輸入`Alert`。  
  
5.  展開**介面資料表**節點以查看 Oracle 應用程式的介面資料表。 按一下以查看可用的作業清單中之資料表的介面資料表**可用的類別和作業**方塊。  
  
     ![瀏覽 Oracle &#45; 中的介面資料表Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/media/fcfbe41c-14e0-43b5-aada-c4c686aecff4.gif "fcfbe41c-14e0-43b5-aada-c4c686aecff4")  
  
    > [!NOTE]
    >  如果介面資料表包含 BLOB 類型的資料行，CLOB、 NCLOB、 或 BFILE 配接器也會公開這類資料行中讀取資料的特定作業。 這類作業的名稱是 Read_\<LOBColName >。 例如，如果介面資料表的資料行，FILE_DATA，BLOB 類型的配接器會公開**Read_FILE_DATA**作業。 如果介面資料表有一個以上的資料行的 BLOB 類型，CLOB、 NCLOB、 和 BFILE 配接器會公開任意數目 Read_\<LOBColName > 作業。  
    >   
    >  同樣地，如果介面資料表包含 BLOB 類型的資料行，CLOB 或 NCLOB 配接器也會公開成這類資料行中更新資料的特定作業。 這類作業的名稱是 Update_\<LOBColName >。 例如，如果介面資料表的資料行，FILE_DATA，BLOB 類型的配接器會公開**Update_FILE_DATA**作業。 如果介面資料表有一個以上的資料行的 BLOB 類型，CLOB，並且 NCLOB 配接器會公開任意數目 Update_\<LOBColName > 作業。 請注意，更新作業不支援的型別 BFILE 資料行上。  
  
6.  展開**介面檢視**節點以查看 Oracle 應用程式的介面檢視。 按一下以查看可用的作業清單檢視中的介面檢視**可用的類別和作業**方塊。  
  
     ![瀏覽 Oracle &#45; 中的介面檢視Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/media/f1dc14cc-ad77-47ed-b0b0-b5fc78ed545b.gif "f1dc14cc-ad77-47ed-b0b0-b5fc78ed545b")  
  
    > [!NOTE]
    >  如果介面檢視包含 BLOB 類型的資料行，CLOB、 NCLOB、 或 BFILE 配接器也會公開這類資料行中讀取資料的特定作業。 這類作業的名稱是 Read_\<LOBColName >。 例如，如果介面檢視有一個資料行，FILE_CONTENT，BLOB 類型的配接器會公開**Read_FILE_CONTENT**作業。 如果介面檢視有一個以上的資料行的 BLOB 類型，CLOB、 NCLOB、 或 BFILE 配接器會公開任意數目 Read_\<LOBColName > 作業。 請注意該 Update_\<LOBColName > 檢視表上不支援作業。  
  
7.  按一下**並行程式**節點以查看應用程式中的並行程式**可用的類別和作業**方塊。  
  
     ![瀏覽 Oracle 應用程式的並行程式](../../adapters-and-accelerators/adapter-oracle-ebs/media/71173055-4250-4406-838b-c5e9d6bf9e8c.gif "71173055-4250-4406-838b-c5e9d6bf9e8c")  
  
     此圖顯示並行 Oracle 應用程式特定的程式和標準並行程式中的所有 Oracle 應用程式。  
  
    > [!IMPORTANT]
    >  [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] (或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]) 會顯示並行程式的易記名稱。 不過，並行處理程式的中繼資料會有並行程式的實際名稱。 例如，應收帳款應用程式包含 「 客戶介面 」 的並行處理程式。 不過，中繼資料會有並行的程式名稱為 RACUST，也就是並行程式的實際名稱。  
  
8.  按一下**要求設定**中的應用程式設定節點以查看要求**可用的類別和作業**方塊。  
  
     ![瀏覽 Oracle 應用程式的要求組](../../adapters-and-accelerators/adapter-oracle-ebs/media/0934f6f5-0d7a-4dad-a550-e7a4f524551b.gif "0934f6f5-0d7a-4dad-a550-e7a4f524551b")  
  
    > [!IMPORTANT]
    >  [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] (或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]) 會顯示要求集合的易記名稱。 不過，要求集的中繼資料已實際要求集的名稱。 例如，應用程式 DBA 應用程式包含"DownloadPatches"要求集。 不過，中繼資料都有要求集名稱為 FNDRSSUB1623，並要求集合的實際名稱。  
  
## <a name="browsing-for-inbound-operations"></a>瀏覽的輸入作業  
 執行下列步驟來瀏覽應用程式為基礎的檢視之下輸入的作業。  
  
#### <a name="to-browse-metadata-for-inbound-operations-under-the-application-based-view"></a>若要瀏覽應用程式為基礎的檢視之下的輸入作業的中繼資料  
  
1.  連接到 Oracle E-business Suite 使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 請參閱[連接到 Visual Studio 中的 Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-the-oracle-e-business-suite-in-visual-studio.md)如需相關指示。  
  
2.  從**選取合約型別**清單，輸入的作業選取**服務 （輸入操作）**。  
  
3.  **選取類別目錄**方塊會列出 Oracle E-business Suite 成品會在其下分類的不同檢視。  
  
     下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。 選取根節點 （/），並在根節點下，您可以使用一般分類節點會列出**可用的類別和作業**方塊。  
  
     ![輸入根層級作業](../../adapters-and-accelerators/adapter-oracle-ebs/media/9f9f95f3-c6cc-415c-b534-d5f1ad1963d5.gif "9f9f95f3-c6cc-415c-b534-d5f1ad1963d5")  
  
     輸入的作業，**通知**，也會提供根層級。  
  
4.  展開**應用程式為基礎的檢視**節點以查看您連線到伺服器上的所有 Oracle E-business suite 可用的應用程式。 展開以查看介面資料表和介面檢視類別的應用程式。  
  
    > [!TIP]
    >  您可以直接移至 「 立即 」 的類別目錄節點或子類別目錄節點的樹狀目錄中，輸入中的成品名稱時的焦點所在的樹狀檢閱中**選取類別目錄**方塊。 例如，若要跳至**警示** 節點，將焦點放在**應用程式為基礎的檢視** 節點，然後輸入`Alert`。  
  
5.  展開以查看介面資料表和可供該應用程式使用的介面檢視類別 Oracle 應用程式。 展開**介面資料表**和**介面檢視**節點，以查看 interface table 和 Oracle 應用程式的介面檢視。 按一下 若要查看輸入的作業使用的資料表或檢視中的介面資料表或介面檢視**可用的類別和作業**方塊。  
  
     在下圖中選取的介面檢視**選取類別目錄**方塊而在檢視上支援的輸入的操作則列於**可用的類別和作業**方塊。  
  
     ![介面檢視上的輸入操作](../../adapters-and-accelerators/adapter-oracle-ebs/media/937f46f2-d142-413f-8744-2180c7116fd4.gif "937f46f2-d142-413f-8744-2180c7116fd4")  
  
    > [!NOTE]
    >  [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]不介面並行程式，要求的輸入操作的集合。  
  
## <a name="see-also"></a>另請參閱  
 [瀏覽、 搜尋及取得 Oracle E-business Suite 作業的中繼資料](../../adapters-and-accelerators/adapter-oracle-ebs/browse-search-and-get-metadata-for-oracle-e-business-suite-operations.md)