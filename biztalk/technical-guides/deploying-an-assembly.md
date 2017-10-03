---
title: "部署組件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 65f8ee21-0e52-4a74-b114-864a3069659c
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 73112fd9efb536452b8641faa976f42bb892b67c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="deploying-an-assembly"></a>部署組件
部署組件會建置組件並匯入，以及協調流程、 管線、 結構描述和對應 （成品），它包含到本機 BizTalk 管理資料庫。 一開始，這是在開發環境中。  
  
 部署也會將組件與您在 Visual Studio 中的專案屬性中所指定的 BizTalk 應用程式產生關聯。 在部署解決方案以後，您便能夠從 [BizTalk Server 管理主控台] 內，或是使用 BTSTask 命令列工具，來檢視和管理已部署的組件及其成品。 您可以管理成品可以個別或應用程式中予以分組。  
  
## <a name="deploying-an-assembly"></a>部署組件  
 您可以下列方式加入應用程式組件：  
  
-   將組件部署到應用程式的 Visual Studio 環境中  
  
-   手動新增到應用程式的 BizTalk Server 管理主控台中的 BizTalk Server 組件  
  
-   使用從命令列指令碼，將 BizTalk 組件加入至應用程式  
  
-   從 BizTalk Server 管理主控台從其他應用程式移動 BizTalk Server 組件  
  
 如需將組件加入至應用程式的詳細資訊，請參閱[從到 BizTalk 應用程式的 Visual Studio 部署 BizTalk 組件](http://go.microsoft.com/fwlink/?LinkID=154719)(http://go.microsoft.com/fwlink/?LinkID=154719)。  
  
## <a name="redeploying-assemblies"></a>重新部署組件  
 在開發和偵錯您的 BizTalk 組件，您可能需要將其重新佈署多次。 BizTalk Server 提供的簡易機制，重新部署。 如果您重新部署組件，而不變更版本號碼，您可以使用重新部署屬性。 BizTalk Server 將會自動執行所有步驟，重新部署您的組件。  
  
 如需有關重新部署組件的詳細資訊，請參閱[如何重新部署 BizTalk 組件從 Visual Studio](http://go.microsoft.com/fwlink/?LinkID=154720) (http://go.microsoft.com/fwlink/?LinkID=154720)。  
  
### <a name="best-practices-for-redeploying-an-assembly"></a>重新部署組件的最佳作法  
 **您必須在 GAC 中安裝新的組件**  
  
-   當您重新部署組件時，所以您必須一律在全域組件快取 (GAC) 中安裝新版的組件。 您可以在重新部署後執行此作業。 如需詳細資訊，請參閱[如何在 GAC 中安裝組件](http://go.microsoft.com/fwlink/?LinkID=154828)(http://go.microsoft.com/fwlink/?LinkID=154828)。  
  
 **您應該永遠重新部署方案層級相依性存在時**  
  
-   如果解決方案中有多個組件，而且此解決方案中的一或多個組件相依於要重新部署的組件，則您必須在解決方案層級重新部署組件。 這是因為 BizTalk Server 時重新部署組件在專案層級，將會停止、 取消登錄、 解除繫結，並移除這個組件所依存的任何相依或此組件上的所有組件中的所有成品。 BizTalk Server 不會執行部署、繫結、登錄和啟動成品的額外步驟。 不過，當您重新部署整個解決方案時，BizTalk Server 會自動執行必要步驟，根據成品的相依性，解除部署和重新部署解決方案中的所有成品。  
  
 **您可能需要手動重新部署相依組件**  
  
-   BizTalk Server 固定會解除部署相依組件時，它會解除部署組件，但在下列情況下，您必須採取其他步驟，部署、 繫結，並且登錄之後重新部署組件所在的每個相依組件中的成品組件而定：  
  
     如果您在專案層級重新部署組件，而且相同解決方案中的另一個組件相依於此組件。  
  
     如果您在解決方案層級重新部署組件，但不同解決方案中存在相依組件。  
  
 **您必須重新啟動主控件執行個體**  
  
-   當您重新部署包含協調流程的組件而不變更組件版本號碼時，BizTalk 管理資料庫中的現有組件會遭到覆寫。 不過，在變更生效之前，您必須重新啟動協調流程所繫結之主控件的每個主控件執行個體。 您可以指定選項，在重新部署組件時，自動重新啟動本機電腦上的所有主控件執行個體。  
  
     當您重新部署包含協調流程的組件而不變更組件版本號碼時，BizTalk 管理資料庫中的現有組件會遭到覆寫。 不過，在變更生效之前，您必須重新啟動協調流程所繫結之主控件的每個主控件執行個體。 您可以指定選項，在重新部署組件時，自動重新啟動本機電腦上的所有主控件執行個體。 如需部署屬性的詳細資訊，請參閱[如何在 Visual Studio 中設定部署屬性](http://go.microsoft.com/fwlink/?LinkID=154718)(http://go.microsoft.com/fwlink/?LinkID=154718)。  
  
     您也可以手動即可停止和啟動每個主控件執行個體。 如需停止和啟動主控件執行個體的詳細資訊，請參閱[如何停止主控件執行個體](http://go.microsoft.com/fwlink/?LinkID=154829)(http://go.microsoft.com/fwlink/?LinkID = 154829) 和[如何啟動主控件執行個體](http://go.microsoft.com/fwlink/?LinkID=154830)(http://go.microsoft.com/fwlink/?LinkID = 154830)。