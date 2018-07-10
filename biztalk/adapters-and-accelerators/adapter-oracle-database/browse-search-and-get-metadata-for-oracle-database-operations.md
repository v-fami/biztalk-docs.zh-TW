---
title: 瀏覽、 搜尋及取得 Oracle 資料庫作業的中繼資料 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF client, generating a
- operations, browsing for
- metadata, browsing
- browse, for operations
- schema, generating
- metadata, retrieving
- browse, metadata
- retrieve, metadata
- operations, searching for
- WCF service contract, generating a
- metadata, browsing, searching, and retrieving
ms.assetid: 65bd59e0-771d-40fe-966c-8cc8a629ce47
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ab8c821f489a510d87fa06546f45a319608b5065
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37005351"
---
# <a name="browse-search-and-get-metadata-for-oracle-database-operations"></a>瀏覽、 搜尋及取得 Oracle 資料庫作業的中繼資料
本節提供有關如何使用資訊[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，和[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]。 透過使用這些[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]元件，您可以：  
  
- 瀏覽作業為其擷取中繼資料。  
  
- 搜尋用來擷取中繼資料的作業。  
  
- 新增選取的作業的訊息結構描述和通訊埠繫結至 BizTalk server 專案的組態檔，使用時[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。  
  
- 將 WCF 用戶端類別或選取的作業和組態檔 (app.config) 的 WCF 服務合約 （介面） 新增至非 BizTalk 的程式設計專案，當使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
  您可以瀏覽、 搜尋，或擷取目標作業的中繼資料之前，您必須連接到 Oracle 資料庫。 如需如何連接到 Oracle 資料庫使用時[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]或是[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，請參閱[連接至 Visual Studio 中的 Oracle 資料庫](../../adapters-and-accelerators/adapter-oracle-database/connect-to-oracle-database-in-visual-studio.md)。  
  
> [!NOTE]
> - [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，和[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]呈現基本上相同的介面，當您瀏覽和搜尋作業，因此所有三個元件所述的相同的主題。  
>   -   您可以選取類別目錄節點，以傳回該類別目錄子樹狀目錄中的所有作業 — 比方說，整個資料表或結構描述 （或結構描述中的所有資料表）。  
  
## <a name="browsing-for-operations"></a>瀏覽作業  
 在瀏覽中繼資料使用時[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]或是[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，則[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]介面：  
  
-   可對資料表、 檢視、 預存程序、 函數和封裝的作業。  
  
-   SQLEXECUTE 作業，可讓配接器用戶端執行的 Oracle 資料庫中的任何一般資料操作語言 (DML) 或預存程序。  
  
-   POLLINGSTMT 和通知的作業，可取得輸入的資料從 Oracle 資料庫配接器用戶端。 它也會公開預存程序、 函式和以進行輪詢作業所公開的個別結構描述底下的封裝的清單。  
  
> [!NOTE]
> - 藉由使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，您可以瀏覽類別] 和 [作業] 節點使用 Windows 介面。  
>   -   SQLEXECUTE、 POLLINGSTMT 和通知的作業會直接在類別目錄樹狀結構中的根節點下。 您必須選取要檢視這些輸入和輸出作業的根節點。  
  
 如需有關瀏覽中繼資料的詳細資訊，請參閱[取得 Visual Studio 中的 Oracle 資料庫作業的中繼資料](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md)  
  
 執行下列步驟來瀏覽 Oracle 資料庫使用的不同成品公開的作業[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]或[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。  
  
#### <a name="to-browse-metadata-in-an-oracle-database"></a>若要瀏覽 Oracle 資料庫中的中繼資料  
  
1. 連接到 Oracle 資料庫使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 請參閱[連接到 Visual Studio 中的 Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/connect-to-oracle-database-in-visual-studio.md)如需相關指示。  
  
2. 從**選取合約的型別**下拉式清單中，選取 根據是否將會執行使用配接器的輸入或輸出作業的合約型別。  
  
3. **選取一個類別** 方塊中列出的 Oracle 資料庫中的結構描述。 按一下 [結構描述，以查看資料表、 程序、 函式、 封裝，以及檢視中的結構描述必須能夠**可用的類別和作業**] 方塊中。 或者，您可以看到分類方法是展開的結構描述節點。  
  
   > [!TIP]
   >  您可以直接移至 「 立即 」 的類別目錄節點或子類別目錄節點樹狀目錄中，當焦點的樹狀檢視中，輸入在成品名稱**選取一個類別** 方塊中。 例如，若要跳至**SCOTT**節點，將焦點保持在根節點，然後輸入`SCOTT`。  
  
    下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。 SCOTT 結構描述節點，並選取 SCOTT 節點下，您可以使用一般分類節點都會列入**可用的類別和作業** 方塊中。  
  
    ![瀏覽 Oracle 資料庫中的使用者](../../adapters-and-accelerators/adapter-oracle-database/media/c6e02d12-278b-4419-8c8d-d12d0d64f325.gif "c6e02d12-278b-4419-8c8d-d12d0d64f325")  
  
4. 按一下 [**表格**節點，查看資料表中的 scott**可用的類別和作業**] 方塊中。 或者，您可以看到資料表清單，展開**資料表**節點。  
  
5. 按一下資料表名稱，若要查看支援的資料表作業。  
  
    下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。 SCOTT 結構描述中可用的資料表都會列入**選取一個類別** 方塊中。 EMP 資料表中可用的作業都會列入**可用的類別和作業** 方塊中。  
  
    ![瀏覽 Oracle 資料庫中的資料表](../../adapters-and-accelerators/adapter-oracle-database/media/6df61a2f-3cd9-486c-9bf5-7968f8f1ce8d.gif "6df61a2f-3cd9-486c-9bf5-7968f8f1ce8d")  
  
6. 按一下 **程序**若要列出可存取至 SCOTT 的結構描述的程序 節點中**可用的類別和作業** 方塊中。  
  
    下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。 一般分類可用的節點 SCOTT 結構描述中所述**選取一個類別** 方塊中。 SCOTT 結構描述中提供的程序所述**可用的類別和作業** 方塊中。  
  
    ![瀏覽 Oracle 資料庫中的程序](../../adapters-and-accelerators/adapter-oracle-database/media/9826e160-5295-4fdc-bd82-ccd456d89242.gif "9826e160-5295-4fdc-bd82-ccd456d89242")  
  
7. 按一下 [**函式**節點，以查看結構描述 SCOTT 函式中**可用的類別和作業**] 方塊中。  
  
    下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。 一般分類可用的節點 SCOTT 結構描述中所述**選取一個類別** 方塊中。 SCOTT 結構描述中可用的函式所示**可用的類別和作業** 方塊中。  
  
    ![瀏覽 Oracle 資料庫中的函式](../../adapters-and-accelerators/adapter-oracle-database/media/ae02731e-7f26-4552-8e40-db797885af01.gif "ae02731e-7f26-4552-8e40-db797885af01")  
  
8. 按一下 [**封裝**節點，查看結構描述 SCOTT 封裝中**可用的類別和作業**] 方塊中。 或者，您可以看到的封裝清單，展開**封裝**節點。  
  
9. 按一下封裝名稱，若要查看支援封裝上的作業。  
  
     下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，其中會列出封裝以及特定的套件，SCOTT 結構描述支援的作業。  
  
     ![瀏覽 Oracle 資料庫中的套件](../../adapters-and-accelerators/adapter-oracle-database/media/bts-r2-net-adapter-oracle-tut1-browse-pckgs.gif "bts_R2_NET_Adapter_Oracle_Tut1_Browse_Pckgs")  
  
10. 按一下 [**檢視**節點，請參閱 SCOTT 的結構描述的檢視中**可用的類別和作業**] 方塊中。 或者，您可以看到檢視清單中的，展開**檢視**節點。  
  
11. 按一下檢視名稱，若要查看支援在檢視上的作業。  
  
     下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，其中會列出檢視，並針對特定的檢視中，SCOTT 結構描述支援的作業。  
  
     ![瀏覽 Oracle 資料庫中的檢視](../../adapters-and-accelerators/adapter-oracle-database/media/cc1079bc-c1ca-4c2b-a291-abf87bf1ac4d.gif "cc1079bc-c1ca-4c2b-a291-abf87bf1ac4d")  
  
    > [!NOTE]
    >  配接器用戶端可以使用 WCF 通道與服務模型，來指定批次大小來批次擷取的中繼資料。  
  
## <a name="searching-for-operations"></a>搜尋作業  
 搜尋 Oracle 中繼資料使用時[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，則[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]:  
  
- 搜尋運算式中支援萬用字元和逸出字元。  
  
- 在其中執行搜尋作業的節點下的可搜尋。 例如，若要搜尋函式，您必須搜尋下\\[Schema] \Functions。 不支援多層級的搜尋。  
  
  下表列出可用來搜尋和其解譯的特殊字元[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。  
  
|特殊字元|解譯|  
|-----------------------|--------------------|  
|_ (底線)|完全符合一個字元<br /><br /> 比方說，A_ 比對 AB、 AC、 AD。|  
|%（百分比）|比對零或多個字元。<br /><br /> 例如，%比對的 AB，ABC。|  
|\ （逸出）|逸出的特殊意義的 %和 _<br /><br /> 例如，A\\_km 符合 A_B。|  
  
> [!NOTE]
>  Put 之前使用萬用字元來表示，應該將萬用字元解譯成正規字元，而不是萬用字元的字元逸出字元。  
  
 如需詳細資訊，請參閱[取得 Visual Studio 中的 Oracle 資料庫作業的中繼資料](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md)  
  
#### <a name="to-search-metadata-in-an-oracle-database"></a>搜尋 Oracle 資料庫中的中繼資料  
  
1. 連接到 Oracle 資料庫使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 請參閱[連接到 Visual Studio 中的 Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/connect-to-oracle-database-in-visual-studio.md)如需相關指示。  
  
2. 在  [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，從**選取合約的型別**下拉式清單中，選取 根據不論您將會搜尋使用配接器的輸入或輸出作業的合約型別。  
  
3. 在 **選取一個類別**方塊中，按一下包含資料表、 程序、 函式、 封裝和您想要搜尋的檢視表的結構描述。 如果您不確定要按一下 結構描述，請按一下 根 節點。  
  
4. 在 **類別中的搜尋**文字中，輸入要搜尋特定的結構描述的搜尋運算式。 例如，若要搜尋其名稱中含有"SC"的結構描述，請輸入 **%sc**在文字方塊中。  
  
5. 按一下向右箭號圖示，開始搜尋 按鈕。 搜尋完成後**可用的類別和作業**方塊會列出符合搜尋準則的結構描述。  
  
6. 在 **選取一個類別**方塊，展開節點，對應結構描述，然後按一下 資料庫項目，您想要在其中搜尋。 在 **分類中的搜尋**文字方塊中，輸入搜尋運算式來搜尋特定的資料庫項目。  
  
    比方說，若要搜尋名稱中有"EMP"的資料表，請選取**表格**，型別 **%emp**中**類別目錄中的搜尋**文字方塊，然後再按一下的按鈕向右箭號圖示。  
  
    下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，其中會列出搜尋結果。  
  
    ![搜尋 Oracle 資料庫中的中繼資料](../../adapters-and-accelerators/adapter-oracle-database/media/1ee912f8-896e-4b45-ba98-1bbd36b56574.gif "1ee912f8-896e-4b45-ba98-1bbd36b56574")  
  
   > [!NOTE]
   >  配接器用戶端可以使用 WCF 通道與服務模型，來指定執行 batch-wise 搜尋中繼資料的批次大小。  
  
## <a name="generating-schema-using-the-consume-adapter-service-add-in-or-add-adapter-metadata-wizard"></a>產生結構描述使用使用配接器服務增益集，或新增配接器中繼資料精靈  
 您可以使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]來產生結構描述選取的 Oracle 資料庫成品。 一旦您瀏覽並搜尋您想要叫用的成品，您可以產生之成品的結構描述，並傳送訊息，符合結構描述，到 Oracle 資料庫。 執行下列步驟來擷取中繼資料從 Oracle 資料庫使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。  
  
> [!NOTE]
>  您可以選取類別目錄節點，以傳回該類別目錄子樹狀目錄中的所有作業 — 比方說，您可以選取整個資料表 （若要產生的所有作業的結構描述資料表中） 或選取特定的作業 （例如，Insert 和 Delete） 的資料表上至產生結構描述的資料表上的作業。 如需有關節點的詳細資訊，請參閱[中繼資料節點 IDs3](../../adapters-and-accelerators/adapter-oracle-database/metadata-node-ids3.md)。  
  
#### <a name="to-retrieve-metadata-from-an-oracle-database"></a>若要從 Oracle 資料庫擷取中繼資料  
  
1. 連接到 Oracle 資料庫使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。 請參閱[連接到 Visual Studio 中的 Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/connect-to-oracle-database-in-visual-studio.md)如需相關指示。  
  
2. 從**選取合約的型別**下拉式清單中，選取 根據是否將會執行使用配接器的輸入或輸出作業的合約型別。  
  
3. 在 **選取一個類別**方塊中，展開結構描述節點。  
  
4. 選取您要產生中繼資料的類別。 比方說，如果您想要產生資料表的中繼資料，請選取**資料表**。  
  
5. 展開該特定的類別目錄 節點中，然後選取您想要產生中繼資料，該節點內的特定項目。  
  
    例如，若要產生給特定資料表的中繼資料，請展開**資料表**節點，然後選取特定資料表名稱。  
  
   > [!NOTE]
   >  如先前程序中所述，您也可以搜尋的特定資料庫項目。  
  
6. 在 **可用的類別和作業**方塊中，選取您在上一個步驟中，選取 資料庫 項目與相關的作業，然後按一下**新增**。 選取的作業都會列入**新增的類別和作業** 方塊中。  
  
    下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，其中會列出選取的作業。  
  
    ![從 Oracle 資料庫擷取中繼資料](../../adapters-and-accelerators/adapter-oracle-database/media/d3950566-8720-4c15-8a16-4ade14bf6221.gif "d3950566-8720-4c15-8a16-4ade14bf6221")  
  
    如果您想要產生結構描述的多個作業，可能會有一些重複的項目定義，在這些失敗可能導致編譯 BizTalk 專案的結構描述之間。 例如，假設您用來產生 「 Op1"作業的結構描述。 「 資料 Op1"的結構描述包含複雜資料類型"CT1"的參數。 在您關閉之後產生結構描述的 「 資料 Op1"[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]並重新開啟，以產生結構描述的另一項作業 」 Op2"。 假設"Op2 」 也包含複雜資料類型"CT1"的參數。 您在結束之後[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]編譯專案時，就會發生編譯錯誤，因為複雜資料型別"CT1 」 定義兩次在不同的 XSD 檔案。 在這種情況下，我們建議下列各項：  
  
   - 產生的所有作業的結構描述中的單一執行[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。 這可確保[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]會產生複雜的資料類型"CT1 」 只有一個定義。  
  
   - 如果您想要在每次執行會產生多個作業的結構描述[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，請確定您已選取**產生唯一的結構描述型別**核取方塊，使所產生的 XSD 檔案包含複雜的唯一命名空間資料類型"CT1 」。  
  
7. 按一下 [確定] 。 結構描述檔案會儲存具有.xsd 副檔名為 BizTalk 專案的所在位置。  
  
    根據預設，檔案會建立命名慣例 「 OracleDBBindingSchema\<n\>.xsd"，其中 'n' 可以是 1，2，依此類推，根據建立的結構描述檔案的數目。 或者，您可以提供自訂結構描述檔案名稱中輸入名稱**檔案名稱前置詞**文字方塊。 [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]現在會建立結構描述檔案，命名慣例\<檔案名稱前置詞\>結構描述\<n\>.xsd。  
  
   > [!NOTE]
   >  [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]也會建立包含時所指定的繫結屬性的繫結檔案 （XML 檔案） 產生的作業和 SOAP 動作叫用作業的結構描述。 您可以匯入在 BizTalk Server 管理 主控台中建立 WCF 自訂連接埠的連線 URI，繫結屬性與此繫結檔案和設定的 SOAP 動作。 如需詳細資訊，請參閱 <<c0> [ 設定為使用 Oracle 資料庫的連接埠繫結檔案的實體連接埠繫結](../../adapters-and-accelerators/adapter-oracle-database/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-database.md)。  
   > 
   > [!IMPORTANT]
   >  使用[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]不會產生繫結檔案。  
  
8. 按一下 [ **檔案** ] 功能表上的 [ **全部儲存**]。  
  
## <a name="generating-a-wcf-client-or-wcf-service-contract-using-the-add-adapter-service-reference-plug-in"></a>產生 WCF 用戶端或 WCF 服務合約使用新增配接器服務參考外掛程式  
 您可以使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]來產生輸出作業的 WCF 用戶端程式碼，或是輸入作業的 WCF 服務程式碼。  
  
#### <a name="to-retrieve-metadata-from-an-oracle-database"></a>若要從 Oracle 資料庫擷取中繼資料  
  
1. 在  [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，從**選取合約的型別**下拉式清單中，選取 根據是否將會執行輸入 (POLLINGSTMT) 或輸出作業的合約型別。  
  
2. 瀏覽或搜尋類別 （例如 Oracle 資料庫資料表），或是您要產生 WCF 用戶端 （或 WCF 服務合約） 的特定作業。   
   例如，若要瀏覽 SCOTT 中的作業。EMP 資料表，在**選取一個類別**方塊：  
  
   1.  展開 [根] 節點 (**/**) 若要查看呈現的 Oracle 資料庫的結構描述。  
  
   2.  在 [根] 節點中，依序展開**SCOTT**節點以查看公開 SCOTT 結構描述的類別。  
  
   3.  底下**SCOTT**節點，展開**資料表**SCOTT 結構描述的節點，查看資料表呈現。  
  
   4.  底下**表格**節點，選取**EMP**節點。 EMP 資料表所呈現的作業都會列入**可用的類別和作業** 方塊中。  
  
3. 在 **可用的類別和作業**方塊中，選取您要產生 WCF 用戶端 （或 WCF 服務合約），然後按一下 類別目錄的作業**新增**。 選取的作業都會列入**新增的類別和作業** 方塊中。  
  
    下圖顯示[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]與 SCOTT 的 Insert 和 Update 作業。選取 EMP 資料表。  
  
    ![已選取 Select 和 Update 作業。] (../../adapters-and-accelerators/adapter-oracle-database/media/4c41ac7b-784a-494c-ac82-c007e22a4fdf.gif "4c41ac7b-784a-494c-ac82-c007e22a4fdf")  
  
   > [!IMPORTANT]
   >  取決於輸出作業 （或類別），您選取多個一個 WCF 用戶端類別可能會產生。 如需詳細資訊，請參閱 <<c0> [ 產生 WCF 用戶端或 Oracle 資料庫解決方案成品的 WCF 服務合約](../../adapters-and-accelerators/adapter-oracle-database/create-a-wcf-client-or-wcf-service-contract-for-oracle-db-solution-artifacts.md)。  
  
4. 在大部分情況下，預設的序列化選項已足夠;不過，如有需要您可以控制所產生的程式碼的幾個層面和序列化程式所使用的類型。 若要設定這些選項：  
  
   1. 按一下 [**進階選項**來開啟**進階選項**] 方塊中。  
  
   2. 在 **進階選項**下方**選擇選項，以產生的 proxy**，選取您想要的選項。 例如，您可以選取是否非同步方法會產生 WCF 用戶端，或停用設定檔的產生。  
  
   3. 底下**序列化程式**選取應該使用的序列化程式。  
  
      下圖顯示**進階選項**隨附的預設選取項目 (**自動**選取如已選取序列化程式和任何其他選項)。  
  
      ![[進階選項] 方塊預設設定](../../adapters-and-accelerators/adapter-oracle-database/media/r2-net-adapters-oracle-msb-advanced-options.gif "R2_NET_Adapters_Oracle_MSB_Advanced_Options")  
  
      您可以在設定的選項**進階選項**方塊會相當於一些可用的選項，當您使用 ServiceModel Metadata Utility Tool (svcutil.exe)。 如需這些選項的詳細資訊，請參閱[ServiceModel Metadata Utility Tool (Svcutil.exe)](https://msdn.microsoft.com/library/aa347733.aspx)。
  
5. 按一下 [確定] 。 [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]儲存 WCF 用戶端類別 （或 WCF 服務介面） 和協助程式程式碼的作業與您選取了您的專案目錄中的類別。 根據預設，也會儲存組態檔。 輸入和輸出作業; 產生稍有不同的檔案如需詳細資訊，請參閱 <<c0> [ 產生 WCF 用戶端或 Oracle 資料庫解決方案成品的 WCF 服務合約](../../adapters-and-accelerators/adapter-oracle-database/create-a-wcf-client-or-wcf-service-contract-for-oracle-db-solution-artifacts.md)。  
  
   您可以選取任何節點中所列**可用的類別和作業** 方塊中。 如果您選取類別節點，則會選取所有位於該節點和其子節點的作業。 例如，若要產生的所有作業的 EMP 資料表中所提出的 WCF 用戶端，您可以選取 [EMP] 節點中;SCOTT 結構描述中產生 WCF 用戶端的所有資料表，您可以選取 [資料表] 節點中;等等。  
  
## <a name="see-also"></a>另請參閱  
[取得 Visual Studio 中的 Oracle 資料庫作業的中繼資料](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md)