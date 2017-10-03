---
title: "匯入 Bindings2 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- bindings, requirements
- importing, bindings
- bindings, importing
ms.assetid: 9e10bc04-aba8-430a-b8fd-de9399d54f88
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b21d5a3dda5bc53816c608e97063a42f3eafa4db
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="importing-bindings"></a>匯入繫結
本節中的主題描述如何將繫結匯入到 BizTalk 群組或應用程式中。  
  
 當您匯入繫結時，請牢記下列要點：  
  
-   **將覆寫現有的繫結。** 如果您要匯入的繫結與現有的繫結同名，將會覆寫現有的繫結。 此外，如果繫結檔案包含合作對象和別名，則已經存在於應用程式之同名的合作對象和別名的任何繫結也會被覆寫。  
  
-   **在群組中的所有繫結必須是唯一的。** 如果已經存在於群組中的繫結與您要匯入的繫結同名，匯入作業將會失敗。  
  
-   **您必須重新設定密碼。** 基於安全性理由，當您匯出繫結檔案時，BizTalk Server 會從該檔案移除繫結的密碼。 匯入繫結後，您必須重新設定密碼，傳送埠和接受位置才能正常運作。 您可以在 BizTalk Server 管理主控台的 [傳輸屬性] 對話方塊中，為傳送埠或接收位置設定密碼。 如需指示，請參閱[如何建立傳送埠](../core/how-to-create-a-send-port2.md)。 另請參閱[如何建立接收位置](../core/how-to-create-a-receive-location.md)。  
  
-   **群組中必須存在該主機。** 對應到繫結中指定之主控件的主控件必須已經存在於要匯入繫結到其中的 BizTalk 群組內，而且主控件信任層級必須相符。 否則，匯入作業將會失敗。  
  
-   **繫結匯入行為取決於繫結來源。** 繫結原先可能是從組件、應用程式或群組匯出的。 根據繫結是從何處匯出而定，匯入作業可能會有不同的效果，如下表所示。  
  
    |繫結的來源|匯入至應用程式|匯入至群組|  
    |----------------------------|-----------------------------------|----------------------------|  
    |從組件匯出繫結|指定的應用程式中必須有包含組件，其名稱與匯出繫結檔案的來源組件相同。 否則，匯入作業會失敗。|此群組必須包含一個組件和應用程式，其名稱與匯出繫結檔案的來源組件和應用程式相同。 否則，匯入作業會失敗。|  
    |從應用程式匯出繫結|匯出繫結檔案的來源應用程式必須與指定的應用程式同名。 否則，匯入作業會失敗。|匯出繫結檔案的來源應用程式，其名稱必須與即將匯入繫結的群組中的某個應用程式相同。 否則，匯入作業會失敗。|  
    |從群組匯出繫結|匯出繫結檔案的來源群組中必須有個應用程式，其名稱與指定的應用程式相同。 否則，匯入作業會失敗。|會針對對應的應用程式來匯入繫結。 也就是說，匯出繫結的來源群組中，特定應用程式的繫結將會匯入到目前群組中同名的應用程式內。|  
  
-   **配接器的 Name 屬性可能不正確。** 若此繫結檔案包含某配接器的設定，請確認繫結檔案中 TransportType 項目的 Name 屬性，與 BizTalk Server 管理主控台中配接器的設定相同 (在 [平台設定] > [配接器] 之下)。  
  
     當您從 [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)] 將繫結匯入到 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] 時，特別應該確認就是這種情況。 下面是這種狀況會造成問題的一些傳輸：  
  
    -   MQS  
  
    -   MSMQ  
  
    -   POP3  
  
    -   Windows SharePoint Services  
  
## <a name="in-this-section"></a>本節內容  
  
-   [如何將繫結匯入到 BizTalk 群組](../core/how-to-import-bindings-into-a-biztalk-group.md)  
  
-   [如何將繫結匯入到 BizTalk 應用程式](../core/how-to-import-bindings-into-a-biztalk-application.md)  
  
-   [如何匯入 EDI AS2 方案的繫結](../core/how-to-import-bindings-for-an-edi-as2-solution.md)