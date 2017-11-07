---
title: "建立 TIBCO Rendezvous 配接器傳送成品 |Microsoft 文件"
description: "建立傳送埠，請設定將訊息從 BizTalk 傳送至 TIBCO Rendezvous 傳輸屬性"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad996c4f-e6ed-4582-a768-0cb1ad25b1d8
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ed6d03885423582c2657c9cb624c63f26ce1c6f3
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="create-tibco-rendezvous-send-handlers"></a>建立 TIBCO Rendezvous 傳送處理常式
本節說明如何建立結構描述，以在 BizTalk Server 協調流程中使用 TIBCO Rendezvous。  
  
## <a name="create-a-send-port"></a>建立傳送埠
  
1.  在**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，然後展開您的應用程式。  
  
2.  以滑鼠右鍵按一下**傳送埠**，指向 [**新增**，然後按一下 [**靜態請求-回應傳送埠**。  
  
3.  在**傳送埠屬性**對話方塊方塊中，執行下列動作：  
  
    1.  輸入傳送埠名稱，例如`SendToTIBCORV`。  
  
    2.  從**類型**下拉式清單中，選取**TIBCO Rendezvous**。  
  
    3.  從**傳送處理常式**下拉式清單中，選取 URI。  
  
    4.  從 [傳送管線] 下拉式清單中，選取 [ **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**。  從**接收管線**下拉式清單中，選取**[microsoft.biztalk.defaultpiplelines.xmlreceive]**。  

        > [!NOTE]
        > Microsoft BizTalk Adapter for TIBCO Rendezvous 需要您選取 XMLTransmit 管線傳送，並針對 receive XMLReceive 管線。
        
    6.  按一下**設定**以設定傳送埠。  
  
4.  在**TIBCO Rendezvous 傳輸屬性**對話方塊方塊中，執行下列動作：  
  
    1.  輸入屬性。  
  
         您不需要設定登入資訊。  
  
    2.  在此清單中，選取您建立來代表 TIBCO Rendezvous 系統的 SSO 分支機構應用程式。  
  
    3.  如**使用 SSO**，選取**是**。  
  
    4.  按一下 **[確定]**。  
  
5.  按一下 **[確定]**。  

## <a name="set-the-transport-properties"></a>設定傳輸屬性
TIBCO Rendezvous 傳輸屬性用於執行階段。 在**傳輸屬性**，設定連線參數來識別您要將產生的訊息發佈的 TIBCO Rendezvous 網域。  
  
 
1.  在**TIBCO Rendezvous 傳輸屬性**畫面上，依序展開**認證寄件者屬性**並輸入下列資訊。  
  
     ![](../core/media/sadp-tibcoren-transs.gif "SAdp_TibcoRen_Transs")  
  
    |使用|動作|  
    |--------------|----------------|  
    |**分類帳名稱**|預設值為空白。 要用於永續性認證訊息傳遞的分類帳檔案名稱。 只能使用本機磁碟機。|  
    |**可重複使用的名稱**|預設值為空白。 要用於認證訊息傳遞的可重複使用對應名稱。 在網路上所有認證訊息通訊人名稱當中，這必須是唯一名稱。|  
  
2.  展開**認證**並輸入伺服器連線的下列資訊。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**密碼**|預設值為空白。 登入 Tibco Rendezvous 精靈的密碼。|  
    |**使用者名稱**|預設值為空白。 Tibco Rendezvous 精靈的使用者名稱。|  
  
3.  展開**一般設定**並輸入 TIBCO Rendezvous 伺服器連線的下列資訊。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**字碼頁編號**|預設值為 65001 (UTF-8 編碼的字碼頁)。 這是 TIBCO Rendezvous SDK 用於字串編碼的字碼頁。|  
    |**預設的主體名稱**|預設值是空白。 主體名稱是在協調流程中設定。 如果某個連接埠用於某種訊息類型，您可以提供預設的主體名稱，這樣可以省去設定主體名稱屬性的需要，而使得協調流程變得更簡單。|  
    |**啟用時間批次**|預設值為 False。 啟用/停用 TIBCO Rendezvous 時間批次功能。|  
    |**將不受支援的型別對應至字串**|預設值是 True。 如果為 true，不支援的類型會對應到字串 (如果可能的話)。 若為 False，就會產生執行階段錯誤。|  
    |**二進位碼檔案，例如 TIBCO Rendezvous 組件的路徑**|如果 PATH 環境變數中尚無此資訊，請提供此資訊。|  
    |**保留器順序**|預設值是 True。 啟用以 BizTalk Server 收到訊息的相同順序，將訊息傳送到 TIBCO Rendezvous 的邏輯。 此參數會強制以相同的順序發佈訊息；這並不表示訂閱者會以相同的順序收到訊息。|  
    |**傳送埠識別碼**|這個識別項會出現在與此連接埠相關聯的記錄訊息中。 這是為了方便您參考而提供。|  
  
4.  展開**Rendezvous 傳輸**並輸入 TIBCO Rendezvous 伺服器的連接資訊，請按一下**套用**，然後按一下 [**確定**。  
  
     您必須設定連線參數，讓 Microsoft BizTalk Adapter for TIBCO Rendezvous 能夠存取 TIBCO Rendezvous。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**精靈**|預設值是空白。<br /><br /> Rendezvous 傳輸精靈參數。|  
    |**網路**|預設值是空白。<br /><br /> Rendezvous 傳輸網路參數。|  
    |**服務**|預設值是空白。<br /><br /> Rendezvous 傳輸服務參數。|  
  
5.  提供使用單一登入 (SSO) 的認證。  
  
     您可以使用兩種方法來存取 TIBCO Rendezvous 系統。 您可以使用認證 (使用者名稱和密碼參數) 或單一登入。  
  
    1.  選取**是**中**使用 SSO**使用單一登入。  
  
        > [!NOTE]
        >  請參閱[安全性](../core/security-in-biztalk-adapter-for-tibco-rendezvous.md)如需有關如何設定 SSO 資訊。  
  
    2.  從清單中選取一個分支機構應用程式。  
  
         企業單一登入工具建立的分支機構應用程式代表一個應用程式 (例如 TIBCO Rendezvous)。 Microsoft BizTalk Adapter for TIBCO Rendezvous 會使用應用程式使用者的認證。 這些認證是針對所指定分支機構應用程式，從伺服器系統的 SSO 資料庫中擷取所得。  
  
        > [!NOTE]
        >  如需如何建立分支機構應用程式資訊，請參閱[建立分支機構應用程式](../core/creating-affiliate-applications1.md)。  
  
6.  按一下**套用**，然後按一下 [**確定**提供所有必要的資訊，以採用連線資訊之後。  
  
     您必須設定連線參數，讓 BizTalk Adapter for TIBCO Rendezvous 能夠存取 TIBCO Rendezvous。  


## <a name="next-steps"></a>後續的步驟
  
-   [從 BizTalk Server 使用 TIBCO Rendezvous 傳送埠](../core/using-tibco-rendezvous-send-ports-from-biztalk-server.md)  
  
-   [TIBCO Rendezvous 中的傳送處理常式資料類型對應](../core/data-type-mapping-for-send-handlers-in-tibco-rendezvous.md)  
  
-   [BizTalk Server 訊息內容屬性 (傳送處理常式)](../core/biztalk-server-message-context-properties-send-handlers.md)