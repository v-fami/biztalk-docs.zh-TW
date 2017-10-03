---
title: "如何設定管線追蹤 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [pipelines], tracking warning
- tracking, pipelines
- tracking, warnings
- configuring, pipelines
- pipelines, tracking
- managing [pipelines], configuring
- tracking, configuring
- pipelines, configuring
- configuring [HAT tracking], pipelines
- HAT, pipelines
- managing [pipelines], tracking
ms.assetid: 4f7f3c4a-4464-4170-a580-b4ce9296a097
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e933e9b50c99e11013ceaedf65c4f253ad1620c2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-tracking-for-a-pipeline"></a>如何設定管線的追蹤
本主題描述如何使用「BizTalk Server 管理」來設定管線追蹤。 您可能需要設定追蹤做為疑難排解和稽核之用。 您可以檢視訊息屬性、 連接埠事件和訊息事件。 您也可以追蹤訊息事件和訊息的連接埠事件。  
  
 您可以設定追蹤其中一個預設管線隨附[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]或自訂管線已部署到 BizTalk 應用程式。 您設定的追蹤設定會套用到管線的所有執行個體。  
  
> [!IMPORTANT]
>  您可以設定管線追蹤，但這將產生大量資料，因為會全域收集使用管線的所有連接埠的資料。 我們建議您改為您設定追蹤傳送和接收埠中所述[如何設定傳送埠的追蹤](../core/how-to-configure-tracking-for-a-send-port.md)和[如何設定追蹤接收埠](../core/how-to-configure-tracking-for-a-receive-port.md)。  
  
 如需有關追蹤功能的訊息事件和服務執行個體[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，請參閱[檢視追蹤的訊息和執行個體資料](../core/viewing-tracked-message-and-instance-data.md)  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
### <a name="to-configure-tracking-for-a-pipeline"></a>設定管線的追蹤  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，依序展開**BizTalk Server 管理**展開包含要設定追蹤的管線的 BizTalk 群組。  
  
3.  執行下列其中之一：  
  
    -   若要設定追蹤其中一個預設 BizTalk 管線中，展開 \<所有成品 >。  
  
    -   若要設定追蹤已部署到 BizTalk 應用程式的自訂管線，請展開包含管線的應用程式。  
  
4.  按一下**管線**資料夾中，以滑鼠右鍵按一下管線，然後按一下**追蹤**。  
  
    > [!NOTE]
    >  若要設定的多個管線，按住 Shift 鍵，按一下 設定每個管線追蹤，以滑鼠右鍵按一下其中一個管線，然後**追蹤**。  
  
5.  下表中所述，設定您要的追蹤選項，然後按一下**確定**。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**連接埠開始與結束事件**|僅限於執行個體開始與結束時，才選取此核取方塊以進行追蹤。 詳細資訊包括項目名稱、組件及其他中繼資料。|  
    |**訊息傳送與接收事件**|選取此核取方塊以追蹤訊息傳送與接收事件。 此核取方塊才**連接埠開始與結束事件**已選取。|  
    |**管線處理之前的訊息**|選取此核取方塊以儲存及追蹤管線所接收的訊息內文，其中包含 URL 及升級屬性等中繼資料。 若此管線屬於接收管線，則訊息內文即為傳輸元件提交給管線的原始訊息。 視您的應用程式而定，訊息可能經過加密、簽章或編碼。 使用 BizTalk 對應時，如果此管線屬於接收管線，則會在處理輸入對應之後執行追蹤。<br /><br /> 此核取方塊才**訊息傳送與接收事件**已選取。|  
    |**管線處理後的訊息**|選取此核取方塊以儲存及追蹤管線所傳送的訊息內文，其中包含 URL 及升級屬性等中繼資料。 若此管線屬於接收管線，則訊息內文即為要提交給 MessageBox 資料庫的已處理訊息，視您的應用程式而定，這個訊息可能是 XML。 使用 BizTalk 對應時，如果此管線屬於傳送管線，則會在處理輸出對應之前執行追蹤。<br /><br /> 此核取方塊才**訊息傳送與接收事件**已選取。|  
  
## <a name="see-also"></a>另請參閱  
 [管理管線](../core/managing-pipelines.md)