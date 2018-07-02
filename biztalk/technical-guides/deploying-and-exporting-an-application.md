---
title: 部署及匯出應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4106a0a7-878d-4052-8eca-02d546233048
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 26c5a32151854bff981d01e4135a1c67e1c4e8ca
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36965959"
---
# <a name="deploying-and-exporting-an-application"></a>部署及匯出應用程式
本章節包含有關如何執行所需的步驟中部署 BizTalk 應用程式的詳細的資訊。 在本節中主題也支援下列檢查清單：  
  
- [檢查清單： 部署應用程式](../technical-guides/checklist-deploying-an-application.md)，但會示範如何部署應用程式的開發環境中，將它匯出至.msi 檔案，然後將它匯入到生產環境中從.msi 檔案。  
  
- [檢查清單： 從另一個應用程式匯出繫結](../technical-guides/checklist-exporting-bindings-from-one-application-to-another.md)，但會示範如何從應用程式中的另一個應用程式匯出繫結的開發或生產環境。  
  
  您可以使用下列工具來部署和管理 BizTalk 應用程式：  
  
|                             工具                             |                                                                                                                                                                                                                                                                                                                                                                                                                                 使用                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|--------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|            BizTalk Server 管理主控台             | 從這個圖形化使用者介面中，您可以執行的所有部署和管理 BizTalk 應用程式，包括下列作業：<br /><br /> 啟動匯入、 安裝和匯出精靈<br />-新增和移除應用程式的成品，以及進行其他修改應用程式<br />的產生 BizTalk 應用程式的 BizTalk Server.msi 檔案<br />-從.msi 檔案安裝到電腦上的應用程式，或從.msi 檔案匯入應用程式，到另一個 BizTalk 群組<br />-應用程式的繫結從檔案匯入繫結<br /><br /> 如需有關 [管理] 主控台的詳細資訊，請參閱[使用 BizTalk Server 管理主控台](http://go.microsoft.com/fwlink/?LinkID=154689)(<http://go.microsoft.com/fwlink/?LinkID=154689>)。 |
|                  BTSTask 命令列工具                   |                                                                                                                                                                                                                                                                                                  您可以從命令列執行許多應用程式管理工作。 如需有關命令列工具的詳細資訊，請參閱 < [BTSTask 命令列參考](http://go.microsoft.com/fwlink/?LinkId=155003)(<http://go.microsoft.com/fwlink/?LinkId=155003>)。                                                                                                                                                                                                                                                                                                   |
|              指令碼處理和可程式性 Api              |                                                                                                                                                                                                                                                           您可以使用 Microsoft Windows Management Instrumentation (WMI) 或 BizTalk 總管物件模型，建立和執行會自動化許多應用程式管理工作的指令碼。 如需指令碼的詳細資訊，請參閱[WMI 類別參考](http://go.microsoft.com/fwlink/?LinkId=155004)(<http://go.microsoft.com/fwlink/?LinkId=155004>)。                                                                                                                                                                                                                                                           |
| [!INCLUDE[btsVStudio2008](../includes/btsvstudio2008-md.md)] |                                                                                                                                                                                                您可以在 Visual Studio 中建立 BizTalk 組件、 使用 部署 命令會自動將它們部署到 BizTalk 應用程式和設定從 Visual Studio 內的應用程式成品使用 BizTalk 總管 中。 如需 Visual Studio 內運作的詳細資訊，請參閱[從 BizTalk 應用程式的 Visual Studio 部署 BizTalk 組件](http://go.microsoft.com/fwlink/?LinkID=154719)(<http://go.microsoft.com/fwlink/?LinkID=154719>)。                                                                                                                                                                                                |
  
## <a name="in-this-section"></a>本節內容  
  
-   [建立應用程式](../technical-guides/creating-an-application.md)  
  
-   [部署組件](../technical-guides/deploying-an-assembly.md)  
  
-   [將成品新增至應用程式](../technical-guides/adding-artifacts-to-an-application.md)  
  
-   [如何將應用程式匯出至 .msi 檔案](../technical-guides/how-to-export-an-application-to-an-msi-file.md)  
  
-   [如何將繫結匯出至繫結檔案](../technical-guides/how-to-export-bindings-to-a-binding-file.md)  
  
-   [如何將繫結檔案新增至應用程式 1](../technical-guides/how-to-add-a-binding-file-to-an-application1.md)  
  
-   [如何從 .msi 檔案匯入應用程式](../technical-guides/how-to-import-an-application-from-an-msi-file.md)  
  
-   [如何安裝應用程式](../technical-guides/how-to-install-an-application.md)  
  
-   [如何從繫結檔案匯入繫結](../technical-guides/how-to-import-bindings-from-a-binding-file.md)  
  
-   [測試應用程式](../technical-guides/testing-an-application.md)  
  
-   [如何新增應用程式的參考](../technical-guides/how-to-add-a-reference-to-an-application.md)