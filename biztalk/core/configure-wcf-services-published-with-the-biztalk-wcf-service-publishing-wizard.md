---
title: 如何使用 BizTalk WCF 服務發佈精靈發佈的 WCF 服務的設定 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF services, WCF Service Publishing Wizard
- WCF services, configuring
- configuring, WCF services
- WCF Service Publishing Wizard
ms.assetid: f51b86c0-8c19-453d-a66d-3f373e9f096e
caps.latest.revision: 26
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 19383ca97f979d6932698d06eabd507b4a00954f
ms.sourcegitcommit: 36350889f318e1f7e0ac9506dc8df794d475bda6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-configure-wcf-services-published-with-the-biztalk-wcf-service-publishing-wizard"></a>如何用 BizTalk WCF 服務發佈精靈來設定已發佈 WCF 服務。
在使用 [BizTalk WCF 服務發佈精靈] 發佈 WCF 服務之後，您還必須適當設定這些服務。 本主題會說明如何設定已發佈的 WCF 服務。  
  
> [!NOTE]
>  您必須先建置 BizTalk 專案，然後再執行 [BizTalk WCF 服務發佈精靈] 發佈它們。 如需如何使用 BizTalk WCF 服務發佈精靈的詳細資訊，請參閱[如何為 WCF 服務使用 BizTalk WCF 服務發佈精靈發佈的協調流程](../core/publish-orchestrations-as-wcf-services--biztalk-wcf-service-publishing-wizard.md)和[如何使用 BizTalk WCF 服務發行精靈，以結構描述發佈為 WCF 服務](../core/publish-schemas-as-wcf-services--use-the-biztalk-wcf-service-publishing-wizard.md)。  
  
### <a name="to-configure-the-receive-locations-for-a-published-wcf-service"></a>若要為已發佈 WCF 服務設定接收位置  
  
1.  執行 [BizTalk WCF 服務發佈精靈] 以發佈 BizTalk 專案。  
  
2.  如果您未選取 **建立 BizTalk 接收位置** 選項如下圖所示，建立 WCF 服務時，建立新的接收埠和接收位置發佈的 WCF 服務，然後選取 WCF 配接器接收位置將使用的傳輸類型。 在選取時，您必須選取相同的 WCF 配接器 **WCF 服務類型** 如下圖所示的頁面。 如需有關如何建立接收位置的詳細資訊，請參閱[如何建立接收位置](../core/how-to-create-a-receive-location.md)。  
  
    > [!NOTE]
    >  [BizTalk WCF 服務發佈精靈] 會在已發佈 WCF 服務 (.svc 檔案) 之 Web 目錄的 \App_Data\Temp 資料夾中，建立繫結檔 BindingInfo.xml。 如果您選取 **建立 BizTalk 接收位置** 選項，精靈會使用繫結檔案來建立接收位置。 您可以在 [BizTalk Server 管理] 主控台中手動匯入此繫結檔來建立接收位置。 如需匯入繫結檔案的詳細資訊，請參閱[匯入繫結](../core/importing-bindings2.md)。  
  
     ![WCF 服務類型 頁面上](../core/media/959900fd-44c9-4f3a-8836-9786a2f5e707.gif "959900fd-44c9-4f3a-8836-9786a2f5e707")  
  
3.  如果有必要，請開啟 BizTalk Server 管理主控台，如下所示︰ 按一下 **啟動**, ，指向 **程式**, ，指向  **Microsoft BizTalk Server**, ，然後按一下  **BizTalk Server 管理**。  
  
4.  在主控台樹狀目錄中，依序展開 **BizTalk Server 管理**, ，展開 **BizTalk 群組**, ，展開 **應用程式**, ，依序展開 應用程式所產生的 WCF 服務應放置的位置，展開 **接收位置**, ，然後按兩下 WCF 服務的接收位置。  
  
5.  在 **接收位置屬性** 對話方塊中，按一下  **設定**。  
  
6.  如果接收位置是裝載 Wcf-basichttp 或 Wcf-wshttp 配接器，在 **傳輸屬性** 對話方塊中，按一下  **安全性** 索引標籤，然後再設定 索引標籤上的安全性內容。如果接收位置是裝載 Wcf-customisolated 配接器在**傳輸屬性**對話方塊中，按一下 **繫結**索引標籤，然後再設定 索引標籤上的 繫結資訊。  
  
     ![WCF 中的 [安全性] 索引標籤&#45;BasicHttp 配接器](../core/media/585ecdad-bdee-40c0-b2f1-7ace74d503e5.gif "585ecdad-bdee-40c0-b2f1-7ace74d503e5")  
  
    > [!NOTE]
    >  外掛式 WCF 配接器的傳輸用戶端認證類型屬性，必須符合裝載此接收位置之 Internet Information Services (IIS) 虛擬目錄的驗證配置。 例如，如果屬性設定為 **Windows**, ，您還必須啟用 **整合式 Windows 驗證** 裝載此虛擬目錄的接收位置。 同樣地，如果您將此屬性設為 **[無]**，您必須允許針對裝載此接收位置的虛擬目錄進行匿名存取。 如需如何設定 Wcf-basichttp 和 Wcf-wshttp 配接器的安全性內容的詳細資訊，請參閱[如何設定 Wcf-basichttp 接收位置](http://msdn.microsoft.com/library/43f18e5d-ba28-453c-b8ce-5bcdc6f27fdd)，和[如何設定 Wcf-wshttp 接收位置](../core/how-to-configure-a-wcf-wshttp-receive-location.md)。 如需如何設定繫結資訊的詳細資訊，請參閱[如何設定 Wcf-customisolated 接收位置](../core/how-to-configure-a-wcf-customisolated-receive-location.md)。  
  
7.  如果您未選取 **建立 BizTalk 接收位置** 選項建立 WCF 服務時，在 **傳輸屬性** 對話方塊中，按一下 [ **一般** ] 索引標籤。在**一般**索引標籤上，針對這個接收位置中的，輸入 URI**位址**文字方塊。 指定虛擬目錄和.svc 檔案名稱 BizTalk WCF 服務發佈精靈產生之前程序中 — 例如，/path/service.svc。  
  
    > [!NOTE]
    >  **位址** 屬性應該啟動以正斜線 （"/"），並以".svc"結束。 **位址**屬性必須包含通訊協定配置、 電腦名稱或連接埠號碼例如http://host:port。 這個屬性只能使用虛擬目錄路徑。 WCF 服務標記檔案必須具有 .svc 副檔名。  
  
     ![WCF 中的 [一般] 索引標籤&#45;BasicHttp 配接器](../core/media/1126fa6a-e3e9-44ad-aeb0-90c78226aeeb.gif "1126fa6a-e3e9-44ad-aeb0-90c78226aeeb")  
  
8.  如果您選取 **傳輸** 或 **TransportWithMessageCredential** 中 **安全性模式** 下拉式清單上的 **安全性**  索引標籤為 Wcf-basichttp 和 Wcf-wshttp 配接器，您必須設定設定安全通訊端層 (SSL) 在 IIS 中。 如果您設定 **傳輸** 或 **TransportWithMessageCredential** Wcf-customisolated 配接器的繫結資訊中的安全性模式，您也必須設定 IIS 中的 SSL。  
  
9. 如果接收位置是裝載 Wcf-basichttp 或 Wcf-wshttp 配接器，在 **傳輸屬性**  對話方塊中，設定 **一般**, ，**繫結**, ，和 **訊息** 視索引標籤。 如果接收位置是裝載 Wcf-customisolated 配接器，設定 **一般**, ，**行為**, ，**其他**, ，和 **訊息** 用於您目的的索引標籤。 Wcf-customisolated 配接器，您可以匯入 **位址 (URI)** 和 **端點身分識別** 屬性 **一般**  索引標籤上的繫結資訊 **繫結** 索引標籤，然後行為會在 **行為**  索引標籤，此接收位置從組態檔。  
  
10. 使用 [BizTalk Server 管理] 主控台來啟用已發佈 WCF 服務的接收位置。 如需如何啟用接收位置的詳細資訊，請參閱[如何啟用接收位置](../core/how-to-enable-a-receive-location.md)。  
  
    > [!NOTE]
    >  接收位置在建立時是停用狀態。 因此在用 [BizTalk Server WCF 服務精靈] 建立接收位置之後，您必須啟用這些接收位置。  
  
11. 使用 [IIS 管理] 主控台，設定 IIS 應用程式集區來裝載已發佈 WCF 服務的接收位置。 如需如何設定外掛式 WCF 配接器的應用程式集區的詳細資訊，請參閱[外掛式 WCF 接收配接器設定的 IIS](../core/configuring-iis-for-the-isolated-wcf-receive-adapters.md)。  
  
12. 開啟命令提示字元，請移至 BizTalk Server WCF 服務發佈精靈建立 WCF 服務中 %SystemDrive%\InetPub 資料夾\\, ，然後開啟 Web.config 檔案，使用 [記事本]。  
  
13. 在記事本中，加入下列一行**\<system.web\>**項目：  
  
    ```  
    <trust level="Full" originUrl="" />  
    ```  
  
    > [!NOTE]
    >  這項設定是選擇性的，而且它會將受限於作業系統安全性之任何資源的存取權授與主控已發佈之 WCF 服務的 ASP.NET 應用程式。 當您在同一部電腦上安裝和執行 Windows SharePoint Services 以及已發佈的 WCF 服務時，這就是 WCF 所需的信任層級。  
  
14. 在 Internet Explorer 中 **位址** 方塊中，輸入 WCF 服務使用格式 http:// URL*主機 [: 連接埠]*/*apppath*/*wcfservicename.svc* 來測試已發佈的 WCF 服務。 下表將描述這些參數。  
  
    |參數|Value|  
    |---------------|-----------|  
    |*主應用程式 [: 連接埠]*|您已部署 WCF 服務之電腦的名稱。 冒號和連接埠編號可以接在這個伺服器名稱後面。|  
    |*apppath*|虛擬目錄的名稱和 Web 應用程式路徑。|  
    |*wcfservicename.svc*|WCF 服務 .svc 檔案的名稱。|  
  
15. 為了避免不小心洩露可能含有機密的服務中繼資料，我們建議您透過執行下列工作，在實際執行環境中停用這種行為：  
  
    1.  在 記事本 開啟 BizTalk Server WCF 服務發佈精靈建立 WCF 服務中 %SystemDrive%\InetPub 資料夾中的 Web.config\\。  
  
    2.  在 [記事本]，設定**httpGetEnabled**屬性**\<serviceMetadata\>**為 false，如下列的行項目：  
  
        ```  
        <serviceMetadata httpGetEnabled="false" httpsGetEnabled="false" />  
        ```  
  
## <a name="see-also"></a>另請參閱  
 [設定 Wcf-basichttp 配接器](http://msdn.microsoft.com/library/5929a338-46e0-4fc4-8837-792d7f7ae0fe)   
 [設定 Wcf-wshttp 配接器](../core/configuring-the-wcf-wshttp-adapter.md)   
 [設定 Wcf-customisolated 配接器](../core/configuring-the-wcf-customisolated-adapter.md)   
 [如何在 Windows Server 2003 中設定 IIS 網站驗證](http://go.microsoft.com/fwlink/?LinkID=75699)