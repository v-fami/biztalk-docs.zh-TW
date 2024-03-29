---
title: 使用 BizTalk Server 管理主控台 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: af00d9de-0f94-407b-b6f4-4da63a0867a0
caps.latest.revision: 42
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c1cfae403a0161f87188b96460e8086cbf90d561
ms.sourcegitcommit: 53b16fe6c1b1707ecf233dbd05f780653eb19419
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2018
ms.locfileid: "50753214"
---
# <a name="using-the-biztalk-server-administration-console"></a>使用 BizTalk Server 管理主控台
BizTalk Server 管理主控台是您可以用來管理與監控 BizTalk Server 的 Microsoft Management Console (MMC)，您也可以用它來部署與管理您的 BizTalk Server 應用程式。  
  
 BizTalk Server 管理主控台左邊的主控台樹狀結構，由表示您可以管理之不同成品的資料夾及子資料夾所組成。  
  
 當您在主控台樹狀結構中選取節點時，管理主控台右窗格上的詳細資料窗格會顯示項目的相關資訊。  
  
 在主控台樹狀目錄中選取 [BizTalk Server 管理] 節點會顯示 [開始] 頁面，其中包含您可以執行，例如連接至現有的 BizTalk Server 群組的動作。 此外，[開始] 頁面包含 BizTalk Server 文件與線上社群網站的連結。  
  
 管理主控台中使用的鍵盤快速鍵的相關資訊，請參閱[管理主控台鍵盤快速鍵](../core/administration-console-keyboard-shortcuts.md)。  
  
## <a name="biztalk-server-artifacts"></a>BizTalk Server 成品  
 您可以使用 BizTalk Server 管理主控台來管理下列成品：  
  
-   **BizTalk 群組**。 在主控台樹狀結構中的 [BizTalk 群組] 節點包含表示該 BizTalk 群組之成品 (應用程式、合作對象與平台設定) 的其他節點。 BizTalk 群組是組織單位，通常表示需要包含 BizTalk Server 實作的企業、部門、中心或其他商務單位。 BizTalk 群組與 BizTalk 管理資料庫有一對一的關係。 如需詳細資訊，請參閱 <<c0> [ 管理群組](../core/managing-groups.md)。  
  
     選取 BizTalk Server 管理主控台中的 [BizTalk 群組] 節點時，詳細資料窗格中會顯示 [BizTalk Server 群組中樞] 頁面。 [BizTalk Server 群組中樞] 頁面會提供 BizTalk Server 系統狀況的整體檢視。 如需詳細資訊，請參閱 <<c0> [ 使用 [群組中樞] 頁面](../core/using-the-group-hub-page.md)。  
  
-   **協調流程**。 協調流程是使用「協調流程設計師」所設計，已部署到 BizTalk 群組，並且顯示在其中的管理主控台上。 如需詳細資訊，請參閱 <<c0> [ 管理協調流程](../core/managing-orchestrations.md)。  
  
-   **角色連結**。 角色連結會定義訊息定義之角色與雙向互動中使用的連接埠類型之間的關係。 如需詳細資訊，請參閱 <<c0> [ 管理角色連結](../core/managing-role-links.md)。  
  
-   **傳送埠群組**。 傳送埠群組是傳送埠的具名集合，可用來在單次設定中傳送相同訊息到多個目的地。 如需詳細資訊，請參閱 <<c0> [ 管理傳送埠與傳送埠群組](../core/managing-send-ports-and-send-port-groups.md)。  
  
-   **傳送埠**。 傳送埠是傳送訊息的 BizTalk 物件。 如需詳細資訊，請參閱 <<c0> [ 管理傳送埠與傳送埠群組](../core/managing-send-ports-and-send-port-groups.md)。  
  
-   **接收埠**。 接收埠是相似接收位置的邏輯群組。 如需詳細資訊，請參閱 <<c0> [ 管理接收埠](../core/managing-receive-ports.md)。  
  
-   **接收位置**。 接收位置是定義為特定位址，輸入文件會送達此處，並結合處理該位址接收之訊息的 BizTalk Server 管線。 如需詳細資訊，請參閱 <<c0> [ 管理接收位置](../core/managing-receive-locations.md)。  
  
-   **原則**。 原則是商務規則的版本集合。 如需詳細資訊，請參閱 <<c0> [ 管理的原則](../core/managing-policies.md)。  
  
-   **結構描述**。 結構描述是訊息的結構。 結構描述可以包含多個子結構描述。 如需詳細資訊，請參閱 <<c0> [ 管理結構描述](../core/managing-schemas.md)。  
  
-   **對應**。 對應是一種 XML 檔案，負責定義不同規格中之記錄與欄位間的對應。 對應包含 Extensible Stylesheet Language (XSL) 樣式表，BizTalk Server 使用此樣式表執行對應中描述的轉換。 如需詳細資訊，請參閱 <<c0> [ 管理對應](../core/managing-maps.md)。  
  
-   **管線**。 管線是定義及連結一或多個處理階段的軟體基礎結構，以指定的順序執行來完成特定工作。 管理將處理分成各個階段，描述工作類別的抽象概念。 它也決定執行每個工作類別的順序。 如需詳細資訊，請參閱 <<c0> [ 管理管線](../core/managing-pipelines.md)。  
  
-   **資源**。 資源是指令碼、部署的組件，或是與應用程式相關聯的其他檔案。 如需詳細資訊，請參閱 <<c0> [ 管理資源](../core/managing-resources.md)。  
  
-   **合作對象**。 合作對象是 BizTalk Server 外部與協調流程互動的實體。 與組織合作的所有夥伴皆視為合作對象，而組織可能有數千個夥伴。 如需詳細資訊，請參閱 <<c0> [ 管理合作對象](../core/managing-parties.md)。  
  
-   **平台設定**。 [平台設定] 節點包含主控件、主控件執行個體、MessageBox 資料庫與配接器的子節點。 如需詳細資訊，請參閱 <<c0> [ 管理的平台設定](../core/managing-platform-settings.md)。  
  
    -   **主機**。 主控件節點包含所有在 BizTalk Server 環境中的內含式與外掛式主控件。 BizTalk 主控件是配接器處理常式、接收位置 (包括管線)，以及協調流程等項目的邏輯容器。 如需詳細資訊，請參閱 <<c0> [ 管理 BizTalk 主控件和主控件執行個體](../core/managing-biztalk-hosts-and-host-instances.md)。  
  
    -   **主控件執行個體**。 主控件執行個體節點包含所有在目前 BizTalk Server 群組中的主控件執行個體。 主控件執行個體是執行應用程式元件的 BizTalk Server 執行階段程序。  
  
         使用主控件執行個體節點，您可以建立新的主控件執行個體並重新整理主控件執行個體資訊。 如需詳細資訊，請參閱 <<c0> [ 管理 BizTalk 主控件和主控件執行個體](../core/managing-biztalk-hosts-and-host-instances.md)。  
  
    -   **伺服器**。 [伺服器] 節點會列出所有加入 BizTalk Server 群組的伺服器。 這是安裝和設定 BizTalk Server 以及執行主控件執行個體所在的電腦。 主控件執行個體的建立方式是將伺服器與特定主控件相關聯。 如需詳細資訊，請參閱 <<c0> [ 管理伺服器](../core/managing-servers.md)。  
  
    -   **訊息方塊**。 MessageBox 節點包含所有目前 BizTalk Server 群組所使用的 MessageBox 資料庫。 使用 MessageBox 節點，您可以建立新的 MessageBox 資料庫以及重新整理 MessageBox 資料庫資訊。 MessageBox 資料庫是在執行協同處裡的伺服器之間進行工作項目負載平衡的基礎。 在處理生命週期中，工作項目可以通過 MessageBox 資料庫一次以上。 MessageBox 資料庫的名稱不能超過 100 個字元。 如需詳細資訊，請參閱 <<c0> [ 管理 MessageBox 資料庫](../core/managing-messagebox-databases.md)。  
  
    -   **配接器**。 配接器節點包含所有為 BizTalk Server 群組與相關配接器處理常式設定之傳送與接收配接器的子節點。 配接器是用來在端點之間傳送和接收訊息的傳訊中介軟體。 如需詳細資訊，請參閱 <<c0> [ 使用配接器](../core/using-adapters.md)。  

## <a name="tips-and-tricks"></a>祕訣和訣竅

#### <a name="update-settings-for-multiple-hosts-and-host-instances-simultaneously"></a>同時更新多個主控件和主控件執行個體的設定
開頭[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]，您可以選取多個主控件和主控件執行個體，並更新部份中設定**設定儀表板**。

**步驟**:

1. 在 BizTalk 管理中，依序展開**BizTalk 群組**，展開**平台設定**。
2. 選取 **主機**。 在主機清單中，使用 CTRL 或 SHIFT 鍵同時選取多部主機上。
3. 以滑鼠右鍵按一下的主機，您選取，然後選取**設定**。 或者，選取**設定**動作 窗格中。
4. 在 設定儀表板中，一般和節流設定可設定，並套用至多部主機您已選取。 
5. 接下來，選取**主控件執行個體**。 在主控件執行個體 清單中，使用 CTRL 或 SHIFT 鍵同時選取多個主控件執行個體。 在 **設定**，.NET CLR 和協調流程節流設定可套用至您選取多個主控件執行個體。 

> [!NOTE]
> 您可以選取多個主機和主機型別相同的主控件執行個體。 如果主控件類型都不同，**設定**選項呈現灰色。例如，如果您複選內含式主控件和外掛式主控件，然後**設定**會呈現灰色。

#### <a name="filter-artifacts-in-your-application"></a>篩選您的應用程式中的成品
從開始[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]，您可以在您的應用程式搜尋成品。 例如，您可以搜尋特定的結構描述或協調流程應用程式中。 

**步驟**:

1. 在 BizTalk 管理中，依序展開**BizTalk 群組**，展開**應用程式**，然後展開您的成品的應用程式的其中一個。 例如，依序展開**BizTalk EDI 應用程式**。 
2. 選取 **結構描述**。 在結構描述清單中，使用**搜尋**方塊來搜尋結構描述，或篩選顯示的結構描述。 例如，輸入**x12**在搜尋方塊中，然後按 enter 鍵。 會顯示所有名稱中的 x12 結構描述。 清除您的搜尋。 

    接下來，輸入**批次**在搜尋方塊中，然後按 enter 鍵。 批次結構描述會顯示。 
    
您可以使用這項搜尋來尋找或篩選的任何成品與您的應用程式，包括傳送埠、 資源、 對應等等。 

#### <a name="save-multiple-suspended-messages-simultaneously-to-a-file-within-group-hub"></a>同時將多個擱置的訊息儲存到 群組中樞內的檔案 
從開始[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]，您可以將多個擱置的訊息儲存至檔案的同時。

**步驟**:

1. 在 BizTalk 管理中，選取  **BizTalk 群組**
2. 選取 **新的查詢**，並在查詢中，**的搜尋**

    搜尋記載的名稱：  
    運算子： 等於  
    值： 訊息
3. 選取 **執行查詢**。 在查詢結果中，使用 CTRL 或 SHIFT 鍵同時選取多個擱置的執行個體。 以滑鼠右鍵按一下，然後選取**安全檔案**。 
4. 選擇您要儲存檔案的資料夾。 儲存時，會將 XML 檔案建立的每一個訊息。

## <a name="next-steps"></a>後續步驟
  
-   [開啟 BizTalk Server 管理主控台](../core/how-to-open-the-biztalk-server-administration-console.md)  
  
-   [使用群組中樞頁面](../core/using-the-group-hub-page.md)
