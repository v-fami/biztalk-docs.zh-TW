---
title: 如何設定排程的接收位置 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- configuring, receive locations
- managing [receive locations], scheduling
- scheduling, receive locations
- managing [receive locations], configuring
ms.assetid: 2653e1c3-ddbd-4d3f-be64-2a5fcd7cf267
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ea43814d6b7c23875bc222f6d6bd4aee5468b60f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22248702"
---
# <a name="how-to-configure-scheduling-for-a-receive-location"></a>如何設定接收位置的排程
本主題描述如何使用 BizTalk Server 管理主控台來設定接收位置的排程屬性。 您可以指定想要接收位置開始和停止處理訊息的日期。 您也可以指定您想要接收位置在一天當中處理訊息的特定時間。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
### <a name="to-configure-scheduling-for-a-receive-location"></a>若要設定接收位置的排程  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，展開您要為其設定接收位置排程的 BizTalk 群組與 BizTalk 應用程式。  
  
3.  按一下**接收位置**，以滑鼠右鍵按一下接收位置，然後按一下**屬性**。  
  
4.  在左窗格中，按一下 **排程**下, 表中所述設定排程的屬性，然後按一下**確定**。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**開始日期**|選取此核取方塊，然後從下拉式日曆選取接收位置開始處理訊息的日期。 若要變更年份，請按一下以顯示的年份。|  
    |**停止日期**|選取此核取方塊，然後從下拉式日曆選取接收位置停止處理訊息的日期。 此屬性是選擇項。 若不指定停止日期，接收位置會一直處於作用中直至停用為止。|  
    |**啟用服務窗口**|選取此核取方塊，以只在指定的時間為一天，然後指定中的時間設定來接收訊息的接收位置**開始時間和停止時間**方塊。 若清除此核取方塊，接收位置便可隨時接收訊息。 預設值為 False (清除核取方塊)。|  
    |**開始時間**|指定接收位置應開始接收訊息的時間。 這個方塊是只有**啟用服務窗口**選取核取方塊。|  
    |**停止時間**|指定接收位置應停止接收訊息的時間。 這個方塊是只有**啟用服務窗口**選取核取方塊。|  
  
## <a name="see-also"></a>另請參閱  
 [管理接收位置](../core/managing-receive-locations.md)