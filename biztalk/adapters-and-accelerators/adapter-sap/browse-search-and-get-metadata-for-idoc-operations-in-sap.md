---
title: 瀏覽、 搜尋及取得 sap IDOC 作業的中繼資料 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF client, generating for IDOC operations
- IDOCs, searching
- searching, IDOCs
- IDOCs, browsing
- browsing, IDOCs
- IDOC operations, generating schema for
- IDOC operations
ms.assetid: 44d05129-ce06-4a10-bf28-9d3519a02a7a
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 27b84c7c3ae8732caaafadfcc403808845d2ccbd
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36996191"
---
# <a name="browse-search-and-get-metadata-for-idoc-operations-in-sap"></a>瀏覽、 搜尋及取得 sap IDOC 作業的中繼資料
本節提供有關如何瀏覽、 搜尋及擷取中繼資料從 SAP IDOC 作業使用的指示[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。 大部分的指示是所有三個使用者介面都相同。 只要適用，個別的程序提供相關的使用者介面。  
  
 執行下列各節提供的步驟之前，您必須具備：  
  
- 建立[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]專案。  
  
- 連接到 SAP 系統時使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 如需指示，請參閱[連接到 Visual Studio 中的 SAP 系統](../../adapters-and-accelerators/adapter-sap/connect-to-the-sap-system-in-visual-studio.md)請注意，連線到 SAP 系統在產生結構描述或 Idoc 的 WCF 用戶端之前，您必須設定特定的繫結屬性。  
  
  - GenerateFlatFileCompatibleIdocSchema  
  
  - ReceiveIdocFormat  
  
  - FlatFileSegmentIndicator  
  
    這些屬性用來管理從 SAP 系統擷取 IDOC 的中繼資料的方式。 如需有關這些屬性的詳細資訊，請參閱 <<c0> [ 了解 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。 如需如何設定繫結屬性的指示，請參閱[設定 SAP 配接器的繫結屬性](../../adapters-and-accelerators/adapter-sap/configure-the-binding-properties-for-the-sap-adapter.md)。  
  
## <a name="browsing-idocs-in-an-sap-system"></a>SAP 系統中的瀏覽 Idoc  
 在瀏覽中繼資料使用時[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，則[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]介面區隔來傳送和從 SAP 系統接收 Idoc 的作業。  
  
- **傳送**並**接收**。 配接器用戶端可以使用這些作業來傳送和接收 Idoc，從 SAP 系統，請使用強型別結構描述。 配接器會呈現這些作業，分別為每個 IDOC，並可在個別的 IDOC 節點下。  
  
- **SendIdoc**並**ReceiveIdoc**。 配接器用戶端可以使用這些作業來傳送和接收 Idoc，從 SAP 系統使用弱型別結構描述。 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]只會呈現一**SendIdoc**並**ReceiveIdoc**所有 Idoc 的作業。 這些作業可直接在底下**IDOC**節點。  
  
  執行下列步驟來瀏覽中 SAP 系統使用的 Idoc [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
#### <a name="to-browse-idocs-in-an-sap-system"></a>若要在 SAP 系統內瀏覽 Idoc  
  
1. 連接到 SAP 伺服器使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 請參閱[連接到 Visual Studio 中的 SAP 系統](../../adapters-and-accelerators/adapter-sap/connect-to-the-sap-system-in-visual-studio.md)如需相關指示。  
  
2. 從**選取合約的型別**下拉式清單中，選取 根據是否將會執行使用配接器的輸入或輸出作業的合約型別。  
  
3. 在 [**選取類別目錄**方塊中，按一下 [IDOC] 節點，請參閱中的 IDOC 訊息類型**可用的類別和作業**] 方塊中。 或者，您也可以在展開 [IDOC] 節點，查看 IDOC 訊息類型。  
  
   > [!TIP]
   >  您可以直接移至 「 立即 」 的類別目錄節點或子類別目錄節點樹狀目錄中，當焦點的樹狀檢視中，輸入在成品名稱**選取一個類別** 方塊中。 例如，若要跳至**ACC_BILLING** IDOC 訊息類型、 專注**IDOC**節點，然後按`ACC_BILLING`。  
  
    下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]列出 IDOC 訊息類型。 根 IDOC 節點也會提供諸如**SendIdoc**傳送弱型別 Idoc 至 SAP 系統的選項。  
  
    ![瀏覽 IDOC 中的訊息類型](../../adapters-and-accelerators/adapter-sap/media/3b8701c2-0530-4577-817c-92af0cd9a770.gif "3b8701c2-0530-4577-817c-92af0cd9a770")  
  
   > [!NOTE]
   >  輸入案例中，根 IDOC 節點表面**ReceiveIdoc**弱式接收作業輸入 Idoc。  
  
4. 按一下以查看相關的 IDOC 類型的 IDOC 訊息類型。 下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]與特定的 IDOC 下的 IDOC 類型的訊息類型。  
  
    ![瀏覽 IDOC 類型](../../adapters-and-accelerators/adapter-sap/media/fee70ed2-74c1-4c91-b2fd-3d281a335145.gif "fee70ed2-74c1-4c91-b2fd-3d281a335145")  
  
5. 按一下以查看 IDOC 類型的不同版本的 IDOC 類型。 下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]以特定的 IDOC 類型的版本。  
  
    ![瀏覽 IDOC 類型的版本](../../adapters-and-accelerators/adapter-sap/media/35603fac-ff48-40b1-bb51-bd0548715cd3.gif "35603fac-ff48-40b1-bb51-bd0548715cd3")  
  
6. 按一下以查看該 IDOC 類型上支援的作業 IDOC 類型的版本。 下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]與特定的 IDOC 類型版本所支援的作業。  
  
    ![瀏覽 IDOC 類型的作業](../../adapters-and-accelerators/adapter-sap/media/f37624b4-f1f2-4d44-8708-01eb51a2d2a7.gif "f37624b4-f1f2-4d44-8708-01eb51a2d2a7")  
  
## <a name="searching-idocs-in-an-sap-system"></a>搜尋 SAP 系統中的 Idoc  
 Idoc 的中繼資料搜尋 SAP 系統使用時[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]， [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，則[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]:  
  
- 支援萬用字元搜尋運算式中。  
  
- 在其中執行搜尋作業的節點下的可搜尋。  
  
  下表列出可用來搜尋和其解譯的特殊字元[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
|特殊字元|解譯|  
|-----------------------|--------------------|  
|+ (加號)|比對一個字元。<br /><br /> 例如，A + 比對 AB、 AC、 AD|  
|* (星號)|比對零或多個字元。<br /><br /> 例如，A * 會比對的 AB，ABC。|  
  
 如需配接器支援的特殊字元的詳細資訊，請參閱[公開配接器設定為使用 WCF LOB 配接器 SDK 的繫結屬性](../../adapters-and-accelerators/wcf-lob-adapter-sdk/expose-adapter-settings-as-a-binding-property-using-the-wcf-lob-adapter-sdk.md)。
  
 執行下列步驟來搜尋 SAP 系統使用的 Idoc [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]， [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
#### <a name="to-search-idocs-in-an-sap-system"></a>搜尋 SAP 系統中的 Idoc  
  
1. 連接到 SAP 伺服器使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 請參閱[連接到 Visual Studio 中的 SAP 系統](../../adapters-and-accelerators/adapter-sap/connect-to-the-sap-system-in-visual-studio.md)如需相關指示。  
  
2. 從**選取合約的型別**下拉式清單中，選取 根據不論您將會搜尋使用配接器的輸入或輸出作業的合約型別。  
  
3. 在 **選取一個類別**方塊中，按一下 IDOC 節點。  
  
   > [!IMPORTANT]
   >  您可以搜尋 IDOCs 只能在根層級。  
  
4. 在 **分類中的搜尋**文字方塊中，輸入要搜尋特定的 IDOC 訊息類型的搜尋運算式。 例如，若要搜尋名稱中有"MATMAS 」 的 Idoc，輸入 * MATMAS\*在文字方塊中。  
  
5. 按一下向右箭號圖示，開始搜尋 按鈕。 搜尋完成後**可用的類別和作業**方塊會列出符合搜尋準則的 Idoc。  
  
    下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]列出 IDOC 搜尋結果。  
  
    ![SAP 系統中搜尋 IDOCs](../../adapters-and-accelerators/adapter-sap/media/tut1-lesson3-step3-idocsearch.gif "Tut1-Lesson3-Step3-IDOCSearch")  
  
## <a name="generating-schema-for-biztalk-projects"></a>對於 BizTalk 專案中產生結構描述  
 您可以使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]來產生結構描述選取 SAP 成品。 一旦您瀏覽並搜尋您想要叫用的成品，您可以產生之成品的結構描述，並傳送訊息，符合結構描述，SAP 系統。  
  
> [!NOTE]
>  您可以選取類別目錄節點，以傳回該類別目錄子樹狀目錄中的所有作業 — 比方說，您可以在這裡選取的 IDOC 類型 （該群組中產生的 Idoc 的所有版本的結構描述），或選取特定版本的 IDOC 產生只有該版本的結構描述IDOC。 如需有關節點的詳細資訊，請參閱[中繼資料節點識別碼](../../adapters-and-accelerators/adapter-sap/metadata-node-ids4.md)。  
  
#### <a name="to-retrieve-metadata-for-idocs"></a>若要擷取 Idoc 的中繼資料  
  
1. 連接到 SAP 伺服器使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。 請參閱[連接到 Visual Studio 中的 SAP 系統](../../adapters-and-accelerators/adapter-sap/connect-to-the-sap-system-in-visual-studio.md)如需相關指示。  
  
2. 從**選取合約的型別**下拉式清單中，選取 根據是否將會執行使用配接器的輸入或輸出作業的合約型別。  
  
3. 在 **選取一個類別**方塊中，按一下 IDOC 訊息類型 或 您要產生中繼資料的 IDOC 類型。  
  
4. 在 **可用的類別和作業**方塊中，選取的 IDOC 類型或您要產生的中繼資料，並按一下 支援的作業**新增**。 會列出所選的 IDOC 類型或 operations**新增的類別和作業** 方塊中。  
  
    下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]列出選取的 Idoc。  
  
    ![擷取 Idoc 的中繼資料](../../adapters-and-accelerators/adapter-sap/media/d9765c62-68b2-4313-9292-9265ab095e2e.gif "d9765c62-68b2-4313-9292-9265ab095e2e")  
  
    如果您想要產生結構描述的多個作業，可能會有一些重複的項目定義，在這些失敗可能導致編譯 BizTalk 專案的結構描述之間。 例如，假設您用來產生 「 Op1"作業的結構描述。 「 資料 Op1"的結構描述包含複雜資料類型"CT1"的參數。 在您關閉之後產生結構描述的 「 資料 Op1"[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]並重新開啟，以產生結構描述的另一項作業 」 Op2"。 假設"Op2 」 也包含複雜資料類型"CT1"的參數。 您在結束之後[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]編譯專案時，就會發生編譯錯誤，因為複雜資料型別"CT1 」 定義兩次在不同的 XSD 檔案。 在這種情況下，我們建議下列各項：  
  
   - 產生的所有作業的結構描述中的單一執行[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。 這可確保[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]會產生複雜的資料類型"CT1 」 只有一個定義。  
  
   - 如果您想要在每次執行會產生多個作業的結構描述[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，請確定您已選取**產生唯一的結構描述型別**核取方塊，使所產生的 XSD 檔案包含複雜的唯一命名空間資料類型"CT1 」。  
  
5. 按一下 [確定] 。 結構描述檔案會儲存具有.xsd 副檔名為 IDOC 專案相同的位置。  
  
   > [!NOTE]
   >  如果您使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，根據預設，檔案會建立命名慣例 「 SAPBinding\<n\>.xsd"，其中 'n' 可以是 1，2，等取決於建立的結構描述檔案的數目。 或者，您可以提供自訂結構描述檔案名稱中輸入名稱**檔案名稱前置詞**文字方塊。 [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]現在會建立結構描述檔案，命名慣例\<檔案名稱前置詞\>\<n\>.xsd。  
   > 
   > [!NOTE]
   >  [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]也會建立包含您在產生結構描述時所指定的繫結屬性的繫結檔案 （XML 檔案） 的作業和叫用作業的 SOAP 動作。 您可以匯入在 BizTalk Server 管理 主控台中建立 WCF 自訂連接埠的連線 URI，繫結屬性與此繫結檔案和設定的 SOAP 動作。 如需詳細資訊，請參閱 <<c0> [ 設定的實體連接埠繫結使用的連接埠繫結檔案至 SAP](../../adapters-and-accelerators/adapter-sap/configure-a-physical-port-binding-using-a-port-binding-file-to-sap.md)。  
  
6. 按一下 [ **檔案** ] 功能表上的 [ **全部儲存**]。  
  
## <a name="generating-a-wcf-client-for-idoc-operations-using-the-add-adapter-service-reference-plug-in"></a>產生 WCF 用戶端使用的 IDOC 作業的新增配接器服務參考外掛程式  
 您可以使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]來產生 WCF 用戶端程式碼，以傳送 Idoc 到 SAP 系統，或者從 SAP 系統接收 Idoc 的 WCF 服務合約。  
  
#### <a name="to-generate-a-wcf-client-or-a-wcf-service-contract-for-idocs"></a>若要針對 Idoc 產生 WCF 用戶端或 WCF 服務合約  
  
1. 在  [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，從**選取合約的型別**下拉式清單中，選取 根據是否將會執行輸入 (接收 Idoc) 或輸出 （傳送 Idoc） 作業的合約型別。  
  
2. 在 [**選取一個類別**方塊中，展開**IDOC** ] 節點，然後瀏覽或搜尋 IDOC 訊息類型或您想要傳送或接收的 IDOC 類型。  
  
3. 在 **可用的類別和作業**方塊中，選取的 IDOC 類型或支援的作業，您想要產生 WCF 用戶端 （或 WCF 服務合約），然後按一下**新增**。 選取的作業都會列入**新增的類別和作業** 方塊中。 您可以選取任何節點中所列**可用的類別和作業** 方塊中。 如果您選取類別節點，然後在該節點和其子節點可用的作業將會新增所有。  
  
   > [!IMPORTANT]
   >  [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]會產生唯一的 WCF 用戶端類別 （或 WCF 服務合約），針對每個 IDOC 類型。 根據分類和您選取的作業，可能會產生一個以上的 WCF 用戶端類別。 如需詳細資訊，請參閱 <<c0> [ 產生 WCF 用戶端或 SAP 解決方案成品的 WCF 服務合約](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md)。  
  
4. 在大部分情況下，預設的序列化選項已足夠;不過，如有需要您可以控制所產生的程式碼的幾個層面和序列化程式所使用的類型。 若要設定這些選項：  
  
   1. 按一下 [**進階選項**來開啟**進階選項**] 方塊中。  
  
   2. 在 **進階選項**下方**選擇選項，以產生的 proxy**，選取您想要的選項。 例如，您可以選取是否非同步方法會產生 WCF 用戶端，或停用設定檔的產生。  
  
   3. 底下**序列化程式**選取應該使用的序列化程式。  
  
      下圖顯示**進階選項**隨附的預設選取項目 (**自動**選取如已選取序列化程式和任何其他選項)。  
  
      ![[進階選項] 方塊預設設定](../../adapters-and-accelerators/adapter-oracle-database/media/r2-net-adapters-oracle-msb-advanced-options.gif "R2_NET_Adapters_Oracle_MSB_Advanced_Options")  
  
      您可以在設定的選項**進階選項**方塊會相當於一些可用的選項，當您使用 ServiceModel Metadata Utility Tool (svcutil.exe)。 如需這些選項的詳細資訊，請參閱[ServiceModel Metadata Utility Tool (Svcutil.exe)](https://msdn.microsoft.com/library/aa347733.aspx)。
  
5. 按一下 [確定] 。 [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]儲存 WCF 用戶端類別 （或 WCF 服務介面） 和協助程式程式碼的作業與您選取了您的專案目錄中的類別。 根據預設，也會儲存組態檔。 輸入和輸出作業; 產生稍有不同的檔案如需詳細資訊，請參閱 <<c0> [ 產生 WCF 用戶端或 SAP 解決方案成品的 WCF 服務合約](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md)。  
  
## <a name="see-also"></a>另請參閱  
 [在 Visual Studio 中取得 SAP 作業的中繼資料](../../adapters-and-accelerators/adapter-sap/get-metadata-for-sap-operations-in-visual-studio.md)