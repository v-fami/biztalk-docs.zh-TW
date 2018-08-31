---
title: 如何使用 BizTalk WCF 服務發佈精靈發佈服務中繼資料之 WCF 接收位置的內容為基礎的路由 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF Service Publishing Wizard, publishing metadata
- WCF services, metadata
ms.assetid: e900b0a0-db17-4db9-a639-54891e02d6d7
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: efcda402c231b990d7fefa239a8ff15798331184
ms.sourcegitcommit: 9b93ee2a019bef8d482626cf5525a6b95509b135
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2018
ms.locfileid: "42709884"
---
# <a name="how-to-use-the-biztalk-wcf-service-publishing-wizard-to-publish-service-metadata-for-a-wcf-receive-location-for-content-based-routing"></a>如何使用 BizTalk WCF 服務發佈精靈來發佈根據訊息內容決定路由之 WCF 接收位置的服務中繼資料
您可以使用 [BizTalk WCF 服務發佈精靈] 來建立 WCF 服務，以便發佈根據訊息內容決定路由之現有 WCF 接收位置的服務中繼資料。  

> [!NOTE]
>  您必須先建置 BizTalk 專案，然後再執行 BizTalk WCF 服務發佈精靈。 BizTalk 專案必須包含結構描述，才能發佈為 WCF 服務。 發佈 WCF 配接器的服務中繼資料之前，您也必須使用 BizTalk Server 管理主控台或 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 隨附的 BTSTask 命令列工具來建立 WCF 接收位置。 如需有關如何建立 WCF 接收位置，請參閱中的每個 WCF 配接器的適當主題[WCF 配接器](../core/wcf-adapters.md)。  

### <a name="to-publish-service-metadata-for-an-existing-wcf-receive-location-for-content-based-routing"></a>若要發佈根據訊息內容決定路由之現有 WCF 接收位置的服務中繼資料  

1. 按一下 **開始**，指向**所有程式**，指向**[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]**，然後按一下**BizTalk WCF 服務發佈精靈**。  

   > [!NOTE]
   >  若要建立並發佈 BizTalk 協調流程和結構描述的 WCF 服務中繼資料，您可以使用 BizTalk WCF 服務發佈精靈。 若要以 SOAP 配接器將協調流程和結構描述發佈成 Web 服務，您可以使用 BizTalk Web 服務發佈精靈。  

2. 在 [**歡迎使用 BizTalk WCF 服務發佈精靈**頁面上，按一下**下一步]**。  

3. 在  **WCF 服務類型**頁面上，選取**中繼資料唯一端點 (MEX)** 來發佈 WCF 服務，以提供 WCF 服務中繼資料的選項接收下一個步驟中，您將選取的位置。  

    ![WCF 服務類型 頁面](../core/media/794a85b5-6454-4cce-8c15-382b5583b0f2.gif "794a85b5-6454-4cce-8c15-382b5583b0f2")  

4. 在上**WCF 服務類型**頁面上，於**發行中繼資料的接收位置**下拉式清單中，選取之 WCF 接收位置來發佈服務中繼資料，然後按一下 **下一步**.  

5. 在 [**建立 WCF 服務**頁面上，選取**結構描述發佈為 WCF 服務**，然後按一下**下一步]**。  

    ![建立 WCF 服務頁面](../core/media/717db27a-2843-4950-899d-0946460f5c1f.gif "717db27a-2843-4950-899d-0946460f5c1f")  

6. 在  **WCF 服務**頁面上，定義要發佈服務中繼資料的 WCF 服務合約。 使用中的樹狀結構**Web 服務描述**對話方塊，即可新增、 移除、 重新命名及編輯 Web 服務描述節點，針對所要發佈的 WCF 服務。 **資訊**對話方塊提供所選節點的相關資訊，並顯示目前的節點或任何子節點中的任何錯誤：  

   -   樹狀結構的根節點 (Web 服務描述) 會描述要發佈的 WCF 服務合約。 虛擬目錄名稱會使用根節點做為預設名稱。 您可以修改 Web 服務描述名稱來選取發佈 WCF 服務**重新命名 web 服務描述**。  

        ![WCF 服務頁面](../core/media/35131a58-dae7-45fe-ac6a-928c8570f27d.gif "35131a58-dae7-45fe-ac6a-928c8570f27d")  

   -   Web 方法節點， **Operation1**，預設服務節點的**Service1**，預設會在所示**Web 服務描述**可用於對話方塊要求-回應接收位置。 如果您選取單向 WCF 接收位置，此服務合約，以滑鼠右鍵按一下 預設的 Web 方法節點，按一下 **刪除 web 方法**，然後建立一個單向 Web 方法，如下所示： 以滑鼠右鍵按一下 預設 服務節點中，點若要**新增 web 方法**，然後按一下**單向**。  

   -   若要加入新的 WCF 服務，以滑鼠右鍵按一下 Web 服務描述名稱，然後**加入 web 服務**。 這樣便會建立新的 WCF 服務，而不需要進行任何 WCF 作業。 修改 WCF 服務的名稱，以滑鼠右鍵按一下該 WCF 服務節點，再按**重新命名 web 服務**，然後按 ENTER 即可接受新的名稱。  

   -   若要加入新的 WCF 作業，以滑鼠右鍵按一下該 WCF 服務節點，指向**新增 Web 方法**，然後按一下**單向**（針對要求 WCF 作業） 或**要求-回應**(如要求-回應 WCF 作業）。  

   -   若要設定的要求和回應結構描述型別，以滑鼠右鍵按一下**要求**或是**回應**節點，然後再按一下**選取結構描述類型**。 在 **要求訊息類型**方塊中，輸入包含中的文件結構描述的組件的名稱**BizTalk 組件檔案**文字方塊中或按一下 **瀏覽**搜尋組件。 **可用的結構描述型別**清單檢視會顯示每個根結構描述項目。 選取要新增為要求或回應結構描述類型的根節點。  

       > [!NOTE]
       >  如果您安裝到全域組件快取 (GAC) 中的 BizTalk 組件檔案，請確定 GAC 中的組件，已更新的組件中選取**要求訊息類型** 對話方塊。 如果 GAC 中的組件具有相同的完整格式名稱，[BizTalk WCF 服務發佈精靈] 就會使用 GAC 中的組件檔案，而非您所選取的檔案。  

        ![要求訊息類型頁面](../core/media/6bb4cc17-b108-4692-a5ca-548c7ef46045.gif "6bb4cc17-b108-4692-a5ca-548c7ef46045")  

   -   您可以重新命名**要求**並**回應**節點，而不會影響產生的程式碼。 在定義結構描述之後，您便可以重新命名部分項目，這樣做會修改 WCF 作業參數名稱。 您可以透過檢視 WCF 服務所要發佈的服務中繼資料，查看這些變更。  

   > [!NOTE]
   >  重新命名任何 Web 服務描述節點時，不可以使用空格。  

7. 按一下 [**下一步]** 來繼續執行精靈。  

8. 在上**WCF 服務屬性**頁面上，於**的 WCF 服務的 Targetnamespace**文字方塊中輸入 WCF 服務的目標命名空間，然後按一下**下一步**。  

    ![WCF 服務屬性頁](../core/media/07518c78-bcae-4274-bb14-aeef107ee4c6.gif "07518c78-bcae-4274-bb14-aeef107ee4c6")  

9. 在  **WCF 服務位置**頁面上，於**位置**文字方塊中，輸入產生 WCF 服務位置的 Web 目錄名稱。 您可以接受預設位置 (`http://localhost/<Web service description name>`)，輸入中的 WCF 服務的位置**位置**文字方塊中或按一下 **瀏覽**並選取 Web 目錄。 接著，選取下列任何一個選項：  

   - **覆寫現有的專案。** 此選項只有在 Web 目錄已存在時才能使用。 只有當您選取了這個選項時，才能夠發佈至相同的位置。 否則，您必須輸入不同的專案位置。  

   - **允許匿名存取 WCF 服務。** 這個選項會新增已建立之虛擬目錄的匿名存取。 根據預設，虛擬目錄會從其父虛擬目錄或網站 (如果它是最上層虛擬目錄的話) 繼承存取權限。  

     當您完成這個頁面上時，按一下**下一步**。  

     ![WCF 服務位置頁面](../core/media/76285470-1520-4d77-a5b6-c58cbe8fc575.gif "76285470-1520-4d77-a5b6-c58cbe8fc575")  

     > [!NOTE]
     >  專案位置可以存在不同的伺服器上。 若要將 WCF 服務發佈到另一部伺服器中，輸入 專案名稱，做為`http://<servername>/<WCF service location>`。  

     > [!NOTE]
     >  專案位置可以存在非預設的網站上。 發佈至非預設的網站時，請在 URL 中加入網站的連接埠編號。 例如， `http://<servername>:8080/<WCF service location>` 。  

     > [!NOTE]
     >  精靈在 Web 應用程式之 \App_Data\Temp 資料夾中建立的 BindingInfo.xml 檔案會使用管線的預設值。 接收管線的預設值是**Microsoft.BizTalk.DefaultPipelines.XMLReceive**管線，而且預設值的傳送管線是**Microsoft.BizTalk.DefaultPipelines.PassThruTransmit**管線。  

10. 在  **WCF 服務摘要**頁面上，檢閱您的 WCF 服務的設定。  

11. 按一下 **建立**以建立 WCF 服務。  

12. 按一下 **完成**完成 BizTalk WCF 服務發佈精靈。  

### <a name="to-configure-the-web-application-for-publishing-service-metadata"></a>若要設定發佈服務中繼資料的 Web 應用程式  

1. 針對 BizTalk WCF 服務發佈精靈所建立的 Web 應用程式啟用 ASP.NET。 如需詳細資訊，請參閱 <<c0> [ 啟用 Web 服務](../core/enabling-web-services.md)。  

   > [!NOTE]
   >  如果您正使用其他版本的 Windows 作業系統，就必須將應用程式集區的識別帳戶新增至 BizTalk Server 系統管理員群組。 將適當的帳戶新增至 BizTalk Server 系統管理員群組之後，您必須重新啟動 IIS 服務，才能讓設定生效。  

2. 開啟命令提示字元，請移至 BizTalk WCF 服務發佈精靈建立 WCF 服務中 %SystemDrive%\InetPub 資料夾\\，然後開啟 Web.config 檔案，使用 記事本。  

3. 在記事本中，加入下的面這一行內**\<system.web\>** 項目：  

   ```  
   <trust level="Full" originUrl="" />  
   ```  

   > [!NOTE]
   >  這項設定是選擇性的，而且它會將受限於作業系統安全性之任何資源的存取權授與主控已發佈之 WCF 服務的 ASP.NET 應用程式。 當您在同一部電腦上安裝和執行 Windows SharePoint Services 以及已發佈的 WCF 服務時，這就是 WCF 所需的信任層級。  

4. 在 Internet Explorer 中**地址**方塊中，輸入 WCF 服務使用格式 http:// URL<em>主控件 [: 連接埠]</em>/*apppath* /*wcfservicename.svc*來測試已發佈的 WCF 服務。 下表將描述這些參數。  


   |      參數       |                                                            值                                                            |
   |----------------------|-----------------------------------------------------------------------------------------------------------------------------|
   |    *主控件 [: 連接埠]*     | 您已部署 WCF 服務之電腦的名稱。 冒號和連接埠編號可以接在這個伺服器名稱後面。 |
   |      *apppath*       |                              虛擬目錄的名稱和 Web 應用程式路徑。                               |
   | *wcfservicename.svc* |                                           WCF 服務 .svc 檔案的名稱。                                            |


5. 為了避免不小心洩露可能含有機密的服務中繼資料，我們建議您透過執行下列工作，在實際執行環境中停用這種行為：  

   1.  在 記事本 開啟 BizTalk WCF 服務發佈精靈建立 WCF 服務中 %SystemDrive%\InetPub 的資料夾中的 Web.config\\。  

   2.  在記事本中，設定**httpGetEnabled**屬性中**\<serviceMetadata\>** 為 false，如下列這一行的項目：  

       ```  
       <serviceMetadata httpGetEnabled="false" httpsGetEnabled="false" />  
       ```  

## <a name="see-also"></a>另請參閱  
 [如何使用 BizTalk WCF 服務發佈精靈發佈為 WCF 服務的結構描述](../core/publish-schemas-as-wcf-services--use-the-biztalk-wcf-service-publishing-wizard.md)   
 [逐步解說：使用 WCF-NetMsmq 配接器發佈 WCF 服務](../core/walkthrough-publishing-wcf-services-with-the-wcf-netmsmq-adapter.md)