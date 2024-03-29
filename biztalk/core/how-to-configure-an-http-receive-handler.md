---
title: 如何設定 HTTP 接收處理常式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- permissions, receive handlers
- configuring [HTTP adapters], permissions
- HTTP adapters, receive handlers
- receive handlers, permissions
- configuring [HTTP adapters], receive handlers
- permissions, HTTP adapters
- receive handlers, HTTP adapters
- HTTP adapters, permissions
ms.assetid: c295489e-dbbb-44f7-bddb-d3cdfe302cf5
caps.latest.revision: 27
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7b58dcb66e4a001d7d163f5d8de53fb89502c6ef
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36983383"
---
# <a name="how-to-configure-an-http-receive-handler"></a>如何設定 HTTP 接收處理常式
使用下列程序可設定 HTTP 接收處理常式的屬性。  
  
> [!NOTE]
>  每個主控件只能有一個關聯的接收處理常式。  
> 
> [!NOTE]
>  HTTP 接收配接器在「BizTalk 外掛式主控件」執行個體的環境中執行。  
> 
> [!CAUTION]
>  在使用 HTTP 或 SOAP 配接器處理常式時，建議您在 Microsoft [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] 或 [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] 電腦上安裝這些處理常式的主控件執行個體。  
  
### <a name="to-configure-the-general-properties-for-an-http-receive-handler"></a>設定 HTTP 接收處理常式的一般屬性  
  
1. 在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]**管理**，展開**BizTalk 群組**，展開**平台設定**，然後展開**配接器**。  
  
2. 在展開的配接器清單中，按一下**HTTP**在右窗格中，以滑鼠右鍵按一下您想要設定，然後按一下 接收處理常式**屬性**。  
  
3. 在 **配接器處理常式屬性**對話方塊的 **一般**索引標籤**主機名稱**清單中，選取與其相關聯的接收處理常式的主控。  
  
4. 按一下 **屬性**若要存取**批次大小**屬性之 http 接收處理常式。  
  
5. 輸入介於 1 到 256 值，然後按一下**確定**。  
  
6. 按一下 [確定] 。  
  
   BizTalk Server 的設計，有效地處理訊息批次，而非快速處理單一訊息。 因此，如果此接收處理常式將會用於「雙向/要求-回應」接收位置，那麼您就可以依照下列步驟，將延遲降到最低：  
  
- 設定**批次大小**屬性設為 1 的值。  
  
- 減少**MaxReceiveInterval**值小於 100 的值從預設值為 500 **Messaging Isolated]、 [XLANG/s**並**Messaging In-process**服務類別。  變更**adm_ServiceClass** BizTalk 管理資料庫，其中包含每個服務類型的一筆記錄的資料表。  變更此設定，因為這是整個服務類型變更時，請務必小心。 此設定會指定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 傳訊代理程式向 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Messagebox 資料庫輪詢訊息的輪詢間隔上限 (以毫秒為單位)。  節流控制器也會使用此設定，決定在特定的負載狀況下是否需要進行訊息節流。 如果有需要，節流控制器將會根據系統上的壓力狀況，以遞增的方式延遲訊息分派間隔。 在高輸送量系統中，將不會使用此設定。  然而一旦使用此值，時間間隔就會在 MaxReceiveInteral/10 與 MaxReceiveInterval 之間動態切換。  
  
  > [!NOTE]
  >  變更此設定會影響所有主機，以建立**主控件類型**的**隔離**。  
  
- 重新啟動與您所設定的任何 HTTP 接收函式相關聯的 IIS 應用程式集區。  
  
  登入帳戶**BizTalkServerIsolatedHost**主控件執行個體必須具有讀取和寫入權限暫存目錄的動態編譯的程式碼後置檔案，使用 HTTP 接收函式。 使用下列程序授與權限。  
  
### <a name="to-grant-the-account-for-the-biztalkserverisolatedhost-host-instance-read-and-write-permissions-to-the-temp-directory-of-your-biztalk-server"></a>授與 BizTalkServerIsolatedHost 主控件執行個體帳戶對於 BizTalk Server 暫存目錄的寫入和讀取權限  
  
1. 按一下 **開始**，按一下**執行**，型別**CMD**，然後按 ENTER。  
  
2. 在命令提示字元中，輸入**設定 TEMP**然後按 ENTER 以顯示相關聯的目錄**TEMP**環境變數。  
  
3. 在命令提示字元中，輸入**set TMP**然後按 ENTER 以顯示相關聯的目錄**TMP**環境變數。  
  
   授與指定的登入帳戶為帳戶**BizTalkServerIsolatedHost**主控執行個體讀取和寫入權限或多個相關聯的目錄**TEMP**並**TMP**環境變數。 若要判斷的登入帳戶**BizTalkServerIsolatedHost**執行個體，在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]**管理**，展開**BizTalk 群組**，依序展開**平台設定**，展開**主控件執行個體**，以滑鼠右鍵按一下**BizTalkServerIsolatedHost**主應用程式在右窗格中，執行個體，然後按**屬性**。 用於主控件執行個體的登入帳戶列在旁**登入**標籤。  
  
## <a name="see-also"></a>另請參閱  
 [設定 HTTP 配接器](../core/configuring-the-http-adapter.md)