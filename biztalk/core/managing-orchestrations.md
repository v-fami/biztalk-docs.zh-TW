---
title: 管理協調流程 |Microsoft 文件
description: 使用協調流程在 BizTalk Server 中，包括啟動、 停止、 繫結、 設定、 啟用追蹤、 暫止的連結等等
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2553eec3-b863-45fb-90af-7eddcfa7add7
caps.latest.revision: 31
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 18cd12c202822c4d9ff849cc762b55e8f4880d80
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22262646"
---
# <a name="manage-orchestrations"></a>管理協調流程

## <a name="overview"></a>概觀
本節中提供的指示，可讓您使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台來管理協調流程。 協調流程是可執行的商務程序。 如需協調流程的背景資訊，請參閱[協調流程](../core/orchestrations.md)。  

## <a name="add-to-application"></a>加入至應用程式  
 協調流程內建於 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，並被編譯到 BizTalk 組件中。 您無法將協調流程個別新增到應用程式；請遵循下列步驟將協調流程新增到應用程式：  
  
-   當您將加入包含應用程式，協調流程的 BizTalk 組件中所述[如何將 BizTalk 組件新增至應用程式](../core/how-to-add-a-biztalk-assembly-to-an-application.md)。  
  
-   當您匯入.msi 檔案包含包含協調流程的 BizTalk 組件中所述的應用程式[如何匯入 BizTalk 應用程式](../core/how-to-import-a-biztalk-application.md)。  
  
-   當開發人員應用程式組件部署到包含從協調流程[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]中所述，[從到 BizTalk 應用程式的 Visual Studio 部署 BizTalk 組件](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)。  

## <a name="biztalk-administration-tasks"></a>BizTalk 系統管理工作  
 您可以使用管理主控台來執行下列動作，如本節中的說明：  
  
-   藉由將協調流程繫結至適當的傳送埠、接收埠和主控件來設定協調流程的繫結，或是將這些繫結從協調流程中移除。  
  
-   設定協調流程的訊息追蹤。  
  
-   檢視協調流程的執行個體資訊。  
  
-   將協調流程登錄到適當的主控件，或從主控件取消登錄協調流程。  
  
-   開始或停止協調流程，使其開始或停止處理訊息。  
  
> [!NOTE]
>  您可以使用 Microsoft Windows Management Instrumentation (WMI) 物件模型，建立和執行會自動化系統管理工作的指令碼。 如需使用 WMI 的詳細資訊，請參閱**WMI 類別參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。 
  
> [!NOTE]
>  開發人員會使用來建立協調流程，協調流程設計師 」 中所述[協調流程使用協調流程設計師建立](../core/creating-orchestrations-using-orchestration-designer.md)。 開發人員也可以在開發程序中，藉由使用管理主控台 (如本節中的說明) 來管理協調流程。  
  
## <a name="next-steps"></a>後續的步驟
  
-   [設定協調流程的繫結](../core/how-to-configure-bindings-for-an-orchestration.md)  
  
-   [解除繫結協調流程](../core/how-to-unbind-an-orchestration.md)  
  
-   [設定協調流程的追蹤](../core/how-to-configure-tracking-for-an-orchestration.md)  
  
-   [檢視協調流程的執行個體資訊](../core/how-to-view-instance-information-for-an-orchestration.md)  
  
-   [從應用程式移除協調流程](../core/how-to-remove-an-orchestration-from-an-application.md)  
  
-   [登錄協調流程](../core/how-to-enlist-an-orchestration.md)  
  
-   [取消登錄協調流程](../core/how-to-unenlist-an-orchestration.md)  
  
-   [啟動協調流程](../core/how-to-start-an-orchestration.md)  
  
-   [停止協調流程](../core/how-to-stop-an-orchestration.md)  
  
-   [擱置、 繼續和終止協調流程執行個體](../core/how-to-suspend-resume-and-terminate-orchestration-instances.md)  
  
-   [升級協調流程](../core/how-to-upgrade-an-orchestration.md)