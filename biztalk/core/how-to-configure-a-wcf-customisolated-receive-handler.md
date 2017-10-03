---
title: "如何設定 Wcf-customisolated 接收處理常式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3e90add2-1a5e-4509-a98c-b3c297b4213f
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 00e52daaaefc3f85537dc3c51f8700da30b74876
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-a-wcf-customisolated-receive-handler"></a>如何設定 Wcf-customisolated 接收處理常式
如果您想要查閱 machine.config 以外的位置的自訂行為延伸模組 Wcf-customisolated 配接器，您必須設定接收處理常式屬性。  
  
## <a name="why-should-wcf-customisolated-adapter-look-up-custom-behavior-extensions-from-locations-other-than-machineconfig"></a>為什麼應該 Wcf-customisolated 配接器查詢自訂行為延伸模組 machine.config 以外的位置？  
 所使用的自訂行為延伸模組[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]machine.config 中註冊。然後再載入行為延伸模組，Wcf-customisolated 配接器會尋找在 machine.config 中的行為延伸模組。不過，machine.config 適合用來儲存特定電腦上執行的所有應用程式需要的組態資訊。 另一方面，需要 WCF 自訂行為延伸模組的可能只有 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，而不是電腦上執行的所有應用程式。 因此，雖然在 machine.config 中儲存自訂行延伸模組可達到目的，但這並不是最佳位置。  
  
 與[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，配接器處理常式屬性提供其他從中 Wcf-customisolated 配接器可以查詢自訂行為延伸模組的位置。 請注意，這並不會取代 machine.config 中已有的行為延伸模組。  
  
### <a name="additional-considerations"></a>其他考量  
 保留下列幾點點時設定 Wcf-customisolated 接收處理常式屬性：  
  
-   自訂行為延伸模組必須出現在 machine.config 或配接器處理常式屬性中。 這兩個位置的自訂行為延伸模組不能重複。  
  
-   如果自訂行為延伸模組已出現在 machine.config 中，而您嘗試在配接器處理常式屬性中設定同一個延伸模組，則當您嘗試設定屬性時會立即出現錯誤。  
  
-   如果配接器處理常式屬性中已經設定自訂行為延伸模組，而您又以同一個行為延伸模組來更新 machine.config，即會出現執行階段錯誤並記錄在事件日誌中。 接收位置同時會遭停用。  
  
-   自訂行為延伸模組中參考的組件必須存在全域組件快取 (GAC) 中，您才能設定配接器處理常式屬性。  
  
## <a name="configuring-the-adapter-handler-properties"></a>設定配接器處理常式屬性  
 使用下列程序來設定 Wcf-customisolated 接收處理常式。  
  
#### <a name="to-configure-the-adapter-handler-properties"></a>若要設定配接器處理常式屬性  
  
1.  在 BizTalk 管理主控台中，展開[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]**管理**，依序展開**BizTalk 群組**，依序展開**平台設定**，然後展開  **配接器**。  
  
2.  在展開的配接器清單中，按一下  **Wcf-customisolated**，在右窗格，以滑鼠右鍵按一下您想要設定的接收處理常式，然後按一下**屬性**。  
  
3.  在**配接器處理常式屬性**對話方塊**一般**索引標籤的**主機名稱**清單中，選取與其相關聯，接收處理常式的主機，然後按一下**屬性**。  
  
4.  在**Wcf-customisolated 傳輸屬性**對話方塊**WCF 延伸模組**索引標籤上，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**匯入**|匯入含有 WCF 自訂行為延伸模組的 WCF 組態檔。 按一下此按鈕會開啟**匯入 WCF 組態**對話方塊，即可瀏覽並尋找 WCF 組態檔。 請注意，此檔案應為有效的 WCF 組態檔。 如需 WCF 組態結構描述的詳細資訊，請參閱 「 Windows Communication Foundation 組態結構描述 」 在[http://go.microsoft.com/fwlink/?LinkId=163953](http://go.microsoft.com/fwlink/?LinkId=163953)。|  
    |**匯出**|將 WCF 自訂行為延伸模組匯出到 WCF 組態檔。 按一下此按鈕會開啟**匯出 WCF 組態**對話方塊，即可瀏覽與儲存 WCF 組態檔。|  
    |**Clear**|從配接器處理常式屬性中清除現有的 WCF 自訂行為延伸模組。|  
  
## <a name="see-also"></a>另請參閱  
 [設定 Wcf-customisolated 配接器](../core/configuring-the-wcf-customisolated-adapter.md)