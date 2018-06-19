---
title: 管理.NET 組件、 憑證和其他資源 |Microsoft 文件
description: 若要加入繫結檔案、 憑證、 組件、 虛擬目錄、 檔案和多個 BizTalk Server 中的連結
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: efe27a11-19d8-4eb3-9f8c-f4336e4c3d66
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fdb74762bdf08e6e9e2a79650a26dedb0915ea8f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22262726"
---
# <a name="manage-net-assemblies-certificates-and-other-resources"></a>管理.NET 組件、 憑證和其他資源

## <a name="overview"></a>概觀
本節提供相關指示，說明如何使用 BizTalk Server 管理主控台和 BTSTask 命令列工具來管理下列類型的 BizTalk 應用程式資源成品。 這些資源成品無法從 Visual Studio 自動部署到 BizTalk 應用程式，所以必須以手動方式將它們新增至應用程式。 不過，一旦新增至應用程式後，您就可以將這些資源成品當做一個單位，搭配應用程式和應用程式的其他成品而進行匯入、匯出及安裝。  
  
-   **檔案。** 您可以包含特定的檔案，例如讀我檔案。 當您在安裝應用程式時，檔案會複製到安裝資料夾。  
  
-   **憑證。** 您可以將憑證檔案新增至應用程式，如此就可以將憑證封裝於應用程式中，從一個 BizTalk 群組傳輸到另一個群組。 您要將憑證指定給傳送埠和接收位置，以確認識別並建立安全的連結。  
  
-   **COM 和 COM + 元件。** 您可以包含 Managed COM 和 Managed COM+ 元件，以在 BizTalk 應用程式中提供其他功能。  
  
-   **.NET 組件。** 您可以在 BizTalk 應用程式中，包含並非確實為 BizTalk 組件的 .NET 組件 (BizTalk 組件是包含 BizTalk 協調流程、管線、結構描述或對應的 .NET 組件)。  
  
-   **BAM 定義檔案。** 若要簡化 BAM 的部署，可以建立 BizTalk 應用程式，然後再對該應用程式新增 BAM 定義。 接下來可以使用 BizTalk 應用程式部署功能，將 BAM 定義部署到不同的環境中。  
  
-   **繫結檔案。** 您可以將繫結檔案新增至應用程式，這樣可以更輕鬆快速地將應用程式從一個部署環境移至另一個部署環境。  
  
-   **虛擬目錄。** 您可以將虛擬目錄新增至應用程式，讓虛擬目錄可以和應用程式一起部署。  
  
> [!NOTE]
>  您可以使用 Microsoft Windows Management Instrumentation (WMI) 物件模型，建立和執行會自動化系統管理工作的指令碼。 如需使用 WMI 的詳細資訊，請參閱**WMI 類別參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
  
## <a name="next-steps"></a>後續的步驟
  
-   [將檔案加入應用程式](../core/how-to-add-a-file-to-an-application.md)  
  
-   [將憑證新增至應用程式](../core/how-to-add-a-certificate-to-an-application.md)  
  
-   [將 COM 元件加入至應用程式](../core/how-to-add-a-com-component-to-an-application.md)  
  
-   [應用程式中加入.NET 組件](../core/how-to-add-a-net-assembly-to-an-application.md)  
  
-   [應用程式中加入 BAM 成品](../core/how-to-add-a-bam-artifact-to-an-application.md)  
  
-   [應用程式中加入繫結檔案](../core/how-to-add-a-binding-file-to-an-application2.md)  
  
-   [應用程式中加入虛擬目錄](../core/how-to-add-a-virtual-directory-to-an-application.md)  
  
-   [修改.NET 組件、 COM 元件、 檔案或 BAM 成品的部署選項](../core/modify-deployment-options-of-net-assembly-com-component-file-bam-artifact.md)  
  
-   [移除應用程式的.NET 組件、 憑證或其他資源成品](../core/remove-a-net-assembly-certificate-or-resource-artifact-from-an-application.md)