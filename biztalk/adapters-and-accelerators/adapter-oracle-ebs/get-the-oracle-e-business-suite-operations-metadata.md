---
title: 取得 Oracle E-business Suite 作業的中繼資料 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 566ae086-183a-47db-8f93-12b5903c85c3
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e8904a70d2bfe1b34b28b7cad807796fac752009
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37014839"
---
# <a name="get-the-oracle-e-business-suite-operations-metadata"></a>取得 Oracle E-business Suite 作業的中繼資料
您可以使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]產生選取的 Oracle E-business Suite 成品的結構描述。 您已經瀏覽及搜尋您想要叫用的成品之後，您可以產生之成品的結構描述，並傳送訊息，符合結構描述，Oracle E-business suite。  
  
> [!NOTE]
>  [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]而[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]呈現基本上相同的介面，當您瀏覽和搜尋作業，因此這兩個元件所述的相同的主題。  
  
## <a name="prerequisites"></a>必要條件  
 您必須先連接到 Oracle E-business Suite，然後再擷取目標作業的中繼資料。 如需如何連接到 Oracle 資料庫使用時[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，請參閱[連接到 Oracle E-business Suite，在 Visual Studio 中](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-the-oracle-e-business-suite-in-visual-studio.md)。  
  
## <a name="generating-schema-using-the-consume-adapter-service-add-in"></a>產生結構描述使用使用配接器服務增益集  
  
> [!NOTE]
>  您可以選取類別目錄節點，以傳回該類別目錄子樹狀目錄中的所有作業 — 比方說，您可以選取**並行程式**（要產生結構描述的 Oracle 應用程式的所有並行程式） 節點，或者您可以選取特定的並行處理程式。 如需有關節點的詳細資訊，請參閱中繼資料節點識別碼。  
  
#### <a name="to-generate-schema-for-oracle-e-business-suite-artifacts"></a>若要產生結構描述的 Oracle E-business Suite 成品  
  
1. 連接到 Oracle E-business Suite 使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 請參閱[連接到 Oracle E-business Suite，在 Visual Studio 中](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-the-oracle-e-business-suite-in-visual-studio.md)如需相關指示。  
  
   > [!IMPORTANT]
   >  若要針對使用執行作業產生結構描述[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，您必須設定**EnableBizTalkCompatibilityMode**繫結屬性，以 **，則為 True**。 建立至 Oracle E-business Suite 連線時，您必須設定這個繫結屬性。  
  
2. 從**選取合約的型別**清單中，選取 根據您是否產生結構描述的輸入或輸出作業的合約型別。  
  
3. 按一下您要產生中繼資料的類別目錄節點。 例如，如果您想要產生的 Oracle 應用程式內的並行處理程式的中繼資料，按一下**並行程式**。  
  
4. 展開 [類別目錄] 節點中，然後選取該節點，您要產生中繼資料內的特定項目。 例如，若要產生 「 銀行中心 」 應用程式的並行程式的中繼資料，請展開**並行程式**節點，然後再按一下**銀行 Center**。  
  
5. 在 **可用的類別和作業**方塊中，選取您想要叫用，然後按一下 operations**新增**。 選取的作業都會列入**新增的類別和作業** 方塊中。 比方說，若要叫用 「 清除 FTP 銀行帳戶 」 和 「 Get_Status 「 同時執行的程式，請按一下作業名稱 中，，，然後按一下**新增**。  
  
    下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，其中會列出選取的作業。  
  
    ![擷取中繼資料從 Oracle E&#45;Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/media/df7de132-9177-4de7-a620-59dbd561efe5.gif "df7de132-9177-4de7-a620-59dbd561efe5")  
  
    如果您想要產生結構描述的多個作業，可能會有一些重複的項目定義，在這些失敗可能導致編譯 BizTalk 專案的結構描述之間。 例如，假設您用來產生 「 Op1"作業的結構描述。 「 資料 Op1"的結構描述包含的資料類型"CT1"的參數。 在您關閉之後產生結構描述的 「 資料 Op1"[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]並重新開啟，以產生結構描述的另一項作業 」 Op2"。 假設"Op2 」 也包含資料類型"CT1"的參數。 您在結束之後[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]編譯專案時，就會發生編譯錯誤，因為複雜資料型別"CT1 」 定義兩次在不同的 XSD 檔案。 在這種情況下，我們建議下列各項：  
  
   - 產生的所有作業的結構描述中的單一執行[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。 這可確保[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]會產生複雜的資料類型"CT1 」 只有一個定義。  
  
   - 如果您想要在每次執行會產生多個作業的結構描述[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，請確定您已選取**產生唯一的結構描述型別**核取方塊，使所產生的 XSD 檔案包含用於唯一的命名空間複雜資料型別 」 CT1"。  
  
6. 按一下 [確定] 。 結構描述檔案會儲存具有.xsd 副檔名為 BizTalk 專案的所在位置。  
  
   > [!NOTE]
   >  如果您用來產生對 Oracle 成品執行作業的中繼資料使用配接器服務增益集，依預設建立的檔案是具有特定命名慣例： 產生的 XSD 檔案名稱具有下列三個部分：  
   > 
   > - 中提供的 「 OracleEBSBinding"或前置詞**檔案名稱前置詞** 方塊中。  
   >   - 中包含的名稱**fileNameHint**產生的 WSDL 中的註解標記。 對於作業而言，檔案名稱提示是相同的作業群組。 複雜類型中，檔案名稱提示是不含命名空間"<http://schemas.microsoft.com/OracleEBS/2008/05/”>前置詞。 例如，介面資料表作業的檔案名稱提示會遵循慣例\<InterfaceTables\>+ < app_short_name > + < interface_table_name >。  
   >   - （選擇性）若要確保檔案名稱是唯一的整數。  
   > 
   >   最後，XSD 檔案的名稱到達時為 < file_name_prefix > +\<fileNameHint\>+ n，其中"n"是唯一的整數。  
   > 
   > [!NOTE]
   >  [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]也會建立包含時所指定的繫結屬性的繫結檔案 （XML 檔案） 產生的作業和 SOAP 動作叫用作業的結構描述。 您可以匯入此繫結檔案中的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台來建立 WCF 自訂連接埠與連接 URI、 繫結屬性和 SOAP 動作設定。 如需詳細資訊，請參閱 <<c0> [ 設定為使用 Oracle 資料庫的連接埠繫結檔案的實體連接埠繫結](../../adapters-and-accelerators/adapter-oracle-database/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-database.md)。  
  
    您已經順利產生 Oracle E-business Suite 構件的中繼資料。 您可以使用中繼資料，將訊息傳送至 Oracle E-business Suite，以執行特定作業。 請參閱[使用 Oracle E-business Suite 配接器開發 BizTalk 應用程式](../../adapters-and-accelerators/adapter-oracle-ebs/develop-biztalk-applications-using-the-oracle-e-business-suite-adapter.md)如需有關如何執行這些作業。  
  
## <a name="generating-a-wcf-client-or-wcf-service-contract-using-the-add-adapter-service-reference-plug-in"></a>產生 WCF 用戶端或 WCF 服務合約使用新增配接器服務參考外掛程式  
 您可以使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]來產生輸出作業的 WCF 用戶端程式碼，或是輸入作業的 WCF 服務程式碼。  
  
#### <a name="to-generate-wcf-client-class-or-service-contract-for-oracle-e-business-suite-operations"></a>若要產生 WCF 用戶端類別或服務合約 Oracle E-business Suite 作業  
  
1. 在  [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，從**選取合約的型別**下拉式清單中，選取 根據是否將會執行輸入或輸出作業的合約型別。  
  
2. 瀏覽或搜尋類別 （例如在介面資料表），或是您要產生 WCF 用戶端 （或 WCF 服務合約） 的特定作業。   
   例如，若要瀏覽 AR_ARCHIVE_PURGE_INTERIM 介面資料表上的作業中**選取一個類別**方塊：  
  
   1. 展開 [根] 節點 (**/**) 以查看作業會顯示 for Oracle E-business Suite 的類別。 相同的介面資料表可以位於**應用程式為基礎的檢視**節點，以及**成品為基礎的檢視**節點。 在此範例中，您會產生 WCF 用戶端類別，從**應用程式為基礎的檢視**節點。  
  
   2. 在 根 節點中，依序展開**應用程式為基礎的檢視**節點以查看 Oracle E-business Suite 中可用的應用程式。  
  
   3. 展開的節點**應收帳款**應用程式，然後展開**Interface Table**節點。  
  
   4. 按一下  **AR_ARCHIVE_PURGE_INTERIM**介面資料表節點，然後在**可用的類別和作業**方塊中，選取您要產生 WCF 用戶端 （或 WCF 服務的作業合約），然後按一下**新增**。 選取的作業都會列入**新增的類別和作業** 方塊中。  
  
       下圖顯示[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]選取 AR_ARCHIVE_PURGE_INTERIM 資料表的 Insert 與 Select 作業使用。  
  
       ![產生 WCF 用戶端或服務合約](../../adapters-and-accelerators/adapter-oracle-ebs/media/oraebs-adap-add-adap-serv-refs.gif "oraebs_adap_add_adap_serv_refs")  
  
      > [!IMPORTANT]
      >  取決於輸出作業 （或類別），您選取多個一個 WCF 用戶端類別可能會產生。 如需詳細資訊，請參閱 <<c0> [ 產生 WCF 用戶端或 Oracle E-business Suite 解決方案成品的 WCF 服務合約](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md)。  
  
3. 在大部分情況下，預設的序列化選項已足夠;不過，如有需要您可以控制所產生的程式碼的幾個層面和序列化程式所使用的類型。 若要設定這些選項：  
  
   1. 按一下 [**進階選項**來開啟**進階選項**] 方塊中。  
  
   2. 在 **進階選項**下方**選擇選項，以產生的 proxy**，選取您想要的選項。 例如，您可以選取是否非同步方法會產生 WCF 用戶端，或停用設定檔的產生。  
  
   3. 底下**序列化程式**選取應該使用的序列化程式。  
  
      下圖顯示**進階選項**隨附的預設選取項目 (**自動**選取如已選取序列化程式和任何其他選項)。  
  
      ![[進階選項] 方塊預設設定](../../adapters-and-accelerators/adapter-oracle-database/media/r2-net-adapters-oracle-msb-advanced-options.gif "R2_NET_Adapters_Oracle_MSB_Advanced_Options")  
  
      您可以在設定的選項**進階選項**方塊會相當於一些可用的選項，當您使用 ServiceModel Metadata Utility Tool (svcutil.exe)。 如需這些選項的詳細資訊，請參閱[ServiceModel Metadata Utility Tool (Svcutil.exe)](https://msdn.microsoft.com/library/aa347733.aspx)。
  
4. 按一下 [確定] 。 [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]儲存 WCF 用戶端類別 （或 WCF 服務介面） 和協助程式程式碼的作業與您選取了您的專案目錄中的類別。 根據預設，也會儲存組態檔。 輸入和輸出作業; 產生稍有不同的檔案如需詳細資訊，請參閱 <<c0> [ 產生 WCF 用戶端或 Oracle E-business Suite 解決方案成品的 WCF 服務合約](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md)。  
  
   您可以選取任何節點中所列**可用的類別和作業** 方塊中。 如果您選取類別節點，則會選取所有位於該節點和其子節點的作業。 例如，若要產生的所有作業 AR_ARCHIVE_PURGE_INTERIM 資料表所呈現的 WCF 用戶端，您可以選取**AR_ARCHIVE_PURGE_INTERIM**節點。  
  
## <a name="see-also"></a>另請參閱  
 [瀏覽、 搜尋及取得 Oracle E-business Suite 作業的中繼資料](../../adapters-and-accelerators/adapter-oracle-ebs/browse-search-and-get-metadata-for-oracle-e-business-suite-operations.md)