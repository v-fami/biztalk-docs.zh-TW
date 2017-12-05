---
title: "如何使用 BizTalk WCF 服務發佈精靈發佈之 WCF 接收位置的服務中繼資料繫結至協調流程連接埠 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Service Publishing Wizard, publishing metadata
- WCF services, orchestration ports
- WCF services, metadata
- orchestrations, WCF services
ms.assetid: 04ccce9f-8d18-433a-8299-d06fa155db06
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a2dce9a66465285dc16f8de804c7a6e99fa7e62a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-use-the-biztalk-wcf-service-publishing-wizard-to-publish-service-metadata-for-a-wcf-receive-location-bound-to-an-orchestration-port"></a>如何使用 BizTalk WCF 服務發佈精靈來發佈繫結至協調流程連接埠之 WCF 接收位置的服務中繼資料
您可以使用 BizTalk WCF 服務發佈精靈來建立 WCF 服務，以便發佈繫結至協調流程連接埠之現有 WCF 接收位置的服務中繼資料。  
  
> [!NOTE]
>  您必須先建置 BizTalk 專案，然後再執行 BizTalk WCF 服務發佈精靈。 BizTalk 專案必須包括至少有一個型別修飾詞為公用之接收埠的協調流程。 發佈 WCF 配接器的服務中繼資料之前，您也必須使用 BizTalk 管理主控台或 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 隨附的 BTSTask 命令列工具來建立 WCF 接收位置。 如需有關如何建立 WCF 接收位置，請參閱中的每個 WCF 配接器的適當主題[WCF 配接器](../core/wcf-adapters.md)。  
  
### <a name="to-publish-service-metadata-for-an-existing-wcf-receive-location-bound-to-an-orchestration-port"></a>若要發佈繫結至協調流程連接埠之現有 WCF 接收位置的服務中繼資料  
  
1.  按一下**啟動**，指向 **所有程式**，指向  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk WCF 服務發佈精靈**。  
  
    > [!NOTE]
    >  若要建立並發佈 BizTalk 協調流程和結構描述的 WCF 服務中繼資料，您可以使用 BizTalk WCF 服務發佈精靈。 若要以 SOAP 配接器將協調流程和結構描述發佈成 Web 服務，您可以使用 BizTalk Web 服務發佈精靈。  
  
2.  在**歡迎使用 BizTalk WCF 服務發佈精靈**頁面上，按一下**下一步**。  
  
3.  在**WCF 服務類型**頁面上，選取**中繼資料唯一端點 (MEX)**選項來發佈 WCF 服務，以提供服務中繼資料之 wcf 接收位置，您將在下一個步驟中選取。  
  
     ![WCF 服務類型 頁面上](../core/media/794a85b5-6454-4cce-8c15-382b5583b0f2.gif "794a85b5-6454-4cce-8c15-382b5583b0f2")  
  
4.  在**WCF 服務類型**頁面上，於**發行中繼資料的接收位置**下拉式清單中，選取之 WCF 接收位置發佈服務中繼資料，然後按一下**下一步**.  
  
5.  在**建立 WCF 服務**頁面上，選取**BizTalk 協調流程發佈為 WCF 服務**，然後按一下 **下一步**。  
  
     ![建立 WCF 服務頁面](../core/media/86cb66b5-6842-4330-8942-20afa68ec5fa.gif "86cb66b5-6842-4330-8942-20afa68ec5fa")  
  
6.  在**BizTalk 組件**頁面上，於**BizTalk 組件檔案 (\*.dll)**文字方塊中，輸入 BizTalk 組件檔案的名稱，或按一下**瀏覽**瀏覽至包含的組件協調流程來發行服務中繼資料，然後按一下**下一步**。  
  
    > [!NOTE]
    >  選取 BizTalk 組件檔案之前，請將所有相依組件與 BizTalk 組件複製到相同的資料夾中，或將這些相依組件安裝至全域組件快取 (GAC)。  
  
    > [!NOTE]
    >  如果您安裝到 GAC 的 BizTalk 組件檔案，請確定您會在選取的組件，已更新組件在 GAC 中的**BizTalk 組件** 對話方塊。 如果 GAC 中的組件具有相同的完整格式名稱，BizTalk WCF 服務發佈精靈就會使用 GAC 中的組件檔案，而非您所選取的組件檔案。  
  
    > [!NOTE]
    >  長度超過 260 個字元的路徑可能會導致路徑太長的錯誤訊息出現。  
  
     ![BizTalk 組件頁面](../core/media/d34a027e-ea82-4048-8b15-d97df795b0d4.gif "d34a027e-ea82-4048-8b15-d97df795b0d4")  
  
7.  在**協調流程和連接埠**頁面上，按一下加號 （+） 展開每個組件和協調流程的樹狀節點。 透過選取對應樹狀節點的核取方塊，選取要發佈中繼資料的協調流程和連接埠。 如果您想要建立一個 WCF 服務 （.svc 檔案） 的所有選取的接收埠，而不是一個 WCF 服務，每個接收埠，請選取**所有選取的連接埠合併成單一 WCF 服務**選項，然後再按一下**下一步**。  
  
    > [!NOTE]
    >  當您將所有選取的連接埠合併成單一 WCF 服務時，所有選取的連接埠都會具有相同的連接埠類型，而且這些連接埠中的作業名稱都是唯一的。  
  
     ![作業和連接埠頁面](../core/media/97112744-ddd4-4512-ac56-41317ba9412b.gif "97112744-ddd4-4512-ac56-41317ba9412b")  
  
8.  在**WCF 服務屬性**頁面上，於**WCF 服務的 Targetnamespace**  文字方塊中，輸入 WCF 服務的目標命名空間，然後按一下**下一步**。  
  
     ![WCF 服務屬性頁面](../core/media/07518c78-bcae-4274-bb14-aeef107ee4c6.gif "07518c78-bcae-4274-bb14-aeef107ee4c6")  
  
9. 在**WCF 服務位置**頁面上，於**位置**文字方塊中，輸入產生 WCF 服務位置的 Web 目錄名稱。 您可以接受預設位置 (http://localhost/ <*BizTalk 組件名稱*>)，輸入中的 WCF 服務的位置**位置**文字方塊中或按一下**瀏覽**，並選取 Web 目錄。 接著，選取下列任何一個選項：  
  
    -   **覆寫現有的專案。** 此選項只有在 Web 目錄已存在時才能使用。 只有當您選取了這個選項時，才能夠發佈至相同的位置。 否則，您必須輸入不同的專案位置。  
  
    -   **允許匿名存取 WCF 服務。** 這個選項會新增已建立之虛擬目錄的匿名存取。 根據預設，虛擬目錄會從其父虛擬目錄或網站 (如果它是最上層虛擬目錄的話) 繼承存取權限。  
  
     當您完成這個頁面上時，按一下**下一步**。  
  
     ![WCF 服務位置頁面](../core/media/76285470-1520-4d77-a5b6-c58cbe8fc575.gif "76285470-1520-4d77-a5b6-c58cbe8fc575")  
  
    > [!NOTE]
    >  專案位置可以存在不同的伺服器上。 若要將 WCF 服務發佈到另一部伺服器中，輸入專案名稱做為 http://&lt*servername*>/<*WCF 服務位置*>。  
  
    > [!NOTE]
    >  專案位置可以存在非預設的網站上。 發佈至非預設的網站時，請在 URL 中加入網站的連接埠編號。 例如，http://&lt*servername*>: 8080 / <*WCF 服務位置*>。  
  
    > [!NOTE]
    >  精靈會建立 Web 應用程式的 App_DataTemp 資料夾中的 BindingInfo.xml 檔案會使用預設值的管線。 接收管線的預設值是**Microsoft.BizTalk.DefaultPipelines.XMLReceive**管線，而預設值的傳送管線是**Microsoft.BizTalk.DefaultPipelines.PassThruTransmit**管線。  
  
10. 在**WCF 服務摘要**頁面上，檢閱您的 WCF 服務的設定。  
  
11. 按一下**建立**建立 WCF 服務。  
  
12. 按一下**完成**完成 BizTalk WCF 服務發佈精靈。  
  
### <a name="to-configure-the-web-application-for-publishing-service-metadata"></a>若要設定發佈服務中繼資料的 Web 應用程式  
  
1.  針對 BizTalk WCF 服務發佈精靈所建立的 Web 應用程式啟用 ASP.NET。 如需詳細資訊，請參閱[啟用 Web 服務](../core/enabling-web-services.md)。  
  
    > [!NOTE]
    >  如果您正使用 Windows Server 2008 或 Windows Vista，就必須將應用程式集區的識別帳戶新增至 BizTalk Server Administrators 群組。 將適當的帳戶新增至 BizTalk Server 系統管理員群組之後，您必須重新啟動 IIS 服務，才能讓設定生效。  
  
2.  開啟命令提示字元，請移至 BizTalk WCF 服務發佈精靈建立 WCF 服務中 %SystemDrive%\InetPub 資料夾\\，然後開啟 Web.config 檔案，使用 記事本。  
  
3.  在記事本中，加入下列一行 **\<system.web\>** 項目：  
  
    ```  
    <trust level="Full" originUrl="" />  
    ```  
  
    > [!NOTE]
    >  這項設定是選擇性的，而且它會將受限於作業系統安全性之任何資源的存取權授與主控已發佈之 WCF 服務的 ASP.NET 應用程式。 當您在同一部電腦上安裝和執行 Windows SharePoint Services 以及已發佈的 WCF 服務時，這就是 WCF 所需的信任層級。  
  
4.  在 Internet Explorer 中**位址**方塊中，輸入使用 http:// 的格式為 WCF 服務的 URL*主機 [: 連接埠]*/*apppath* /*wcfservicename.svc*來測試已發佈的 WCF 服務。 下表將描述這些參數。  
  
    |參數|值|  
    |---------------|-----------|  
    |*主機 [: 連接埠]*|您已部署 WCF 服務之電腦的名稱。 冒號和連接埠編號可以接在這個伺服器名稱後面。|  
    |*apppath*|虛擬目錄的名稱和 Web 應用程式路徑。|  
    |*wcfservicename.svc*|WCF 服務 .svc 檔案的名稱。|  
  
5.  為了避免不小心洩露可能含有機密的服務中繼資料，我們建議您透過執行下列工作，在實際執行環境中停用這種行為：  
  
    1.  在 記事本 開啟 BizTalk WCF 服務發佈精靈建立 WCF 服務中 %SystemDrive%\InetPub 資料夾中的 Web.config\\。  
  
    2.  在 [記事本]，設定**httpGetEnabled**屬性 **\<serviceMetadata\>** 為 false，如下列一行所示的項目：  
  
        ```  
        <serviceMetadata httpGetEnabled="false" httpsGetEnabled="false" />  
        ```  
  
## <a name="see-also"></a>請參閱  
 [如何使用 BizTalk WCF 服務發佈精靈來發佈 WCF 接收位置的內容為基礎的路由服務中繼資料](../core/publish-service-metadata-for-a-wcf-receive-location-for-content-based-routing.md)   
 [逐步解說：使用 WCF-NetMsmq 配接器發佈 WCF 服務](../core/walkthrough-publishing-wcf-services-with-the-wcf-netmsmq-adapter.md)