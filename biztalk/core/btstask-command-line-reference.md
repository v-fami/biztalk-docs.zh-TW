---
title: BTSTask 命令列參考 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3c350695-13e9-441a-9f1e-03cdc3e41328
caps.latest.revision: 30
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2c2de1e2e616b57d0cc8eda0cb9de9eae5c72d26
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22231918"
---
# <a name="btstask-command-line-reference"></a>BTSTask 命令列參考
本節主題提供 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 所附 BTSTask 命令列工具的參考資訊。 您可以使用 BTSTask 從命令列執行許多應用程式部署工作，如下所示：  
  
-   使用 AddApp 命令，將 BizTalk 應用程式新增至 BizTalk 管理資料庫。  
  
-   使用 AddResource 命令，將成品新增至應用程式。  
  
-   使用 ExportApp 命令，將應用程式及其成品匯出至 .msi 檔案。  
  
-   使用 ExportBindings 命令，將繫結資訊匯出至 .xml 檔案。  
  
-   使用 ImportApp 命令，從 .msi 檔案匯入應用程式。  
  
-   使用 ImportBindings 命令，從 .xml 檔案匯入繫結資訊。  
  
-   使用 ListApp 命令，列出包含在應用程式中的成品以及成品的本機唯一識別碼 (LUID)。  
  
-   使用 ListApps 命令，列出 BizTalk 群組在 BizTalk 管理資料庫中的所有應用程式。  
  
-   使用 ListPackage 命令，列出 .msi 檔案中的資源。  
  
-   使用 ListTypes 命令，列出 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 支援的所有成品類型。  
  
-   使用 RemoveApp 命令，從 BizTalk 管理資料庫及 BizTalk 管理主控台移除應用程式。  
  
-   使用 RemoveResource 命令，從應用程式移除成品。  
  
-   使用 UninstallApp 命令，從本機電腦解除安裝應用程式。  
  
> [!IMPORTANT]
>  在將於應用程式匯入期間執行的前置處理或後置處理指令碼中不得使用 BTSTask 命令。 若您這麼做，匯入就會失敗。 這是因為指令碼看不見匯入期間所做的變更。  
  
 此外，您還可以試著編輯 BTSTask 的主控台前景色彩。 如果主控台背景色彩是白色的，就難以判讀 BTSTask 主控台的輸出，因而需要修改主控台前景色彩。  
  
> [!NOTE]
>  當指令碼完成後，將傳回零 (0) 表示已順利完成，或傳回非零值表示失敗。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [AddApp 命令](../core/addapp-command.md)  
  
-   [AddResource 命令](../core/addresource-command.md)  
  
-   [ExportApp 命令](../core/exportapp-command.md)  
  
-   [ExportBindings 命令](../core/exportbindings-command.md)  

- [ExportParties 命令](../core/exportparties-command.md)

- [ExportSettings 命令](../core/exportsettings-command.md)
  
-   [ImportApp 命令](../core/importapp-command.md)  
  
-   [ImportBindings 命令](../core/importbindings-command.md)  

- [ImportParties 命令](../core/importparties-command.md)

- [ImportSettings 命令](../core/importsettings-command.md)
  
-   [ListApp 命令](../core/listapp-command.md)  
  
-   [ListApps 命令](../core/listapps-command.md)  
  
-   [ListPackage 命令](../core/listpackage-command.md)  
  
-   [ListTypes 命令](../core/listtypes-command.md)  
  
-   [RemoveApp 命令](../core/removeapp-command.md)  
  
-   [RemoveResource 命令](../core/removeresource-command.md)  
  
-   [UninstallApp 命令](../core/uninstallapp-command.md)  
  
-   [如何編輯 BTSTask 的主控台色彩](../core/how-to-edit-the-console-colors-for-btstask.md)