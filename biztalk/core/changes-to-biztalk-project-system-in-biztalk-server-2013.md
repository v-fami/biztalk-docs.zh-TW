---
title: "在 BizTalk Server 2013 中的 BizTalk 專案系統變更 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 82f0dd18-073c-4cba-aa0d-48076c58f874
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dff1f35955229306bc2f39e0af670f939dec82da
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="changes-to-biztalk-project-system-in-biztalk-server-2013"></a>在 BizTalk Server 2013 中的 BizTalk 專案系統變更
本主題提供您有關 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] 中 BizTalk 專案系統變更的概要簡介。  
  
## <a name="project-properties-are-displayed-in-project-designer-window"></a>專案屬性會顯示在專案設計工具視窗中  
 BizTalk Server 專案的屬性現在會顯示於 Visual Studio 的專案設計工具中，而非 [屬性] 對話方塊中。 專案設計工具提供了可供管理專案屬性、設定和資源的集中式位置。 專案設計工具會和其他設計工具 (如表單或類別設計工具) 一樣，以單一視窗的形式顯示在 Visual Studio IDE 中，並包含一些可透過左側索引標籤存取的頁面。 如需詳細資訊，請參閱[http://go.microsoft.com/fwlink/?LinkId=190417](http://go.microsoft.com/fwlink/?LinkId=190417)。  
  
## <a name="properties-for-schema-and-map-files-are-displayed-in-properties-window"></a>結構描述與對應檔案的屬性會顯示在屬性視窗中  
 屬性結構描述和對應檔案，例如**輸入執行個體檔案名稱**和**測試對應輸入執行個體**會顯示在 屬性 視窗而不是在個別**屬性**  對話方塊。  
  
## <a name="add-web-reference-option-on-projects"></a>專案上的加入 Web 參考選項  
 **加入 Web 參考**選項時，無法使用您以滑鼠右鍵按一下專案名稱或**參考**在 [方案總管] 中。 您可以使用下列步驟，加入 Web 服務 (.asmx) 的 Web 參考︰  
  
1.  以滑鼠右鍵按一下**參考**中專案，然後按一下**加入服務參考**。  
  
2.  在**加入服務參考**對話方塊中，按一下 **進階**。  
  
3.  在**服務參考設定**對話方塊中，按一下 **加入 Web 參考**。  
  
4.  輸入 URL，然後按一下**移**。  
  
5.  按一下**加入參考**加入 Web 參考。  
  
    > [!TIP]
    >  加入 Web 參考加入 BizTalk 專案之後,**加入 Web 參考**參考、 Web 參考和專案節點上就提供功能表選項。  
  
 如需加入服務與 Web 參考的詳細資訊，請參閱[http://go.microsoft.com/fwlink/?LinkId=131577](http://go.microsoft.com/fwlink/?LinkId=131577)。  
  
## <a name="msbuild-integration"></a>MSBUILD 整合  
 Visual Studio 使用 MSBUILD 專案檔案格式來儲存有關受管理專案 (包含 BizTalk 專案) 的建置資訊。 如需詳細資訊，請參閱[與 Visual Studio 的 MSBUILD 整合](../core/msbuild-integration-with-visual-studio.md)。  
  
## <a name="team-foundation-server-integration"></a>Team Foundation Server 整合  
 您可以使用 Team Foundation Server 做為 BizTalk 專案的來源控制系統。 您可以從 [方案總管] 視窗本身執行存回及取出等作業。  
  
## <a name="support-for-unit-testing"></a>支援單元測試  
 這項功能可讓您進行結構描述、對應和管線的單元測試。 如需詳細資訊，請參閱[單元測試使用 BizTalk Server 專案](../core/unit-testing-with-biztalk-server-projects.md)。  
  
## <a name="debug-map-feature"></a>偵錯對應功能  
 **偵錯對應功能**。 您可以使用 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中內嵌的 XSLT 偵錯工具，以偵錯對應 (XSLT)。 如需詳細資訊，請參閱[如何偵錯對應](../core/how-to-debug-maps.md)。  
  
## <a name="migrating-biztalk-server-projects"></a>移轉的 BizTalk Server 專案  
 使用 Visual Studio 轉換精靈，可以將針對較舊版本 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 開發的 Visual Studio 專案移轉至 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] 環境。 如需詳細資訊，請參閱[移轉 BizTalk Server 專案](../core/migrating-a-biztalk-server-project.md)。  
  
## <a name="release-and-debug-build-types"></a>發行和偵錯組建類型  
 BizTalk 專案現在有兩個組建類型：**發行**和**偵錯**，取代了**開發**和**部署**的前面版本。 不過，您將會繼續看見**開發**和**部署**從移轉的專案組態[!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)]。  
  
## <a name="embedding-tracking-and-debugging-information"></a>內嵌追蹤和偵錯資訊  
 **內嵌追蹤資訊**和**產生偵錯資訊**輸出組態屬性會取代**定義 TRACE 常數**和**定義 DEBUG 常數**上建置選項**建置**專案設計工具 索引標籤。 **BPEL 規範程式碼產生**組態屬性會取代**BPEL 規範程式碼產生**專案屬性 視窗中的屬性。  
  
> [!IMPORTANT]
>  Visual Studio 轉換精靈會負責將前述設定自動移轉到新環境。  
  
## <a name="user-access-control"></a>使用者存取控制  
 除非您以系統管理權限執行 Visual Studio，否則 Visual Studio 不會讓您在已開啟使用者存取控制 (UAC) 功能的電腦上部署 BizTalk 專案。 以系統管理權限執行 Visual Studio，請按一下**啟動**，指向 **所有程式**，指向  **Microsoft Visual Studio**，以滑鼠右鍵按一下**Microsoft Visual Studio\<版本 >**，然後按一下 **系統管理員身分執行**。  
  
## <a name="c-files-in-a-biztalk-project"></a>BizTalk 專案中的 C# 檔案  
 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]可讓您結合只有滿足您彈性封裝需要的 BizTalk 成品的 helper 類別。  不過，您無法加入新的 C# 檔案直接透過使用**加入新項目**或**加入新類別**功能表選項。  
  
## <a name="generatecsfiles-registry-key-is-obsolete"></a>GenerateCSFiles 登錄機碼已過時  
 **GenerateCSFiles**登錄機碼現在已過時。 所有產生的 .cs 檔都會顯示在 [方案總管] 視窗中。 您可能需要按一下**顯示所有檔案**中，查看與某些 BizTalk 項目相關聯的.cs 檔案的 [方案總管] 視窗的工具列項目。