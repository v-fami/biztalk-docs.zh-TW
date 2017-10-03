---
title: "瀏覽、 搜尋，並取得中繼資料的 Oracle 資料庫作業 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
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
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8735040dd1cad2df59e18dbb572dad322ec46fcf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="browse-search-and-get-metadata-for-oracle-database-operations"></a>瀏覽、 搜尋和 Oracle 資料庫作業，取得中繼資料
本節提供有關如何使用資訊[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，和[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]。 使用這些[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]元件，您可以：  
  
-   瀏覽要為其擷取中繼資料的作業。  
  
-   搜尋作業為其擷取中繼資料。  
  
-   新增選取的作業的訊息結構描述和通訊埠繫結至 BizTalk server 專案的組態檔，當使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。  
  
-   WCF 用戶端類別或選取的作業和組態檔 (app.config) 的 WCF 服務合約 （介面） 的非 BizTalk 程式設計專案時加入使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
 您可以瀏覽、 搜尋，或擷取目標作業的中繼資料之前，您必須連接到 Oracle 資料庫。 如需如何連接到 Oracle 資料庫使用時[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，請參閱[連接至 Visual Studio 中的 Oracle 資料庫](../../adapters-and-accelerators/adapter-oracle-database/connect-to-oracle-database-in-visual-studio.md)。  
  
> [!NOTE]
>  -   [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，和[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]呈現基本上相同的介面，當您瀏覽和搜尋作業，因此在相同主題中涵蓋三個元件時。  
> -   您可以選取分類節點，以傳回該類別目錄子樹狀目錄中的所有作業，例如，整個資料表或結構描述 （或甚至所有資料表的結構描述）。  
  
## <a name="browsing-for-operations"></a>瀏覽作業  
 在瀏覽中繼資料使用時[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]、[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]介面：  
  
-   可對資料表、 檢視、 預存程序、 函數以及封裝執行的作業。  
  
-   SQLEXECUTE 作業，可讓配接器用戶端執行 Oracle 資料庫中的任何一般資料操作語言 (DML) 或預存程序。  
  
-   POLLINGSTMT 和通知的作業，可讓配接器用戶端從 Oracle 資料庫中取得輸入的資料。 它也會公開預存程序、 函數和封裝會公開為輪詢作業的個別結構描述底下的清單。  
  
> [!NOTE]
>  -   使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，您可以瀏覽使用 Windows 介面的類別和作業節點。  
> -   SQLEXECUTE、 POLLINGSTMT 和通知的作業會顯示類別目錄樹狀結構中的根節點正下方。 您必須選取根節點，即可檢視這些傳出和傳入的作業。  
  
 如需有關瀏覽中繼資料的詳細資訊，請參閱[取得 Visual Studio 中的 Oracle 資料庫作業的中繼資料](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md)  
  
 執行下列步驟來瀏覽 Oracle 資料庫使用中的不同成品公開作業[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]或[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。  
  
#### <a name="to-browse-metadata-in-an-oracle-database"></a>若要瀏覽 Oracle 資料庫中的中繼資料  
  
1.  連接到 Oracle 資料庫使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 請參閱[連接至 Visual Studio 中的 Oracle 資料庫](../../adapters-and-accelerators/adapter-oracle-database/connect-to-oracle-database-in-visual-studio.md)如需相關指示。  
  
2.  從**選取合約型別**下拉式清單中，選取 根據是否將執行使用配接器的輸入或輸出作業的合約的型別。  
  
3.  **選取類別目錄**方塊會列出 Oracle 資料庫中的結構描述。 按一下以查看資料表、 程序、 函數、 封裝和檢視中的結構描述存取結構描述**可用的類別和作業**方塊。 或者，您可以查看分類展開結構描述節點。  
  
    > [!TIP]
    >  您可以直接移至 「 立即 」 的類別目錄節點或子類別目錄節點的樹狀目錄中，輸入中的成品名稱時的焦點所在的樹狀檢閱中**選取類別目錄**方塊。 例如，若要跳至**SCOTT**  節點，將焦點放在根節點，然後輸入`SCOTT`。  
  
     下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。 SCOTT 結構描述節點，並選取 SCOTT 節點下，您可以使用一般分類節點會列出**可用的類別和作業**方塊。  
  
     ![瀏覽 Oracle 資料庫中的使用者](../../adapters-and-accelerators/adapter-oracle-database/media/c6e02d12-278b-4419-8c8d-d12d0d64f325.gif "c6e02d12-278b-4419-8c8d-d12d0d64f325")  
  
4.  按一下**資料表**節點以查看資料表中的 scott**可用的類別和作業**方塊。 或者，您可以看到的資料表清單，方法是展開**資料表**節點。  
  
5.  按一下資料表名稱，才能看到資料表上支援的作業。  
  
     下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。 SCOTT 結構描述中可用的資料表中所列**選取類別目錄**方塊。 作業可用來 EMP 資料表中所列**可用的類別和作業**方塊。  
  
     ![瀏覽 Oracle 資料庫中的資料表](../../adapters-and-accelerators/adapter-oracle-database/media/6df61a2f-3cd9-486c-9bf5-7968f8f1ce8d.gif "6df61a2f-3cd9-486c-9bf5-7968f8f1ce8d")  
  
6.  按一下**程序**節點，以列出結構描述 SCOTT 可以存取的程序中**可用的類別和作業**方塊。  
  
     下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。 一般分類中可用的節點 SCOTT 結構描述中所列**選取類別目錄**方塊。 SCOTT 結構描述中提供的程序所述**可用的類別和作業**方塊。  
  
     ![瀏覽 Oracle 資料庫中的程序](../../adapters-and-accelerators/adapter-oracle-database/media/9826e160-5295-4fdc-bd82-ccd456d89242.gif "9826e160-5295-4fdc-bd82-ccd456d89242")  
  
7.  按一下**函式**節點以查看結構描述 SCOTT 函式中**可用的類別和作業**方塊。  
  
     下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。 一般分類中可用的節點 SCOTT 結構描述中所列**選取類別目錄**方塊。 SCOTT 結構描述中可用函數會列在**可用的類別和作業**方塊。  
  
     ![瀏覽 Oracle 資料庫中的函式](../../adapters-and-accelerators/adapter-oracle-database/media/ae02731e-7f26-4552-8e40-db797885af01.gif "ae02731e-7f26-4552-8e40-db797885af01")  
  
8.  按一下**封裝**節點，查看結構描述 SCOTT 封裝中**可用的類別和作業**方塊。 或者，您可以看到的封裝清單，方法是展開**封裝**節點。  
  
9. 按一下封裝名稱，若要查看支援封裝上的作業。  
  
     下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，其中會列出封裝以及特定套件中，SCOTT 結構描述支援的作業。  
  
     ![瀏覽 Oracle 資料庫中的套件](../../adapters-and-accelerators/adapter-oracle-database/media/bts-r2-net-adapter-oracle-tut1-browse-pckgs.gif "bts_R2_NET_Adapter_Oracle_Tut1_Browse_Pckgs")  
  
10. 按一下**檢視**節點以查看 SCOTT 結構描述檢視中**可用的類別和作業**方塊。 或者，您可以在這裡看到的檢視清單展開**檢視**節點。  
  
11. 按一下檢視名稱，若要查看支援在檢視上的作業。  
  
     下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，其中會列出檢視表，並針對特定的檢視中，SCOTT 結構描述支援的作業。  
  
     ![瀏覽 Oracle 資料庫中的檢視](../../adapters-and-accelerators/adapter-oracle-database/media/cc1079bc-c1ca-4c2b-a291-abf87bf1ac4d.gif "cc1079bc-c1ca-4c2b-a291-abf87bf1ac4d")  
  
    > [!NOTE]
    >  使用 WCF 通道與服務模型，配接器用戶端可以指定批次大小執行批次擷取中繼資料。  
  
## <a name="searching-for-operations"></a>搜尋作業  
 搜尋 Oracle 中繼資料使用時[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]、 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]:  
  
-   搜尋運算式中支援萬用字元和逸出字元。  
  
-   啟用立即節點下搜尋在其中執行搜尋作業。 例如，若要搜尋的函式，您必須搜尋下\\[Schema] \Functions。 不支援多層級的搜尋。  
  
 下表列出可用於搜尋和由其解譯的特殊字元[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。  
  
|特殊字元|解譯|  
|-----------------------|--------------------|  
|_ (底線)|完全符合一個字元<br /><br /> 例如，A_ 比對 AB、 AC、 AD。|  
|%（百分比）|比對零個或多個字元。<br /><br /> 例如，%比對 A，AB，ABC。|  
|\ （逸出）|逸出的特殊意義的 %和 _<br /><br /> 例如，A\\_km 符合 A_B。|  
  
> [!NOTE]
>  逸出字元是會放置在使用萬用字元來表示，應該將萬用字元解譯成正規字元，而不是萬用字元前面的字元。  
  
 如需詳細資訊，請參閱[取得 Visual Studio 中的 Oracle 資料庫作業的中繼資料](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md)  
  
#### <a name="to-search-metadata-in-an-oracle-database"></a>搜尋 Oracle 資料庫中的中繼資料  
  
1.  連接到 Oracle 資料庫使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 請參閱[連接至 Visual Studio 中的 Oracle 資料庫](../../adapters-and-accelerators/adapter-oracle-database/connect-to-oracle-database-in-visual-studio.md)如需相關指示。  
  
2.  在[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，從**選取合約型別**下拉式清單中，選取 根據是否您將會搜尋使用配接器的輸入或輸出作業的合約的型別。  
  
3.  在**選取類別目錄**方塊中，按一下資料表、 程序、 函數、 封裝及您想要搜尋的檢視所包含的結構描述。 如果您不確定要按一下結構描述，請按一下根節點。  
  
4.  在**類別目錄中的搜尋**文字方塊中，輸入要搜尋特定的結構描述的搜尋運算式。 例如，若要搜尋其名稱中含有"SC"的結構描述，請輸入**%sc**在文字方塊中。  
  
5.  按一下向右箭號圖示，開始搜尋 按鈕。 搜尋完成之後，**可用的類別和作業**方塊會列出符合搜尋準則的結構描述。  
  
6.  在**選取類別目錄**方塊，展開節點，對應結構描述，然後再按一下 資料庫項目，您要搜尋。 在**類別目錄中的搜尋**文字方塊中，輸入要搜尋的特定資料庫項目搜尋運算式。  
  
     例如，若要搜尋名稱中有"EMP 」 的資料表，請選取**資料表**，型別**%emp**中**類別目錄中的搜尋**文字方塊，然後再按一下按鈕向右箭號圖示。  
  
     下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，其中會列出搜尋結果。  
  
     ![搜尋 Oracle 資料庫中的中繼資料](../../adapters-and-accelerators/adapter-oracle-database/media/1ee912f8-896e-4b45-ba98-1bbd36b56574.gif "1ee912f8-896e-4b45-ba98-1bbd36b56574")  
  
    > [!NOTE]
    >  使用 WCF 通道與服務模型，配接器用戶端可以指定批次大小執行 batch-wise 搜尋的中繼資料。  
  
## <a name="generating-schema-using-the-consume-adapter-service-add-in-or-add-adapter-metadata-wizard"></a>產生結構描述使用使用配接器服務增益集，或新增配接器中繼資料精靈  
 您可以使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]產生選取的 Oracle 資料庫成品的結構描述。 一旦您瀏覽並搜尋您想要叫用的成品，您可以產生結構描述的那些成品，並傳送訊息，符合結構描述到 Oracle 資料庫。 執行下列步驟來擷取中繼資料從 Oracle 資料庫使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。  
  
> [!NOTE]
>  您可以選取要在該類別目錄子樹狀結構中傳回所有作業類別目錄節點： 例如，您可以選取整個資料表 （若要產生的所有作業的結構描述資料表中） 或選取特定的作業 （例如，Insert 和 Delete） 的資料表上以產生結構描述的資料表上的作業。 如需節點的詳細資訊，請參閱[中繼資料節點 IDs3](../../adapters-and-accelerators/adapter-oracle-database/metadata-node-ids3.md)。  
  
#### <a name="to-retrieve-metadata-from-an-oracle-database"></a>若要從 Oracle 資料庫擷取中繼資料  
  
1.  連接到 Oracle 資料庫使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。 請參閱[連接至 Visual Studio 中的 Oracle 資料庫](../../adapters-and-accelerators/adapter-oracle-database/connect-to-oracle-database-in-visual-studio.md)如需相關指示。  
  
2.  從**選取合約型別**下拉式清單中，選取 根據是否將執行使用配接器的輸入或輸出作業的合約的型別。  
  
3.  在**選取類別目錄**方塊中，展開結構描述節點。  
  
4.  選取您要產生中繼資料的類別。 例如，如果您想要產生資料表的中繼資料中，選取**資料表**。  
  
5.  展開該特定類別目錄 節點，然後選取該節點，您要產生中繼資料內的特定項目。  
  
     例如，若要產生給特定資料表的中繼資料，請展開**資料表**節點，然後選取特定資料表名稱。  
  
    > [!NOTE]
    >  您也可以搜尋特定資料庫的項目，先前的程序中所述。  
  
6.  在**可用的類別和作業**方塊中，選取您在上一個步驟中選取的資料庫項目與相關的作業，然後按一下**新增**。 選取的作業中所列**加入的類別和作業**方塊。  
  
     下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，其中會列出選取的作業。  
  
     ![從 Oracle 資料庫擷取中繼資料](../../adapters-and-accelerators/adapter-oracle-database/media/d3950566-8720-4c15-8a16-4ade14bf6221.gif "d3950566-8720-4c15-8a16-4ade14bf6221")  
  
     如果您想要產生結構描述的多個作業，可能是在這些失敗可能導致編譯 BizTalk 專案的結構描述之間的一些重複的項目定義。 例如，假設您用來產生 「 Op1 」 作業的結構描述。 「 Op1"的結構描述包含複雜資料類型"CT1"的參數。 在您關閉之後產生結構描述的 「 Op1" [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ，再重新開啟 「 Op2"的另一個作業產生結構描述。 假設 「 Op2 」 也包含複雜資料類型"CT1"的參數。 結束之後[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]編譯專案，就會發生編譯錯誤，因為複雜資料型別"CT1 」 定義不同的 XSD 檔案中的兩倍。 在這種情況下，我們建議下列各項：  
  
    -   產生的所有作業的結構描述中的單一執行[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。 如此可確保[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]會產生只有一個定義的複雜資料型別"CT1"。  
  
    -   如果您想要產生多個作業的結構描述的不同執行[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，請確定您選取**產生唯一的結構描述型別**核取方塊，以便讓所產生的 XSD 檔案包含複雜的唯一命名空間資料型別"CT1"。  
  
7.  按一下 **[確定]**。 結構描述檔案會儲存具有.xsd 副檔名為 BizTalk 專案的相同位置。  
  
     根據預設，檔案會建立命名慣例 」 OracleDBBindingSchema\<n >.xsd"，其中 'n' 可以是 1、 2，依此類推，依照建立的結構描述檔案的數目。 或者，您可以提供自訂結構描述檔案名稱中輸入名稱**檔案名稱前置詞**文字方塊。 [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]現在建立結構描述檔案命名慣例\<檔案名稱前置詞 > 結構描述\<n >.xsd。  
  
    > [!NOTE]
    >  [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]也會建立包含時指定的繫結屬性的繫結檔案 （XML 檔案） 產生的結構描述的作業和要叫用作業的 SOAP 動作。 您可以匯入此繫結檔案，在 BizTalk Server 管理主控台中，建立 WCF 自訂連接埠與連接 URI，繫結屬性和設定的 SOAP 動作。 如需詳細資訊，請參閱[設定使用 Oracle 資料庫的連接埠繫結檔案的實體連接埠繫結](../../adapters-and-accelerators/adapter-oracle-database/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-database.md)。  
  
    > [!IMPORTANT]
    >  使用[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]不會產生繫結檔案。  
  
8.  按一下 [ **檔案** ] 功能表上的 [ **全部儲存**]。  
  
## <a name="generating-a-wcf-client-or-wcf-service-contract-using-the-add-adapter-service-reference-plug-in"></a>產生 WCF 用戶端或 WCF 服務合約使用新增配接器服務參考外掛程式  
 您可以使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]來產生傳出作業的 WCF 用戶端程式碼，或是 WCF 服務程式碼的輸入操作。  
  
#### <a name="to-retrieve-metadata-from-an-oracle-database"></a>若要從 Oracle 資料庫擷取中繼資料  
  
1.  在[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，從**選取合約型別**下拉式清單中，選取 根據是否執行的輸入 (POLLINGSTMT) 或輸出作業的合約的型別。  
  
2.  瀏覽或搜尋的類別 （例如 Oracle 資料庫資料表），或是您要產生 WCF 用戶端 （或 WCF 服務合約） 的特定作業。   
    例如，若要瀏覽 SCOTT 中的作業。EMP 表格中，於**選取類別目錄**方塊：  
  
    1.  展開根節點 (**/**) 若要查看 Oracle 資料庫中顯示的結構描述。  
  
    2.  根節點下，依序展開**SCOTT**節點以查看 SCOTT 結構描述所公開的類別。  
  
    3.  在下**SCOTT** ] 節點，展開 [**資料表**SCOTT 結構描述節點，查看資料表中顯示。  
  
    4.  在下**資料表**節點，選取**EMP**節點。 EMP 資料表中顯示的作業中所列**可用的類別和作業**方塊。  
  
3.  在**可用的類別和作業**方塊中，選取您要產生 WCF 用戶端 （或 WCF 服務合約），然後按一下 類別目錄的作業**新增**。 選取的作業中所列**加入的類別和作業**方塊。  
  
     下圖顯示[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]與 SCOTT 的 Insert 和 Update 作業。選取 EMP 資料表。  
  
     ![已選取 Select 和 Update 作業。] (../../adapters-and-accelerators/adapter-oracle-database/media/4c41ac7b-784a-494c-ac82-c007e22a4fdf.gif "4c41ac7b-784a-494c-ac82-c007e22a4fdf")  
  
    > [!IMPORTANT]
    >  取決於輸出作業 （或類別），您選取多個一個 WCF 用戶端類別可能會產生。 如需詳細資訊，請參閱[產生 WCF 用戶端或 WCF 服務合約的 Oracle 資料庫方案成品](../../adapters-and-accelerators/adapter-oracle-database/create-a-wcf-client-or-wcf-service-contract-for-oracle-db-solution-artifacts.md)。  
  
4.  在大部分情況下，預設序列化選項已經足夠;不過，如果需要您可以控制所產生的程式碼的幾個層面和序列化程式所使用的類型。 若要設定這些選項：  
  
    1.  按一下**進階選項**開啟**進階選項**方塊。  
  
    2.  在**進階選項**下方的 **選擇選項來產生 proxy**，選取您想要的選項。 例如，您可以選取是否非同步方法產生 WCF 用戶端，或停用組態檔的產生。  
  
    3.  在下**序列化程式**選取應該使用的序列化程式。  
  
     下圖顯示**進階選項**隨附的預設選項 (**自動**選取所選的序列化程式，且沒有其他選項)。  
  
     ![[進階選項] 方塊預設設定](../../adapters-and-accelerators/adapter-oracle-database/media/r2-net-adapters-oracle-msb-advanced-options.gif "R2_NET_Adapters_Oracle_MSB_Advanced_Options")  
  
     您可以在設定的選項**進階選項**方塊相當於某些可用的選項時使用 ServiceModel Metadata Utility Tool (svcutil.exe)。 如需有關這些選項的詳細資訊，請參閱[ServiceModel Metadata Utility Tool (Svcutil.exe)](https://msdn.microsoft.com/library/aa347733.aspx)。
  
5.  按一下 **[確定]**。 [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] WCF 用戶端類別 （或 WCF 服務介面） 會將儲存和協助程式程式碼的作業和專案目錄中所選取的類別。 根據預設，也會儲存組態檔。 輸入和輸出作業; 產生稍有不同的檔案如需詳細資訊，請參閱[產生 WCF 用戶端或 WCF 服務合約的 Oracle 資料庫方案成品](../../adapters-and-accelerators/adapter-oracle-database/create-a-wcf-client-or-wcf-service-contract-for-oracle-db-solution-artifacts.md)。  
  
 您可以選取任何節點中所列**可用的類別和作業**方塊。 如果您選取類別目錄節點，則會選取所有適用於該節點和其子節點的作業。 比方說，若要產生 WCF 用戶端的所有 EMP 資料表中顯示的作業，您可以選取 [EMP] 節點中。若要產生 WCF 用戶端的所有資料表 SCOTT 結構描述中，您可以選取資料表節點;等等。  
  
## <a name="see-also"></a>另請參閱  
[取得 Visual Studio 中的 Oracle 資料庫作業的中繼資料](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md)