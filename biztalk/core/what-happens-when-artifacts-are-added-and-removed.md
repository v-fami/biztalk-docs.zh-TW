---
title: 加入和移除成品時，會發生什麼情況 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- creating, artifacts
- artifacts, deleting
- artifacts, creating
- deleting, artifacts
ms.assetid: 811166ba-3ff4-4224-9d84-a2f4ed31bf4d
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 464964714993205ef65d5a67de3399935f79320f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22288878"
---
# <a name="what-happens-when-artifacts-are-added-and-removed"></a>加入和移除成品時發生的狀況
本主題說明在應用程式中加入成品時發生的狀況。 您可以使用 BizTalk Server 管理主控台或 BTSTask 命令列工具，將以檔案為基礎的成品加入至應用程式。 以檔案為基礎的成品包含下列類型：  
  
-   BizTalk 組件  
  
-   非 BizTalk 專屬的 .NET 組件  
  
-   繫結 (.xml) 檔案  
  
-   COM 元件  
  
-   憑證  
  
-   前置或後置處理指令碼  
  
-   原則  
  
-   臨機操作檔案，例如讀我檔案  
  
-   虛擬目錄  
  
-   BAM 成品  
  
> [!NOTE]
>  傳送埠、傳送埠群組、接收位置和接收埠不是以檔案為基礎的成品，無法加入至應用程式。 您必須在指定的應用程式中建立這些成品。 必要時，再將它們移至另一個應用程式。 協調流程、結構描述、對應和管線全部會做為包含組件的一部分，來進行部署和管理。  
  
 當您將成品加入至應用程式時，成品會與 BizTalk 管理資料庫中的應用程式相關聯，而且成品以檔案為基礎的資料也會加入至管理資料庫中。 這可讓您輕鬆地將應用程式和成品從一個 BizTalk 群組傳輸至另一個群組，因為您可以將應用程式和成品資料從管理資料庫匯出至 .msi 檔案，然後再將它匯入至另一個 BizTalk 群組中的管理資料庫。  
  
 當您將繫結檔案加入至應用程式時，可以指定要套用繫結的目標部署環境。 與匯入繫結檔案不同，加入繫結檔案不會套用其繫結。  
  
 如果您指定這個選項，當您將 BizTalk 組件或 .NET 組件加入至應用程式時，便會將組件加入至全域組件快取 (GAC) 中。  
  
## <a name="see-also"></a>另請參閱  
 [會發生什麼事成品至應用程式部署期間](../core/what-happens-to-artifacts-during-application-deployment.md)   
 [如何建立或新增成品](../core/how-to-create-or-add-an-artifact.md)   
 [如何匯入 BizTalk 應用程式](../core/how-to-import-a-biztalk-application.md)   
 [如何匯出 BizTalk 應用程式](../core/how-to-export-a-biztalk-application.md)