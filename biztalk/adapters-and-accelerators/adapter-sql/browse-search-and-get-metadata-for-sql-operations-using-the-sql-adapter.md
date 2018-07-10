---
title: 瀏覽、 搜尋及取得使用 SQL 配接器的 SQL 作業的中繼資料 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cdd5ca6f-30ff-4d32-a656-bbd54b9d072e
caps.latest.revision: 30
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 30f76d18f79206fff217ab080c9e2b052aa4f73b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36971095"
---
# <a name="browse-search-and-get-metadata-for-sql-operations-using-the-sql-adapter"></a>瀏覽、 搜尋及取得使用 SQL 配接器的 SQL 作業的中繼資料
本節提供有關如何使用資訊[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]，則[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，和[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]。 透過使用這些[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]元件，您可以：  
  
- 瀏覽作業為其擷取中繼資料。  
  
- 搜尋用來擷取中繼資料的作業。  
  
- 新增選取的作業的訊息結構描述和連接埠繫結的組態檔來[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]專案時使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。  
  
- 將 WCF 用戶端類別或選取的作業和組態檔 (app.config) 的 WCF 服務合約 （介面） 新增至非 BizTalk 的程式設計專案，當使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
> [!NOTE]
>  [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，則[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，和[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]呈現基本上相同的介面，當您瀏覽和搜尋作業，因此所有三個元件所述的相同的主題。  
  
## <a name="prerequisites"></a>先決條件  
 您可以瀏覽、 搜尋，或擷取目標作業的中繼資料之前，您必須連接到 SQL Server。 如需如何連接到 SQL Server，當您使用的詳細資訊[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，則[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或有[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，請參閱[連接到 SQL Server，在 Visual Studio 中使用 取用配接器服務增益集](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-in-visual-studio-using-the-consume-adapter-service-add-in.md)。  
  
## <a name="browsing-for-operations"></a>瀏覽作業  
 您可以使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，則[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或有[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]瀏覽可以在 SQL Server 上執行的輸入和輸出作業使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  
  
### <a name="outbound-operations"></a>輸出的作業  
 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]可讓用戶端可以執行下列的輸出作業。  
  
- 插入、 選取更新和刪除資料表和檢視上的作業。  
  
- 設定資料表和檢視上的 < column_name > 作業。 這項作業會有的 varchar （max）、 nvarchar （max） 或 varbinary （max） 資料行的資料表上公開。 這類作業可讓大型物件資料流。  
  
- 預存程序，弱式和強型別做為作業。  
  
- 純量和資料表值函式做為作業。  
  
  配接器也會公開一般的傳出作業這類**ExecuteReader**， **ExecuteScalar**，並**ExecuteNonQuery**根層級。  
  
### <a name="inbound-operations"></a>輸入的作業  
 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]可讓用戶端可以執行下列的輸入的作業。  
  
-   **輪詢**從 SQL Server 接收以輪詢為基礎的資料變更訊息的作業。 這項作業所接收的訊息不是強型別。  
  
-   **TypedPolling**從 SQL Server 接收以輪詢為基礎的資料變更訊息的作業。 這項作業所接收的訊息是強型別。  
  
-   **通知**以接收來自 SQL Server 查詢通知的作業。  
  
> [!NOTE]
>  配接器也支援**XmlPolling**輸入來啟用輪詢使用 SELECT 陳述式和含有 FOR XML 子句的預存程序的 SQL Server 資料庫的作業。 不過，配接器不會公開這個特定的輸入的作業。 如需 XmlPolling 的詳細資訊，請參閱[來接收輪詢訊息使用 FOR XML 子句中使用 BizTalk Server 的 SQL SELECT 陳述式](../../adapters-and-accelerators/adapter-sql/receive-polling-messages-using-select-with-for-xml-clause-with-the-sql-adapter.md)。  
  
 如需有關這些作業的詳細資訊，請參閱 <<c0> [ 連接到 SAP 系統使用配接器](../../adapters-and-accelerators/adapter-sap/connect-to-an-sap-system-using-the-adapter.md)。  
  
> [!NOTE]
>  藉由使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，您可以瀏覽類別] 和 [作業] 節點使用 Windows 介面。  
  
 如需有關瀏覽中繼資料的詳細資訊，請參閱 <<c0> [ 取得 Visual Studio 中使用 SQL 配接器中的 SQL Server 作業的中繼資料](../../adapters-and-accelerators/adapter-sql/get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md)。  
  
##### <a name="to-browse-outbound-operations-on-sql-server"></a>若要瀏覽 SQL Server 上的傳出作業  
  
1. 使用 SQL Server 驗證連接[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 請參閱[連接到 SQL Server，在 Visual Studio 中使用 取用配接器服務增益集](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-in-visual-studio-using-the-consume-adapter-service-add-in.md)如需相關指示。  
  
2. 從**選取合約的型別**清單中，選取傳出作業**用戶端 （傳出作業）**。  
  
3. **選取一個類別**方塊會列出您連接到 SQL Server 資料庫中可用的成品。 按一下以檢視該成品中可用的作業成品**可用的類別和作業** 方塊中。  
  
   > [!TIP]
   >  您可以直接移至 「 立即 」 的類別目錄節點或子類別目錄節點樹狀目錄中，輸入時的焦點所在的樹狀檢視中的成品，名稱**選取一個類別** 方塊中。 例如，若要跳至**員工**資料表節點中，將焦點保持在**資料表**節點，然後按`Employee`。  
  
    下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。 選取根節點 （/），且一般分類可用的節點的根節點下所述**可用的類別和作業** 方塊中。  
  
    ![作業與類別可在根層級](../../adapters-and-accelerators/adapter-sql/media/3eef7b99-da8e-4b98-8b14-8e48fd7b3801.gif "3eef7b99-da8e-4b98-8b14-8e48fd7b3801")  
  
   > [!NOTE]
   >  ExecuteReader、 ExecuteScalar 等 ExecuteNonQuery 標準的 SQL Server 作業也會提供根層級中。 如需有關這些作業的詳細資訊，請參閱 <<c0> [ 支援 ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 作業](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-executenonquery-executereader-and-executescalar-operations.md)。  
  
4. 若要查看可用的 SQL Server 資料庫中的程序，請按一下**程序**節點。 在下圖中，**程序** 中選取節點**選取類別目錄** 方塊中，而對應的程序會列在**可用分類和作業方塊**.  
  
    ![瀏覽 SQL Server 中的程序](../../adapters-and-accelerators/adapter-sql/media/e3b1a070-4077-4e4d-bfc7-558df9b8b9d5.gif "e3b1a070-4077-4e4d-bfc7-558df9b8b9d5")  
  
   > [!NOTE]
   >  下面列出的程序的同一組**程序** 節點也會提供下**Strongly-Typed 程序**節點。 不同之處在於結構描述的產生的方式。 在下一個程序**程序** 節點，結構描述是弱型別。 不過，對於在下一個程序**Strongly-Typed 程序** 節點，結構描述強型別。 強型別結構描述是很有用，如果您想要的一項作業的結構描述對應到另一項作業使用 BizTalk 對應工具，因為在建立 BizTalk 專案時可供您在設計階段結構描述。 弱型別程序，程序的結構描述就會收到執行階段的回應訊息的一部分。  
  
5. 若要查看 SQL Server 資料庫中的資料表，請按一下**資料表**節點。 或者，依序展開**資料表**節點。  
  
6. 若要查看支援的資料表作業，請按一下資料表名稱。  
  
    下圖顯示一份資料表中**選取一個類別** 方塊中。 **可用的類別和作業**方塊會列出選取之資料表支援的作業。  
  
    ![瀏覽 SQL Server 資料庫中的資料表](../../adapters-and-accelerators/adapter-sql/media/3966f3b9-85a0-4354-8ed4-da5ae74c9885.gif "3966f3b9-85a0-4354-8ed4-da5ae74c9885")  
  
   > [!NOTE]
   >  如果 SQL Server 資料表中包含的類型 varchar （max）、 nvarchar （max） 和 varbinary （max） 資料行，則配接器也會公開特定的動作，以更新該資料行中的資料。 這項作業的名稱會設定 < column_name >。 比方說，如果資料表有資料行 」 Job_Description"的類型 varchar （max），作業的名稱會是"SetJob_Description 」。  
  
7. 若要查看 SQL Server 資料庫中的檢視，請按一下**檢視**節點。 或者，依序展開**檢視**節點。  
  
8. 若要查看支援在檢視上的作業，按一下 檢視名稱。  
  
    下圖顯示一份檢視中**選取一個類別** 方塊中。 **可用的類別和作業**方塊會列出選取的檢視支援的作業。  
  
    ![瀏覽 SQL Server 資料庫中的檢視](../../adapters-and-accelerators/adapter-sql/media/67362fb2-35fb-4afb-8ff6-e519b26bd187.gif "67362fb2-35fb-4afb-8ff6-e519b26bd187")  
  
   > [!NOTE]
   >  如果檢視包含的類型 varchar （max）、 nvarchar （max） 和 varbinary （max） 資料行，則配接器也會公開特定的動作，以更新該資料行中的資料。 這項作業的名稱會設定 < column_name >。 比方說，如果資料表有資料行 」 Job_Description"的類型 varchar （max），作業的名稱會是"SetJob_Description 」。  
  
9. 若要查看清單中的 SQL Server 資料庫中定義的純量函式**可用的類別和作業**方塊中，按一下**純量函數**節點。  
  
     在下圖中，**純量函式** 中選取節點**選取類別目錄** 方塊中，而對應的函式會列在**可用分類和作業**  方塊中。  
  
     ![瀏覽 SQL Server 中的純量函式](../../adapters-and-accelerators/adapter-sql/media/78b9f720-2cb2-44a8-b8cc-49e4fb608a1f.gif "78b9f720-2cb2-44a8-b8cc-49e4fb608a1f")  
  
10. 若要查看資料表清單值 SQL Server 資料庫中定義的函式**可用的類別和作業**方塊中，按一下**資料表值函式**節點。  
  
     在下圖中，**資料表值函式** 中選取節點**選取類別目錄** 方塊中，而對應的函式會列在**可用分類和作業** 方塊中。  
  
     ![瀏覽 SQL Server 中的資料表值函式](../../adapters-and-accelerators/adapter-sql/media/b007059f-280e-40d7-9553-eca4216296f4.gif "b007059f-280e-40d7-9553-eca4216296f4")  
  
##### <a name="to-browse-inbound-operations-on-sql-server"></a>若要瀏覽 SQL Server 上的輸入的操作  
  
1. 使用 SQL Server 驗證連接[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，則[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 請參閱[連接到 SQL Server，在 Visual Studio 中使用 取用配接器服務增益集](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-in-visual-studio-using-the-consume-adapter-service-add-in.md)如需相關指示。  
  
2. 從**選取合約的型別**清單中的，輸入作業中，選取**服務 （輸入作業）**。  
  
3. 所支援的輸入的作業[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]位於根節點。 按一下以檢視可用的輸入的作業的根節點 （/）。  
  
    ![輸入配接器所支援的作業](../../adapters-and-accelerators/adapter-sql/media/133732c0-ca8f-4e57-8a70-ba4fb561a37b.gif "133732c0-ca8f-4e57-8a70-ba4fb561a37b")  
  
## <a name="searching-for-operations"></a>搜尋作業  
 您可以使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，則[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]搜尋 SQL Server 資料庫中的特定成品。 搜尋 SQL Server 的中繼資料時[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]:  
  
- 搜尋運算式中支援萬用字元和逸出字元。  
  
- 在其中執行搜尋作業的節點下的可搜尋。 例如，若要搜尋資料表，您必須搜尋 \Table 底下。 不支援多層級的搜尋。  
  
  下表列出可用於搜尋成品和其解譯的特殊字元[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  
  
|特殊字元|解譯|範例|  
|-----------------------|--------------------|-------------|  
|_ (底線)|完全符合一個字元|「 A_ 」 比對 AB、 AC、 AD。|  
|%|比對零或多個字元|"%"會比對的 AB，AC。|  
|[ ]|-逸出的特殊意義的 %和 _<br />-指定範圍或集合必須存在的字元|-%[%] %比對所有的名稱包含 %符號。<br />-[-f] 比對所有的名稱，有個字元之間 （包括） 'a' 和 'f'。<br />-[abc] 比對所有的名稱有字元 'a'、 'b' 和 'c'。|  
|[^]|指定的範圍或集合不會出現的字元|-[^ a-f] 比對不會有個字元之間 （且包含） 的所有名稱 'a' 和 'f'。<br />-[^ abc] 比對所有的名稱，並沒有字元 'a'、 'b' 和 'c'。|  
  
> [!NOTE]
>  逸出字元是放前方使用萬用字元來表示，應該將萬用字元解譯成正規字元，而不是萬用字元的字元。  
  
 如需詳細資訊，請參閱 <<c0> [ 取得 Visual Studio 中使用 SQL 配接器中的 SQL Server 作業的中繼資料](../../adapters-and-accelerators/adapter-sql/get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md)。  
  
 若要搜尋的中繼資料在 SQL Server 中使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，執行下列步驟。  
  
#### <a name="to-search-metadata-in-sql-server"></a>若要搜尋 SQL Server 中的 中繼資料  
  
1. 使用 SQL Server 驗證連接[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，則[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 請參閱[連接到 SQL Server，在 Visual Studio 中使用 取用配接器服務增益集](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-in-visual-studio-using-the-consume-adapter-service-add-in.md)如需相關指示。  
  
2. 從**選取合約的型別**清單中，選取 根據您要搜尋的輸入或輸出作業的合約型別。  
  
3. 在 **選取一個類別**方塊中，按一下您要在其下搜尋特定成品的類別目錄節點。 例如，若要搜尋資料表，請按一下**資料表**節點。  
  
4. 在 **分類中的搜尋**方塊中，輸入要搜尋特定成品的搜尋運算式。 例如，若要搜尋其名稱中含有 「 客戶 」 的資料表，請輸入`%Customer%`。  
  
   > [!NOTE]
   >  搜尋字串會區分大小寫。  
  
5. 若要開始搜尋，請按一下向右箭號圖示的按鈕。 搜尋完成後**可用的類別和作業**方塊會列出符合搜尋準則的成品。  
  
    下圖顯示其名稱中包含 「 客戶 」 的 SQL Server 資料表。  
  
    ![搜尋 SQL Server 中的 中繼資料](../../adapters-and-accelerators/adapter-sql/media/62c24ed3-f4e5-47de-8e8d-35af96e6c5ec.gif "62c24ed3-f4e5-47de-8e8d-35af96e6c5ec")  
  
## <a name="generating-schema-for-biztalk-projects"></a>對於 BizTalk 專案中產生結構描述  
 您可以使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]產生選取的 SQL Server 成品的結構描述。 一旦您瀏覽並搜尋您想要叫用的成品，您可以產生之成品的結構描述，並傳送訊息，符合結構描述，SQL server。  
  
> [!NOTE]
>  您可以選取類別目錄節點，以傳回該類別目錄子樹狀目錄中的所有作業 — 比方說，您可以選取整個資料表 （若要產生的所有作業的結構描述資料表中） 或選取特定的作業 （例如，Insert 和 Delete） 的資料表上至產生結構描述的資料表上的作業。 如需有關節點的詳細資訊，請參閱[中繼資料節點識別碼](../../adapters-and-accelerators/adapter-sql/metadata-node-ids2.md)。  
  
#### <a name="to-generate-schema-for-sql-server-artifacts"></a>若要產生結構描述的 SQL Server 成品  
  
1. 使用 SQL Server 驗證連接[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。 請參閱[連接到 SQL Server，在 Visual Studio 中使用 取用配接器服務增益集](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-in-visual-studio-using-the-consume-adapter-service-add-in.md)如需相關指示。  
  
   > [!IMPORTANT]
   >  若要針對使用執行作業產生結構描述[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，您必須設定**EnableBizTalkCompatibilityMode**繫結屬性，以 **，則為 True**。 建立 SQL Server 資料庫的連接時，您必須設定這個繫結屬性。  
  
2. 從**選取合約的型別**清單中，選取 根據您是否產生結構描述的輸入或輸出作業的合約型別。  
  
3. 按一下您要產生中繼資料的類別目錄節點。 例如，如果您想要產生資料表的中繼資料，按一下**資料表**。  
  
4. 展開 [類別目錄] 節點中，然後選取該節點，您要產生中繼資料內的特定項目。 例如，若要產生 「 CustomerTable 」 資料表上的作業的中繼資料，請展開**資料表**節點，然後再按一下**CustomerTable**。  
  
5. 在 **可用的類別和作業**方塊中，選取您想要執行 SQL Server 上，然後按一下 operations**新增**。 選取的作業都會列入**新增的類別和作業** 方塊中。 比方說，若要執行 Insert 和 Select 作業 」 CustomerTable 」 資料表上的，按一下作業名稱 中，，，然後按一下**新增**。  
  
    下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，其中會列出選取的作業。  
  
    ![從 SQL Server 擷取中繼資料](../../adapters-and-accelerators/adapter-sql/media/a6a95291-f6ed-46d1-bacc-2dfc27638117.gif "a6a95291-f6ed-46d1-bacc-2dfc27638117")  
  
    如果您想要產生結構描述的多個作業，可能會有一些重複的項目定義，在這些失敗可能導致編譯 BizTalk 專案的結構描述之間。 例如，假設您用來產生 「 Op1"作業的結構描述。 「 資料 Op1"的結構描述包含的資料類型"CT1"的參數。 在您關閉之後產生結構描述的 「 資料 Op1"[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]並重新開啟，以產生結構描述的另一項作業 」 Op2"。 假設"Op2 」 也包含資料類型"CT1"的參數。 您在結束之後[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]編譯專案時，就會發生編譯錯誤，因為複雜資料型別"CT1 」 定義兩次在不同的 XSD 檔案。 在這種情況下，我們建議下列各項：  
  
   - 產生的所有作業的結構描述中的單一執行[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。 這可確保[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]會產生複雜的資料類型"CT1 」 只有一個定義。  
  
   - 如果您想要在每次執行會產生多個作業的結構描述[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，請確定您已選取**產生唯一的結構描述型別**核取方塊，使所產生的 XSD 檔案包含用於唯一的命名空間複雜資料型別 」 CT1"。  
  
6. 按一下 [確定] 。 結構描述檔案會儲存具有.xsd 副檔名為 BizTalk 專案的所在位置。  
  
   > [!NOTE]
   >  如果您使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]來產生特定的命名慣例，會建立檔案的預設 SQL Server 構件的中繼資料。 包含產生的 WSDL **fileNameHint**註解標記，其中包含應指派至 XSD 檔案的名稱。 例如，資料表作業的結構描述檔案的檔案名稱提示遵循 TableOperation 的慣例。\<結構描述\>。\<tablename\>。 如果您想要自訂所產生的 XSD 檔案的名稱，您可以提供的前置詞**檔案名稱前置詞** 方塊中。 最後，XSD 檔案的名稱是在抵達為檔案名稱前置詞 + fileNameHint + 唯一整數 （如有必要，以確保檔案名稱是唯一）。  
   > 
   > [!NOTE]
   >  [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]也會建立包含時所指定的繫結屬性的繫結檔案 （XML 檔案） 產生的作業和 SOAP 動作叫用作業的結構描述。 您可以匯入此繫結檔案中的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台來建立 WCF 自訂連接埠] 或 [BizTalk SQL 配接器與連線 URI 的連接埠、 繫結屬性和 SOAP 動作設定。 如需詳細資訊，請參閱 <<c0> [ 設定要使用 SQL 配接器使用的連接埠繫結檔案的實體連接埠繫結](../../adapters-and-accelerators/adapter-sql/configure-a-physical-port-binding-using-a-port-binding-file-to-sql-adapter.md)。
  
    您已經順利產生 SQL Server 構件的中繼資料。 您可以使用中繼資料，將訊息傳送至 SQL Server 來執行特定作業。 請參閱[使用 SQL 配接器開發 BizTalk 應用程式](../../adapters-and-accelerators/adapter-sql/develop-biztalk-applications-using-the-sql-adapter.md)如需有關如何執行這些作業。  
  
## <a name="generating-a-wcf-client-or-wcf-service-contract-using-the-add-adapter-service-reference-plug-in"></a>產生 WCF 用戶端或 WCF 服務合約使用新增配接器服務參考外掛程式  
 您可以使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]來產生輸出作業的 WCF 用戶端程式碼，或是輸入作業的 WCF 服務程式碼。  
  
#### <a name="to-generate-wcf-client-class-or-service-contract-for-sql-server-operations"></a>若要產生 WCF 用戶端類別或服務合約的 SQL Server 作業  
  
1. 在  [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，從**選取合約的型別**下拉式清單中，選取 根據是否將會執行輸入或輸出作業的合約型別。  
  
2. 瀏覽或搜尋類別 （例如資料庫資料表），或是您要產生 WCF 用戶端 （或 WCF 服務合約） 的特定作業。   
   例如，若要瀏覽 Employee 資料表中的作業中**選取一個類別**方塊：  
  
   1.  展開 [根] 節點 (**/**) 以查看作業會顯示 SQL Server 資料庫的類別。  
  
   2.  在 [根] 節點中，依序展開**資料表**節點以查看可用的資料表。  
  
3. 按一下 **員工**資料表節點，然後在**可用的類別和作業**方塊中，選取您想要產生 WCF 用戶端 （或 WCF 服務合約），類別的作業，然後按一下 **新增**。 選取的作業都會列入**新增的類別和作業** 方塊中。  
  
    下圖顯示[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]Insert 與所選的 Employee 資料表的 Select 作業。  
  
    ![產生 WCF 用戶端或服務合約](../../adapters-and-accelerators/adapter-sql/media/sql-adap-add-adap-serv-ref.gif "sql_adap_add_adap_serv_ref")  
  
   > [!IMPORTANT]
   >  取決於輸出作業 （或類別），您選取多個一個 WCF 用戶端類別可能會產生。 如需詳細資訊，請參閱 <<c0> [ 產生的 SQL Server 成品的 WCF 用戶端或 WCF 服務合約](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md)。  
  
4. 在大部分情況下，預設的序列化選項已足夠;不過，如有需要您可以控制所產生的程式碼的幾個層面和序列化程式所使用的類型。 若要設定這些選項：  
  
   1. 按一下 [**進階選項**來開啟**進階選項**] 方塊中。  
  
   2. 在 **進階選項**下方**選擇選項，以產生的 proxy**，選取您想要的選項。 例如，您可以選取是否非同步方法會產生 WCF 用戶端，或停用設定檔的產生。  
  
   3. 底下**序列化程式**選取應該使用的序列化程式。  
  
      下圖顯示**進階選項**隨附的預設選取項目 (**自動**選取如已選取序列化程式和任何其他選項)。  
  
      ![[進階選項] 方塊預設設定](../../adapters-and-accelerators/adapter-oracle-database/media/r2-net-adapters-oracle-msb-advanced-options.gif "R2_NET_Adapters_Oracle_MSB_Advanced_Options")  
  
      您可以在設定的選項**進階選項**方塊會相當於一些可用的選項，當您使用 ServiceModel Metadata Utility Tool (svcutil.exe)。 如需這些選項的詳細資訊，請參閱[ServiceModel Metadata Utility Tool (Svcutil.exe)](https://msdn.microsoft.com/library/aa347733.aspx)。 
  
5. 按一下 [確定] 。 [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]儲存 WCF 用戶端類別 （或 WCF 服務介面） 和協助程式程式碼的作業與您選取了您的專案目錄中的類別。 根據預設，也會儲存組態檔。 輸入和輸出作業; 產生稍有不同的檔案如需詳細資訊，請參閱 <<c0> [ 產生的 SQL Server 成品的 WCF 用戶端或 WCF 服務合約](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md)。  
  
   您可以選取任何節點中所列**可用的類別和作業** 方塊中。 如果您選取類別節點，則會選取所有位於該節點和其子節點的作業。 例如，若要產生的所有作業顯示為 [員工] 資料表的 WCF 用戶端，您可以選取 [員工] 節點。  
  
## <a name="see-also"></a>另請參閱  
 [取得在 Visual Studio 中使用 SQL 配接器的 SQL Server 作業的中繼資料](../../adapters-and-accelerators/adapter-sql/get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md)