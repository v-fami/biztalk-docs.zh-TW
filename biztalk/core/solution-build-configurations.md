---
title: "方案組建組態 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Configuration Manager
- building, solutions
- building, Configuration Manager
- solutions, deploying
- deploying, building
- solutions, developing
- solutions, build configuration
ms.assetid: 6f2cce47-388d-4c93-9146-768f53b8207e
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e537ca4bc2dd85722ddf3afd4eaba443aab7a25b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="solution-build-configurations"></a>方案建置組態
如同您在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中所建置的其他專案一樣，您可以使用「組態管理員」以指定方案建置組態。 方案組建組態可讓您決定哪些專案来包含在建置方案的如果將部署。 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]同時支援**偵錯**和**發行**組建組態。  
  
 方案建置組態中的核取記號**建置**資料行可讓您建置方案，以及當您完成時產生組件。 如果核取記號也會出現在**部署**資料行，則應用程式將會部署專案設計工具中的部署設定所決定。  
  
 Configuration Manager 和組態的完整參考選項提供由對話方塊方塊中，請參閱下列參考連結： [http://go.microsoft.com/fwlink/?LinkId=125365](http://go.microsoft.com/fwlink/?LinkId=125365)。  
  
### <a name="to-configure-build-properties-in-configuration-manager"></a>在組態管理員中設定建置屬性  
  
1.  按一下 [ **建置** ] 功能表上的 [ **組態管理員**]。  
  
2.  在**Configuration Manager**對話方塊中，選取其中一個下列命令來設定建置屬性。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**Configuration**|選擇從**發行**或**偵錯**專案的組態。 或者，建立新的組態或編輯現有的組態。|  
    |**平台**|為專案選擇代表編譯後組件之 CPU 架構的平台。 或者，建立新的平台，或編輯現有。|  
    |**建置**|針對專案核取此欄位的方塊，以建置或重新建置專案來回應方案的建置命令。|  
    |**部署**|針對方案或專案發出建置命令後，核取此欄位的方塊以依據部署設定來部署專案。|  
  
## <a name="see-also"></a>另請參閱  
 [如何部署 BizTalk 組件從 Visual Studio](../core/how-to-deploy-a-biztalk-assembly-from-visual-studio.md)   
 [如何建立 BizTalk 專案](../core/how-to-create-biztalk-projects.md)