---
title: 管理對應 |Microsoft Docs
description: 若要使用對應在 BizTalk Server 中，包括檢視和移除對應的連結
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0e8e3057-5a9f-4b6b-b6ee-c71b7e6a51ac
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5d6957a4f3d73c5f59df5cd36f70a7ed34631fa6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37019828"
---
# <a name="manage-maps"></a>管理對應

## <a name="overview"></a>概觀
本節提供使用 BizTalk Server 管理主控台管理對應的指示。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 要轉譯的記錄和記錄的一個結構描述中的欄位和另一個結構描述中的欄位，會使用對應。 對應可供協調流程、傳送埠和接收埠使用。  

## <a name="add-maps-to-an-application"></a>將地圖加入至應用程式  
 對應內建於 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，並被編譯到 BizTalk 組件中。 您無法將對應個別新增至應用程式；對應會在下列情況中新增至應用程式：  
  
- 當您將包含應用程式，對應的 BizTalk 組件中所述[如何將 BizTalk 組件新增至應用程式](../core/how-to-add-a-biztalk-assembly-to-an-application.md)。  
  
- 當您匯入.msi 檔案包含應用程式，包含對應的 BizTalk 組件中所述[如何匯入 BizTalk 應用程式](../core/how-to-import-a-biztalk-application.md)。  
  
- 當開發人員應用程式組件部署到包含從對應[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]中所述[從 BizTalk 應用程式的 Visual Studio 部署 BizTalk 組件](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)。  
  
  如需地圖的背景資訊，請參閱 <<c0> [ 對應](../core/maps.md)。 如需建立對應的資訊，請參閱[建立對應使用 BizTalk 對應工具](../core/creating-maps-using-biztalk-mapper.md)。  
  
> [!NOTE]
>  您可以使用 Microsoft Windows Management Instrumentation (WMI) 物件模型，建立和執行會自動化系統管理工作的指令碼。 如需使用 WMI 的詳細資訊，請參閱**WMI 類別參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
  
## <a name="next-steps"></a>後續的步驟 
  
-   [檢視應用程式的對應](../core/how-to-view-the-maps-for-an-application.md)  
  
-   [從應用程式移除對應](../core/how-to-remove-a-map-from-an-application.md)