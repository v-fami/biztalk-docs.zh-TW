---
title: 步驟 2： 設定雙向 Wcf-webhttp 傳送埠 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0bcab296-7921-4df4-abcc-eea78cc827e8
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f355275f9480cfa13f3a15bcc6522fbe7ec83b8c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22278886"
---
# <a name="step-2-configure-a-two-way-wcf-webhttp-send-port"></a>步驟 2： 設定雙向 Wcf-webhttp 傳送埠
在這個步驟您要設定雙向**Wcf-webhttp**傳送埠以叫用 REST 資源 URL，以擷取在美國空中電信業者的排程中的延遲。  
  
### <a name="to-configure-wcf-webhttp-send-port"></a>若要設定 WCF-WebHttp 傳送埠  
  
1.  從 BizTalk Server 管理主控台，在**BizTalk Application 1** ] 節點，以滑鼠右鍵按一下**傳送埠**，指向**新增**，然後按一下 [**靜態請求-回應傳送埠**。  
  
2.  在 [一般] 索引標籤上，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**名稱**|型別**SendPortRESTAzureMarketPlace**。|  
    |**型別**|選取**Wcf-webhttp**。|  
    |**傳送處理常式**|選取 **[BizTalkServerApplication]**。|  
    |**傳送管線**|選取**PassThruTransmit**。|  
    |**接收管線**|選取**PassThruReceive**。|  
  
     按一下**設定**。  
  
3.  從**Wcf-webhttp 傳輸屬性**對話方塊方塊中，執行下列動作：  
  
    1.  在**一般**索引標籤上，針對**位址 (URI)**，輸入`https://api.datamarket.azure.com/oakleaf/US_Air_Carrier_Flight_Delays_Incr/`。  
  
    2.  在 [一般] 索引標籤上的**HTTP 方法和 URL 對應**，輸入下列命令：  
  
        ```  
        <BtsHttpUrlMapping>  
        <Operation Method="GET" Url="/On_Time_Performance" />  
        </BtsHttpUrlMapping>  
  
        ```  
  
         在這裡，**取得**為 HTTP 動詞命令和**On_Time_Performance**附加至基底 URI 來建構唯一資源 URL，以擷取航班延誤。  
         
         > [!TIP] 
         > 在 [URL] 欄位中，任何特殊的 XML 字元必須"逸出"。 這可確保，處理，並且保留連接埠的特殊 XML 字元。 例如，`&`必須逸出特殊字元為`&amp;`。 
           >
           >從：`Url=”/Customer?{ID}& group=Location”`
           >
           >
           >若要：`Url=”/Customer?{ID}&amp;group=Location”`
  
    3.  在**繫結**索引標籤上，針對**接收訊息大小上限**欄位中，選取夠大的值。 這是因為含有航班狀態的回應訊息通常相當大，有可能超過指定的預設訊息大小。  
  
    4.  在**安全性**索引標籤上，執行下列動作：  
  
        1.  如**安全性模式**，選取**傳輸**。  
  
        2.  如**傳輸用戶端認證類型**，選取**基本**。  
  
        3.  在下**使用者名稱認證**方塊中，按一下**編輯**。 在**用戶端認證**對話方塊中，選取**執行不會使用單一登入**，並輸入使用者名稱和密碼從您擷取**我的帳戶**索引標籤上，當您有了登入[Windows Azure Marketplace](http://go.microsoft.com/fwlink/p/?LinkId=257913)。 認證會列出針對**客戶 ID** （使用者名稱） 和**主要帳戶金鑰**（密碼） 標籤。  
  
        4.  按一下 **[確定]**。  
  
    5.  在**訊息**索引標籤上，針對**隱藏動詞命令的主體**，指定您要刪除從要求訊息的訊息內容的動詞。 此教學課程中，指定為`GET`。 原因如下： GET 方法呼叫美國空中載波飛行延遲 REST 端點上的不需要的訊息內容。REST 資源 URL 就足以擷取資訊。 不過，要觸發程序**Wcf-webhttp**讓其餘呼叫的傳送埠，您卸除具有某些訊息內文將虛擬訊息。 傳送埠必須 REST 端點傳送該虛擬訊息，因為稍早所述，端點未預期的訊息內容。 因此，再叫用 REST 端點，配接器去除訊息內容，從空的訊息只會針對您在中指定的動詞命令**隱藏動詞命令的主體**文字方塊。  
  
    6.  按一下**確定**直到您會回到 [傳送埠屬性] 對話方塊。 從左窗格中，按一下 **篩選**，並指定要取用接收透過接收所有訊息的篩選條件連接埠中建立您[步驟 1： 設定 FILE 接收位置](../core/step-1-configure-a-file-receive-location.md)。  
  
        |||  
        |-|-|  
        |**屬性**|設定為**BTS。ReceivePortName**|  
        |**運算子**|設定為**==**|  
        |**值**|設定為`ReceivePortRestAzureMarketPlace`|  
  
    7.  按一下 **[確定]**。  
  
## <a name="see-also"></a>另請參閱  
 [教學課程 5： 叫用 REST 介面使用 BizTalk Server](../core/tutorial-5-invoking-a-rest-interface-using-biztalk-server.md)