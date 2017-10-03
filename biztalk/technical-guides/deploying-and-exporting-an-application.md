---
title: "部署和應用程式匯出 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4106a0a7-878d-4052-8eca-02d546233048
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b33762f50f32dda58f1453fde7be37bc959af6aa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="deploying-and-exporting-an-application"></a>部署及匯出應用程式
本節包含有關如何執行所需的步驟，將 BizTalk 應用程式部署的詳細的資訊。 本節中的主題也支援下列檢查清單：  
  
-   [檢查清單： 部署應用程式](../technical-guides/checklist-deploying-an-application.md)，其示範如何部署開發環境中的應用程式，將它匯出至.msi 檔案，然後將它匯入到生產環境中，從.msi 檔案。  
  
-   [檢查清單： 匯出繫結到另一個應用程式從](../technical-guides/checklist-exporting-bindings-from-one-application-to-another.md)，其示範如何從應用程式中的另一個應用程式匯出繫結在開發或實際執行環境。  
  
 您可以使用下列工具來部署和管理 BizTalk 應用程式：  
  
|工具|使用|  
|----------|---------|  
|BizTalk Server 管理主控台|從這個圖形化使用者介面，您可以執行的所有部署和管理 BizTalk 應用程式，包括下列作業：<br /><br /> 啟動匯入、 安裝和匯出精靈<br />-加入和移除應用程式的成品，以及進行其他修改應用程式<br />的產生 BizTalk 應用程式的 BizTalk Server.msi 檔案<br />-從.msi 檔案安裝應用程式的電腦上，或從.msi 檔案將應用程式匯入到另一個 BizTalk 群組<br />-從匯入應用程式的繫結的繫結檔案<br /><br /> 如需管理主控台的詳細資訊，請參閱[使用 BizTalk Server 管理主控台](http://go.microsoft.com/fwlink/?LinkID=154689)(http://go.microsoft.com/fwlink/?LinkID=154689)。|  
|BTSTask 命令列工具|您可以從命令列執行許多應用程式管理工作。 如需命令列工具的詳細資訊，請參閱[BTSTask 命令列參考](http://go.microsoft.com/fwlink/?LinkId=155003)(http://go.microsoft.com/fwlink/?LinkId=155003)。|  
|指令碼和程式設計 Api|您可以使用 Microsoft Windows Management Instrumentation (WMI) 或 BizTalk 總管物件模型，建立和執行會自動化許多應用程式管理工作的指令碼。 如需指令碼的詳細資訊，請參閱[WMI 類別參考](http://go.microsoft.com/fwlink/?LinkId=155004)(http://go.microsoft.com/fwlink/?LinkId=155004)。|  
|[!INCLUDE[btsVStudio2008](../includes/btsvstudio2008-md.md)]|您可以在 Visual Studio 中建立 BizTalk 組件、 使用 部署 命令會自動將它們部署到 BizTalk 應用程式和設定從 Visual Studio 中的應用程式成品使用 BizTalk 總管 中。 如需 Visual Studio 中運作的詳細資訊，請參閱[從到 BizTalk 應用程式的 Visual Studio 部署 BizTalk 組件](http://go.microsoft.com/fwlink/?LinkID=154719)(http://go.microsoft.com/fwlink/?LinkID=154719)。|  
  
## <a name="in-this-section"></a>本節內容  
  
-   [建立應用程式](../technical-guides/creating-an-application.md)  
  
-   [部署組件](../technical-guides/deploying-an-assembly.md)  
  
-   [將成品新增至應用程式](../technical-guides/adding-artifacts-to-an-application.md)  
  
-   [如何匯出至.msi 檔案的應用程式](../technical-guides/how-to-export-an-application-to-an-msi-file.md)  
  
-   [如何匯出繫結至繫結檔案](../technical-guides/how-to-export-bindings-to-a-binding-file.md)  
  
-   [如何將繫結檔案新增至 Application1](../technical-guides/how-to-add-a-binding-file-to-an-application1.md)  
  
-   [如何從.msi 檔案匯入應用程式](../technical-guides/how-to-import-an-application-from-an-msi-file.md)  
  
-   [如何安裝應用程式](../technical-guides/how-to-install-an-application.md)  
  
-   [如何從繫結檔案匯入繫結](../technical-guides/how-to-import-bindings-from-a-binding-file.md)  
  
-   [測試應用程式](../technical-guides/testing-an-application.md)  
  
-   [如何將參考加入至應用程式](../technical-guides/how-to-add-a-reference-to-an-application.md)