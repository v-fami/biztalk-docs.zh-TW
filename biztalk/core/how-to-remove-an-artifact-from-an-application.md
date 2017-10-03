---
title: "如何從應用程式移除成品 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- artifacts, deleting
- applications, modifying
- applications, artifacts
- modifying, applications
- deleting, artifacts
ms.assetid: c528be0b-0b1a-4c5f-acd2-7355da91a253
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 25d57c41311cef12a33685dcc4c8aacd85290b7f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-remove-an-artifact-from-an-application"></a>如何從應用程式移除成品
移除或刪除成品後，該成品便會從 BizTalk Server 資料庫刪除，因此不會再出現在管理主控台或 BTSTask ListApp 命令所產生的應用程式成品清單中。 這項作業並不會將 Windows 登錄、全域組件快取 (GAC)、虛擬目錄或檔案系統等位置中的成品移除 (如果有的話)。 如果是只存在 BizTalk 管理資料庫的傳送埠、傳送埠群組、接收埠和接收位置，這項作業會將成品完全刪除。 如需背景資訊，請參閱[什麼發生當成品新增和移除](../core/what-happens-when-artifacts-are-added-and-removed.md)  
  
 移除或刪除成品對應用程式功能所造成的影響，會隨著成品類型而有所不同。 如需移除或刪除特定成品類型的詳細資訊與指示，請參閱下列適當主題：  
  
-   [如何從應用程式移除協調流程](../core/how-to-remove-an-orchestration-from-an-application.md)  
  
-   [如何刪除傳送埠](../core/how-to-delete-a-send-port.md)  
  
-   [如何刪除傳送埠群組](../core/how-to-delete-a-send-port-group.md)  
  
-   [如何刪除接收埠](../core/how-to-delete-a-receive-port.md)  
  
-   [如何刪除接收位置](../core/how-to-delete-a-receive-location.md)  
  
-   [如何從應用程式和 BizTalk 群組移除原則](../core/how-to-remove-a-policy-from-an-application-and-the-biztalk-group.md)  
  
-   [如何從應用程式移除結構描述](../core/how-to-remove-a-schema-from-an-application.md)  
  
-   [如何從應用程式中移除對應](../core/how-to-remove-a-map-from-an-application.md)  
  
-   [如何從應用程式移除 BizTalk 組件](../core/how-to-remove-a-biztalk-assembly-from-an-application.md)  
  
-   [如何從應用程式移除前置或後置處理指令碼](../core/how-to-remove-a-pre-or-post-processing-script-from-an-application.md)  
  
-   [如何從應用程式移除.NET 組件、 憑證或其他資源成品](../core/remove-a-net-assembly-certificate-or-resource-artifact-from-an-application.md)  
  
## <a name="see-also"></a>另請參閱  
 [建立和修改 BizTalk 應用程式](../core/creating-and-modifying-biztalk-applications.md)   
 [RemoveResource 命令](../core/removeresource-command.md)