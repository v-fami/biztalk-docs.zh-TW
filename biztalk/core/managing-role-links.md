---
title: 管理角色連結 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b8860e11-3d2c-450f-a7d2-cc116478999c
caps.latest.revision: 22
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e31ec8af7f8c5dd785b471654e9a9cfd7446bbf3
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36998943"
---
# <a name="manage-role-links"></a>管理角色連結

## <a name="overview"></a>概觀
本節提供使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台管理 BizTalk 應用程式中的角色連結的指示。 角色連結會定義參與商務交易的合作對象之間的關係，並指定用於雙向互動的訊息及連接埠類型。 如需角色連結的背景資訊，請參閱[協調流程中使用角色連結](../core/using-role-links-in-orchestrations.md)。  

## <a name="added-to-application"></a>新增至應用程式  
 角色連結內建於 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中，並且編譯成 BizTalk 組件。 您無法將角色連結個別新增至應用程式；角色連結會在下列情況中新增至應用程式：  
  
- 當您新增 BizTalk 組件包含應用程式，角色連結中所述[如何將 BizTalk 組件新增至應用程式](../core/how-to-add-a-biztalk-assembly-to-an-application.md)。  
  
- 當您匯入.msi 檔案包含 BizTalk 組件包含角色連結，如中所述的應用程式[如何匯入 BizTalk 應用程式](../core/how-to-import-a-biztalk-application.md)。  
  
- 當開發人員部署至應用程式包含角色連結的組件[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]中所述[從 BizTalk 應用程式的 Visual Studio 部署 BizTalk 組件](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)。  

## <a name="deploy-to-production"></a>部署到生產環境  
 BizTalk 應用程式開發人員會建立角色連結以實作兩個或更多參與商務交易的合作對象 (例如您的組織和供應商) 之間的通訊。 開發人員不一定要指定參與交易的合作對象，只需指定其角色即可。 若要將包含角色連結的應用程式部署到生產環境，並且在合作對象之間啟用實際的通訊，則必須執行下列組態，如本節中所述：  
  
- 如果未在開發程序中完成，則必須將合作對象指派給角色連結中定義的每個角色。 此即所謂「登錄」角色的合作對象。 如果您不想再讓合作對象具有指派的角色，則可以事後取消登錄該合作對象。  
  
- 角色連結內定義的每個合作對象的邏輯連接埠必須繫結至裝載應用程式之 BizTalk 主控件執行個體上的實體連接埠。  
  
  如需有關如何開發角色連結的詳細資訊，請參閱[協調流程中使用角色連結](../core/using-role-links-in-orchestrations.md)。  
  
> [!NOTE]
>  您可以使用 Microsoft Windows Management Instrumentation (WMI) 物件模型，建立和執行會自動化系統管理工作的指令碼。 如需使用 WMI 的詳細資訊，請參閱**WMI 類別參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。  
  
## <a name="next-step"></a>下一步
  
-   [如何登錄或取消登錄角色的合作對象](../core/how-to-enlist-or-unenlist-a-party-for-a-role.md)