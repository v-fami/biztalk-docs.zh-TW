---
title: 建立 TIBCO EMS 接收成品 |Microsoft 文件
description: 建立接收埠，並設定在 BizTalk Server 使用 TIBCO Enterprise Message Service 配接器傳輸屬性
ms.custom: ''
ms.date: 10/23/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e1307e3c-0237-4f19-a642-58e694fe95d0
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bf5810dc012c7aa5dcc2fbdfcecd9d59d066ced7
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
ms.locfileid: "24015373"
---
# <a name="create-tibco-ems-receive-artifacts"></a>建立 TIBCO EMS 接收成品

## <a name="overview"></a>概觀
TIBCO Enterprise Message Service 接收器是一項待命程式服務，能夠註冊特定的佇列或主題，然後接收相關的訊息。 BizTalk Adapter for TIBCO Enterprise Message Service 會先開啟新的工作階段以向 TIBCO Enterprise Message Service 註冊，然後才繼續輪詢以接收訊息。 本節將說明如何設定傳送埠以連線至 TIBCO Enterprise Message Service，以及如何在協調流程中納入 XML 以在執行階段與 TIBCO EMS 互動。  

## <a name="create-a-receive-port"></a>建立接收埠  
  
1.  在 BizTalk Server 管理主控台中，展開**BizTalk 群組**，依序展開**應用程式**，然後展開您的應用程式。  
  
2.  以滑鼠右鍵按一下**接收埠**，選取**新增**，然後按一下 **單向接收埠**。  
  
3.  在**接收埠屬性**視窗，請在**一般**頁面上，執行下列動作：  
  
    1.  在**名稱**欄位中，輸入`ReceiveFromTIBCOEMS`。  
  
    2.  在**驗證**群組方塊中，指定使用驗證時，如何處理的訊息。  
  
    3.  選取**啟用的路由失敗訊息**核取方塊。  
  
4.  在**接收位置**頁面上，執行下列動作：  
  
    1.  按一下 **[新增]**。  
  
    2.  在**接收位置**視窗，請在**一般**頁面上，輸入**名稱**接收位置。  
  
    3.  從**類型**下拉式清單中，選取傳輸類型，以及從**接收處理常式**下拉式清單中，選取傳輸位址。  
  
    4.  從**接收管線**下拉式清單中，選取接收管線。  
  
    5.  在**排程**頁面上，選取**開始日期**和**結束日期**限制接收文件。  
  
    6.  選取**啟用服務窗口**核取方塊。  
  
    7.  按一下 **[確定]**。  
  
5.  在**輸入對應**頁面上，選取輸入的對應轉換文件上選取的連接埠。  
  
6.  在**追蹤**頁面上，選取所需的追蹤訊息內文和追蹤訊息屬性。  
  
7.  按一下 **[確定]**。  

## <a name="set-the-receive-port-transport-properties"></a>設定接收埠傳輸屬性
如 TIBCO Enterprise Message System (EMS) 接收位置， **URL**和**目標命名空間**至 TIBCO EMS 系統是所需的組態值。    
 
1.  展開**系統定義**並輸入 TIBCO EMS 伺服器連線的所有必要的資訊。  
  
2.  展開**訊息處理**並輸入所有必要的資訊。  
  
    |參數|Description|  
    |---------------|-----------------|  
    |**訊息選取器**|只有在對目的地中的訊息評估此字串得到 True 時，才會接收訊息。<br /><br /> 允許接收埠只接收內部標頭屬性與此欄位所述運算式相符的訊息。<br /><br /> 訊息選取器的語法是以 SQL92 條件運算式語法的子集為基礎。 TIBCO EMS 使用者指南含有此語法的完整說明。<br /><br /> 例如，如果訊息中包含名為 NewsType 的標頭屬性，則接收埠只能擷取屬於 Sports 或 Editorial 類型的訊息。|  
    |**重試計數**|傳輸的重試計數。 預設值為 0。|  
    |**重試間隔**|配接器進行重試之前所等候的時間。 預設值為五分鐘。|  
  
3.  展開**伺服器連線定義**並輸入所有必要的資訊。  
  
    |參數|Description|  
    |---------------|-----------------|  
    |**目的地**|必要設定。 定義目的地的名稱與類型。 使用下列格式定義佇列或主題：Queue[queue.name] 或 Topic[topic.name]。|  
    |**通訊埠編號**|TIBCO EMS 伺服器所收聽的連接埠。|  
    |**伺服器名稱**|必要設定。 裝載 TIBCO EMS 伺服器的系統名稱。|  
  
4.  提供使用單一登入 (SSO) 的認證。  
  
     有兩種方法可以用來存取 TIBCO EMS 系統。 您可以使用「認證」(使用者名稱與密碼參數) 或「單一登入」。  
  
    -   選取**是**中**使用 SSO**使用單一登入。  
  
    -   在清單中選取分支機構應用程式。  
  
         由企業單一登入工具所建立的分支機構應用程式代表如 TIBCO EMS 之類的應用程式。 Microsoft BizTalk Adapter for TIBCO EMS 會使用應用程式使用者的認證。 這些認證是針對所指定分支機構應用程式，從伺服器系統的 SSO 資料庫中擷取所得。  
  
         如需如何建立分支機構應用程式的詳細資訊，請參閱[建立分支機構應用程式](../core/creating-affiliate-applications5.md)。  
  
5.  展開**使用者認證**輸入**使用者名**和**密碼**來存取 TIBCO EMS 伺服器。  
  
    |參數|Description|  
    |---------------|-----------------|  
    |`Password`|用來與 TIBCO EMS 精靈通訊的使用者密碼。<br /><br /> 如果您未選取**使用 SSO**，您必須設定為 BizTalk Adapter for TIBCO EMS 才能與 TIBCO EMS 精靈通訊的認證參數。|  
    |`User Name`|用來與 TIBCO EMS 精靈通訊的使用者名稱。<br /><br /> 如果您未選取**使用 SSO**，您必須設定為 BizTalk Adapter for TIBCO EMS 才能與 TIBCO EMS 精靈通訊的認證參數。|  
  
6.  按一下**套用**，然後按一下 **確定**。 

## <a name="next-steps"></a>後續的步驟
[TIBCO EMS 訊息內容屬性](../core/message-context-properties-in-biztalk-server.md)