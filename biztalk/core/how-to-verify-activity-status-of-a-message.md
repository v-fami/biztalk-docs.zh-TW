---
title: 如何驗證訊息的活動狀態 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- activities, verifying status
- PeopleSoft Integration Broker
- verifying message status in PeopleSoft
- messages, verifying status
ms.assetid: b8cee6f9-0f65-4228-a87a-3f3aca6182bf
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8af3a77b9bb169e394571444c7eb7e3984f7f7c3
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37013039"
---
# <a name="how-to-verify-activity-status-of-a-message"></a>如何確認訊息的活動狀態
您可以使用 PeopleSoft Integration Broker 建立 PeopleSoft HTTP 主控件和連接埠，讓 PeopleSoft 傳送事件。 請依照下列步驟，確定訊息正在作用中，並且已路由傳送。  
  
### <a name="to-verify-that-a-message-is-active-and-routed-correctly"></a>若要確認訊息正在作用中並已正確路由傳送  
  
1. 按一下 **開始**，指向**程式**，指向**PeopleSoft 應用程式名稱**，然後選取**應用程式設計工具**。  
  
2. 上**PeopleSoft 登入**畫面上，輸入**使用者識別碼**並**密碼**，然後按一下 **確定**。  
  
    ![](../core/media/psadapter-24-task-userpass.gif "PSAdapter_24_Task_UserPass")  
  
    ![](../core/media/psadapter-25-task-emptydesigner.gif "PSAdapter_25_Task_EmptyDesigner")  
  
3. 在 應用程式設計工具中，在**檔案**功能表上，指向**開啟**，然後選取**訊息**。  
  
    ![](../core/media/psadapter-26-task-filemessage.gif "PSAdapter_26_Task_FileMessage")  
  
4. 在 **開啟定義**畫面上，在**名稱**欄位中，輸入`LOCATION_SYNC`，然後按一下**開啟**。  
  
    ![](../core/media/psadapter-27-task-locationsync.gif "PSAdapter_27_Task_LocationSync")  
  
5. 在 **定義符合選取準則**區段中，按兩下**LOCATION_SYNC**來檢視屬性的訊息。  
  
    ![](../core/media/psadapter-28-task-locationproperties.gif "PSAdapter_28_Task_LocationProperties")  
  
6. 在 應用程式設計工具中，以滑鼠右鍵按一下**location_tbl**，然後選取**訊息屬性**。  
  
    ![](../core/media/psadapter-29-task-loctionmenu.gif "PSAdapter_29_Task_LoctionMenu")  
  
7. 在 [**訊息屬性**畫面上，按一下**使用**] 索引標籤。  
  
    確認下列項目，然後再按一下**確定**。  
  
   1. **訊息：** Active  
  
   2. **訊息通道：** ENTERPRISE_SETUP  
  
   3. **預設版本：** VERSION_1  
  
      ![](../core/media/psadapter-30-task-messageuse.gif "PSAdapter_30_Task_MessageUse")  
  
8. 結束 [Application Designer]。  
  
    這會確定 PeopleSoft 中該訊息處於作用中狀態、使用 VERSION_1，並且流程會經由 ENTERPRISE_SETUP 通道。  
  
9. 設定 Integration.Gateway.properties 檔案，與 PeopleSoft 應用程式通訊。  
  
     確認已設定下列屬性：  
  
    -   **ig.isc.serverurl:** //server:9000  
  
    -   **ig.isc.userid:** PS 的識別碼  
  
    -   **ig.isc.password:** PS 的密碼  
  
    -   **ig.isc.toolsrel:** 特定版本  
  
## <a name="see-also"></a>另請參閱  
 [建立 PeopleSoft HTTP 主控件和連接埠](../core/creating-a-peoplesoft-http-host-and-port.md)