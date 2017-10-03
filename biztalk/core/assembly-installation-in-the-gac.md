---
title: "組件安裝在 GAC 中的 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3b12d00c-8750-4c6d-8244-e613f955a478
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e48ec0dddcf17be70b915d2beb058f1ab2f6f576
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="assembly-installation-in-the-gac"></a>GAC 中的組件安裝
每部電腦都含有全域組件快取 (GAC)，其中包含該部電腦上一個或多個應用程式所使用的組件。 為了讓 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 在執行階段期間處理訊息，BizTalk 應用程式所包含的組件必須存在於執行應用程式之電腦的 GAC 中。  
  
 如果您的應用程式隔離在一個伺服器上，組件就只需要存在於該伺服器的 GAC 中。 但是，如果有多部伺服器在主控應用程式，該應用程式中的組件就必須存在於需要存取組件所包含之成品的每部電腦的 GAC 中。 例如，如果您將 Assembly_A 部署至 Server_1，然後在 Server_2 上的主機中登錄 Assembly_A，assembly_a 就必須安裝在 Server_2 上的 GAC 中。 如果不是，Server_2 將無法在執行階段期間存取 Assembly_A。  
  
 尤其，包含協調流程及其所依靠之任合組件的組件，都一定得安裝在伺服器上的 GAC 中，且這些伺服器必須執行協調流程所繫結之目標主控件的執行個體。 此外，包含由連接埠使用之對應和管線的組件，也必須安裝在執行主控件 (提供連接埠之配接器處理常式服務) 之執行個體的伺服器上。  
  
 您可以指定每個組件的部署選項，以便在從 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 部署組件時將其安裝到 GAC 中。 或者，您可以用手動方式將組件安裝到 GAC 中。 此外，您可以指定將組件部署到 BizTalk 應用程式後，在 GAC 中安裝組件的部署選項。  
  
 下列摘要可在 GAC 中安裝組件的工具和方法：  
  
-   **Microsoft Visual Studio。** 如先前所述，您可以設定專案屬性的組件在 GAC 中自動安裝時，您將部署中所述[如何在 Visual Studio 中設定部署屬性](../core/how-to-set-deployment-properties-in-visual-studio.md)。 您也可以手動安裝的組件在 GAC 中所隨附的 Gacutil 命令列工具[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]中所述，[如何在 GAC 中安裝組件](../core/how-to-install-an-assembly-in-the-gac.md)。  
  
-   **BTSTask 命令列工具。** 當您使用 BTSTask 將組件新增至 BizTalk 應用程式時，即可指定在匯入或安裝包含該組件的應用程式時，將組件安裝到 GAC 中的選項。 如需詳細資訊，請參閱[AddResource 命令： BizTalk 組件](../core/addresource-command-biztalk-assembly.md)。 另請參閱[AddResource 命令：.NET 組件](../core/addresource-command-net-assembly.md)。  
  
-   **BizTalk Server 管理主控台。** 使用與 BTSTask 相同的方式，當您使用 [管理主控台] 將組件新增至應用程式時，即可指定在匯入或安裝包含該組件的應用程式時，將組件安裝到 GAC 中的選項。 如需詳細資訊，請參閱[如何將 BizTalk 組件新增至應用程式](../core/how-to-add-a-biztalk-assembly-to-an-application.md)。 另請參閱[如何將.NET 組件新增至應用程式](../core/how-to-add-a-net-assembly-to-an-application.md)。  
  
     此外，您可以設定部署選項在任何時間之後已部署至或加入至應用程式，組件中所述[如何修改 BizTalk 組件的部署選項](../core/how-to-modify-the-deployment-options-of-a-biztalk-assembly.md)。 組件會部署到[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]從[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]第一次，在管理主控台中的部署選項設定如下： GAC 安裝上的已啟用和停用 GAC，匯入。 如果您變更了這些設定，即使組件已經從 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 重新部署，您的變更依然會具有效果。  
  
-   **拖放。** 使用 Windows 檔案總管中，您可以拖放組件檔\< *Windows 資料夾*> \assembly。  
  
-   **其他方法。** 還有其他工具和方法，包括使用 Windows Installer 或協力廠商所建立的工具，都能將組件安裝到 GAC 中。  
  
> [!IMPORTANT]
>  為了讓您的應用程式能夠適當運作，請確定在 GAC 中具有與 BizTalk 管理資料庫中版本相同的組件。 如果您沒有總是在部署組件時將其安裝到 GAC 中，就可能會在 GAC 和 BizTalk 管理資料庫中擁有不同的版本，這樣將會造成執行階段期間的處理錯誤。  
  
> [!IMPORTANT]
>  如需版本編號的詳細資訊，請參閱 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 所提供「.NET Framework 說明」中的＜組件版本編號＞。 請注意，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 不支援使用 .NET 原則檔。  
  
## <a name="see-also"></a>另請參閱  
 [部署 BizTalk 組件從 Visual Studio 到 BizTalk 應用程式](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)   
 [了解 BizTalk 應用程式部署和管理](../core/understanding-biztalk-application-deployment-and-management.md)