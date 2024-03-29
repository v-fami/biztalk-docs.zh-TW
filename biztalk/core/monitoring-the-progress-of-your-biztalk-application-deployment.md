---
title: 監控 BizTalk 應用程式部署的進度 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- monitoring, deploying
- applications, monitoring
- deploying [applications], monitoring
- monitoring, applications
ms.assetid: a69a8288-0203-440f-9805-52786525e193
caps.latest.revision: 20
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 07beea810ff64c807685b8170009d5204ede1af7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37001151"
---
# <a name="monitoring-the-progress-of-your-biztalk-application-deployment"></a>監控 BizTalk 應用程式部署的進度
有兩個方法可以監控 BizTalk 應用程式部署的進度：  
  
- **BizTalk 安裝記錄檔**： 您可以查閱 BizTalk Server 產生安裝記錄檔。 安裝記錄檔位於 %SystemDrive%\Documents and Settings\\<*目前的使用者*\>\application data\microsoft\biztalk Server\Deployment。  
  
- **本機事件記錄檔**： 您可以追蹤本機事件記錄檔中安裝的進度。 因此，您可以以個別伺服器為基礎來追蹤自訂安裝動作。  
  
- **Windows Installer 記錄**: Microsoft Windows 安裝程式會建立自訂動作的動作記錄在本機電腦上的記錄檔。 您可以使用 msiexec 命令的 /log 選項來指定這個記錄檔。 如需詳細資訊，請參閱 Windows Installer 的文件。  
  
> [!IMPORTANT]
>  部署或解除部署屬性結構描述可能會公開機密資料，而之後可能會在追蹤期間公開機密資訊。 每當部署或解除部署包含屬性結構描述的組件時，事件檢視器會將事件記錄在 Windows 應用程式事件記錄中。 您應檢查事件日誌檔中的這些訊息，確保所有組件部署活動都符合任何機密資料的原則 (部署為事件記錄檔產生的訊息: 「 使用者 」{1}「 已部署組件 」{0}"包含屬性結構描述 」。 解除部署是產生事件記錄檔的訊息: 「 使用者 」{1}"已解除部署組件 」{0}"包含屬性結構描述 」。)  
  
## <a name="see-also"></a>另請參閱  
 [部署 BizTalk 應用程式](../core/deploying-biztalk-applications.md)