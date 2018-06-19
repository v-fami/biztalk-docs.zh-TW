---
title: 管理資源 |Microsoft 文件
description: 工作與組件、 指令碼、 憑證、 繫結檔案和其他 BizTalk Server 中使用 btstask 」 或 「 BizTalk 管理
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b478ef2e-1363-4c2c-a4b7-6a582a6b33a5
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 07248c1689adf6b6474fd8e1f3e01f2d660becdc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22262438"
---
# <a name="manage-resources"></a>管理資源

## <a name="overview"></a>概觀
本節中的主題提供如何使用 BizTalk Server 管理主控台或 BTSTask 命令列工具，在將 BizTalk Server 資源部署至 BizTalk 群組後管理這些資源的指示。 資源包括下列成品類型：  
  
-   BizTalk 組件  
  
-   前置或後置處理指令碼  
  
-   .NET 組件  
  
-   COM 元件  
  
-   憑證  
  
-   臨機操作檔案  
  
-   BAM 定義  
  
-   繫結檔案  
  
-   虛擬目錄  
  
> [!NOTE]
>  您可以使用 Microsoft Windows Management Instrumentation (WMI) 物件模型，建立和執行會自動化系統管理工作的指令碼。 如需使用 WMI 的詳細資訊，請參閱**WMI 類別參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
  
> [!NOTE]
>  請勿將具有相同名稱 (不論大小寫) 的多個資源新增到 BizTalk Server 群組。 不支援將具有相同的名稱的多個資源新增到 BizTalk Server 群組，即使在 BizTalk Server 管理資料庫儲存在設定為使用二進位定序並支援區分大小寫功能的 SQL Server 上也一樣。  
  
## <a name="next-steps"></a>後續的步驟
  
-   [管理 BizTalk 組件](../core/managing-biztalk-assemblies.md)  
  
-   [管理前置或後置處理指令碼](../core/managing-pre-and-post-processing-scripts.md)  
  
-   [管理.NET 組件、 憑證和其他資源](../core/managing-net-assemblies-certificates-and-other-resources.md)  
  
-   [重新整理資源](../core/how-to-refresh-a-resource.md)