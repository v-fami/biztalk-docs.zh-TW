---
title: 何謂 BizTalk 應用程式？ | Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BizTalk.System application, about BizTalk.System application
- applications, default
- BizTalk.System application
- artifacts, about artifacts
- applications
- applications, about applications
- applications, warnings
- applications, BizTalk.System
- what's new, applications
- BizTalk.System application, warnings
ms.assetid: 68b5527c-d5e1-453b-a51b-3fc1a1d5dce2
caps.latest.revision: 28
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 68e01881693c7db8b12b7da4edf246942fe02825
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26008775"
---
# <a name="what-is-a-biztalk-application"></a>何謂 BizTalk 應用程式？
BizTalk 應用程式是 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的功能，能讓 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 商務解決方案的部署、管理和疑難排解更加快速輕鬆。 BizTalk 應用程式是 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 商務解決方案中所使用項目 (稱為「成品」) 的邏輯群組。 在本主題在稍後將會詳細說明成品。  
  
 全新設計的管理和監控 BizTalk server 的工具利用這個新概念，使您可以管理和設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式層級，而不只是在個別成品層級的商務解決方案。 透過建立應用程式並將成品加入至其中，您可以將解決方案中的一組成品當做單一實體，予以檢視、封裝、部署和管理. 因此，隨著複雜應用程式的增加，您仍然可以透過簡單、直覺化方式個別管理它們。  
  
 有數種工具可用來建立和管理應用程式，如下所述[應用程式部署和管理工具](../core/application-deployment-and-management-tools.md)。  
  
 下列圖表說明兩個 BizTalk 應用程式及其包含的成品。  
  
 ![BizTalk 應用程式和成品](../core/media/biztalkapplication.gif "BizTalkApplication")  
  
## <a name="artifacts"></a>成品  
 成品如下：  
  
-   BizTalk 組件及其包含的 BizTalk 特定資源，例如協調流程、管線、結構描述和對應  
  
-   不包含 BizTalk 特定資源的 .NET 組件  
  
-   原則  
  
-   傳送埠、接收埠群組、接收位置和接收埠  
  
-   解決方案使用的其他項目，例如憑證、COM 元件和指令碼  
  
 如需每種類型的成品的背景資訊，請參閱[執行階段架構](../core/runtime-architecture.md)。 如需有關新增的詳細資訊，請移除和設定成品，請參閱[管理成品](../core/managing-artifacts.md)。  
  
 一個應用程式可以包含商務解決方案中使用的全部成品或其中一部分。 根據所需的部署成品方式，您可以將成品放入一個或多個應用程式中。 如需有關決定如何群組成品的詳細資訊，請參閱[部署 BizTalk 應用程式的最佳作法](../core/best-practices-for-deploying-a-biztalk-application.md)。  
  
## <a name="the-default-application"></a>預設應用程式  
 在安裝之後設定 BizTalk Server 時，會自動建立名為 BizTalk Application 1 的預設應用程式。 如需最佳作法，將成品分組到不同的應用程式的資訊，請參閱[部署 BizTalk 應用程式的最佳作法](../core/best-practices-for-deploying-a-biztalk-application.md)。 您也可以變更或重新命名預設應用程式。  
  
 在下列實例中，成品會自動加入至預設應用程式：  
  
-   當您從 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 將組件部署至 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，但未指定應用程式名稱時。 如需詳細資訊，請參閱[如何部署 BizTalk 組件從 Visual Studio](../core/how-to-deploy-a-biztalk-assembly-from-visual-studio.md)。  
  
-   當您使用 BTSTask 將成品加入至應用程式，但未指定應用程式名稱時。 如需詳細資訊，請參閱[AddResource 命令](../core/addresource-command.md)。  
  
-   當您使用 BTSTask 匯入應用程式 .msi 檔案，但未指定應用程式名稱時。 如需詳細資訊，請參閱[ImportApp 命令](../core/importapp-command.md)。  
  
## <a name="the-biztalksystem-application"></a>BizTalk.System 應用程式  
 設定下列安裝 BizTalk Server 時，名為 BizTalk.System 的應用程式會自動建立並填入所有的 BizTalk 應用程式，例如預設結構描述和管線所使用的一般成品。 BizTalk.System 及其成品都是唯讀。 您不能刪除或重新命名 BizTalk.System，也不能刪除、重新命名或移動其中包含的任何成品。  
  
> [!IMPORTANT]
>  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的每個應用程式都會自動包含 BizTalk.System 應用程式的參考。 這是因為每個 BizTalk 應用程式都會使用 BizTalk.System 的成品。 您絕對不能移除 BizTalk.系統應用程式的參考， 否則您的應用程式可能無法正常運作。  
  
## <a name="see-also"></a>請參閱  
 [了解 BizTalk 應用程式部署和管理](../core/understanding-biztalk-application-deployment-and-management.md)