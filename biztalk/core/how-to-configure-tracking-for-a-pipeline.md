---
title: 啟用追蹤的管線 |Microsoft 文件
description: 追蹤訊息內文和在管線處理訊息，BizTalk Server 中的事件
ms.custom: ''
ms.date: 12/13/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4f7f3c4a-4464-4170-a580-b4ce9296a097
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2ed836947ff47e21eeeb3bc306e94ea08f5464f0
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/13/2017
ms.locfileid: "26686621"
---
# <a name="configure-pipeline-tracking-in-biztalk-server"></a>設定追蹤 BizTalk Server 中的管線
您可以使用 BizTalk Server 管理來設定管線追蹤。 您可能需要設定追蹤做為疑難排解和稽核之用。 您可以檢視訊息屬性、 連接埠事件和訊息事件。 您也可以追蹤訊息事件和訊息的連接埠事件。  
  
 您可以設定追蹤其中一個預設管線隨附[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]或自訂管線已部署到 BizTalk 應用程式。 您設定的追蹤設定會套用到管線的所有執行個體。  
  
> [!IMPORTANT]
>  雖然您可以設定管線追蹤，這會產生大量的資料因為資料會全域收集使用管線的所有連接埠。 相反地，我們建議您設定追蹤傳送和接收埠中所述[設定傳送埠的追蹤](../core/how-to-configure-tracking-for-a-send-port.md)和[設定追蹤接收埠](../core/how-to-configure-tracking-for-a-receive-port.md)。  
  
 如需有關追蹤功能的訊息事件和服務執行個體[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，請參閱[檢視追蹤的訊息和執行個體資料](../core/viewing-tracked-message-and-instance-data.md)  
  
## <a name="prerequisites"></a>Prerequisites  
使用 BizTalk Server 系統管理員群組的成員帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
## <a name="enable-pipeline-tracking"></a>啟用管線追蹤
  
1.  在**BizTalk Server 管理**，展開包含管線的 BizTalk 群組。 
  
2.  執行下列其中之一：  
  
    -   若要設定追蹤其中一個預設 BizTalk 管線中，展開 \<所有成品\>。  
  
    -   若要設定追蹤已部署到 BizTalk 應用程式的自訂管線，請展開包含管線的應用程式。  
  
3.  選取**管線**資料夾中，以滑鼠右鍵按一下管線，然後選取**追蹤**。  
  
    > [!NOTE]
    >  若要設定追蹤，多個管線，按住 Shift 鍵，選取要設定每個管線，以滑鼠右鍵按一下其中一個管線，然後選取**追蹤**。  
  
4.  使用下列詳細資料，若要設定追蹤選項，然後再選取**確定**以儲存變更。  
  
    |使用|以進行此動作|  
    |--------------|----------------|  
    |**追蹤事件-傳送埠開始與結束事件**|只有當執行個體的開始和結束追蹤。 詳細資訊包括項目名稱、組件及其他中繼資料。|  
    |**追蹤事件-訊息傳送與接收事件**|追蹤訊息傳送與接收事件。 僅適用於當**連接埠開始與結束事件**已選取。|  
    |**追蹤訊息內文-管線處理之前的訊息**|儲存及追蹤管線，其中包含中繼資料，例如 Url 及升級屬性所接收的訊息內文。 若此管線屬於接收管線，則訊息內文即為傳輸元件提交給管線的原始訊息。 視您的應用程式而定，訊息可能經過加密、簽章或編碼。 使用 BizTalk 對應時，如果此管線屬於接收管線，則會在處理輸入對應之後執行追蹤。<br /><br /> 僅適用於當**訊息傳送與接收事件**已選取。|  
    |**追蹤訊息內文-管線處理後的訊息**|儲存和追蹤訊息內文，傳送管線，其中包含中繼資料，例如 Url 及升級屬性。 若此管線屬於接收管線，則訊息內文即為要提交給 MessageBox 資料庫的已處理訊息，視您的應用程式而定，這個訊息可能是 XML。 使用 BizTalk 對應時，如果此管線屬於傳送管線，則會在處理輸出對應之前執行追蹤。<br /><br /> 僅適用於當**訊息傳送與接收事件**已選取。|  
  
## <a name="see-also"></a>請參閱  
 [管理管線](../core/managing-pipelines.md)
