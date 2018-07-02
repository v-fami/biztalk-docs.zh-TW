---
title: 如何啟動和停止 BizTalk 應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- starting
- starting, applications
- managing [applications], starting
- managing [applications], stopping
- applications, starting
- stopping, applications
- applications, stopping
- stopping
ms.assetid: f9f83e99-a1e2-4dfd-b3be-60d3ec2cbcc4
caps.latest.revision: 20
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 979de8e8614d05ba97223e43c90ed0ec83cefc4a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36968727"
---
# <a name="how-to-start-and-stop-a-biztalk-application"></a>如何啟動和停止 BizTalk 應用程式
本主題描述如何使用 [BizTalk Server 管理] 主控台來啟動及停止 BizTalk 應用程式。  
  
 您可以啟動應用程式之前，繫結必須設定、 包含的所有協調流程中所述[如何設定協調流程繫結](../core/how-to-configure-bindings-for-an-orchestration.md)。  
  
 在啟動應用程式時，可以選取一個或多個下列的選項：  
  
-   登錄並啟動所有的協調流程。  
  
-   登錄並啟動所有的傳送埠。  
  
-   登錄並啟動所有的傳送埠群組。  
  
-   啟用所有的接收位置。  
  
-   啟動所有關聯的主控件執行個體。  
  
-   繼續擱置的執行個體。  
  
-   部署所有原則。  
  
> [!NOTE]
>  只會自動部署應用程式中已發佈的原則。 如果原則尚未發佈，則不會加以部署。  
  
 在停止應用程式時，可以選取一個或多個下列的選項：  
  
-   **部分停止-允許正在執行個體，以繼續。** ：這個選項會停用應用程式中的所有接收位置，但保留所有其他成品的先前狀態。 如此可以讓正在執行的執行個體完成系統中目前訊息的處理。 請注意，如果訊息交易需要多項輸入，則使用這個選項可能無法完成。  
  
-   **部分停止-擱置正在執行的執行個體。** ：這個選項會停用應用程式中的所有接收位置，並停止應用程式中的所有協調流程和傳送埠。 它不會取消登錄或解除部署任何成品。 如果想要暫停應用程式，請使用此選項。  
  
-   **完全停止-終止執行個體。** ：這個選項會停用應用程式中的所有接收位置，並停止及取消登錄所有的協調流程和傳送埠，並解除部署所有的原則。 如果想要完全解除部署應用程式，請使用此選項。 請注意，仍在處理訊息的所有執行中執行個體都不會完成處理作業。 如需詳細資訊，請參閱 <<c0> [ 解除部署 BizTalk 應用程式](../core/undeploying-biztalk-applications.md)。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。 BizTalk 操作員可以執行部分停止，但無法執行完全停止。 此外，如果所有成員都已登錄，則 BizTalk 操作員可以啟動應用程式。 如需詳細的權限的詳細資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
### <a name="to-start-or-stop-a-biztalk-application"></a>如何啟動和停止 BizTalk 應用程式  
  
1. 按一下 **開始**，指向**所有程式**，指向[!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。  
  
2. 在主控台樹狀目錄中，依序展開**BizTalk Server 管理**，展開 BizTalk 群組，然後再展開**應用程式**。  
  
3. 以滑鼠右鍵按一下您想要啟動或停止，然後按一下 BizTalk 應用程式**開始**或是**停止**。  
  
4. 選取啟動或停止選項，以及按一下**開始**或是**停止**。  
  
## <a name="see-also"></a>另請參閱  
 [部署和管理 BizTalk 應用程式](../core/deploying-and-managing-biztalk-applications.md)   
 [更新 BizTalk 應用程式](../core/updating-biztalk-applications.md)