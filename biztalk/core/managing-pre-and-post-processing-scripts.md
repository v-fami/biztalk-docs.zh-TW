---
title: "管理前置或後置處理指令碼 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 107ada12-fef2-4b56-8ff8-228c13761104
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 18926a0c51e5ab5f65b32373d20b2931ccaa627d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="manage-pre--and-post-processing-scripts"></a>管理前置或後置處理指令碼

## <a name="overview"></a>概觀
本節提供使用 BizTalk Server 管理主控台或 BTSTask 命令列工具以管理前置或後置處理指令碼的指示。 您可以建立想要在匯入、安裝或解除安裝 (移除) BizTalk 應用程式時執行的指令碼，然後將該指令碼加入至應用程式。 當您加入指令碼時，請指定它是前置處理指令碼 (會在匯入或安裝前，以及在解除安裝後執行)，還是後置處理指令碼 (會在匯入或安裝後，以及在解除安裝前執行)。  
  
 如果您在匯出應用程式時選取指令碼，則該指令碼會包含在應用程式的 .msi 檔案中。 當您安裝、解除安裝或匯入應用程式時，指令碼就會依照您撰寫指令碼的方式自動執行。 如需有關建立和使用指令碼的詳細資訊，請參閱[使用前置和後置處理指令碼，以自訂應用程式部署](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md)。  
  
> [!NOTE]
>  您可以使用 Microsoft Windows Management Instrumentation (WMI) 物件模型，建立和執行會自動化系統管理工作的指令碼。 如需使用 WMI 的詳細資訊，請參閱**WMI 類別參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
  
## <a name="next-steps"></a>後續的步驟 
  
-   [應用程式中加入前置或後置處理指令碼](../core/how-to-add-a-pre-or-post-processing-script-to-an-application.md)  
  
-   [變更前置或後置處理指令碼的目的地位置](../core/how-to-change-the-destination-location-of-a-pre-or-post-processing-script.md)  
  
-   [從應用程式移除前置或後置處理指令碼](../core/how-to-remove-a-pre-or-post-processing-script-from-an-application.md)