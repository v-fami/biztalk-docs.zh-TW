---
title: 追蹤 BizTalk Server 應用程式中成品之間的相依性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 503cadfc-08e5-4b34-94a2-3b0ea6ad6228
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3edd162075f1ad660c005fd387ac9bc6c8c79e38
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22279950"
---
# <a name="tracking-dependencies-between-artifacts-in-a-biztalk-server-application"></a>追蹤 BizTalk Server 應用程式中成品之間的依存性
典型的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 應用程式包含各種成品，例如協調流程、傳送埠、接收位置、管線、結構描述、對應等等。 這些成品相互依存。 下表列出這些依存性。  
  
|成品|協調流程|傳送埠|接收埠|接收位置|管線|地圖|結構描述|  
|---------------|-------------------|---------------|------------------|----------------------|--------------|----------|-------------|  
|**協調流程**||![使用](../core/media/dependency-using-icon.png "Dependency_Using_Icon")||![使用](../core/media/dependency-using-icon.png "Dependency_Using_Icon")||||  
|**傳送埠**|![使用](../core/media/dependency-usedby-icon.png "Dependency_UsedBy_Icon")||||![使用](../core/media/dependency-using-icon.png "Dependency_Using_Icon")|![使用](../core/media/dependency-using-icon.png "Dependency_Using_Icon")||  
|**接收埠**|![使用](../core/media/dependency-usedby-icon.png "Dependency_UsedBy_Icon")|||![使用](../core/media/dependency-using-icon.png "Dependency_Using_Icon")||![使用](../core/media/dependency-using-icon.png "Dependency_Using_Icon")||  
|**接收位置**|||![使用](../core/media/dependency-usedby-icon.png "Dependency_UsedBy_Icon")||![使用](../core/media/dependency-using-icon.png "Dependency_Using_Icon")|||  
|**管線**||![使用](../core/media/dependency-usedby-icon.png "Dependency_UsedBy_Icon")||![使用](../core/media/dependency-usedby-icon.png "Dependency_UsedBy_Icon")||||  
|**對應**||![使用](../core/media/dependency-usedby-icon.png "Dependency_UsedBy_Icon")|![使用](../core/media/dependency-usedby-icon.png "Dependency_UsedBy_Icon")||||![使用](../core/media/dependency-using-icon.png "Dependency_Using_Icon")|  
|**結構描述**||||||![使用](../core/media/dependency-usedby-icon.png "Dependency_UsedBy_Icon")||  
  
 如此表所建議，依存性模式有兩種。  
  
-   使用 (![使用](../core/media/dependency-using-icon.png "Dependency_Using_Icon")) – 成品會使用其他成品，例如，傳送埠會使用管線。  
  
-   被使用 (![供](../core/media/dependency-usedby-icon.png "Dependency_UsedBy_Icon")) – 成品由其他成品，例如，傳送埠由協調流程。  
  
 由於有這些依存性，如果您需要更新成品，則必須知道必須停止或重新部署依存性階層中的哪些成品。 這類依存性資訊可以在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台中取得。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台會顯示相依性資訊以兩種模式 – 不論是成品使用其他成品*以及*成品由另一個成品。  
  
## <a name="viewing-dependencies"></a>檢視依存性  
 本節提供如何使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台檢視依存性的相關資訊。  
  
> [!NOTE]
>  下列程序提供如何檢視協調流程依存性的指示。 您也可以遵循相同的指示來檢視其他成品的依存性。  
  
#### <a name="to-view-dependencies-for-an-artifact"></a>若要檢視成品的依存性  
  
1.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開 應用程式，然後按一下**協調流程**。 在中間窗格中，以滑鼠右鍵按一下您要查看的相依性，然後按一下 協調的流程**檢視相依性**。  
  
2.  [] 窗格的底端**依存性統計資料**窗格會顯示兩種依存性。 **被使用**類別顯示使用該特定協調流程的成品。 **使用**類別顯示特定協調流程所使用的成品。  
  
     ![相依性的協調流程](../core/media/dependency-orchestration.jpg "Dependency_Orchestration")  
  
     因為沒有其他成品相依於協調流程，**被使用**協調流程的相依性分類是空的。 但是，在**使用**相依性模式中，影像顯示協調流程會相依於一個傳送埠。 依存性數目會顯示為超連結，按一下此超連結，只會顯示協調流程所依存的傳送埠。 請注意，按一下此超連結以列出傳送埠之後，依存性窗格仍會顯示協調流程 (而非傳送埠) 的依存性統計資料。  
  
     您可以以滑鼠右鍵按一下傳送埠，然後按一下**檢視相依性**同樣地，若要查看傳送埠的相依性矩陣。 您可以檢視任何層次的依存性樹狀結構。 窗格上方的麵包屑軌跡會顯示您位於依存性樹狀結構中的層次，如下圖所示。  
  
     ![麵包相依性樹狀結構的麵包屑](../core/media/dependency-breadcrumbs.jpg "Dependency_BreadCrumbs")