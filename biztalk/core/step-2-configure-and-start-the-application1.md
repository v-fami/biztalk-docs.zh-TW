---
title: 步驟 2： 設定並啟動 Application1 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5cb061ca-acf4-4de4-a634-b3bb98876989
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cc9c3c027126d3a461bf99329b70fda57b9be647
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22280006"
---
# <a name="step-2-configure-and-start-the-application"></a>步驟 2： 設定並啟動應用程式
![步驟 3 之 2](../adapters-and-accelerators/adapter-oracle-database/media/step-2of3.gif "Step_2of3")  
  
 **若要完成的時間：** 10 分鐘  
  
 **目標：** 在此步驟中，設定並啟動 EAISolution 應用程式。  
  
 **用途：** 是多半關於繫結的組態。  繫結會在邏輯端點 (例如協調流程連接埠或角色連結) 與實體端點 (例如傳送和接收埠或合作對象) 之間建立對應。 這讓通訊能在不同的 BizTalk 商務方案元件之間進行。 您可以使用 [BizTalk Server 管理主控台] 建立繫結。  
  
## <a name="prerequisites"></a>必要條件  
 開始此步驟之前，請注意下列需求：  
  
-   在開始此步驟之前必須先完成[步驟 1： 部署專案](../core/step-1-deploy-the-projects.md)。  
  
-   您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分來登入。  
  
## <a name="procedures"></a>程序  
 BizTalk 應用程式是 BizTalk Server 的其中一項功能，能讓 BizTalk Server 商務解決方案的部署、管理和疑難排解更加快速輕鬆。 BizTalk 應用程式是 BizTalk Server 商務解決方案中所使用項目 (稱為「成品」) 的邏輯群組。  如需詳細資訊，請參閱[什麼是 BizTalk 應用程式？](../core/what-is-a-biztalk-application.md)。  在[步驟 1： 部署專案](../core/step-1-deploy-the-projects.md)，我們設定的應用程式名稱是"EAISolution"，然後再部署專案。  因此，EAISolution 應用程式包含協調流程、兩個結構描述以及對應。  
  
#### <a name="to-open-the-eaisolution-application-from-biztalk-server-administration-console"></a>若要從 BizTalk Server 管理主控台開啟 EAISolution 應用程式  
  
1.  按一下**啟動**，指向 **所有程式**，指向  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]。  
  
2.  左邊的主控台樹狀目錄中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開  [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，以滑鼠右鍵按一下**BizTalk 群組**，然後按一下 **重新整理**。  
  
3.  展開**BizTalk 群組**，依序展開**應用程式**，然後按一下  **EAISolution**。  
  
 在[第 2 課： 定義商務程序](../core/lesson-2-define-the-business-process.md)，我們建立了協調流程。  在協調流程中，我們定義了邏輯連接埠。  在下列程序中，您將會定義實體連接埠，並將實體連接埠繫結至邏輯連接埠。  
  
#### <a name="to-create-the-receiverequest-port"></a>若要建立 ReceiveRequest 連接埠  
  
1.  BizTalk Server 管理主控台，從下**EAISolution** ] 節點，以滑鼠右鍵按一下**接收埠**，指向 [**新增**，然後按一下**單向接收埠**。  
  
2.  在 [一般] 索引標籤上執行下列作業：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**名稱**|型別**EAISolutionReceiveRequestPort**。|  
    |**啟用失敗訊息的路由**|(清除)|  
  
3.  按一下**接收位置**，然後按一下 **新增**。  
  
4.  從 [Receive Location1 - 接收位置屬性] 中，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**名稱**|型別**EAISolutionReceiveRequestLocation**。|  
    |**型別**|選取**檔案**。|  
    |**接收處理常式**|選取 **[BizTalkServerApplication]**。|  
    |**接收管線**|選取**XMLReceive**。|  
  
5.  按一下**設定**。  
  
6.  從 [檔案傳輸屬性] 中，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**接收資料夾**|型別**C:\BTSTutorials\WareHouse\Request**。|  
  
7.  按一下**確定**三次。  
  
#### <a name="to-create-the-senddecline-port"></a>若要建立 SendDecline 連接埠  
  
1.  從 BizTalk Server 管理主控台，在**EAISolution** ] 節點，以滑鼠右鍵按一下**傳送埠**，指向**新增**，然後按一下 [**靜態單向傳送埠**。  
  
2.  在 [一般] 索引標籤上，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**名稱**|型別**EAISolutionSendDeclinePort**。|  
    |**型別**|選取**檔案**。|  
    |**傳送處理常式**|選取**BizTAlkServerApplication**。|  
    |**傳送管線**|選取**XML 傳輸**。|  
  
3.  按一下**設定**。  
  
4.  從 [檔案傳輸屬性] 中，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**接收資料夾**|型別**C:\BTSTutorials\WareHouse\RequestDecline**。|  
    |**檔案名稱**|型別**RequestDecline_%MessageID%.xml**。|  
  
5.  按兩次 **[確定]** 。  
  
#### <a name="to-create-the-sendtoerp-port"></a>若要建立 SendToERP 連接埠  
  
1.  從 BizTalk Server 管理主控台，在**EAISolution** ] 節點，以滑鼠右鍵按一下**傳送埠**，指向**新增**，然後按一下 [**靜態單向傳送埠**。  
  
2.  在 [一般] 索引標籤上，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**名稱**|型別**EAISolutionSendToERPPort**。|  
    |**型別**|選取**檔案**。|  
    |**傳送處理常式**|選取**BizTAlkServerApplication**。|  
    |**傳送管線**|選取**XML 傳輸**。|  
  
3.  按一下**設定**。  
  
4.  從 [檔案傳輸屬性] 中，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**接收資料夾**|型別**C:\BTSTutorials\ERP\Request**。|  
    |**檔案名稱**|型別**Request_%MessageID%.xml**。|  
  
5.  按兩次 **[確定]** 。  
  
#### <a name="to-bind-the-ports"></a>若要繫結連接埠  
  
1.  從 BizTalk Server 管理主控台，以滑鼠右鍵按一下**EAISolution**，然後按一下 **設定**。  
  
2.  設定應用程式，從左窗格中，按一下**EAIProcess**。  這是我們建立的協調流程。  
  
3.  從右窗格中，執行下列步驟：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**Host**|選取 **[BizTalkServerApplication]**。|  
    |**接收埠**如**ReceiveRequestPort**|選取 **[eaisolutionreceivereqeustport]**。|  
    |**傳送埠與傳送埠群組**如**ReceiveRequestPort**|選取**EAISolutionSendDeclinePort**。|  
    |**接收埠**如**ReceiveRequestPort**|選取**EAISolutionSendToERPPort**。|  
  
4.  按一下**確定**儲存設定。  
  
#### <a name="to-start-the-application"></a>啟動應用程式  
  
1.  從 BizTalk Server 管理主控台，以滑鼠右鍵按一下**EAISolution**，然後按一下 **啟動**。  
  
2.  從對話方塊中，按一下 **啟動**。  
  
## <a name="what-did-i-just-do"></a>我剛剛做了什麼？  
 在此步驟中，您設定和啟動了 EAIApplication 應用程式。  
  
## <a name="next-steps"></a>後續步驟  
 您可以測試 EAI 方案處理訊息中的方式[步驟 3： 測試方案](../core/step-3-test-the-solution2.md)。  
  
## <a name="see-also"></a>另請參閱  
 [步驟 1： 部署專案](../core/step-1-deploy-the-projects.md)   
 [步驟 3： 測試方案](../core/step-3-test-the-solution2.md)