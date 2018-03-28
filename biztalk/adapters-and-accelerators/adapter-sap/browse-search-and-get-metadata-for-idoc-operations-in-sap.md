---
title: 瀏覽、 搜尋，並取得中繼資料中 SAP IDOC 作業的 |Microsoft 文件
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
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b4c82ecf945e85c8e4c9b5f365c808598fcbbf3a
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="browse-search-and-get-metadata-for-idoc-operations-in-sap"></a>瀏覽、 搜尋和 sap IDOC 作業取得中繼資料
本節提供有關如何瀏覽、 搜尋，以及擷取中繼資料從 SAP IDOC 作業使用的指示[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。 大部分的指示會針對所有三種使用者介面相同。 只要適用的話，個別的程序提供相關的使用者介面。  
  
 執行下列各節將提供的步驟之前，您必須：  
  
-   建立[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]專案。  
  
-   連接到 SAP 系統使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 如需指示，請參閱[連接到 Visual Studio 中的 SAP 系統](../../adapters-and-accelerators/adapter-sap/connect-to-the-sap-system-in-visual-studio.md)請注意，連接到 SAP 系統產生結構描述或 Idoc 的 WCF 用戶端之前您必須設定特定的繫結屬性。  
  
    -   GenerateFlatFileCompatibleIdocSchema  
  
    -   ReceiveIdocFormat  
  
    -   FlatFileSegmentIndicator  
  
     這些屬性控制如何從 SAP 系統會擷取 IDOC 的中繼資料。 如需有關這些屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。 如需有關如何設定繫結屬性指示，請參閱[設定 SAP 配接器的繫結屬性](../../adapters-and-accelerators/adapter-sap/configure-the-binding-properties-for-the-sap-adapter.md)。  
  
## <a name="browsing-idocs-in-an-sap-system"></a>瀏覽 Idoc 中的 SAP 系統  
 在瀏覽中繼資料使用時[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]、[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]介面分隔來傳送和從 SAP 系統接收 Idoc 的作業。  
  
-   **傳送**和**接收**。 配接器用戶端可以使用這些作業來傳送和接收 Idoc 從 SAP 系統使用強型別結構描述。 配接器會呈現這些作業分別為每個 IDOC，並個別 IDOC 節點底下。  
  
-   **SendIdoc**和**ReceiveIdoc**。 配接器用戶端可以使用這些作業來傳送和接收 Idoc 從 SAP 系統使用弱式型別的結構描述。 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]只能呈現一個**SendIdoc**和**ReceiveIdoc**所有的 Idoc 的作業。 這些作業都可直接在**IDOC**節點。  
  
 執行下列步驟，在 SAP 系統使用瀏覽 Idoc [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
#### <a name="to-browse-idocs-in-an-sap-system"></a>若要瀏覽 SAP 系統中的 Idoc  
  
1.  連接到 SAP 伺服器使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 請參閱[連接到 Visual Studio 中的 SAP 系統](../../adapters-and-accelerators/adapter-sap/connect-to-the-sap-system-in-visual-studio.md)如需相關指示。  
  
2.  從**選取合約型別**下拉式清單中，選取 根據是否將執行使用配接器的輸入或輸出作業的合約的型別。  
  
3.  在**選取類別目錄**方塊中，按一下 [IDOC] 節點，請參閱中的 IDOC 訊息類型**可用的類別和作業**方塊。 或者，您也可以在展開的 IDOC 節點，查看 IDOC 訊息類型。  
  
    > [!TIP]
    >  您可以直接移至 「 立即 」 的類別目錄節點或子類別目錄節點的樹狀目錄中，輸入中的成品名稱時的焦點所在的樹狀檢閱中**選取類別目錄**方塊。 例如，若要跳至**ACC_BILLING** IDOC 訊息類型，然後將焦點放在**IDOC**  節點，然後輸入`ACC_BILLING`。  
  
     下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]列出 IDOC 訊息類型。 根 IDOC 節點也會提供諸如**SendIdoc**傳送弱型別 Idoc 至 SAP 系統的選項。  
  
     ![瀏覽 IDOC 中的訊息類型](../../adapters-and-accelerators/adapter-sap/media/3b8701c2-0530-4577-817c-92af0cd9a770.gif "3b8701c2-0530-4577-817c-92af0cd9a770")  
  
    > [!NOTE]
    >  輸入案例中，根 IDOC 節點介面**ReceiveIdoc**作業，接收弱型別 Idoc。  
  
4.  按一下以查看相關的 IDOC 類型的 IDOC 訊息類型。 下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]特定 IDOC 的 IDOC 類型的訊息類型。  
  
     ![瀏覽 IDOC 類型](../../adapters-and-accelerators/adapter-sap/media/fee70ed2-74c1-4c91-b2fd-3d281a335145.gif "fee70ed2-74c1-4c91-b2fd-3d281a335145")  
  
5.  按一下以查看 IDOC 類型的不同版本的 IDOC 類型。 下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]以特定的 IDOC 類型的版本。  
  
     ![瀏覽 IDOC 類型的版本](../../adapters-and-accelerators/adapter-sap/media/35603fac-ff48-40b1-bb51-bd0548715cd3.gif "35603fac-ff48-40b1-bb51-bd0548715cd3")  
  
6.  按一下以查看該 IDOC 型別上支援的作業 IDOC 類型的版本。 下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]與特定的 IDOC 類型版本所支援的作業。  
  
     ![瀏覽 IDOC 類型的作業](../../adapters-and-accelerators/adapter-sap/media/f37624b4-f1f2-4d44-8708-01eb51a2d2a7.gif "f37624b4-f1f2-4d44-8708-01eb51a2d2a7")  
  
## <a name="searching-idocs-in-an-sap-system"></a>搜尋 SAP 系統中的 Idoc  
 在 SAP 系統使用搜尋 Idoc 的中繼資料時[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]， [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]、 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]:  
  
-   支援萬用字元搜尋運算式中。  
  
-   啟用立即節點下搜尋在其中執行搜尋作業。  
  
 下表列出可用於搜尋和由其解譯的特殊字元[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
|特殊字元|解譯|  
|-----------------------|--------------------|  
|+ (加號)|比對一個字元。<br /><br /> 例如，A + 比對 AB、 AC、 AD|  
|* (星號)|比對零個或多個字元。<br /><br /> 例如，A * 比對 A，AB，ABC。|  
  
 如需配接器支援的特殊字元的詳細資訊，請參閱[公開介面卡設定為繫結屬性使用 WCF LOB 配接器 SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/expose-adapter-settings-as-a-binding-property-using-the-wcf-lob-adapter-sdk.md)。
  
 執行下列步驟，以搜尋 SAP 系統使用的 Idoc [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]， [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
#### <a name="to-search-idocs-in-an-sap-system"></a>搜尋 SAP 系統中的 Idoc  
  
1.  連接到 SAP 伺服器使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 請參閱[連接到 Visual Studio 中的 SAP 系統](../../adapters-and-accelerators/adapter-sap/connect-to-the-sap-system-in-visual-studio.md)如需相關指示。  
  
2.  從**選取合約型別**下拉式清單中，選取 根據是否您將會搜尋使用配接器的輸入或輸出作業的合約的型別。  
  
3.  在**選取類別目錄**方塊中，按一下 [IDOC] 節點。  
  
    > [!IMPORTANT]
    >  您可以搜尋 Idoc 只能在根層級。  
  
4.  在**類別目錄中的搜尋**文字方塊中，輸入要搜尋特定的 IDOC 訊息類型的搜尋運算式。 例如，若要搜尋名稱中有"MATMAS 」 的 Idoc，請輸入 * MATMAS\*在文字方塊中。  
  
5.  按一下向右箭號圖示，開始搜尋 按鈕。 搜尋完成之後，**可用的類別和作業**方塊會列出符合搜尋準則的 Idoc。  
  
     下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]列出 IDOC 搜尋結果。  
  
     ![搜尋 SAP 系統中的 Idoc](../../adapters-and-accelerators/adapter-sap/media/tut1-lesson3-step3-idocsearch.gif "Tut1 Lesson3 步驟 3-IDOCSearch")  
  
## <a name="generating-schema-for-biztalk-projects"></a>產生結構描述的 BizTalk 專案  
 您可以使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]產生結構描述選取 SAP 成品。 一旦您瀏覽並搜尋您想要叫用的成品，您可以產生結構描述的那些成品，並傳送訊息，符合結構描述至 SAP 系統。  
  
> [!NOTE]
>  您可以選取要在該類別目錄子樹狀結構中傳回所有作業類別目錄節點 — 例如，您可以選取 IDOC 類型 （以產生該群組中的所有版本的 Idoc 的結構描述），或選取特定版本的 IDOC 產生只有該版本的結構描述IDOC。 如需節點的詳細資訊，請參閱[中繼資料的節點識別碼](../../adapters-and-accelerators/adapter-sap/metadata-node-ids4.md)。  
  
#### <a name="to-retrieve-metadata-for-idocs"></a>若要擷取 Idoc 的中繼資料  
  
1.  連接到 SAP 伺服器使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。 請參閱[連接到 Visual Studio 中的 SAP 系統](../../adapters-and-accelerators/adapter-sap/connect-to-the-sap-system-in-visual-studio.md)如需相關指示。  
  
2.  從**選取合約型別**下拉式清單中，選取 根據是否將執行使用配接器的輸入或輸出作業的合約的型別。  
  
3.  在**選取類別目錄**方塊中，按一下 IDOC 訊息類型或您要產生中繼資料的 IDOC 類型。  
  
4.  在**可用的類別和作業**方塊中，選取的 IDOC 類型或支援的作業，您要產生中繼資料，並按一下**新增**。 會列出所選的 IDOC 類型或作業**加入的類別和作業**方塊。  
  
     下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]列出選取的 Idoc。  
  
     ![擷取 Idoc 的中繼資料](../../adapters-and-accelerators/adapter-sap/media/d9765c62-68b2-4313-9292-9265ab095e2e.gif "d9765c62-68b2-4313-9292-9265ab095e2e")  
  
     如果您想要產生結構描述的多個作業，可能是在這些失敗可能導致編譯 BizTalk 專案的結構描述之間的一些重複的項目定義。 例如，假設您用來產生 「 Op1 」 作業的結構描述。 「 Op1"的結構描述包含複雜資料類型"CT1"的參數。 在您關閉之後產生結構描述的 「 Op1" [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ，再重新開啟 「 Op2"的另一個作業產生結構描述。 假設 「 Op2 」 也包含複雜資料類型"CT1"的參數。 結束之後[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]編譯專案，就會發生編譯錯誤，因為複雜資料型別"CT1 」 定義不同的 XSD 檔案中的兩倍。 在這種情況下，我們建議下列各項：  
  
    -   產生的所有作業的結構描述中的單一執行[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。 如此可確保[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]會產生只有一個定義的複雜資料型別"CT1"。  
  
    -   如果您想要產生多個作業的結構描述的不同執行[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，請確定您選取**產生唯一的結構描述型別**核取方塊，以便讓所產生的 XSD 檔案包含複雜的唯一命名空間資料型別"CT1"。  
  
5.  按一下 **[確定]**。 結構描述檔案會儲存具有.xsd 副檔名為 IDOC 專案相同的位置。  
  
    > [!NOTE]
    >  如果您使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，根據預設，檔案會建立命名慣例 」 SAPBinding\<n\>.xsd"，其中 'n' 可以是 1，2，等等取決於建立的結構描述檔案數目。 或者，您可以提供自訂結構描述檔案名稱中輸入名稱**檔案名稱前置詞**文字方塊。 [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]現在建立結構描述檔案命名慣例\<檔案名稱前置詞\>\<n\>.xsd。  
  
    > [!NOTE]
    >  [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]也會建立包含產生結構描述時指定的繫結屬性的繫結檔案 （XML 檔案） 的作業和要叫用作業的 SOAP 動作。 您可以匯入此繫結檔案，在 BizTalk Server 管理主控台中，建立 WCF 自訂連接埠與連接 URI，繫結屬性和設定的 SOAP 動作。 如需詳細資訊，請參閱[設定實體連接埠繫結使用連接埠繫結檔案至 SAP](../../adapters-and-accelerators/adapter-sap/configure-a-physical-port-binding-using-a-port-binding-file-to-sap.md)。  
  
6.  按一下 [ **檔案** ] 功能表上的 [ **全部儲存**]。  
  
## <a name="generating-a-wcf-client-for-idoc-operations-using-the-add-adapter-service-reference-plug-in"></a>產生 IDOC 作業使用的 WCF 用戶端新增配接器服務參考外掛程式  
 您可以使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]來產生 WCF 用戶端程式碼傳送 Idoc 到 SAP 系統，或者從 SAP 系統接收 Idoc 的 WCF 服務合約。  
  
#### <a name="to-generate-a-wcf-client-or-a-wcf-service-contract-for-idocs"></a>若要針對 Idoc 產生 WCF 用戶端或 WCF 服務合約  
  
1.  在[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，從**選取合約型別**下拉式清單中，選取 根據是否執行的輸入 (接收 Idoc) 或輸出 （傳送 Idoc） 作業的合約的型別。  
  
2.  在**選取類別目錄**方塊中，展開 [ **IDOC** ] 節點，然後瀏覽或搜尋 IDOC 訊息類型或您想要傳送或接收的 IDOC 類型。  
  
3.  在**可用的類別和作業**方塊中，選取的 IDOC 類型或支援的作業，您要產生 WCF 用戶端 （或 WCF 服務合約），然後按一下 **新增**。 選取的作業中所列**加入的類別和作業**方塊。 您可以選取任何節點中所列**可用的類別和作業**方塊。 如果您選取類別目錄節點，則所有可在該節點和其子節點的作業會加入。  
  
    > [!IMPORTANT]
    >  [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]為每個 IDOC 類型產生唯一的 WCF 用戶端類別 （或 WCF 服務合約）。 根據您選取的作業和類別，可能會產生一個以上的 WCF 用戶端類別。 如需詳細資訊，請參閱[產生 WCF 用戶端或 WCF 服務合約的 SAP 方案成品](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md)。  
  
4.  在大部分情況下，預設序列化選項已經足夠;不過，如果需要您可以控制所產生的程式碼的幾個層面和序列化程式所使用的類型。 若要設定這些選項：  
  
    1.  按一下**進階選項**開啟**進階選項**方塊。  
  
    2.  在**進階選項**下方的 **選擇選項來產生 proxy**，選取您想要的選項。 例如，您可以選取是否非同步方法產生 WCF 用戶端，或停用組態檔的產生。  
  
    3.  在下**序列化程式**選取應該使用的序列化程式。  
  
     下圖顯示**進階選項**隨附的預設選項 (**自動**選取所選的序列化程式，且沒有其他選項)。  
  
     ![[進階選項] 方塊預設設定](../../adapters-and-accelerators/adapter-oracle-database/media/r2-net-adapters-oracle-msb-advanced-options.gif "R2_NET_Adapters_Oracle_MSB_Advanced_Options")  
  
     您可以在設定的選項**進階選項**方塊相當於某些可用的選項時使用 ServiceModel Metadata Utility Tool (svcutil.exe)。 如需有關這些選項的詳細資訊，請參閱[ServiceModel Metadata Utility Tool (Svcutil.exe)](https://msdn.microsoft.com/library/aa347733.aspx)。
  
5.  按一下 **[確定]**。 [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] WCF 用戶端類別 （或 WCF 服務介面） 會將儲存和協助程式程式碼的作業和專案目錄中所選取的類別。 根據預設，也會儲存組態檔。 輸入和輸出作業; 產生稍有不同的檔案如需詳細資訊，請參閱[產生 WCF 用戶端或 WCF 服務合約的 SAP 方案成品](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md)。  
  
## <a name="see-also"></a>另請參閱  
 [在 Visual Studio 中取得 SAP 作業的中繼資料](../../adapters-and-accelerators/adapter-sap/get-metadata-for-sap-operations-in-visual-studio.md)