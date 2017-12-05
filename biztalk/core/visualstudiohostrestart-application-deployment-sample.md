---
title: "VisualStudioHostRestart （應用程式部署範例） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d0b82627-1552-479d-a083-cdc9fe4843c3
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d98a3a5e497a4476de897c8008f3a9976812209a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="visualstudiohostrestart-application-deployment-sample"></a>VisualStudioHostRestart (應用程式部署範例)
本主題會說明如何使用 VisualStudioHostRestart 範例指令碼，重新啟動本機電腦上 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 所執行的主控件執行個體。 您可以在重新部署 Visual Studio 中的組件時使用這個指令碼，以便 BizTalk Server 執行階段立即接受變更。 此外，您可以用這個選項來重新啟動主控件執行個體，這個選項可在專案的 [部署] 屬性中加以設定。 如需詳細資訊，請參閱[如何在 Visual Studio 中設定部署屬性](../core/how-to-set-deployment-properties-in-visual-studio.md)。  
  
## <a name="what-this-sample-does"></a>此範例的用途  
 這個範例指令碼會依序執行下列動作：  
  
1.  停止本機電腦上的所有內含式主控件執行個體。  
  
2.  啟動本機電腦上的所有內含式主控件執行個體。  
  
## <a name="where-to-find-this-sample"></a>可在何處找到此範例  
 此範例位於[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，如下所示的安裝資料夾： *\<範例路徑\>*\Application Deployment\VisualStudioHostRestart。  
  
 此範例包含下列檔案：  
  
-   RestartBizTalkHostInstances.vbs  
  
## <a name="how-to-use-this-sample"></a>如何使用此範例  
 請使用下列程序來執行此範例。  
  
### <a name="to-run-the-sample"></a>執行範例  
  
-   執行 RestartBizTalkHostInstances.vbs。  
  
## <a name="see-also"></a>請參閱  
 [應用程式部署 （BizTalk Server 範例資料夾）](../core/application-deployment-biztalk-server-samples-folder.md)   
 [部署 BizTalk 組件從 Visual Studio 到 BizTalk 應用程式](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)   
 [部署 BizTalk 應用程式](../core/deploying-biztalk-applications.md)