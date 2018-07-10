---
title: 瀏覽、 搜尋及取得 Siebel 作業的中繼資料 |Microsoft Docs
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
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d4f6821f252bf2854b7ed64f57cbdf742c378c5c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36991415"
---
# <a name="browse-search-and-get-metadata-for-siebel-operations"></a>瀏覽、 搜尋及取得 Siebel 作業的中繼資料
本節提供有關如何使用資訊[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]，則[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，和[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]。 透過使用這些[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]元件，您可以：  
  
- 瀏覽作業為其擷取中繼資料。  
  
- 搜尋用來擷取中繼資料的作業。  
  
- 新增選取的作業的訊息結構描述和連接埠繫結的組態檔來[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]專案時使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。  
  
- 將 WCF 用戶端類別或選取的作業和組態檔 (app.config) 的 WCF 服務合約 （介面） 新增至非 BizTalk 的程式設計專案，當使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
> [!NOTE]
>  [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，則[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，和[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]呈現基本上相同的介面，當您瀏覽和搜尋作業，因此所有三個元件所述的相同的主題。  
  
## <a name="prerequisites"></a>先決條件  
 您可以瀏覽、 搜尋，或擷取目標作業的中繼資料之前，您必須連接到 Siebel 系統。 如需如何連接至 Siebel 系統中，當您使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，則[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或有[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，請參閱[連接至 Siebel 系統，在 Visual Studio 中](../../adapters-and-accelerators/adapter-siebel/connect-to-the-siebel-system-in-visual-studio.md)。  
  
## <a name="browsing-metadata"></a>瀏覽中繼資料  
 在瀏覽中繼資料使用時[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，則[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，則[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]介面：  
  
-   可對 Siebel 商務元件這類的作業會插入、 查詢、 更新和刪除的資料。  
  
-   配接器用戶端可以叫用的商務服務方法。  
  
> [!NOTE]
>  藉由使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，則[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，您可以瀏覽類別] 和 [作業] 節點使用 Windows 介面。  
  
 如需有關如何瀏覽 Siebel 中繼資料的詳細資訊，請參閱[瀏覽、 搜尋及取得 Siebel 中繼資料](../../adapters-and-accelerators/adapter-siebel/browse-search-and-get-siebel-metadata.md) 
  
 執行下列步驟來瀏覽 Siebel 系統使用的中繼資料[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
#### <a name="to-browse-metadata-in-a-siebel-system"></a>若要在 Siebel 系統中，瀏覽中繼資料  
  
1. 連接到 Siebel 系統 using [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 請參閱[連接到 Visual Studio 中的 Siebel 系統](../../adapters-and-accelerators/adapter-siebel/connect-to-the-siebel-system-in-visual-studio.md)如需相關指示。  
  
2. 從**選取合約的型別**下拉式清單中，選取 根據是否將會執行使用配接器的輸入或輸出作業的合約型別。  
  
3. **選取一個類別**方塊清單**商務物件**並**商務服務**節點。 按一下 [**商務物件**節點，查看清單中的商務物件**可用的類別和作業**] 方塊中。 或者，您可以看到的商務物件清單，展開**商務物件**節點。  
  
   > [!TIP]
   >  您可以直接移至 「 立即 」 的類別目錄節點或子類別目錄節點樹狀目錄中，當焦點的樹狀檢視中，輸入在成品名稱**選取一個類別** 方塊中。 例如，若要跳至**帳號**商務物件專注**商務物件**節點，然後按`Account`。  
  
4. 按一下 商務物件，若要查看特定的商務物件的商務元件的清單。 或者，您可以看到商務元件的清單，展開 商務物件。  
  
5. 按一下商務元件，若要查看支援的特定商務元件作業的清單。  
  
    下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，其中會列出商務物件，這些商務元件，以及支援的作業。  
  
    ![瀏覽 Siebel 商務元件](../../adapters-and-accelerators/adapter-siebel/media/11c63383-4269-4ba0-909b-e2cbec7eae04.gif "11c63383-4269-4ba0-909b-e2cbec7eae04")  
  
6. 按一下 [**商務服務**節點，查看清單中的商務服務**可用的類別和作業**] 方塊中。 或者，您可以看到資料表清單，展開**商務服務**節點。  
  
7. 按一下 商務服務，若要查看對應的商務服務方法的清單。  
  
    下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，其中會列出商務服務和對應的商務服務方法。  
  
    ![瀏覽 Siebel 商務服務](../../adapters-and-accelerators/adapter-siebel/media/60405c18-6035-42a5-851f-a0ed6d0570d6.gif "60405c18-6035-42a5-851f-a0ed6d0570d6")  
  
## <a name="searching-metadata"></a>搜尋中繼資料  
 搜尋 Siebel 中繼資料使用時[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，則[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]:  
  
- 支援萬用字元和逸出字元。  
  
- 在其中執行搜尋作業的節點下的可搜尋。 例如，若要搜尋的商務服務，您必須搜尋 \Business 服務 下。  
  
  下表列出可用來搜尋和其解譯的特殊字元[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。  
  
|特殊字元|解譯|  
|-----------------------|--------------------|  
|? （問號）|完全符合一個字元<br /><br /> 例如，A 嗎？比對 AB、 AC、 AD。|  
|* (星號)|比對零或多個字元。<br /><br /> 例如，A * 會比對的 AB，ABC。|  
  
 執行下列步驟，以搜尋在 Siebel 系統中使用的中繼資料[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
#### <a name="to-search-metadata-in-a-siebel-system"></a>若要在 Siebel 系統中搜尋中繼資料  
  
1. 連接到 Siebel 系統 using [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 請參閱[連接到 Visual Studio 中的 Siebel 系統](../../adapters-and-accelerators/adapter-siebel/connect-to-the-siebel-system-in-visual-studio.md)如需相關指示。  
  
2. 從**選取合約的型別**下拉式清單中，選取**用戶端 （傳出作業）** 合約。  
  
3. 在 **選取一個類別**方塊中，按一下**商務物件**節點。  
  
4. 若要搜尋特定的商務物件，請按一下**商務物件**中的節點**類別目錄中的搜尋**文字輸入的搜尋運算式。 例如，若要搜尋名稱開頭 「 帳戶 」 的商務物件，請輸入**帳號\\*** 在文字方塊中。  
  
5. 按一下向右箭號圖示，開始搜尋 按鈕。 搜尋完成後**可用的類別和作業**方塊會列出符合搜尋準則的商務物件。  
  
6. 若要搜尋特定的商務元件在商務物件中，按一下 商務物件，並在**分類中的搜尋**文字方塊中，輸入的搜尋運算式。 例如，若要搜尋名稱開頭 「 帳戶 」 的商務元件，輸入**帳號\\*** 在文字方塊中。  
  
7. 按一下向右箭號圖示，開始搜尋 按鈕。 搜尋完成後**可用的類別和作業**方塊會列出符合搜尋準則的商務元件。  
  
8. 若要搜尋特定的商務元件作業，請按一下 商務元件和在**類別中的搜尋**文字方塊中，輸入的搜尋運算式。 例如，若要搜尋名稱開頭的 「 查詢 」 的作業，請輸入**查詢\\*** 在文字方塊中。  
  
9. 按一下向右箭號圖示，開始搜尋 按鈕。 搜尋完成後**可用的類別和作業**方塊會列出符合搜尋準則的商務元件。  
  
     下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，其中會列出搜尋結果。  
  
     ![搜尋商務元件](../../adapters-and-accelerators/adapter-siebel/media/siebel-adpt-lesson1-step3-04-search.gif "SIEBEL-ADPT-Lesson1-Step3-04-search")  
  
     執行類似的程序下搜尋**商務服務**節點。  
  
## <a name="generating-schema-for-biztalk-projects"></a>對於 BizTalk 專案中產生結構描述  
 您可以使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]產生選取的 Siebel 成品的結構描述。 一旦您瀏覽並搜尋您想要叫用的成品，您可以產生之成品的結構描述，並傳送訊息，符合結構描述，siebel。  
  
> [!NOTE]
>  您可以選取類別目錄節點，以傳回該類別目錄子樹狀目錄中的所有作業，例如，您可以在其中選取商務元件 （以業務元件中產生的所有作業的結構描述） 或選取特定的作業上 （適用於商務元件範例中，Insert 和 Delete） 產生結構描述的作業。 如需有關節點的詳細資訊，請參閱[中繼資料節點識別碼](../../adapters-and-accelerators/adapter-siebel/metadata-node-ids1.md)。  
  
#### <a name="to-generate-schema-for-siebel-artifacts"></a>若要產生結構描述的 Siebel 成品  
  
1. 連接到 Siebel 系統 using[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。 請參閱[連接到 Visual Studio 中的 Siebel 系統](../../adapters-and-accelerators/adapter-siebel/connect-to-the-siebel-system-in-visual-studio.md)如需相關指示。  
  
2. 從**選取合約的型別**下拉式清單中，選取**用戶端 （傳出作業）** 合約。  
  
3. 在 **選取一個類別**方塊中，展開 商務物件或商務服務 節點。  
  
4. 在 **可用的類別和作業**方塊中，選取商務元件或商務服務或對應的作業，您想要產生中繼資料，然後按**新增**。 會列出所選的功能區域或 operations**新增的類別和作業** 方塊中。  
  
    下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，其中會列出選取的作業。  
  
    ![擷取商務物件的中繼資料](../../adapters-and-accelerators/adapter-siebel/media/siebel-adpt-lesson1-step3-05-get.gif "SIEBEL-ADPT-Lesson1-Step3-05-get")  
  
    如果您想要產生結構描述的多個作業，可能會有一些重複的項目定義，在這些失敗可能導致編譯 BizTalk 專案的結構描述之間。 例如，假設您用來產生 「 Op1"作業的結構描述。 「 資料 Op1"的結構描述包含複雜資料類型"CT1"的參數。 在您關閉之後產生結構描述的 「 資料 Op1"[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]並重新開啟，以產生結構描述的另一項作業 」 Op2"。 假設"Op2 」 也包含複雜資料類型"CT1"的參數。 您在結束之後[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]編譯專案時，就會發生編譯錯誤，因為複雜資料型別"CT1 」 定義兩次在不同的 XSD 檔案。 在這種情況下，我們建議下列各項：  
  
   - 產生的所有作業的結構描述中的單一執行[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。 這可確保[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]會產生複雜的資料類型"CT1 」 只有一個定義。  
  
   - 如果您想要在每次執行會產生多個作業的結構描述[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，請確定您已選取**產生唯一的結構描述型別**核取方塊，使所產生的 XSD 檔案包含複雜的唯一命名空間資料類型"CT1 」。  
  
5. 按一下 [確定] 。 結構描述檔案會儲存具有.xsd 副檔名為 BizTalk 專案的所在位置。  
  
    根據預設，檔案會建立命名慣例 「 SiebelBindingSchema\<n\>.xsd"，其中 'n' 可以是 1，2，依此類推，根據建立的結構描述檔案的數目。 或者，您可以提供自訂結構描述檔案名稱中輸入名稱**檔案名稱前置詞**文字方塊。 [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]現在會建立結構描述檔案，命名慣例\<檔案名稱前置詞\>結構描述\<n\>.xsd。  
  
   > [!NOTE]
   >  [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]也會建立包含時所指定的繫結屬性的繫結檔案 （XML 檔案） 產生的作業和 SOAP 動作叫用作業的結構描述。 您可以匯入在 BizTalk Server 管理 主控台中建立 WCF 自訂連接埠的連線 URI，繫結屬性與此繫結檔案和設定的 SOAP 動作。 如需詳細資訊，請參閱 <<c0> [ 設定的實體連接埠繫結使用的連接埠繫結檔案至 Siebel](../../adapters-and-accelerators/adapter-siebel/configure-a-physical-port-binding-using-a-port-binding-file-to-siebel.md)。  
  
6. 按一下 [ **檔案** ] 功能表上的 [ **全部儲存**]。  
  
## <a name="generating-a-wcf-client-using-the-add-adapter-service-reference-plug-in"></a>產生 WCF 用戶端使用新增配接器服務參考外掛程式  
 您可以使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]來產生 WCF 用戶端程式碼，針對 Siebel 系統上的傳出作業。  
  
#### <a name="to-generate-a-wcf-client"></a>若要產生 WCF 用戶端  
  
1. 在  [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，從**選取合約的型別**下拉式清單中，選取**用戶端 （傳出作業）**。  
  
2. 在 **選取一個類別**方塊中，展開 商務物件或商務服務 節點。  
  
3. 在 **可用的類別和作業**方塊中，選取 商務元件、 商務服務或對應的作業，您想要產生 WCF 用戶端，然後按**新增**。 會列出所選的功能區域或 operations**新增的類別和作業** 方塊中。 您可以選取任何節點中所列**可用的類別和作業** 方塊中。 如果您選取類別節點，則會選取所有可用的作業在該節點和其子節點下。  
  
   > [!IMPORTANT]
   >  根據分類和您選取的作業，可能會產生一個以上的 WCF 用戶端類別。 如需詳細資訊，請參閱 <<c0> [ 產生 WCF 用戶端或 Siebel 解決方案成品的 WCF 服務合約](../../adapters-and-accelerators/adapter-siebel/generate-a-wcf-client-or-a-wcf-service-contract-for-siebel-solution-artifacts.md)。  
  
4. 在大部分情況下，預設的序列化選項已足夠;不過，如有需要您可以控制所產生的程式碼的幾個層面和序列化程式所使用的類型。 若要設定這些選項：  
  
   1. 若要開啟 **進階選項**方塊中，按一下**進階選項**。  
  
   2. 在 **進階選項**下方**選擇選項，以產生的 proxy**，選取您想要的選項。 例如，您可以選取是否非同步方法會產生 WCF 用戶端，或您可以停用設定檔的產生。  
  
   3. 底下**序列化程式**，選取應該使用的序列化程式。  
  
      下圖顯示**進階選項**隨附的預設選取項目 (**自動**選取如已選取序列化程式和任何其他選項)。  
  
      ![[進階選項] 方塊預設設定](../../adapters-and-accelerators/adapter-oracle-database/media/r2-net-adapters-oracle-msb-advanced-options.gif "R2_NET_Adapters_Oracle_MSB_Advanced_Options")  
  
      您可以在設定的選項**進階選項**方塊會相當於一些可用的選項，當您使用 ServiceModel Metadata Utility Tool (svcutil.exe)。 如需這些選項的詳細資訊，請參閱[ServiceModel Metadata Utility Tool (Svcutil.exe)](https://msdn.microsoft.com/library/aa347733.aspx)。
  
5. 按一下 [確定] 。 [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]儲存 WCF 用戶端的操作和您選取了您的專案目錄中的類別的類別和協助程式程式碼。 根據預設，也會儲存組態檔。 如需詳細資訊，請參閱 <<c0> [ 產生 WCF 用戶端或 Siebel 解決方案成品的 WCF 服務合約](../../adapters-and-accelerators/adapter-siebel/generate-a-wcf-client-or-a-wcf-service-contract-for-siebel-solution-artifacts.md)。  
  
## <a name="see-also"></a>另請參閱  
 [在 Visual Studio 中取得 Siebel 作業的中繼資料](../../adapters-and-accelerators/adapter-siebel/get-metadata-for-siebel-operations-in-visual-studio.md)