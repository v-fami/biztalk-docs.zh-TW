---
title: "使用 Visual Studio |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio
ms.assetid: 1ef68df2-5205-4d96-9e0f-0ae78800a121
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b48f5aca0bd1e5c17d942e332f7f3d223d752b67
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-visual-studio"></a>使用 Visual Studio
在 BizTalk 專案系統中，您可使用 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中的許多可用工具，以及專為建立在 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 上執行的應用程式而設計的工具。 本主題描述一些您可用來建立在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 上執行之應用程式的常見程序。  
  
 當您使用 BizTalk 專案系統時，會使用許多相同的使用者介面 (UI) 元件 (例如 [方案總管] 和 [屬性] 視窗) 來建立應用程式。 此外，像是 BizTalk 編輯器等元件，只有在您安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 之後才可使用。 這些特定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] UI 元件除了可搭配任何專案系統使用，更可讓您建置能在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 上執行的應用程式。  
  
 雖然 BizTalk 專案系統使用許多與其他 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 專案系統相同的功能表和功能表命令，不過，在使用 BizTalk 專案系統時，有些命令卻是新的、無法使用的、經過擴充的或有限制的。 這個主題描述在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中可用的各種功能表，以及這些功能表與 BizTalk 專案系統互動的方式。  
  
> [!NOTE]
>  下列主題著重在顯示運作方式與 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 不同的功能表和功能表項目。  
  
## <a name="file-menu"></a>檔案功能表  
 大部分的**檔案**功能表命令的運作方式與其他的 BizTalk 專案的相同[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]專案。 使用於 BizTalk 專案時，部分的命令不支援或無法使用。 例如，**列印**當您使用管線時，不支援命令。  
  
## <a name="view-menu"></a>檢視功能表  
 下表列出 BizTalk 專案系統視窗、 工具列和可從工具箱**檢視**功能表。  
  
|子功能表名稱|子功能表名稱 (若適用)|Description|  
|------------------|------------------------------------|-----------------|  
||||  
|**其他視窗**|**協調流程檢視**|[協調流程檢視] 這個視窗，可以讓您新增、刪除和檢查協調流程參數、連接埠與連接埠類型、訊息與多部分訊息類型、相互關聯集與相互關聯類型、角色連結與角色連結類型、範圍以及協調流程屬性。 **注意：**此視窗，才可以從開啟的協調流程內使用。|  
|**其他視窗**|**運算式編輯器**|運算式編輯器屬於可用視窗之一，是一個附有 IntelliSense 而可讓您輸入複雜運算式的標準 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 文字編輯器。|  
|**[工具箱]**|**BizTalk 管線元件**|此為列出您可拖曳至管線設計介面上的管線元件之清單。 您只能新增管線元件到可用的作用中管線。|  
|**[工具箱]**|**BizTalk 協調流程**|此為列出您可拖曳至協調流程設計介面上的協調流程圖形之清單。|  
|**[工具箱]**|**BizTalk 對應工具**|此為列出您可拖曳至對應格線介面上的運算質之清單。 運算質依其功能分組。|  
|**工具列**|**BizTalk 編輯器**|簡化建立結構化文件結構描述的程序之視覺工具，以 XML 結構描述定義語言 (XSD) 指定，可用於 XML 與非 XML 格式。|  
|**工具列**|**BizTalk 對應工具**|一項圖形使用者介面工具，可簡化指定 XML 文件轉換的程序，以使用 [BizTalk 編輯器] 建立的兩個結構描述為基礎，產生「可延伸樣式表語言轉換」(XSLT) 樣式表作為已編譯輸出。|  
  
## <a name="project-menu"></a>專案功能表  
 下表列出的某些命令上**專案**功能表。  
  
|子功能表名稱|Description|  
|------------------|-----------------|  
|**加入參考**|使用此功能表項目以參考其他專案、其他 .NET 專案或 COM 專案。|  
|**加入服務參考**|使用此功能表項目加入 WCF 服務參考。 您也使用此項目，即可將 Web 參考**進階**上**加入服務參考** 對話方塊。|  
|**加入產生的項目**|使用此功能表項目加入產生的配接器或結構描述檔案，或是取用 WCF 服務。|  
|**新增配接器服務參考**|使用此功能表項目以瀏覽 (和搜尋) 中繼資料，並使用選取的作業和/或類型產生 .NET CLR Proxy 類別。 **注意：**此項目會出現在 BizTalk 功能表只有當至少一張介面卡 (隨附於[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]) 安裝在電腦上。|  
|**加入使用配接器參考**|使用此功能表項目從配接器瀏覽 (和搜尋) 中繼資料，然後產生已選取作業的 XML 結構描述。 **注意：**此項目會出現在 BizTalk 功能表只有當至少一張介面卡 (隨附於[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]) 安裝在電腦上。|  
  
 如需將 BizTalk Web 服務的 Web 參考加入資訊，請參閱[加入 Web 參考](../core/adding-web-references.md)。  
  
## <a name="build-menu"></a>建置功能表  
 **建置**功能表包含建置命令。 它也包含要執行的命令**Configuration Manager**設定組建與部署組態選項。 若要部署專案，以滑鼠右鍵按一下方案總管] 中的專案，然後按一下 [**部署**命令。 只有當您在開發應用程式或者當您的實例很簡單時，才使用這個部署方法。 這種部署方法沒有**不**追蹤版本，，而且您可以輕鬆地覆寫舊版的組件。 在開發或測試階段中重複使用相同版本是相當有用的，但是在生產環境中就不是這麼一回事。 如需部署資訊，請參閱[瞭解 BizTalk 應用程式部署和管理](../core/understanding-biztalk-application-deployment-and-management.md)。  
  
 若要將您的 BizTalk 成品新增到 BizTalk 管理資料庫，請執行「組件部署精靈」。 如需組件部署精靈 」 的詳細資訊，請參閱[如何部署 BizTalk 組件從 Visual Studio](../core/how-to-deploy-a-biztalk-assembly-from-visual-studio.md)。  
  
> [!NOTE]
>  [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 包含 Dotfuscator 的版本，它會對已編譯的組件進行模糊化，並重新命名符號及其他識別項，藉以保護智慧財產。 透過此工具執行的組件無法加以部署。  
  
## <a name="debug-menu"></a>偵錯功能表  
 BizTalk 專案系統支援**偵錯**功能表命令。 如需有關偵錯資訊[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，請參閱[偵錯協調流程](../core/debugging-orchestrations.md)。  
  
## <a name="biztalk-menu"></a>BizTalk 功能表  
 當您使用專案時， **BizTalk**當您開啟 BizTalk 編輯器 」 或 「 BizTalk 對應工具或 「 BizTalk 協調流程設計師時，就會出現功能表。 換句話說，當您嘗試編輯結構描述或對應或協調流程時，就會出現 [BizTalk] 功能表。  
  
> [!NOTE]
>  雖然您可以在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中從其他專案系統存取「協調流程設計師」、「BizTalk 編輯器」以及「BizTalk 對應工具」，不過，這些 BizTalk 工具的行為可能難以預測。 您應該在 BizTalk 專案的環境中使用「協調流程設計師」、「BizTalk 編輯器」以及「BizTalk 對應工具」。  
  
## <a name="help-menu"></a>說明功能表  
 下表列出的某些命令上**協助**功能表與[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。  
  
|功能表命令|Description|  
|------------------|-----------------|  
|**動態說明**|此功能表命令會開啟**動態說明**動態產生主題的索引標籤會根據工作。|  
|**目錄**|此功能表命令會開啟**內容**索引標籤，顯示所有已安裝的說明集合。 您必須已安裝 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 與 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的產品文件，才能檢視內容。|  
|**關於 Microsoft BizTalk Server**|此功能表命令會開啟**關於 Microsoft BizTalk Server**  對話方塊。 此對話方塊會顯示 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 產品資訊。|  
|**Index**|在此版本中，「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 說明」文件無法透過索引加以存取。|  
|**搜尋**|沒有任何篩選條件的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]說明 」 文件，在此版本中，但如果您選取**（未篩選）**中**經過**下拉式清單中，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]說明文件，可用於搜尋。|  
  
## <a name="property-pages"></a>屬性頁  
 您可以使用專案設計工具中的屬性頁，來為 BizTalk 專案設定組件專案屬性和部署屬性。  
  
### <a name="procedures"></a>程序  
  
##### <a name="to-configure-assembly-project-properties"></a>設定組件專案屬性  
  
1.  在 [方案總管] 中，選取一個專案。  
  
2.  在**專案**功能表上，按一下 **屬性**啟動專案設計工具。  
  
3.  按一下**應用程式** 索引標籤。  
  
4.  按一下**組件資訊**及更新的所需的組件屬性。  
  
    > [!NOTE]
    >  使用**簽署**] 索引標籤來指定組件的金鑰檔位置，如果您使用的憑證與您在執行的應用程式的 [專案設計工具中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  
  
##### <a name="to-configure-deployment-properties"></a>若要設定部署屬性  
  
1.  選取您想要設定部署屬性的專案。  
  
2.  在**專案**功能表上，按一下 **屬性**啟動專案設計工具。  
  
3.  按一下**部署**索引標籤上，並更新您的部署屬性。  
  
## <a name="see-also"></a>另請參閱  
 [開發人員工具](../core/developer-tools.md)