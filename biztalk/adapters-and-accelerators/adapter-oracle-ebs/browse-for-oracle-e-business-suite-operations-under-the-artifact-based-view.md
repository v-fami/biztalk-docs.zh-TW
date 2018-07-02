---
title: 瀏覽 Oracle E-business Suite 作業，以檢視成品形式 |Microsoft Docs
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
ms.openlocfilehash: a70b378393839a4f1f03dbd6841d85fbd06fd18d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36979623"
---
# <a name="browse-for-oracle-e-business-suite-operations-under-the-artifact-based-view"></a>瀏覽 Oracle E-business Suite 作業，以檢視成品形式
您可以使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]瀏覽 Oracle E-business Suite 可以執行的傳出和傳入作業使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。 本主題提供有關如何瀏覽 以檢視成品形式的輸入和輸出作業的資訊。  
  
> [!NOTE]
>  [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]而[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]呈現基本上相同的介面，當您瀏覽和搜尋作業，因此這兩個元件所述的相同的主題。  
  
## <a name="prerequisites"></a>必要條件  
 您可以瀏覽目標作業的中繼資料之前，您必須連接到 Oracle E-business Suite。 如需如何連接到 Oracle 資料庫使用時[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，請參閱[連接到 Oracle E-business Suite，在 Visual Studio 中](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-the-oracle-e-business-suite-in-visual-studio.md)。  
  
## <a name="browsing-for-outbound-operations"></a>瀏覽輸出的作業  
 執行下列步驟來瀏覽 以檢視成品形式傳出作業。  
  
#### <a name="to-browse-metadata-for-outbound-operations-under-the-artifact-based-view"></a>若要瀏覽以檢視成品形式的輸出作業的中繼資料  
  
1. 連接到 Oracle E-business Suite 使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 請參閱[連接到 Oracle E-business Suite，在 Visual Studio 中](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-the-oracle-e-business-suite-in-visual-studio.md)如需相關指示。  
  
2. 從**選取合約的型別**清單中，選取傳出作業**用戶端 （傳出作業）**。  
  
3. **選取一個類別**方塊會列出 Oracle E-business Suite 成品的分類所在的不同檢視。  
  
    下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。 選取根節點 （/），且一般分類可用的節點的根節點下所述**可用的類別和作業** 方塊中。  
  
    ![作業與類別的根層級](../../adapters-and-accelerators/adapter-oracle-ebs/media/559a6652-2d9d-4ecd-a1bb-4f63750c9518.gif "559a6652-2d9d-4ecd-a1bb-4f63750c9518")  
  
   > [!NOTE]
   >  ExecuteReader、 ExecuteScalar 等 ExecuteNonQuery 標準作業可在根層級。 如需有關這些作業的詳細資訊，請參閱 <<c0> [ 支援 ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 作業](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-executenonquery-executereader-and-executescalar-operations.md)。 如需有關如何執行這些作業使用指示[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，請參閱 < [ExecuteReader、 ExecuteScalar 或 ExecuteNonQuery 作業中使用 BizTalk Server 的 SQL](../../adapters-and-accelerators/adapter-sql/executereader-executescalar-or-executenonquery-in-sql-server-using-biztalk.md)。  
  
4. 依序展開**成品為基礎的檢視**節點以查看針對 Oracle E-business Suite 和基礎資料庫的成品的類別。 根據其所屬 （適用於 Oracle-E-business Suite 成品，例如介面資料表、 介面檢視、 同時執行的程式，並要求集） 的應用程式或 （適用於 Oracle 資料庫成品，例如其所屬的結構描述進一步分類每個類別目錄PL-SQL Api、 程序、 函數、 資料表和檢視)。  
  
   > [!TIP]
   >  您可以直接移至 「 立即 」 的類別目錄節點或子類別目錄節點樹狀目錄中，輸入時的焦點所在的樹狀檢視中的成品名稱**選取一個類別** 方塊中。 例如，若要跳至**程序**節點，專注**成品的檢視形式**節點，然後按`Procedures`。  
  
5. 依序展開**Interface Table**節點以查看所有 Oracle E-business Suite 應用程式。 展開 Oracle E-business suite 應用程式列出所有屬於該應用程式的介面資料表。 按一下以查看可供中的資料表作業的介面資料表名稱**可用的類別和作業** 方塊中。  
  
   > [!NOTE]
   >  如果在介面資料表包含 BLOB 類型的資料行，CLOB、 NCLOB、 或 BFILE 配接器也會公開這類資料行中讀取資料的特定作業。 這類作業的名稱是 Read_\<LOBColName\>。 例如，如果介面資料表的資料行，FILE_DATA，BLOB 類型的配接器會公開**Read_FILE_DATA**作業。 CLOB、 NCLOB、 和 BFILE 配接器在介面資料表有一個以上的資料行的 BLOB 類型，如果會公開多個數目 Read_\<LOBColName\>作業。  
   >   
   >  同樣地，如果在介面資料表包含 BLOB 類型的資料行，CLOB、 或 NCLOB 配接器也會公開特定的作業來更新資料到這類資料行。 這類作業的名稱是 Update_\<LOBColName\>。 例如，如果介面資料表的資料行，FILE_DATA，BLOB 類型的配接器會公開**Update_FILE_DATA**作業。 CLOB，並且 NCLOB 配接器在介面資料表有一個以上的資料行的 BLOB 類型，如果會公開多個數目 Update_\<LOBColName\>作業。 請注意，更新作業不支援的型別 BFILE 資料行上。  
  
6. 依序展開**介面檢視**節點以查看所有 Oracle E-business Suite 應用程式。 展開 Oracle E-business suite 應用程式來列出屬於該應用程式的所有介面檢視。 按一下介面檢視名稱，以檢視中檢視可用的作業**可用的類別和作業** 方塊中。  
  
   > [!NOTE]
   >  如果介面檢視包含 BLOB 類型的資料行、 CLOB、 NCLOB、 或 BFILE 配接器也會公開這類資料行中讀取資料的特定作業。 這類作業的名稱是 Read_\<LOBColName\>。 例如，如果介面檢視具有資料行，FILE_CONTENT，BLOB 類型的配接器會公開**Read_FILE_CONTENT**作業。 CLOB、 NCLOB、 或 BFILE 配接器如果介面檢視的 BLOB 類型的多個資料行，會公開多個數目 Read_\<LOBColName\>作業。 請注意該 Update_\<LOBColName\>檢視上不支援作業。  
  
7. 依序展開**並行程式**節點以查看所有 Oracle E-business Suite 應用程式。 按一下 [Oracle E-business suite 應用程式來列出屬於該應用程式中的所有並行程式**可用的類別和作業**] 方塊中。  
  
   > [!IMPORTANT]
   >  [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] (或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]) 會顯示並行程式的易記名稱。 不過，並行處理程式的中繼資料會有並行處理程式的實際名稱。 例如，應收帳款應用程式包含 「 客戶介面 」 的並行處理程式。 不過，中繼資料會有並行的程式名稱為 RACUST，也就是並行處理程式的實際名稱。  
  
8. 依序展開**要求集**節點以查看所有 Oracle E-business Suite 應用程式。 按一下 [Oracle E-business suite 應用程式來列出屬於該應用程式中的所有要求集**可用的類別和作業**] 方塊中。  
  
   > [!IMPORTANT]
   >  [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] (或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]) 會顯示要求集的好記名稱。 不過，要求集的中繼資料具有要求集的實際名稱。 比方說，應用程式 DBA 應用程式會包含"DownloadPatches 」 要求集。 不過，中繼資料具有要求集名稱為 FNDRSSUB1623，這是實際要求集的名稱。  
  
9. 依序展開**PL-SQL Api**節點以查看目前的使用者結構描述 （與您登入） 和基礎的 Oracle 資料庫中所定義的所有其他結構描述的類別目錄節點。 依序展開**目前的結構描述 (\<結構描述名稱\>)** 節點，查看針對該結構描述定義的所有封裝。 按一下封裝名稱，若要查看的函式和程序中的封裝內**可用的類別和作業** 方塊中。  
  
     ![瀏覽 Oracle 資料庫中的套件](../../adapters-and-accelerators/adapter-oracle-ebs/media/7a9dc061-db0b-4a8e-bfc6-3a003ad687d8.gif "7a9dc061-db0b-4a8e-bfc6-3a003ad687d8")  
  
     同樣地，依序展開**所有結構描述**節點以查看在 Oracle 資料庫中定義的所有結構描述的清單。 展開結構描述節點，以查看針對該結構描述定義的套件清單。 按一下封裝名稱，若要查看的函式和程序中的封裝內**可用的類別和作業** 方塊中。  
  
     ![瀏覽所有結構描述的 Oracle 資料庫中的套件](../../adapters-and-accelerators/adapter-oracle-ebs/media/09a4841b-b88f-490d-a49a-94e392b5493c.gif "09a4841b-b88f-490d-a49a-94e392b5493c")  
  
10. 依序展開**程序**節點以查看目前的使用者結構描述 （與您登入） 和基礎的 Oracle 資料庫中所定義的所有其他結構描述的類別目錄節點。 按一下 [**目前的結構描述 (\<結構描述名稱\>)** 節點以查看針對該結構描述中定義的所有程序**可用分類和作業**] 方塊中。  
  
     ![瀏覽 Oracle 資料庫結構描述中的程序](../../adapters-and-accelerators/adapter-oracle-ebs/media/6d78563a-53f7-45cc-8652-f40d4703bdf4.gif "6d78563a-53f7-45cc-8652-f40d4703bdf4")  
  
     同樣地，依序展開**所有結構描述**節點以查看在 Oracle 資料庫中定義的所有結構描述的清單。 按一下 [結構描述節點，以查看針對該結構描述中定義的程序的清單**可用的類別和作業**] 方塊中。  
  
     ![瀏覽 Oracle 資料庫結構描述中的程序](../../adapters-and-accelerators/adapter-oracle-ebs/media/a514d199-d6c1-44a0-bf6b-28ddf702081a.gif "a514d199-d6c1-44a0-bf6b-28ddf702081a")  
  
11. 依序展開**函式**節點以查看目前的使用者結構描述 （與您登入） 和基礎的 Oracle 資料庫中所定義的所有其他結構描述的類別目錄節點。 按一下 [**目前的結構描述 (\<結構描述名稱\>)** 節點以查看針對該結構描述中定義的所有函式**可用分類和作業**] 方塊中。  
  
     ![瀏覽 Oracle 資料庫結構描述中的函式](../../adapters-and-accelerators/adapter-oracle-ebs/media/22c1cabf-9754-4ecd-be37-dbeeb7a6a8fd.gif "22c1cabf-9754-4ecd-be37-dbeeb7a6a8fd")  
  
     同樣地，依序展開**所有結構描述**節點以查看在 Oracle 資料庫中定義的所有結構描述的清單。 按一下 [結構描述節點，以查看針對該結構描述中定義的函式的清單**可用的類別和作業**] 方塊中。  
  
     ![瀏覽所有結構描述的 Oracle 資料庫中的函式](../../adapters-and-accelerators/adapter-oracle-ebs/media/b4d29036-3d37-4a50-82c2-3532adbe2875.gif "b4d29036-3d37-4a50-82c2-3532adbe2875")  
  
12. 依序展開**資料表**節點以查看目前的使用者結構描述 （與您登入） 和基礎的 Oracle 資料庫中所定義的所有其他結構描述的類別目錄節點。 依序展開**目前的結構描述 (\<結構描述名稱\>)** 節點以查看針對該結構描述定義的所有資料表。 按一下資料表名稱，以查看在該資料表上支援的作業**可用的類別和作業** 方塊中。  
  
     ![瀏覽 Oracle 資料庫結構描述中的資料表](../../adapters-and-accelerators/adapter-oracle-ebs/media/6ba7420f-9893-4b3e-91cb-10f29d725ad3.gif "6ba7420f-9893-4b3e-91cb-10f29d725ad3")  
  
     同樣地，依序展開**所有結構描述**節點以查看在 Oracle 資料庫中定義的所有結構描述的清單。 展開結構描述節點，以查看針對該結構描述定義資料表的清單。 按一下資料表名稱，以查看在該資料表上支援的作業**可用的類別和作業** 方塊中。  
  
     ![瀏覽 Oracle 資料庫資料表以尋找所有結構描述](../../adapters-and-accelerators/adapter-oracle-ebs/media/d7c52ab4-ba27-404a-9db6-32b2a635ad2f.gif "d7c52ab4-ba27-404a-9db6-32b2a635ad2f")  
  
    > [!NOTE]
    >  如果資料表包含 BLOB 類型的資料行、 CLOB、 NCLOB、 或 BFILE 配接器也會公開這類資料行中讀取資料的特定作業。 這類作業的名稱是 Read_\<LOBColName\>。 例如，如果資料表有資料行，而相片，BLOB 類型的配接器會公開**Read_PHOTO**作業。 如果資料表有一個以上的資料行的 BLOB 類型，CLOB、 NCLOB、 和 BFILE 配接器會公開多個數目 Read_\<LOBColName\>作業。  
    >   
    >  同樣地，如果資料表包含 BLOB 類型的資料行、 CLOB、 或 NCLOB 配接器也會公開特定作業來更新資料到這類資料行。 這類作業的名稱是 Update_\<LOBColName\>。 例如，如果資料表有資料行，而相片，BLOB 類型的配接器會公開**Update_PHOTO**作業。 如果資料表有一個以上的資料行的 BLOB 類型，CLOB，並且 NCLOB 配接器會公開多個數目 Update_\<LOBColName\>作業。 請注意，更新作業不支援的型別 BFILE 資料行上。  
  
13. 依序展開**檢視**節點以查看目前的使用者結構描述 （與您登入） 和基礎的 Oracle 資料庫中所定義的所有其他結構描述的類別目錄節點。 依序展開**目前的結構描述 (\<結構描述名稱\>)** 節點以查看所定義的所有檢視。 按一下 [檢視名稱可查看在該檢視上支援的作業**可用的類別和作業**] 方塊中。  
  
     ![瀏覽 Oracle 資料庫中目前的結構描述中的檢視](../../adapters-and-accelerators/adapter-oracle-ebs/media/2a38cfed-007d-431a-af60-c9c8be5369ab.gif "2a38cfed-007d-431a-af60-c9c8be5369ab")  
  
     同樣地，依序展開**所有結構描述**節點以查看在 Oracle 資料庫中定義的所有結構描述的清單。 展開結構描述節點，以查看該結構描述定義檢視的清單。 按一下 [檢視名稱可查看在該檢視上支援的作業**可用的類別和作業**] 方塊中。  
  
     ![瀏覽所有結構描述的 Oracle 資料庫中的檢視](../../adapters-and-accelerators/adapter-oracle-ebs/media/67ca336c-62ac-4374-87da-07cf331ea4ad.gif "67ca336c-62ac-4374-87da-07cf331ea4ad")  
  
    > [!NOTE]
    >  如果檢視包含 BLOB 類型的資料行、 CLOB、 NCLOB、 或 BFILE 配接器也會公開這類資料行中讀取資料的特定作業。 這類作業的名稱是 Read_\<LOBColName\>。 例如，如果檢視有一個資料行，類型的 BLOB 的規則，配接器會公開**Read_RULE**作業。 如果檢視有一個以上的資料行的類型 BLOB、 CLOB、 NCLOB、 或 BFILE 配接器會公開 Read_ 的多個數目\<LOBColName\>作業。 請注意該 Update_\<LOBColName\>檢視上不支援作業。  
  
## <a name="browsing-for-inbound-operations"></a>瀏覽的輸入操作  
 執行下列步驟來瀏覽 以檢視成品形式的輸入的作業。  
  
#### <a name="to-browse-metadata-for-inbound-operations-under-the-artifact-based-view"></a>若要瀏覽以檢視成品形式的輸入作業的中繼資料  
  
1. 連接到 Oracle E-business Suite 使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 請參閱[連接到 Oracle E-business Suite，在 Visual Studio 中](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-the-oracle-e-business-suite-in-visual-studio.md)如需相關指示。  
  
2. 從**選取合約的型別**清單中，輸入的作業選取**服務 （輸入作業）**。  
  
3. **選取一個類別**方塊會列出 Oracle E-business Suite 成品的分類所在的不同檢視。  
  
    下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。 選取根節點 （/），且一般分類可用的節點的根節點下所述**可用的類別和作業** 方塊中。  
  
    ![輸入根層級的作業](../../adapters-and-accelerators/adapter-oracle-ebs/media/9f9f95f3-c6cc-415c-b534-d5f1ad1963d5.gif "9f9f95f3-c6cc-415c-b534-d5f1ad1963d5")  
  
    輸入的作業，**通知**，也會提供根層級。  
  
4. 依序展開**成品為基礎的檢視**節點以查看針對 Oracle E-business Suite 和基礎資料庫的成品的類別。 根據其所屬 （適用於 Oracle-E-business Suite 成品，例如介面資料表和介面檢視） 的應用程式或 （適用於 Oracle 資料庫成品，例如 PL-SQL Api，程序、 函式所屬的結構描述進一步分類每個類別目錄資料表和檢視表）。  
  
   > [!TIP]
   >  您可以直接移至 「 立即 」 的類別目錄節點或子類別目錄節點樹狀目錄中，輸入時的焦點所在的樹狀檢視中的成品名稱**選取一個類別** 方塊中。 例如，若要跳至**程序**節點，專注**成品的檢視形式**節點，然後按`Procedures`。  
   > 
   > [!NOTE]
   >  [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]不介面同時執行的程式，要求輸入作業的集。  
  
5. 展開 Oracle 應用程式以查看介面資料表和介面檢視適用於該應用程式的類別。 依序展開**Interface Table**並**介面檢視**節點，以查看介面資料表和介面檢視尋找 Oracle 應用程式。 按一下以查看輸入的作業使用資料表或檢視中的介面資料表或介面檢視**可用的類別和作業** 方塊中。  
  
    在下圖中，介面會選取檢視中**選取一個類別** 方塊中輸入的作業，支援在檢視上就會列在**可用的類別和作業** 方塊中。  
  
    ![介面檢視上的輸入操作](../../adapters-and-accelerators/adapter-oracle-ebs/media/937f46f2-d142-413f-8744-2180c7116fd4.gif "937f46f2-d142-413f-8744-2180c7116fd4")  
  
6. 依序展開**PL-SQL Api**節點以查看目前的使用者結構描述 （與您登入） 和基礎的 Oracle 資料庫中所定義的所有其他結構描述的類別目錄節點。 依序展開**目前的結構描述 (\<結構描述名稱\>)** 節點，查看針對該結構描述定義的所有封裝。 按一下封裝名稱，若要查看的函式和程序中的封裝內**可用的類別和作業** 方塊中。 每個所列出函式和程序可用於輪詢 Oracle 資料庫。  
  
    ![瀏覽 PL&#45;在 Oracle 中的 SQL Api 資料庫進行輪詢](../../adapters-and-accelerators/adapter-oracle-ebs/media/4b31ea85-9c5a-42b4-82b2-2cb6d3ead35a.gif "4b31ea85-9c5a-42b4-82b2-2cb6d3ead35a")  
  
    同樣地，依序展開**所有結構描述**節點以查看在 Oracle 資料庫中定義的所有結構描述的清單。 展開結構描述節點，以查看針對該結構描述定義的套件清單。 按一下封裝名稱，若要查看的函式和程序中的封裝內**可用的類別和作業** 方塊中。 每個所列出函式和程序可用於輪詢 Oracle 資料庫。  
  
    ![瀏覽 PL&#45;SQL Api 進行輪詢的所有結構描述](../../adapters-and-accelerators/adapter-oracle-ebs/media/e28a803e-fcfb-4021-9225-924d54a484c0.gif "e28a803e-fcfb-4021-9225-924d54a484c0")  
  
7. 依序展開**程序**節點以查看目前的使用者結構描述 （與您登入） 和基礎的 Oracle 資料庫中所定義的所有其他結構描述的類別目錄節點。 按一下 [**目前的結構描述 (\<結構描述名稱\>)** 節點以查看針對該結構描述中定義的所有程序**可用分類和作業**] 方塊中。 每個列出的程序可用於輪詢 Oracle 資料庫。  
  
    ![瀏覽程序進行輪詢的所有結構描述](../../adapters-and-accelerators/adapter-oracle-ebs/media/5e78da80-d99a-44d3-8eac-f636828f8ceb.gif "5e78da80-d99a-44d3-8eac-f636828f8ceb")  
  
    同樣地，依序展開**所有結構描述**節點以查看在 Oracle 資料庫中定義的所有結構描述的清單。 按一下 [結構描述節點，以查看針對該結構描述中定義的程序的清單**可用的類別和作業**] 方塊中。 每個列出的程序可用於輪詢 Oracle 資料庫。  
  
    ![瀏覽輪詢 Oracle 資料庫中的程序](../../adapters-and-accelerators/adapter-oracle-ebs/media/22d8e866-ed19-49f4-a6eb-683343b16cf5.gif "22d8e866-ed19-49f4-a6eb-683343b16cf5")  
  
8. 依序展開**函式**節點以查看目前的使用者結構描述 （與您登入） 和基礎的 Oracle 資料庫中所定義的所有其他結構描述的類別目錄節點。 按一下 [**目前的結構描述 (\<結構描述名稱\>)** 節點以查看針對該結構描述中定義的所有函式**可用分類和作業**] 方塊中。 每個所列出函式可用來輪詢 Oracle 資料庫。  
  
    ![瀏覽輪詢 Oracle 資料庫中的函式](../../adapters-and-accelerators/adapter-oracle-ebs/media/64c0a30d-a2d6-4dee-90cb-a7e7e2bf62cf.gif "64c0a30d-a2d6-4dee-90cb-a7e7e2bf62cf")  
  
    同樣地，依序展開**所有結構描述**節點以查看在 Oracle 資料庫中定義的所有結構描述的清單。 按一下 [結構描述節點，以查看針對該結構描述中定義的函式的清單**可用的類別和作業**] 方塊中。  每個所列出函式可用來輪詢 Oracle 資料庫。  
  
    ![瀏覽輪詢 Oracle 資料庫中的函式](../../adapters-and-accelerators/adapter-oracle-ebs/media/1d22c3c8-8c24-4905-8144-bdb4840244f1.gif "1d22c3c8-8c24-4905-8144-bdb4840244f1")  
  
9. 依序展開**資料表**節點以查看目前的使用者結構描述 （與您登入） 和基礎的 Oracle 資料庫中所定義的所有其他結構描述的類別目錄節點。 依序展開**目前的結構描述 (\<結構描述名稱\>)** 節點以查看針對該結構描述定義的所有資料表。 按一下資料表名稱，以查看**輪詢**輸入該資料表中支援的作業**可用的類別和作業** 方塊中。  
  
     ![瀏覽輪詢 Oracle 資料庫中的資料表](../../adapters-and-accelerators/adapter-oracle-ebs/media/7c60dfbf-3836-4e72-abe8-5f32a0936807.gif "7c60dfbf-3836-4e72-abe8-5f32a0936807")  
  
     同樣地，依序展開**所有結構描述**節點以查看在 Oracle 資料庫中定義的所有結構描述的清單。 展開結構描述節點，以查看針對該結構描述定義資料表的清單。 按一下資料表名稱，以查看**輪詢**輸入該資料表中支援的作業**可用的類別和作業** 方塊中。  
  
     ![瀏覽輪詢 Oracle 資料庫中的資料表](../../adapters-and-accelerators/adapter-oracle-ebs/media/c5fbaf59-2e79-4141-8a85-1e1b8eedcea7.gif "c5fbaf59-2e79-4141-8a85-1e1b8eedcea7")  
  
10. 依序展開**檢視**節點以查看目前的使用者結構描述 （與您登入） 和基礎的 Oracle 資料庫中所定義的所有其他結構描述的類別目錄節點。 依序展開**目前的結構描述 (\<結構描述名稱\>)** 節點以查看所定義的所有檢視。 按一下 [檢視名稱，以查看**輪詢**輸入該檢視中支援的作業**可用的類別和作業**] 方塊中。  
  
     ![瀏覽輪詢 Oracle 資料庫中的檢視](../../adapters-and-accelerators/adapter-oracle-ebs/media/2299de79-9f50-433d-9e71-164f6d02bd78.gif "2299de79-9f50-433d-9e71-164f6d02bd78")  
  
     同樣地，依序展開**所有結構描述**節點以查看在 Oracle 資料庫中定義的所有結構描述的清單。 展開結構描述節點，以查看該結構描述定義檢視的清單。 按一下 [檢視名稱，以查看**輪詢**輸入該檢視中支援的作業**可用的類別和作業**] 方塊中。  
  
     ![瀏覽輪詢 Oracle 資料庫中的檢視](../../adapters-and-accelerators/adapter-oracle-ebs/media/860e6636-1ef6-42ad-a0e2-d661e632b624.gif "860e6636-1ef6-42ad-a0e2-d661e632b624")  
  
## <a name="see-also"></a>另請參閱  
 [瀏覽、 搜尋及取得 Oracle E-business Suite 作業的中繼資料](../../adapters-and-accelerators/adapter-oracle-ebs/browse-search-and-get-metadata-for-oracle-e-business-suite-operations.md)