---
title: '專案設計工具: [部署] 索引標籤 |Microsoft 文件'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- properties, Configuration database [BizTalk Server]
- Redeploy property
- configuration properties [deployment], Server property
- Server property
- configuration properties [deployment], Install to Global Assembly Cache (GAC) property
- properties, Management database
- Install to Global Assembly Cache (GAC) property
- Configuration database [BizTalk Server], properties
- Management database, properties
- Administration Group property
- configuration properties [deployment], Redeploy property
- configuration properties [deployment], Management database property
- configuration properties [deployment], Administration Group property
ms.assetid: 5b64f99c-4ec6-4ed3-8590-46420e2f75b8
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 972f3956a19d66d47238ee8170584b4faf6ba886
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22264942"
---
# <a name="project-designer-deployment-tab"></a>專案設計工具：[部署] 索引標籤
**部署**屬性索引標籤的 專案設計工具可讓您設定 BizTalk 專案的部署屬性。 您必須同時設定**伺服器**和**組態資料庫**（也稱為 「 BizTalk 管理資料庫） 屬性為集合，部署才能成功。  
  
## <a name="application-name"></a>Application Name  
 指定要部署組件的 BizTalk 應用程式。 如果這個名稱是空的，專案就會部署到預設應用程式中。  
  
## <a name="configuration-database"></a>組態資料庫  
 使用此欄位為已部署的組件指定「BizTalk 組態」資料庫的名稱。 若已將 BizTalk 專案設定為部署專案，則適用此選項。  
  
> [!NOTE]
>  「BizTalk 組態」資料庫也稱為「BizTalk 管理」資料庫。  
  
 預設的組態資料庫名稱為 BizTalkMgmtDb。  
  
## <a name="server"></a>Server  
 這是組態儲存機制 (也稱為「BizTalk 管理」或「BizTalk 組態」資料庫) 所在的伺服器名稱。 若將 BizTalk 專案設定為「部署」，則會將 BizTalk 專案部署至此伺服器。  
  
## <a name="redeploy"></a>重新部署  
 您使用**重新部署**屬性來判斷是否要刪除現有組態並重新建立設定每次部署組件。 預設值是`True`。  
  
## <a name="install-to-global-assembly-cache"></a>安裝到全域組件快取  
 您使用**安裝到全域組件快取**屬性，指出如果[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]需要將 BizTalk 組件安裝至全域組件快取 (GAC)。  
  
## <a name="restart-host-instances"></a>重新啟動主控件執行個體  
 如果您設定**重新啟動主控件執行個體**至**True**，部署專案時，將重新啟動本機電腦上的主控件執行個體[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。 這在您進行變更和經常進行重新部署的開發週期非常有用；您將不需要手動重新啟動相關的主控件執行個體。  
  
 如果您未重新啟動相關的主控件執行個體，最近的變更就不會反映在 BizTalk 應用程式中，因為舊版可能仍在快取中。 重新啟動主控件執行個體可清除快取的組件。  
  
## <a name="enable-unit-testing"></a>啟用單元測試  
 指定是否為專案啟用單元測試。  
  
## <a name="see-also"></a>另請參閱  
 [如何部署 BizTalk 組件從 Visual Studio](../core/how-to-deploy-a-biztalk-assembly-from-visual-studio.md)   
 [BizTalk 專案 [屬性] 視窗](../core/biztalk-project-properties-window.md)