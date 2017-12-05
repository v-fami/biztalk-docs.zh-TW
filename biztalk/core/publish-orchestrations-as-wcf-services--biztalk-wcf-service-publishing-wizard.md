---
title: "如何使用 BizTalk WCF 服務發佈精靈協調流程發佈為 WCF 服務 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tools, WCF Service Publishing Wizard
- WCF services, WCF Service Publishing Wizard
- WCF services, orchestrations
- publishing, orchestrations [WCF services]
- orchestrations, WCF services
- WCF Service Publishing Wizard
ms.assetid: db352132-2fe8-4d53-b239-45e5c3525b6c
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 76e233cfdd0871b55776cdf7cbaa9ee5b2af2724
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-use-the-biztalk-wcf-service-publishing-wizard-to-publish-orchestrations-as-wcf-services"></a>如何使用 BizTalk WCF 服務發佈精靈將協調流程發佈為 WCF 服務
您可以使用 [BizTalk WCF 服務發佈精靈] 將協調流程發佈為 WCF 服務。  
  
> [!NOTE]
>  您必須先建置 BizTalk 專案，然後再執行 BizTalk WCF 服務發佈精靈。 BizTalk 專案必須包括至少有一個型別修飾詞為公用之接收埠的協調流程。 當連接埠建立時，這個類型修飾詞會存在協調流程的屬性中。  
  
### <a name="to-publish-an-orchestration-as-a-wcf-service"></a>若要將協調流程發佈為 WCF 服務  
  
1.  按一下**啟動**，指向 **所有程式**，指向  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，然後按一下  **BizTalk WCF 服務發佈精靈**。  
  
    > [!NOTE]
    >  您可以使用 [BizTalk WCF 服務發佈精靈] 來建立 BizTalk 協調流程和結構描述，並使用 WCF 配接器將它們發佈為 WCF 服務。 若要以 SOAP 配接器將協調流程和結構描述發佈成 Web 服務，您可以使用 BizTalk Web 服務發佈精靈。  
  
2.  在**歡迎使用 BizTalk WCF 服務發佈精靈**頁面上，按一下**下一步**。  
  
3.  在**WCF 服務類型**頁面上，選取**服務端點**BizTalk 組件中選取 BizTalk 協調流程上發佈 WCF 服務的選項。  
  
     ![WCF 服務類型 頁面上](../core/media/959900fd-44c9-4f3a-8836-9786a2f5e707.gif "959900fd-44c9-4f3a-8836-9786a2f5e707")  
  
4.  在**WCF 服務類型**頁面上，選取**啟用中繼資料端點**核取方塊以指出外掛式的 WCF 接收位置網際網路資訊服務 (IIS) 裝載是否發行服務中繼資料使用 HTTP/GET 要求擷取。 啟用此核取方塊，精靈便會產生 Web.config 其中**httpGetEnabled**屬性 **\<serviceMetadata\>** 元素設定為**，則為 true**. 您可以在開發環境中使用中繼資料匯入工具 (例如 SvcUtil.exe) 產生呼叫此服務所需的用戶端程式碼。 中繼資料發行的位址是端點位址加上一個**？ wsdl**查詢字串。  
  
    > [!NOTE]
    >  為避免不慎洩露較為機密的服務中繼資料，建議您在實際執行環境中停用此行為。 這可透過將 httpgetenabled 設為 False 或刪除 MEX 虛擬目錄來完成。  
  
5.  在**WCF 服務類型**頁面上，於**配接器名稱 （傳輸類型）**下拉式清單中，選取要用來發佈 WCF 服務的外掛式的 WCF 配接器。 您可以選取下列任何一個配接器：  
  
    -   **Wcf-basichttp。** WCF-BasicHttp 配接器可以與 WS-I 基本設定檔 1.1 相符的 Web 服務 (例如以 ASMX 為基礎的服務) 通訊。  
  
    -   **Wcf-wshttp。** WCF-WSHttp 配接器可以透過 HTTP 和 HTTPS 上的 WS-* 標準，與服務進行通訊。  
  
    -   **Wcf-customisolated。** WCF-CustomIsolated 配接器可以在 HTTP 傳輸上啟用 Windows Communication Foundation (WCF) 擴充性功能。  
  
6.  在**WCF 服務類型**頁面上，選取**下列應用程式中的建立 BizTalk 接收位置**核取方塊來建立接收埠與對應於每個產生的.svc 檔案的位置您在選取的 WCF 配接器**配接器名稱**下拉式清單。 如果接收位置已經存在，則不會取代該接收位置。 選取此選項之後，選擇 應用程式，其中的接收埠和位置將會產生在**BizTalk 應用程式名稱**下拉式清單，然後按一下**下一步**。  
  
7.  在**建立 WCF 服務**頁面上，選取**BizTalk 協調流程發佈為 WCF 服務**，然後按一下 **下一步**。  
  
     ![建立 WCF 服務頁面](../core/media/86cb66b5-6842-4330-8942-20afa68ec5fa.gif "86cb66b5-6842-4330-8942-20afa68ec5fa")  
  
8.  在**BizTalk 組件**頁面上，於**BizTalk 組件檔案 (\*.dll)**文字方塊中，輸入 BizTalk 組件檔案的名稱，或按一下**瀏覽**瀏覽至包含的組件協調流程來發行，然後按一下**下一步**。  
  
    > [!NOTE]
    >  選擇 BizTalk 組件檔案之前，請將所有相依的組件複製到與 BizTalk 組件相同的資料夾中，或將這些相依組件安裝至全域組件快取 (GAC)。  
  
    > [!NOTE]
    >  如果您安裝到 GAC 的 BizTalk 組件檔案，請確定您會在選取的組件，已更新組件在 GAC 中的**BizTalk 組件** 對話方塊。 如果 GAC 中的組件具有相同的完整格式名稱，BizTalk WCF 服務發佈精靈就會使用 GAC 中的組件檔案，而非您所選取的組件檔案。  
  
    > [!NOTE]
    >  長度超過 260 個字元的路徑可能會導致路徑太長的錯誤訊息出現。  
  
     ![BizTalk 組件頁面](../core/media/d34a027e-ea82-4048-8b15-d97df795b0d4.gif "d34a027e-ea82-4048-8b15-d97df795b0d4")  
  
9. 在**協調流程和連接埠**頁面上，按一下加號 （+） 展開每個組件和協調流程的樹狀節點。 透過選取對應樹狀節點的核取方塊，選取要發佈的協調流程和連接埠。 如果您想要建立一個 WCF 服務 （.svc 檔案） 的所有選取的接收埠，而不是一個 WCF 服務，每個接收埠，請選取**所有選取的連接埠合併成單一 WCF 服務**選項，然後再按一下**下一步**。  
  
    > [!NOTE]
    >  當您將所有選取的連接埠合併成單一 WCF 服務時，所有選取的連接埠都會具有相同的連接埠類型，而且這些連接埠中的作業名稱都是唯一的。  
  
     ![作業和連接埠頁面](../core/media/97112744-ddd4-4512-ac56-41317ba9412b.gif "97112744-ddd4-4512-ac56-41317ba9412b")  
  
10. 在**WCF 服務屬性**頁面上，於**WCF 服務的 Targetnamespace**  文字方塊中，輸入 WCF 服務的目標命名空間，然後按一下**下一步**。  
  
     ![WCF 服務屬性頁面](../core/media/07518c78-bcae-4274-bb14-aeef107ee4c6.gif "07518c78-bcae-4274-bb14-aeef107ee4c6")  
  
11. 在**WCF 服務位置**頁面上，於**位置**文字方塊中，輸入產生 WCF 服務位置的 Web 目錄名稱。 您可以接受預設位置 (http://localhost/ <*BizTalk 組件名稱*>)，輸入中的 WCF 服務的位置**位置**文字方塊中或按一下**瀏覽**，並選取 Web 目錄。 接著，選取下列任何一個選項：  
  
    -   **覆寫現有的專案。** 這個選項只有在 Web 目錄已經存在時才能使用。 只有當您選取了這個選項時，才能夠發佈至相同的位置。 否則，您必須輸入不同的專案位置。  
  
    -   **允許匿名存取 WCF 服務。** 這個選項會新增已建立之虛擬目錄的匿名存取。 根據預設，虛擬目錄會從其父虛擬目錄或網站 (如果它是最上層虛擬目錄的話) 繼承存取權限。  
  
     當您完成這個頁面上時，按一下**下一步**。  
  
     ![WCF 服務位置頁面](../core/media/76285470-1520-4d77-a5b6-c58cbe8fc575.gif "76285470-1520-4d77-a5b6-c58cbe8fc575")  
  
    > [!NOTE]
    >  專案位置可以存在不同的伺服器上。 若要將 WCF 服務發佈到另一部伺服器中，輸入專案名稱做為 http://&lt*servername*>/<*WCF 服務位置*>。  
  
    > [!NOTE]
    >  專案位置可以存在非預設的網站上。 發佈至非預設的網站時，請在 URL 中加入網站的連接埠編號。 例如，http://&lt*servername*>: 8080 / <*WCF 服務位置*>。  
  
    > [!NOTE]
    >  在使用精靈建立接收位置時，精靈會使用預設值來建立接收位置。 接收管線的預設值是**Microsoft.BizTalk.DefaultPipelines.PassThruReceive**管線。 如果透過已發佈的 WCF 服務收到的訊息需要任何特殊管線處理 （例如，驗證、 相互關聯/屬性升級或輸入/輸出對應），則您應該設定接收管線**Microsoft.BizTalk.DefaultPipelines.XMLReceive**，或自訂管線，使用 BizTalk Server 管理主控台。  
  
    > [!NOTE]
    >  如果您決定不要使用**協調流程發佈為 WCF 服務**選項之後，您在到達此頁面上，**建立 WCF 服務**頁面上，您可能會看到的**Web 服務描述** BizTalk 組件之前您所選取的服務和方法名稱的顯示變更發佈選項。 這是因為發佈方法變更時，記憶體中的 Web 服務描述並未清除。  
  
12. 在**WCF 服務摘要**頁面上，檢閱您的 WCF 服務的設定。  
  
13. 按一下**建立**建立 WCF 服務。  
  
14. 按一下**完成**完成 BizTalk WCF 服務發佈精靈。  
  
15. 在使用 [BizTalk WCF 服務發佈精靈] 發佈 WCF 服務之後，您還必須適當設定這些服務。 如需有關如何設定外掛式的 WCF 接收配接器，請參閱[如何使用 BizTalk WCF 服務發佈精靈設定 WCF 服務發佈](../core/configure-wcf-services-published-with-the-biztalk-wcf-service-publishing-wizard.md)。  
  
## <a name="see-also"></a>請參閱  
 [如何設定使用 BizTalk WCF 服務發佈精靈發佈的 WCF 服務](../core/configure-wcf-services-published-with-the-biztalk-wcf-service-publishing-wizard.md)   
 [逐步解說： 使用發佈 WCF 服務 Wcf-basichttp 配接器](../core/walkthrough-publishing-wcf-services-with-the-wcf-basichttp-adapter.md)   
 [如何使用 BizTalk WCF 服務發佈精靈結構描述發佈為 WCF 服務](../core/publish-schemas-as-wcf-services--use-the-biztalk-wcf-service-publishing-wizard.md)