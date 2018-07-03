---
title: 管理傳送埠與傳送埠群組 |Microsoft Docs
description: 連結來建立、 設定、 登錄、 取消登錄和啟動和停止 BizTalk Server 中的傳送埠
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: db45f9f9-b32a-4b9c-a3bf-8c271d0f0cf9
caps.latest.revision: 24
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6b3fe64a46ec4dd80d278e36f91406db0c431972
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37015751"
---
# <a name="manage-send-ports-and-send-port-groups"></a>管理傳送埠與傳送埠群組

## <a name="overview"></a>概觀
本節提供使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台，在 BizTalk 應用程式中建立、設定和管理傳送埠與傳送埠群組的相關指示。 傳送埠會指定傳送訊息所至以及選擇性接收回應的位置。 每當訊息傳送至傳送埠，建立傳送埠服務的新執行個體，也就所謂*服務執行個體*。  
  
 傳送埠群組是傳送埠的邏輯群組。 將訊息傳送至傳送埠群組時，該訊息會路由至所有相關的傳送埠。  如需傳送埠與傳送埠群組的背景資訊，請參閱[傳送埠與傳送埠群組](../core/send-ports-and-send-port-groups.md)。  
  
> [!NOTE]
>  您可以使用 Microsoft Windows Management Instrumentation (WMI) 物件模型，建立和執行會自動化系統管理工作的指令碼。 如需使用 WMI 的詳細資訊，請參閱**WMI 類別參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
> 
> [!NOTE]
>  開發 BizTalk 應用程式時，開發人員可以使用 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中的 BizTalk 設計工具 (例如協調流程設計師)，來建立和設定傳送埠與傳送埠群組。 如需詳細資訊，請參閱 <<c0> [ 協調流程中使用連接埠](../core/using-ports-in-orchestrations.md)。  
  
## <a name="next-steps"></a>後續的步驟
  
-   [建立和設定傳送埠](../core/creating-and-configuring-send-ports.md)  
  
-   [建立和設定傳送埠群組](../core/creating-and-configuring-send-port-groups.md)  
  
-   [登錄傳送埠或傳送埠群組](../core/how-to-enlist-a-send-port-or-send-port-group.md)  
  
-   [取消登錄傳送埠或傳送埠群組](../core/how-to-unenlist-a-send-port-or-send-port-group.md)  
  
-   [啟動傳送埠或傳送埠群組](../core/how-to-start-a-send-port-or-send-port-group.md)  
  
-   [停止傳送埠或傳送埠群組](../core/how-to-stop-a-send-port-or-send-port-group.md)