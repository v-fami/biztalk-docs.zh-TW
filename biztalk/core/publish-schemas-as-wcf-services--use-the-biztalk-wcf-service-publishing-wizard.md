---
title: 如何使用 BizTalk WCF 服務發佈精靈發佈為 WCF 服務的結構描述 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- schemas, WCF services
- tools, WCF Service Publishing Wizard
- publishing, schemas [WCF services]
- WCF services, schemas
- WCF Service Publishing Wizard
ms.assetid: 3b770fd5-5b7b-493f-9016-d7d58854c5ff
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cf10236b5db5b1af1a0a115e57a71ad2ae415eda
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37022164"
---
# <a name="how-to-use-the-biztalk-wcf-service-publishing-wizard-to-publish-schemas-as-wcf-services"></a>如何使用 BizTalk WCF 服務發佈精靈將結構描述發佈為 WCF 服務
您會使用 [BizTalk WCF 服務發佈精靈] 將結構描述發佈為 WCF 服務。  
  
> [!NOTE]
>  您必須先建置 BizTalk 專案，然後再執行 BizTalk WCF 服務發佈精靈。 BizTalk 專案必須包含結構描述，才能發佈為 WCF 服務。  
  
### <a name="to-publish-schemas-as-wcf-servicees"></a>將結構描述發佈為 WCF 服務  
  
1. 按一下 **開始**，指向**所有程式**，指向[!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk WCF 服務發佈精靈**。  
  
   > [!NOTE]
   >  您可以使用 [BizTalk WCF 服務發佈精靈] 來建立 BizTalk 協調流程和結構描述，並使用 WCF 配接器將它們發佈為 WCF 服務。 若要以 SOAP 配接器將協調流程和結構描述發佈成 Web 服務，您可以使用 BizTalk Web 服務發佈精靈。  
  
2. 在 [**歡迎使用 BizTalk WCF 服務發佈精靈**頁面上，按一下**下一步]**。  
  
3. 在  **WCF 服務類型**頁面上，選取**服務端點**BizTalk 組件中選取 BizTalk 協調流程上發佈的 WCF 服務的選項。  
  
    ![WCF 服務類型 頁面](../core/media/959900fd-44c9-4f3a-8836-9786a2f5e707.gif "959900fd-44c9-4f3a-8836-9786a2f5e707")  
  
4. 在  **WCF 服務類型**頁面上，選取或清除**啟用中繼資料端點**核取方塊，以指出外掛式的 WCF 接收位置裝載網際網路資訊服務 (IIS) 是否會將發佈使用 HTTP/GET 要求進行擷取服務中繼資料。  
  
    選取此核取方塊時，精靈會產生 Web.config 檔案所在**httpGetEnabled**屬性**\<serviceMetadata\>** 元素設定為 **，則為 true**。 您可以在開發環境中使用中繼資料匯入工具 (例如 SvcUtil.exe) 產生呼叫此服務所需的用戶端程式碼。 中繼資料發行的位址是端點位址加上 **？ wsdl**查詢字串。  
  
   > [!NOTE]
   >  為避免不慎洩露機密的服務中繼資料，建議您在實際執行環境中停用此行為。 這可透過將 httpgetenabled 設為 False 或刪除 MEX 虛擬目錄來完成。  
  
5. 在  **WCF 服務類型**頁面上，於**配接器名稱 （傳輸類型）** 下拉式清單中，選取用來發佈 WCF 服務的外掛式的 WCF 配接器。 您可以選取下列任何一個配接器：  
  
   -   **Wcf-basichttp。** WCF-BasicHttp 配接器可以與 WS-I 基本設定檔 1.1 相符的 Web 服務 (例如以 ASMX 為基礎的服務) 通訊。  
  
   -   **Wcf-wshttp。** WCF-WSHttp 配接器可以透過 HTTP 和 HTTPS 上的 WS-* 標準，與服務進行通訊。  
  
   -   **Wcf-customisolated。** WCF-CustomIsolated 配接器可以在 HTTP 傳輸上啟用 Windows Communication Foundation (WCF) 擴充性功能。  
  
6. 在  **WCF 服務類型**頁面上，選取**下列應用程式中的建立 BizTalk 接收位置**核取方塊，來建立接收埠和相對應的每個產生的.svc 檔的位置您在選取的 WCF 配接器**配接器名稱**下拉式清單。 如果接收位置已經存在，則不會取代該接收位置。 選取此選項之後，選擇 [接收埠和位置會產生位置中的應用程式**BizTalk 應用程式名稱**下拉式清單中，然後再按一下**下一步]**。  
  
7. 在 [**建立 WCF 服務**頁面上，選取**結構描述發佈為 WCF 服務**，然後按一下**下一步]**。  
  
    ![建立 WCF 服務頁面](../core/media/717db27a-2843-4950-899d-0946460f5c1f.gif "717db27a-2843-4950-899d-0946460f5c1f")  
  
8. 在  **WCF 服務**頁面上，定義要發佈的 WCF 服務。 使用中的樹狀結構**Web 服務描述**對話方塊，即可新增、 移除、 重新命名及編輯 Web 服務描述節點，針對所要發佈的 WCF 服務。 **資訊**對話方塊提供所選節點的相關資訊，並顯示目前節點或子節點中的任何錯誤：  
  
   -   樹狀結構的根節點 (Web 服務描述) 會描述要發佈的 WCF 服務。 虛擬目錄名稱會使用根節點做為預設名稱。 您可以修改 Web 服務描述名稱來選取發佈 WCF 服務**重新命名 web 服務描述**。  
  
        ![WCF 服務頁面](../core/media/35131a58-dae7-45fe-ac6a-928c8570f27d.gif "35131a58-dae7-45fe-ac6a-928c8570f27d")  
  
   -   Web 方法節點， **Operation1**，預設服務節點的**Service1**，預設會在所示**Web 服務描述**可用於對話方塊要求-回應接收位置。 如果您打算發佈單向的 WCF 接收位置，此服務的描述，以滑鼠右鍵按一下 預設的 Web 方法節點，按一下**刪除 web 方法**，然後建立一個單向 Web 方法，如下所示： 以滑鼠右鍵按一下 預設的服務節點，指向**新增 web 方法**，然後按一下**單向**。  
  
   -   若要加入新的 WCF 服務，以滑鼠右鍵按一下 Web 服務描述名稱，然後**加入 web 服務**。 這樣便會建立新的 WCF 服務，而不需要進行任何 WCF 作業。 修改 WCF 服務的名稱，以滑鼠右鍵按一下該 WCF 服務節點，再按**重新命名 web 服務**，然後按 ENTER 即可接受新的名稱。  
  
   -   若要加入新的 WCF 作業，以滑鼠右鍵按一下該 WCF 服務節點，指向**新增 Web 方法**，然後按一下**單向**（針對要求 WCF 作業） 或**要求-回應**(如要求-回應 WCF 作業）。  
  
   -   若要設定的要求和回應結構描述型別，以滑鼠右鍵按一下**要求**或是**回應**節點，然後再按一下**選取結構描述類型**。 在 **要求訊息類型**方塊中，輸入包含中的文件結構描述的組件的名稱**BizTalk 組件檔案**文字方塊中或按一下 **瀏覽**搜尋組件。 **可用的結構描述型別**清單檢視會顯示每個根結構描述項目。 選取要新增為要求或回應結構描述類型的根節點。  
  
       > [!NOTE]
       >  如果您安裝到全域組件快取 (GAC) 中的 BizTalk 組件檔案，請確定 GAC 中的組件，已更新的組件中選取**要求訊息類型** 對話方塊。 如果 GAC 中的組件具有相同的完整格式名稱，[BizTalk WCF 服務發佈精靈] 就會使用 GAC 中的組件檔案，而非您所選取的檔案。  
  
        ![要求訊息類型頁面](../core/media/6bb4cc17-b108-4692-a5ca-548c7ef46045.gif "6bb4cc17-b108-4692-a5ca-548c7ef46045")  
  
   -   您可以重新命名**要求**並**回應**節點，而不會影響產生的程式碼。 在定義結構描述之後，您便可以重新命名部分項目，這樣做會修改 WCF 作業參數名稱。 您可以透過檢視 WCF 服務所要發佈的服務中繼資料，查看這些變更。  
  
       > [!NOTE]
       >  重新命名任何 Web 服務描述節點時，不可以使用空格。  
  
9. 按一下 [**下一步]** 來繼續執行精靈。  
  
10. 在上**WCF 服務屬性**頁面上，於**的 WCF 服務的 Targetnamespace**文字方塊中輸入 WCF 服務的目標命名空間，然後按一下**下一步**。  
  
     ![WCF 服務屬性頁](../core/media/07518c78-bcae-4274-bb14-aeef107ee4c6.gif "07518c78-bcae-4274-bb14-aeef107ee4c6")  
  
11. 在  **WCF 服務位置**頁面上，於**位置**文字方塊中，輸入產生 WCF 服務位置的 Web 目錄名稱。 您可以接受預設位置 (http://localhost/<*Web 服務描述名稱*>)，輸入中的 WCF 服務位置**位置**文字方塊中或按一下**瀏覽**並選取 Web 目錄。 接著，選取下列任何一個選項：  
  
    - **覆寫現有的專案。** 此選項只有在 Web 目錄已存在時才能使用。 只有當您選取了這個選項時，才能夠發佈至相同的位置。 否則，您必須輸入不同的專案位置。  
  
    - **允許匿名存取 WCF 服務。** 這個選項會新增已建立之虛擬目錄的匿名存取。 根據預設，虛擬目錄會從其父虛擬目錄或網站 (如果它是最上層虛擬目錄的話) 繼承存取權限。  
  
      當您完成這個頁面上時，按一下**下一步**。  
  
      ![WCF 服務位置頁面](../core/media/76285470-1520-4d77-a5b6-c58cbe8fc575.gif "76285470-1520-4d77-a5b6-c58cbe8fc575")  
  
    > [!NOTE]
    >  專案位置可以存在不同的伺服器上。 若要將 WCF 服務發佈到另一部伺服器中，輸入專案名稱做為 http://&lt*servername*>/<*WCF 服務位置*>。  
  
    > [!NOTE]
    >  專案位置可以存在非預設的網站上。 發佈至非預設的網站時，請在 URL 中加入網站的連接埠編號。 例如，http: http://&lt*servername*>: 8080 / <*WCF 服務位置*>。  
  
    > [!NOTE]
    >  在使用精靈建立接收位置時，精靈會使用預設值來建立接收位置。 接收管線的預設值是**Microsoft.BizTalk.DefaultPipelines.PassThruReceive**管線。 如果透過已發佈的 WCF 服務收到的訊息需要任何特殊管線處理 （例如驗證、 相互關聯/屬性升級或輸入/輸出對應），則您應該設定接收管線**Microsoft.BizTalk.DefaultPipelines.XMLReceive**，或使用 BizTalk 管理主控台自訂管線。  
  
12. 在  **WCF 服務摘要**頁面上，檢閱您的 WCF 服務的設定。  
  
13. 按一下 **建立**以建立 WCF 服務。  
  
14. 按一下 **完成**完成 BizTalk WCF 服務發佈精靈。  
  
15. 在使用 [BizTalk WCF 服務發佈精靈] 發佈 WCF 服務之後，您還必須適當設定這些服務。 如需有關如何設定外掛式的 WCF 接收配接器，請參閱[如何使用 BizTalk WCF 服務發佈精靈設定 WCF 服務發佈](../core/configure-wcf-services-published-with-the-biztalk-wcf-service-publishing-wizard.md)。  
  
## <a name="see-also"></a>另請參閱  
 [如何設定使用 BizTalk WCF 服務發佈精靈發佈的 WCF 服務](../core/configure-wcf-services-published-with-the-biztalk-wcf-service-publishing-wizard.md)   
 [逐步解說： 發行使用 Wcf-basichttp 配接器的 WCF 服務](../core/walkthrough-publishing-wcf-services-with-the-wcf-basichttp-adapter.md)   
 [如何使用 BizTalk WCF 服務發佈精靈協調流程發佈為 WCF 服務](../core/publish-orchestrations-as-wcf-services--biztalk-wcf-service-publishing-wizard.md)