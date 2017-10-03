---
title: "部署及管理 BizTalk 應用程式所需的權限 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying [applications], security
- permissions, EDI adapters
- deploying, security
- security, applications
- security, EDI adapters
- assemblies, permissions
- permissions, deploying
- EDI adapters, security
- permissions, assemblies
- security, assemblies
- permissions, applications
- deploying, permissions
- applications, importing
- applications, exporting
- permissions, exporting
- installing, permissions
- applications, security
- security, permissions
- applications, installing
- assemblies, security
- managing, security
ms.assetid: 4a459ff1-661d-403a-99e0-d54b82e008d0
caps.latest.revision: "24"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 608da93cd1960d26304f4dcebe239367de2404e4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="permissions-required-for-deploying-and-managing-a-biztalk-application"></a>部署和管理 BizTalk 應用程式所需的權限
應用程式部署包括從 Visual Studio 部署 BizTalk 組件，以及匯入、匯出和安裝 BizTalk 應用程式。 執行這些工作所需的基本權限如下：  
  
-   身為「BizTalk Server 系統管理員」群組的成員，您將被授與從 Visual Studio 部署 BizTalk 組件所需的權限。  
  
-   身為「BizTalk Server 系統管理員」群組的成員，您將被授與將 BizTalk 應用程式匯入 BizTalk 群組所需的權限。 如果已指定在匯入時將應用程式中包含的組件新增到全域組件快取 (GAC) 的選項，您也必須擁有組件資料夾的寫入權限。 身為本機「系統管理員」群組的成員，您將擁有此權限。  
  
-   身為「BizTalk Server 系統管理員」或「BizTalk 操作員」群組的成員，您將被授與執行以下動作所需的權限：  
  
    -   匯出 BizTalk 應用程式  
  
    -   啟動和停止傳送埠、傳送埠群組和協調流程  
  
    -   啟用和停用接收位置  
  
    -   擱置、繼續和終止執行個體。  
  
    -   啟動和停止應用程式  
  
-   身為本機「系統管理員」群組的成員，您將被授與在本機電腦上安裝 BizTalk 應用程式的權限。  
  
 您可能會想要為使用者提供執行這些工作最嚴格的權限。 本主題接下來將為所需的權限提供更詳盡的說明，如下所示。  
  
-   [部署 BizTalk 組件從 Visual Studio 的權限](#BKMK_Permissions_for_deploying)  
  
-   [匯入應用程式的權限](#BKMK_Permissions_for_importing)  
  
-   [匯出應用程式的權限](#BKMK_Permissions_for_exporting)  
  
-   [安裝應用程式的權限](#BKMK_Permissions_for_installing_an_application)  
  
##  <a name="BKMK_Permissions_for_deploying"></a>部署 BizTalk 組件從 Visual Studio 的權限  
 若要從 Visual Studio 中部署 BizTalk 組件，您必須至少擁有 BizTalk 管理資料庫的「寫入」權限。 身為「BizTalk Server 系統管理員」群組的成員，您將被授與此權限。  
  
##  <a name="BKMK_Permissions_for_importing"></a>匯入應用程式的權限  
 若要匯入 BizTalk 應用程式，您至少必須擁有下列權限。 身為「BizTalk Server 系統管理員」群組的成員，您將被授與所有需要的權限，但如果您想要將任何組件安裝到 GAC，您還必須擁有組件資料夾的「寫入」權限。  
  
|項目|Permissions|需要時|  
|----------|-----------------|-------------------|  
|BizTalk 管理資料庫|讀取/寫入|永遠需要。|  
|BizTalk 規則引擎資料庫|讀取/寫入|只有應用程式包括規則資源時才需要。|  
|BAM 資料庫|讀取/寫入|只有應用程式包括 BAM 資源時才需要|  
|全域組件快取 (GAC)|讀取/寫入|只有當應用程式包括組件資源並且您指定在匯入時將組件加入 GAC 時才需要。 (請參閱注意。)|  
  
> [!NOTE]
>  當使用「匯入精靈」匯入組件時，您可以指定此選項以新增組件至全域組件快取 (GAC)。 在此情況下，您必須擁有組件資料夾的寫入權限。 如需組件資料夾的詳細資訊，請參閱[安裝應用程式的權限](#BKMK_Permissions_for_installing_an_application)。  
>   
>  如果您的應用程式包含的某個指令碼會部署除了所列以外的任何項目，您必須有適當的權限才能進行部署。  
  
##  <a name="BKMK_Permissions_for_exporting"></a>匯出應用程式的權限  
 若要匯出 BizTalk 應用程式，您至少必須擁有下列權限。 身為「BizTalk 作員」群組的成員，您將被授與所需的權限。  
  
|項目|Permissions|需要時|  
|----------|-----------------|-------------------|  
|BizTalk 管理資料庫|讀取|永遠需要。|  
|BizTalk 規則引擎資料庫|讀取|只有應用程式包括規則資源時才需要。|  
|憑證存放區|讀取|只有應用程式包括憑證資源時才需要。|  
|Internet Information Services|讀取|只有應用程式包括虛擬目錄資源時才需要。|  
  
##  <a name="BKMK_Permissions_for_installing_an_application"></a>安裝應用程式的權限  
 依照預設，身為本機「系統管理員」群組的成員會擁有在本機電腦上安裝 BizTalk 應用程式所需的權限。 如果您想要為需要安裝應用程式的使用者提供最嚴格的權限，下表提供您必須設定的最低權限。 除了這些權限以外，如果您的應用程式擁有需要其他權限才能安裝的資源，例如建立新資料庫或資料庫資料表，您還必須擁有這些權限。  
  
|項目|Permissions|需要時|  
|----------|-----------------|-------------------|  
|憑證存放區|讀取/寫入|只有應用程式包括憑證資源時才需要。|  
|Internet Information Services|讀取/寫入|只有應用程式包括虛擬目錄資源時才需要。|  
|GAC|讀取/寫入|只有當應用程式包括組件資源並且您指定在安裝時將組件加入 GAC 時才需要。 (參閱下方的注意。)|  
|檔案系統|讀取/寫入|只有在資源已設定目的屬性時才需要。|  
|登錄|讀取/寫入|若**regsvcs**或**regasm**屬性設為 True，適用於組件資源包含 managed COM 或 COM + 元件。|  
|登錄|讀取/寫入|當應用程式包括 Unmanaged COM 資源時才需要。|  
  
> [!NOTE]
>  從 BizTalk Server 管理主控台，您可以指定在安裝時將組件加入 GAC (使用滑鼠右鍵按一下資源資料夾中的組件，然後按一下 [修改])。 如果指定此選項，則安裝 BizTalk 應用程式將需要組件資料夾 (包含 GAC) 的「寫入」權限。 組件資料夾的路徑為 %SystemRoot%\assembly。  
  
## <a name="see-also"></a>另請參閱  
 [應用程式部署的安全性考量](../core/security-considerations-for-application-deployment.md)