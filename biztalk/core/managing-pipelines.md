---
title: "管理管線 |Microsoft 文件"
description: "若要啟用追蹤和傳送埠上的管線屬性，或在 BizTalk Server 接收位置的快速連結"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d60b54e0-0a5a-4264-b0e5-96bb187d782b
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0edfbdd97e134abc6f153acf136ff62a979f8b0c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="managing-pipelines"></a>管理管線

## <a name="overview"></a>概觀
本節提供相關指示，說明如何使用 BizTalk Server 管理主控台管理 BizTalk 群組中的管線。 您可以設定事件和訊息追蹤，也可以設定特定傳送埠或接收位置的管線屬性。  
  
 管線會對內送和外寄訊息執行動作，例如將訊息從原生格式轉換成 XML、加密或解密資料、執行屬性升級等等。  
  
 您不能將管線個別新增至應用程式；管線會在下列情況中新增至應用程式：  
  
-   當您將加入包含應用程式，管線的 BizTalk 組件中所述[如何將 BizTalk 組件新增至應用程式](../core/how-to-add-a-biztalk-assembly-to-an-application.md)。  
  
-   當您匯入.msi 檔案包含包含管線的 BizTalk 組件中所述的應用程式[如何匯入 BizTalk 應用程式](../core/how-to-import-a-biztalk-application.md)。  
  
-   當開發人員應用程式組件部署到包含從 Visual Studio 中，管線中所述[從到 BizTalk 應用程式的 Visual Studio 部署 BizTalk 組件](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)。  
  
 如需管線的背景資訊，請參閱[管線](../core/pipelines.md)。 如需開發管線的詳細資訊，請參閱[管線使用管線設計師建立](../core/creating-pipelines-using-pipeline-designer.md)。  
  
> [!NOTE]
>  您可以使用 Microsoft Windows Management Instrumentation (WMI) 物件模型，建立和執行會自動化系統管理工作的指令碼。 如需使用 WMI 的詳細資訊，請參閱**WMI 類別參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
  
## <a name="next-steps"></a>後續的步驟
  
-   [設定管線追蹤](../core/how-to-configure-tracking-for-a-pipeline.md)  
  
-   [設定傳送埠的每個執行個體管線屬性](../core/how-to-configure-per-instance-pipeline-properties-for-a-send-port.md)  
  
-   [設定每個執行個體管線屬性的接收位置](../core/how-to-configure-per-instance-pipeline-properties-for-a-receive-location.md)