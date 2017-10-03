---
title: "瀏覽、 搜尋，並取得中繼資料中 SAP 的 BAPI 作業 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
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
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7ef2594346552ee707705a3bb3398e2bbce70126
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="browse-search-and-get-metadata-for-bapi-operations-in-sap"></a>瀏覽、 搜尋和 SAP 中的 BAPI 作業取得中繼資料
本節提供有關如何瀏覽、 搜尋和中繼資料擷取 BAPI 作業使用的 SAP 指示[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。 大部分的指示會針對所有三種使用者介面相同。 只要適用的話，個別的程序提供相關的使用者介面。  
  
 執行下列各節將提供的步驟之前，您必須：  
  
-   建立[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]專案。  
  
-   連接到 SAP 系統使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 如需指示，請參閱[連接到 Visual Studio 中的 SAP 系統](../../adapters-and-accelerators/adapter-sap/connect-to-the-sap-system-in-visual-studio.md)。  
  
## <a name="browsing-bapis-in-an-sap-system"></a>SAP 系統中的瀏覽 Bapi  
 在瀏覽中繼資料使用時[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] Bapi 會呈現為商務物件和 rfc。 瀏覽 Bapi rfc 是類似於瀏覽 RFC，SAP 系統中。 在此情況下，Bapi 是在 Rfc 可用**RFC**。 如需有關如何瀏覽 Rfc 的詳細資訊，請參閱[瀏覽、 搜尋和 sap RFC 作業的 get 中繼資料](../../adapters-and-accelerators/adapter-sap/browse-search-and-get-metadata-for-rfc-operations-in-sap.md)。  
  
 本節提供 瀏覽 Bapi 為商務物件的資訊。 如需有關如何瀏覽 SAP 中繼資料的詳細資訊，請參閱[配接器介面的 SAP 中繼資料的運作方式？](https://msdn.microsoft.com/library/dd788039.aspx)  
  
 執行下列步驟，在 SAP 系統使用瀏覽 Bapi [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
 
  
#### <a name="to-browse-bapis-in-an-sap-system"></a>若要瀏覽 SAP 系統中的 Bapi  
  
1.  連接到 SAP 伺服器使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 請參閱[連接到 Visual Studio 中的 SAP 系統](../../adapters-and-accelerators/adapter-sap/connect-to-the-sap-system-in-visual-studio.md)如需相關指示。  
  
2.  從**選取合約型別**下拉式清單中，選取 根據是否將執行使用配接器的輸入或輸出作業的合約的型別。  
  
3.  在**選取類別目錄**方塊中，按一下要查看的 BAPI 功能區域中的 BAPI 節點**可用的類別和作業**方塊。 或者，您也可以在展開 BAPI 節點，查看 BAPI 功能區域。  
  
    > [!TIP]
    >  您可以直接移至 「 立即 」 的類別目錄節點或子類別目錄節點的樹狀目錄中，輸入中的成品名稱時的焦點所在的樹狀檢閱中**選取類別目錄**方塊。 例如，若要跳至**控制**BAPI 功能區域中，將焦點放在**BAPI**  節點，然後輸入`Controlling`。  
  
     下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]列出 BAPI 功能區域。  
  
     ![瀏覽 BAPI 中的功能區域](../../adapters-and-accelerators/adapter-sap/media/d4b03725-44d2-449d-a035-491cd7415139.gif "d4b03725-44d2-449d-a035-491cd7415139")  
  
4.  按一下以查看進一步的分類的 BAPI 功能區域的 BAPI 功能區域。  
  
5.  按一下以查看支援該功能區域的相關操作的 BAPI 功能區域。 下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]以支援特定功能區域的作業。  
  
     ![瀏覽 BAPI 的](../../adapters-and-accelerators/adapter-sap/media/1a9be42e-1f9e-4cf6-a555-c4e755fcc0ea.gif "1a9be42e-1f9e-4cf6-a555-c4e755fcc0ea")  
  
## <a name="searching-bapis-in-an-sap-system"></a>搜尋 SAP 系統中的 Bapi  
 在 SAP 系統使用搜尋 Bapi 的中繼資料時[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]:  
  
-   支援萬用字元搜尋運算式中。  
  
-   啟用立即節點下搜尋在其中執行搜尋作業。  
  
 下表列出可用於搜尋和由其解譯的特殊字元[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
|特殊字元|解譯|  
|-----------------------|--------------------|  
|+ (加號)|比對一個字元。<br /><br /> 例如，A + 比對 AB、 AC、 AD|  
|* (星號)|比對零個或多個字元。<br /><br /> 例如，A * 比對 A，AB，ABC。|  
  
 如需配接器支援的特殊字元的詳細資訊，請參閱[配接器介面的 SAP 中繼資料的運作方式？](https://msdn.microsoft.com/library/dd788039.aspx)  
  
 執行下列步驟，以搜尋 SAP 系統使用中的 Bapi [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
#### <a name="to-search-bapis-in-an-sap-system"></a>搜尋 SAP 系統中的 Bapi  
  
1.  連接到 SAP 伺服器使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 請參閱[連接到 Visual Studio 中的 SAP 系統](../../adapters-and-accelerators/adapter-sap/connect-to-the-sap-system-in-visual-studio.md)如需相關指示。  
  
2.  從**選取合約型別**下拉式清單中，選取 根據是否您將會搜尋使用配接器的輸入或輸出作業的合約的型別。  
  
3.  在**選取類別目錄**方塊中，按一下包含您想要搜尋的 BAPI 的 BAPI 功能區域。  
  
    > [!NOTE]
    >  您可以搜尋 Bapi 只能在根層級。  
  
4.  在**類別目錄中的搜尋**文字方塊中，輸入要搜尋特定的 BAPI 搜尋運算式。 例如，若要搜尋名稱中有 「 帳戶 」 的 Bapi，請輸入 * 帳戶\*在文字方塊中。  
  
5.  按一下向右箭號圖示，開始搜尋 按鈕。 搜尋完成之後，**可用的類別和作業**方塊會列出符合搜尋準則的 Bapi。  
  
6.  下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]列出 BAPI 搜尋結果。  
  
     ![搜尋 SAP 系統中的 Bapi](../../adapters-and-accelerators/adapter-sap/media/82771a47-b656-473e-a96d-998bced38b35.gif "82771a47-b656-473e-a96d-998bced38b35")  
  
## <a name="generating-schema-for-biztalk-projects"></a>產生結構描述的 BizTalk 專案  
 您可以使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]產生結構描述選取 SAP 成品。 一旦您瀏覽並搜尋您想要叫用的成品，您可以產生結構描述的那些成品，並傳送訊息，符合結構描述至 SAP 系統。  
  
> [!NOTE]
>  您可以選取要在該類別目錄子樹狀結構中傳回所有作業類別目錄節點： 例如，您可以選取整個 BAPI 子功能會 （若要產生該群組中的所有 Bapi 結構描述） 或選取特定的 Bapi 產生這些的 Bapi 結構描述。 如需節點的詳細資訊，請參閱[中繼資料節點 IDs4](../../adapters-and-accelerators/adapter-sap/metadata-node-ids4.md)。  
  
#### <a name="to-retrieve-metadata-for-bapis"></a>若要擷取 Bapi 的中繼資料  
  
1.  連接到 SAP 伺服器使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。 請參閱[連接到 Visual Studio 中的 SAP 系統](../../adapters-and-accelerators/adapter-sap/connect-to-the-sap-system-in-visual-studio.md)如需相關指示。  
  
2.  從**選取合約型別**下拉式清單中，選取 根據是否將執行使用配接器的輸入或輸出作業的合約的型別。  
  
3.  在**選取類別目錄**方塊中，按一下包含您要產生中繼資料的 BAPI 的 BAPI 功能群組。  
  
4.  在**可用的類別和作業**方塊中，選取您要產生中繼資料，並按一下的作業的功能區域**新增**。 會列出選取的功能區域或作業**加入的類別和作業**方塊。  
  
     下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]列出所選的 Bapi。  
  
     ![擷取 BAPI 的中繼資料](../../adapters-and-accelerators/adapter-sap/media/74170978-aef0-46c9-a6e2-36d6e9c2aefc.gif "74170978-aef0-46c9-a6e2-36d6e9c2aefc")  
  
     如果您想要產生結構描述的多個作業，可能是在這些失敗可能導致編譯 BizTalk 專案的結構描述之間的一些重複的項目定義。 例如，假設您用來產生 「 Op1 」 作業的結構描述。 「 Op1"的結構描述包含複雜資料類型"CT1"的參數。 在您關閉之後產生結構描述的 「 Op1" [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ，再重新開啟 「 Op2"的另一個作業產生結構描述。 假設 「 Op2 」 也包含複雜資料類型"CT1"的參數。 結束之後[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]編譯專案，就會發生編譯錯誤，因為複雜資料型別"CT1 」 定義不同的 XSD 檔案中的兩倍。 在這種情況下，我們建議下列各項：  
  
    -   產生的所有作業的結構描述中的單一執行[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。 如此可確保[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]會產生只有一個定義的複雜資料型別"CT1"。  
  
    -   如果您想要產生多個作業的結構描述的不同執行[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，請確定您選取**產生唯一的結構描述型別**核取方塊，以便讓所產生的 XSD 檔案包含複雜的唯一命名空間資料型別"CT1"。  
  
5.  按一下 **[確定]**。 結構描述檔案會儲存具有.xsd 副檔名為 BizTalk 專案的相同位置。  
  
    > [!NOTE]
    >  如果您使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，根據預設，檔案會建立命名慣例 」 SAPBinding\<n >.xsd"，其中 'n' 可以是 1，2，等等取決於建立的結構描述檔案數目。 或者，您可以提供自訂結構描述檔案名稱中輸入名稱**檔案名稱前置詞**文字方塊。 [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]現在建立結構描述檔案命名慣例\<檔案名稱前置詞 >\<n >.xsd。  
  
    > [!NOTE]
    >  [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]也會建立包含產生結構描述時指定的繫結屬性的繫結檔案 （XML 檔案） 的作業和要叫用作業的 SOAP 動作。 您可以匯入此繫結檔案，在 BizTalk Server 管理主控台中，建立 WCF 自訂連接埠與連接 URI，繫結屬性和設定的 SOAP 動作。 如需詳細資訊，請參閱[設定實體連接埠繫結使用連接埠繫結檔案至 SAP](../../adapters-and-accelerators/adapter-sap/configure-a-physical-port-binding-using-a-port-binding-file-to-sap.md)。
  
6.  按一下 [ **檔案** ] 功能表上的 [ **全部儲存**]。  
  
## <a name="generating-a-wcf-client-for-bapi-operations-using-the-add-adapter-service-reference-plug-in"></a>產生 WCF 用戶端使用的 BAPI 作業的新增配接器服務參考外掛程式  
 您可以使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]產生 BAPI 作業 （輸入的作業不支援的 Bapi） 的 WCF 用戶端程式碼。  
  
#### <a name="to-generate-a-wcf-client-for-bapis"></a>若要產生 WCF 用戶端的 Bapi  
  
1.  在[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，從**選取合約型別**下拉式清單中選取**用戶端 （輸出作業）**。  
  
2.  在**選取類別目錄**方塊中，展開 [ **BAPI** ] 節點，然後瀏覽或搜尋 BAPI 類別或您要產生 WCF 用戶端作業。  
  
3.  在**可用的類別和作業**方塊中，選取您要產生 WCF 用戶端，然後按一下 類別目錄 （BAPI 功能群組） 的作業**新增**。 選取的作業中所列**加入的類別和作業**方塊。 您可以選取任何節點中所列**可用的類別和作業**方塊。 如果您選取類別目錄 節點，則會選取所有適用於該節點和其子節點的作業。  
  
    > [!IMPORTANT]
    >  [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]產生唯一的 WCF 用戶端類別的每個商務物件。 根據您選取的作業和類別，可能會產生一個以上的 WCF 用戶端類別。 如需詳細資訊，請參閱[產生 WCF 用戶端或 WCF 服務合約的 SAP 方案成品](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md)。  
  
4.  在大部分情況下，預設序列化選項已經足夠;不過，如果需要您可以控制所產生的程式碼的幾個層面和序列化程式所使用的類型。 若要設定這些選項：  
  
    1.  按一下**進階選項**開啟**進階選項**方塊。  
  
    2.  在**進階選項**下方的 **選擇選項來產生 proxy**，選取您想要的選項。 例如，您可以選取是否非同步方法產生 WCF 用戶端，或停用組態檔的產生。  
  
    3.  在下**序列化程式**選取應該使用的序列化程式。  
  
     下圖顯示**進階選項**隨附的預設選項 (**自動**選取所選的序列化程式，且沒有其他選項)。  
  
     ![[進階選項] 方塊預設設定](../../adapters-and-accelerators/adapter-oracle-database/media/r2-net-adapters-oracle-msb-advanced-options.gif "R2_NET_Adapters_Oracle_MSB_Advanced_Options")  
  
     您可以在設定的選項**進階選項**方塊相當於某些可用的選項時使用 ServiceModel Metadata Utility Tool (svcutil.exe)。 如需有關這些選項的詳細資訊，請參閱[ServiceModel Metadata Utility Tool (Svcutil.exe)](https://msdn.microsoft.com/library/aa347733.aspx)。 
  
5.  按一下 **[確定]**。 [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]將 WCF 用戶端類別和協助程式程式碼儲存在您選取的作業和類別目錄的專案目錄中。 根據預設，也會儲存組態檔。 如需詳細資訊，請參閱[產生 WCF 用戶端或 WCF 服務合約的 SAP 方案成品](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md)。  
  
## <a name="see-also"></a>另請參閱  
 [取得 Visual Studio 中的 SAP 作業的中繼資料](../../adapters-and-accelerators/adapter-sap/get-metadata-for-sap-operations-in-visual-studio.md)