---
title: 瀏覽、 搜尋及取得 SAP 中的 BAPI 作業的中繼資料 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BAPI operations
- WCF client, generating for BAPI operations
- BAPIs, browsing
- searching, BAPIs
- browsing, BAPIs
- BAPIs, searching
- BAPI operations, generating schema
ms.assetid: 2884215a-ddba-40c7-bf9f-bfc7831f90bb
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 97a043c08cf8d7ef258ceb2a2f311d2a86302881
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36978951"
---
# <a name="browse-search-and-get-metadata-for-bapi-operations-in-sap"></a>瀏覽、 搜尋及取得 SAP 中的 BAPI 作業的中繼資料
本節提供如何瀏覽、 搜尋及擷取 SAP 中的中繼資料，使用的 BAPI 作業的指示[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。 大部分的指示是所有三個使用者介面都相同。 只要適用，個別的程序提供相關的使用者介面。  
  
 執行下列各節提供的步驟之前，您必須具備：  
  
- 建立[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]專案。  
  
- 連接到 SAP 系統時使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 如需指示，請參閱[連接到 Visual Studio 中的 SAP 系統](../../adapters-and-accelerators/adapter-sap/connect-to-the-sap-system-in-visual-studio.md)。  
  
## <a name="browsing-bapis-in-an-sap-system"></a>SAP 系統中的瀏覽 Bapi  
 在瀏覽中繼資料使用時[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)][!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]商務物件，以及 Rfc，請瀏覽 Bapi。 瀏覽 Bapi rfc 是類似瀏覽 RFC，SAP 系統中。 在此情況下，Bapi 可在 Rfc **RFC**。 如需有關如何瀏覽 Rfc 的詳細資訊，請參閱[瀏覽、 搜尋及取得中繼資料，在 SAP 中的 RFC 作業的](../../adapters-and-accelerators/adapter-sap/browse-search-and-get-metadata-for-rfc-operations-in-sap.md)。  
  
 本節會提供資訊，在瀏覽 Bapi 商務物件。 如需有關如何瀏覽 SAP 中繼資料的詳細資訊，請參閱[配接器介面 SAP 中繼資料的運作方式？](https://msdn.microsoft.com/library/dd788039.aspx)  
  
 執行下列步驟來瀏覽中 SAP 系統使用的 Bapi [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
 
  
#### <a name="to-browse-bapis-in-an-sap-system"></a>若要在 SAP 系統內瀏覽 Bapi  
  
1. 連接到 SAP 伺服器使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 請參閱[連接到 Visual Studio 中的 SAP 系統](../../adapters-and-accelerators/adapter-sap/connect-to-the-sap-system-in-visual-studio.md)如需相關指示。  
  
2. 從**選取合約的型別**下拉式清單中，選取 根據是否將會執行使用配接器的輸入或輸出作業的合約型別。  
  
3. 在 [**選取類別目錄**方塊中，按一下 [BAPI] 節點，請參閱中的 BAPI 功能區域**可用的類別和作業**] 方塊中。 或者，您也可以在展開 [BAPI] 節點，查看 BAPI 功能區域。  
  
   > [!TIP]
   >  您可以直接移至 「 立即 」 的類別目錄節點或子類別目錄節點樹狀目錄中，當焦點的樹狀檢視中，輸入在成品名稱**選取一個類別** 方塊中。 例如，若要跳至**控**BAPI 功能區域，專注**BAPI**節點，然後按`Controlling`。  
  
    下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]列出 BAPI 功能區域。  
  
    ![瀏覽 BAPI 中的功能區域](../../adapters-and-accelerators/adapter-sap/media/d4b03725-44d2-449d-a035-491cd7415139.gif "d4b03725-44d2-449d-a035-491cd7415139")  
  
4. 按一下以查看進一步的分類 BAPI 功能區域的 BAPI 功能區域。  
  
5. 按一下以查看支援該功能區域的相關作業 [BAPI] 功能區域。 下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]與支援特定功能區域的作業。  
  
    ![瀏覽 BAPI 的作業](../../adapters-and-accelerators/adapter-sap/media/1a9be42e-1f9e-4cf6-a555-c4e755fcc0ea.gif "1a9be42e-1f9e-4cf6-a555-c4e755fcc0ea")  
  
## <a name="searching-bapis-in-an-sap-system"></a>搜尋 SAP 系統中的 Bapi  
 在 SAP 系統使用搜尋 Bapi 的中繼資料時[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]:  
  
- 支援萬用字元搜尋運算式中。  
  
- 在其中執行搜尋作業的節點下的可搜尋。  
  
  下表列出可用來搜尋和其解譯的特殊字元[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
|特殊字元|解譯|  
|-----------------------|--------------------|  
|+ (加號)|比對一個字元。<br /><br /> 例如，A + 比對 AB、 AC、 AD|  
|* (星號)|比對零或多個字元。<br /><br /> 例如，A * 會比對的 AB，ABC。|  
  
 如需配接器支援的特殊字元的詳細資訊，請參閱[配接器介面 SAP 中繼資料的運作方式？](https://msdn.microsoft.com/library/dd788039.aspx)  
  
 執行下列步驟來搜尋 SAP 系統使用的 Bapi [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
#### <a name="to-search-bapis-in-an-sap-system"></a>搜尋 SAP 系統中的 Bapi  
  
1. 連接到 SAP 伺服器使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 請參閱[連接到 Visual Studio 中的 SAP 系統](../../adapters-and-accelerators/adapter-sap/connect-to-the-sap-system-in-visual-studio.md)如需相關指示。  
  
2. 從**選取合約的型別**下拉式清單中，選取 根據不論您將會搜尋使用配接器的輸入或輸出作業的合約型別。  
  
3. 在 **選取一個類別**方塊中，按一下包含您想要搜尋的 BAPI BAPI 功能區域。  
  
   > [!NOTE]
   >  您可以搜尋只能在根層級的 Bapi。  
  
4. 在 **分類中的搜尋**文字方塊中，輸入要搜尋特定的 BAPI 的搜尋運算式。 例如，若要搜尋名稱中有 「 帳戶 」 的 Bapi，輸入 * 帳戶\*在文字方塊中。  
  
5. 按一下向右箭號圖示，開始搜尋 按鈕。 搜尋完成後**可用的類別和作業**方塊會列出符合搜尋準則的 Bapi。  
  
6. 下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]列出 BAPI 搜尋結果。  
  
    ![搜尋 SAP 系統中的 Bapi](../../adapters-and-accelerators/adapter-sap/media/82771a47-b656-473e-a96d-998bced38b35.gif "82771a47-b656-473e-a96d-998bced38b35")  
  
## <a name="generating-schema-for-biztalk-projects"></a>對於 BizTalk 專案中產生結構描述  
 您可以使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]來產生結構描述選取 SAP 成品。 一旦您瀏覽並搜尋您想要叫用的成品，您可以產生之成品的結構描述，並傳送訊息，符合結構描述，SAP 系統。  
  
> [!NOTE]
>  您可以選取類別目錄節點，以傳回該類別目錄子樹狀目錄中的所有作業 — 比方說，您可以在其中選取整個 BAPI 子功能會 （以產生該群組中的所有 Bapi 結構描述），或選取要都產生的只有這些 Bapi 結構描述特定的 Bapi。 如需有關節點的詳細資訊，請參閱[中繼資料節點 IDs4](../../adapters-and-accelerators/adapter-sap/metadata-node-ids4.md)。  
  
#### <a name="to-retrieve-metadata-for-bapis"></a>若要擷取 Bapi 的中繼資料  
  
1. 連接到 SAP 伺服器使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。 請參閱[連接到 Visual Studio 中的 SAP 系統](../../adapters-and-accelerators/adapter-sap/connect-to-the-sap-system-in-visual-studio.md)如需相關指示。  
  
2. 從**選取合約的型別**下拉式清單中，選取 根據是否將會執行使用配接器的輸入或輸出作業的合約型別。  
  
3. 在 **選取一個類別**方塊中，按一下包含您要產生中繼資料的 BAPI 的 BAPI 功能群組。  
  
4. 在 **可用的類別和作業**方塊中，選取您要產生的中繼資料，並按一下的作業的功能區域**新增**。 會列出所選的功能區域或 operations**新增的類別和作業** 方塊中。  
  
    下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]列出所選的 Bapi。  
  
    ![擷取 BAPI 的中繼資料](../../adapters-and-accelerators/adapter-sap/media/74170978-aef0-46c9-a6e2-36d6e9c2aefc.gif "74170978-aef0-46c9-a6e2-36d6e9c2aefc")  
  
    如果您想要產生結構描述的多個作業，可能會有一些重複的項目定義，在這些失敗可能導致編譯 BizTalk 專案的結構描述之間。 例如，假設您用來產生 「 Op1"作業的結構描述。 「 資料 Op1"的結構描述包含複雜資料類型"CT1"的參數。 在您關閉之後產生結構描述的 「 資料 Op1"[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]並重新開啟，以產生結構描述的另一項作業 」 Op2"。 假設"Op2 」 也包含複雜資料類型"CT1"的參數。 您在結束之後[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]編譯專案時，就會發生編譯錯誤，因為複雜資料型別"CT1 」 定義兩次在不同的 XSD 檔案。 在這種情況下，我們建議下列各項：  
  
   - 產生的所有作業的結構描述中的單一執行[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。 這可確保[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]會產生複雜的資料類型"CT1 」 只有一個定義。  
  
   - 如果您想要在每次執行會產生多個作業的結構描述[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，請確定您已選取**產生唯一的結構描述型別**核取方塊，使所產生的 XSD 檔案包含複雜的唯一命名空間資料類型"CT1 」。  
  
5. 按一下 [確定] 。 結構描述檔案會儲存具有.xsd 副檔名為 BizTalk 專案的所在位置。  
  
   > [!NOTE]
   >  如果您使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，根據預設，檔案會建立命名慣例 「 SAPBinding\<n\>.xsd"，其中 'n' 可以是 1，2，等取決於建立的結構描述檔案的數目。 或者，您可以提供自訂結構描述檔案名稱中輸入名稱**檔案名稱前置詞**文字方塊。 [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]現在會建立結構描述檔案，命名慣例\<檔案名稱前置詞\>\<n\>.xsd。  
   > 
   > [!NOTE]
   >  [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]也會建立包含您在產生結構描述時所指定的繫結屬性的繫結檔案 （XML 檔案） 的作業和叫用作業的 SOAP 動作。 您可以匯入在 BizTalk Server 管理 主控台中建立 WCF 自訂連接埠的連線 URI，繫結屬性與此繫結檔案和設定的 SOAP 動作。 如需詳細資訊，請參閱 <<c0> [ 設定的實體連接埠繫結使用的連接埠繫結檔案至 SAP](../../adapters-and-accelerators/adapter-sap/configure-a-physical-port-binding-using-a-port-binding-file-to-sap.md)。
  
6. 按一下 [ **檔案** ] 功能表上的 [ **全部儲存**]。  
  
## <a name="generating-a-wcf-client-for-bapi-operations-using-the-add-adapter-service-reference-plug-in"></a>產生 WCF 用戶端使用的 BAPI 作業的新增配接器服務參考外掛程式  
 您可以使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]產生 WCF 用戶端程式碼 （輸入的作業不支援 Bapi） 的 BAPI 作業的。  
  
#### <a name="to-generate-a-wcf-client-for-bapis"></a>若要產生 WCF 用戶端的 Bapi  
  
1. 在  [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，從**選取合約的型別**下拉式清單中，選取**用戶端 （傳出作業）**。  
  
2. 在 [**選取類別目錄**方塊中，展開**BAPI** ] 節點，然後瀏覽或搜尋 BAPI 類別或您要產生 WCF 用戶端作業。  
  
3. 在 **可用的類別和作業**方塊中，選取您要產生 WCF 用戶端，然後按一下 類別目錄 （BAPI 功能群組） 的作業**新增**。 選取的作業都會列入**新增的類別和作業** 方塊中。 您可以選取任何節點中所列**可用的類別和作業** 方塊中。 如果您選取類別節點，則會選取所有可用的作業在該節點和其子節點下。  
  
   > [!IMPORTANT]
   >  [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]會產生唯一的 WCF 用戶端類別的每個商務物件。 根據分類和您選取的作業，可能會產生一個以上的 WCF 用戶端類別。 如需詳細資訊，請參閱 <<c0> [ 產生 WCF 用戶端或 SAP 解決方案成品的 WCF 服務合約](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md)。  
  
4. 在大部分情況下，預設的序列化選項已足夠;不過，如有需要您可以控制所產生的程式碼的幾個層面和序列化程式所使用的類型。 若要設定這些選項：  
  
   1. 按一下 [**進階選項**來開啟**進階選項**] 方塊中。  
  
   2. 在 **進階選項**下方**選擇選項，以產生的 proxy**，選取您想要的選項。 例如，您可以選取是否非同步方法會產生 WCF 用戶端，或停用設定檔的產生。  
  
   3. 底下**序列化程式**選取應該使用的序列化程式。  
  
      下圖顯示**進階選項**隨附的預設選取項目 (**自動**選取如已選取序列化程式和任何其他選項)。  
  
      ![[進階選項] 方塊預設設定](../../adapters-and-accelerators/adapter-oracle-database/media/r2-net-adapters-oracle-msb-advanced-options.gif "R2_NET_Adapters_Oracle_MSB_Advanced_Options")  
  
      您可以在設定的選項**進階選項**方塊會相當於一些可用的選項，當您使用 ServiceModel Metadata Utility Tool (svcutil.exe)。 如需這些選項的詳細資訊，請參閱[ServiceModel Metadata Utility Tool (Svcutil.exe)](https://msdn.microsoft.com/library/aa347733.aspx)。 
  
5. 按一下 [確定] 。 [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]將 WCF 用戶端類別和協助程式程式碼儲存在您選取的作業和類別目錄的專案目錄中。 根據預設，也會儲存組態檔。 如需詳細資訊，請參閱 <<c0> [ 產生 WCF 用戶端或 SAP 解決方案成品的 WCF 服務合約](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md)。  
  
## <a name="see-also"></a>另請參閱  
 [在 Visual Studio 中取得 SAP 作業的中繼資料](../../adapters-and-accelerators/adapter-sap/get-metadata-for-sap-operations-in-visual-studio.md)