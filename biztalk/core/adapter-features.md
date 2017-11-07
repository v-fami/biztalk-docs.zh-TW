---
title: "TIBCO Enterprise Message Service 配接器功能 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ede748ce-3f28-4942-b2bd-e38e5f1b0f54
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ce63950ea9fca42969a7d8574fec76f438ed5f8f
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="tibco-ems-adapter-features"></a>TIBCO EMS 配接器功能
Microsoft BizTalk Adapter for TIBCO Enterprise Message Service (EMS) 可讓您使用 BizTalk Server 和 TIBCO SDK 來發佈和訂閱由 TIBCO EMS 所管理的佇列和主題。 此配接器以快速、 簡易而可靠的方式與 TIBCO EMS 訊息整合。 其在 TIBCO EMS 伺服器與 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 之間交換 XML 資料格式，以提供緊密整合而可靠的應用程式基礎結構。 它會提供傳輸和接收配接器整合作業提供端對端商務程序管理使用 XML 結構描述。  
  
## <a name="data-validation"></a>資料驗證  
 BizTalk Adapter for TIBCO EMS 會以嚴密整合的原生內含式配接器形式，搭配 BizTalk Server 主控件執行，並且會在進行設定時驗證連接埠設定。 它會盡量驗證許多資料，例如有效名稱、有效數字、有效範圍。 它不會嘗試建立連線。 因此，主控件、連接埠目的地、使用者和密碼在到了執行階段被呼叫之前，都未經過驗證，在此情況下就會記錄錯誤訊息。  
  
## <a name="message-delivery"></a>訊息傳遞  
 BizTalk Adapter for TIBCO EMS 保證訊息只會傳遞一次。 未到達 EMS 而遭到擱置的訊息會標示為可重試。 但也可能會有一些例外，例如執行時有無效的連接埠組態存在。  
  
 此配接器會接受文字 EMS 訊息類型。  配接器支援前往 EMS，訊息的交易和交易支援由[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  
  
> [!NOTE]
>  BizTalk Adapter for TIBCO EMS 與 EMS 伺服器之間使用不安全的連線。 所提供的 TIBCO EMS SDK 並不支援此連線。  
  
 此配接器支援所有標準的 JMS 屬性和 EMS 延伸模組。 這些屬性會放在 BizTalk 訊息內容中以供協調流程使用。  
  
## <a name="general-adapter-features"></a>一般配接器功能  
 BizTalk Adapter for TIBCO EMS 提供一種在 TIBCO EMS 系統與 BizTalk Server 之間交換即時商務資料的方法。 此配接器讓 XML 應用程式與 TIBCO EMS 得以彼此互動。 其可讓 XML 應用程式處理輸入自或輸出至 TIBCO EMS 的訊息。  
  
 此配接器會使用下列其中一項接受 XML 訊息，讓 BizTalk Server 應用程式能夠與 TIBCO EMS 進行通訊：  
  
-   傳輸配接器，使用「靜態單向傳送埠」來傳送訊息給 TIBCO EMS。  
  
-   接收配接器，使用「靜態單向接收埠」接收來自 TIBCO EMS 的訊息。  
  
### <a name="transmit-adapter-architecture-send--static-one-way"></a>傳輸配接器架構： 傳送 – 靜態單向  
 在單向傳送的實例中，傳送埠會設定為將訊息傳送至某個佇列/主題。 BizTalk Adapter for TIBCO Enterprise Message Service 會將所指定的佇列/主題上的要求轉寄給 TIBCO EMS 伺服器。 此配接器會使用 TIBCO EMS 通訊協定將訊息傳送給 TIBCO EMS 系統。 TIBCO EMS 系統會接收要求，然後執行商務邏輯。 若要呼叫 TIBCO EMS，您必須提供此配接器和用於存取 TIBCO EMS 伺服器的組態資訊。  
  
 下圖顯示此配接器的單向傳送作業。  
  
 ![](../core/media/tibcoems-architecture-send.gif "TIBCOEMS_architecture_send")  
  
### <a name="receive-adapter-architecture-receive--static-one-way"></a>接收配接器架構： 接收 – 靜態單向  
 在單向接收的實例中，接收位置會設定為接收某個 EMS 佇列/主題上的訊息。 BizTalk Adapter for TIBCO EMS 會接聽所指定佇列/主題上的訊息，然後將收到的訊息提交給 BizTalk 伺服器。  
  
 下圖顯示此配接器的單向接收作業。  
  
 ![](../core/media/tibcoems-architecture-receive.gif "TIBCOEMS_architecture_receive")  
  
## <a name="see-also"></a>另請參閱  
 [開發應用程式](../core/developing-applications5.md)   
 [快速入門](../core/getting-started-with-biztalk-adapter-for-tibco-enterprise-message-service.md)