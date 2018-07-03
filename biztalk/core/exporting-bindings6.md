---
title: 匯出 Bindings6 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- bindings, exporting
- exporting, bindings
ms.assetid: 052a429e-3237-44d4-8933-00aa5edfb212
caps.latest.revision: 22
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ee3d7df759dab97dca6a2e7677abb0bad15f8cd7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37022876"
---
# <a name="exporting-bindings"></a>匯出繫結
本節中的主題描述如何將 BizTalk 群組、組件或應用程式的繫結匯出至 .xml 檔案中 (繫結會定義主控件、傳送埠、傳送埠群組、接收埠、接收位置和合作對象如何與協調流程、管線、對應和結構描述產生關聯)。之後您可以將這些繫結從 .xml 檔案匯入到其他群組或應用程式。 匯入繫結會覆寫群組或應用程式中任何同名的現有繫結。 您也可以將繫結加入應用程式中，這樣並不會覆寫現有的繫結。 加入的繫結會在您匯入該應用程式之後才生效。  
  
 您可能會在下列實例中發現，使用繫結檔案時就不需要手動設定繫結，因此可以加速應用程式部署：  
  
- 將應用程式從一個部署環境移動到另一個部署環境。  
  
- 更新組件。  
  
- 將組件及其繫結一併部署到多個 BizTalk 群組。  
  
  如需針對這些用途使用繫結檔案的詳細資訊，請參閱[繫結檔案和應用程式部署](../core/binding-files-and-application-deployment.md)。  
  
  如需有關匯入及新增繫結的詳細資訊，請參閱 <<c0> [ 如何匯入到 BizTalk 群組的繫結](../core/how-to-import-bindings-into-a-biztalk-group.md)，[匯入繫結至 BizTalk 應用程式如何](../core/how-to-import-bindings-into-a-biztalk-application.md)，和[如何新增繫結應用程式的檔案](../core/how-to-add-a-binding-file-to-an-application2.md)。  
  
> [!IMPORTANT]
>  繫結檔案可能包含敏感性資料。 請務必採取步驟來確保檔案安全。  
  
> [!NOTE]
>  基於安全性理由，當您匯出繫結檔案時，BizTalk Server 會從該檔案移除繫結的密碼。 匯入繫結後，您必須重新設定密碼，傳送埠和接受位置才能正常運作。 您可以在 BizTalk Server 管理主控台的 [傳輸屬性] 對話方塊中，為傳送埠或接收位置設定密碼。 如需相關指示，請參閱 <<c0> [ 如何建立傳送埠](../core/how-to-create-a-send-port2.md)。 另請參閱[如何建立接收位置](../core/how-to-create-a-receive-location.md)。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [如何匯出 BizTalk 群組的繫結](../core/how-to-export-bindings-for-a-biztalk-group.md)  
  
-   [如何匯出 BizTalk 應用程式的繫結](../core/how-to-export-bindings-for-a-biztalk-application.md)  
  
-   [如何匯出 BizTalk 組件的繫結](../core/how-to-export-bindings-for-a-biztalk-assembly.md)  
  
-   [如何匯出 EDI-AS2 解決方案的繫結](../core/how-to-export-bindings-for-an-edi-as2-solution.md)