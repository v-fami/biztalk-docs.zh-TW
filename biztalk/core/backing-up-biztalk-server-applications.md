---
title: "備份 BizTalk Server 應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b51e3ae6-08ed-48ca-8977-13f46144a5fa
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1d125a1430aa2d044abba7632fa31a9c89f2bc50
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="backing-up-biztalk-server-applications"></a>備份 BizTalk Server 應用程式
若要確保硬體失敗後可以復原您的 BizTalk Server 系統，擁有良好的備份是很重要的。 在備份過程中，您可以匯出 BizTalk 應用程式到遠端伺服器以及備份這些應用程式。  
  
 之後，在還原 BizTalk Server 資料庫及重新安裝 BizTalk Server 時，您就可以匯入這些應用程式。 如需如何匯出和匯入應用程式的詳細資訊，請參閱[部署和管理 BizTalk 應用程式](../core/deploying-and-managing-biztalk-applications.md)。  
  
 對於所有部署在電腦上的 BizTalk 應用程式，您應匯出 .msi 檔案，並將其儲存在備份位置 (不同的伺服器上)。 .msi 檔案可讓您在復原目的電腦後重新安裝 BizTalk Server 所需的資源。 您應確定 .msi 檔案包含所有必要的資源，以及指定在 .msi 安裝上要對這些資源執行的動作。 如果您的 BizTalk 應用程式相依於未包含在 .msi 檔案中的任何使用者組件或其他 DLL，就必須分別將其備份。  
  
 對以內容為基礎的路由實例以及具有協調流程的實例，應用程式匯出程序都相同。 只要變更 BizTalk 應用程式，您就應該重複這個程序。 如需詳細資訊，請參閱[如何匯出 BizTalk 應用程式](../core/how-to-export-a-biztalk-application.md)。  
  
## <a name="see-also"></a>另請參閱  
 [備份執行 BizTalk Server 的電腦](../core/backing-up-a-computer-running-biztalk-server.md)