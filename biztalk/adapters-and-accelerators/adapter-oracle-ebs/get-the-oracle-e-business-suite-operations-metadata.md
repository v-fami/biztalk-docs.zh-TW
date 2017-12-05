---
title: "取得 Oracle E-business Suite 作業的中繼資料 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 566ae086-183a-47db-8f93-12b5903c85c3
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1443219f8562caee53547be3f78df15834ddf4b7
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="get-the-oracle-e-business-suite-operations-metadata"></a>取得 Oracle E-business Suite 作業的中繼資料
您可以使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]產生選取的 Oracle E-business Suite 成品的結構描述。 您已經瀏覽及搜尋您想要叫用的成品之後，您可以產生結構描述的那些成品，並傳送訊息，符合結構描述到 Oracle E-business Suite 的資訊。  
  
> [!NOTE]
>  [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]和[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]呈現基本上相同的介面，當您瀏覽和搜尋作業，因此相同的主題將涵蓋這兩個元件。  
  
## <a name="prerequisites"></a>必要條件  
 擷取目標作業的中繼資料之前，您必須連接到 Oracle E-business Suite 的資訊。 如需如何連接到 Oracle 資料庫使用時[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，請參閱[連接到 Visual Studio 中的 Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-the-oracle-e-business-suite-in-visual-studio.md)。  
  
## <a name="generating-schema-using-the-consume-adapter-service-add-in"></a>產生結構描述使用使用配接器服務增益集  
  
> [!NOTE]
>  您可以選取要在該類別目錄子樹狀結構中傳回所有作業類別目錄節點： 例如，您可以選取**並行程式**節點 （以產生結構描述的所有 Oracle 應用程式的並行程式），或者您可以選取特定的並行處理程式。 如需節點的詳細資訊，請參閱 < 中繼資料的節點識別碼。  
  
#### <a name="to-generate-schema-for-oracle-e-business-suite-artifacts"></a>若要產生結構描述的 Oracle E-business Suite 成品  
  
1.  連接到 Oracle E-business Suite 使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 請參閱[連接到 Visual Studio 中的 Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-the-oracle-e-business-suite-in-visual-studio.md)如需相關指示。  
  
    > [!IMPORTANT]
    >  若要產生結構描述執行作業使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]必須設定**EnableBizTalkCompatibilityMode**內容繫結至**True**。 您必須連接到 Oracle E-business Suite 的資訊來設定這個繫結屬性。  
  
2.  從**選取合約型別**清單中，選取是否要產生的輸入或輸出作業的結構描述為基礎的合約的型別。  
  
3.  按一下您要產生中繼資料的類別目錄節點。 例如，如果您想要產生中繼資料的並行程式 Oracle 應用程式中，按一下**並行程式**。  
  
4.  展開 [類別目錄] 節點，然後選取該節點，您要產生中繼資料內的特定項目。 例如，若要產生同時執行的 「 銀行中心 」 應用程式的中繼資料，請展開**並行程式**節點，然後再按一下**銀行 Center**。  
  
5.  在**可用的類別和作業**方塊中，選取您想要叫用，然後按一下 operations**新增**。 選取的作業中所列**加入的類別和作業**方塊。 例如，要叫用 「 清除 FTP 銀行帳戶 」 和 「 Get_Status"並行程式，按一下作業名稱，然後按一下**新增**。  
  
     下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，其中會列出選取的作業。  
  
     ![從 Oracle &#45; 擷取中繼資料Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/media/df7de132-9177-4de7-a620-59dbd561efe5.gif "df7de132-9177-4de7-a620-59dbd561efe5")  
  
     如果您想要產生結構描述的多個作業，可能是在這些失敗可能導致編譯 BizTalk 專案的結構描述之間的一些重複的項目定義。 例如，假設您用來產生 「 Op1 」 作業的結構描述。 「 Op1"的結構描述包含資料類型"CT1"的參數。 在您關閉之後產生結構描述的 「 Op1" [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ，再重新開啟 「 Op2"的另一個作業產生結構描述。 假設 「 Op2 」 也包含資料類型"CT1"的參數。 結束之後[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]編譯專案，就會發生編譯錯誤，因為複雜資料型別"CT1 」 定義不同的 XSD 檔案中的兩倍。 在這種情況下，我們建議下列各項：  
  
    -   產生的所有作業的結構描述中的單一執行[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。 如此可確保[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]會產生只有一個定義的複雜資料型別"CT1"。  
  
    -   如果您想要產生多個作業的結構描述的不同執行[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，請確定您選取**產生唯一的結構描述型別**核取方塊，以便讓所產生的 XSD 檔案包含用於唯一命名空間複雜資料型別"CT1"。  
  
6.  按一下 **[確定]**。 結構描述檔案會儲存具有.xsd 副檔名為 BizTalk 專案的相同位置。  
  
    > [!NOTE]
    >  如果您用來產生 Oracle 成品上作業的中繼資料使用配接器服務增益集，預設會建立檔案使用特定的命名慣例： 產生的 XSD 檔案名稱具有下列三個部分：  
    >   
    >  -   中提供 」 OracleEBSBinding"或前置詞**檔案名稱前置詞**方塊。  
    > -   名稱中包含**fileNameHint**產生的 WSDL 中的註解標記。 對於作業而言，檔案名稱提示是相同作業群組。 針對複雜型別，檔案名稱提示為不含"http://schemas.microsoft.com/OracleEBS/2008/05/"前置詞的命名空間。 例如，介面資料表作業的檔案名稱提示所遵循的慣例\<InterfaceTables\>+ < app_short_name > + < interface_table_name >。  
    > -   （選擇性）整數，以確保檔案名稱是唯一。  
    >   
    >  最後，XSD 檔案的名稱到達時做為 < file_name_prefix > +\<fileNameHint\>+ n，其中"n"是唯一的整數。  
  
    > [!NOTE]
    >  [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]也會建立包含時指定的繫結屬性的繫結檔案 （XML 檔案） 產生的結構描述的作業和要叫用作業的 SOAP 動作。 您可以將此繫結檔案匯入[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台來建立 WCF 自訂連接埠與連接 URI、 繫結屬性和 SOAP 動作設定。 如需詳細資訊，請參閱[設定使用 Oracle 資料庫的連接埠繫結檔案的實體連接埠繫結](../../adapters-and-accelerators/adapter-oracle-database/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-database.md)。  
  
     您已成功產生供 Oracle E-business Suite 成品的中繼資料。 您可以使用中繼資料，將訊息傳送至 Oracle E-business Suite 來執行特定作業。 請參閱[開發 BizTalk 應用程式使用 Oracle E-business Suite 介面卡](../../adapters-and-accelerators/adapter-oracle-ebs/develop-biztalk-applications-using-the-oracle-e-business-suite-adapter.md)如需有關如何執行這些作業。  
  
## <a name="generating-a-wcf-client-or-wcf-service-contract-using-the-add-adapter-service-reference-plug-in"></a>產生 WCF 用戶端或 WCF 服務合約使用新增配接器服務參考外掛程式  
 您可以使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]來產生傳出作業的 WCF 用戶端程式碼，或是 WCF 服務程式碼的輸入操作。  
  
#### <a name="to-generate-wcf-client-class-or-service-contract-for-oracle-e-business-suite-operations"></a>若要產生 WCF 用戶端類別或服務 Oracle E-business Suite 作業合約  
  
1.  在[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，從**選取合約型別**下拉式清單中，選取 根據是否執行的輸入或輸出作業的合約的型別。  
  
2.  瀏覽或搜尋的類別 （如介面資料表），或是您要產生 WCF 用戶端 （或 WCF 服務合約） 的特定作業。   
    例如，若要瀏覽 AR_ARCHIVE_PURGE_INTERIM 介面資料表上的作業中**選取類別目錄**方塊：  
  
    1.  展開根節點 (**/**) 以查看作業會顯示 for Oracle E-business Suite 的類別。 相同的介面資料表可以是適用於**應用程式為基礎的檢視**節點以及**成品為基礎的檢視**節點。 在此範例中，您會產生 WCF 用戶端類別，從**應用程式為基礎的檢視**節點。  
  
    2.  根節點下，依序展開**應用程式為基礎的檢視**節點，查看 Oracle E-business Suite 中可用的應用程式。  
  
    3.  展開的節點**應收帳款**應用程式，然後展開 **介面資料表**節點。  
  
    4.  按一下**AR_ARCHIVE_PURGE_INTERIM**介面資料表節點，然後在**可用的類別和作業**方塊中，選取您要產生 WCF 用戶端 （或 WCF 服務的作業合約），然後按一下 **新增**。 選取的作業中所列**加入的類別和作業**方塊。  
  
         下圖顯示[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]與所選 AR_ARCHIVE_PURGE_INTERIM 資料表的 Insert 與 Select 作業。  
  
         ![產生 WCF 用戶端或服務合約](../../adapters-and-accelerators/adapter-oracle-ebs/media/oraebs-adap-add-adap-serv-refs.gif "oraebs_adap_add_adap_serv_refs")  
  
        > [!IMPORTANT]
        >  取決於輸出作業 （或類別），您選取多個一個 WCF 用戶端類別可能會產生。 如需詳細資訊，請參閱[產生 WCF 用戶端或 WCF 服務合約，如 Oracle E-business Suite 方案成品](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md)。  
  
3.  在大部分情況下，預設序列化選項已經足夠;不過，如果需要您可以控制所產生的程式碼的幾個層面和序列化程式所使用的類型。 若要設定這些選項：  
  
    1.  按一下**進階選項**開啟**進階選項**方塊。  
  
    2.  在**進階選項**下方的 **選擇選項來產生 proxy**，選取您想要的選項。 例如，您可以選取是否非同步方法產生 WCF 用戶端，或停用組態檔的產生。  
  
    3.  在下**序列化程式**選取應該使用的序列化程式。  
  
     下圖顯示**進階選項**隨附的預設選項 (**自動**選取所選的序列化程式，且沒有其他選項)。  
  
     ![[進階選項] 方塊預設設定](../../adapters-and-accelerators/adapter-oracle-database/media/r2-net-adapters-oracle-msb-advanced-options.gif "R2_NET_Adapters_Oracle_MSB_Advanced_Options")  
  
     您可以在設定的選項**進階選項**方塊相當於某些可用的選項時使用 ServiceModel Metadata Utility Tool (svcutil.exe)。 如需有關這些選項的詳細資訊，請參閱[ServiceModel Metadata Utility Tool (Svcutil.exe)](https://msdn.microsoft.com/library/aa347733.aspx)。
  
4.  按一下 **[確定]**。 [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] WCF 用戶端類別 （或 WCF 服務介面） 會將儲存和協助程式程式碼的作業和專案目錄中所選取的類別。 根據預設，也會儲存組態檔。 輸入和輸出作業; 產生稍有不同的檔案如需詳細資訊，請參閱[產生 WCF 用戶端或 WCF 服務合約，如 Oracle E-business Suite 方案成品](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md)。  
  
 您可以選取任何節點中所列**可用的類別和作業**方塊。 如果您選取類別目錄節點，則會選取所有適用於該節點和其子節點的作業。 例如，若要產生的所有作業 AR_ARCHIVE_PURGE_INTERIM 資料表中顯示的 WCF 用戶端，您可以選取**AR_ARCHIVE_PURGE_INTERIM**節點。  
  
## <a name="see-also"></a>請參閱  
 [瀏覽、 搜尋及取得 Oracle E-business Suite 作業的中繼資料](../../adapters-and-accelerators/adapter-oracle-ebs/browse-search-and-get-metadata-for-oracle-e-business-suite-operations.md)