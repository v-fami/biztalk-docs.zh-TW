---
title: 瀏覽、 搜尋及取得 sap RFC 作業的中繼資料 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- browsing, RFCs
- RFCs, searching
- RFCs, browsing
- RFC operations, generating schema
- RFC operations
- searching, RFCs
- WCF client, generating a
ms.assetid: 68d9e7b2-b8ab-47f5-afda-2811f68e834b
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c712075358cfacfbbf2ae3478f76fd64b78db6ae
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36966943"
---
# <a name="browse-search-and-get-metadata-for-rfc-operations-in-sap"></a>瀏覽、 搜尋及取得 sap RFC 作業的中繼資料
本節提供有關如何瀏覽、 搜尋及擷取中繼資料從 SAP RFC 作業使用的指示[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。 大部分的指示是所有三個使用者介面都相同。 只要適用，個別的程序提供相關的使用者介面。  
  
 執行下列各節提供的步驟之前，您必須具備：  
  
- 建立[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]專案。  
  
- 連接到 SAP 系統時使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 如需指示，請參閱[連接到 Visual Studio 中的 SAP 系統](../../adapters-and-accelerators/adapter-sap/connect-to-the-sap-system-in-visual-studio.md)。  
  
## <a name="browsing-rfcs-in-an-sap-system"></a>SAP 系統中的瀏覽 Rfc  
 在瀏覽中繼資料使用時[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)][!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]介面：  
  
- Rfc 做為可叫用 SAP 系統的作業。  
  
- RfcGetAttributes 作業，可讓配接器用戶端取得的 RFC 連線參數的相關資訊。  
  
  如需有關如何瀏覽 SAP 中繼資料的詳細資訊，請參閱[公開配接器設定為使用 WCF LOB 配接器 SDK 的繫結屬性](../../adapters-and-accelerators/wcf-lob-adapter-sdk/expose-adapter-settings-as-a-binding-property-using-the-wcf-lob-adapter-sdk.md)。
  
  執行下列步驟來瀏覽中使用您建立 SAP 系統的 Rfc [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
#### <a name="to-browse-rfcs-in-an-sap-system"></a>若要瀏覽 SAP 系統中的 Rfc  
  
1. 連接到 SAP 伺服器使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 請參閱[連接到 Visual Studio 中的 SAP 系統](../../adapters-and-accelerators/adapter-sap/connect-to-the-sap-system-in-visual-studio.md)如需相關指示。  
  
2. 從**選取合約的型別**下拉式清單中，選取 根據是否將會執行使用配接器的輸入或輸出作業的合約型別。  
  
3. 在**選取一個類別**方塊中，按一下 RFC 節點，請參閱 RFC 功能群組，在**可用的類別和作業** 方塊中。 或者，您也可以在展開 [RFC] 節點，查看 RFC 功能群組。  
  
   > [!TIP]
   >  您可以直接移至 「 立即 」 的類別目錄節點或子類別目錄節點樹狀目錄中，當焦點的樹狀檢視中，輸入在成品名稱**選取一個類別** 方塊中。 例如，若要跳至**為基礎**RFC 功能群組，將焦點保持在**RFC**節點，然後按`Basis`。  
  
    下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]列出 RFC 功能群組。  
  
    ![瀏覽 RFC 功能群組](../../adapters-and-accelerators/adapter-sap/media/958cba26-1644-4700-a647-9eeb0273ebd1.gif "958cba26-1644-4700-a647-9eeb0273ebd1")  
  
4. 按一下 RFC 功能群組，以查看相關的 Rfc。 下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]與特定的 RFC 功能群組下的 Rfc。  
  
    ![在 功能群組中，瀏覽 Rfc](../../adapters-and-accelerators/adapter-sap/media/bf725aa9-a547-4f20-8246-d9c8fedadb40.gif "bf725aa9-a547-4f20-8246-d9c8fedadb40")  
  
## <a name="searching-rfcs-in-an-sap-system"></a>搜尋 SAP 系統中的 Rfc  
 在中繼資料搜尋 SAP 系統使用 Rfc [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]:  
  
- 支援萬用字元搜尋運算式中。  
  
- 在其中執行搜尋作業的節點下的可搜尋。  
  
  下表列出可用來搜尋和其解譯的特殊字元[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
|特殊字元|解譯|  
|-----------------------|--------------------|  
|+ (加號)|比對一個字元。<br /><br /> 例如，A + 比對 AB、 AC、 AD|  
|* (星號)|比對零或多個字元。<br /><br /> 例如，A * 會比對的 AB，ABC。|  
  
 如需配接器支援的特殊字元的詳細資訊，請參閱[公開配接器設定為使用 WCF LOB 配接器 SDK 的繫結屬性](../../adapters-and-accelerators/wcf-lob-adapter-sdk/expose-adapter-settings-as-a-binding-property-using-the-wcf-lob-adapter-sdk.md)。
  
 執行下列步驟來搜尋 SAP 系統使用的 Rfc [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
#### <a name="to-search-rfcs-in-an-sap-system"></a>搜尋 SAP 系統中的 Rfc  
  
1. 連接到 SAP 伺服器使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 請參閱[連接到 Visual Studio 中的 SAP 系統](../../adapters-and-accelerators/adapter-sap/connect-to-the-sap-system-in-visual-studio.md)如需相關指示。  
  
2. 從**選取合約的型別**下拉式清單中，選取 根據不論您將會搜尋使用配接器的輸入或輸出作業的合約型別。  
  
3. 在 **選取一個類別**方塊中，按一下包含您想要搜尋的 RFC 的 RFC 功能群組。 如果您不確定哪一個要搜尋的功能群組，請按一下根 RFC 節點。  
  
4. 在 **分類中的搜尋**文字方塊中，輸入要搜尋特定的 RFC 的搜尋運算式。 例如，若要搜尋名稱中有"RFC_CUST"的 Rfc，請輸入 * RFC_CUST\*在文字方塊中。  
  
5. 按一下向右箭號圖示，開始搜尋 按鈕。 搜尋完成後**可用的類別和作業**方塊會列出符合搜尋準則的 Rfc。  
  
    下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]列出 RFC 搜尋結果。  
  
    ![搜尋 SAP 系統中的 RFC](../../adapters-and-accelerators/adapter-sap/media/2cf0b262-bbc7-4d0f-a9cf-5b090fb744b6.gif "2cf0b262-bbc7-4d0f-a9cf-5b090fb744b6")  
  
## <a name="generating-schema-for-biztalk-projects"></a>對於 BizTalk 專案中產生結構描述  
 您可以使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]來產生結構描述選取 SAP 成品。 一旦您瀏覽並搜尋您想要叫用的成品，您可以產生之成品的結構描述，並傳送訊息，符合結構描述，SAP 系統。  
  
> [!NOTE]
>  您可以選取類別目錄節點，以傳回該類別目錄子樹狀目錄中的所有作業 — 比方說，您可以在其中選取整個 RFC 功能群組 （若要產生的結構描述該群組中的所有 Rfc），或選取特定的 Rfc 來產生結構描述的只有這些 Rfc。 如需有關節點的詳細資訊，請參閱[中繼資料節點識別碼](../../adapters-and-accelerators/adapter-sap/metadata-node-ids4.md)。  
  
#### <a name="to-retrieve-metadata-for-rfcs"></a>若要擷取 Rfc 的中繼資料  
  
1. 連接到 SAP 伺服器使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。 請參閱[連接到 Visual Studio 中的 SAP 系統](../../adapters-and-accelerators/adapter-sap/connect-to-the-sap-system-in-visual-studio.md)如需相關指示。  
  
2. 從**選取合約的型別**下拉式清單中，選取 根據是否將會執行使用配接器的輸入或輸出作業的合約型別。  
  
3. 在 **選取一個類別**方塊中，按一下包含您要產生中繼資料的 RFC 的 RFC 功能群組。  
  
    您也可以搜尋特定的 Rfc。 例如，若要搜尋其名稱中包含"RFC_CUST"的 Rfc 按一下 RFC 節點，並在**分類中的搜尋**文字方塊中輸入\*RFC_CUST\*。 按一下向右箭號圖示，開始搜尋 按鈕。 **可用的類別和作業**方塊會列出所有名稱中具有"RFC_CUST"的 Rfc。  
  
4. 在 **可用的類別和作業**方塊中，選取您要產生的中繼資料，並按一下 的 Rfc**新增**。 列出所選的 Rfc**新增的類別和作業** 方塊中。  
  
    下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]列出所選的 Rfc。  
  
    ![擷取 RFC 的中繼資料](../../adapters-and-accelerators/adapter-sap/media/f7c89882-e2d7-409b-af2e-e35c7268c137.gif "f7c89882-e2d7-409b-af2e-e35c7268c137")  
  
    如果您想要產生結構描述的多個作業，可能會有一些重複的項目定義，在這些失敗可能導致編譯 BizTalk 專案的結構描述之間。 例如，假設您用來產生 「 Op1"作業的結構描述。 「 資料 Op1"的結構描述包含複雜資料類型"CT1"的參數。 在您關閉之後產生結構描述的 「 資料 Op1"[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]並重新開啟，以產生結構描述的另一項作業 」 Op2"。 假設"Op2 」 也包含複雜資料類型"CT1"的參數。 您在結束之後[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]編譯專案時，就會發生編譯錯誤，因為複雜資料型別"CT1 」 定義兩次在不同的 XSD 檔案。 在這種情況下，我們建議下列各項：  
  
   - 產生的所有作業的結構描述中的單一執行[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。 這可確保[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]會產生複雜的資料類型"CT1 」 只有一個定義。  
  
   - 如果您想要在每次執行會產生多個作業的結構描述[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，請確定您已選取**產生唯一的結構描述型別**核取方塊，使所產生的 XSD 檔案包含複雜的唯一命名空間資料類型"CT1 」。  
  
5. 按一下 [確定] 。 結構描述檔案會儲存具有.xsd 副檔名為 BizTalk 專案的所在位置。  
  
   > [!NOTE]
   >  如果您使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，根據預設，檔案會建立命名慣例 「 SAPBinding\<n >.xsd"，其中 'n' 可以是 1，2，等取決於建立的結構描述檔案的數目。 或者，您可以提供自訂結構描述檔案名稱中輸入名稱**檔案名稱前置詞**文字方塊。 [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]現在會建立結構描述檔案，命名慣例\<檔案名稱前置詞 >\<n >.xsd。  
   > 
   > [!NOTE]
   >  [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]也會建立包含您在產生結構描述時所指定的繫結屬性的繫結檔案 （XML 檔案） 的作業和叫用作業的 SOAP 動作。 您可以匯入在 BizTalk Server 管理 主控台中建立 WCF 自訂連接埠的連線 URI，繫結屬性與此繫結檔案和設定的 SOAP 動作。 如需詳細資訊，請參閱 <<c0> [ 設定的實體連接埠繫結使用的連接埠繫結檔案至 SAP](../../adapters-and-accelerators/adapter-sap/configure-a-physical-port-binding-using-a-port-binding-file-to-sap.md)。
  
6. 按一下 [ **檔案** ] 功能表上的 [ **全部儲存**]。  
  
## <a name="generating-a-wcf-client-for-rfc-operations-using-the-add-adapter-service-reference-plug-in"></a>產生 WCF 用戶端使用的 RFC 作業的新增配接器服務參考外掛程式  
 您可以使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]產生其中一個 WCF 用戶端程式碼來將 SAP 傳送 Rfc 系統或 WCF 服務合約和程式碼，以接收來自 SAP 系統的 Rfc （RFC 伺服器）。  
  
#### <a name="to-generate-a-wcf-client-or-a-wcf-service-contract-for-rfcs"></a>若要針對 Rfc 產生 WCF 用戶端或 WCF 服務合約  
  
1. 在  [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，從**選取合約的型別**下拉式清單中，選取 根據是否將會執行輸入 （RFC 伺服器） 或輸出作業的合約型別。  
  
2. 在**選取一個類別**方塊中，展開**RFC** ] 節點，然後按一下 [RFC 功能群組包含您要產生 WCF 用戶端或 WCF 服務合約的 RFC。  
  
    您也可以搜尋 Rfc。 例如，若要搜尋其名稱中包含"RFC_CUST"的 Rfc，請按一下**RFC**節點並在**類別目錄中的搜尋**文字方塊中輸入\*RFC_CUST\*。 按一下向右箭號圖示，開始搜尋 按鈕。 **可用的類別和作業**方塊會列出所有名稱中具有"RFC_CUST"的 Rfc。  
  
3. 在 **可用的類別和作業**方塊中，選取您要產生 WCF 用戶端 （或 WCF 服務合約），然後按一下 類別目錄 （RFC 功能群組） 的作業**新增**。 選取的作業都會列入**新增的類別和作業** 方塊中。 您可以選取任何節點中所列**可用的類別和作業** 方塊中。 如果您選取類別節點，然後在該節點和其子節點可用的作業將會新增所有。  
  
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