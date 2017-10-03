---
title: "逐步解說： 部署基本 BizTalk 應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying, tutorials
- tutorials, deploying
- tutorials, applications
- applications, tutorials
ms.assetid: 21b67153-0f8c-406a-a224-fc792b16192f
caps.latest.revision: "69"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5db86f672cd17965ec76877cc3867594bf82b40d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="walkthrough-deploying-a-basic-biztalk-application"></a>逐步解說： 部署基本 BizTalk 應用程式
Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 包含可簡化 BizTalk 商務解決方案之管理和部署的功能。 它現在為商務解決方案中的項目 (例如，協調流程、結構描述、對應、管線和 .NET 組件) 提供了 BizTalk 應用程式容器。 您可以管理、 修改、 部署和安裝的所有項目當做單一單位的應用程式中。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]也包含精靈，可協助自動化應用程式部署工作。 如需背景資訊，請參閱[應用程式部署和管理功能](../core/application-deployment-and-management-features.md)和[應用程式部署和管理工具](../core/application-deployment-and-management-tools.md)。  
  
 此逐步解說針對 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 部署功能的使用，提供按部就班的指示，以便您瞭解它們如何共同運作。 此逐步解說中說明的部署程序不一定能反映貴公司管理應用程式部署的方式。  
  
 在此逐步解說中，您將會建立簡單的 BizTalk 應用程式，然後將它從開發環境部署至測試環境，接著再部署至臨時環境和實際執行環境。 完成此逐步解說之後，您將會瞭解如何執行下列工作：  
  
-   從開發電腦上的 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，使用 [部署] 命令將 BizTalk 組件部署至 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的本機執行個體。 這樣會建立有組件填入其中的 BizTalk 應用程式。 BizTalk 組件包含資源資訊；例如，要在 BizTalk 方案中使用的協調流程、管線、結構描述和對應。  
  
-   從[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，新增、 建立、 設定及移除任何項目 (稱為*成品*) 視需要建立功能完整的商務解決方案，例如傳送和接收連接埠、 原則、 組件，並指令碼。  
  
-   使用匯出、 匯入和安裝精靈部署到測試電腦上的 BizTalk 應用程式功能及系統測試。  
  
-   使用匯出、 匯入和安裝精靈來部署至臨時伺服器進行最後的設定應用程式和部署到實際伺服器。  
  
## <a name="prerequisites"></a>必要條件  
 有兩種方式可讓您設定此逐步解說的測試環境：  
  
-   您可以在單一電腦上執行此逐步解說中的工作。  
  
-   您可以設定不同的電腦分別當做開發、測試、執行和實際執行電腦，更貼切地模擬真實世界的部署。 但是，您不應在實際執行環境中執行此逐步解說中的任何工作。  
  
 若要執行此逐步解說中的步驟，請確定您的測試環境符合下列必要條件：  
  
-   您用來部署 BizTalk 組件的開發電腦具有 Microsoft[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]安裝。  
  
-   在本逐步解說，包括開發電腦中的應用程式部署程序中使用的每部電腦都有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝。  
  
-   每個[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]執行個體則是個別安裝; 也就是說，它有自己[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫和群組。  
  
 除了上述的需求，您必須先[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]方案或專案可包含 BizTalk 組件。 如果您沒有現有的方案或專案，您可以使用隨附的 ErrorHandling 範例方案[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]SDK 為此目的。 本逐步解說稍後會提供使用此範例的相關指示。  
  
 您也必須有成員的使用者帳戶[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Administrators 群組，以及您將用來執行工作，在本逐步解說的電腦上本機 Administrators 群組。  
  
 如需有關安裝和設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，請參閱[新功能、 安裝、 設定及升級](../install-and-config-guides/biztalk-server-what-s-new-installation-configuration-and-upgrade.md)。
  
##  <a name="BKMK_Assumptions"></a>假設  
 本逐步解說有下列假設：  
  
-   您有基本知識[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 [開始使用 BizTalk Server](../core/getting-started-with-biztalk-server.md)應該可以幫助。
  
-   您使用的 BizTalk 組件，之前尚未部署至測試環境中的應用程式。 如果已經部署，您應該將已部署這些組件的 BizTalk 應用程式解除部署。 如需指示，請參閱[解除部署 BizTalk 應用程式](../core/undeploying-biztalk-applications.md)。  
  
-   沒有任何應用程式資源是與其他應用程式共用的。  
  
##  <a name="BKMK_Audience"></a>對象  
 本逐步解說的目標讀者：  
  
-   **BizTalk 應用程式開發人員。** 開發人員可以了解如何設定專案屬性[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]和部署 BizTalk 組件從[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]BizTalk 應用程式。 開發人員也會學到如何新增成品至應用程式，再匯出應用程式至 .msi 檔案。 開發人員 背景應用程式部署工作的相關資訊，請參閱[BizTalk 應用程式部署的開發工作](../core/development-tasks-for-biztalk-application-deployment.md)。  
  
-   **BizTalk 應用程式測試人員。** 測試人員可以了解如何.msi 檔案匯入[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]其註冊為 BizTalk 應用程式的測試電腦上執行。 測試人員接著可以學到如何在測試電腦上安裝應用程式，並驗證其安裝。 如需測試的應用程式部署工作的背景資訊，請參閱[BizTalk 應用程式部署的測試工作](../core/testing-tasks-for-biztalk-application-deployment.md)。  
  
-   **BizTalk Server IT 系統管理員。** 負責將 BizTalk 應用程式部署至開發用及實際執行伺服器的 IT 系統管理員，可以瞭解此項工作的必要基本步驟。 應用程式部署工作的相關背景資訊的 IT 系統管理員，請參閱[BizTalk 應用程式部署的暫存工作](../core/staging-tasks-for-biztalk-application-deployment.md)和[實際執行工作，BizTalk 應用程式部署](../core/production-tasks-for-biztalk-application-deployment.md).  
  
##  <a name="BKMK_Overview"></a>這個逐步解說的概觀  
 本逐步解說的目的是要在實驗室環境中部署 BizTalk 應用程式，以評估此技術日後部署於實際執行環境時的運作狀況。 此逐步解說會探討一個簡單實例 (在一台電腦上將單一 .msi 檔案部署為 BizTalk 應用程式)，將有助您熟悉應用程式部署所涉及的基本工作。  
  
> [!NOTE]
>  對於應用程式正常運作所需的應用程式組態設定 (例如，繫結協調流程、設定連接埠等)，此逐步解說未提供相關指引。 此逐步解說只是要介紹新的應用程式部署功能，別無其他用意。  
  
 本文件中提供的指示涵蓋下列工作：  
  
1.  **設定必要的權限。** 在開始此逐步解說之前，必須確定您具有適當的權限可執行每項工作。  
  
2.  **從 Visual Studio 部署 BizTalk 組件。** 這個步驟是由應用程式開發人員執行。 部署 BizTalk 組件從[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]自動建置組件，並將其內容部署到 BizTalk 應用程式。 如果應用程式尚不存在，部署組件也將建立應用程式。 此時會註冊應用程式成品，並將其資料儲存在 BizTalk 管理資料庫中。 還會依預設將組件安裝在本機電腦的全域組件快取 (GAC) 中。 建立應用程式之後，您可以檢視並管理其成品從[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。 在管理主控台中，每個應用程式都會儲存在它自己的資料夾中，而且還有包含所有應用程式成品之參考的子資料夾。  
  
3.  **設定應用程式。** 這個步驟可由應用程式開發人員或 IT 系統管理員執行，以新增、建立和設定應用程式正常運作所需的任何成品。 在管理主控台中，您可以輕鬆地新增、建立、設定和移除成品，例如傳送和接收埠、指令碼以及其他組件。 當您確信應用程式包含了必要的成品且設定正確後，即可將它匯出至 .msi 檔案，如下所述。  
  
4.  **應用程式匯出至.msi 檔案。** 這個步驟可由開發人員、測試人員或 IT 系統管理員執行，以產生可用於將 BizTalk 應用程式部署至不同環境的 .msi 檔案。 例如，開發人員可以匯出供測試人員用來部署應用程式至測試伺服器的 .msi 檔案。 完成測試之後，IT 系統管理員就可以接著使用已測試的 .msi 檔案，將應用程式部署至開發用或實際執行伺服器 (如下所述)。 這個逐步解說將說明如何匯出至.msi 檔案的應用程式使用匯出精靈 」，可從[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
5.  **匯入從.msi 檔案安裝應用程式。** 這個步驟可由測試人員或 IT 系統管理員執行，將 BizTalk 應用程式部署至開發用或實際執行伺服器。 例如，測試人員可以將應用程式從開發人員提供的 .msi 檔案匯入至測試電腦上的 BizTalk 群組，然後從 .msi 檔案安裝應用程式，以便進行測試。 IT 系統管理員同樣可以從測試人員提供的 .msi 檔案中，將應用程式部署至開發用或實際執行伺服器。 此逐步解說將說明如何使用「匯入精靈」，將 .msi 檔案匯入至 BizTalk 群組中的應用程式。 如同步驟 2，會註冊應用程式的成品，以及其資料儲存在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫。 此逐步解說也將說明如何使用「安裝精靈」或以按兩下 .msi 檔案的方式，將應用程式安裝在目前的伺服器上。 如此，您就可以在目前的伺服器上執行應用程式。  
  
##  <a name="BKMK_Step-by-step"></a>若要部署 BizTalk 應用程式的逐步指南  
 本節提供逐步的程序，從開發、測試、執行以至實際執行，一路完成部署 BizTalk 應用程式的所有階段。 如前所述，您可以一直在同一台電腦上執行這些步驟，或者如果您想要更貼切地模擬實際環境，也可以使用多台電腦。  
  
#### <a name="1-configure-permissions"></a>1.設定權限  
 第一個步驟是要確定您具有適當權限，可執行此逐步解說中的工作。 請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)，和[最低安全性權限](https://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2006-to-2016.aspx)。
  
#### <a name="2-deploy-the-biztalk-assemblies"></a>2.部署 BizTalk 組件  
 從 Microsoft 內部[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]的開發電腦上，使用程序在這個步驟中部署 BizTalk 組件到 BizTalk 應用程式。  
  
 在開始之前，您必須擁有在可用的 BizTalk 方案[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。 您可以自行建立方案或專案，也可以設定 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] 隨附的 ErrorHandling 範例。 您可以設定 ErrorHandling 範例方案中[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，如下所示：  
  
###### <a name="to-set-up-the-errorhandling-solution"></a>若要設定 ErrorHandling 方案  
  
1.  在開發電腦上瀏覽至：  
  
     [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\Messaging\ErrorHandling\ErrorHandler  
  
2.  按兩下**ErrorHandler.btproj**。  
  
     ErrorHandler 方案隨即在中開啟[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。 此方案包含兩個專案： ErrorHandler 和 PipelinesAndSchemas。  
  
     ![在方案中的 visual Studio 專案](../core/media/errorhandlingprojects.gif "ErrorHandlingProjects")  
  
 接下來，您必須設定方案中每個專案的屬性。 ErrorHandling 範例方案包含兩個專案，您應該設定屬性： ErrorHandler 和 PipeLinesAndSchemas。 設定屬性以反映開發電腦的環境。 例如，您指定的 SQL Server 應該是在開發電腦上執行的執行個體，而此執行個體則裝載著本機 BizTalk 管理資料庫。  
  
###### <a name="to-configure-project-properties"></a>若要設定專案屬性  
  
1.  在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]方案總管 中，以滑鼠右鍵按一下專案，您想要設定屬性，然後再按一下**屬性**。  
  
2.  按一下**部署**專案設計工具中的索引標籤。  
  
     ![在 Visual Studio 2005 中的部署屬性工作表](../core/media/deploymentproperties.gif "DeploymentProperties")  
  
3.  下表中所述，設定專案屬性，然後按一下**確定**。  
  
    |屬性|值|說明|  
    |--------------|-----------|-----------------|  
    |Application Name|\<Name>|要部署此專案內組件的 BizTalk 應用程式名稱。 如果應用程式已經存在，組件便會在您部署專案時加入至其中。 如果應用程式不存在，則會建立該應用程式。 如果此欄位為空白，組件將會部署至目前群組中的預設 BizTalk 應用程式，即 "BizTalk Application 1"。 名稱如果包含空格，則必須括在雙引號 (") 中。|  
    |設定資料庫|\<BizTalk 管理資料庫名稱 >|群組的 BizTalk 管理資料庫名稱，依預設為 BizTalkMgmtDb。|  
    |Server|\<伺服器名稱 >|在本機電腦上，裝載 BizTalk 管理資料庫之 SQL Server 執行個體的名稱。 在單一電腦安裝中，這通常是本機電腦的名稱。 **注意：**如果您將這個 BizTalk 專案移至不同的電腦時，您必須修改伺服器屬性，以反映新的電腦名稱，然後您才能部署組件。|  
    |重新部署|True 或 False|將此項設定為 True (預設)，可讓您不變更版本號碼而重新部署 BizTalk 組件。|  
    |安裝到全域組件快取|True 或 False|將此項設定為 True (預設)，可在部署組件時，將組件安裝到本機電腦上的全域組件快取 (GAC)。|  
    |重新啟動主控件執行個體|True 或 False|將此項設定為 True，可在重新部署組件時，自動重新啟動執行於本機電腦上的所有主控件執行個體。 如果設定為 False (預設)，您必須在重新部署組件時，手動重新啟動主控件執行個體。 **注意：**如果您重新部署組件從方案層級時，主控件執行個體將會重新啟動一次每個專案，這個選項設為 True。 這樣可能會產生多次的重新啟動。 如果您打算從方案層級重新部署，您可能會想要只在方案中的一個專案上將此屬性設為 True，以免主控件執行個體重新啟動多次。 這應該在方案中最後一個將要重新部署的專案上設定。 此外，如果當您執行重新部署時，主控件執行個體停止了，它將不會啟動。|  
    |啟用單元測試|True 或 False|指定是否要對專案啟用單元測試。|  
  
4.  針對方案中的每個專案，重複步驟 1、2 和 3。  
  
 部署程序要求組件必須是以強式名稱簽署的。 若要以強式名稱簽署組件，請將專案與強式名稱組件金鑰檔案產生關聯。 如果您還沒有這樣做，請使用下列程序來產生強式名稱組件金鑰檔案。  
  
###### <a name="to-create-a-strong-name-assembly-key-file"></a>建立強式名稱組件金鑰檔  
  
1.  啟動**Visual Studio 命令提示字元**。  
  
2.  在命令提示字元中，切換到您想要儲存金鑰檔案的資料夾，再輸入下列命令，然後按下 ENTER：  
  
     **sn-k***file_name* **.snk**   
  
     範例： **sn-k ErrorHandling.snk**  
  
     確認訊息，**金鑰組寫入\<**  *file_name***>.snk** `,`會出現在命令列。  
  
 接下來，您必須將方案中的每個專案與金鑰檔案產生關聯。  
  
###### <a name="to-associate-your-projects-with-the-key-file"></a>若要建立專案與金鑰檔案的關聯  
  
1.  在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]方案總管 中，以滑鼠右鍵按一下專案，然後按一下**屬性**。  
  
2.  按一下**簽署**專案設計工具中的索引標籤。  
  
3.  在右窗格中，檢查**簽署組件**方塊。  
  
4.  按一下底下的下拉式清單方塊**選擇強式名稱金鑰檔**，按一下  **\<瀏覽 >**，然後瀏覽至金鑰檔。  
  
5.  按一下金鑰檔案，然後按一下**開啟**。  
  
6.  針對方案中的每個專案，重複步驟 1 至 5。  
  
 現在只需一個步驟，就可以建置和部署方案中的所有組件，如下所述。  
  
###### <a name="to-deploy-the-assemblies-in-a-solution"></a>若要部署方案中的組件  
  
-   在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]方案總管 中，以滑鼠右鍵按一下方案，然後**部署方案**。  
  
     建置和部署程序的狀態會顯示在頁面左下角。 如果您使用 ErrorHandling 範例方案，輸出視窗中將會顯示數個警告訊息。 基於此逐步解說的目的，您可以忽略這些訊息。 部署完成時，「 部署： 2 已成功，0 失敗、 0 略過 」 會顯示在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]輸出 視窗。  
  
 部署 BizTalk 組件時，會在 BizTalk 管理資料庫中，將這些組件註冊為指定 BizTalk 應用程式的一部分。 它也會填入資料庫的所有項目，或*成品*，包含組件中。 如果應用程式在部署之前尚不存在，這個步驟也會建立新的應用程式。 您現在可以檢視 BizTalk 應用程式及其成品從[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]開發電腦上的管理主控台。  
  
###### <a name="to-view-the-biztalk-application-and-its-artifacts"></a>若要檢視 BizTalk 應用程式及其成品  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。  
  
3.  展開剛才在其中部署組件的應用程式資料夾。  
  
4.  按一下應用程式資料夾下的資料夾，以檢視其內容。 在適當的資料夾中，您應該會看見所部署之組件中包含的成品。 如果是部署 BizTalk 範例方案 ErrorHandling，您應該會在 [協調流程]、[結構描述] 和 [資源] 資料夾中看見成品。 您可以以滑鼠右鍵按一下成品，然後按一下**屬性**以檢視其組態設定。  
  
5.  展開**資源**資料夾中，以滑鼠右鍵按一下其中一個組件，然後**修改**。  
  
6.  在**選項**方塊中，請注意，已針對組件的部署選項。  
  
7.  在**目的地位置**，記下安裝應用程式時複製的組件檔案所在的位置路徑。 根據預設，這是組件的來源位置。  
  
> [!NOTE]
>  如果您的應用程式不會顯示，以滑鼠右鍵按一下**BizTalk 群組**按一下**重新整理**。  
  
 如需部署組件的詳細資訊，請參閱[從到 BizTalk 應用程式的 Visual Studio 部署 BizTalk 組件](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)。  
  
#### <a name="3-configure-the-application"></a>3.設定應用程式  
 從[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，您可以設定您的應用程式建立、 新增和設定成品。  
  
 若要讓應用程式正常運作，就必須正確設定。 例如，協調流程必須繫結至主控件，而且必須設定傳送埠和接收位置。 如果是部署 ErrorHandling 範例方案，您將會發現應用程式沒有傳送埠、接收埠或接收位置。 這表示協調流程無法傳送或接收訊息。 有關設定應用程式的指示，已超出此逐步解說的範圍。 不過，如果您想要這麼做，最快的方法就是使用 [設定應用程式] 對話方塊；您只要以滑鼠右鍵按一下應用程式，再按一下 [設定] 即可存取它。 如需詳細資訊，請參閱[如何設定應用程式](../core/how-to-configure-an-application.md)。 除了這個方法之外，您也可以設定協調流程，同時個別建立、設定和刪除傳送埠、傳送埠群組、接收埠和接收位置。 如需詳細資訊，請參閱中的適當主題[管理成品](../core/managing-artifacts.md)。  
  
 您可能也會想要將前置處理指令碼或讀我檔案等加入至應用程式成品，或移除成品。 您可以使用下列程序來嘗試此功能 (ErrorHandling 範例未包含可加入的額外成品，但是您可以將環境中可能已經存在的項目加入，以便測試此功能)。  
  
> [!NOTE]
>  您可以在應用程式匯入、安裝或解除安裝之前或之後，使用前置和後置處理指令碼來執行動作。 例如，您或許有意在解除安裝之後，使用前置處理指令碼來解除安裝 GAC 中的組件。 如需詳細資訊，請參閱[使用前置和後置處理指令碼，以自訂應用程式部署](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md)。  
  
###### <a name="to-add-an-artifact-to-an-application"></a>若要新增成品至應用程式  
  
1.  開啟[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。 按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。  
  
3.  若要新增下列類型的成品，以滑鼠右鍵按一下 ErrorHandling 應用程式資料夾，然後**新增**。 請注意，當您新增 BizTalk 組件時，其中包含的成品也會新增至應用程式中的適當資料夾。  
  
    -   BizTalk 組件  
  
    -   前置處理指令碼  
  
    -   後置處理指令碼  
  
    -   資源 (BizTalk 組件、.NET 組件、前置處理指令碼、後置處理指令碼、檔案、憑證、COM 元件、 BAM 成品、繫結檔案和虛擬目錄)  
  
    -   原則  
  
 您也可以從應用程式移除成品。  
  
###### <a name="to-remove-an-artifact-from-an-application"></a>若要從應用程式移除成品  
  
1.  開啟[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。 按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。  
  
3.  展開包含該成品的資料夾，以滑鼠右鍵按一下成品，然後按一下**移除**。  
  
 如需有關如何設定您的應用程式的詳細資訊，請參閱[建立和修改 BizTalk 應用程式](../core/creating-and-modifying-biztalk-applications.md)。  
  
#### <a name="4-export-the-application"></a>4.匯出應用程式  
 您已建立 BizTalk 應用程式，並視需要修改它之後，您可以匯出應用程式中匯出 MSI 檔案精靈[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。 這樣就會產生 .msi 檔案，您稍後可以將它匯入至其他 BizTalk 群組，以便在新的群組中重新建立應用程式。 若要在特定伺服器上執行應用程式，您也必須在該伺服器的本機，透過 .msi 檔案進行安裝。  
  
###### <a name="to-export-the-application"></a>匯出應用程式  
  
1.  開啟[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。 按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。  
  
3.  BizTalk 應用程式上按一下滑鼠右鍵，指向**匯出**，然後按一下  **MSI 檔案**。  
  
4.  在**歡迎使用匯出 MSI 檔案精靈**頁面上，按一下**下一步**。  
  
5.  在**選取資源**頁面上，選取要匯出至.msi 檔案，然後按一下資源**下一步**。 在此逐步解說中，您可以接受預設值。  
  
6.  如果出現提示，請在**指定 IIS 主控件**頁面上，輸入您想要加入，然後再按一下虛擬目錄所在電腦的伺服器名稱**下一步**。 只有在虛擬目錄先前已新增至 BizTalk 管理資料庫，例如已新增至應用程式或匯入應用程式時，系統才會提示您指定伺服器。  
  
    > [!NOTE]
    >  ErrorHandling 範例方案中沒有包含虛擬目錄。  
  
7.  在**相依性**頁面上，檢閱應用程式的相依性，然後按一下**下一步**。  
  
8.  在**目的地**頁面上，於**目的地應用程式名稱**，輸入應用程式名稱。  
  
9. 在**要產生的 MSI 檔案**，輸入.msi 檔案的完整路徑，然後按一下**匯出**。 範例：C:\MSI\Errorhandling.msi  
  
    > [!NOTE]
    >  Microsoft 建議您將 .msi 檔案儲存在安全的資料夾中。  
  
10. 在**摘要**頁面上，記下此作業中，記錄檔的位置，然後按一下**完成**。  
  
 在檔案系統中，確認已在您指定的位置中建立 .msi 檔案。  
  
> [!NOTE]
>  基於安全性考量，應用程式匯出期間將從應用程式繫結移除密碼。 從 .msi 檔案安裝應用程式後，您必須重新設定密碼，應用程式才能運作。 然而，密碼不會從您新增至應用程式的任何繫結檔案移除。  
  
 如需有關匯出應用程式和成品的詳細資訊，請參閱[如何匯出 BizTalk 應用程式](../core/how-to-export-a-biztalk-application.md)。  
  
#### <a name="5-import-and-install-the-application"></a>5.匯入和安裝應用程式  
 下一個步驟是從您剛才在 BizTalk 群組中產生的 .msi 檔案匯入應用程式，並在本機電腦進行安裝。 您可以使用匯入 MSI 精靈 」 和 「 安裝精靈中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台來執行這項操作。  
  
> [!NOTE]
>  應用程式必須安裝在群組中將執行應用程式的每一台電腦上。 您可以按兩下 .msi 檔案，將它安裝到其他電腦。  
  
 每當您想要將應用程式從一個 BizTalk 群組移轉至另一個群組 (例如，從開發環境至測試環境、從測試環境至執行環境，或從執行環境至實際執行環境進行移轉) 時，就可以重複這個步驟中的工作。  
  
 此時，如果只使用一台電腦來執行此逐步解說，您應該從 BizTalk 群組刪除應用程式。 您也應該從全域組件快取 (GAC) 中刪除組件。 這樣，當您匯入應用程式時，才可以確認是否已經正確地重新建立它。 如果是使用多台電腦執行此逐步解說，則不需要執行這些工作。  
  
###### <a name="to-delete-the-application-from-the-biztalk-group"></a>若要從 BizTalk 群組刪除應用程式  
  
1.  開啟[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。 按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  以滑鼠右鍵按一下應用程式，然後按一下**刪除**。  
  
###### <a name="to-delete-assemblies-from-the-gac"></a>若要從 GAC 刪除組件  
  
1.  在檔案系統中，瀏覽至 %systemdrive%\Windows\assembly。  
  
2.  以滑鼠右鍵按一下您的解決方案所產生每個組件檔案中，按一下**解除安裝**，然後按一下 **是**確認。 例如，與 ErrorHandling 專案關聯的組件檔案是 ErrorHandling.ErrorHandler 和 ErrorHandling.PipelinesAndSchemas。  
  
     ![從 GAC 刪除組件](../core/media/deleteassembly.gif "DeleteAssembly")  
  
 現在您可以開始將應用程式匯入至 BizTalk 群組。 如果您想要將應用程式匯入至執行於另一台電腦上的 BizTalk 群組，則 .msi 檔案必須是可從其他電腦存取的。  
  
> [!CAUTION]
>  在安裝任何應用程式之前，請確認您是從信任的來源取得 .msi 檔案。 惡意使用者可能會將程式碼包含在 .msi 檔案中，而在您的系統或網路上造成嚴重的後果。 如需詳細資訊，請參閱[安全性和 Windows Installer](../core/security-and-windows-installer.md)。  
  
###### <a name="to-import-and-install-the-application"></a>若要匯入和安裝應用程式  
  
1.  開啟[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]的執行個體的系統管理主控台[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]到您要匯入應用程式。 按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，然後展開**BizTalk 群組**。  
  
3.  以滑鼠右鍵按一下**應用程式**，指向 **匯入**，然後按一下  **MSI 檔案**。  
  
4.  在**歡迎使用匯入精靈**頁面上，於**要匯入 MSI 檔案**，輸入.msi 檔案的完整路徑，然後按一下**下一步**。 範例： C:\msi\MyApplication.msi  
  
5.  在**應用程式設定**頁面上，於**可用的應用程式將參考加入至**，選取要加入的參考，，然後按一下 應用程式**下一步**。 如果是使用 ErrorHandling 範例方案，您可以接受預設值。  
  
     ![將參考加入至應用程式](../core/media/appreferences.gif "AppReferences")  
  
6.  在**應用程式目標環境設定**頁面上，確認**\<預設 >**已選取並按**下一步**。  
  
7.  在**匯入摘要**頁面上，確認摘要資訊是否正確，然後按**匯入**。  
  
8.  在 匯入 MSI 精靈的最後一個畫面中，選取 **執行應用程式安裝精靈在本機電腦上安裝應用程式**，然後按一下 **完成**。  
  
     ![從匯入精靈啟動安裝](../core/media/startinstallation.gif "StartInstallation")  
  
9. 在**選取安裝資料夾**頁面上，於**資料夾**，輸入 BizTalk 應用程式的安裝路徑，然後按一下**下一步**。  
  
10. 按一下**下一步**接下來的三頁面以繼續安裝。  
  
     Windows Installer 就會將應用程式安裝在本機電腦上。  
  
11. 在**安裝完成**頁面上，按一下**關閉**。  
  
 如需有關匯入應用程式的詳細資訊，請參閱[如何匯入 BizTalk 應用程式](../core/how-to-import-a-biztalk-application.md)。 如需有關如何安裝應用程式的詳細資訊，請參閱[如何安裝 BizTalk 應用程式](../core/how-to-install-a-biztalk-application.md)。  
  
 接下來，您可以檢查下列事項來確定已匯入並安裝了應用程式：  
  
-   在管理主控台中，應用程式及其所有成品都存在於該應用程式的資料夾內。  
  
-   應用程式組件存在於 GAC 中。  
  
-   與應用程式關聯的檔案存在於您當初安裝應用程式時指定的路徑中。  
  
-   應用程式顯示在 [控制台] 的 [新增或移除程式] 中。  
  
-   如果您已設定應用程式，使它可以正常運作，例如透過指定傳送和接收埠，您現在可以啟動應用程式按滑鼠右鍵，然後按一下**啟動**。 不過，ErrorHandling 範例應用程式在預設情況下，並未設定成可以正常運作，所以除非您已經手動加以設定，否則無法啟動它。  
  
-   若要完全移除應用程式的 BizTalk 群組和本機電腦，請依照中的指示[解除部署 BizTalk 應用程式](../core/undeploying-biztalk-applications.md)。  
  
## <a name="see-also"></a>另請參閱  
[了解 BizTalk 應用程式部署和管理](../core/understanding-biztalk-application-deployment-and-management.md)