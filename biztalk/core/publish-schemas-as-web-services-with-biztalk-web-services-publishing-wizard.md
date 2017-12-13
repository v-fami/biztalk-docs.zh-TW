---
title: "如何使用 BizTalk Web 服務發佈精靈將結構描述發佈為 Web 服務 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BizTalk Web Services Publishing Wizard, publishing
- BizTalk Web Services Publishing Wizard, schemas
ms.assetid: b22de720-1416-486a-988f-e52527ad9ab1
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ba7f93eae8866212546f5daa3b9ed1a5b653c983
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-use-the-biztalk-web-services-publishing-wizard-to-publish-schemas-as-a-web-service"></a>如何使用 BizTalk Web 服務發佈精靈將結構描述發佈為 Web 服務
您可以使用「BizTalk Web 服務發佈精靈」將結構描述發佈為 Web 服務。  
  
### <a name="to-publish-schemas-as-a-web-service"></a>若要將結構描述發佈為 Web 服務  
  
1.  按一下**啟動**，指向 **所有程式**，指向  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Web 服務發佈精靈**。  
  
    > [!IMPORTANT]
    >  您必須先建置 BizTalk 專案，才可以執行「BizTalk Web 服務發佈精靈」。  
  
2.  在**歡迎**頁面上，按一下**下一步**。  
  
3.  在**建立 Web 服務**頁面上，選取**結構描述發佈為 web 服務**，然後按一下 **下一步**。  
  
4.  在**Web 服務**頁面上，定義要發佈的 Web 服務。 使用中的樹狀結構**Web 服務描述**來新增、 移除、 重新命名，並編輯 Web 服務描述節點 對話方塊。 **資訊**對話方塊提供所選節點的相關資訊，並顯示目前的節點或任何子節點中的任何錯誤：  
  
    -   樹狀目錄的根節點 (Web 服務描述) 會描述 Web 服務專案名稱。 虛擬目錄名稱會使用根節點做為預設名稱。 您可以修改所選取的 Web 服務描述**重新命名 web 服務描述**。  
  
    -   若要加入新的 Web 服務，以滑鼠右鍵按一下**Web 服務描述**節點，然後再按一下**加入 web 服務**。 這樣便會建立新的 Web 服務，但不含任何 Web 方法。 若要修改 Web 服務的名稱，以滑鼠右鍵按一下 Web 服務節點，然後選取**重新命名 web 服務**，然後按 Enter 以接受新的名稱。  
  
    -   若要加入新的 Web 方法，以滑鼠右鍵按一下 Web 服務節點，指向**新增 Web 方法**，然後按一下 **單向**（針對要求 Web 方法） 或**要求-回應**(如要求-回應 Web 方法） 從捷徑功能表。  
  
    -   若要設定的要求和回應結構描述型別，以滑鼠右鍵按一下**要求**或**回應**節點，然後再按一下**選取結構描述類型**。 在**要求訊息類型**對話方塊方塊中，輸入包含中的文件結構描述的組件名稱**BizTalk 組件檔案**文字方塊中或按一下**瀏覽**搜尋組件。 **可用結構描述型別**清單檢視會顯示結構描述的每個根項目。 選取要新增為要求或回應結構描述類型的根節點。  
  
        > [!NOTE]
        >  如果您安裝 BizTalk 組件檔案至全域組件快取 (GAC) 中，請確定您會在選取的組件，已更新組件在 GAC 中的**要求訊息類型** 對話方塊。 如果 GAC 具有相同的完整格式名稱，[BizTalk Web 服務發佈精靈] 就會使用 GAC 中的組件檔案，而非您所選取的檔案。  
  
    -   您可以重新命名**要求**和**回應**節點，而不會影響產生的程式碼。 在定義結構描述之後，您可以重新命名部分項目，這樣做則會修改 Web 方法參數名稱。 您可以檢視所產生的 Web 服務程式碼，即可看見這些變更。  
  
    > [!NOTE]
    >  重新命名任何 Web 服務描述節點時，不可以使用空格。  
  
5.  按一下**下一步**繼續使用精靈。  
  
6.  在**Web 服務屬性**頁面上，於**web 服務目標命名空間**對話方塊中，輸入 Web 服務的目標命名空間，然後選取適當的方塊，以指定精靈應該如何處理 SOAP 標頭和單一登入支援 Web 服務。 如果您想要進一步自訂的 Web 服務實作中，按一下**進階** 按鈕。 如此將顯示更多可用的選項：  
  
    |選項|值|Description|  
    |------------|-----------|-----------------|  
    |SOAP 參數樣式|預設值|這個選項會指定參數在 SOAP 訊息中格式化的方式。 如需詳細資訊，請參閱 < SoapParameterStyle 列舉 >，網址[http://go.microsoft.com/fwlink/?LinkId=62259](http://go.microsoft.com/fwlink/?LinkId=62259)。|  
    |SOAP 參數樣式|Bare|這個選項會指定參數在 SOAP 訊息中格式化的方式。 如需詳細資訊，請參閱 < SoapParameterStyle 列舉 >，網址[http://go.microsoft.com/fwlink/?LinkId=62259](http://go.microsoft.com/fwlink/?LinkId=62259)。|  
    |SOAP 參數樣式|Wrapped|這個選項會指定參數在 SOAP 訊息中格式化的方式。 如需詳細資訊，請參閱 < SoapParameterStyle 列舉 >，網址[http://go.microsoft.com/fwlink/?LinkId=62259](http://go.microsoft.com/fwlink/?LinkId=62259)。|  
    |相容主張|無|這個選項會指定繫結主張所遵詢的「Web 服務互通性」(WSI) 規格。 如需詳細資訊，請參閱 < WebServiceBindingAttribute.ConformsTo 屬性[http://go.microsoft.com/fwlink/?LinkId=193064](http://go.microsoft.com/fwlink/?LinkId=193064)。|  
    |相容主張|WS-I 基本設定檔 1.1|這個選項會指定繫結主張所遵詢的「Web 服務互通性」(WSI) 規格。 如需詳細資訊，請參閱 < WebServiceBindingAttribute.ConformsTo 屬性[http://go.microsoft.com/fwlink/?LinkId=193064](http://go.microsoft.com/fwlink/?LinkId=193064)。|  
    |強制要求回應|[預設]|這個選項會指定單向 BizTalk 作業是否應該公開為要求-回應的 Web 方法。 預設是不強制單向旗標。|  
  
    > [!NOTE]
    >  執行這個精靈執行個體時，所有選取的 SOAP 標頭選項都會全域套用至建立的所有 Web 服務和 Web 方法。  
  
7.  在**Web 服務屬性**頁面上，按一下**下一步**。  
  
8.  如果您選取**新增其他 SOAP 標頭**、**要求 SOAP 標頭**和**回應 SOAP 標頭**會出現一個頁面。 您可以加入和移除要求和回應 SOAP 標頭，使用**新增**和**移除**下列對話方塊中的按鈕：  
  
    -   若要新增 SOAP 標頭，請按一下**新增**。 在**BizTalk 組件名稱 (\*.dll)**文字方塊中，輸入組件名稱，或瀏覽包含 SOAP 標頭結構描述中的組件**BizTalk 組件檔案**文字方塊。 **可用結構描述型別**清單檢視會顯示結構描述的每個根項目。 選取要新增為要求或回應 SOAP 標頭的根節點。 若要選取多個項目，按住 CTRL 鍵並按一下**確定**。  
  
    -   若要從清單中移除 SOAP 標頭，從已加入 SOAP 標頭的清單中選取，然後按一下 **移除**。  
  
    -   按一下**下一步**在每個 SOAP 標頭頁面繼續執行精靈。  
  
    > [!NOTE]
    >  目標命名空間和根項目名稱會定義 SOAP 標頭。  
  
    > [!NOTE]
    >  如果目標命名空間/根項目名稱的相同組合新增為要求和回應 SOAP 標頭，它將不會被視為輸入/輸出標頭。 您必須在協調流程內部，手動將內送標頭複製到外寄標頭。  
  
    > [!NOTE]
    >  目標命名空間/根項目名稱的相同組合只能新增為要求 SOAP 標頭和回應 SOAP 標頭各一次。  
  
9. 在**Web 服務專案**頁面上，於**專案位置**文字中，輸入專案位置。 您可以接受預設位置 (http://localhost/ <*project_name*>)，輸入專案位置，或按一下**瀏覽**，並選取 Web 目錄。 接著，選取下列任何一個選項：  
  
    -   **覆寫現有的專案。** 這個選項只有在專案位置已經存在時才能使用。 您只能在這個選項已選取時，才能夠發佈至相同的位置。 否則，您必須輸入不同的專案位置。  
  
    -   **允許匿名存取 web 服務。** 這個選項會新增已建立之虛擬目錄的匿名存取。 根據預設，虛擬目錄會從其父虛擬目錄或網站 (如果它是最上層虛擬目錄的話) 繼承存取權限。  
  
    -   **建立 BizTalk 接收位置。** 這個選項會自動建立對應於每個產生之 .asmx 檔案的 SOAP 配接器接收埠和位置。 如果另一個接收位置已經存在，則不會取代該接收位置。 SOAP 配接器會使用格式來解析的接收位置 」 /\<*虛擬目錄名稱*\>/\<*namespace_typename_portname 協調流程* \>.asmx"。 選取這個選項之後，再選擇將產生接收埠和位置的應用程式。  
  
        > [!NOTE]
        >  專案位置可以存在不同的伺服器上。 若要發行到不同的伺服器的 Web 服務，輸入專案名稱，做為 **http://&lt*servername*>/<*project_name*> * *。  
  
        > [!NOTE]
        >  專案位置可以存在非預設的網站上。 發行到非預設的網站時，請在 URL 中加入網站的通訊埠編號： http://localhost:8080/< / <*project_name*>。  
  
        > [!NOTE]
        >  當您使用精靈建立接收位置時，精靈會使用許多預設值來建立接收位置。 接收和傳送管線的預設值為**Microsoft.BizTalk.DefaultPipelines.PassThruReceive**和**Microsoft.BizTalk.DefaultPipelines.PassThruTransmit**。 如果透過已發佈的 Web 服務收到的訊息需要任何特殊管線處理 （例如，驗證、 相互關聯或輸入/輸出對應），則您應該設定傳送和接收管線**Microsoft.BizTalk.DefaultPipelines.XMLReceive**， **Microsoft.BizTalk.DefaultPipelines.XMLSend**，或自訂管線。  
  
10. 按一下**下一步**檢閱您的 ASP.NET Web 服務專案設定。  
  
11. 按一下**建立**建立 ASP.NET Web 服務。  
  
12. 按一下**完成**完成 BizTalk Web 服務發佈精靈。  
  
## <a name="see-also"></a>請參閱  
 [將結構描述發佈為 Web 服務](../core/publishing-schemas-as-a-web-service.md)