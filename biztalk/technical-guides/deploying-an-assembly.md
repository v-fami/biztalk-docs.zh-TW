---
title: 部署組件 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 65f8ee21-0e52-4a74-b114-864a3069659c
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5fb363b6060b0c06436b36202100e855062c026f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36984767"
---
# <a name="deploying-an-assembly"></a>部署組件
部署組件建置的組件，並匯入，以及協調流程、 管線、 結構描述，以及它包含到本機 BizTalk 管理資料庫的對應 （成品）。 一開始，這是在開發環境中。  
  
 部署也會將組件與您在 Visual Studio 內專案屬性中指定的 BizTalk 應用程式產生關聯。 在部署解決方案以後，您便能夠從 [BizTalk Server 管理主控台] 內，或是使用 BTSTask 命令列工具，來檢視和管理已部署的組件及其成品。 您可以管理成品可以個別或應用程式內的群組。  
  
## <a name="deploying-an-assembly"></a>部署組件  
 您可以新增應用程式的組件，以下列方式：  
  
- 應用程式從 Visual Studio 環境中部署組件  
  
- 手動新增到應用程式的 BizTalk Server 管理主控台中的 BizTalk Server 組件  
  
- 使用指令碼，從命令列，將 BizTalk 組件新增至應用程式  
  
- 移動 BizTalk Server 組件從 BizTalk Server 管理主控台內的其他應用程式  
  
  如需有關如何將組件新增至應用程式的詳細資訊，請參閱[從 BizTalk 應用程式的 Visual Studio 部署 BizTalk 組件](http://go.microsoft.com/fwlink/?LinkID=154719)(http://go.microsoft.com/fwlink/?LinkID=154719)。  
  
## <a name="redeploying-assemblies"></a>重新部署組件  
 在開發和偵錯您的 BizTalk 組件，您可能需要重新部署這些多次。 BizTalk Server 提供的重新部署簡單的機制。 如果您想要重新部署組件而不需要變更的版本號碼，您可以使用 [重新部署] 屬性。 BizTalk Server 會自動執行所有步驟，以重新部署您的組件。  
  
 如需有關如何重新部署組件的詳細資訊，請參閱 <<c0> [ 如何重新部署 BizTalk 組件從 Visual Studio](http://go.microsoft.com/fwlink/?LinkID=154720) (http://go.microsoft.com/fwlink/?LinkID=154720)。  
  
### <a name="best-practices-for-redeploying-an-assembly"></a>重新部署組件的最佳作法  
 **您必須在 GAC 中安裝新的組件**  
  
- 當您重新部署組件時，您一律必須在全域組件快取 (GAC) 中，安裝新版的組件。 您可以在重新部署後執行此作業。 如需詳細資訊，請參閱 <<c0> [ 如何將組件安裝在 GAC](http://go.microsoft.com/fwlink/?LinkID=154828) (http://go.microsoft.com/fwlink/?LinkID=154828)。  
  
  **您應該一律重新部署方案層級相依性存在時**  
  
- 如果解決方案中有多個組件，而且此解決方案中的一或多個組件相依於要重新部署的組件，則您必須在解決方案層級重新部署組件。 這是因為當您重新部署專案層級的組件，BizTalk Server 會停止、 取消登錄、 解除繫結，這個組件所依存的其中一個相依於此組件或上的所有組件中移除成品。 BizTalk Server 不會執行部署、繫結、登錄和啟動成品的額外步驟。 不過，當您重新部署整個解決方案時，BizTalk Server 會自動執行必要步驟，根據成品的相依性，解除部署和重新部署解決方案中的所有成品。  
  
  **您可能需要以手動方式重新部署相依組件**  
  
- BizTalk Server 永遠解除部署相依組件，當它解除部署組件，但在下列情況中，您必須採取其他步驟，部署、 繫結，並且登錄之後重新部署組件所在的每個相依組件中的成品組件而定：  
  
   如果您在專案層級重新部署組件，而且相同解決方案中的另一個組件相依於此組件。  
  
   如果您在解決方案層級重新部署組件，但不同解決方案中存在相依組件。  
  
  **您必須重新啟動主控件執行個體**  
  
- 當您重新部署包含協調流程的組件而不變更組件版本號碼時，BizTalk 管理資料庫中的現有組件會遭到覆寫。 不過，在變更生效之前，您必須重新啟動協調流程所繫結之主控件的每個主控件執行個體。 您可以指定選項，在重新部署組件時，自動重新啟動本機電腦上的所有主控件執行個體。  
  
   當您重新部署包含協調流程的組件而不變更組件版本號碼時，BizTalk 管理資料庫中的現有組件會遭到覆寫。 不過，在變更生效之前，您必須重新啟動協調流程所繫結之主控件的每個主控件執行個體。 您可以指定選項，在重新部署組件時，自動重新啟動本機電腦上的所有主控件執行個體。 如需有關部署屬性的詳細資訊，請參閱 <<c0> [ 如何在 Visual Studio 中的 設定部署屬性](http://go.microsoft.com/fwlink/?LinkID=154718)(http://go.microsoft.com/fwlink/?LinkID=154718)。  
  
   您也以手動方式即可停止和啟動每個主控件執行個體。 如需停止和啟動主控件執行個體的詳細資訊，請參閱[如何停止主控件執行個體](http://go.microsoft.com/fwlink/?LinkID=154829)(http://go.microsoft.com/fwlink/?LinkID=154829)並[如何啟動主控件執行個體](http://go.microsoft.com/fwlink/?LinkID=154830)(http://go.microsoft.com/fwlink/?LinkID=154830)。