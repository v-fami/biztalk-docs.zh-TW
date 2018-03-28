---
title: 瀏覽、 搜尋及取得 Siebel 作業的中繼資料 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- metadata, retrieving
- how to, browse metadata
- how to, retrieve metadata
- retrieving, metadata
- metadata, browsing
- browsing, metadata
- metadata, searching
- how to, seach metadata
- searching, metadata
ms.assetid: 7e474d8e-b030-47ea-b1b6-8048cddbba8a
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 68e7d8dc1b067096f118eb1145554edf0b11f605
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="browse-search-and-get-metadata-for-siebel-operations"></a>瀏覽、 搜尋及取得 Siebel 作業的中繼資料
本節提供有關如何使用資訊[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]、 [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，而[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]。 使用這些[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]元件，您可以：  
  
-   瀏覽要為其擷取中繼資料的作業。  
  
-   搜尋作業為其擷取中繼資料。  
  
-   加入選取的作業的訊息結構描述和連接埠繫結的組態檔來[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]專案時使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。  
  
-   WCF 用戶端類別或選取的作業和組態檔 (app.config) 的 WCF 服務合約 （介面） 的非 BizTalk 程式設計專案時加入使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
> [!NOTE]
>  [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]、 [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，而[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]呈現基本上相同的介面，當您瀏覽和搜尋作業，因此在相同主題中涵蓋所有的三個元件時。  
  
## <a name="prerequisites"></a>필수 구성 요소  
 您可以瀏覽、 搜尋，或擷取目標作業的中繼資料之前，您必須連接至 Siebel 系統。 如需有關如何連接至 Siebel 系統中，當您使用資訊[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]、 [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，請參閱[連接到 Visual Studio 中的 Siebel 系統](../../adapters-and-accelerators/adapter-siebel/connect-to-the-siebel-system-in-visual-studio.md)。  
  
## <a name="browsing-metadata"></a>瀏覽中繼資料  
 在瀏覽中繼資料使用時[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]、 [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]、[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]介面：  
  
-   可對 Siebel 商務元件這類的作業可以插入、 查詢、 更新和刪除。  
  
-   配接器用戶端可以叫用的商務服務方法。  
  
> [!NOTE]
>  使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]、 [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，您可以瀏覽使用 Windows 介面的類別和作業節點。  
  
 如需有關如何瀏覽 Siebel 中繼資料的詳細資訊，請參閱[瀏覽、 搜尋和 get Siebel 中繼資料](../../adapters-and-accelerators/adapter-siebel/browse-search-and-get-siebel-metadata.md) 
  
 執行下列步驟來瀏覽 Siebel 系統使用的中繼資料[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
#### <a name="to-browse-metadata-in-a-siebel-system"></a>若要在 Siebel 系統中，瀏覽中繼資料  
  
1.  連接至 Siebel 系統使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 請參閱[連接到 Visual Studio 中的 Siebel 系統](../../adapters-and-accelerators/adapter-siebel/connect-to-the-siebel-system-in-visual-studio.md)如需相關指示。  
  
2.  從**選取合約型別**下拉式清單中，選取 根據是否將執行使用配接器的輸入或輸出作業的合約的型別。  
  
3.  **選取類別目錄**方塊清單**商務物件**和**商務服務**節點。 按一下**商務物件**節點，查看清單中的商務物件**可用的類別和作業**方塊。 或者，您可以看到商務物件的清單，方法是展開**商務物件**節點。  
  
    > [!TIP]
    >  您可以直接移至 「 立即 」 的類別目錄節點或子類別目錄節點的樹狀目錄中，輸入中的成品名稱時的焦點所在的樹狀檢閱中**選取類別目錄**方塊。 例如，若要跳至**帳戶**商務物件，將焦點放在**商務物件** 節點，然後輸入`Account`。  
  
4.  按一下商務物件，若要查看特定的商務物件的商務元件的清單。 或者，您可以看到商務元件的清單展開商務物件。  
  
5.  按一下商務元件，若要查看特定的商務元件之支援的作業清單。  
  
     下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，其中會列出商務物件、 商務元件和支援的作業。  
  
     ![瀏覽 Siebel 商務元件](../../adapters-and-accelerators/adapter-siebel/media/11c63383-4269-4ba0-909b-e2cbec7eae04.gif "11c63383-4269-4ba0-909b-e2cbec7eae04")  
  
6.  按一下**商務服務**節點，查看清單中的商務服務的**可用的類別和作業**方塊。 或者，您可以看到的資料表清單，方法是展開**商務服務**節點。  
  
7.  按一下 商務服務，若要查看對應的商務服務方法的清單。  
  
     下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，其中會列出商務服務和對應的商務服務方法。  
  
     ![瀏覽 Siebel 商務服務](../../adapters-and-accelerators/adapter-siebel/media/60405c18-6035-42a5-851f-a0ed6d0570d6.gif "60405c18-6035-42a5-851f-a0ed6d0570d6")  
  
## <a name="searching-metadata"></a>搜尋中繼資料  
 搜尋 Siebel 中繼資料使用時[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]、 [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]:  
  
-   支援萬用字元和逸出字元。  
  
-   啟用立即節點下搜尋在其中執行搜尋作業。 例如，若要搜尋的商務服務，您必須搜尋 \Business 服務 下。  
  
 下表列出可用於搜尋和由其解譯的特殊字元[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。  
  
|特殊字元|解譯|  
|-----------------------|--------------------|  
|? （問號）|完全符合一個字元<br /><br /> 例如，A？比對 AB、 AC、 AD。|  
|* (星號)|比對零個或多個字元。<br /><br /> 例如，A * 比對 A，AB，ABC。|  
  
 執行下列步驟，以搜尋中繼資料中使用 Siebel 系統[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
#### <a name="to-search-metadata-in-a-siebel-system"></a>若要在 Siebel 系統中搜尋中繼資料  
  
1.  連接至 Siebel 系統使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 請參閱[連接到 Visual Studio 中的 Siebel 系統](../../adapters-and-accelerators/adapter-siebel/connect-to-the-siebel-system-in-visual-studio.md)如需相關指示。  
  
2.  從**選取合約型別**下拉式清單中選取**用戶端 （輸出作業）**合約。  
  
3.  在**選取類別目錄**方塊中，按一下**商務物件**節點。  
  
4.  若要搜尋特定的商務物件，請按一下**商務物件**節點**類別目錄中的搜尋**文字方塊並輸入搜尋運算式。 例如，若要搜尋的名稱開頭為 「 帳戶 」 的商務物件，輸入**帳戶\***在文字方塊中。  
  
5.  按一下向右箭號圖示，開始搜尋 按鈕。 搜尋完成之後，**可用的類別和作業**方塊會列出符合搜尋準則的商務物件。  
  
6.  若要搜尋特定的商務元件在商務物件中，按一下 商務物件和中**類別目錄中的搜尋**文字方塊中輸入搜尋運算式。 例如，若要搜尋的商務元件，以 「 帳戶 」 開頭的名稱，輸入**帳戶\***在文字方塊中。  
  
7.  按一下向右箭號圖示，開始搜尋 按鈕。 搜尋完成之後，**可用的類別和作業**方塊會列出符合搜尋準則的商務元件。  
  
8.  若要搜尋商務元件的特定作業，請按一下 商務元件和**類別目錄中的搜尋**文字方塊中輸入搜尋運算式。 例如，若要搜尋名稱開頭為 「 查詢 」 的作業，請輸入**查詢\***在文字方塊中。  
  
9. 按一下向右箭號圖示，開始搜尋 按鈕。 搜尋完成之後，**可用的類別和作業**方塊會列出符合搜尋準則的商務元件。  
  
     下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，其中會列出搜尋結果。  
  
     ![搜尋商務元件](../../adapters-and-accelerators/adapter-siebel/media/siebel-adpt-lesson1-step3-04-search.gif "SIEBEL-ADPT-Lesson1-Step3-04-search")  
  
     執行類似的程序，來搜尋下**商務服務**節點。  
  
## <a name="generating-schema-for-biztalk-projects"></a>產生結構描述的 BizTalk 專案  
 您可以使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]產生選取的 Siebel 成品的結構描述。 一旦您瀏覽並搜尋您想要叫用的成品，您可以產生結構描述的那些成品，並傳送訊息，符合結構描述到 Siebel。  
  
> [!NOTE]
>  您可以選取要在該類別目錄子樹狀結構中傳回所有作業類別目錄節點： 例如，您可以在其中選取商務元件 （業務元件中產生的所有作業的結構描述） 或選取特定的作業上 （適用於商務元件例如，Insert 和 Delete） 產生只有這些作業的結構描述。 如需節點的詳細資訊，請參閱[中繼資料的節點識別碼](../../adapters-and-accelerators/adapter-siebel/metadata-node-ids1.md)。  
  
#### <a name="to-generate-schema-for-siebel-artifacts"></a>若要產生結構描述的 Siebel 成品  
  
1.  連接至 Siebel 系統使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。 請參閱[連接到 Visual Studio 中的 Siebel 系統](../../adapters-and-accelerators/adapter-siebel/connect-to-the-siebel-system-in-visual-studio.md)如需相關指示。  
  
2.  從**選取合約型別**下拉式清單中選取**用戶端 （輸出作業）**合約。  
  
3.  在**選取類別目錄**方塊中，展開 [商務物件或商務服務] 節點。  
  
4.  在**可用的類別和作業**方塊中，選取商務元件或商務服務或您想要產生中繼資料，然後按一下對應的作業**新增**。 會列出選取的功能區域或作業**加入的類別和作業**方塊。  
  
     下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，其中會列出選取的作業。  
  
     ![擷取商務物件的中繼資料](../../adapters-and-accelerators/adapter-siebel/media/siebel-adpt-lesson1-step3-05-get.gif "SIEBEL-ADPT-Lesson1-Step3-05-get")  
  
     如果您想要產生結構描述的多個作業，可能是在這些失敗可能導致編譯 BizTalk 專案的結構描述之間的一些重複的項目定義。 例如，假設您用來產生 「 Op1 」 作業的結構描述。 「 Op1"的結構描述包含複雜資料類型"CT1"的參數。 在您關閉之後產生結構描述的 「 Op1" [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ，再重新開啟 「 Op2"的另一個作業產生結構描述。 假設 「 Op2 」 也包含複雜資料類型"CT1"的參數。 結束之後[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]編譯專案，就會發生編譯錯誤，因為複雜資料型別"CT1 」 定義不同的 XSD 檔案中的兩倍。 在這種情況下，我們建議下列各項：  
  
    -   產生的所有作業的結構描述中的單一執行[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。 如此可確保[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]會產生只有一個定義的複雜資料型別"CT1"。  
  
    -   如果您想要產生多個作業的結構描述的不同執行[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，請確定您選取**產生唯一的結構描述型別**核取方塊，以便讓所產生的 XSD 檔案包含複雜的唯一命名空間資料型別"CT1"。  
  
5.  按一下 **[確定]**。 結構描述檔案會儲存具有.xsd 副檔名為 BizTalk 專案的相同位置。  
  
     根據預設，檔案會建立命名慣例 」 SiebelBindingSchema\<n\>.xsd"，其中 'n' 可以是 1、 2，依此類推，依照建立的結構描述檔案的數目。 或者，您可以提供自訂結構描述檔案名稱中輸入名稱**檔案名稱前置詞**文字方塊。 [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]現在建立結構描述檔案命名慣例\<檔案名稱前置詞\>結構描述\<n\>.xsd。  
  
    > [!NOTE]
    >  [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]也會建立包含時指定的繫結屬性的繫結檔案 （XML 檔案） 產生的結構描述的作業和要叫用作業的 SOAP 動作。 您可以匯入此繫結檔案，在 BizTalk Server 管理主控台中，建立 WCF 自訂連接埠與連接 URI，繫結屬性和設定的 SOAP 動作。 如需詳細資訊，請參閱[設定實體連接埠繫結使用連接埠繫結檔案至 Siebel](../../adapters-and-accelerators/adapter-siebel/configure-a-physical-port-binding-using-a-port-binding-file-to-siebel.md)。  
  
6.  按一下 [ **檔案** ] 功能表上的 [ **全部儲存**]。  
  
## <a name="generating-a-wcf-client-using-the-add-adapter-service-reference-plug-in"></a>產生使用 WCF 用戶端新增配接器服務參考外掛程式  
 您可以使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]產生 WCF 用戶端程式碼的輸出 Siebel 系統上的作業。  
  
#### <a name="to-generate-a-wcf-client"></a>若要產生 WCF 用戶端  
  
1.  在[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，從**選取合約型別**下拉式清單中選取**用戶端 （輸出作業）**。  
  
2.  在**選取類別目錄**方塊中，展開 [商務物件或商務服務] 節點。  
  
3.  在**可用的類別和作業**方塊中，選取商務元件、 商務服務或您想要產生 WCF 用戶端，然後按一下對應的作業**新增**。 會列出選取的功能區域或作業**加入的類別和作業**方塊。 您可以選取任何節點中所列**可用的類別和作業**方塊。 如果您選取類別目錄 節點，則會選取所有適用於該節點和其子節點的作業。  
  
    > [!IMPORTANT]
    >  根據您選取的作業和類別，可能會產生一個以上的 WCF 用戶端類別。 如需詳細資訊，請參閱[產生 WCF 用戶端或 WCF 服務合約的 Siebel 方案成品](../../adapters-and-accelerators/adapter-siebel/generate-a-wcf-client-or-a-wcf-service-contract-for-siebel-solution-artifacts.md)。  
  
4.  在大部分情況下，預設序列化選項已經足夠;不過，如果需要您可以控制所產生的程式碼的幾個層面和序列化程式所使用的類型。 若要設定這些選項：  
  
    1.  若要開啟**進階選項**方塊中，按一下**進階選項**。  
  
    2.  在**進階選項**下方的 **選擇選項來產生 proxy**，選取您想要的選項。 例如，您可以選取是否產生 WCF 用戶端的非同步方法，或您可以停用組態檔的產生。  
  
    3.  在下**序列化程式**，選取應該使用的序列化程式。  
  
     下圖顯示**進階選項**隨附的預設選項 (**自動**選取所選的序列化程式，且沒有其他選項)。  
  
     ![[進階選項] 方塊預設設定](../../adapters-and-accelerators/adapter-oracle-database/media/r2-net-adapters-oracle-msb-advanced-options.gif "R2_NET_Adapters_Oracle_MSB_Advanced_Options")  
  
     您可以在設定的選項**進階選項**方塊相當於某些可用的選項時使用 ServiceModel Metadata Utility Tool (svcutil.exe)。 如需有關這些選項的詳細資訊，請參閱[ServiceModel Metadata Utility Tool (Svcutil.exe)](https://msdn.microsoft.com/library/aa347733.aspx)。
  
5.  按一下 **[確定]**。 [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]儲存 WCF 用戶端類別和協助程式程式碼的作業和專案目錄中所選取的類別。 根據預設，也會儲存組態檔。 如需詳細資訊，請參閱[產生 WCF 用戶端或 WCF 服務合約的 Siebel 方案成品](../../adapters-and-accelerators/adapter-siebel/generate-a-wcf-client-or-a-wcf-service-contract-for-siebel-solution-artifacts.md)。  
  
## <a name="see-also"></a>另請參閱  
 [在 Visual Studio 中取得 Siebel 作業的中繼資料](../../adapters-and-accelerators/adapter-siebel/get-metadata-for-siebel-operations-in-visual-studio.md)